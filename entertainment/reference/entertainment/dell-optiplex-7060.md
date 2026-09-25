# Dell OptiPlex 7060

The home PC. It runs Windows for personal use and entertainment, runs Fedora for all code work, and plays all music through Qobuz. Complaints: it doesn't turn the AVR/TV on or off, it's slow, the SSD is small, and the fan is loud.

> Researched September 2026. Anything marked **(unverified)** could not be confirmed from a primary source. Prices are rough US street prices and are unusually volatile in 2026 because of the DRAM/NAND shortage (see [Prices](#a-note-on-2026-prices)).

---

## TL;DR — what this machine actually is, and what to do

What the machine reports about itself, read live from the running Fedora install on 2026-09-24:

| Item | Value | How it was read |
|---|---|---|
| Model | Dell OptiPlex 7060, system SKU `085A`, board `0NC2VH` | `/sys/class/dmi/id/*` |
| Form factor | **Probably SFF** (see [Identify your form factor](#1-identify-your-form-factor)) | 3 SATA ports implemented (SFF has 3, MT has 4), slim DVD drive present (Micro has none), chassis type 3 "Desktop" |
| BIOS | **1.32.0** (2024-09-03), which is Dell's latest release | `/sys/class/dmi/id/bios_version` |
| CPU | **Core i7-8700** (6C/12T, 65 W, PL1 65 W / PL2 122 W) | `/proc/cpuinfo`, RAPL |
| RAM | 16 GB (number of sticks unknown; check with `sudo dmidecode -t memory`) | `free` |
| Windows drive | **ADATA SU800 256 GB SATA SSD** (`sda`, 6 Gb/s), NTFS "Crash's Main Drive" | `lsblk` |
| Fedora drive | **Kingston XS1000 1 TB external USB SSD** (`sdb`), LUKS + btrfs, **linked at only 5 Gb/s** | `lsblk`, `/sys/bus/usb` |
| NVMe | **None installed.** The M.2 2280 slot may be free if the SU800 is the 2.5" version | `lspci` |
| SATA mode | AHCI (good for Linux) | `lspci` |
| Secure Boot | Disabled; the boot order is Fedora (shim) first, then Windows Boot Manager | `efibootmgr`, `mokutil` |
| Video/audio out | **HDMI into the Denon.** The EDID reports `DENON-AVAMP`, via a DP++ port with a DP→HDMI cable or adapter | `/sys/class/drm/card0-HDMI-A-2` |
| Fan at idle | ~890 RPM at 32–33 °C | `dell_smm` hwmon |
| Linux audio | Qobine (Flatpak Qobuz client) → PipeWire → HDMI, **but PipeWire is locked to 48 kHz**, so playback is **not bit-perfect** | `wpctl status`, `pw-metadata` |

**Top recommendations, in order:**

1. **Fix Linux bit-perfect audio now (free, 2 minutes).** Allow PipeWire to switch sample rates ([Linux audio](#linux-fedora--qobuz)). The HDMI link to the Denon already accepts **2-channel PCM up to 24-bit/192 kHz**, which the Denon's own EDID confirms. You do **not** need a USB-to-S/PDIF adapter.
2. **Install an internal NVMe SSD (1–2 TB) and move Fedora onto it.** It will be ~5–7× faster than the USB drive running at 5 Gb/s. Keep Windows on its own drive. This fixes "small SSD" and most of "slow" at the same time. ([Storage](#6-fixing-small-ssd))
3. **Go to 32 GB RAM** if you run dev tools, containers or VMs. ([Slow](#5-fixing-slow))
4. **Power control:** a **USB-to-RS-232 cable to the Denon** (`PWON`/`PWSTANDBY`, 9600 8N1, confirmed in Denon's protocol document), plus a **Broadlink RM4 mini IR blaster** for the Vizio (no CEC anywhere in this chain), triggered by Windows Task Scheduler and a systemd sleep hook. About $50 total. ([Power control](#4-fixing-doesnt-power-avrtv-onoff))
5. **Fan:** blow out the dust, repaste, and cap CPU power. The 7060 BIOS has **no Quiet/Cool thermal-mode option**, only "Fan Control Override" (which forces full speed). Cap package power to ~45–50 W on Linux (RAPL) or Windows (max processor state / ThrottleStop). ([Fan](#7-fixing-loud-fan))
6. **Keep the OptiPlex.** An i7-8700 is still a capable 6-core/12-thread machine. Replace it only if you want a silent box. ([Alternatives](#10-alternatives-and-upgrade-path))

---

## 1. Identify your form factor

The 7060 came in three chassis. The **Micro** was also sold as "Tiny". Everything about upgrades depends on which one you have.

| Clue | Micro (D10U) | SFF (D11S) | MT/Tower (D18M) |
|---|---|---|---|
| Size (H × W × D) | 18.2 × 3.6 × 17.8 cm (1.2 L), lunchbox-sized | **29 × 9.3 × 29.2 cm (7.8 L)**, lies flat or stands | 35 × 15.4 × 27.4 cm (14.8 L), mini tower |
| Power | External brick (90 W or 130 W) | Internal 200 W PSU, IEC cord | Internal 260 W or 360 W PSU, IEC cord |
| Optical drive | None | Slim, optional | Slim, optional |
| PCIe slots | None | 2 low-profile | 4 full-height |
| SATA ports on board | 1 | **3** | 4 |
| RAM | 2× SO-DIMM | 4× DIMM | 4× DIMM |

**This machine:** The kernel reports "3/4 ports implemented" on the SATA controller, there's a slim DVD drive, and the chassis type is "Desktop", so it is **most likely the SFF (unverified)**. To confirm, measure it: an SFF is ~9 cm wide and a tower is ~15 cm.

### Service tag lookup
- The sticker is on the back or top of the chassis. The SFF and MT back-panel diagrams show a "Service tag" label.
- Windows (PowerShell): `Get-CimInstance Win32_BIOS | Select SerialNumber`. `wmic bios get serialnumber` is deprecated.
- Fedora: `sudo dmidecode -s system-serial-number`, or `sudo cat /sys/class/dmi/id/product_serial`.
- Enter it at <https://www.dell.com/support/home/>. You get the **original factory configuration** (CPU, RAM, drive, PSU wattage, heatsink part), drivers, BIOS and warranty status.
- Useful identifiers: `sudo dmidecode -s chassis-type`, `cat /sys/class/dmi/id/product_sku` (this box: `085A`).

---

## 2. Specifications by form factor

Source: Dell *Setup and Specifications* guides for each chassis (Rev A01/A02, 2021).

| Spec | Micro | SFF | MT (Tower) |
|---|---|---|---|
| Chipset | Intel Q370 | Intel Q370 | Intel Q370 |
| CPUs (official) | 8th gen **T (35 W)**: i3-8100T/8300T, i5-8400T/8500T/8600T, i7-8700T, Celeron G4900T, Pentium G5400T. **65 W** i3-8100…i7-8700 are also listed, but only with the 130 W adapter and the larger 65 W heatsink | 8th gen 65 W: i3-8100/8300, i5-8400/8500/8600, i7-8700 | Same as SFF |
| 9th gen (i7-9700 etc.) | **Not supported by Dell BIOS** (a modded BIOS exists) | **Not supported** | **Not supported** |
| RAM slots / max | 2× SO-DIMM, 32 GB (2×16) | 4× DIMM, 64 GB (4×16) | 4× DIMM, 64 GB (4×16) |
| RAM type / speed | DDR4-2666 non-ECC (runs at 2400 with i3) | same | same |
| M.2 storage | 1× M.2 2230/2280 (NVMe PCIe 3.0 x4 **or** SATA) | 1× M.2 2230/2280 (NVMe x4 or SATA) | 1× M.2 2230/2280 (NVMe x4 or SATA) |
| M.2 Wi-Fi | 1× 2230 (CNVi) | 1× 2230 | 1× 2230 |
| 2.5"/3.5" bays | 1× 2.5" | 2× 2.5" **or** 1× 3.5" (+ slim ODD) | 3.5" + 2.5" (+ slim ODD) |
| SATA ports | 1 | 3 (1 is Gen2 for the ODD) | 4 (1 is Gen2 for the ODD) |
| PCIe | none | 1× x16 (Gen3) + 1× x4 open-ended, **low-profile only** | 1× x16, 1× x16 (wired x4), 1× x1, 1× legacy PCI; full height |
| iGPU | UHD Graphics 630 | UHD 630 | UHD 630 |
| Native video | **2× DisplayPort 1.2** + optional flex port (VGA / DP / HDMI 2.0b / USB-C alt mode) | **2× DP 1.2** + optional flex port | **2× DP 1.2** + optional flex port |
| HDMI | **No native HDMI** unless the flex-port option was fitted. Use a DP++ passive DP→HDMI adapter (carries audio) | same | same |
| Max resolution | DP: 4096×2160 @ 60 Hz. Dell lists HDMI at 1920×1080 @ 60 via a passive adapter (1.4-level: 4K @ 30 in practice) | same | same |
| Front USB | 1× USB-C 3.1 Gen2 (10 Gb/s), 1× USB-A 3.1 Gen1 | 1× USB-C Gen2, 1× USB-A Gen1, 2× USB 2.0 | same as SFF |
| Rear USB | 4× USB-A 3.1 Gen1 (one with SmartPower On) | USB 3.1 Gen1 + USB 2.0 (SmartPower On) | 4× USB-A Gen1, 2× USB 2.0 |
| Audio | Front: universal headset jack + line-out. Realtek ALC3234, internal mono speaker | Front headset jack, rear line-out | same as SFF |
| S/PDIF out | **None** | **None** | **None** |
| Optional ports | Serial or Serial+PS/2 module | Serial, PS/2 ×2, SD reader, antenna SMA | Serial, PS/2 ×2, SD reader |
| LAN | Intel I219-LM GbE (WoL, vPro/AMT) | same | same |
| Wi-Fi option | Intel 9560 (Wi-Fi 5 + BT 5) or QCA61x4A | same | same |
| PSU | 90 W brick (T CPUs) / **130 W brick (65 W CPUs)** | **200 W** (Bronze or Platinum) | **260 W** (Bronze/Platinum) or **360 W** Gold |
| Biggest GPU that fits | none | Low-profile, **single-slot, ≤75 W slot power** (no PCIe power lead on a 200 W PSU). Examples: RX 6400 LP, Intel Arc A310 LP, RTX A1000/T1000 class. Dual-slot cards like the RTX A2000 are blocked by the PSU | Full-height; ~75 W slot-powered is safe on 260 W. With 360 W and an aux lead, a GTX 1650/RTX 3050 class card **(unverified)** |

**Notes on this system's iGPU (UHD 630):**
- It hardware-decodes H.264, HEVC 8/10-bit and VP9. **No AV1 decode.** That matters little at 1080p, but AV1 YouTube falls back to the CPU.
- For audio it can output multichannel LPCM and bitstream DD/DTS, as well as TrueHD/DTS-HD MA (driver dependent). The Denon only understands DD, DTS and LPCM.

---

## 3. Audio to the Denon AVR-3806

### The answer: HDMI, which you already have

The PC connects over HDMI into the AVR (the kernel sees an HDMI sink named **DENON-AVAMP**). I decoded the AVR's EDID live from `/sys/class/drm/card0-HDMI-A-2/edid`:

| Format the AVR advertises over HDMI | Channels | Sample rates | Bit depth |
|---|---|---|---|
| LPCM | **2** | 32–**192 kHz** (incl. 88.2/176.4) | 16/20/24 |
| LPCM | 6 (5.1) | 32–**96 kHz** | 16/20/24 |
| Dolby Digital (AC-3) | 6 | up to 48 kHz stream | — |
| DTS | 6 | — | — |

- The AVR-3806 has **HDMI 1.1** inputs (2 in, 1 out) that "accept multi-channel digital audio input". It has 24-bit/192 kHz DACs.
- **For stereo Qobuz, HDMI already delivers full 24/192 bit-perfect.** A USB→S/PDIF box would be a step sideways.
- **No Dolby TrueHD / DTS-HD / Atmos.** HDMI 1.1 predates them. For movies, let the player decode to multichannel LPCM (≤ 5.1 @ 96 kHz), or pass through core DD/DTS.
- The HDMI Audio setting on the AVR must be **"AMP"** (System Setup → Video Setup → HDMI In Assign). Otherwise the audio goes to the TV.
- The AVR ignores HDMI control: its manual says it "cannot be controlled by another device via the HDMI connector". **There is no CEC.**
- The AVR has only **two HDMI inputs**. The PC and the Xbox use both.
- Stay on HDMI cables ≤ 5 m, as the manual recommends.

### Alternative: USB → S/PDIF (only if HDMI becomes a problem)
- **The OptiPlex has no S/PDIF output on any chassis**, so this needs a USB device. Options: a USB DDC (digital-to-digital converter) such as the SMSL PO100-class (~$50–90), or a DAC with a digital out such as the Topping D10s (~$90–120) **(unverified prices)**. Avoid the Behringer UFO202 and similar: they top out at 48 kHz.
- The AVR-3806 has **2 coax + 5 optical inputs**. Denon doesn't state the maximum PCM rate on coax. Receivers of that era usually take **≤96 kHz** on S/PDIF **(unverified; 192 kHz on coax not confirmed)**, so cap the device at 96 kHz.
- S/PDIF only carries 2-channel PCM or DD/DTS bitstream. For 5.1 from games or movies over S/PDIF you'd need real-time encoding (Dolby Digital Live / DTS Connect), e.g. a Creative Sound Blaster X4-class USB card. HDMI avoids all of this.

### Windows setup
1. **Sound settings → Output → DENON-AVAMP (Intel Display Audio) → Properties**, or the legacy control panel `mmsys.cpl`:
   - **Configure speakers:** choose the layout you actually have (e.g. **5.1** for an Acoustimass 5-satellite + bass module setup). The EDID allows 7.1 speaker allocation but only 6-channel LPCM, so pick **5.1 or stereo**, not 7.1.
   - **Advanced → Default format:** 24-bit, 48000 Hz for everyday/system audio.
   - **Tick** "Allow applications to take exclusive control of this device" and "Give exclusive mode applications priority".
   - **Turn off audio enhancements** and Spatial sound. "Dolby Atmos for home theater" needs an Atmos receiver, which the 3806 isn't.
2. **Qobuz desktop app:**
   - Settings → Streaming quality: **Hi-Res, up to 24-bit/192 kHz** (needs a Studio/Sublime plan).
   - Click the **audio device button at the bottom right** → choose **DENON-AVAMP** → enable **Exclusive mode** (WASAPI Exclusive). Qobuz ranks ASIO or WASAPI Exclusive as best. Intel HDMI has no ASIO driver, so use WASAPI Exclusive.
   - Leave the app volume at 100% and use the AVR volume. Exclusive mode bypasses the Windows mixer and resampler, and the AVR's display should show the incoming sample rate.
3. **Movies from the PC:** in mpv, MPC-HC or Kodi, enable **passthrough for AC3 and DTS only**. Leave TrueHD, DTS-HD and E-AC3 off so the player decodes those to LPCM 5.1. The Denon's `AUTO` input mode shows DD/DTS/PCM correctly.
4. On the AVR, use **DIRECT/PURE DIRECT** for critical stereo listening. Whether Audyssey or the DSP resamples 176.4/192 kHz input is **(unverified)**.

### Linux (Fedora) + Qobuz

**Current state: not bit-perfect.** PipeWire's `clock.allowed-rates` is `[ 48000 ]`, so every 44.1/88.2/96/192 kHz track is resampled to 48 kHz before the Denon sees it.

**Fix: let PipeWire follow the source rate.**
```bash
mkdir -p ~/.config/pipewire/pipewire.conf.d
cat > ~/.config/pipewire/pipewire.conf.d/10-hifi-rates.conf <<'EOF'
context.properties = {
    default.clock.rate          = 48000
    # rates the Denon accepts for 2ch LPCM over HDMI (from its EDID)
    default.clock.allowed-rates = [ 44100 48000 88200 96000 176400 192000 ]
}
EOF
systemctl --user restart pipewire pipewire-pulse wireplumber
```
- PipeWire switches the graph rate when the Qobuz stream is the only one playing. It can't switch while another app, like a browser tab, holds the device at a different rate.
- **Keep the PipeWire sink volume and the app volume at 100%.** Software volume below 100% changes the samples.
- **Verify** while a hi-res track plays: `pw-top` (RATE column), or `cat /proc/asound/card0/pcm*p/sub0/hw_params | grep rate`. The AVR front panel should also show the rate.

**Qobuz clients on Linux.** There is no official Linux app.

| Option | What it is | Bit-perfect? | Notes |
|---|---|---|---|
| **Qobine** (what you use; Flathub `io.github.sofusa.qobine`) | GNOME client, fork of hifi.rs | Yes, via PipeWire once the rates fix above is in | Flatpak; outputs via the ALSA plugin → PipeWire |
| **QBZ** (`github.com/afonsojramos/qbz`) | Native Rust/Tauri client with PipeWire, ALSA and **ALSA Direct (hw: exclusive)** backends, 44.1–192 kHz switching, Qobuz Connect | Yes. Use the **RPM, not the Flatpak** (the sandbox limits PipeWire bit-perfect) | `sudo dnf install ./qbz-*.rpm`. Seeking in >96 kHz tracks is slow (10–20 s) |
| Strawberry | General player with a Qobuz plugin | Yes, with the rates fix | In Fedora repos |
| Web player (play.qobuz.com) | Browser | **No**: browsers cap at 48 kHz | Convenience only |
| Roon / Audirvana | Paid players with Qobuz integration. Roon Server runs on Linux; Audirvana Studio has a Linux core **(unverified current status)** | Yes | Only if you want library management or multi-room |
| qobuz-dl | Downloads **purchased** albums | n/a | Not streaming. Mind Qobuz's terms |
| mpd + upmpdcli | MPD with a Qobuz plugin (via upmpdcli) | Yes | For a headless or phone-controlled setup |

For guaranteed bit-perfect output that ignores PipeWire entirely, use QBZ's **ALSA Direct** backend to `hw:` the HDMI device. It blocks all other sound while playing.

---

## 4. Fixing "doesn't power AVR/TV on/off"

**Why it doesn't work:** Nothing in this chain speaks HDMI-CEC. The Intel iGPU has no CEC. The AVR-3806 manual explicitly says it can't be controlled over HDMI. The 2008 Vizio VS420LF1A manual makes no mention of CEC or RS-232 **(no CEC: unverified but very likely)**. So the PC has to "press the buttons" some other way.

### Options compared

| Option | Controls | Cost (2026) | Reliability | Verdict |
|---|---|---|---|---|
| **USB→RS-232 cable to the Denon** | AVR: power, input, volume, mute, surround mode, **plus status queries** | $15–25 (FTDI chipset) | Excellent: discrete commands with feedback | **Use this for the AVR** |
| **Broadlink RM4 mini** (Wi-Fi IR blaster) | TV (and the AVR as a backup) | $25–35 | Good. IR is one-way, but discrete Vizio codes exist | **Use this for the TV** |
| ESPHome IR blaster (ESP32 + IR LED, e.g. OpenIRBlaster) | TV | $10–25 DIY | Good, local-only, native in Home Assistant | Great if you run Home Assistant |
| USB IR transmitter + LIRC (FTDI-based, irblaster.info) | TV | $20–40 | Fine on Linux, awkward on Windows | Only for a Linux-only setup |
| Pulse-Eight USB-CEC adapter | Nothing here | ~$45 | — | **Useless**: neither the AVR nor the TV speaks CEC |
| Smart plug on the AVR/TV | Hard power | $10–20 | Poor. The TV returns to standby, the AVR's power-restore behavior is **(unverified)**, and cutting mains to an amp is crude | Not recommended |
| FLIRC | — | — | Receive-only | Not a transmitter |

### Denon RS-232 (confirmed from Denon's protocol document)
The AVR-3805/3806-era protocol (Ver. 4.0):
- DB-9 **female** on the AVR, **DCE, straight-through**, **9600 baud, 8 data bits, no parity, 1 stop bit**, no flow control. Use a **straight** (not null-modem) USB-serial cable with a DB-9 male end. FTDI-chipset cables are the least trouble.
- Commands are ASCII terminated with CR (`\r`): `PWON` / `PWSTANDBY` (power), `ZMON` / `ZMOFF` (main zone), `SIDVD` / `SITV` / `SIDBS/SAT` / `SIVCR-1` … (input), `MVUP` / `MVDOWN` / `MV45` (volume, 80 = 0 dB), `MUON` / `MUOFF`. Append `?` to query, e.g. `PW?` → `PWON` or `PWSTANDBY`, and `SI?`.
- Leave the AVR's front **ON/STANDBY switch in the operating position**. RS-232 can only wake it from standby, not from the main power switch.
- The command set for the 3806 is assumed identical to the 3805 document (same generation). A user on the Ezlo forum confirmed power, mute and volume working on an AVR-3806 over direct RS-232. **Input names: (unverified), check with `SI?`.**

**Linux** (add yourself to `dialout`: `sudo usermod -aG dialout $USER`):
```bash
#!/usr/bin/env bash
# /usr/local/bin/denon  — usage: denon PWON | denon PWSTANDBY | denon 'SI?'
PORT=${DENON_PORT:-$(ls /dev/serial/by-id/usb-FTDI_* | head -1)}
stty -F "$PORT" 9600 cs8 -cstopb -parenb -crtscts raw -echo
exec 3<>"$PORT"                      # keep port open so the reply isn't lost
printf '%s\r' "$1" >&3
if [[ "$1" == *\? ]]; then IFS= read -r -d $'\r' -t 0.5 reply <&3 && echo "$reply"; fi
exec 3>&-
```

**Windows** (PowerShell, e.g. `C:\Scripts\denon.ps1`):
```powershell
param([string]$Cmd = "PWON", [string]$Port = "COM3")
$p = New-Object System.IO.Ports.SerialPort $Port,9600,None,8,One
$p.NewLine = "`r"; $p.ReadTimeout = 500; $p.Open()
$p.Write("$Cmd`r")
if ($Cmd.EndsWith("?")) { try { $p.ReadLine() } catch {} }
$p.Close()
```

### Vizio TV via Broadlink RM4 mini
- Set it up once with the Broadlink app (you can then block its cloud access). Control it locally with **python-broadlink** (`pip install broadlink`, `broadlink_cli`) from either OS, or with Home Assistant's Broadlink integration.
- **Discrete Vizio power codes** (Pronto, published by Just Add Power). I decoded them as NEC address `0x04`: **ON = command `0x2A`**, **OFF = command `0x25`** (toggle is `0x08`). Whether a 2008 VS420LF1A honors the discrete codes is **(unverified)**. Test them. If they fail, learn the toggle from the Vizio remote, and use the AVR's `PW?` state to decide when to send it.

### Triggers: when to fire the commands
**Windows:** Task Scheduler → Create Task → "Run whether user is logged on or not":
- **On wake:** trigger *On an event*, Log `System`, Source `Microsoft-Windows-Power-Troubleshooter`, **Event ID 1** → `denon.ps1 PWON`, then `SI<pc input>`, then the TV ON code.
- **On sleep:** Log `System`, Source `Kernel-Power`, **Event ID 42** → `PWSTANDBY` + TV OFF. This is best-effort: Windows may suspend before the task finishes. Serial writes take milliseconds, so it usually works.
- **On shutdown:** Event `User32` **1074**, or a gpedit shutdown script (Windows Pro only).
- **At logon or startup:** a normal task trigger.
- **Don't kill the Xbox:** before sending `PWSTANDBY`, query `SI?`, and only power off if the AVR is still on the PC's input.

**Fedora:** a systemd sleep hook. Executables in `/usr/lib/systemd/system-sleep/` get `pre|post` and `suspend|hibernate|…`:
```bash
#!/bin/sh
# /usr/lib/systemd/system-sleep/50-avr   (chmod +x)
case "$1" in
  pre)  [ "$(/usr/local/bin/denon 'SI?')" = "SIDVD" ] && /usr/local/bin/denon PWSTANDBY ;;  # adjust input
  post) /usr/local/bin/denon PWON; sleep 3; /usr/local/bin/denon SIDVD ;;
esac
```
Add a oneshot unit with `ExecStart=` (boot) and `ExecStop=` (shutdown) for full power-on/off coverage.

**Recommended build:** FTDI USB-serial cable to the Denon, plus a Broadlink RM4 mini for the TV, plus scripts on both OSes. If you later run **Home Assistant**, move the serial port to an ESP32 + MAX3232 running ESPHome (the AVR becomes network-controllable from anywhere) and build "Watch Xbox / Listen to music / PC" scenes there.

---

## 5. Fixing "slow"

The CPU is not the bottleneck: the i7-8700 is the fastest official CPU for this board. What's slow:

| Cause | Evidence | Fix | Cost |
|---|---|---|---|
| **Fedora runs from a USB SSD at 5 Gb/s** | `Kingston XS1000` at 5000 Mb/s over UAS, so ~400–450 MB/s at best, with USB latency and LUKS on top | Move Fedora to an **internal NVMe** (PCIe 3.0 x4, ~3,000+ MB/s). As a quick win, plug the XS1000 into the **front USB-C (10 Gb/s Gen2)** port if its cable allows. Only the front Type-C is Gen2 | $0 / NVMe price |
| **Windows on a nearly full 256 GB SATA SSD** | SU800 is a DRAM-less-class SATA drive, slow once full | Move Windows to a bigger SSD, or keep it and move data off | see Storage |
| **16 GB RAM** | 10 GiB used, ~5 GiB available while browsing plus Qobuz; dev tools, containers and a browser will swap to zram | **32 GB** (2×16 GB DDR4-2666). Up to 64 GB on SFF/MT. Keep dual-channel (matched pairs) | ~$60–120 for 2×16 GB used/new (2026, volatile) |
| Windows bloat | — | Uninstall OEM junk and startup items, turn off the Widgets/Copilot/Start suggestions/indexing of big folders; `winget upgrade --all`. Avoid "debloat" scripts that strip Defender or Update. Consider a clean install of Windows 11, which officially supports the i7-8700 (8th gen) and TPM 2.0. **Windows 10 support ended 14 Oct 2025** | $0 |
| Fedora extras | btrfs + LUKS on USB | Internal NVMe; keep `zram` (already on) | $0 |

**CPU upgrade:** not worth it. Dell never shipped 9th-gen microcode for the 7060, so an i7-9700 won't POST on stock BIOS 1.32.0. A community-modded BIOS adds 9th-gen microcode (reported working on a 7060 Micro). It gains ~15–20% multi-thread for real brick risk, with no Secure Boot/Dell update path afterwards. **Not recommended.**

**Realistic expectations after NVMe + 32 GB:** Fedora boots and builds feel like a modern mid-range desktop. Geekbench-class single-thread is roughly 60–70% of a 2025 Ryzen 7 **(unverified estimate)**. Heavy parallel compiles are fine on 12 threads. Gaming on the UHD 630 is not a thing, which is what the Xbox is for.

---

## 6. Fixing "small SSD"

### The plan (separate drives, no bootloader fights)

| Drive | Where | Contents |
|---|---|---|
| **New 1–2 TB NVMe** | Internal M.2 2280 slot | **Fedora** (clone the XS1000, or fresh install and restore /home) |
| ADATA SU800 256 GB → or a new 1 TB SATA SSD | 2.5" bay | **Windows** (clone up if you replace it) |
| Kingston XS1000 | External | Freed up for backups (btrfs send, Timeshift/Snapper, Windows File History) |

Each OS gets its **own EFI System Partition on its own drive**, as today (Fedora's ESP lives on the XS1000 and Windows' on `sda1`). Windows updates then can't clobber GRUB. Use **F12** to pick an OS, or leave Fedora's GRUB first and let `os-prober` or a custom entry chainload Windows.

**First, open the case and check the M.2 slot.** It's next to the CPU/RAM on the SFF.
- If the **SU800 is a 2.5" drive**, the M.2 slot is free: add the NVMe there.
- If the **SU800 is an M.2 SATA stick**, it occupies the only M.2 slot. Clone Windows to a **2.5" SATA SSD** in the bay (you need a Dell SATA data + power cable if none is fitted; SFF part numbers vary, **(unverified)**), then put the NVMe in the M.2 slot.
- SFF alternative: an **M.2-to-PCIe x4 low-profile adapter** in the x4 slot adds a second NVMe (~$15). Booting from it on the 7060 UEFI is **(unverified)**, so use it as a data drive only.

### Drive picks (PCIe 4.0 drives run fine at Gen3 x4 speeds here)

| Use | Model class | 2026 price (rough) |
|---|---|---|
| Fedora NVMe | WD Black SN7100 / Crucial P310 / Samsung 990 EVO Plus / Kingston NV3, 1–2 TB | 1 TB ~$90–150, 2 TB ~$180–300 |
| Windows 2.5" SATA | Crucial MX500 / Samsung 870 EVO, 1 TB | ~$90–140 |

Avoid QLC for the dev drive if you do heavy builds. Any TLC Gen3/Gen4 drive saturates this slot (PCIe 3.0 x4 ≈ 3.5 GB/s).

### Cloning
- **Fedora (LUKS + btrfs):** Easiest is a `dd` or Clonezilla image of the whole XS1000 onto the NVMe, then grow partition 3, `cryptsetup resize`, and `btrfs filesystem resize max /`. Alternatively, do a fresh Fedora install on the NVMe and `btrfs send/receive` or rsync `/home`. Then remove the old Fedora boot entry with `efibootmgr -b XXXX -B`.
- **Windows:** Macrium Reflect Free has been discontinued, so use **Clonezilla**, Rescuezilla, or the free tool from the SSD vendor (Samsung Data Migration, Acronis for Crucial/WD). Do it from a live USB.
- Controller is in **AHCI mode** (already the case). **Never switch to "RAID On"**: Linux can't see NVMe in Intel RST RAID mode. If a future Windows reinstall is in RAID On, switch to AHCI using `bcdedit /set {current} safeboot minimal` → BIOS → AHCI → boot → `bcdedit /deletevalue {current} safeboot`.

---

## 7. Fixing "loud fan"

**What the BIOS offers:** Unlike newer OptiPlex models, the 7060 BIOS (per Dell's manual) has **no Thermal Management "Quiet/Cool/Optimized/Ultra Performance" setting**. The only fan item is **"Fan Control Override"**, which forces the fan to full speed, so leave it **off**. BIOS 1.32.0 is already the latest; an earlier release fixed "CPU fan erroneously spun at max speed on boot". Some 7060 owners report the fan surging to 100% for a few seconds every ~10 minutes with no fix from Dell.

**What makes it loud:** an **i7-8700 (65 W TDP, 122 W PL2 turbo)** in a small SFF cooler. It is quiet at idle (~890 RPM here) and ramps hard during builds or turbo.

| Fix | How | Effect | Cost |
|---|---|---|---|
| **Dust** | Power off and unplug. Compressed air through the heatsink fins, the CPU fan, the **PSU grille** (the SFF PSU has its own fan) and the front intake | Often the whole fix on a 7-year-old box | $0–10 |
| **Repaste** | Remove the heatsink shroud; clean with IPA; apply Arctic MX-4/MX-6 or Noctua NT-H2 | 5–15 °C on old dried paste | ~$10 |
| **Cap CPU power (Linux)** | Set PL2 = PL1 and lower PL1, e.g. 45 W: `echo 45000000 \| sudo tee /sys/class/powercap/intel-rapl:0/constraint_0_power_limit_uw` and `…constraint_1…` (make persistent with a systemd unit). `thermald` is already active | Loses ~10–15% all-core, turbo still on for bursts; big noise drop | $0 |
| **Cap CPU power (Windows)** | Power Options → Processor power management → **Maximum processor state 99%** (disables turbo, ~3.2 GHz). Or use **ThrottleStop** to set PL1/PL2 ≈ 45–55 W | Same | $0 |
| Disable Turbo in BIOS | Performance → Intel TurboBoost | Dell's own suggestion. Crude; affects both OSes | $0 |
| **Undervolting** | Intel XTU/ThrottleStop/`intel-undervolt`. Most Dell BIOSes from 2020 on lock voltage control after Plundervolt (CVE-2019-11157) | **Probably locked on 1.32.0 (unverified).** Power limits are the practical lever | $0 |
| **i7-8700T swap** | 35 W T-series part, same socket | Much quieter, ~25% slower multi-thread | ~$60–90 used |
| **Replace fan/heatsink** | Dell's SFF uses a proprietary shroud + heatsink. Buy the **65 W-rated** Dell heatsink/fan assembly for the 7060 SFF (listings cite KGWT4/3CWF9, **(unverified)**) if the fan bearing is rattling | Fixes a noisy bearing | ~$20–40 |
| PSU noise | If the whine or hum is from the PSU (SFF 200 W / MT 260 W), replace it with the same Dell part; the SFF can't take an ATX PSU | Only if the PSU is the source | ~$30–50 used |

**Linux fan monitoring:** the `dell_smm_hwmon` driver reads fan RPM and temperatures (`sensors`). The kernel has a quirk entry for this model because its BIOS errors on fan-state queries, so **manual fan control from Linux isn't reliable**. Control heat (power), not the fan.

---

## 8. Fedora specifics

- **Current layout:** Fedora sits on the external Kingston with its own ESP (`/boot/efi` sdb1), `/boot` ext4, and LUKS2 → btrfs `/` + `/home`. The UEFI order is **Fedora (shimx64.efi) first**, then Windows Boot Manager, with a 1 s timeout.
- **F2** = BIOS setup, **F12** = one-time boot menu (pick Fedora or Windows, or BIOS Flash Update). The Dell manual also says F12 for setup in places.
- **Secure Boot is currently off.** Fedora supports Secure Boot out of the box (signed shim + kernel), so you can turn it on after the NVMe move. The exceptions are out-of-tree modules (NVIDIA, VirtualBox), which need MOK enrollment. Dell's generic Linux KB says "Secure Boot off", which is overly conservative for Fedora. Turning it on also helps Windows 11 security features.
- **Firmware updates via fwupd/LVFS:** `fwupdmgr refresh && fwupdmgr get-updates`. Caveats from the fwupd tracker:
  - LVFS has lagged Dell for this model (issues #202/#232 note 1.32.0 missing on LVFS).
  - fwupd BIOS updates on the 7060 **don't apply if no display is attached**.

  You're already on **1.32.0**, so nothing is pending. Otherwise use Dell's `.exe` from Windows or the **F12 → BIOS Flash Update** menu with the file on a FAT32 USB.
- **Dual-boot hygiene:** keep each OS on its own disk and ESP. Windows fast startup/hibernation locks NTFS, so **disable Fast Startup** (`powercfg /h off`) if Fedora mounts "Crash's Main Drive" read-write.
- **Clock:** Windows uses local time in the RTC. Either `timedatectl set-local-rtc 1` on Fedora, or set Windows `RealTimeIsUniversal=1`.

---

## 9. Relevant BIOS settings

(System Setup → the category shown, per Dell's 7060 manual)

| Setting | Where | Recommended | Why |
|---|---|---|---|
| **AC Recovery** | Power Management | **Last Power State** (default Power Off) | Comes back on after an outage if it was on |
| **Auto On Time** | Power Management | Optional | Daily scheduled power-on |
| **Deep Sleep Control** | Power Management | **Disabled** (default) | Deep sleep cuts USB/NIC power in S4/S5, which **breaks Wake-on-LAN and USB wake** |
| **Wake on LAN/WWAN** | Power Management | **LAN Only** | Wake the PC from a phone, Home Assistant or the other OS (`wakeonlan <MAC>`). Also enable WoL in the Windows NIC driver and Fedora (`nmcli c mod <con> 802-3-ethernet.wake-on-lan magic`) |
| **USB Wake Support** | Power Management | Enabled | Keyboard/mouse wake from sleep |
| **Block Sleep** | Power Management | Off | — |
| Intel Speed Shift / SpeedStep / C-States | Power Mgmt / Performance | Enabled | Lower idle power and noise |
| Intel TurboBoost | Performance | Enabled (cap with power limits instead) | See [Fan](#7-fixing-loud-fan) |
| **SATA Operation** | System Configuration | **AHCI** | Linux sees NVMe |
| Fast Boot | POST Behavior | Minimal | Faster boot. Use F12 to change OS |
| Secure Boot | Secure Boot | Enable after migrating (see Fedora) | — |
| **Fan Control Override** | Power Management | **Off** | On = full-speed fan |
| Power button behavior | *OS setting*, not BIOS | Windows: "When I press the power button: Sleep". Fedora: `HandlePowerKey=suspend` in `/etc/systemd/logind.conf` | Sleep/wake then triggers the AVR/TV scripts |
| Rear USB 2.0 "SmartPower On" | Hardware | Plug the keyboard here | Keyboard can wake it from S3/S4 |

---

## 10. Alternatives and upgrade path

**Recommendation: keep the OptiPlex and do the ~$200–350 refresh** (NVMe, 32 GB RAM, repaste, power caps, serial + IR control). It stays a strong Fedora dev box and a perfectly good music/HTPC source. The HDMI 1.1 AVR and 1080p TV cap the rest of the chain anyway.

Consider a new box only if you want **silence** or **4K/AV1** (e.g. after a TV/AVR upgrade):

| Option | CPU | Pros | Cons | 2026 price (rough) |
|---|---|---|---|---|
| Keep OptiPlex + refresh | i7-8700 6C/12T | Already owned; 4 DIMM slots, SATA bays, serial option | Fan under load; no AV1; no native HDMI | $200–350 in parts |
| Beelink EQ14 / similar | Intel N150 (4C) | Silent-ish, 6–10 W idle, AV1 decode, HDMI 2.0 | **Far slower than the i7-8700 for dev**; single-channel RAM | ~$190–230 |
| N305 mini PC (Beelink EQ13 etc.) | i3-N305 (8 E-cores) | Quiet, low power, dual NIC variants | Still slower than the i7-8700 multithreaded in many cases | ~$250–350 |
| Ryzen 7 8745H/HS mini PC (Minisforum UM870, Beelink SER8, etc.) | 8C/16T Zen 4, Radeon 780M | ~2× the i7-8700; HDMI 2.1, 4K/AV1, decent iGPU | Small fans can be loud under long loads. DDR5 + SSD prices inflated in 2026 | ~$450–650 |
| Used OptiPlex 7070/7080/7090 SFF | i7-9700 / i7-10700 | Same ecosystem, cheap | Same fan story, same lack of HDMI | ~$120–250 |

A good split if budget allows: a **silent N150 mini PC as a dedicated HTPC/Qobuz player** in the rack, with the OptiPlex moved to the desk as the Fedora dev machine. This also frees the PC from having to be on for music.

### A note on 2026 prices
DRAM and NAND contract prices have been rising through 2026 (AI data-center demand). A 2 TB NVMe that was $120–150 in 2025 runs $180–480 now depending on model, and DDR4/DDR5 kits are well above 2024 prices. Buy DDR4 used or refurbished for this machine, and check price-history sites before buying.

---

## 11. How it fits this system

```
            ┌──────────── RS-232 (USB-serial) ─────────────┐
            │                                              ▼
 OptiPlex 7060 ──DP→HDMI──► Denon AVR-3806 HDMI IN ──HDMI OUT──► Vizio VS420LF1A (1080p)
 (Win / Fedora)             ▲    (audio: "AMP")                   ▲
   │  Wi-Fi/LAN             │                                     │ IR
   └──► Broadlink RM4 mini ─┴──────────────── IR ─────────────────┘
 Xbox One ──HDMI──► Denon HDMI IN #2
 Denon speaker outs ──► Bose Acoustimass
```

- **Role:** Qobuz source (bit-perfect up to 24/192 stereo over HDMI), occasional movie source (5.1 LPCM ≤ 96 kHz or DD/DTS), dev box, and the **brain for the AVR/TV power automation**.
- **Input budget:** the AVR has only **2 HDMI inputs**, taken by the PC and the Xbox. Anything new (streaming stick, future console) needs an HDMI switch or a new AVR.
- **Xbox interplay:** the power scripts should check `SI?` so the PC going to sleep doesn't turn off the AVR mid-Xbox session.
- **Sound/movie-reactive light (future):** the PC is the natural place to drive it:
  - **Music-reactive:** **LedFx** (Windows/Linux) analyzes PC audio and streams effects to **WLED** (ESP32 LED controllers) over E1.31/DDP/UDP. WLED's built-in **audio-reactive** mode works standalone with an ESP32 + I2S mic (e.g. INMP441), which also reacts to the Xbox. That makes it the most system-wide option.
  - **Movie/ambient (screen-reactive):** **HyperHDR** or **Hyperion.ng** capture the PC's screen (or an HDMI capture of *any* source via a USB grabber + HDMI splitter) and drive WLED or Adalight strips. **Prismatik** (Windows) is simpler for PC-only ambilight.
  - **SignalRGB** (Windows) can drive WLED devices with screen-ambience and audio effects. Philips Hue Sync (desktop) works if you go Hue.
  - Best whole-system choice: **ESP32 + WLED with an I2S mic** for sound-reactive light that works for every source. Add HyperHDR on the PC later if you want screen-matched color for PC video.

---

## Sources

- Dell, *OptiPlex 7060 Small Form Factor Setup and Specifications Guide* (D11S): <https://dl.dell.com/topicspdf/optiplex-7060-desktop_specifications2_en-us.pdf>
- Dell, *OptiPlex 7060 Micro Setup and Specifications Guide* (D10U): <https://dl.dell.com/topicspdf/optiplex-7060-desktop_specifications3_en-us.pdf>
- Dell, *OptiPlex 7060 Tower Setup and Specifications Guide* (D18M): <https://dl.dell.com/topicspdf/optiplex-7060-desktop_specifications_en-us.pdf>
- Dell, OptiPlex 7060 spec sheet: <https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/OptiPlex_7060_Spec_Sheet.pdf>
- Dell, SFF service manual (M.2 install): <https://www.dell.com/support/manuals/en-us/optiplex-7060-sff/opti_7060_sff_service_manual/installing-the-m2-pcie-ssd?guid=guid-a395ed6c-a717-40ef-9a4c-942e43860790&lang=en-us>
- Dell, OptiPlex 7060 System BIOS: <https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=08yw8>
- Dell, Recommended BIOS settings for Linux: <https://www.dell.com/support/kbdoc/en-us/000123462/recommended-bios-settings-for-your-linux-system>
- Dell Community, 7060 SFF i7-9700 upgrade thread: <https://www.dell.com/community/en/conversations/optiplex-desktops/optiplex-7060-sff-upgrade-from-i5-8500-to-i7-9700/647f8421f4ccf8a8de2fdd92?page=2>
- Bios-mods forum, 7060 9th-gen modded BIOS: <https://www.bios-mods.com/forum/Thread-Optiplex-7060-SFF-9th-Generation-Intel-Core-support>
- Dell Community, 7060 fan noise: <https://www.dell.com/community/en/conversations/optiplex-desktops/optiplex-7060-fan-noise/647f81dbf4ccf8a8de090856>
- Dell Community, 7060 SFF fan surging: <https://www.dell.com/community/en/conversations/optiplex-desktops/7060-sff-fans-continue-to-randomly-spin-at-max-speed/647f80adf4ccf8a8def5cd3d>
- Dell Community, RTX A2000 in OptiPlex SFF: <https://www.dell.com/community/en/conversations/optiplex-desktops/can-i-install-rtx-a2000-on-dell-optiplex-7000-sff/647fa3d5f4ccf8a8de9d1a5c>
- Linux kernel patch, dell-smm-hwmon: add OptiPlex 7060: <https://lkml.iu.edu/2406.3/07989.html>
- fwupd firmware-dell issues #202 / #232 / #127: <https://github.com/fwupd/firmware-dell/issues/202>, <https://github.com/fwupd/firmware-dell/issues/232>, <https://github.com/fwupd/firmware-dell/issues/127>
- Hardware Corner, OptiPlex 7060 SFF specs and upgrades: <https://www.hardware-corner.net/desktop-models/Dell-OptiPlex-7060-SFF/>
- ServeTheHome, OptiPlex 7060 Micro at 65 W TDP: <https://www.servethehome.com/dell-optiplex-7060-micro-tinyminimicro-at-65w-tdp-cpu-overview/3/>
- Denon, AVR-3806 information sheet (HDMI 1.1, 24/192 DAC, RS-232C): <https://assets.denon.com/documentmaster/us/avr3806.pdf>
- Denon, AVR-3806 owner's manual: <https://www.denon.com/on/demandware.static/-/Library-Sites-denon_apac_shared/default/dwd8318111/downloads/archived/avr-3806-owners-manual-en.pdf>
- Denon, AVR/AVC control protocol Ver. 4.0 (AVR-3805 RS-232C): <https://assets.denon.com/documentmaster/uk/139_avr-3805_rs232.pdf>
- Ezlo Community, AVR-3806 RS-232 control: <https://community.ezlo.com/t/controlling-denon-avr-3806-via-startech-rs232-1-serial-to-ethernet-adapter/176493>
- Home Assistant Community, AVR-3806 RS232: <https://community.home-assistant.io/t/denon-avr-3806-rs232/306382>
- Just Add Power, Vizio discrete IR codes: <https://support.justaddpower.com/kb/article/250-vizio-ir-control/>
- Qobuz Magazine, desktop playback modes: <https://www.qobuz.com/us-en/magazine/story/Qobuz-Vous/The-playback-modes-of-Desktop179419/>
- Qobuz Help, Hi-Res on PC: <https://help.qobuz.com/en/articles/10202-how-do-i-experience-hi-res-on-pc>
- Qobine (Flathub / GitHub): <https://flathub.org/en/apps/io.github.sofusa.qobine>, <https://github.com/SofusA/qobine>
- QBZ native Qobuz client: <https://github.com/afonsojramos/qbz>
- Korben, Qobuz bit-perfect on Linux: <https://korben.info/en/qobuz-bit-perfect-linux.html>
- systemd-sleep(8): <https://www.man7.org/linux//man-pages/man8/systemd-sleep.8.html>
- OpenIRBlaster (ESPHome): <https://github.com/jaycollett/OpenIRBlaster>
- irblaster.info FTDI USB IR blasters for LIRC: <https://www.irblaster.info/usb_blaster.html>
- Intel Community, UHD 630 HDMI bitstream: <https://community.intel.com/t5/Graphics/HD630-audio-bitstream-limitations-Cannot-get-all-audio-options/td-p/1310505>
- PCWorld, best mini PC deals Sept 2026: <https://www.pcworld.com/article/2999556/best-mini-pc-deals-top-picks-for-performance-gaming-and-more.html>
- Botmonster, mini PCs N150 vs N305 vs Ryzen (2026): <https://botmonster.com/self-hosting/best-mini-pcs-home-lab-2026/>
- Tech-Insider, SSD prices and the 2026 NAND shortage: <https://tech-insider.org/ssd-prices-nand-shortage-2026/>
- Local system inspection (2026-09-24): `/sys/class/dmi/id`, `lsblk`, `lspci`, `efibootmgr`, EDID of `card0-HDMI-A-2`, `wpctl`, `pw-metadata`, `dell_smm` hwmon, RAPL powercap.
