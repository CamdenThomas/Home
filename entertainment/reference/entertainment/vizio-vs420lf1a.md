# Vizio VS420LF1A: 42" 1080p LCD HDTV

> **TL;DR**: A late-2008, 42", 1920x1080, **60 Hz** LCD. It has an LG Display S-IPS panel with a **fluorescent (EEFL) backlight**, not LED. There are 3x HDMI 1.3 inputs (HDCP 1.x) and a VGA input that accepts 1920x1080. It has **no HDMI-CEC, no ARC, no network, no apps and no documented control protocol**. The speaker bar with the bronze grille is **part of the cabinet and can't be removed**. Turn the speakers off with *Menu > Audio > Speakers > Off*. The only practical way to automate power from a PC is **IR** (NEC protocol, device 0x04). It's a fine 1080p screen for an Xbox One and a PC. Anything newer (4K, HDR, VRR, eARC) needs a new TV, and the old Denon limits how much a new TV can do.

Legend: facts from the Vizio user manual or service manual are stated plainly. Anything I couldn't confirm is marked **(unverified)**. My own calculations or inferences are marked **(est.)**.

---

## 1. Overview

| Item | Value | Source / note |
|---|---|---|
| Model | VS420LF1A (also listed as "VS420LF"). Service manual pairs it with the **VW42L FHDTV10A** chassis | Service manual cover |
| Released | **Late 2008.** The user manual is dated 10/22/2008. Warehouse-club sales at about $698 to $700 were reported in Nov 2008. Last ship date was **Sept 2009** | Manual; AnandTech; HDTVSolutions |
| MSRP | **$829** (HDTVSolutions listing, unverified). Street price was $599 to $700 at Costco, Sam's and Woot | HDTVSolutions, Woot, AVS/eBay reviews |
| Size | 42" class (42.02" viewable), 16:9 | Manual, Woot |
| Panel | **LG Display LC420WUE-SAA1**, a-Si TFT, **S-IPS**, normally black, matte (haze 13%, 3H hard coat). Active area 930.24 x 523.26 mm (36.6" x 20.6") | Service manual model string "FHDTV10A_**LGD-WUE-SAA1**" plus the TWScreen panel datasheet. The panel table in the service manual is a copy-paste error (it names a CMO 21.6" part). Individual units could use a different panel **(unverified)** |
| Backlight | **Fluorescent: EEFL (external-electrode fluorescent lamps), 18 lamps**, driven by an inverter. The TV's "Backlight" control "adjusts the lamp current". Not LED, not local dimming | Panel datasheet; manual p.39; service manual (inverter connectors CN4/CN5) |
| Native resolution | **1920 x 1080** (pixel pitch 0.4845 mm) | Manual spec |
| Refresh rate | **60 Hz** (no 120 Hz, no motion interpolation). The panel datasheet lists 60 Hz, and period forum posts say the VS420 was cheaper because it lacked 120 Hz | Panel datasheet; AVS/eBay reviews |
| Bit depth / colors | 8-bit, 16.7 M colors | Manual |
| Contrast | 1000:1 typical (panel datasheet: 1300:1), "DCR" dynamic 5000:1 | Manual; panel datasheet |
| Brightness | 500 cd/m² typical (at maximum backlight) | Manual |
| Viewing angle | 178° H/V (IPS, so it holds color well off-axis) | Manual |
| Response time | 5 ms GtG (panel spec; retail listings say 5 or 8 ms) | Panel datasheet; HDTVSolutions |
| Input lag | **Unknown.** No published measurement found. A Game picture mode exists. Expect "2008 TV" lag of roughly 30 to 60 ms **(unverified, est.)** | n/a |
| Power | **250 W max**, standby < 0.5 W (service manual says < 1 W). Typical on-mode draw isn't published. Probably about 150 to 200 W at moderate backlight **(est.)** | Manual; service manual |
| Voltage | 100 to 240 VAC, 50/60 Hz, IEC power inlet | Manual |
| Speakers | 2 x 10 W, in the bottom bar behind the bronze grille | Manual |
| Panel life | 50,000 h to half brightness | Manual |
| Made in | Mexico (assembled) | AnandTech forum spec copy |

### Dimensions and weight

| Configuration | W x H x D | Weight |
|---|---|---|
| With stand | **40.5" x 28.4" x 9.7"** (1028 x 722 x 245 mm) | **48.1 lb** net |
| Without stand | **40.5" x 27.3" x 3.9"** | **46.0 lb** |
| Shipping box | n/a | 61 lb gross |
| Thinnest cabinet section | about 2.5" (HDTVSolutions) | n/a |
| "Without speaker bar" | **Not applicable**, because the bar can't be removed (see section 4). Panel module outline is 983 x 576 mm (38.7" x 22.7"). The remaining cabinet height is roughly 4.6", mostly the speaker bar **(est.)** | n/a |

The service manual gives 21.2 kg (46.7 lb) net and 27.3 kg gross. The manual's unpacking section says "approximately 49 lbs".

### Wall mount

| Item | Value |
|---|---|
| Hole pattern | **600 mm (H) x 200 mm (V)**, holes in the center of the back panel |
| Screws | **Metric M8 x 1.25 mm pitch**. Length depends on the bracket plate |
| Stand removal | Lay face down on padding and remove **8 screws** |
| Mount size | 600x200 is an odd pattern, but most "up to 600x400" universal mounts accept it (the arms slide) |

---

## 2. Inputs and outputs

Rear panel, left to right as documented in the manual (p.11), plus the side panel (p.12):

| # | Port | Qty | Details |
|---|---|---|---|
| 1 | AC IN | 1 | IEC inlet |
| 2 | **SERVICE** | 1 | "Custom communication port for factory service only. Using it voids the warranty." HDTVSolutions lists it as **RS-232**, but **Vizio never published a command set**, so it isn't usable for power control **(unverified)** |
| 3 to 5 | **HDMI 1, 2, 3** | 3 | **HDMI v1.3 with HDCP** (HDCP 1.x, not 2.2). HDMI 3 pairs with the L/R RCA audio input for DVI sources. Accepts 480i/p, 720p, 1080i and **1080p**, plus PC timings (below) |
| n/a | HDMI-CEC | n/a | **Not supported.** It isn't mentioned in the manual or the spec sheet, and there are no CEC or "Link" items in any OSD menu (service manual OSD tree). This is typical of 2008 Vizios **(high confidence)** |
| n/a | ARC | n/a | **No.** ARC arrived with HDMI 1.4 in 2009 |
| 6 | **RGB PC (VGA, 15-pin D-sub)** plus 3.5 mm audio in | 1 | 1920x1080 @ 60 Hz supported with Vizio's reduced-blanking timing (section 3.3) |
| 7 to 8 | Component YPbPr plus L/R audio | 2 | Up to 1080i per the spec. 1080p over component is **(unverified)** |
| 9 | AV1 composite plus L/R | 1 | Rear |
| n/a | AV2 composite **or** S-Video plus L/R | 1 | **Left side**. S-Video takes priority over composite |
| 10 | RF coax (DTV/TV) | 1 | **ATSC (8VSB) / Clear QAM / NTSC** tuner. No CableCARD |
| 11 | **Optical digital audio out** (S/PDIF) | 1 | Menu options Off / Dolby Digital / PCM. The manual says it's "active for all audio (RF, Component, Composite and HDMI) inputs". Whether it passes DD 5.1 from HDMI sources (rather than only from the built-in tuner) is **(unverified)** |
| 12 | Analog audio out (L/R RCA) | 1 | Line level, not amplified |
| n/a | USB | ? | The service manual's connector list includes "USB", but the user manual has **no user USB port**. Don't count on USB for media, firmware or powering LED strips **(unverified)** |
| n/a | Network / Ethernet / Wi-Fi | 0 | None |
| n/a | Headphone | 0 | None documented |

Input cycle order (INPUT button): TV > AV1 > AV2/S-Video > Comp1 > Comp2 > RGB > HDMI1 > HDMI2 > HDMI3.

---

## 3. Picture settings

### 3.1 Every menu option (from the service manual OSD tree and the user manual, ch.4)

**PICTURE** (TV, AV, Component and HDMI inputs)

| Setting | Range / options | What it does |
|---|---|---|
| Picture Mode | Custom / Standard / Movie / Game | Presets. All sliders stay adjustable in every mode |
| Backlight | 0 to 100 | Lamp current (overall light output). Doesn't change black or white *level*, only overall brilliance |
| Brightness | 0 to 100 | Black level |
| Contrast | 0 to 100 | White level |
| Color | 0 to 100 | Saturation |
| Tint | -32 to +32 | Hue |
| Sharpness | 0 to 100 | Edge enhancement |
| Color Temperature | Cool (**default, 9300K**) / Normal / Warm / Custom (R/G/B gain) | The spec lists 9300K, 6500K and 5400K presets. Mapping Normal to 6500K and Warm to 5400K is likely **(unverified)** |
| Advanced Video > DNR | Off / Low / Medium / Strong | Noise reduction |
| Advanced Video > Black Level Extender | On / Off | Crushes near-black for "punch" |
| Advanced Video > White Peak Limiter | On / Off | Clamps peak whites |
| Advanced Video > CTI | Off / Low / Medium / Strong | Color transient "sharpening" |
| Advanced Video > Flesh Tone | On / Off | Skin/sky color bias |
| Advanced Video > Adaptive Luma | On / Off | Raises average picture level on dark scenes |
| Advanced Video > DCR | On / Off | Dynamic contrast (backlight follows content) |

**PICTURE** (RGB/VGA input only): Auto Adjust (Auto Picture), Backlight, Brightness, Contrast, Color Temperature (**Custom / 6500K / 9300K**, default 9300K), H-Size (0 to 255), H-Position, V-Position, Fine Tune (0 to 31, phase).

**AUDIO**: Volume, Bass, Treble, Balance (-50 to +50), Surround (On/Off), **Digital Audio Out (Off / Dolby Digital / PCM)**, **Speakers (On/Off)**, Lip Sync (0 to 5).

**SETUP**: Language, Sleep Timer (Off/30/60/90/120), **Wide** (aspect), Input Naming, CC settings, H/V Position (AV/Component/HDMI), Reset All.

**Wide (aspect) modes**: Normal (4:3 pillarbox), Wide, Zoom, Stretch, Panoramic. **There is no "Just Scan", "Dot-by-Dot", "Full Pixel" or "1:1" mode**, and no HDMI Black Level / RGB Range option.

### 3.2 Recommended settings

No professional ISF or RTINGS calibration was ever published for this exact model. A 2008 LCD TV Buying Guide review of the sibling **VW42LF** (same Vizio 42" FHD platform) calibrated to D65 and recommended **Backlight 22 to 32** depending on room light. Vizio's own "fine tuning for home use" step says to set Picture Mode **Standard** and Color Temp **Normal**. Use the table below as a starting point, then fine-tune with test patterns (for example the AVS HD 709 disc, or the Xbox/Windows HDR-off calibration screens).

| Setting | Movies (dim room) | Gaming (Xbox) | PC desktop (VGA) |
|---|---|---|---|
| Picture Mode | Movie | **Game** | n/a (VGA has its own menu) |
| Backlight | 20 to 35 (dark) / 50 to 70 (bright) | to taste | 30 to 50 |
| Brightness | ~50. Set so the near-black bars (17 to 25) are just visible | same | Set with a black-level pattern |
| Contrast | ~45 to 55. Back off until whites 230 to 234 still separate | same | same |
| Color | ~50 (default) | same | n/a |
| Tint | 0 | 0 | n/a |
| Sharpness | **Low** (0 to 10). Raise until ringing appears, then back off (unverified neutral point) | Low | n/a |
| Color Temp | **Warm** (or Normal, then trim R/G/B with a meter) | Warm/Normal | **6500K** |
| DNR | Off (HD) / Low (SD/OTA) | Off | n/a |
| Black Level Extender | Off | Off | n/a |
| White Peak Limiter | Off | Off | n/a |
| CTI | Off | Off | n/a |
| Flesh Tone | Off | Off | n/a |
| Adaptive Luma | Off | Off | n/a |
| DCR | Off (avoids backlight pumping) | Off | n/a |
| Wide | Wide (16:9 sources) | Wide | n/a |

Settings are stored **per input** for aspect and volume (manual troubleshooting page). Whether picture settings are per-input is **(unverified)**; the VW42LF review says there are "no discrete picture settings per input". Assume they may be global, and write down your Movie and Game values.

### 3.3 PC use and 1:1 pixel mapping

* **VGA (RGB PC) is the documented 1:1 path.** Vizio says to use "VESA 1920x1080 @ 60 Hz" with its **reduced-blanking timing at 136.5 MHz**. Run *Auto Adjust* once, then *Fine Tune* (phase) on a pixel-checkerboard pattern until shimmer disappears.
  * Timing from the VS420LF1A manual p.28: H total 2048, V total 1111, 66.65 kHz, 60 Hz, 136.5 MHz. The porches below come from the sibling VS42L manual (same timing): **H 1920/32/32/64, V 1080/1/3/27**. Sync polarity: the preset table says +H +V, while the RB table appears to say negative. Most panels ignore polarity, but try + first.
  * Linux/X11 modeline:
    ```
    Modeline "1920x1080_vizio" 136.50 1920 1952 1984 2048 1080 1081 1084 1111 +hsync +vsync
    ```
    Windows: Intel Graphics Command Center, Custom Resolution, same numbers.
  * Other presets: 640x480@60/75, 720x400@70, 800x600@60/72/75, 1024x768@60/70/75, and (on the sibling manual) 1360x768@60.
  * Catch: the **OptiPlex 7060 has no native VGA output** (Intel UHD 630: DP 1.2 x2, plus HDMI 1.4 on MT/SFF chassis; check yours). You'd need an active DisplayPort-to-VGA adapter that can handle 136.5 MHz. Analog is also slightly soft.
* **HDMI from a PC.** The spec sheet lists "Computer 640x480 ... 1920x1080 via VGA **or HDMI**". There's no overscan-off control, though. Whether HDMI 1080p is shown 1:1 or overscanned about 3 to 5% is **(unverified)** for this model. **Test it:** display a 1-pixel border test image (for example from lagom.nl or `testufo.com`). If the edges are cropped, either use VGA or set GPU underscan (which rescales, so text gets softer).
* **RGB range over HDMI**: there's no TV setting. A 2008 consumer TV almost certainly expects **Limited (16 to 235)** for CEA video timings such as 1080p60 **(unverified)**. If blacks look gray, set the PC to Full. If shadow detail is crushed, set it to Limited. Pick whichever passes a black-level (PLUGE) pattern. Intel: *Graphics Command Center > Display > Color > Quantization Range*. Linux: `xrandr --output HDMI-1 --set "Broadcast RGB" "Limited 16:235"` (X11) or the compositor's color settings.
* Aspect for PC: use **Wide** (never Zoom, Panoramic or Stretch).

---

## 4. The speaker bar

| Question | Answer |
|---|---|
| Where is it? | Bottom of the cabinet, behind a **bronze speaker grille** under the piano-black bezel (Vizio's "V-shaped", under-mounted speaker design). 2 x 10 W drivers |
| Detachable? | **No.** Unlike some later sets that shipped with a separate bar, the VS420LF1A's speakers are **built into the one-piece cabinet**. The service manual's disassembly procedure (base: 8 screws; rear cover: **24 screws**; main shield: 10 + 2 + 6 screws + 2 hex standoffs) shows the speakers wired internally to the **main board connector J6**. No detachable speaker module, bracket or cable exists. Vizio never supported removal |
| Can it be cut off? | Only by opening the TV and modifying the front bezel. Not recommended: the bezel frames the panel, there are high voltages (inverter, PSU), and the result would look worse. **Don't.** |
| Silencing it (supported) | **Menu > Audio > Speakers > Off.** The Speakers setting appears in the Audio menu of the TV, AV, Component, HDMI and RGB inputs. Vizio recommends exactly this "so that the sound... will be routed through your Receiver/Amp" |
| Silencing it (internal) | Unplugging the speaker cable at **J6** on the main board is a no-cost, reversible step if you open the set for another repair. It isn't needed otherwise |
| Hiding it (cosmetic) | Matte black fabric or vinyl over the grille. Bias lighting also draws the eye to the screen. A new TV with no speaker bar is the real fix |

**For this system**: set Speakers = Off once. Leave the TV's own volume alone (it only affects the internal speakers and the analog out). All audio should go to the Denon (see section 8).

---

## 5. Remote, IR codes and control options

### 5.1 Stock remote and universal codes

* Stock remote: **Vizio VR2** (2 x AA). Range about 30 ft, ±30° horizontal, ±20° vertical.
* Cable/satellite and universal remote codes from the manual: **5-digit 11758, then 10178, then 01377. 4-digit 1758 or 0178. Dish/EchoStar 3-digit 627.** Usually only power, volume and mute work.
* Other universal codes: many "Vizio" code lists work (Logitech Harmony DB: "Vizio VS420LF1A" or "VS420LF" if present, **unverified**).

### 5.2 IR protocol (for PC automation)

All Vizio TVs since about 2006 use **NEC1, device 4 (address byte 0x04, complement 0xFB)**. Functions from the IRDB for the same-era Vizio VX37L / generic Vizio TV:

| Function | NEC function # (dec / hex) | 32-bit NEC code (LSB-first bytes: addr, ~addr, cmd, ~cmd) |
|---|---|---|
| **Power toggle** | 8 / 0x08 | 04 FB 08 F7 |
| Vol + / - | 2 / 3 | 04 FB 02 FD / 04 FB 03 FC |
| Mute | 9 | 04 FB 09 F6 |
| Ch + / - | 0 / 1 | n/a |
| Input (cycle) | 47 / 0x2F | n/a |
| HDMI (cycles HDMI 1 to 3) | 198 / 0xC6 | n/a |
| RGB (VGA) | 152 / 0x98 | n/a |
| Component | 90 / 0x5A | n/a |
| AV | 81 / 0x51 | n/a |
| TV | 214 / 0xD6 | n/a |
| Menu / OK / Up / Down / Left / Right / Exit | 67 / 68 / 69 / 70 / 71 / 72 / 73 | n/a |
| Wide (aspect) | 119 | n/a |
| Sleep | 14 | n/a |
| **Discrete Power ON** | 42 / 0x2A | 04 FB 2A D5 (**unverified on this 2008 model**) |
| **Discrete Power OFF** | 37 / 0x25 | 04 FB 25 DA (**unverified**) |
| Discrete HDMI 1 / 2 / 3 | 129 / 130 / 131 (0x81 to 0x83) | **unverified** on this model |

The discrete codes come from Just Add Power's Vizio Pronto table (decoded). They're documented for newer Vizios. Test them. If they don't work, use **Power toggle** combined with **state detection** (next section).

Pronto for **Power ON** (discrete, from Just Add Power):
```
0000 006D 0022 0002 0157 00AC 0015 0016 0015 0016 0015 0041 0015 0016 0015 0016 0015 0016 0015 0016 0015 0016 0015 0041 0015 0041 0015 0016 0015 0041 0015 0041 0015 0041 0015 0041 0015 0041 0015 0016 0015 0041 0015 0016 0015 0041 0015 0016 0015 0041 0015 0016 0015 0016 0015 0041 0015 0016 0015 0041 0015 0016 0015 0041 0015 0016 0015 0041 0015 0041 0015 0689 0157 0056 0015 0E94
```

### 5.3 Automation options from the PC (Windows/Fedora)

| Method | Works on this TV? | Notes |
|---|---|---|
| **HDMI-CEC** | **No** | The TV has no CEC. (A Pulse-Eight USB-CEC adapter is only worth buying for a *new* TV.) |
| **RS-232** | **No (practically)** | The "SERVICE" port is factory-only with no public protocol |
| Network / IP control | No | No network port |
| **IR blaster**: USB IR transceiver + LIRC/`ir-ctl` on Fedora | **Yes** | For example, a Linux-supported USB IR (`ir-ctl -S nec:0x04 ...` style scancodes; check your driver's format), or **ESP32 + IR LED running ESPHome** (`remote_transmitter`, `transmit_nec: address 0xFB04, command 0xF708`, where ESPHome uses 16-bit addr/cmd including complements, **verify byte order**), or a **Broadlink RM4 mini** (learn the codes from the VR2 remote) driven by Home Assistant or `python-broadlink` |
| On/off **state detection** | Indirect | No feedback channel. Use a **smart plug with power metering** (TV on is roughly 100 to 200 W, standby < 1 W), a light sensor on the "VIZIO" logo LED (white = on, orange = standby), or EDID/hotplug on HDMI (unreliable) |
| Cutting mains power with a smart plug | Not recommended | Plasma/LCD sets of this era normally come back in standby after power loss, not "on" (**unverified**), and repeated hard power cuts stress the PSU |

Practical recipe: **ESP32 IR blaster + power-metering plug**, orchestrated by Home Assistant. On the PC, a script or HA automation sends "TV ON", or toggles only if metering shows < 5 W. The same blaster can also send the Denon's IR codes. That solves the "PC can't power the TV/AVR" problem for both devices.

---

## 6. Known issues, failure modes and firmware

| Symptom | Likely cause | Notes |
|---|---|---|
| Blank screen at first power-up, OK after off/on; relay clicking; no power | **Power supply board electrolytic capacitors** (bulging/leaking), typical of 2008-era Vizio | Recap or replace the PSU. Look for domed caps near the standby/12 V sections |
| **Sound but black screen**, or the picture flashes on then goes dark | **Backlight: EEFL lamps or inverter** (service manual inverter connectors CN4/CN5), or less often T-Con/LVDS | Shine a flashlight on the screen. If the image is faintly visible, it's the backlight/inverter. Otherwise check T-Con and LVDS (J7) |
| Dim, pinkish, uneven picture after years | Aging fluorescent lamps (rated 50,000 h to half brightness) | Normal wear. Raise Backlight to compensate |
| Unresponsive, stuck on logo, erratic | **Main board 3642-0552-0150 (board 0171-2271-2813)**, also used in VW42LF/VW42L HDTV10A | Used or refurbished boards are about $30 to $80 (eBay/ShopJimmy/TVPartsGuy) **(est.)**. Some listings mention EEPROM U18 |
| HDMI "no signal", sparkles, or handshake failure | HDMI 1.3 / **HDCP 1.x only**; **EDID** EEPROM corruption (the service manual has a "Trouble of EDID reading" flowchart); marginal cables; the old Denon's HDMI repeater | Use short, high-quality cables. Power-on order: **TV first, then AVR, then source.** Force the source to 1080p60 8-bit. HDCP 2.2 sources (4K-capable) negotiate down to HDCP 1.4 at 1080p |
| Garbled/lines on digital cable | Weak QAM signal | From user reviews |

**Firmware**: there are no user-installable firmware updates. Vizio serviced these sets through the factory SERVICE port **(unverified)**. There's no network, so it gets no updates, no ads and no telemetry.

---

## 7. Compatibility with the rest of the system

### 7.1 Xbox One
* Settings > General > TV & display options:
  * **Resolution 1080p**
  * **Video fidelity > Refresh rate 60 Hz**
  * **Allow 4K** off (automatic)
  * **Allow HDR** off (not available anyway)
  * **Color depth 24 bits (8-bit)**
  * **Color space: Standard (recommended)** (limited range, which is what the TV expects)
  * **Allow 24 Hz: Off** (1080p24 acceptance isn't documented)
  * **Allow 50 Hz: Off**
* TV side: Picture Mode **Game**, all Advanced Video processing Off, Wide aspect.
* **Xbox "TV & A/V power" / HDMI-CEC: won't work** (no CEC on the TV). The Kinect IR-blaster feature (discontinued) could once send Vizio IR codes.
* The Xbox audio problem noted in the README (DD vs stereo): that's between the Xbox and the Denon. The TV isn't involved as long as its speakers are off.

### 7.2 Dell OptiPlex 7060
* Best image: **HDMI (1.4 port on MT/SFF) or DP-to-HDMI cable**, 1920x1080 @ 60 Hz. Test for overscan (section 3.3). If it overscans, use an active DP-to-VGA adapter with the Vizio 136.5 MHz modeline.
* Set the Intel quantization range to match the TV (probably Limited), and scaling to 100% on a 42" at couch distance (125 to 150% for couch use).
* Audio for Qobuz shouldn't go through the TV. Send it to the Denon directly (see the Denon page).

### 7.3 HDMI through the Denon AVR-3806
* The 3806 is a 2005 HDMI 1.1-era repeater (2 in / 1 out) with **no CEC and no ARC**. Forum reports: multichannel PCM over HDMI is flaky, and 4K isn't possible.
* **Chain A**: Xbox/PC > Denon HDMI in > Denon HDMI out > TV HDMI 1. This works at 1080p for most users, but it's a common place for handshake problems.
* **Chain B (more robust)**: sources go **directly to the TV's HDMI 1 to 3**, and audio goes to the Denon by **optical/coax** (Xbox One has optical out) or by a separate cable from the PC. The TV's own optical out only matters for the built-in OTA tuner.
* No ARC exists anywhere in this chain, so the TV can't send HDMI audio back to the Denon.

### 7.4 Bias lighting / ambient (Ambilight-style) lighting

| Measurement | Value |
|---|---|
| Overall cabinet (no stand) | 40.5" W x 27.3" H |
| **Outer perimeter** | 2 x (40.5 + 27.3) = **135.6" (about 3.44 m)** |
| Strip run inset about 1.5" from each edge on the back | 2 x (37.5 + 24.3) = **about 124" (3.15 m)** **(est.)** |
| Screen (active area) | 36.6" x 20.6" (perimeter about 114") |
| Bottom-edge option | Skip the bottom run (speaker-bar side, often blocked by the stand/furniture): top + 2 sides is about **75 to 85"** **(est.)** |
| Rear surface | Plastic rear cover, textured, with a raised central electronics hump. The thinnest section is about 2.5"; the VESA area is 3.9" deep. Clean with isopropyl alcohol before using adhesive LED strip. Keep strips clear of the **vent slots** (fluorescent backlight + inverter run warm) |
| Ideal wall gap | About 4 to 10" behind the TV for a soft halo. On the stock stand the TV sits about 3" off the wall, which is fine |
| Power for LEDs | Don't rely on a TV USB port (none documented). Use a 5 V/12 V PSU or the controller's own supply |

Options:
1. **Simple bias light** (6500K white, CRI > 90, e.g. MediaLight/LX1): best for movie contrast perception, and it needs no signal.
2. **Screen-reactive**: an HDMI sync box (e.g. Philips Hue Play HDMI Sync Box, Govee AI Sync Box). Put it between Denon HDMI out (or the source) and the TV. At 1080p/HDCP 1.4 this is fine, but it adds one more HDMI handshake hop.
3. **PC-driven**: HyperHDR/Hyperion on Fedora (or Prismatik/Ambibox on Windows), with a WLED/ESP32 or Adalight strip. It reacts to PC content natively, and to the Xbox via an HDMI splitter plus USB capture card. It can also do **sound-reactive** modes for Qobuz playback (WLED audio-reactive with a microphone, or line-in from the Denon's zone/record out).

LED count example: 60 LED/m x 3.15 m is about 190 LEDs (e.g. top 57, sides 34 each, bottom 57 or skipped) **(est.)**.

---

## 8. How it fits this system

* **Role**: a dumb 1080p60 display. It has no apps, CEC or network, which is actually fine because the Xbox handles streaming and the PC handles everything else.
* **Audio**: TV speakers **Off**. Nothing should rely on the TV for audio. The Denon gets audio straight from the sources (HDMI via the Denon, or optical from the Xbox).
* **Video**: HDMI 1 = Denon HDMI out (if routing through the AVR) **or** Xbox direct. HDMI 2 = PC. Use *Input Naming* ("XBOX", "PC") so the banner shows friendly names.
* **Power automation**: IR only. An ESP32/Broadlink blaster that sends Vizio NEC codes and Denon codes, plus a power-metering plug for state, gives the PC one-click "theater on/off".
* **Weak spots**: 1080p/60 Hz ceiling, no HDR, weak blacks (IPS + fluorescent backlight, about 1000:1), a 17-year-old PSU and backlight, and the speaker bar. None of these can be fixed in place.
* **Keep or replace?** Keep it while it works if the Xbox One is an original (1080p only) and the Denon stays. A 4K TV gives the biggest gains once you have a 4K source (Xbox One S/X for 4K streaming, or a newer PC GPU), and ideally a new AVR.

---

## 9. Upgrade path (2026)

### 9.1 What a replacement fixes

| Pain point | 2026 mid-range TV |
|---|---|
| 1080p only | 4K (3840x2160). 8K has almost no content, so skip it |
| No HDR | HDR10 / HDR10+ / Dolby Vision, 1000 to 3000+ nits on Mini-LED |
| Weak blacks | Mini-LED local dimming or OLED |
| 60 Hz, unknown lag | 120 to 165 Hz, VRR/FreeSync, ALLM, about 10 ms or less in game mode |
| No CEC/ARC | HDMI-CEC + **eARC** (lossless Atmos/TrueHD out to a new AVR) |
| Speaker bar | Thin bezels. Built-in speakers are hidden (down-firing) |
| No control | IP control, CEC, apps and Home Assistant integrations (LG webOS, Google TV, Sony) |

### 9.2 Size vs viewing distance (4K)

| Seat distance | Recommended size (about 30 to 40° field of view) |
|---|---|
| 6 ft (1.8 m) | 55" |
| 7 ft (2.1 m) | 55 to 65" |
| 8 ft (2.4 m) | 65" |
| 9 to 10 ft (2.7 to 3 m) | 75" |
| 11 ft+ | 85" |

Check wall/stand width. A 65" is about 57" wide, and a 75" is about 66" wide.

### 9.3 Good-value picks (US prices, approximate, as of Sept 2026; they move a lot)

| Model | Type | Why | Approx. price |
|---|---|---|---|
| **TCL QM6K** (2025, still sold) | QD-Mini-LED, 144 Hz | Best budget value. 2x HDMI 2.1 (4K144, 1080p288 VRR), eARC (on an HDMI 2.0 port), DV + HDR10+, Google TV | 55" about $500 to 600 on sale. 65" about $700 to 800 |
| **TCL QM7L** (2026) | SQD Mini-LED | Tom's Guide's "top Mini-LED value of the year" | 55" from $1,200 list, about $1,000 on sale |
| **Hisense U7SG** (2026) | Mini-LED, 165 Hz, up to about 3000 nits | Very bright, good for daytime rooms and sports | 55" $1,299 / 65" $1,499 list (sales lower) |
| **LG C5 OLED** (2025 clearance) or **LG C6** (2026) | WOLED | Perfect blacks, 4x HDMI 2.1, excellent CEC/eARC, 42" size available | C6 55" about $1,600. C5 heavily discounted |
| **Samsung S90F OLED** (2025) | QD-OLED | Often cheaper than the LG C-series on sale. **No Dolby Vision** | Varies. Check sale price |
| **Sony Bravia 7 / 7 II** (2026) | Mini-LED | Best processing and upscaling in the class (good for 1080p Xbox One and streaming) | 65" about $1,600 |

### 9.4 eARC/CEC and the old Denon: pitfalls

* **Keeping the AVR-3806**:
  * It has **no ARC/eARC, no CEC, no HDCP 2.2 and no 4K passthrough**. Route **all 4K sources directly to the new TV**.
  * Get TV audio to the Denon via the **TV's optical out**, which is limited to **Dolby Digital 5.1 / DTS (brand-dependent) / PCM 2.0**. There's no TrueHD/Atmos/multichannel PCM. Check the TV passes DD 5.1 over optical: most LG, Sony, Samsung and TCL models do, but some strip DTS.
  * The Denon won't follow TV power or volume (no CEC). Keep the **IR blaster** plan.
  * The TV's own streaming apps will work at DD 5.1 over optical.
* **Upgrading the AVR too**: buy a receiver with **HDMI 2.1 + eARC** (e.g. Denon AVR-X1800H/X2800H class). Then all sources plug into the TV (or the AVR), and the TV sends lossless audio via eARC. CEC links power and volume, so one remote or one Home Assistant command controls everything. The Xbox DD/stereo switching headache also goes away (the Xbox can send multichannel LPCM or Atmos).
* **PC to 4K TV**: the OptiPlex 7060 (Intel UHD 630) tops out at **4K60 via DisplayPort 1.2**. Its HDMI 1.4 port is only 4K30. Use an **active DP-to-HDMI 2.0 adapter** for 4K60 (HDR on Linux is still rough). For CEC from the PC on a new TV, add a **Pulse-Eight USB-CEC adapter** (libcec, works on Fedora).
* Pick a TV with **HDMI inputs ≥ 3** if the AVR stays (Xbox, PC, spare). eARC ports on some TCL/Hisense sets are the HDMI 2.0 port, so plan which device goes where.

---

## Sources

* Vizio VS420LF1A user manual (v10/22/2008), ManualsLib: https://www.manualslib.com/manual/336838/Vizio-Vs420lf.html (rear panel p.11, remote codes p.14, PC timings p.27 to 28, OSD p.37 to 61, specs p.66, wall mount p.7)
* Vizio VS420LF1A product manuals index: https://www.manualslib.com/products/Vizio-Vs420lf1a-6072343.html
* Service Manual: Vizio VS420LF1A (VS420LF1A_LGD / VW42L FHDTV10A_LGD), Internet Archive: https://archive.org/details/Vizio_VS420LF1A (full text: https://archive.org/stream/Vizio_VS420LF1A/Vizio_VS420LF1A_djvu.txt)
* Vizio legacy manual CDN (the file named for this model actually contains the predecessor VS42L FHDTV10A manual; used for the reduced-blanking porch values): https://cdn.vizio.com/manuals/kb/legacy/vs420lf1amanual.pdf
* LG Display LC420WUE-SAA1 panel spec, TWScreen: https://www.twscreen.com/en/lcdpanel/7824
* HDTVSolutions VS420LF spec page (MSRP, last ship date, RS-232 listing): http://www.hdtvsolutions.com/VIZIO-VS420LF.htm
* HDTVSolutions reviews: http://www.hdtvsolutions.com/VIZIO-VS420LF-reviews.htm?review_id=1727
* Woot listing (dimensions, weights, I/O): https://www.woot.com/offers/vizio-42-1080p-lcd-hdtv-nov-17
* AnandTech forum, VS420 at Sam's Club (2008 pricing): https://forums.anandtech.com/threads/vizio-vs420-42-inch-1080p-lcd-hdtv.239339/
* eBay product reviews: https://www.ebay.com/urw/Vizio-VS420LF1A-42-1080p-HD-LCD-Television/product-reviews/77208564
* AVS Forum VS420LF1A thread (access-restricted; cited via search excerpts): https://www.avsforum.com/threads/vizio-vs420lf1a.1085567/
* LCD TV Buying Guide, Vizio VW42LF review (sibling; backlight/calibration notes): https://reviews.lcdtvbuyingguide.com/lcdtvreviews/vizio-vw42lf-review.shtml
* Badcaps, "Vizio VS420LF1A: Attack of the Black Screen": https://www.badcaps.net/forum/troubleshooting-hardware-devices-and-electronics-theory/troubleshooting-tvs-and-video-sources/14052-vizio-vs420lf1a-attack-of-the-black-screen
* JustAnswer, VS420LF1A black screen with sound: https://www.justanswer.com/tv-repair/4e78x-vizio-black-screen-sound-vizio-42-inch-vs420lf1a.html
* Main board 3642-0552-0150 / 0171-2271-2813: https://www.shopjimmy.com/vizio-3642-0552-0150-0171-2271-2813-main-board-vs420lf1a-vw42lfhdtv10a-vw42lhdtv10a/ and https://www.tvpartsguy.com/products/vizio-vs420lf1a-main-board-0171-2271-2813-3642-0552-0150.html
* IRDB (Vizio NEC device 4 function list): https://github.com/probonopd/irdb/tree/master/codes/Vizio
* Just Add Power, Vizio IR control (discrete Pronto codes): https://support.justaddpower.com/kb/article/250-vizio-ir-control/
* Vizio support, CEC overview (newer models): https://support.vizio.com/s/article/CEC-Consumer-Electronics-Control?language=en_US
* Denon AVR-3806 HDMI audio discussion (Audioholics): https://forums.audioholics.com/forums/threads/avr-3806-dvd-2910-hdmi-audio-problems.16840/
* RTINGS TCL QM6K review: https://www.rtings.com/tv/reviews/tcl/qm6k
* Tom's Guide TCL QM7L review: https://www.tomsguide.com/tvs/qled-tvs/tcl-qm7l-review
* RTINGS TCL QM8L review: https://www.rtings.com/tv/reviews/tcl/qm8l
* Best Buy Hisense U7SG (2026): https://www.bestbuy.com/product/hisense-65-class-u7-series-miniled-qled-uhd-4k-hdr-smart-google-tv-2026/J3Z9Z42HT2
* RTINGS LG C6 OLED review: https://www.rtings.com/tv/reviews/lg/c6-oled-2026
* What Hi-Fi, Sony 2026 lineup: https://www.whathifi.com/tv-home-cinema/televisions/sony-2026-tv-lineup-everything-you-need-to-know-about-the-new-bravia-tvs
* Tom's Guide, best HDMI 2.1 TVs: https://www.tomsguide.com/best-picks/the-best-hdmi-21-tvs
