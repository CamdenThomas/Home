# Denon AVR-3806 A/V Receiver

> Reference page for the Denon AVR-3806 in the home entertainment system. Facts come from Denon's own documents where possible: the owner's manual, the info sheet, the archived 2005–2006 Denon USA product page, the official RS-232 protocol, the IR code sheet and the Audyssey FAQ. Claims that come from forums or single sources, or that are my own inference, are marked **(unverified)**.
>
> Last researched: 2026-09-24

---

## Table of contents

1. [Overview](#1-overview)
2. [Specifications](#2-specifications)
3. [Connections (every port)](#3-connections-every-port)
4. [HDMI behavior in detail](#4-hdmi-behavior-in-detail)
5. [Decoding and surround modes](#5-decoding-and-surround-modes)
6. [The Xbox Dolby Digital vs. stereo problem](#6-the-xbox-dolby-digital-vs-stereo-problem)
7. [Bass management](#7-bass-management)
8. [Audyssey MultEQ XT room correction](#8-audyssey-multeq-xt-room-correction)
9. [Recommended setup for this system](#9-recommended-setup-for-this-system)
10. [Control: RS-232, IR, 12 V trigger, automation](#10-control-rs-232-ir-12-v-trigger-automation)
11. [Known issues, failure modes, firmware](#11-known-issues-failure-modes-firmware)
12. [Tips, hidden features, and reset](#12-tips-hidden-features-and-reset)
13. [Limitations vs. goals, and the upgrade path](#13-limitations-vs-goals-and-the-upgrade-path)
14. [How it fits this system](#14-how-it-fits-this-system)
15. [Sources](#15-sources)

---

## 1. Overview

| Item | Value |
|---|---|
| Model | Denon AVR-3806 (black or silver) |
| Type | 7.1-channel A/V surround receiver with 7 amplifier channels |
| Released | Fall 2005. The info sheet is dated 2005-09-02 and the US manual was posted 2005-10-17. It sold through 2006. HiFi Engine lists "2005-07". |
| Original MSRP | **$1,299 USD** (archived Denon USA product page). HiFi-Wiki lists €1,399 for Europe. |
| Predecessor / successor | Replaced the AVR-3805. Succeeded by the AVR-3808CI in 2007. **(unverified: there was no "3807")** |
| Tier | Upper-midrange. In the 2005–06 Denon line it sat under the AVR-4306, AVR-4806CI and AVR-5805 flagships and over the AVR-2807, 2307CI, 1907 and lower models. |
| Made in | Japan |
| Used value (2026) | About **$75–$200** on eBay, depending on condition and whether it comes with the remote and the Audyssey mic. HiFi-Wiki saw $140–$180. **(price range unverified; it moves)** |
| Headline features when new | HDMI 1.1 switching (2 in, 1 out) with 1080p pass-through, analog-to-HDMI video conversion, Audyssey MultEQ XT with 6 measurement positions, HDCD decoding, DENON LINK 3rd edition, XM-Ready, Zone 2 and Zone 3, RS-232C, two 12 V triggers |

**In short:** in 2005 this was a very good receiver. Its amplifiers and room correction still hold up. The HDMI section is the weak point by today's standards. It is HDMI 1.1: no 4K, no HDR, no lossless or object audio (TrueHD, DTS-HD MA, Atmos, DTS:X), no CEC and no ARC.

---

## 2. Specifications

### 2.1 Amplifier

| Parameter | Rating (from Denon's info sheet) |
|---|---|
| Channels | 7, discrete, equal power |
| Rated power, 8 Ω (FTC-style) | **120 W + 120 W**, 20 Hz–20 kHz, 0.05 % THD. The same figure is given for the front, center, surround and surround-back pairs. |
| Rated power, 6 Ω | **160 W/ch**, 1 kHz, 0.7 % THD |
| THD | 0.05 % at rated power into 8 Ω. The info sheet notes that THD figures are for the power-amp stage. |
| Denon's archived product page | "Watts per channel 120, all channels rated @ 0.05 THD" |
| Denon's current archive page title | "7.1 Ch. **130W**", which is inconsistent with the manual and info sheet. Treat 120 W / 8 Ω as the real rating. |
| Amp assign | The two surround-back amp channels can be reassigned to **Front bi-amp**, **Front B**, **Zone 2** or **Zone 3** |
| Protection | Relay-controlled protection circuits for over-current, short circuit and over-temperature |
| Power consumption | 7.1 A at 120 V (US). 540 W for EU units. |
| Cooling | Passive. No internal fan is listed, and owners say it runs hot. **(no fan: unverified)** |

The rating is "120 W + 120 W" per pair. Denon does not publish an all-7-channels-driven figure, and real all-channel output will be lower, which is normal for receivers of this period.

### 2.2 Pre-amp, DAC and DSP

| Parameter | Value |
|---|---|
| DSP | **Analog Devices "Hammerhead" SHARC, 32-bit floating point** ("New DDSC-Digital" platform). The archived product page also lists a TI Aureus line, but that looks like a template carry-over from the 4806/5805, so it is **(unverified)**. |
| DACs | **Burr-Brown PCM1791, 24-bit/192 kHz** (archived Denon product page) |
| ADC | Burr-Brown PCM1804, 24-bit/192 kHz |
| Processing | AL24 Processing Plus on all channels, applied to PCM in Pure Direct, Direct, Stereo and Multi-Ch modes |
| Input sensitivity | Phono (MM): 2.5 mV / 47 kΩ. Line inputs: 200 mV / 47 kΩ. |
| Sub pre-out level | 1.2 V / 10 kΩ |
| Frequency response | 10 Hz–100 kHz (+1/−3 dB), Direct mode |
| S/N | 102 dB (IHF-A), Direct mode |
| Volume | −80 dB to +18 dB in 0.5 dB steps ("variable gain volume") |
| Crossover | 40, 60, 80, 90, 100, 110, 120, 150, 200, 250 Hz, global or per speaker ("Advanced") |
| Tone and EQ | Bass and treble, Cinema EQ, Night mode, D.Comp (dynamic range compression), Manual 9-band graphic EQ (the "Manual" Room EQ), Audyssey curves |
| Audio delay (lip sync) | 0–200 ms, stored per input |

### 2.3 Tuner

| | |
|---|---|
| FM | 87.5–107.9 MHz, 1.0 µV (11.2 dBf) usable sensitivity |
| AM | 520–1710 kHz, 18 µV |
| XM | "Connect-and-Play" XM-Ready with an optional antenna. The legacy XM service is effectively obsolete for this hardware **(unverified)**. |
| Presets | 56 random presets for AM, FM and XM, in blocks A–G |

### 2.4 Physical

| | |
|---|---|
| Dimensions | 434 W × 171 H × 429 D mm (17-3/32" × 6-47/64" × 16-57/64") |
| Weight | 17.5 kg (38 lb 9.3 oz) |
| Power cord | Detachable (IEC inlet) |
| Remote | RC-1024, a pre-programmed and learning EL-backlit touch-panel remote for 10 devices, plus a smaller sub-remote |
| Included mic | DM-S205 Audyssey setup microphone. It is **specific to this generation** and not interchangeable with the DM-S305 used by the 4806/5805. |

---

## 3. Connections (every port)

### 3.1 Audio inputs

| Port | Count | Notes |
|---|---|---|
| Analog stereo (RCA) | 9 + tuner | PHONO (MM), CD, DVD, VDP, TV, DBS, VCR-1, VCR-2, CDR/TAPE, and V.AUX on the front panel |
| Phono | 1 | MM only, with a ground terminal |
| 7.1 / 8-ch analog EXT. IN | 1 set | FL, FR, C, SL, SR, SBL, SBR, SW. For SACD/DVD-A players or external decoders. |
| Optical (Toslink) | 5 | Including 1 on the front panel. Assignable. |
| Coaxial (RCA) | 2 | Assignable |
| DENON LINK (3rd ed.) | 1 | Denon-proprietary LVDS link to matching Denon DVD/SACD players. Carries 24/96 6-ch or 24/192 2-ch LPCM, plus DSD. Of no use here. |
| HDMI in | **2** | HDMI 1.1. Carries **audio and video**. See section 4. |
| Setup mic | 1 | Front panel, 3.5 mm, for the DM-S205 only |
| XM antenna | 1 | Mini-DIN, for XM Connect-and-Play |
| AM / FM antenna | 1 each | FM is an F-connector |

### 3.2 Audio outputs

| Port | Count | Notes |
|---|---|---|
| Speaker terminals | 7 channels + Surround B | Binding posts that take banana plugs. Front A/B switching on the surrounds. |
| 7.1 pre-outs | 1 set | FL, FR, C, SL, SR, SBL, SBR, SW. Use them to add external amps or to tap the post-processing signal. |
| Subwoofer pre-out | Included above | Line level, 1.2 V |
| Zone 2 pre-out | 1 stereo pair | Variable level. **Analog sources only.** |
| Zone 3 pre-out | 1 stereo pair | Fixed level. **Analog sources only.** |
| REC OUT | 3 | VCR-1, VCR-2, CDR/TAPE. Analog only. Digital input signals are not converted to REC OUT. |
| Optical out | 2 | For digital recording of 2-ch digital sources (pass-through) |
| Headphone | 1 | Front 1/4" jack |

> **Important for the planned sound-reactive light:** the manual states that "Digital signals are not output from the ZONE2 and ZONE3 audio output terminals" and that analog REC OUT does not carry digital inputs. A light that needs the audio of the Xbox or the PC (both digital) therefore has to be fed from the **7.1 pre-outs**, for example a Y-splitter on the SUBWOOFER pre-out for a bass-driven light or on the FL/FR pre-outs. It can also listen with its own microphone. I have not verified whether the 3806 mutes its internal amplifiers when the pre-outs are in use. On most Denons of this era the pre-outs run in parallel with the amps. Test before relying on it.

### 3.3 Video

| Port | Inputs | Outputs | Notes |
|---|---|---|---|
| HDMI | 2 | 1 | 1080p pass-through. Converts analog inputs to HDMI. **No HDMI-to-analog down-conversion.** |
| Component (YPbPr) | 3 (assignable) | 2 (Monitor 1, Monitor 2) | 100 MHz bandwidth switching |
| S-Video | 7 | 3 (Monitor, VCR-1, VCR-2), plus Zone 2 video | |
| Composite | 7 | 3 (Monitor, VCR-1, VCR-2), plus Zone 2 video | |

Video conversion covers composite ↔ S-Video ↔ component, and composite, S-Video or component → HDMI. Analog sources go out over HDMI **at their original resolution**. The 3806 converts, but it is **not a scaler**: 480i stays 480i. Component can be down-converted to S-Video or composite only when the input is 480i.

### 3.4 Control

| Port | Notes |
|---|---|
| **RS-232C** | DB-9 **female, DCE**, straight-through. Pin 2 TxD, pin 3 RxD, pin 5 GND. 9600-8-N-1. See section 10. |
| IR Remote IN / OUT | 3.5 mm jacks for wired IR repeaters and room-to-room kits (Denon RC-616/617/618) |
| 12 V TRIGGER OUT | **2**, each assignable by zone, input and surround mode. The archived spec lists "2 / 25 mA", which is low current and only suitable for signal-type trigger inputs **(current rating unverified)**. |
| USB / Ethernet / network | **None.** The archived spec sheet marks RJ-45, Internet radio and USB flash drive with a dash (not present). |
| iPod | Supported through the optional Denon ASD-1R dock, controlled over the dock port. Largely irrelevant today. |

---

## 4. HDMI behavior in detail

This section is where the receiver interacts most with the Xbox, the PC and the TV.

| Question | Answer | Source |
|---|---|---|
| HDMI version | **1.1** | Manual, info sheet |
| Max video pass-through | **1080p** ("1080p HDMI switching") | Archived Denon USA page |
| Does it take audio from HDMI? | **Yes.** "The HDMI terminals also accept multi-channel digital audio input and the input signals can be output via amps." | Info sheet |
| Multichannel LPCM over HDMI? | **Yes.** The manual's HDMI input table lists DVD-Video LPCM, Dolby Digital, DTS and DVD-Audio LPCM/packed PCM. Owners have run PS3 5.1/7.1 LPCM into it. Multichannel PCM is handled in the **MULTI CH IN** mode family. | Manual p.20, forum reports |
| Dolby TrueHD / DTS-HD MA / DD+ / Atmos bitstream | **No.** These formats postdate HDMI 1.1 and this decoder. A source must decode them to LPCM first. | Inference from HDMI 1.1 spec and decoder list |
| SACD over HDMI | Not supported (DSD needs DENON LINK) | Manual |
| HDMI audio routing | Per input, **"AMP"** plays through the receiver's speakers and **"TV"** passes the audio on to the TV. Set it under *Video Setup → HDMI In Assign*. The same screen sets a fallback (ANALOG or EXT. IN) for when HDMI audio "unlocks". | Manual p.66–67 |
| Analog audio out over HDMI to the TV? | **No.** "Audio signals are only output from the HDMI monitor out terminal when audio signals are input to the HDMI input terminal." | Manual p.16 |
| HDCP | Supported (HDCP 1.x). No video is output if the display does not support HDCP. | Manual |
| Resolution handling | HDMI video passes through at its **original resolution**. The receiver does no scaling on HDMI, so source and display must agree. | Manual p.21 |
| On-screen display over HDMI | The menu reaches the HDMI output only through the analog-to-HDMI path, at **480i/576i**. It is **not overlaid on HDMI video**, so the menu cannot be seen while watching the Xbox or PC. That is a big part of why the interface feels clunky. | Manual p.15, forum reports |
| **CEC** | **None, confirmed.** "The AVR-3806 cannot be controlled by another device via the HDMI connector." | Manual p.21 |
| ARC / eARC | None. ARC arrived with HDMI 1.4 in 2009. Plugging the HDMI out into a TV's ARC port does **not** return TV audio. **(unverified: one Q&A site blames ARC/HDMI mis-wiring for a blown fuse)** | Spec timeline |
| HDMI in standby | **No pass-through while in standby.** The receiver must be on for any HDMI video to reach the TV. **(inference; HDMI standby pass-through appeared on much later Denons)** | |
| Cable length | Denon recommends ≤ 5 m for stable operation | Manual |

### 4.1 Modern sources (Xbox One, PC) through HDMI 1.1

- **Xbox One (any variant):** 1080p SDR over HDCP 1.x through an HDMI 1.1 repeater should work, because HDMI 1.1 carries 1080p60. I found **no first-hand report of an Xbox One through a 3806**, so test it. Possible problems: an HDCP handshake failure (black screen or snow), EDID quirks where the Xbox offers odd modes, and 4K on a One S or One X being unavailable (1080p is the ceiling). The Xbox's video-fidelity settings may need to be forced to 1080p. **(unverified)**
- **What HDMI gains for the Xbox:** the Xbox reads the receiver's audio EDID and offers **Stereo uncompressed, 5.1 uncompressed, 7.1 uncompressed and Bitstream** (Dolby Digital or DTS). Over optical it can only offer stereo PCM or bitstream, because optical carries no capability information.
- **Dell OptiPlex 7060:** the Intel UHD 630 outputs through DisplayPort, or HDMI on some configurations. A **passive DP++-to-HDMI adapter carries audio**, and Windows can then send 2-ch or up to 7.1 LPCM to the receiver. 1080p60 is fine. This is the cleanest way to get the PC's Qobuz audio into the receiver digitally, since the 7060 has no optical output. HDMI 1.1 carries 2-ch LPCM up to 24/192. Whether the 3806 accepts 192 kHz over HDMI (rather than only through DENON LINK) is **(unverified)**. 96 kHz is safe.
- **Hot-plug side effect:** when the receiver is off or on another HDMI input, the PC sees its display vanish and may rearrange windows or drop the audio device. That is one more reason to automate the receiver's power (section 10).

---

## 5. Decoding and surround modes

### 5.1 Decoders on board

Dolby Digital, **Dolby Digital EX**, **Dolby Pro Logic IIx** (Cinema, Music, Game), Pro Logic II (Cinema, Music, Game, Pro Logic), Dolby Pro Logic, **DTS**, **DTS-ES Discrete 6.1**, **DTS-ES Matrix 6.1**, **DTS 96/24**, **DTS Neo:6** (Cinema, Music), **HDCD**, and multichannel PCM. There is **no** THX, Dolby Headphone, AAC, TrueHD, DTS-HD, Atmos or DTS:X. The RS-232 protocol lists THX and Dolby H/P modes as "Invalid at AVR-3806".

Denon DSP simulation modes: Wide Screen (7.1), Super Stadium, Rock Arena, Jazz Club, Classic Concert, Mono Movie, Video Game, Matrix, Virtual, and 5CH/7CH Stereo. Direct modes: Pure Direct, Direct, Stereo, and Multi-Ch (Pure) Direct.

### 5.2 Which modes are available for which input (from the manual's tables, p.96–97)

Legend: ✅ selectable, ⭐ default when this signal arrives, ❌ not available. "SB" means the mode needs surround-back speakers.

| Surround mode | Analog | **LPCM 2-ch** | **DD 2.0** | DD 3/4/5-ch | **DD 5.1** | DD EX (flagged) | DTS 5.1 | DTS-ES | DTS 96/24 | **Multi-ch PCM** (HDMI LPCM, DVD-A) |
|---|---|---|---|---|---|---|---|---|---|---|
| Dolby PLIIx Cinema / Music / Game (SB) | ✅ | ✅ | ⭐ Cinema | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Dolby PLII Cinema / Music / Game, PL | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| DTS Neo:6 Cinema / Music | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Dolby Digital | ❌ | ❌ | ❌ | ⭐ | ⭐ | ✅ | ❌ | ❌ | ❌ | ❌ |
| Dolby Digital EX (SB) | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **DD + PLIIx Cinema / Music** (5.1 → 7.1, SB) | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| DTS Surround | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ⭐ | ✅ | ❌ | ❌ |
| DTS + PLIIx / DTS + Neo:6 (SB) | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ |
| Multi Ch In | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ⭐ |
| **Multi In + PLIIx Cinema / Music** (SB) | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Direct / Pure Direct | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ (uses Multi-Ch Direct) |
| Stereo | ⭐ | ⭐ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| DSP modes (Wide Screen, Stadium, Arena, Jazz, Classic, Mono Movie, Video Game, Matrix, Virtual) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 7CH Stereo (5CH Stereo if no SB) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Direct answers to the key questions:**

- **Can it apply PLIIx or Neo:6 to 2-ch PCM?** **Yes.** LPCM 2-ch and analog both allow every PLII, PLIIx and Neo:6 variant.
- **Can PLII be applied to a Dolby Digital 2.0 stream?** **Yes.** For DD 2-ch the default mode is **PLIIx Cinema**, and all PLII, PLIIx and Neo:6 variants are available.
- **Can it upmix DD 5.1 to 7.1?** **Yes**, with "Dolby Digital + PLIIx Cinema/Music" or with "Dolby Digital EX" (matrix). Both need the surround-back speakers enabled, and PLIIx Cinema needs 2 SB speakers. DTS 5.1 likewise gets DTS + PLIIx or DTS + Neo:6.
- **Can it apply PLII to DD 5.1, or to multichannel PCM that only has content in L/R?** **No.** Matrix decoders are offered only for 2-ch signals. A 5.1 stream, even one with silent center and surround channels, can only be decoded as 5.1 (optionally extended to 7.1), sent through a DSP hall mode, or spread with **7CH Stereo**.

### 5.3 Auto Surround Mode (per-input memory)

*Advanced Playback → Auto Surround Mode* remembers the **last mode used for each of four signal types, separately for each input**:

| Signal type | Factory default |
|---|---|
| Analog and PCM 2-ch | STEREO |
| DD or DTS **2-ch** | DOLBY PLIIx CINEMA |
| DD or DTS multichannel | DOLBY/DTS SURROUND |
| Multichannel PCM (and DSD) | MULTI CH IN |

So on the Xbox's input, pick PLIIx Game (or Neo:6 Cinema) **once** while 2-ch PCM is playing, and pick DD+PLIIx Cinema once while DD 5.1 is playing. After that the receiver switches between them automatically as the signal type changes. Pure Direct overrides this: when Pure Direct is active the mode does not change with the input signal.

---

## 6. The Xbox Dolby Digital vs. stereo problem

> **Update 2026-09-24 (owner tested):** with the Xbox on 5.1 uncompressed, stereo content arrives as 6-channel PCM with silent channels, and PLIIx is locked out, exactly as with DD. The current recommended fix (Xbox optical → DAC → the Xbox source's analog input, toggled with INPUT MODE) is in [SETUP.md](../../SETUP.md#3-xbox-one-the-stereo51-problem-solved-as-far-as-current-gear-allows).


**The complaint:** with the Xbox set to Dolby Digital, stereo content plays only from the front L/R and the Denon cannot upmix it. With the Xbox set to stereo uncompressed, the Denon never receives 5.1.

**Why it happens:**

1. In **Bitstream → Dolby Digital** mode the Xbox **re-encodes everything**, games and apps alike, into a real-time Dolby Digital stream. The commonly reported behavior is that the encoder always produces a **5.1 (3/2.1) stream**, even when the source is stereo. The stereo audio sits in L/R and the other channels are silent **(widely reported; not confirmed by Microsoft)**. The 3806 sees "Dolby Digital 3/2.1". As the table above shows, PLII and Neo:6 are not offered for multichannel DD, so it cannot upmix. The Nakamichi support note confirms that "when content is encoded in stereo 2.0, the Xbox is not able to upmix 2.0 to multiple channels when set to Bitstream."
2. In **Stereo uncompressed** the Xbox downmixes 5.1 and 7.1 game audio to 2-ch PCM. The 3806 can PLIIx or Neo:6 that, but it is matrix-derived surround, not discrete. The Xbox's downmix is probably Lo/Ro rather than a Pro Logic–friendly Lt/Rt, so steering is weaker **(unverified)**.
3. Over **optical**, the Xbox has no EDID from the receiver and cannot "know" what it decodes. That limit belongs to optical, not to the receiver.
4. Over **HDMI** at **5.1/7.1 uncompressed**, the Xbox sends discrete multichannel LPCM. That is ideal for games and movies, but stereo content arrives inside an 8-ch container with only L/R populated. The 3806 shows MULTI CH IN, and again cannot apply PLII **(behavior widely reported for Xbox One)**.

**Diagnose first:** play a stereo source (YouTube, Spotify) with the Xbox in DD mode and press **STATUS** on the receiver, or ON SCREEN on the remote, to see the incoming format. If it says **DD 2/0**, press STANDARD / SURROUND MODE and PLIIx *is* selectable. That would be the case for apps whose native Dolby Digital 2.0 track passes through with *Allow bitstream passthrough* on. If it says **3/2.1** or 3/2, the Xbox has re-encoded to 5.1 and PLII is locked out.

**Options with the 3806 as it is:**

| Option | How | Result |
|---|---|---|
| **A. Everything as stereo PCM + PLIIx** | Xbox: Stereo uncompressed. On the Xbox's input, select PLIIx **Game** or **Cinema** (or Neo:6 Cinema) once, and Auto Surround remembers it. | One setting, no switching, all speakers always active. Loses discrete 5.1 in games and movies (matrix surround instead). Least effort. |
| **B. DD bitstream + 7CH Stereo for stereo content** | Keep the Xbox on Bitstream DD with *Allow bitstream passthrough* on. For stereo apps, switch the receiver to **7CH STEREO** (remote button, or RS-232 `MS7CH STEREO`). | Discrete 5.1 when it matters. Stereo plays from all speakers, but as a same-signal spread, not steered surround. Still needs a mode change, on the receiver instead of the Xbox. What 7CH Stereo does with the silent channels of a 5.1 DD input **(unverified)**. |
| **C. HDMI + 7.1 LPCM** | Run the Xbox through the 3806 over HDMI and set **7.1 uncompressed** (or 5.1). | Best discrete game audio: no DD encoder latency, no 640 kbps lossy encode, true 7.1 if you have SB speakers. Stereo content still lands in L/R only, and Multi In + PLIIx only adds surround-back. Use 7CH STEREO for stereo apps. HDMI compatibility needs testing (section 4.1). |
| **D. Automate the switch** | A PC or Home Assistant sends `MS…` over RS-232 based on what is playing, for example when the Xbox app state or media-player source changes. | Removes the manual step, at the cost of setup effort. See section 10. |
| **E. Replace the receiver** | See section 13. | Modern Denons also cannot unscramble stereo sent inside a 5.1 container, **but** they have per-input sound-mode memory, "Multi Ch Stereo", network control and HDMI-CEC, and they take HDMI 2.1 from an Xbox so the Xbox can use Dolby Atmos or LPCM with full EDID knowledge. The stereo-in-5.1 behavior is the Xbox's, not the receiver's. |

**Recommendation:** try **C (HDMI, 7.1 or 5.1 uncompressed)** for games and movies, with **7CH STEREO** saved as a quick-recall mode for stereo apps. Use the remote's USER 1/2/3 memory buttons, or RS-232. If HDMI through the 3806 is flaky, fall back to **A**, since it needs no switching at all.

---

## 7. Bass management

### 7.1 Settings available

| Setting | Options | Notes |
|---|---|---|
| Speaker size | Front, Center, Surround A, Surround B, Surround Back: **Large / Small / None**. Subwoofer: **Yes / No**. SB: **2spkrs / 1spkr / None**. | Setting Front to Small forces Subwoofer to Yes. Setting Subwoofer to No forces Front to Large. |
| Crossover | **40, 60, 80, 90, 100, 110, 120, 150, 200, 250 Hz**, globally or **per speaker ("Advanced")** | The high 150/200/250 Hz points are unusual and suit tiny satellites like Bose cubes |
| Crossover slope | 12 / 24 dB per octave (high-pass / low-pass) per the archived spec **(fixed or selectable: unverified)** | |
| Subwoofer mode | **LFE** or **LFE + Main** | LFE: the sub gets the LFE channel plus bass from Small channels. LFE + Main: channels set to Large *also* send bass to the sub. |
| Distance / delay | Per speaker, in 0.1 ft or 0.01 m steps | Speakers may differ from each other by at most 20 ft (6 m) |
| Channel level | −12 to +12 dB in 0.5 dB steps, per speaker. A global level plus a per-surround-mode level is remembered. | Test tone in Auto or Manual mode |
| SW ATT | Available on EXT.IN only | |
| Sub on/off in Direct | Subwoofer ON/OFF can be set in Direct and Pure Direct | |

Manual note: with **analog or PCM input that has no LFE, and speakers set to Large, "LFE" mode sends nothing to the sub.** Choose LFE + Main in that case, or set the speakers to Small.

### 7.2 Configuring for Bose Acoustimass (small cubes and a bass module)

There are two basic wiring philosophies. The Bose page covers the module itself.

**Wiring 1: Bose's intended way (everything through the bass module).** All receiver speaker outputs go into the Acoustimass module at speaker level. The module splits off bass with its own fixed passive or active crossover (around 200 Hz, model-dependent) and feeds the cubes. Bose's own AM-10 instructions for Dolby Digital receivers:

| Speaker | Bose-recommended setting |
|---|---|
| Front L/R | Large |
| Center | Small |
| Surround L/R | Large |
| Subwoofer | **OFF** (the module is fed at speaker level instead) |
| LFE | ON (mixed into the Large channels) |
| Crossover | 200 Hz |

With this wiring, the 3806's bass management and Audyssey both act on a system that has its own crossover inside. That is the "sub wants to receive all inputs" complaint. It works, but the receiver never controls the low end directly.

**Wiring 2: receiver-only processing (what the user wants).**

- Wire the cubes **directly** to the 3806's speaker terminals, bypassing the module's cube outputs.
- Feed the Bose module from the **SUBWOOFER pre-out**, *if* the module has a line-level or LFE input. Some Acoustimass models do and some don't, so check the Bose page. If it only has speaker-level inputs, the options are (a) a line-to-speaker-level adapter, (b) replacing the Bose module with any conventional powered subwoofer (the cleanest fix), or (c) staying with wiring 1.
- On the 3806, set every cube to **Small**, Subwoofer **Yes**, subwoofer mode **LFE**, and crossover **Advanced: about 150–200 Hz for the cubes**. Bose cubes roll off steeply in the 150–250 Hz region, so start at 200 Hz and let Audyssey propose values. Cubes placed close to the listener may tolerate 150 Hz.
- Run Audyssey afterwards. It will set distances, levels and crossovers, and EQ the sub. If the Bose module has a built-in low-pass that cannot be defeated, Audyssey will report the sub as *farther* away than it really is. That is correct compensation for the filter delay, so leave it (Audyssey FAQ, question 7).
- A caveat: at crossovers of 150–200 Hz, bass starts to become localizable. Put the bass module near the front or center of the room.

---

## 8. Audyssey MultEQ XT room correction

### 8.1 What it does

- **Auto Setup** detects which speakers are connected, classifies each as satellite or sub, checks **polarity**, and sets **distance (delay), level and crossover** per speaker.
- **Room EQ** uses **FIR filters with several hundred coefficients**, not parametric IIR bands. It corrects both frequency and time domains, with more resolution in the bass.
- It combines up to **6 listening positions** on the 3806 (the 4806 and 5805 allow 8) using Audyssey's *clustering* method rather than simple averaging, so the whole seating area is corrected rather than one seat.
- The DM-S205 mic is calibrated to match the receiver, so use only that mic.

### 8.2 Curves (the ROOM EQ button cycles through them)

| Curve | What it does | Use for |
|---|---|---|
| **Audyssey** | Full correction with a gentle treble roll-off to balance direct and reflected sound | Movies and most listening in normal rooms. Recommended default. |
| **Front** | EQs all speakers to *match the front L/R* (the fronts themselves get no filter). The sub is still EQ'd flat. | If you like how the fronts sound on their own |
| **Flat** | Full correction without the high-frequency roll-off | Small or treated rooms, near-field seating, discrete multichannel music |
| **Manual** | Traditional graphic EQ, no MultEQ. The measured curve can be copied in as a starting point. | Manual tweaking |
| **OFF** | No EQ | Comparison |

The MultEQ XT indicator lights **green** for Audyssey and **red** for Front or Flat. It also turns red if Speaker Config, Distance, Level or Crossover is **changed by hand after Auto Setup**. The EQ stays active, but the calibration is no longer purely Audyssey's. Changing crossovers or Small/Large afterwards does *not* alter the MultEQ filters (Audyssey FAQ, question 14).

### 8.3 Running it properly

1. **Prepare the room.** Turn off the HVAC, fans (including the PC's loud fan) and appliances, and close the doors. The preliminary pass measures background noise.
2. **Prepare the sub.** Volume at about halfway, its crossover at maximum or bypassed, and auto-standby off.
3. Plug the DM-S205 into **SETUP MIC** on the front panel. Mount it on a **camera tripod at ear height, pointing at the ceiling**. Do not hold it and do not set it on the couch.
4. On the receiver: *SETUP → Auto Setup / Room EQ*. First set **Power Amp Assign** (Surround Back, Front bi-amp, Front B or Zone 2/3). Then run the **Preliminary measurement** (speaker detect and polarity) and check the results. For speakers with intentional phase tricks, press *Skip* on a "phase" error if the wiring is correct.
5. **Position 1 = main listening position.** It sets the distances.
6. Positions 2–6: move the mic around the seating area, within about 2 ft of the main seat for a single listener, or to each seat for a family couch. **Use all 6.**
7. *Calculate*, check the results (config, distance, level, crossover), then **Store**. **Do not power off while it stores**, or the Room EQ data is erased.
8. Don't touch the master volume during measurement, since that cancels it. Don't stand between the speakers and the mic.
9. Afterwards, check that the Bose cubes were detected as Small with sensible crossovers. Raise any crossover Audyssey set below about 150 Hz for the cubes.
10. Turn on **Setup Lock** so the calibration isn't changed by accident.

---

## 9. Recommended setup for this system

The assumptions are listed so they can be corrected: Xbox and PC over HDMI into the 3806, 3806 HDMI out to the Vizio, Bose satellites plus bass module, 5.1 or 7.1.

### 9.1 Menu walk-through (SETUP button → System Setup Menu)

| Step | Menu path | Setting |
|---|---|---|
| 1 | **Auto Setup / Room EQ → Power Amp Assign** | "Surround Back" if you have SB speakers. Otherwise "Front B", or leave it (unused). |
| 2 | **Auto Setup** | Run the full 6-position calibration (section 8.3). |
| 3 | **Speaker Setup → Speaker Config** | Check the result: all cubes **Small**, Sub **Yes**. SB 2spkrs, 1spkr or None to match reality. PLIIx Cinema on 5.1 → 7.1 needs **2spkrs**. |
| 4 | Speaker Setup → Subwoofer Setup | **LFE** (with everything Small, this is the correct choice) |
| 5 | Speaker Setup → Crossover Frequency | **Advanced**: cubes at about 150–200 Hz. Keep Audyssey's values unless they are below about 150 Hz. |
| 6 | **Input Setup → Input Assign → HDMI In Assign** | **Owner-confirmed: only TV (HDMI 1 only) and DBS (HDMI 2 only) can take HDMI on this unit.** Current: PC → **TV = HDMI 1**, Xbox → **DBS = HDMI 2**, audio **AMP**. Fallback: ANALOG. Assigning HDMI *also switches that input's digital-audio assignment to HDMI.* |
| 7 | Input Setup → Digital In Assign | Only if a source uses optical. For example, if the Xbox stays on optical, assign OPT-x to its input. Remember step 6 may have overwritten it. |
| 8 | Input Setup → Rename | Rename DBS → "XBOX" and VDP → "PC" so the display makes sense |
| 9 | **Video Setup → Video Convert** | **OFF** for the Xbox and PC inputs. The manual warns that non-standard signals from game machines can break conversion. HDMI isn't converted anyway. |
| 10 | Video Setup → **HDMI Out Setup** | *Analog to HDMI Convert* **ON** (needed to see the 480i menu over HDMI). If the Vizio flickers or blanks each time the menu appears, set it OFF and use the front-panel display. Color Space **YCbCr**. RGB Mode **Normal** (Enhanced only if blacks look grey). |
| 11 | Video Setup → **Audio Delay** | Per input. Start at **0 ms** for the Xbox (game latency), and add 20–60 ms only if lips visibly lag. |
| 12 | Video Setup → On Screen Display | Turn OSD messages on so volume and mode show on screen when viewing analog video. They won't overlay HDMI video. |
| 13 | **Advanced Playback → Auto Surround Mode** | ON. Then *on each input*, while playing each signal type, choose once: Xbox 2-ch PCM → **PLIIx Game** (or Cinema). Xbox DD 5.1 → **DD + PLIIx Cinema** (7.1) or **Dolby Digital** (5.1). Xbox multichannel PCM → **Multi Ch In** (+PLIIx C if 7.1). PC 2-ch PCM → **Stereo** or **Direct** for Qobuz (or PLIIx Music if you want the cubes filled). |
| 14 | Surround Parameter (SURROUND PARAMETER button) | Cinema EQ **OFF**, D.Comp **OFF**, Night **OFF**, AFDM **ON**. For PLIIx Music: Panorama OFF, Dimension 3, Center Width 3. |
| 15 | **Option Setup → Trigger Out** | Optional: Trigger 1 ON for Main Zone, all inputs, to switch a power strip for accessories. Keep the 25 mA limit in mind **(unverified)**. |
| 16 | Option Setup → Setup Lock | **ON** once everything is dialed in |
| 17 | Remote **INPUT MODE** | **AUTO** for every digital input. Avoid forced PCM, which makes noise on bitstream. |

### 9.2 Source settings

- **Xbox:** *Settings → General → Volume & audio output.* Speaker audio: **HDMI audio**, with **7.1 uncompressed** (or 5.1 without SB). Or use Bitstream **Dolby Digital** with **Allow bitstream passthrough ON**. Use video fidelity **1080p**, and turn off 4K, HDR and 24 Hz if offered, since the 3806 cannot pass them. **Do not** choose "Dolby Atmos for home theater", "Dolby Atmos for headphones"/Windows Sonic for the speakers, or DTS:X bitstream: the 3806 cannot decode Atmos (TrueHD/DD+). Plain DD is the only safe bitstream.
- **PC (Windows):** *Sound → Playback → [Denon AVR, HDMI/DP audio] → Configure.* Choose **Stereo** for music (let the receiver decide whether to upmix), or 5.1/7.1 for games. Set the default format to 24-bit/48 kHz, or match Qobuz (44.1/96 kHz). WASAPI exclusive mode in the Qobuz app sends bit-perfect audio. On Fedora the device appears as an HDMI/DP output in PipeWire.
- **Vizio TV:** set the TV's own speakers **off** (Audio → TV Speakers Off). Set the input the 3806 feeds to 1080p with no overscan if the TV offers it.

---

## 10. Control: RS-232, IR, 12 V trigger, automation

This solves "the PC doesn't power the AVR on or off."

### 10.1 RS-232 physical layer

| Item | Value |
|---|---|
| Connector | DB-9 **female**, **DCE**. Pin 2 = TxD (from the receiver), pin 3 = RxD, pin 5 = GND (pin 1 also GND). Pins 4 and 6–9 are not connected. |
| Cable | A **straight-through** (not null-modem) M–F cable from a PC's DTE port. A typical **FTDI-based USB-to-serial adapter** (male DB-9, DTE) plugs straight in or uses a straight M–F extension. |
| Format | **9600 baud, 8 data bits, no parity, 1 stop bit, no flow control**. Half duplex. |
| Framing | ASCII `COMMAND + PARAMETER + CR (0x0D)`. The receiver also sends **EVENT** messages on its own when its state changes (front panel, remote), and answers `XX?` queries within 200 ms. |
| Prerequisite | The rear **POWER switch must be ON** (standby). In the OFF position nothing, remote or serial, can wake it. The manual's first-time procedure: turn the unit on, send a standby command from the controller, confirm it went to standby, and from then on control works. |
| OptiPlex 7060 | Some 7060 configurations have an optional rear DB-9 serial port. Otherwise use a USB adapter. On Fedora, add the user to the `dialout` group. |

### 10.2 Command reference (from the official "AVR-3806/AVC-3920 control protocol Ver. 4.45")

| Function | Command(s) | Notes |
|---|---|---|
| Power on / standby | `PWON` / `PWSTANDBY` | `PW?` asks for the state |
| Main zone on/off | `ZMON` / `ZMOFF` | |
| Volume | `MVUP`, `MVDOWN`, `MV**` | `MV80` = 0 dB, `MV00` = −80 dB, `MV98` = +18 dB, `MV99` = muted/min. Half-dB steps use 3 digits: `MV795` = −0.5 dB. The front display's "−40 dB" equals `MV40`. |
| Mute | `MUON` / `MUOFF` | |
| Input | `SIPHONO`, `SICD`, `SITUNER`, `SIDVD`, `SIVDP`, `SITV`, `SIDBS`, `SIVCR-1`, `SIVCR-2`, `SIV.AUX`, `SICDR/TAPE` | `SIVCR-3` is invalid on the 3806 |
| Input mode | `SDAUTO`, `SDPCM`, `SDDTS`, `SDANALOG`, `SDEXT.IN-1` | |
| Video select | `SVDVD` … `SVSOURCE` | Shows one source's video with another's audio |
| Surround mode | `MSDIRECT`, `MSPURE DIRECT`, `MSSTEREO`, `MSMULTI CH IN`, `MSDOLBY PL2X` (and other Dolby/DTS names, which are treated as the **STANDARD** button), `MSDTS NEO:6`, `MSWIDE SCREEN`, `MS7CH STEREO`, `MSSUPER STADIUM`, `MSROCK ARENA`, `MSJAZZ CLUB`, `MSCLASSIC CONCERT`, `MSMONO MOVIE`, `MSMATRIX`, `MSVIDEO GAME`, `MSVIRTUAL`, `MSUSER1..3` | The Dolby/DTS group maps to "STANDARD" (the receiver picks the decoder for the signal). Choose the variant with `PS` below. |
| Decoder variant | `PSMODE:CINEMA`, `PSMODE:MUSIC`, `PSMODE:GAME`, `PSMODE:PRO LOGIC` | With SB on this selects PLIIx, otherwise PLII |
| Surround-back handling | `PSSB:MTRX ON`, `PSSB:PL2X CINEMA`, `PSSB:PL2X MUSIC`, `PSSB:NON MTRX`, `PSSB:OFF` | E.g. DD 5.1 → DD+PLIIx C |
| Room EQ | `PSROOM EQ:AUDYSSEY`, `:FRONT`, `:FLAT`, `:MANUAL`, `:OFF` | |
| Tone, Cinema EQ, Night | `PSTONE DEFEAT ON/OFF`, `PSCINEMA EQ.ON/OFF`, `PSNIGHT ON/OFF` | |
| Audio delay | `PSDELAY 000`–`200` (ms), `PSDELAY UP/DOWN` | |
| Channel levels | `CVFL 50` (50 = 0 dB, 38 = −12 dB, 62 = +12 dB), also FR, C, SW, SL, SR, SBL, SBR, SB; `CVSW 00` = sub off (Direct only) | |
| Zone 2 / 3 | `Z2ON/OFF`, `Z2<source>`, `Z2UP/DOWN`, `Z2**`, `Z2MUON`. Same for `Z3`. | |
| Tuner | `TFUP/DOWN`, `TF105000`, `TPA1`, `TMFM/AM/XM/AUTO/MANUAL` | |
| Lock | `SYREMOTE LOCK ON/OFF`, `SYPANEL LOCK ON`, `SYPANEL+V LOCK ON`, `SYPANEL LOCK OFF` | |

Practical note: after `PWON`, wait about 1–2 s before sending the next command, because the receiver ignores commands while its relays settle **(common advice, unverified for this model)**.

### 10.3 Example scripts

**Linux (Fedora), shell:**

```bash
PORT=/dev/ttyUSB0
stty -F "$PORT" 9600 cs8 -cstopb -parenb -crtscts raw -echo
printf 'PWON\r'      > "$PORT"; sleep 2
printf 'SIVDP\r'     > "$PORT"      # PC input (whatever HDMI 2 is assigned to)
printf 'MSSTEREO\r'  > "$PORT"
printf 'MV45\r'      > "$PORT"      # -35 dB
# ...later
printf 'PWSTANDBY\r' > "$PORT"
```

**Python (pyserial), works on Windows (`COM3`) or Linux:**

```python
import serial, time

def denon(*cmds, port="/dev/ttyUSB0"):
    with serial.Serial(port, 9600, bytesize=8, parity="N", stopbits=1, timeout=0.3) as s:
        for c in cmds:
            s.write((c + "\r").encode("ascii"))
            time.sleep(0.2 if not c.startswith("PWON") else 2.0)
        s.write(b"PW?\r")
        return s.read(256).decode("ascii", "replace")

print(denon("PWON", "SIDBS", "MSDOLBY PL2X", "PSMODE:GAME"))
```

**Windows PowerShell (for Task Scheduler on logon, wake, shutdown or lock):**

```powershell
$p = New-Object System.IO.Ports.SerialPort 'COM3',9600,'None',8,'One'
$p.Open(); $p.Write("PWON`r"); Start-Sleep 2; $p.Write("SIVDP`r"); $p.Close()
```

Tie these to events. On Windows, use Task Scheduler triggers for *On workstation unlock*, *On event: Power-Troubleshooter 1 (resume)*, and a shutdown script via gpedit for `PWSTANDBY`. On Fedora, use a systemd unit with `WantedBy=multi-user.target`, a `systemd-sleep` hook, and an `ExecStop`.

### 10.4 Existing software

| Tool | Notes |
|---|---|
| **Home Assistant "Denon RS-232"** (official, since HA 2026.5) | Power, volume, mute, source, tuner, zones. Push updates from EVENT messages. Works with a local serial port or an **ESPHome serial proxy** (an ESP32 plus a MAX3232 board placed at the receiver). Built on `home-assistant-libs/denon-rs232`, whose model list includes the **AVR-3805** and **AVR-2807** (same protocol family) but **not the 3806 by name**. Expect it to work with the closest profile **(unverified)**. |
| Custom `denon232` components (doucga, bajansen, mhannis, bluepixel00) | Older HACS/custom integrations for any Denon with the classic serial protocol |
| DenonESP232 (GitHub) | ESP-based RS-232-to-network bridge |
| EventGhost "DenonSerial" plugin (Windows) | Old but simple Windows automation |
| `ser2net` on a Raspberry Pi | Exposes the port over TCP so any machine can send `PWON\r` with `nc` |

**Integration idea:** Home Assistant's Xbox integration (or a ping of the console) detects when the Xbox turns on, then runs `PWON` + `SIDBS` + the preferred mode. The PC runs the scripts above. That fixes the "doesn't power the AVR on or off" complaint for both sources, and it is the only practical way, since the 3806 has no CEC.

### 10.5 IR

- The official **IR code sheet** is archived (see Sources). Format: **"SHARP" 15-bit**, 38 kHz carrier **(carrier assumed; standard for the Sharp protocol)**. System address `01000`, with extension bits selecting code pages.
- There are **discrete** codes for **POWER ON** (#33) and **POWER OFF** (#34) on system 01000/ext 11. That matters for automation, because a toggle code can leave the receiver in the wrong state. There are also discrete input, mode (STANDARD, DSP SIMULATION, STEREO, DIRECT, 7CH STEREO) and volume-preset codes (0 dB, −20, −40).
- Options: a Broadlink RM4 Mini or Pro (learns codes; HA integration), a USB-UIRT or Iguanaworks transceiver with LIRC or WinLIRC, or an ESPHome IR blaster (`remote_transmitter`, Sharp protocol). A wired IR emitter can go into the rear **REMOTE IN** jack for 100 % reliability.
- RS-232 is better than IR here because it reports state back.

### 10.6 12 V trigger

Two outputs. Each can be programmed per **zone** (on or off with that zone) or per **input/surround mode**. Use them to switch a trigger-controlled power strip, a powered-sub trigger input, a screen, or the future reactive light. The receiver has **no trigger input**, so the PC cannot wake it this way. Use RS-232 for that.

---

## 11. Known issues, failure modes, firmware

| Issue | Details |
|---|---|
| **Heat and protection mode** | Runs hot, with no fan. Symptoms: the power LED **flashes red** and it shuts down. Causes: poor ventilation, long high-output use, or shorted speaker-wire strands. Fix: leave ≥ 12 in of clearance above it and don't enclose it. A USB or thermostat-controlled cabinet fan (e.g. AC Infinity) is a common owner fix. If protection keeps triggering with good wiring and cool conditions, the amp needs service (output transistors or relays). |
| **HDMI handshake / "no picture"** | HDCP 1.x or EDID issues with some newer sources and displays. The receiver outputs no video if any device in the chain lacks HDCP. Fix: power things on in order (TV, then AVR, then source), use shorter cables (≤ 5 m), and force the source to 1080p. Reports of intermittent HDMI dropouts exist. |
| **HDMI board / fuse failure** | "Powers on, no HDMI audio or video" can be a failed HDMI board or blown internal fuse. Hot-plugging HDMI with everything powered is a suspected cause (common across Denon generations). Repair is usually uneconomical on a $150 receiver. Workaround: bypass HDMI, with video to the TV and audio via optical/coax. |
| **HDMI audio "unlock"** | If HDMI audio drops, the receiver switches to the fallback set in HDMI In Assign (ANALOG or EXT. IN). If sound disappears, check that the fallback isn't selecting an empty input. |
| **Microprocessor lock-up** | Caused by power surges or static. First unplug for 10 minutes; if that fails, do a factory reset (section 12). |
| **Room EQ data loss** | Powering off during "Storing" wipes the Audyssey data |
| **Aging** | Typical for 20-year-old gear **(general, unverified for this unit)**: dried electrolytic capacitors in the power supply and DSP board (hum, dropouts, no boot), scratchy volume encoder, dim VFD display, oxidized relays (one channel cuts out; cycling the power or speakers A/B can clear it temporarily). |
| **Firmware** | There were no user-installable firmware updates for the 3806 (no USB or network). Factory service updates for early 4806/5805 Audyssey bass issues did not apply to the 3806, per Denon's FAQ. Treat the firmware as fixed. |

---

## 12. Tips, hidden features, and reset

- **Factory reset (microprocessor initialization):** 1) Switch off the main **POWER** switch. 2) **Hold PURE DIRECT and NIGHT** and switch POWER on. 3) When the whole display flashes at about 1-second intervals, release. All settings, including Audyssey and presets, go back to defaults. If it didn't work, repeat.
- **Setup Lock** (*Option Setup*) freezes system setup, surround parameters, tone, levels and Room EQ, and shows "Setup Locked".
- **Panel and remote lock** only via RS-232 (`SYPANEL LOCK ON`, `SYREMOTE LOCK ON`).
- **USER 1/2/3 memory buttons** store and recall the input, surround mode, levels and more. Hold to store. This is the practical "one-press Xbox stereo mode" (`MSUSER1`).
- **Per-mode channel levels:** levels adjusted inside a surround mode are remembered *for that mode*. Levels set in System Setup are the master baseline.
- **STATUS button** (front) or **ON SCREEN** (remote) shows the incoming signal format. This is the key diagnostic for the Xbox issue.
- **Test-tone levels by remote:** TEST TONE, then left/right. This only works in Auto mode and in STANDARD (Dolby/DTS surround).
- **Dimmer** cycles the display through bright, medium, dim and off.
- **Pure Direct** turns off the video circuits, the display and tone controls for the cleanest analog path. Nice for Qobuz from the PC's analog out. Bass management is bypassed in Pure Direct, so with Bose cubes set to Small, use **Direct** or **Stereo** instead to keep the sub in play.
- **Front B / bi-amp:** unused surround-back amps can bi-amp the fronts (not useful with Bose) or drive a second stereo pair or Zone 2/3 speakers.
- **Surround A/B:** two sets of surround speakers can be selected or combined, each with its own saved levels.
- **Last-function memory and backup:** settings survive about a week unplugged.
- **Remote punch-through:** the RC-1024 can learn the Vizio and Xbox codes and build macros, for example a single button for Xbox input, TV on and mode.

---

## 13. Limitations vs. goals, and the upgrade path

### 13.1 Complaint → root cause → what fixes it

| Complaint or goal | 3806 limitation | What fixes it |
|---|---|---|
| No 4K/8K | HDMI 1.1 / 1080p max; no HDR | Any Denon or Marantz with **HDMI 2.1 / 8K inputs** (2020+), plus a 4K TV |
| No Atmos | No TrueHD, DD+ or Atmos decoding; no height channels | Any current Denon **X or S** (Atmos + DTS:X) **plus** height or up-firing speakers. Bose cubes can serve as heights in a pinch. |
| Clunky tuning/adjusting | 480i menu with no overlay on HDMI; buttons and cursor only | Modern **GUI overlaid on 4K video**, Setup Assistant, **Denon AVR Remote / HEOS app**, **web UI**, **Audyssey MultEQ-X (PC)** or **MultEQ Editor (phone)** for editing target curves |
| PC can't power AVR/TV | No CEC, no network | Modern receivers have **HDMI-CEC** (TV and source power sync), **Telnet/HTTP control over Ethernet using the same PW/SI/MV/MS command set**, and a native Home Assistant integration (`denonavr`) |
| Xbox DD vs. stereo | Fixed Xbox output modes; 2005 decoder can't upmix multichannel | Partly helped: with **HDMI 2.1 + EDID** the Xbox can use LPCM 7.1 or Atmos with full knowledge of the receiver; modern "**Multi Ch Stereo**", Dolby Surround and Neural:X upmixers; per-input mode memory; network automation. Stereo inside a 5.1 container remains an Xbox-side behavior. |
| Clean receiver-only processing (Bose) | The 3806 can do it (crossovers to 250 Hz) | Mostly a speaker and sub question. A new receiver also brings **multiple sub outs**, **XT32** or **Dirac Live Bass Control**, and **Sub EQ HT** |
| Room correction | MultEQ XT with 6 positions, fixed curves, no editing | **MultEQ XT32** (X3800H and up, and the Marantz Cinema 60 and up) with the **MultEQ-X** app, or **Dirac Live** (paid license on 2022+ Denon X3800H/X4800H/X6800H and the 2026 X2900H/X3900H) |
| TV speaker bar | n/a | Once all audio goes through the receiver, turn the TV speakers off. **eARC** on a new receiver and TV lets TV apps' audio (including Atmos) reach the receiver. |

### 13.2 Current models, as of about September 2026 (US street prices, which rose with 2025 tariffs)

| Model | Year | Channels / power | Video | Room EQ | Approx. price | Notes |
|---|---|---|---|---|---|---|
| Denon **AVR-S770H** / **AVR-X1800H** | 2023 | 7.2 ch, 75–80 W | HDMI 2.1, 8K inputs, eARC | MultEQ XT | **~$750–850** new | Entry point. Fixes 4K, CEC and Atmos (5.1.2). Single sub-signal output on the S770H **(unverified)**. |
| Denon **AVR-X2900H** | 2026 (May/June) | 7.2 ch, 95 W | 6 HDMI in, 2 out, eARC, 8K/60, 4K/120 | Audyssey (**XT vs XT32 unverified**) + **Dirac Live optional (paid)** | **$1,349** | Successor to the X2800H. First Denon at this price with a Dirac option. |
| Denon **AVR-X3900H** / AVC-X3900H | 2026 | 9.4 ch, 105 W, 11.4 processing | 6 HDMI in, 3 out, eARC | Audyssey + Dirac. Some sources say the full Dirac suite is included; others say it is an upgrade **(unverified which)**. | **$1,849** | 4 independent subs, 32-bit DACs, IMAX Enhanced, Auro-3D |
| Denon **AVR-X3800H** | 2022 | 9.4 ch, 105 W | 6 × 8K in | **XT32** + Dirac upgrade ($259–$349 full-band; Bass Control extra) | **~$900–1,100** refurbished or clearance | Probably the best value now that the X3900H has replaced it |
| Marantz **Cinema 70s** (Series 2) | 2025–26 | 7.2 slim, 50 W | 8K, eARC | XT + optional Dirac | **~$1,300–1,500** | Slim; less power |
| Marantz **Cinema 60** (Series 2) | 2025–26 | 7.2 ch | 8K, eARC | XT32 + optional Dirac | **~$1,800–2,000** | |
| Marantz **Cinema 50** (Series 2) | 2025–26 | 9.4 ch | 8K, eARC | XT32 + Dirac | **~$2,800–3,000** | |

Prices come from 2026 launch coverage and retailer snapshots and change often. Treat them as ±15 %.

### 13.3 Buying used: what to look for

- **Target used models:** Denon AVR-X3600H, X3700H or X4500H, or Marantz SR6015 and similar, about **$350–700** **(price range unverified)**. They have 4K HDR, Atmos, XT32 and CEC/ARC. The X3700H and X4700H add 8K and eARC.
- **Early 8K Denon/Marantz (2020: X3700H, X4700H, X6700H, SR6015/7015/8015):** a known **HDMI 2.1 chipset bug with 4K/120 from the Xbox Series X** was fixed by a free Denon/Marantz adapter. Ask the seller whether the unit has it. It doesn't matter for an Xbox One.
- **HDMI board failures** are the classic Denon and Marantz failure (a 2026 law-firm investigation is collecting reports). Test **every HDMI input**, ARC/eARC and the HDMI out before buying. Prefer refurbished units with a warranty.
- Check that the Audyssey mic is included (model-specific), and that the unit has been **factory reset** and **HEOS account removed**.
- The TV matters too: 4K, HDR, CEC and eARC need a new TV as well as a new receiver. The Vizio VS420LF1A is a 1080p HDTV.

### 13.4 Keep or replace?

The 3806 is **worth keeping** if the TV stays 1080p and Atmos isn't a near-term plan. It has plenty of amplifier power, good room EQ, and high crossovers that suit the Bose cubes, and **RS-232 automation fixes the power complaint for about $15** (a USB-serial adapter). Replace it together with the TV when moving to 4K. A new receiver alone gains CEC, a GUI and room-EQ upgrades, but no picture improvement on the Vizio.

---

## 14. How it fits this system

| Component | Interaction with the AVR-3806 |
|---|---|
| **Dell OptiPlex 7060** | **Audio and video:** DP++ → HDMI into HDMI 2 (e.g. the "VDP" input) gives 1080p video and up to 7.1 LPCM. This is the best Qobuz path. Use Stereo, Direct or PLIIx Music. The other option is the PC's analog out into a line input (CD) with Pure Direct, which bypasses bass management. **Power:** the PC can't wake the receiver over HDMI (no CEC) → use **RS-232** with a USB-FTDI adapter and scripts on logon, wake and shutdown (section 10). **Fan noise** interferes with Audyssey, so stop it or shut the PC down during measurement. **Display hot-plug** when the receiver switches input or powers off may shuffle Windows displays. |
| **Xbox One** | HDMI into HDMI 1 ("DBS" or renamed) gives 7.1 or 5.1 LPCM or DD bitstream. Needs testing on HDMI 1.1 (section 4.1); optical is the fallback. **The DD/stereo problem** and its workarounds are in section 6. Never select an Atmos or DTS:X bitstream. 4K is impossible through this receiver. Power automation via Home Assistant's Xbox state → RS-232 `PWON`. |
| **Bose Acoustimass** | Either Bose-style (all channels into the module, speakers Large and center Small, sub Off, 200 Hz) or **receiver-only**: cubes on the receiver's amps set to Small at about 150–200 Hz, and the module fed from the SUB pre-out *if it has a line input*. The 3806's 150/200/250 Hz crossovers are well suited to cubes. Run Audyssey after any rewiring. |
| **Vizio VS420LF1A** | HDMI out → TV at 1080p (the TV's maximum). No CEC or ARC on the receiver, so TV-tuner audio needs the TV's optical/analog out into a receiver input (e.g. "TV"), or nothing. The receiver's menu reaches the TV only as 480i, not overlaid on HDMI video. Turn the TV's speakers off in its menu. Its IR can be automated with an IR blaster alongside the receiver's RS-232. |
| **Sound-reactive light** (planned) | Feed it from the **SUB pre-out** (Y-splitter; bass-driven) or the **FL/FR pre-outs**. **Not** from Zone 2/3 or REC OUT, which carry no digital sources (the Xbox and PC are both digital). The **12 V trigger** can switch the light's power with the receiver. A mic-based light, or one driven by the PC (e.g. WLED + a PC audio-capture app), avoids wiring entirely. |

---

## 15. Sources

**Primary (Denon / Audyssey / Bose)**

- Denon USA archive product page, with the owner's manual and info sheet: https://www.denon.com/en-us/product/archive-av-receivers/avr-3806/AVR3806.html
- AVR-3806 Owner's Manual (English, PDF): https://www.denon.com/on/demandware.static/-/Library-Sites-denon_northamerica_shared/default/dwf5ed74ff/downloads/archived/avr-3806-owners-manual-en.pdf
- AVR-3806 Info Sheet (PDF): https://www.denon.com/on/demandware.static/-/Library-Sites-denon_northamerica_shared/default/dw72d411e6/downloads/archived/avr-3806-info-sheet-en.pdf
- Archived Denon USA product page (MSRP $1,299, SHARC DSP, PCM1791 DACs, 1080p HDMI, feature matrix), 2007 snapshot: http://web.archive.org/web/20070102151018/http://usa.denon.com:80/ProductDetails/623.asp
- **AVR-3806 RS-232 Serial Protocol Ver. 4.45 (PDF, archived):** http://web.archive.org/web/20061230092038/http://usa.denon.com:80/AVR-3806SerialProtocol_Ver(4.5).pdf
- **AVR-3806 IR code sheet (PDF, archived):** http://web.archive.org/web/20070208101944/http://usa.denon.com:80/AVR3806IR.pdf
- Denon / Audyssey MultEQ XT FAQ (PDF, archived): http://web.archive.org/web/20100326160553/http://www.usa.denon.com:80/Denon_Audyssey_FAQs.pdf
- Denon AVR/AVC control protocol v4.0 (AVR-3805, same family): https://assets.denon.com/documentmaster/uk/139_avr-3805_rs232.pdf
- Bose Acoustimass 10 owner's guide (receiver settings): https://products.bose.com/pdf/customer_service/owners/am10_guide.pdf

**Reviews, specs, and community**

- The Absolute Sound review: https://www.theabsolutesound.com/articles/denon-avr-3806-71-channel-av-receiver/
- HiFi-Wiki (dimensions, I/O counts, EU price, used prices): https://hifi-wiki.com/index.php/Denon_AVR-3806
- HiFi Engine manual library: https://www.hifiengine.com/manual_library/denon/avr-3806.shtml
- Internet Archive spec sheet: https://archive.org/details/generalmanual_000075272
- [H]ard|Forum launch thread (3805 vs 3806, MultEQ XT discussion): https://hardforum.com/threads/denon-avr-3806-out.958437/
- Home Theater Forum, 3805 vs 3806: https://www.hometheaterforum.com/community/threads/denon-3805-or-3806-which-one-to-buy.229846/
- AVS Forum, Denon 3806 Owners Thread: https://www.avsforum.com/threads/denon-3806-owners-thread.589323/
- AVS Forum, Denon 3806 HDMI Audio: https://www.avsforum.com/threads/denon-3806-hdmi-audio.795678/
- AVS Forum, 3806 vs 2807 (1080p pass-through): https://www.avsforum.com/threads/denon-3806-vs-2807-which-one.664732/
- Steve Hoffman forum, AVR-3806 + PS3 HDMI audio: https://forums.stevehoffman.tv/threads/denon-avr-3806-ps3-3-0-firmware-and-hdmi-audio.194382/
- Audioholics, AVR-3806 HDMI audio problems: https://forums.audioholics.com/forums/threads/avr-3806-dvd-2910-hdmi-audio-problems.16840/
- JustAnswer, 3806 HDMI/ARC fuse Q&A (low-confidence source): https://www.justanswer.com/home-theater-stereo/jbz80-denon-avr-3806-bought-new-tv-mistakenly.html

**Xbox behavior**

- Nakamichi helpdesk, Xbox One S audio (bitstream can't upmix 2.0): https://www.helpdesk.nakamichi-usa.com/xbox-one-s-audio
- AVS Forum, Xbox One S uncompressed/bitstream issues: https://www.avsforum.com/threads/uncompressedd-bitstream-xbox-one-s-audio-output-issues.2961336/
- AVS Forum, Denon 3311ci + Xbox One audio settings: https://www.avsforum.com/threads/denon-3311ci-xbox-one-console-which-audio-settings-to-choose.1521130/

**Control and automation**

- Home Assistant, Denon RS-232 integration: https://www.home-assistant.io/integrations/denon_rs232/
- home-assistant-libs/denon-rs232: https://github.com/home-assistant-libs/denon-rs232
- doucga/denon232: https://github.com/doucga/denon232
- HA community, older Denon AVR with RS232: https://community.home-assistant.io/t/older-denon-avr-with-rs232/211985
- DenonESP232: https://github.com/Kousei-Uchu/DenonESP232
- AVS Forum, DenonSerial EventGhost plugin: https://www.avsforum.com/threads/denonserial-control-denon-avrs-via-rs232-eventghost-plugin.652307/
- Remote Central, Denon RS-232/IP protocol library: https://files.remotecentral.com/library/22-1/denon/receiver/index.html

**Upgrade path**

- ecoustics, Denon AVR-X2900H / X3900H hands-on: https://www.ecoustics.com/products/denon-avr-x2900h-x3900h/
- Gear Patrol, Denon 2026 X-series: https://www.gearpatrol.com/audio/denon-x-series-avrs-2026/
- Audio Review Blog, 2026 X-series announcement: https://audiomatome.com/en/news/2026-05-19-denon-x-series-2026/
- Dirac Live for Denon X3800H (pricing): https://www.dirac.com/products/denon-avr-x3800h-avc-x3800h
- Marantz Cinema Series 2 overview: https://www.worldwidestereo.com/blogs/guides/marantz-cinema-series-2-review
- Denon AVR-X1800H: https://www.denon.com/en-us/product/av-receivers/avr-x1800h/300773.html
- AVS Forum, Denon prices rising (tariffs): https://www.avsforum.com/threads/denon-prices-on-the-rise.3327018/
- Migliaccio & Rathod, Denon AVR HDMI board failure investigation (2026): https://classlawdc.com/2026/07/17/denon-avr-hdmi-board-failure-investigation/
