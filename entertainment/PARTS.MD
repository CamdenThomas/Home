# Parts Buying Guide: Home Entertainment System

A list to buy from over time. Nothing here needs buying today. The **free fixes** (Xbox on HDMI at 5.1 uncompressed, the Bose rewire and Audyssey rerun, Vizio speakers off, PipeWire bit-perfect, dusting the OptiPlex) come first and are covered in [system-overview.md](reference/entertainment/system-overview.md#6-upgrade-roadmap-order-matters).

How to read this page:
- **Prices** are US street prices checked around **24 September 2026**. They move a lot. **2026 is a bad year for memory, SSDs and anything with RAM in it:** DRAM and NAND shortages pushed 2 TB SSDs up roughly 85–150% since late 2025, and DDR4 kits roughly doubled. Streaming boxes and mini PCs rose too; the Google TV Streamer went from $99.99 to $149.99 on 31 Aug 2026. **Used and refurbished is where the value is this year.**
- **"unverified"** means we couldn't confirm it from a store page or primary source. Check before buying.
- Each section says **which complaint it fixes**. The complaints are in [README.md](README.md).

---

## 1. Buy order when money allows

Highest impact per dollar first.

| # | Buy | Approx. cost | Fixes | Depends on / notes |
|---|---|---|---|---|
| 1 | **Toslink→RCA DAC** (you already own the Toslink and RCA cables) ([§3.1](#31-cheapest-fix-optical-to-analog-dac-for-a-true-2-channel-path)), **your pick:** [generic USB-powered Toslink/coax→RCA converter (Walmart)](https://www.walmart.com/ip/Digital-Optical-Toslink-SPDIF-Coax-Analog-Audio-Converter-Adapter-Fiber-Cable-1-x-Digital-Analog-Audio-Converter-Adapter-1-x-USB-Power-Cable-58cm-len/17348966041?athAsset=eyJhdGhjcGlkIjoiMTczNDg5NjYwNDEiLCJhdGhzdGlkIjoiQ1M0Nzh%2BQ1MwMDQiLCJhdGhlZSI6eyJhIjoyMC4wLCJiIjo5ODAuMCwidyI6MC4wMjA3ODcxOTYwMDc0ODcxNywibCI6MC41fSwiYXRocG9zYiI6IjI4IiwiYXRoYW5jaWQiOiIxNzExMTM1NTU1NCIsImF0aHJrIjowLjB9&athena=true&ssp=TQIX) | **~$15–20** | Xbox: real **Pro Logic IIx for stereo** without touching Xbox menus | None. The Xbox's HDMI audio stays on 5.1 uncompressed. The Xbox optical output runs through the DAC into the analog inputs of the Xbox source on the Denon. |
| 2 | **USB→RS-232 cable, genuine FTDI, straight-through, male DB9** ([§2.4](#24-power-control-usbrs-232-cable-for-the-denon)) | $14–40 | PC can power the **Denon** on and off, switch inputs, and toggle input mode | Avoid null-modem cables. Scripts are in [OptiPlex §4](reference/entertainment/dell-optiplex-7060.md#4-fixing-doesnt-power-avrtv-onoff). |
| 3 | **IR blaster** (Seeed XIAO Smart IR Mate $12, or Broadlink RM4 mini $26) ([§2.5](#25-power-control-ir-blasters-for-the-vizio)) | $12–26 | PC or Home Assistant can power the **Vizio** | Buy together with #2 for one-command power on/off. |
| 4 | **Thermal paste + compressed air** ([§2.3](#23-cooling-fan-noise)) | $6–15 | **Loud fan** | Also cap CPU power (free). |
| 5 | **Streaming box that switches formats with the content** ([§3](#3-streaming-box-the-real-fix-for-the-xbox-stereo--51-problem)) | $50–150 | Xbox stereo/5.1: removes the switching entirely for streaming | Optional once #1 works. Keep the Xbox for games. |
| 6 | **1 TB TLC NVMe for Fedora** ([§2.1](#21-nvme-ssd-for-fedora)) | $100–190 | **Slow** and **small SSD** | Open the case first to check the M.2 slot is free. |
| 7 | **Real subwoofer** that plays cleanly to 200–250 Hz ([§6](#6-subwoofers-replacing-the-bose-bass-module)) | $300–600 (used Rythmik/SVS), $600 new | Bose: **clean AVR-only bass** | Carries over to any future speakers and AVR. |
| 8 | **32 GB DDR4** ([§2.2](#22-ram-32-gb-ddr4)) | ~$126 used, $180–235 new | **Slow** (dev tools, containers) | Wait for prices to fall if you can. |
| 9 | **Universal remote**: SofaBaton U2 $70 or X1S $180 ([§10](#10-remotes-and-control)) | $70–180 | One-button "watch/listen/off" | Most useful after #2 and #3 are working. |
| 10 | **Reactive light**: Govee TV Backlight 3 Lite 40–50" ([§9](#9-reactive-light)) | $53–55 | Wants a reactive light | Camera-based, so no HDMI changes. |
| 11 | *Later, optional:* **always-on Home Assistant host** ([§10.4](#104-always-on-automation-host-later-optional)) | $12–150 | Automation that works even while the OptiPlex is off or booted into the other OS | Only if automation outgrows the PC scripts. |
| 12 | **TV + AVR together** ([§7](#7-tvs), [§5](#5-av-receivers)) | $1,300–2,500 | No 4K/HDR, no CEC/eARC, speaker bar, clunky Denon UI, no Atmos | **Buy both together.** A 4K TV behind the HDMI 1.1 Denon shows no 4K from sources routed through the Denon. A new AVR on the old Vizio gains no picture quality. See [Vizio §9.4](reference/entertainment/vizio-vs420lf1a.md#94-earccec-and-the-old-denon-pitfalls). |
| 13 | **Speakers** ([§8](#8-speaker-packages)) | $180–1,400 | Bose cubes' sound (the 200 Hz handoff, no treble above ~13 kHz) | After the AVR, so the new AVR's room EQ runs on the new speakers. The sub from #7 is reused. |

**Dependencies at a glance**
- #2 + #3 go together (Denon and TV power).
- #12: buy the TV and AVR together, or buy the TV first and plug 4K sources straight into it, with TV optical going to the Denon.
- #13 comes after #7 and #12.
- #5 isn't needed if #1 is good enough for you, or once #12 is done and you use the new TV's apps over eARC.
- The **Xbox Series X|S** does **not** fix the audio problem ([§4](#4-game-consoles)).

---

## 2. PC (Dell OptiPlex 7060) upgrades

Keep the OptiPlex. At 2026 prices an NVMe drive plus used RAM costs about $316, which is less than a new N150 mini PC and much faster ([OptiPlex §10](reference/entertainment/dell-optiplex-7060.md#10-alternatives-and-upgrade-path)).

**Form factor first:** the SFF (~9 cm wide) and tower take desktop **DIMMs**. The Micro takes laptop **SO-DIMMs**. This machine is most likely SFF ([OptiPlex §1](reference/entertainment/dell-optiplex-7060.md#1-identify-your-form-factor)).

### 2.1 NVMe SSD for Fedora

The slot is PCIe 3.0 x4, so any Gen4 drive tops out at ~3.5 GB/s here. That's fine. Prefer **TLC** for a dev drive. Prices are from cheapestssd.com, 24 Sep 2026.

| Drive | NAND | 1 TB | 2 TB | Why / caveats |
|---|---|---|---|---|
| **SK hynix Platinum P41** | TLC, DRAM | **$99.99** (may be limited/third-party stock) | ~$159 (unverified) | Best value **if** actually in stock at that price. Excellent controller. |
| **WD Black SN7100** | TLC | $191 | $330 (Prime Day low $243) | Safe default. Efficient and cool. |
| Samsung 990 EVO Plus | TLC | $208–240 | $370 | Fine but pricey this year. |
| Kingston NV3 | QLC / varies | $150 (cheapest 1 TB) | $289 | Budget. NAND varies by batch; weaker under sustained writes. |
| Crucial P310 | QLC | $172 | $252 | 2 TB is the cheapest large drive. QLC slows on long builds. |
| ADATA Legend 710 | Gen3 | — | $220 (cheapest 2 TB) | Budget 2 TB for bulk data. |
| **Used NVMe (eBay sold)** | varies | ~$100 | ~$184 | Check SMART health (`smartctl -a`) on arrival. |

Plan and cloning: [OptiPlex §6](reference/entertainment/dell-optiplex-7060.md#6-fixing-small-ssd).

### 2.2 RAM (32 GB DDR4)

DDR4-2666 is the platform's speed. DDR4-3200 kits run at 2666 here. Keep matched pairs for dual channel.

| Option | Type | Price | Notes |
|---|---|---|---|
| **Used 2×16 GB DDR4 (eBay sold data)** | DIMM | **~$126** | Best value in 2026. Run `memtest86+` on arrival. |
| Crucial CT2K16G4DFRA32A (3200 CL22) | DIMM | ~$180 (Techinn) | Name brand, runs at 2666. |
| Timetec / Winten 2666 2×16 GB | DIMM | $176–190 | Budget brands, JEDEC 2666. |
| Kingston Fury / Corsair Vengeance LPX 2×16 GB | DIMM | ~$180–250 (unverified) | Typical 32 GB DDR4 kit median is ~$235. |
| Corsair / Lexar 3200 2×16 GB | **SO-DIMM (Micro only)** | ~$120 (unverified) | Only if your 7060 is the Micro. Single 16 GB SO-DIMMs run $82–100. |

SFF/tower: up to 64 GB (4×16 GB). Micro: 32 GB max.

### 2.3 Cooling (fan noise)

Clean it and cap CPU power first. Those are free and usually enough ([OptiPlex §7](reference/entertainment/dell-optiplex-7060.md#7-fixing-loud-fan)).

| Part | Price | Why / caveats |
|---|---|---|
| **Arctic MX-6 (4 g)** | ~$6–12 | Cheap and non-conductive. Repasting gains 5–15 °C on dried paste. |
| Noctua NT-H2 / Thermal Grizzly Kryonaut | ~$10–15 (unverified) | Marginally better. Not needed here. |
| Compressed air or an electric duster | $8–40 | Heatsink fins, CPU fan, PSU grille. |
| **Dell 7060 SFF 65 W heatsink + fan**, P/N **KGWT4** (also listed as 3CWF9, 7D86K, 48J9V) | ~$20–40 (unverified) | Only if the fan **bearing** rattles or grinds. The fan alone is 03CWF9 / 04H9JF. Micro 65 W: 35KV1 / 3XHPM. |
| i7-8700T (35 W), used | ~$75–160 | **Skip.** A PL1 cap on your 8700 gets nearly the same result for free. |

### 2.4 Power control: USB→RS-232 cable for the Denon

The AVR-3806 has a **DB9 female** port at 9600 8N1. You need a **straight-through (not null-modem) cable with a male DB9**. Genuine **FTDI** chips work everywhere, including Fedora without drivers.

| Cable | Chip | Price | Notes |
|---|---|---|---|
| **Sabrent CB-FTDI** (6 ft, thumbscrews) | FT232RL | ~$14 (sold out on sabrent.com; Amazon/B&H price unverified) | Best value if in stock. |
| DTECH FTDI (1.5–16 ft lengths) | FT232RL | ~$15–25 (unverified) | **Avoid DTECH's PL2303 version** (a different SKU). |
| UGREEN USB–RS232 FTDI (2 m) | FT232RL | ~$27 (Newegg marketplace) | |
| **StarTech ICUSB2321F** | FT232RL | $38–42 | Premium, reliable. |
| ~~StarTech ICUSB232FTN~~ | FT232RL | $55 | **Wrong cable: null-modem (DCE).** Don't buy. |

### 2.5 Power control: IR blasters for the Vizio

**2026 change:** Home Assistant 2026.4 added a native **Infrared** entity platform. It works with ESPHome, SMLIGHT and Broadlink emitters. HA 2026.6 added two-way IR. There's no Vizio device integration, so you use learned or raw codes ([Vizio §5.2](reference/entertainment/vizio-vs420lf1a.md#52-ir-protocol-for-pc-automation)).

| Device | Price | HA / cloud | Fit |
|---|---|---|---|
| **Seeed XIAO Smart IR Mate** (ESP32-C3, ESPHome) | **$11.99** | HA's recommended hardware; local only; learns codes | **Best value** if you run Home Assistant. |
| **Broadlink RM4 mini** | $25.99 | Official HA integration, local after setup; `python-broadlink` works from a plain script | **Best if you script from the PC without HA.** |
| Broadlink RM4 pro | $44.99 | Same, adds RF | Only if you also need RF (fans, blinds). |
| M5Stack AtomS3 Lite (ESPHome) | ~$8–15 (unverified) | Local | Transmit only; can't learn codes without an extra receiver. |
| SwitchBot Hub Mini (Matter) | $59.99 | Cloud, or limited IR over Matter | Easy app, weaker automation. |
| SwitchBot Hub 2 / Hub 3 | $69.99 / ~$129 | Cloud integration for IR | Overkill here. |
| ~~Broadlink RM Max / RM5 plus~~ | $49.99 | **Not supported** by HA's Broadlink integration | Avoid. |

A wired IR emitter into the Denon's rear **REMOTE IN** jack is also possible, but RS-232 is better for the Denon ([Denon §10.5](reference/entertainment/denon-avr-3806.md#105-ir)).

### 2.6 PC replacements (only if you want silence, or 4K/AV1 after a TV upgrade)

New mini PCs rose sharply in 2026. N150 boxes that were ~$190 in 2025 are $385–500 now. For a quiet **music/TV-only** box, a **used business mini** is the value play. None of these have HDMI-CEC, except the ASUS NUC 14 Pro. For CEC on anything else, add a Pulse-Eight USB-CEC adapter ($48), which only helps with a CEC-capable TV/AVR.

| Class | Model | Price (Sep 2026) | Vs the i7-8700 | Why / caveats |
|---|---|---|---|---|
| **Used business mini** | **Lenovo M720q / M920q Tiny** | M720q i5-8400T/16/256 **$299** refurb (eBay i3 from $75–145). M920q i7-8700T/16/512 $449 | Similar (8700T) | Quiet, 1-yr refurb warranty (System Liquidation). DP-first: HDMI is optional or needs an adapter. |
| Used business mini | **HP EliteDesk 800 G4 Mini** | i5-8500T/32/1TB from **$230** | Slightly slower | Best refurb value found. G5/G6 unverified. |
| Used business mini | Lenovo M80q Gen 1 (i5-10500T) / M75q Gen 1 (Ryzen 5 3400GE) | $399 / $289 | Similar | |
| Used business mini | OptiPlex 7060 Micro | ~$200 (eBay) | Same era | Same fan behavior as yours. |
| N150 (low power) | Beelink EQ14 | $385 (list $469) | **Much slower** for dev | Quiet, 6–10 W, AV1, HDMI 2.0. Bad value at 2026 prices. |
| N150 fanless | MeLE Quieter 4C | $460 (earlier coupons $252–270) | Much slower | **Silent.** Good dedicated Qobuz/HTPC box if it goes on sale. |
| N150 fanless | Zotac ZBOX CI360 nano | ~€230 barebone (EU); US unverified | Much slower | Silent. |
| Ryzen 7 8745H | **Minisforum UM870 Slim** | **$319** sale (list $399); $529 with 32 GB/1 TB | ~2× | Best Ryzen value found. Small fan can be audible under long loads. |
| Ryzen 9 8945HS | Minisforum UM890 Pro / GMKtec K8 Plus | $463 / $400 | ~2×+ | Strong dev box. |
| Ryzen 7 H 255 | GMKtec K12 | $360 | ~2× | |
| Premium | Beelink SER8 / SER9 | $769–1,169 | 2×+ | Good build; expensive this year. |

---

## 3. Streaming box: the real fix for the Xbox stereo / 5.1 problem

### What the problem needs

The Denon's **Auto Surround Mode** remembers a separate mode for each incoming signal type ([Denon §5.3](reference/entertainment/denon-avr-3806.md#53-auto-surround-mode-per-input-memory)). It can only do the right thing automatically if the **source changes format with the content**:
- **Stereo content → 2-channel PCM** (or DD 2.0). The Denon applies **PLIIx** automatically.
- **5.1 content → Dolby Digital 5.1** (DD+ converted to DD, because the 3806 can't decode DD+), **or 5.1 LPCM**. The Denon plays it discrete.

The Xbox never does this. It mixes everything into one fixed format ([Xbox §3.1](reference/entertainment/xbox-one.md#31-the-key-idea-the-xbox-is-a-mixer-not-a-passthrough-device)). You confirmed that 5.1 uncompressed behaves like DD: silent channels, no upmix. **Xbox Series X|S has the same pipeline.**

**The Denon's EDID advertises 6-channel LPCM, AC-3 and DTS**, read live from the PC ([OptiPlex §3](reference/entertainment/dell-optiplex-7060.md#3-audio-to-the-denon-avr-3806)). So a streamer on "Auto" may send decoded DD+ as **5.1 LPCM** instead of DD. That's equally good (lossless), provided stereo still goes out as PCM **2.0**. **Keep the Xbox on 5.1 uncompressed, never 7.1:** the EDID only lists 6-channel LPCM.

**One caveat applies to every box: Netflix.** An Nvidia staff reply on Nvidia's forum says Netflix sends many **stereo titles as 5.1 with empty channels**, to avoid audio gaps when the format switches. The receiver then sees DD 5.1 and won't upmix. So even the best box fixes YouTube, Qobuz, Spotify, Plex and most apps, but not every stereo Netflix title. For those, use 5CH STEREO or the DAC path in §3.1.

### 3.1 Cheapest fix: optical-to-analog DAC for a true 2-channel path

**Plan:** Xbox **HDMI audio = 5.1 uncompressed** into the Denon as now. Xbox **Optical audio = Stereo uncompressed** (the Xbox drives HDMI and optical at the same time with different settings, per [Xbox §3.2](reference/entertainment/xbox-one.md#32-speaker-audio-options)). The optical output goes through a small DAC into the **analog RCA inputs of the Xbox's Denon source** (for example DBS).

The Denon's **INPUT MODE** button (RS-232 `SDAUTO` / `SDANALOG`) then flips between:
- **AUTO:** HDMI, discrete 5.1 PCM for games and 5.1 movies.
- **ANALOG:** true 2-channel. The Denon remembers **PLIIx** for this signal type.

HDMI video keeps playing in both modes. The switch is **one button on the Denon remote**, or a PC/HA command, instead of a trip through Xbox menus. The Denon digitizes the analog input again for PLIIx. At normal listening levels that's inaudible.

The Xbox optical output is 48 kHz PCM, so any 24/96- or 24/192-capable DAC is more than enough. Prefer units with a **separate power supply** (a DC wall adapter) over USB-bus-powered ones, which can pick up ground-loop hum. Exact SKUs and prices are **unverified**, because the web-search budget ran out before this item could be checked.

| DAC (optical/coax → RCA) | Approx. price | Notes |
|---|---|---|
| **Musou** optical/coax to RCA + 3.5 mm | ~$12–18 (unverified) | Popular budget pick. Some kits include a Toslink cable and power adapter. |
| **J-Tech Digital** 192 kHz DAC converter | ~$20–30 (unverified) | US brand with a separate 5 V supply. Good budget-to-mid choice. |
| **Monoprice** digital-to-analog audio converter | ~$15–25 (unverified) | Monoprice support; basic. |
| **ViewHD** optical/coax to analog | ~$15–25 (unverified) | Similar to the above. |
| **Fosi Audio** small DAC (e.g., with optical in) | ~$40–70 (unverified) | Overkill here, but reusable later as a proper desktop DAC. |
| + **Toslink cable** (Amazon Basics / Monoprice, 1–2 m) | ~$6–10 | **Already owned**, so skip it |
| + **RCA stereo cable** (Amazon Basics / Monoprice, 1–2 m) | ~$5–8 | **Already owned**, so skip it |

**Why a DAC and not a second optical input:** on the 3806, a source's digital audio comes from **either** HDMI **or** one optical/coax input, never both (assigning one replaces the other, manual p.67). The INPUT MODE button (AUTO/PCM/DTS/ANALOG/EXT.IN) has no HDMI-vs-optical toggle (manual p.29). The source's **analog** jacks are the only second audio path that works alongside HDMI video, so the DAC is required. Setup steps are in [SETUP.md §3](SETUP.md#3-xbox-one-the-stereo51-problem-solved-as-far-as-current-gear-allows).

### 3.2 Streaming boxes compared

| Rank | Box | Price (Sep 2026) | Stereo → PCM 2.0? | DD+ → DD 5.1? | Qobuz app | Verdict |
|---|---|---|---|---|---|---|
| **1** | **Nvidia Shield TV Pro (2019), used** | New $199 but **out of stock at every US retailer since Aug 2026** (AFTVnews, 22 Sep 2026); the base "tube" Shield is gone. **Used ~$120–180 (unverified)** | **Yes (reported):** *Stereo upmix* setting **Off** keeps stereo streams as stereo | **Yes, documented.** Nvidia's own legacy-AVR instruction: *Available formats → **Manual**, disable all Dolby formats **except AC3***. Dolby audio processing converts DD+ → AC3 (2019 models only) | **Yes** (Android TV app, Nov 2025) | Best-documented fit and has Qobuz, but used-only for now. Buy a **2019** unit (P2897 Pro or the tube). 2015/2017 Shields **can't** transcode DD+ and fall back to PCM stereo. |
| **2** | **Roku Ultra (2024, model 4850R)** | ~$99 list (unverified 2026) | **Yes (reported):** Roku passes stereo as PCM and bitstreams 5.1 in *Auto detect*/passthrough | **Yes.** The Roku Team said on Best Buy Q&A that *"our top of the line Roku Ultra can transcode / convert DD+ to DD for output via HDMI."* The Streaming Stick 4K **cannot**: no Dolby decoder | No (unverified) | **Best new-in-box pick.** Set *Digital output format* to Auto, or Custom with **Dolby Digital** only (not DD+). Must be the **Ultra**. Brief audio drop at the start of playback is the format switching, which is expected. |
| **3** | **Amazon Fire TV Stick 4K Max (2nd gen) / Fire TV Cube (3rd gen)** | Stick ~$40–60 on sale; Cube ~$110–140 (both unverified for Sep 2026) | **Reported yes** with *Audio → Surround Sound → **Always Dolby Digital***: forum users say stereo can then be upmixed by the AVR and DD content plays as DD. **Best Available** may instead send DD+ as multichannel PCM to a PCM-capable AVR (reported) | **Yes.** Amazon: *"Most Amazon devices have the capability to automatically transcode DDP content to DD"* | No (unverified) | **Cheapest experiment.** Buy from a store with easy returns and test both settings. Same Netflix caveat. |
| 4 | **Walmart Onn 4K Pro (2nd gen)** | ~$50 (unverified) | **Uncertain.** Forum reports: with a DD-only sink it transcodes "all content to DD 5.1 or DD 2.0". If stereo arrives as **DD 2.0**, the 3806 *can* apply PLIIx (it treats DD 2.0 as a 2-channel source). If stereo arrives as DD 5.1, it's the Xbox problem again | Yes (transcodes; no passthrough of lossless) | **Yes** (Google TV) | Cheap Google TV box with Qobuz. Gamble on the stereo behavior; buy to test. |
| 5 | **Google TV Streamer** | **$149.99** (raised from $99.99 on 31 Aug 2026) | **Uncertain:** it **transcodes** rather than passes through (manual formats: DD+, DD, PCM stereo). Same MS12-style risk as the Onn | Yes, via the Manual format setting | **Yes** | More expensive than the Onn for the same risk. Skip unless on sale. |
| 6 | **Apple TV 4K** | $199 (64 GB Wi-Fi) / $249 (128 GB + Ethernet) | Auto sends decoded multichannel LPCM. Users report stereo arriving as multichannel PCM, which defeats receiver upmixing | **No.** Apple: in *Dolby Digital 5.1* mode it **"re-encodes audio"**, which is exactly the Xbox behavior | Unverified | **Don't buy for this problem.** Excellent box otherwise. |

**Verdict:**
1. Try the **$20 DAC path (§3.1)** first. It works with the Xbox you have.
2. For zero-switching streaming, buy a **Roku Ultra** new, or a **used 2019 Shield TV Pro** if you find one at a fair price (it adds Qobuz and has documented legacy-AVR settings).
3. A **Fire TV Stick 4K Max** is the cheapest test.
4. Avoid Apple TV for this.

**HDMI 1.1 compatibility (all boxes):**
- At 1080p these boxes use HDCP 1.4, which the 3806 supports. HDCP 2.2 is only needed for 4K.
- Set the box's output to **1080p60 SDR manually**. A 4K box reading an old EDID can pick odd modes.
- Power on in order: TV, then Denon, then box.
- No one has reported these exact pairings with a 3806 **(unverified)**. Buy from a store with returns.

---

## 4. Game consoles

| Console | Price (Aug 2026) | Fixes the audio switching? | Notes |
|---|---|---|---|
| Keep **Xbox One** | $0 | No, but §3.1 plus a streaming box work around it | Fine for 1080p gaming on this TV. |
| Xbox Series S | $499.99 | **No.** Same fixed-format audio mixer | Also **no optical out**, so the §3.1 DAC trick is impossible. |
| Xbox Series X | $799.99 | **No.** Same | Same: no optical. Worth it only with a 4K TV + HDMI 2.1 AVR. |
| Used Xbox Series S/X | ~60–75% of new (unverified) | No | Buy only for games. |

**Upgrade the console only for games, and only after the TV and AVR.** A Series console has no optical out, so it gives up the §3.1 workaround on the old Denon.

---

## 5. AV receivers

What to look for in the replacement:
- **Crossover up to 250 Hz** while the Bose cubes remain. **Only Denon/Marantz go to 250 Hz.** Yamaha, Onkyo/Pioneer and Sony stop at 200 Hz, which Bose's own guidance says is workable but leaves no headroom.
- HDMI 2.1 + **eARC + CEC**.
- **Network control** with the Home Assistant `denonavr` integration, which is local and uses the same PW/SI/MV/MS command set as your RS-232 scripts.
- Room EQ: **XT32 or Dirac**.
- **Two or more sub outputs**.
- On-screen GUI over video.

**Upmixing reality check (researched):**
- Dolby Surround, DTS Neural:X, Denon *Multi Ch Stereo* and Yamaha *All-Channel Stereo* **cannot recreate surround from stereo sent inside a 5.1 container**. Dolby Surround and Neural:X redistribute the channels that are present, so silent C/Ls/Rs stay silent.
- Multi Ch Stereo and All-Ch Stereo just copy the fronts to more speakers, with no steering. Yamaha's manual says it first mixes multichannel down to 2 channels.
- Denon's *Auto* mode plays PCM 2.0 as stereo and never upmixes 5.1 PCM.
- **A new AVR does not fix the Xbox stereo problem by itself.** The source still has to send true 2.0 (§3).
- Modern Denons save the sound mode **per input** ("Personal memory plus"), and the MOVIE/MUSIC/GAME buttons each remember their last mode.

**Denon/Marantz HDMI board failures:** a law firm (Migliaccio & Rathod) opened an **investigation** on 17 Jul 2026 into multiple HDMI inputs dying, black screens and ARC/eARC loss. No lawsuit has been filed. Prefer **new or refurbished with a warranty**, and test every HDMI port on used units ([Denon §13.3](reference/entertainment/denon-avr-3806.md#133-buying-used-what-to-look-for)).

### 5.1 New and refurbished

| Model | Price (Sep 2026) | Room EQ | Subs | Max crossover | HA | Why / caveats |
|---|---|---|---|---|---|---|
| **Denon AVR-X1800H** | **$849** new; refurb seen ~$411 on a 25%-off sale | MultEQ XT | 2 | 250 Hz | denonavr | **Entry pick.** Fixes 4K, CEC, eARC, Atmos (5.1.2) and the GUI. |
| Denon AVR-S770H | Discontinued; Denon refurb $499 when in stock | XT | 2 | 250 Hz | denonavr | Watch for refurb restocks. |
| Denon AVR-S980H (2026) | $949 | Reportedly basic MultEQ, not XT (unverified) | 2 | 250 Hz likely | denonavr | Worse value than the X1800H. |
| **Denon AVR-X2800H** | ~$999 new (clearance); refurb $699–949 | XT + paid Dirac | 2 | 250 Hz (manual) | denonavr | **Sweet spot on clearance or refurb.** |
| Denon AVR-X2900H (2026) | $1,349 | XT + optional Dirac (~$259–299) | 2 | 250 Hz (unverified) | denonavr | New model; not better value than a refurb X3800H. |
| **Denon AVR-X3800H** refurb | ~$1,100 (Accessories4less, **3-yr warranty**); Denon refurb $1,299 | **XT32** + paid Dirac | **4** | 250 Hz | denonavr | **Best value for serious EQ.** |
| Denon AVR-X3900H (2026) | $1,849 | XT32 + Dirac (included vs paid unverified) | 4 | 250 Hz (unverified) | denonavr | Premium new. |
| **Marantz Cinema 70s** (1st gen) refurb | **$999** (1-yr warranty) | XT + paid Dirac | 2 | 250 Hz (unverified) | denonavr | Slim, nicer sound and looks; 50 W is less power. |
| Marantz Cinema 70s Series 2 / Cinema 60 Series 2 | $1,500 / $2,000 | Dirac option | 2 | — | denonavr | New Sept/Aug 2026. |
| Yamaha RX-V6A | ~$646 | YPAO | 2 | **200 Hz** | yamaha_musiccast | Good value and HA support; 200 Hz max. |
| Yamaha RX-V4A | ~$550–650 | YPAO | 1 (unverified) | 200 Hz | yamaha_musiccast | 5.2 only. |
| Yamaha RX-A4A / RX-A6A | ~$1,400 / ~$2,680 (unverified) | YPAO-RSC | 2 | 200 Hz | yamaha_musiccast | |
| ~~Yamaha RX300A / RX500A~~ (2026) | $400 / $600 | YPAO | — | unverified | **No MusicCast** ("Audio Connect" app) | Weak HA support. Skip. |
| Onkyo TX-NR6100 | ~$475 deal – $699 | AccuEQ + paid Dirac | 2 | 200 Hz | onkyo | Budget Dirac path. |
| Onkyo TX-RZ30 | ~$699 deal | **Dirac included** | 2 | 200 Hz (assumed) | onkyo | Cheapest included-Dirac option. |
| Pioneer Elite VSX-LX305 | $599–999 (availability unverified) | Dirac | 2 | 200 Hz (unverified) | onkyo | |
| Sony STR-AN1000 | from ~$948 | DCAC IX | 2 | 200 Hz | songpal: partial (power/volume only) | Skip: weaker control. |
| 2026 Onkyo NR6200/RZ31 etc. | Not shipping in the US yet | Dirac | — | — | — | Wait. |

### 5.2 Used

| Model | Typical used price | Notes |
|---|---|---|
| **Denon AVR-X3700H** | $500–950 (eBay Jun–Jul 2026) | XT32, 8K/eARC. Ask about the 4K120 HDMI fix (it doesn't matter for Xbox One). |
| Denon AVR-X4700H | ~$900–1,000 | More power, XT32, eARC. |
| Marantz SR6015 | ~€700 median (HifiShark) | XT32, eARC, Marantz sound. |
| Denon AVR-X3600H / X4500H | ~$400–550 / ~$550–750 (unverified) | HDMI 2.0, **ARC not eARC** (unverified). XT32. |
| Marantz SR5015 | ~$500–650 (unverified) | XT (not 32). |

**Pick:** X1800H new (budget) → **X3800H refurb with 3-yr warranty** (best value) → X3900H (premium). Buy it **together with the TV**.

---

## 6. Subwoofers (replacing the Bose bass module)

**The key spec:** with the cubes crossed at **200 Hz**, the sub must play **flat to ~200–250 Hz** with its own low-pass **off or bypassed**. Let the Denon do all the filtering. Most budget subs have filters that stop at 140–160 Hz, and ports that resonate in the midbass. **Sealed** is preferred.

| Model | Box | Rated response / filter | Price new | Used | Fit for 200 Hz | Notes |
|---|---|---|---|---|---|---|
| **SVS SB-1000 Pro** (12", 325 W) | **Sealed** | **20–270 Hz ±3 dB**; low-pass defeatable in the app | **$599.99** (outlet $675 gloss) | Original SB-1000 ~$250–350 (unverified) | **Best documented fit** | 45-day in-home trial. Stays with you through every future speaker set. |
| **Rythmik L12** (12" servo) | **Sealed** | LFE input 18–200 Hz; 12–250 Hz ±3 dB | $791 incl. shipping | **$295–550** (US Audio Mart) | **Excellent** | **Best value bought used.** |
| SVS SB-2000 Pro | Sealed | Same app/DSP | $899.99 | — | Good | More output for a bigger room. |
| Monoprice Monolith M10-S / M12-S | Sealed | Unverified | ~$500 / ~$800 at launch (M12-S seen at $488) | Unverified | Likely good | Current status unverified. |
| BIC PL-200 II (12") | Ported | 21–200 Hz; **crossover bypassable** | MSRP $649 (street ~$300 historically) | — | OK | Port noise possible near 200 Hz. |
| Dayton CS1000 / CS1200 (replaced SUB-1000/1200) | Ported | to 200 Hz; filter max 160 Hz | $250 / $300 | SUB-1200 used ~$60–120 (unverified) | Marginal | Budget stopgap only. |
| Sony SA-CS9 (10") | Ported | 28–200 Hz | Discontinued | Used | Fair | Only as a cheap used find. |
| ~~Dayton SUB-1000L~~ | Ported (not sealed) | 32–**140 Hz** | $273 | — | **No** | Rolls off too low. |
| ~~Klipsch R-101SW / R-100SW~~ | Ported | 29.5–**120 Hz** | $170–380 | — | **No** | |
| ~~Polk PSW10 / Monitor XT10/XT12~~ | Ported | filter max 160 Hz | $185–399 | $50–80 | Poor/marginal | Fine for bookshelf speakers at 80 Hz later, not for cubes. |

**Pick:** a **used Rythmik L12 or SVS SB-1000 (Pro)** at $300–550, or a **new SB-1000 Pro at $600**. Set its low-pass off, connect it to the Denon's SUBWOOFER PRE OUT, and rerun Audyssey. Retire or sell the Bose module ([Bose §9](reference/entertainment/bose-acoustimass.md#9-honest-sound-quality-assessment-and-upgrade-path)).

---

## 7. TVs

1080p is fine for now. A new TV only pays off **together with a new AVR** (see buy order #12). Size vs distance for 4K ([Vizio §9.2](reference/entertainment/vizio-vs420lf1a.md#92-size-vs-viewing-distance-4k)): 6 ft → 55", 7 ft → 55–65", 8 ft → 65".

Must-haves:
- **HDMI-CEC** and **eARC**. On some TCL/Hisense sets eARC is on an HDMI 2.0 port, so plan which device goes where.
- **≥3 HDMI inputs** if the old Denon stays for a while.
- An **optical out that passes DD 5.1** (a bridge to the old Denon). Most TVs send only PCM 2.0 or DD 5.1 over optical, with no DTS.

All the 4K sets below have eARC and CEC.

| Tier | Model | Price seen (Sep 2026) | Why for this system | Caveats |
|---|---|---|---|---|
| Stopgap 1080p | **Insignia F20 42/43"** 1080p (Fire TV) | ~$119–180 | Removes the speaker bar and adds CEC and apps | **Only worth it under ~$120.** A 43" 4K set costs only $30–80 more. |
| Small 4K | **Sony Bravia 3 II 43"** (2026) | ~$550–600 | Only premium-brand 43"; good upscaling; Google TV (has Qobuz) | Expensive for its size. TCL/Hisense 43–50" QLEDs run ~$200–300 (unverified). |
| **Budget** | **Hisense U6 (2025) 55"** / **U6 Pro (2026) 55"** | $399.99 / $499.99 | Mini-LED; U6 Pro is RTINGS' current budget pick | Fire TV OS (Qobuz availability unverified). |
| **Value** | **TCL QM6K 55–65"** (2025, clearance) | 55" $448–548; **65" $529** (Best Buy) | QD-Mini-LED, 144 Hz, 2× HDMI 2.1, DV + HDR10+, Google TV | Smallest size is 55". eARC is on an HDMI 2.0 port. Clearance stock is going. |
| Value+ | TCL QM7K 55" (2025, clearance) | $599.99 (list $1,199) | Brighter than the QM6K | Clearance. |
| Mid | TCL QM7L (2026) / Hisense U7SG (2026) | QM7L 55" from $1,199.99; U7SG 55"/65" $1,299.99/$1,499.99 | Tom's Guide: QM7L is the best mini-LED value of 2026. U7SG is 165 Hz | Wait for sales. |
| Upper-mid | TCL QM8L 65" (2026) | $1,499.99 (list $2,499) | Top LCD for the money | |
| **Entry OLED** | **LG B5 55"** (2025, clearance) / **Samsung S85F 55"** | $850 (low $599.99 in June) / $847–897 | Perfect blacks at mid-LCD prices; great CEC/eARC | S85F has no Dolby Vision. |
| Premium OLED | LG C6 65" (2026) / Samsung S90F 55" | $1,599.99 / $999.99 | 4× HDMI 2.1 (LG) | LG C5 clearance price unverified. |
| Premium LCD | Sony Bravia 7 II (2026, RGB mini-LED) | 50" ~$1,600; 65" $2,599 | Best processing | Pricey. |
| New in 2026 | Roku Pro Series OLED 55" | $999 MSRP (Pro LX OLED $1,299, ships Oct 2026) | New | Roku OS; no Qobuz (unverified). |
| Light built in | Philips Ambilight 65" (7985, Roku) | ~$470 (per the light page) | Solves the reactive light and the TV in one purchase ([light §3.8](reference/entertainment/reactive-light.md#38-philips-ambilight-tv-if-replacing-the-tv)) | Roku OS. |

**Pick:**
- **TCL QM6K 65" at ~$529** while clearance lasts. That's the best value if your seat is 7–8 ft away.
- **LG B5 55"** if you want OLED on a budget.
- If the 42" spot can't grow, a **Sony Bravia 3 II 43"**, or the LG C-series 42" (Vizio page).

---

## 8. Speaker packages

Conventional passive speakers with binding posts, plus the powered sub from §6. Cross over at 80–100 Hz once the cubes are gone, then rerun room EQ. Sub prices aren't included unless stated.

| Tier | Package | Approx. price | Footprint | Why / caveats |
|---|---|---|---|---|
| **Budget, like-for-like size** | **Energy Take Classic 5.1** (3" satellites + 8" ported sub) | **$179** sale (Adorama, 4 Sep 2026; regular $299) | Closest to the cubes | A full kit. Its sub is basic; use your §6 sub if you have one. |
| **Budget, best sound** | **Micca MB42X ×4 + MB42X-C** (5.0) | **~$215** | Small bookshelf (4") | Needs a crossover at 80–100 Hz, so a real sub is required. |
| Budget | Pioneer SP-BS22-LR ×2 + SP-C22 (Andrew Jones) | Used ~$120–150/pair | Bookshelf | **Discontinued**, used only. |
| Budget | Sony SS-CS5M2 (pair) + SS-CS8M2 center (2025 "M2") | $228/pair + $198 | Bookshelf | 3-way. Easy to find. |
| Mid | **Polk Monitor XT15 ×2 pairs + XT30** (5.0) | **~$537** list | Bookshelf | Often on sale; forgiving. |
| Mid | **ELAC Debut 3.0** DB53 ×2 pairs + DC53/DC63 | ~$630–800 | Bookshelf | Andrew Jones lineage; much better for Qobuz. ELAC store prices may be open-box. |
| Mid | Klipsch Reference R-40M/R-50M + R-30C/R-50C | R-40M $200–300/pair; R-50M $396/pair | Bookshelf | Bright horn tweeters. Factory refurb R-40M at klipsch.com. |
| Upper-mid | Polk Signature Elite ES15/ES20 + ES30/ES35 | $299–399/pair (20–35% off on sales) | Bookshelf | |
| **Premium small-footprint** | **SVS Prime Satellite 5.1** (5 satellites + **SB-1000 Pro**) | **$1,399.99** | Satellites ~8.5" | Includes the sub. If you already own an SB-1000 Pro, the satellites are ~$800 of it. |
| Premium | KEF Q1 Meta (pair) ×2 + Q-series center | $699.99/pair (seen $399.99) | Bookshelf | Excellent imaging for music. |
| Premium | Polk Reserve R100/R200 + R300 | $699–799/pair + $499 | Bookshelf | |
| Used, slim | KEF T101/T301 (ultra-thin) | T301 + T301c ~$400 (eBay) | Wall-flat | Used only in the US. |

### 8.1 Atmos / height (later, with the new AVR)

| Model | Type | Price | Notes |
|---|---|---|---|
| **Polk Monitor XT90** | Up-firing module | **$119/pair** | Budget entry. |
| ELAC Debut 3.0 DA43 | Up-firing / on-wall | $389/pair (may be open-box) | |
| Klipsch R-40SA | Up-firing / wall | $540/pair | |
| Polk ES90 / Reserve R900 | Up-firing | $449 / $599 per pair | |
| **SVS Prime Elevation** | Angled on-wall/ceiling | $275 each | **Best real height option.** |
| In-ceiling (Micca M-8C etc.) | Ceiling | unverified | Best Atmos effect; needs ceiling work. |

Up-firing modules need a flat, reflective ceiling about 7.5–12 ft high. In a pinch the old **Bose cubes can serve as heights**.

---

## 9. Reactive light

The tiers match [reactive-light.md §10](reference/entertainment/reactive-light.md#10-recommendation-tiers). Prices are updated for September 2026.

| Tier | Pick | Price (Sep 2026) | Why for this system | Caveats |
|---|---|---|---|---|
| **Budget (start here)** | **Govee TV Backlight 3 Lite (40–50", H6097)** | **$53–55** (list $69.99) | Camera-based, so no HDMI changes and no risk to the HDMI 1.1 chain. Works with Netflix. Mic music mode. **Fits the 42"** | Moderate lag. |
| Budget add-on | Govee RGBIC Floor Lamp Basic (Matter) | $59–70 (list $100) | Groups with the backlight (DreamView); music mic | |
| DIY audio-only | **GLEDOPTO GL-C-015WL-M** (ESP32, WLED preinstalled, built-in mic), or an **Athom WLED music controller** + an LED strip | Controller ~$30–40 (US unverified) + strip/PSU | Reacts to every source; local Home Assistant control. Add **LedFx** (free) on the OptiPlex to drive it from PC audio, which beats a mic for Qobuz | DIY. For line-level input, use the Denon **front pre-outs**, not Zone 2/REC OUT ([light §8](reference/entertainment/reactive-light.md#8-getting-audio-to-a-sound-reactive-controller)). |
| DIY, sturdier | QuinLED Dig-Uno (prebuilt) | $27.50–53 | Well-built WLED board with fusing | Needs a separate mic/line-in board for audio. |
| Value HDMI | WiZ HDMI Sync Box kit | $89.99 (55–65") | HDMI accuracy + mic, no hub | Strip is 55"+ and not cuttable; HDMI 2.0 only. |
| Camera, bigger TV | Nanoleaf 4D V2 / Govee Envisual T2 | $99.99 / ~$75–120 | For a future 55–65" TV | Don't fit the 42". |
| HDMI box | Govee AI Sync Box Kit 2 | ~$240–249 | 4× HDMI 2.1 in, Matter | Strip is 55"+. |
| DIY hybrid | WLED + HyperHDR on a Pi 5 or the OptiPlex, with a splitter **after the Denon** | $120–200 | True video sync + line-level music, any TV size | HDCP content needs care ([light §5.2](reference/entertainment/reactive-light.md#52-hyperionng--hyperhdr-on-a-raspberry-pi-with-usb-hdmi-capture)). |
| **Best overall / carries over** | **Philips Hue Sync Box 8K** (after the Denon; $349.99 list, sales to $244.99) + **Bridge Pro ($139, up from $99 on 16 Sep 2026)** + Play gradient strip 55" (~$154) | **~$530–650** | Most accurate; every piece moves to a future 4K TV/AVR | Expensive. |
| Future | Philips Ambilight TV | ~$470 (65") | Built in; see §7 | Replaces the TV. |

---

## 10. Remotes and control

Goal: one button for "Watch Xbox", "Listen (PC/Qobuz)" and "All off", despite no CEC anywhere.

### 10.1 Universal remotes

| Remote | Price (Sep 2026) | Why / caveats |
|---|---|---|
| **SofaBaton X1S** | **$179.99** (often $20 off) | Hub with IR + Bluetooth; activities with discrete power. A **local Home Assistant integration** ("Sofabaton X", HACS, posted 17 Sep 2026) supports the X1, X1S and X2: activities, commands, IR learning, and mapping remote buttons to HA actions. **Best pick.** |
| SofaBaton X2 | $359.99 (launched ~$289) | Adds a touchscreen, dock, RF and MQTT. Premium. |
| SofaBaton U2 / U2 Backlit | **$69.99** | No hub, IR only, limited macros, no HA. **Budget pick** if you just want one remote for the Denon, Vizio and Xbox. |
| SofaBaton X1 | Discontinued, used only | Same HA integration as the X1S. A good used find. |
| **Used Logitech Harmony** (Hub, Companion, Elite, 650/665/950) | Companion $50–119 used; Elite $69–400; Hub-only ~$25–50 (unverified) | **Hardware discontinued in 2021; servers still up** (StatusGator, 22 Sep 2026). MyHarmony-app models can still be edited. No development, and it could stop working at any time. The Harmony Hub has a local HA integration. Buy only cheaply. |
| Unfolded Circle Remote 3 | €329 (+ Dock €99) | **New pre-orders on hold** (RAM/eMMC shortage). Not buyable now. |
| **Home Assistant dashboard + IR blaster** (§2.5) | $12–40 + phone | **Cheapest "one-button" setup.** HA scripts call the Denon over RS-232 and the TV over IR. |

### 10.2 Xbox IR emitter cable

The Xbox's rear **IR Out** port (3.5 mm) drives an **IR emitter cable** (generic 3.5 mm single or dual "IR blaster/extender" emitters, ~$5–10). Stick the emitters on the Denon's and Vizio's IR windows if the console is in a cabinet, or the front blaster can't see them ([Xbox §7](reference/entertainment/xbox-one.md#7-power-control-turning-on-the-tv-and-the-denon)). The original Xbox One (1540) has an IR Out port but no front blaster.

### 10.3 Smart plugs with power monitoring

Use these for **sensing**, not cutting power. For example, "Xbox is drawing power → turn on the Denon". Never switch the Denon off at the wall.

| Plug | Price (unverified) | Control |
|---|---|---|
| **TP-Link Tapo P110M / Kasa KP125M** (Matter, energy monitoring) | ~$15–25 each | Matter = local HA control. |
| **Shelly Plug US Gen4** | ~$20–25 | Fully local (HTTP/MQTT), excellent in HA. |
| Third Reality smart plug (Zigbee, energy) | ~$15 | Needs a Zigbee coordinator. |
| Eve Energy (Matter/Thread) | ~$35–40 | Premium, Thread. |

### 10.4 Always-on automation host (later, optional)

The OptiPlex dual-boots and isn't always on, so PC-hosted automation stops whenever it's off or in the other OS. An always-on host runs Home Assistant with the **Denon RS-232** (HA integration added in 2026.5; see [system-overview §5](reference/entertainment/system-overview.md#5-how-the-parts-interact-watch-outs)), the IR blaster and the smart plugs. Then any source, remote or phone can drive the system. Prices below are rough and **unverified**, since the search budget ran out.

| Option | Approx. price | Why / caveats |
|---|---|---|
| **ESP32 + MAX3232 RS-232 board running ESPHome** | ~$10–20 | Puts the Denon on Wi-Fi by itself: an ESPHome UART bridge speaks PW/SI/MS commands. Can share a board with the IR blaster. Not a full HA host, but makes the Denon network-controllable from anything. |
| **Home Assistant Green** | ~$130–150 | Official plug-and-play HA box. Easiest option. Low power, silent. |
| **Raspberry Pi 5 (4–8 GB) kit** or Pi 4 | ~$100–150 (kit with case, PSU, SSD/SD) | Flexible; can also run HyperHDR for the light. RAM price rises in 2026 hit Pi prices too. |
| **Used thin client** (Dell Wyse 5070, HP t630/t640) | ~$40–80 used | Cheapest x86 HA host; silent, low power. |
| Used business mini (§2.6) | $200–300 | Only if it also becomes the HTPC. |

With a USB-RS-232 cable (§2.4) plugged into the always-on host, the PC-side scripts become optional.

---

## 11. Cables and tidy-up

| Item | Pick | Approx. price (unverified) | Notes |
|---|---|---|---|
| Speaker wire (cubes, or future speakers) | Amazon Basics / Monoprice **16 AWG** | ~$15–25 per 100 ft | 16 AWG is plenty for runs under ~50 ft. |
| **Flat / paintable speaker wire** (surround runs under rugs and along baseboards) | Monoprice flat, or the flat-wire kits sold for surround rears | ~$20–40 per 50 ft | Tuck-in and paintable. |
| **RCA subwoofer cable** | Monoprice / Amazon Basics / Mediabridge, single RCA | ~$8–15 | Denon SUBWOOFER PRE OUT → sub (or Bose LFE). Get the length right to avoid coils. |
| **Certified HDMI** | **Premium High Speed** (18 Gb/s) for now; **Ultra High Speed** (48 Gb/s) if buying for a future 4K/120 TV + AVR. Brands: Monoprice, Zeskit, Cable Matters, Amazon Basics (certified SKUs) | ~$8–20 | Look for the **scannable certification label**. Keep runs short (≤5 m) with the 3806 ([Denon §11](reference/entertainment/denon-avr-3806.md#11-known-issues-failure-modes-firmware)). |
| Toslink cable | Amazon Basics / Monoprice | ~$6–10 | For §3.1. |
| Cable management | Velcro ties, split-loom sleeves, adhesive J-channel raceway, paintable wall raceway | ~$10–30 | |

### 11.1 Removing the bulky Bose input cable

The powered Acoustimass modules (AM6 III/V, AM10 III–V, AM15 II, AM16) take a **standard-density DB-15 (DA-15, 2 rows, 8 over 7)** "Audio Input" cable with thumbscrews ([Bose §1](reference/entertainment/bose-acoustimass.md#1-identify-the-exact-model)). The module side is male, so a replacement plug is a **female DA-15**. **Don't buy HD-15 (3-row VGA) parts.**

The cable's receiver end splits into five speaker-wire pairs plus the **LFE RCA**. The LFE RCA is wired into the DB-15, not a separate jack on the module. With the cubes wired straight to the Denon, the only thing you need from the cable is the LFE feed.

- **No off-the-shelf "DB-15 → RCA LFE pigtail" exists** (none found).
- **Bose has never published the DB-15 pinout.** Forum requests went unanswered. Whether the module needs a turn-on or sense pin to wake is **unverified**.
- **Simplest, $0:** keep the original cable plugged in. Use only its LFE RCA and insulate the unused speaker leads ([Bose Fix B](reference/entertainment/bose-acoustimass.md#fix-b--module-becomes-a-plain-powered-sub-cubes-wired-direct)). Coil and velcro the rest behind the module.
- **DIY short pigtail (< $15 in parts):**
  - Parts: a **female DA-15 solder-cup connector + hood** (~$3–8, e.g. L-com SD15S or an eBay kit), a panel RCA jack (~$2), and shielded wire.
  - First **map the LFE signal and ground pins with a multimeter** (continuity from the LFE RCA tip and sleeve to the DB-15 pins) on your own cable. Then wire only those two.
  - If the module won't wake, some other pin matters. Put the original cable back.
- **If the cable is lost or damaged:** a used OEM Bose input cable runs **$32–68 on eBay** (most $39–48). The third-party **Xetilmo** DB-15 → 5 pairs + LFE cable (6 m) is on Amazon (US price unverified; £66 in the UK).
- **Best long-term answer:** replace the module with a real sub (§6). The whole cable then goes away.

---

## 12. Skip these

| Item | Why it won't help this system |
|---|---|
| **Pulse-Eight USB-CEC adapter (for now)** | Neither the Denon nor the Vizio speaks CEC. Only useful with a new TV/AVR. |
| **Xbox Series X/S to fix audio** | Same fixed-format mixer, and **no optical out** (which removes the §3.1 fix). |
| **Apple TV 4K to fix audio** | "Dolby Digital 5.1" re-encodes everything, exactly like the Xbox. |
| **Roku Streaming Stick 4K / Roku Express** | No Dolby decoder, so no DD+ → DD for the 3806. Only the **Ultra** does it. |
| **2015/2017 Nvidia Shield** | Can't transcode DD+ → DD; falls back to stereo PCM. Only 2019 models. |
| **A new AVR alone, hoping it upmixes Xbox stereo** | No upmixer recovers surround from stereo inside a 5.1 container. |
| **A 4K TV alone behind the old Denon** | HDMI 1.1 caps everything routed through it at 1080p, with no ARC/CEC. Buy the TV with the AVR, or run 4K sources straight into the TV. |
| **HDMI audio extractors / "HDMI to 5.1 analog" boxes** | The 3806 already decodes DD, DTS and multichannel PCM. Adds lag and clutter. |
| **Smart plug to turn the Denon/TV on and off** | Power returns to standby, and it's crude for an amp. Use RS-232/IR; plugs only for sensing. |
| **Dayton SUB-1000L, Klipsch R-100SW/R-101SW, small ported Polk subs as a Bose replacement** | Filters and responses stop at 120–160 Hz; they can't fill the 200 Hz handoff to the cubes. |
| **i7-9700 with a modded BIOS / i7-8700T swap** | Brick risk for ~15% gain / same result as a free power cap. |
| **7.1 uncompressed on the Xbox** | The Denon EDID lists only 6-channel LPCM, and you have 5.1 speakers. Stay on **5.1 uncompressed**. |
| **Broadlink RM Max / RM5** | Not supported by Home Assistant's Broadlink integration. |
| **StarTech ICUSB232FTN** | Null-modem cable. Wrong for the Denon. |
| **QLC NVMe for heavy dev builds** | Slows on sustained writes; pick TLC (P41, SN7100). |
| **Premium HDMI "audiophile" cables** | Certified Premium High Speed cables perform identically. |

---

## 13. Sources

Component research pages (same folder): [system-overview](reference/entertainment/system-overview.md) · [OptiPlex 7060](reference/entertainment/dell-optiplex-7060.md) · [Xbox One](reference/entertainment/xbox-one.md) · [Denon AVR-3806](reference/entertainment/denon-avr-3806.md) · [Bose Acoustimass](reference/entertainment/bose-acoustimass.md) · [Vizio VS420LF1A](reference/entertainment/vizio-vs420lf1a.md) · [Reactive light](reference/entertainment/reactive-light.md)

**Streaming boxes**
- Nvidia, AVR/Surround Audio Setup (legacy receivers: Manual, AC3 only): https://www.nvidia.com/en-us/shield/support/shield-tv-pro/avr-surround-audio-setup/
- Nvidia forum, Dolby audio processing (DD+→AC3 for older receivers; Netflix stereo-as-5.1): https://www.nvidia.com/en-us/geforce/forums/shield-tv/9/389092/dolby-audio-processing-howwhen-does-it-work/ · https://www.nvidia.com/en-us/geforce/forums/shield-tv/9/380402/dolby-audio-processing-enable-or-disable/2736774/
- Nakamichi, Shield TV audio settings (Stereo Upmix = stereo streams to 5.1 PCM): https://www.helpdesk.nakamichi-usa.com/nvidia-shield-tv-pro-audio
- AFTVnews, Shield TV Pro out of stock everywhere (22 Sep 2026): https://www.aftvnews.com/shield-tv-pro-is-out-of-stock-everywhere-is-this-the-end-of-the-line-or-could-a-new-model-be-coming/
- Best Buy Q&A, Roku Team: Ultra transcodes DD+→DD; Streaming Stick 4K has no Dolby decoder: https://www.bestbuy.com/site/questions/roku-streaming-stick-4k-streaming-device-4k-hdr-dolby-vision-with-roku-voice-remote-and-tv-controls-black/6479078/question/100f258f-6553-3413-9402-bb1d2cd2b5ae
- Roku Ultra product page (4850R): https://www.roku.com/products/roku-ultra · Roku surround setup: https://support.roku.com/article/set-up-your-player-for-surround-sound
- Amazon, Dolby integration guidelines (DDP→DD transcode): https://developer.amazon.com/docs/fire-tv/dolby-integration-guidelines.html
- Home Theater Forum, Fire TV "Always Dolby Digital" behavior: https://www.hometheaterforum.com/community/threads/pass-through-audio-on-fire-stick-4k.365533/
- Nakamichi, Fire TV Cube audio: https://www.helpdesk.nakamichi-usa.com/amazon-fire-tv-cube-audio
- AFTVnews, Onn 4K Pro (2nd gen) audio: https://www.aftvnews.com/2nd-gen-onn-4k-pro-does-not-support-lossless-dolby-truehd-and-dtsx-audio-passthrough-like-the-onn-4k-stick/ · AVS Onn thread: https://www.avsforum.com/threads/walmart-onn-4k-streaming-box.3198184/page-26
- Google TV Streamer audio formats: https://support.google.com/chromecast/answer/10110321 · https://www.androidpolice.com/google-tv-streamer-audio-output/ · price hike: https://9to5google.com/2026/08/31/google-tv-streamer-increase/
- Apple: audio formats ("re-encodes audio" for DD 5.1): https://support.apple.com/en-us/102218 · price: https://www.apple.com/shop/buy-tv/apple-tv-4k · https://discussions.apple.com/thread/255839500
- Qobuz Android/Google TV app launch: https://community.qobuz.com/press-en/qobuz-launches-android-tv-app · https://www.audioadvice.com/blogs/expert-advice/qobuz-comes-to-google-tv

**PC**
- SSD prices: https://cheapestssd.com/1tb-nvme-ssd/ · https://cheapestssd.com/ · https://gamersnexus.net/features/ssds-wtf · https://pangoly.com/en/price-history/sk-hynix-platinum-p41-1tb · https://www.getpcparts.com/market-prices
- RAM: https://rampricesusa.com/best-32gb-ddr4-ram · https://rampricesusa.com/laptop-ram-prices · https://www.tomshardware.com/pc-components/ram/ram-price-index-2026-lowest-price-on-ddr5-and-ddr4-memory-of-all-capacities · https://www.getpcparts.com/market-prices/ram-memory/16gb-ddr4
- Cooling: https://www.walmart.com/ip/Dell-OptiPlex-3060-5060-7060-3050-7050-SFF-65W-CPU-Cooling-Fan-Heatsink-Assembly-KGWT4/20630062987 · https://www.amazon.com/Heatsink-Assembly-3CWF9-Replacement-Optiplex/dp/B0CKJ494JZ · https://www.tomshardware.com/pc-components/thermal-paste/get-rid-of-that-ancient-thermal-paste-with-arctics-mx-6-which-just-hit-an-all-time-low-price-at-amazon-a-cheap-fix-for-what-could-turn-into-an-expensive-problem
- Serial cables: https://www.technologygalaxy.com/Startech-1-Port-FTDI-USB-to-Serial-RS232-Adapter-Cable-ICUSB2321F/p/302588 · https://us.rs-online.com/product/startech-com/icusb232ftn/72015383/ · https://sabrent.com/products/cb-ftdi · https://www.newegg.com/p/181-08M5-001C2 · https://www.amazon.com/DTECH-RS232-Serial-Adapter-Cable/dp/B00H8HDS2K
- IR / HA: https://www.home-assistant.io/blog/2026/04/01/release-20264/ · https://www.home-assistant.io/integrations/infrared/ · https://www.seeedstudio.com/XIAO-Smart-IR-Mate-p-6492.html · https://www.home-assistant.io/integrations/broadlink/ · https://github.com/orgs/home-assistant/discussions/465 · https://us.switch-bot.com/pages/matter · https://www.howtogeek.com/switchbot-hub-3-review/
- Mini PCs: https://www.bee-link.com/products/beelink-eq14-n150 · https://store.mele.cn/products/mele-quieter-4c-n150-3-6ghz-fanless-mini-computer-ddr4-hdmi-4k-wi-fi-5-bt-5-1-usb-3-2-2-usb-2-0-1-type-c-1 · https://www.fanlesstech.com/2026/08/zbox-ci360-available.html · https://store.minisforum.com/collections/mini-pc · https://www.gmktec.com/collections/k-series · https://systemliquidation.com/collections/refurbished-lenovo-desktops · https://systemliquidation.com/collections/hp-elitedesk-series-desktops · https://www.asus.com/us/displays-desktops/nucs/nuc-mini-pcs/asus-nuc-14-pro/ · https://www.pulse-eight.com/p/104/usb-hdmi-cec-adapter

**AV receivers**
- Denon: https://www.denon.com/en-us/product/av-receivers/avr-x1800h/300773.html · https://www.denon.com/en-us/product/av-receivers/avr-s770h/300777-refurbished.html · https://www.denon.com/en-us/product/denon-certified-refurbished/avr-x2800h/300610-refurbished.html · https://www.denon.com/en-us/product/av-receivers/avr-x3800h/300609-refurbished.html · https://www.accessories4less.com/make-a-store/item/denavrx3800h-rb/denon-avr-x3800h-9.4-ch-x-105-watts-8k-a/v-receiver-w/heos/1.html · https://audiomatome.com/en/news/2026-05-19-denon-x-series-2026/ · https://www.whathifi.com/tv-home-cinema/av-receivers/denon-avr-x2900h-review · https://www.crutchfield.com/p_033AVX3900/Denon-AVR-X3900H.html · https://www.ecoustics.com/products/denon-avr-s980h/
- Denon manuals (crossover, sound modes, memory): https://manuals.denon.com/AVRX2800H/EU/EN/GFNFSYitmloggd.php · https://manuals.denon.com/AVRX2800H/NA/EN/DRDZSYyrtgycpw.php · https://manuals.denon.com/avrs760h/na/en/DRDZSYhrhvtgzs.php · https://manuals.denon.com/AVRX3800H/NA/EN/GFNFSYuiedzpst.php · https://manuals.denon.com/avrx6800h/na/en/GFNFSYvhhpesdv.php
- Marantz: https://www.marantz.com/en-us/product/marantz-recertified/cinema-70s/300619-refurbished.html · https://www.theabsolutesound.com/articles/introducing-marantz-cinema-series-2/
- Yamaha: https://manual.yamaha.com/av/20/rxv6a/en-US/317345163.html · https://www.dealnews.com/products/Yamaha/Yamaha-RX-V6-A-7-2-Channel-AV-Receiver/502000.html · https://www.prnewswire.com/news-releases/yamaha-debuts-rx300a-and-rx500a-home-theater-av-receivers-302768806.html · https://www.manualslib.com/manual/2734254/Yamaha-Aventage-Rx-A6a.html
- Onkyo/Pioneer/Sony: https://support.onkyousa.com/hc/en-us/articles/10376381563156-TX-NR6100-Setup-Menu-Speaker · https://www.ecoustics.com/products/onkyo-av-receivers-2026/ · https://helpguide.sony.net/ha/strtaan10/v1/en/contents/TP1000544505.html · https://community.home-assistant.io/t/sony-ta-an1000-receiver-not-working-with-songpal-integration/975461
- Upmixing on 5.1 input: https://www.avsforum.com/threads/the-official-dolby-surround-dts-x-faq-discussion-thread.2210106/
- Used: https://www.hifishark.com/model/denon-avr-x-3700-h · https://www.hifishark.com/model/denon-avr-x-4700-h · https://www.hifishark.com/model/marantz-sr-6015
- HDMI board investigation: https://classlawdc.com/2026/07/17/denon-avr-hdmi-board-failure-investigation/
- Bose + 200 Hz crossover: https://forums.audioholics.com/forums/threads/yamaha-663-bose-acoustimass-10.47055/

**Subwoofers and speakers**
- https://www.svsound.com/products/sb-1000-pro-subwoofer · https://hometheaterhifi.com/reviews/speaker/subwoofers/svs-sb-1000-pro-subwoofer-review/ · https://www.svsound.com/products/sb-2000-pro · https://www.svsound.com/products/prime-satellite-5-1 · https://www.svsound.com/products/prime-elevation
- https://www.rythmikaudio.com/L12.html · https://www.rythmikaudio.com/L12_specs.html · https://www.usaudiomart.com/details/649475885-rythmik-l12-sealed-servo-subwoofer/
- https://www.daytonaudio.com/product/1238/sub-1000l-10-low-profile-powered-subwoofer · https://www.daytonaudio.com/product/2157/cs1000-10-180w-powered-subwoofer-black · https://www.daytonaudio.com/product/2159/cs1200-12-200w-powered-subwoofer-black · https://www.parts-express.com/Dayton-Audio-SUB-1200-Powered-Subwoofer-300-629
- https://www.audioholics.com/subwoofer-reviews/monolith-sealed-subs · https://www.bicamerica.com/product-page/acoustech-pl-200ii-1000w · https://assets.klipsch.com/product-specsheets/Reference-R-101SW-Spec-Sheet.pdf · https://www.abt.com/Sony-Home-Theater-Black-Subwoofer-SACS9/p/110825.html
- https://www.polkaudio.com/en-us/category/monitor-xt-series/ · https://www.polkaudio.com/en-us/category/signature-elite-series/ · https://www.polkaudio.com/en-us/category/reserve-series/
- https://www.miccatron.com/micca-mb42x/ · https://www.erinsaudiocorner.com/loudspeakers/micca_mb42x_center/ · https://www.hifishark.com/model/pioneer-sp-bs-22-lr · https://slickdeals.net/f/19971360-energy-take-classic-5-1-channel-home-theater-system-179-free-s-h
- https://www.bestbuy.com/product/elac-debut-3-0-6-5-bookshelf-speakers-db63-bk-pair-black/J3R8Z6HJ6J/sku/10769519 · https://elac.com/db53 · https://www.abt.com/Klipsch-R-40M-Reference-Black-Bookshelf-Speakers-Pair-1069855/p/178856.html · https://us.kef.com/products/q1-meta · https://www.hifishark.com/model/kef-t-101 · https://www.abt.com/Klipsch-R-40SA-Reference-Black-Dolby-Atmos-Elevation-Surround-Speakers-Pair-1069858/p/178858.html

**TVs**
- https://camelcamelcamel.com/product/B0DSR9CHB1 · https://slickdeals.net/f/19213405-tcl-65-class-qm6k-series-4k-uhd-hdr-qd-mini-led-smart-tv-with-google-tv-2025-529-at-best-buy · https://us.tcl.com/products/qm7k-series-qd-mini-led-qled-4k-uhd-smart-tv-with-google-tv · https://www.tomsguide.com/tvs/qled-tvs/tcl-qm7l-review · https://us.tcl.com/products/qm8l-series-sqd-mini-led-4k-uhd-hdr-smart-tv-with-google-tv
- https://www.bestbuy.com/product/hisense-55-class-u6-pro-miniled-series-qled-4k-uhd-smart-fire-tv-2026/J3Z9Z42W4J · https://www.bestbuy.com/product/hisense-55-class-u6-series-miniled-qled-uhd-4k-hdr-smart-fire-tv-2025/J3Z9Z42SLP/sku/6620385 · https://www.bestbuy.com/product/hisense-65-class-u7-series-miniled-qled-uhd-4k-hdr-smart-google-tv-2026/J3Z9Z42HT2
- https://newsroom.roku.com/news/2026/09/roku-launches-all-new-pro-series-oled-and-pro-series/piv2e7pu-1788194403 · https://www.bestbuy.com/product/sony-43-class-bravia-3-ii-4k-hdr-led-google-tv-with-gemini-2026/J7XSRH54S3 · https://www.rtings.com/tv/reviews/sony/bravia-7-ii
- https://slickdeals.net/f/18937264-lg-55-class-b5-series-oled-ai-4k-uhd-smart-webos-tv-2025-850-at-best-buy · https://www.tomsguide.com/us/best-tv-deals,news-26008.html · https://slickdeals.net/f/19260040-samsung-s85f-55-4k-hdr-smart-oled-tv-848-b-h-65-1098ac · https://slickdeals.net/f/17812821-limited-time-deal-for-prime-members-insignia-42-inch-class-f20-series-smart-full-hd-1080p-fire-tv-with-alexa-voice-remote-ns-42f201na23-119-99

**Lights**
- https://us.govee.com/products/govee-tv-backlight-3-lite · https://9to5toys.com/2026/05/05/govee-matter-ready-floor-lamps-up-to-40-savings-starting-from-70/ · https://www.techradar.com/home/smart-lights/wiz-hdmi-sync-box-kit-review · https://us-shop.nanoleaf.me/products/nanoleaf-4d-v2 · https://us.govee.com/products/govee-ai-sync-box-kit-2
- https://www.philips-hue.com/en-us/p/hue-philips-hue-play-hdmi-sync-box-8k/046677579753 · https://9to5google.com/2026/09/16/philips-hue-bridge-pro-price-hikes/ · https://gledopto.com/h-pd-9.html · https://www.athom.tech/blank-1/wled-esp32-music-addressable-led-strip-controller · https://quinled.info/pre-assembled-quinled-dig-uno/ · https://docs.ledfx.app/en/latest/

**Remotes and plugs**
- https://www.sofabaton.com/product/x2/ · https://www.onesmartcrib.com/sofabaton-comparison-chart/ · https://community.home-assistant.io/t/sofabaton-x-local-home-assistant-integration-for-the-x1-x1s-and-x2/1025412
- https://statusgator.com/services/logitech/harmony-service · https://www.ebay.com/p/4028673631 · https://www.ebay.com/p/219502522 · https://www.unfoldedcircle.com/updates/meet-remote-3 · https://www.home-assistant.io/integrations/tplink/

**Bose input cable**
- https://www.hometheatershack.com/threads/acoustimass-10-series-iii-subwoofer-to-receiver-connection-cable.72149/ · https://www.audio-digital.net/b-pages/bose-acoustimass-15-audio-input-cable.html · https://www.manualslib.com/manual/19601/Bose-Acoustimass-15.html?page=10 · https://www.manualslib.com/manual/394997/Bose-Acoustimass-10-Series-Iv.html?page=9
- https://forum.allaboutcircuits.com/threads/converting-proprietary-bose-link-connectors-to-standard-rcas.110329/ · https://www.amazon.com/Xetilmo-Subwoofer-Receiver-acoustimass-Speaker/dp/B0CTXZD1JY · https://www.ebay.com/p/697783983 · https://www.l-com.com/d-sub-solder-cup-d-sub-connector-db15-female

**Other:** older TV and light figures also appear in the component pages' research ([Vizio §9.3](reference/entertainment/vizio-vs420lf1a.md#93-good-value-picks-us-prices-approximate-as-of-sept-2026-they-move-a-lot), [reactive-light §4](reference/entertainment/reactive-light.md#4-comparison-table)); see their Sources sections. Smart-plug, DAC, HA-host and cable prices are marked unverified above; the web-search budget ran out before they could be checked.

*Compiled 2026-09-24. Prices move weekly; items marked "unverified" weren't confirmed from a primary source.*
