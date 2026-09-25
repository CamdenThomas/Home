# Bose Acoustimass Speaker System

Reference page for the Bose Acoustimass cube/bass-module system in the home entertainment setup
(Denon AVR-3806, Dell OptiPlex 7060 / Qobuz, Xbox One, Vizio VS420LF1A).

> **The problem:** "The sub wants to receive all inputs to control. I want clean AVR-only audio processing."
>
> **Short answer:** Every Acoustimass system works this way on purpose. The bass module is the hub.
> The receiver's speaker-level outputs go into the module. The module splits off the bass, applies
> Bose's own filtering, EQ and (on powered models) loudness compensation, then sends what's left to the
> cubes. How you get the Denon back in charge depends on the model:
>
> - **Powered module with an LFE input** (AM6 III/V, AM10 III/IV/V, AM15 II, AM16): the fix costs
>   nothing. Set every cube to **Small at 200 Hz** and connect the LFE RCA plug to the Denon's sub
>   pre-out. The Denon then does the bass management (see [Fix A](#fix-a--avr-managed-bass-through-the-module-no-modifications)).
>   The cleanest fix goes one step further: wire the cubes straight to the Denon and use the module
>   only as a powered LFE sub ([Fix B](#fix-b--module-becomes-a-plain-powered-sub-cubes-wired-direct)).
> - **Passive module** (AM5, AM6 I/II, AM10 I/II): the module has no LFE input, so the Denon can't
>   manage its bass. Your options are to accept the hub, or bypass the module and add a real powered
>   subwoofer ([Fix C](#fix-c--passive-module-systems-retire-the-module-add-a-real-sub)).
>
> Step 1 is to [identify the exact model](#1-identify-the-exact-model).

Items marked **(unverified)** could not be confirmed from a primary source.

---

## Contents

1. [Identify the exact model](#1-identify-the-exact-model)
2. [Model reference table](#2-model-reference-table)
3. [How the bass module works (and why it fights the AVR)](#3-how-the-bass-module-works-and-why-it-fights-the-avr)
4. [Measurements](#4-measurements)
5. [Solutions to "the sub wants all inputs"](#5-solutions-to-the-sub-wants-all-inputs)
6. [Recommended Denon AVR-3806 settings](#6-recommended-denon-avr-3806-settings)
7. [Audyssey MultEQ XT with Bose](#7-audyssey-multeq-xt-with-bose)
8. [Known issues and used value (2026)](#8-known-issues-and-used-value-2026)
9. [Honest sound-quality assessment and upgrade path](#9-honest-sound-quality-assessment-and-upgrade-path)
10. [How it fits this system](#10-how-it-fits-this-system)
11. [Sources](#11-sources)

---

## 1. Identify the exact model

Work through these checks, from most to least reliable:

1. **Label on the module.** The model name and series ("Acoustimass 10 Series IV") are printed on the
   rear connector panel or on the bottom label, next to the serial number. Bose support needs the serial
   number, and it also confirms the model.
2. **Power cord?**
   - **No power cord → passive module.** This covers AM5 (all series), AM6 I/II and AM10 I/II. The Denon's
     amplifiers drive the module's woofers.
   - **Power cord → powered module.** This covers AM6 III/IV/V, AM10 III/IV/V, AM15 I/II and AM16. The module
     has its own bass amplifier, which draws 135 W (AM6), 270 W (AM10) or 400 W (AM15 II/16).
3. **Receiver input connector on the module.**

   | What you see | Likely family |
   |---|---|
   | Spring-clip terminals marked "INPUTS FROM AMP OR RECEIVER", L/R only | **AM5** (stereo, passive) |
   | Row of colored RCA-style jacks marked "INPUTS FROM RECEIVER OR AMPLIFIER" (L, C, R, LS, RS). The cable carries speaker-level signal on RCA plugs | **AM6 II, AM10 I/II** (passive) |
   | One multi-pin connector (15-pin D-sub, 8 over 7) with **two thumbscrews**, labeled "Audio Input". The cable has an **RCA plug marked LFE** with a cap. **LFE** and **Bass/Room compensation** knobs | **AM6 III/IV/V, AM10 III/IV/V, AM15 II, AM16** (powered) |
   | 8-pin or 13-pin DIN, 3.5 mm jacks, "serial data" | **Lifestyle / Acoustimass 9 / CineMate** modules. These are *not* designed for a standalone AVR (see note below) |

4. **Cube type.**
   - **Single cube** (one 2.5" "Twiddler" driver, about 3.1 x 3.1 x 4 in): AM5 uses single cubes stacked in
     pairs as "arrays", AM6 uses them for all five channels.
   - **Double cube / "Direct/Reflecting" array** (two stacked cubes that swivel, about 6.2 x 3.1 x 4 in, 2.4 lb):
     AM10, AM15, AM16 and AM5. On AM10 IV/V the center is a horizontal double cube.
   - **"Jewel Cube"** (thin, curved, single piece, about 5.6 in tall): Lifestyle 38/48/V-class and CineMate systems.
     These arrived with the proprietary Lifestyle consoles, not with receiver-oriented Acoustimass packages.
5. **Cube connectors.**
   - Spring clips on the back of each cube: AM5, AM6 I/II, AM10 I/II, AM6 III/AM10 III, AM10 IV.
   - Molded plug at both ends: AM6 V/AM10 V ("insert the other end of each cable into the connector on each
     speaker, with the label facing down").
   - Cube cable end at the module: speaker wire (AM5), colored RCA plugs (AM6 II/III, AM10 I–III, AM15 II/16:
     blue for front, orange for rear), labeled plugs (AM10 IV/V).
6. **Count the woofers** (visible through the port, or listed on the label): AM6 has 1 (powered) or 2 (passive),
   AM10 has 2 (III–V) or 3 (I/II), AM15/16 has 3.

> **Lifestyle / CineMate warning:** Lifestyle PS-series and Acoustimass 9 modules take their input and control
> (on/off and volume over serial data) from a Bose console. People do reverse-engineer them (for example, the 8-pin DIN
> pinout on the ecoustics thread in Sources), but they are not a drop-in for an AVR. If your module has a DIN
> connector and no speaker-level input, it's one of these. The practical answer then is to retire it.

---

## 2. Model reference table

Receiver-oriented Acoustimass packages. Specs come from Bose owner's guides and spec sheets unless marked.
Bose never published crossover frequencies or measured impedance curves. Every model is rated "compatible with
receivers rated 4–8 Ω" (and 10–200 W or 10–150 W).

| Model / series | Approx. years | Ch. | Cubes | Module woofers | Module | LFE (low-level) input? | Receiver → module | Module → cubes | Bose receiver setting |
|---|---|---|---|---|---|---|---|---|---|
| **AM5 Series I/II/III** | ~1987–2010s (unverified) | 2.1 (stereo) | 2 double-cube arrays (4 × 2.5") | 2 × 5.25" | **Passive** | No | Spring clips, L/R speaker-level | Spring clips, bare wire | Stereo amp. Use the receiver's bass control |
| **AM6 Series I/II** | ~1995–2001 | 5.1 (bass summed) | 5 single cubes (1 × 2.5") | 2 × 5.25" dual-voice-coil | **Passive** | No | RCA-style plugs carrying speaker-level signal | RCA-style plugs → cube spring clips | L/R/Surr **Large**, **Center Small**, Sub **Off** |
| **AM10 (Series I)** | ~1995–2000 | 5.1 (bass summed) | 5 double-cube arrays | 3 × 5.25" (for L/R front and surround) | **Passive** | No | Colored RCA-style plugs (speaker-level) | Colored RCA-style plugs → spring clips | L/R/Surr **Large**, **Center Small**, Sub **Off**, crossover **200 Hz** |
| **AM10 Series II** | ~2000–2003 | 5.1 (bass summed) | 5 double-cube arrays | 3 × 5.25" (L, C, R and surround) | **Passive** | No | 5 pairs on RCA plugs (speaker-level) | Bare wire → cube spring clips | All **Large**, Sub **Off**, LFE **On**, crossover **200 Hz** |
| **AM15 (Series I)** | ~1998–2002 | 5.1 | 5 double-cube arrays | 2 × 5.25" | **Powered** | Unverified (probably no) | Multi-pin (unverified) | — | Likely all Large (unverified) |
| **AM6 Series III** / **AM10 Series III** | ~2002–2006 | 5.1 | AM6: single cubes. AM10: double arrays + double center | AM6: 1 × 5.25". AM10: 2 × 5.25" | **Powered** (135 W / 270 W draw) | **Yes**, RCA on the input cable | 15-pin D-sub + thumbscrews | Blue (front) / orange (rear) RCA plugs → cube clips | All **Large**, LFE/Sub **On**, crossover at the "lowest number, typically 80 Hz" |
| **AM15 Series II** / **AM16** | ~2002–2006 | 5.1 / 6.1 | Double-cube arrays (6 on AM16, with center surround) | 3 × 5.25" | **Powered** (400 W draw) | **Yes** | Multi-pin + LFE RCA | Blue/orange RCA plugs | All **Large**, LFE **On**, crossover about 80 Hz |
| **AM6 Series IV** (unverified) / **AM10 Series IV** | ~2006–2014 | 5.1 | AM10 IV: double arrays + horizontal double center | AM10 IV: 2 × 5.25" | **Powered** (270 W) | **Yes** | Multi-pin (D-sub) + thumbscrews, LFE RCA | Labeled plug at module → spring clips at cube | All **Large**, LFE/Sub **On**, crossover about 80 Hz |
| **AM6 Series V** / **AM10 Series V** | ~2014–2020 (unverified) | 5.1 | Redesigned "Virtually Invisible" cubes (AM6 single, AM10 double) | AM6: 1 × 5.25". AM10: 2 × 5.25" | **Powered** (135 W / 270 W) | **Yes** | Multi-pin + thumbscrews, LFE RCA | Plug at both ends | All **Large**, LFE/Sub **On** |
| **AM16 Series II** | ~2006–2010 (unverified) | 6.1 | Double arrays | 3 × 5.25" (unverified) | **Powered** | Yes (unverified) | Multi-pin + LFE RCA | Plugs | All Large |

Notes:

- **Impedance.** Bose rates everything 4–8 Ω. Sound & Vision (Aug 1999) measured an AM-15 system at **5.3 Ω
  minimum, 8 Ω nominal**. A magazine test of the AM5 Series II (reprinted on hifi-classic.net) reported
  **4.7 Ω minimum at about 300 Hz**. Around the crossover region, expect a real-world load of **about 5–6 Ω**.
- The **Denon AVR-3806 manual** rates its outputs for **6–16 Ω**. It also warns that loads under the
  rated impedance can trip the protection circuit during long, loud sessions. Bose cubes and modules
  slightly undercut that rating. At normal living-room levels this is fine. Just don't run the Denon hard for hours.
- **"Series" numbering doesn't line up across lines.** AM6 III was sold alongside AM10 III, and AM6 III alongside AM10 IV (both appear in one owner's guide).

---

## 3. How the bass module works (and why it fights the AVR)

### Signal flow (all Acoustimass systems)

```
                    Bose "hub" topology (factory wiring)
 Denon speaker-level outputs (FL, C, FR, SL, SR) ──► Acoustimass module
                                                     ├─ low-pass on every channel ─► summed ─► module woofers
                                                     │   (+ Bose EQ, loudness comp, limiter on powered models)
 Denon SW pre-out (LFE) ──► module LFE RCA ──────────┘   (powered models only; own LFE level knob)
                                                     └─ high-pass (passive network) ─► each cube
```

- **The crossover lives in the module, not in the cubes.** The cubes have no crossover or protection of
  their own. The module's passive network high-passes the signal to each cube, and on passive models
  it routes the low end to the woofers.
- **Crossover point: about 200 Hz** (per forum consensus and Bose's own guides for AM10 I/II, which say to set the
  receiver's crossover to 200 Hz). Measured cube -3 dB point is about 280 Hz, and the module reaches up to
  about 200 Hz (see [Measurements](#4-measurements)). Bose never published the exact filter slopes (unverified).
- **Passive modules** (AM5, AM6 I/II, AM10 I/II) are a band-pass woofer box plus passive crossover.
  The **Denon's amplifiers drive the woofers**, through the same wires that feed the cubes. AM6 II
  uses dual-voice-coil woofers so each channel can drive the woofers directly. On AM6 II/AM10 I the
  center channel has no woofer path, which is why Bose says to set **Center = Small**: the Denon then
  sends center bass to L/R.
- **Powered modules** (AM6 III+, AM10 III+, AM15, AM16). Bose's AM15 II spec sheet lists these features:
  - **"Multi-channel bass extraction and summation"**: the module low-passes every speaker-level input and
    sums them into its own amplifier.
  - **"Active electronic equalization"**: it applies a fixed EQ curve to the module output.
  - **"Bose patented signal processing: automatically adjusts the level of low notes at low volumes"**: this is
    level-dependent loudness compensation, a dynamic EQ that you can't turn off.
  - **Automatic protection circuitry**: a limiter/compressor that reduces output at high levels.
  - The speaker-level signal passes through to the cubes via a passive high-pass. A YouTube teardown of an AM6 III
    says the module "does not have [an] amplifier for the satellite speakers, it only has filters or
    crossovers."
  - An **LFE RCA input** with its own **LFE level knob**, plus a **Bass/Room compensation knob** that "works post-LFE".
- Bose's own description (AM15 II/AM16 guide): *"Integrated Signal Processing assures full bass performance
  from all channels at all listening levels, **regardless of your receiver settings**."* That hub design is
  exactly what you're complaining about.

### Why it conflicts with AVR bass management

| AVR expects | Bose hub does |
|---|---|
| The AVR decides the crossover per channel (Small/Large, 40–250 Hz on the 3806) | A fixed internal crossover at about 200 Hz on every channel, whatever the AVR does |
| One sub channel the AVR can delay, level-trim and EQ on its own | Bass is re-extracted from all 5 speaker feeds and summed in the module. The AVR sees five "full-range" speakers |
| Audyssey measures and corrects each speaker plus the sub separately | Audyssey measures a speaker that is really "cube + shared module". Each channel's correction also changes the shared bass |
| Flat, level-independent response (Audyssey reference) | Bose loudness compensation changes the bass balance with volume, underneath Audyssey |
| The AVR sets sub level | The module's LFE and Bass knobs are extra gain stages in series |
| Bose tells you to set all channels **Large** | This turns off the Denon's bass management completely |

---

## 4. Measurements

Bose doesn't publish frequency response data. The best independent numbers:

| Source | Unit | Cubes | Module |
|---|---|---|---|
| *Sound & Vision*, Aug 1999, via intellexual.net | Acoustimass 15 (Series I) | 280 Hz–13.3 kHz **±10.5 dB**. **-3 dB at 280 Hz, -6 dB at 220 Hz**. Sensitivity 85.1 dB (2.83 V/1 m). Impedance 5.3 Ω min / 8 Ω nominal | 46–202 Hz ±2.3 dB. -3 dB at 46 Hz, -6 dB at 40 Hz |
| Magazine test reprinted on hifi-classic.net (unverified which magazine) | Acoustimass 5 Series II | LF response "dropped at a rate of 15 dB per octave below 300 Hz" (satellite alone). Minimum impedance 4.7 Ω at 300 Hz, under 9 Ω across the satellite's range | — |

What that means:

- **Cubes are useless below about 220–250 Hz.** With about 15 dB/octave rolloff below 300 Hz, the cubes are down roughly 30 dB at 100 Hz.
  Any AVR crossover below about 150 Hz hands the cubes bass they physically can't play.
- **A dip between the module and the cubes (about 200–280 Hz).** The module's -3 dB point (202 Hz) sits below
  the cubes' -3 dB point (280 Hz). Critics call this a "gap" in which "80 Hz is erased". That overstates it,
  because the acoustic sum through the crossover region is a dip, not silence. It's a real weakness in the upper-bass/lower-male-vocal range, though,
  and it's where "boxy/thin voice" complaints come from.
- **±10.5 dB above 280 Hz is very uneven.** Good bookshelf speakers hold ±3 dB. The dual 2.5" paper-cone full-range
  drivers have no tweeter and no crossover. Measured response stops around 13 kHz, and the Direct/Reflecting angle
  adds reflected energy. Response is built around an equalized "presence" balance, not flat (details unverified; the S&V graph itself was not retrievable).
- **The module is a multi-chamber band-pass** (Bose's Acoustimass patent). It trades flatness and time-domain
  behavior (tight bass) for output from small woofers. Audioholics forum engineers (e.g., TLS Guy) describe it
  as high-Q, "sloppy" bass. The 46 Hz -3 dB point is respectable, but there's nothing useful below 40 Hz.

---

## 5. Solutions to "the sub wants all inputs"

Pick the row for your model, then follow the matching fix.

| Your module | Best fix | Effort | How much does the Denon/Audyssey control? |
|---|---|---|---|
| Powered, has LFE RCA | **Fix A** (no mods) | 10 min | Most. The module's filter on the cubes and its EQ on the LFE remain |
| Powered, has LFE RCA | **Fix B** (cubes wired direct) | 1–2 h, cut or adapt cables | Almost all. Only the module's internal EQ/limiter on the LFE path remains |
| Passive (no power cord) | **Fix C** (retire the module, add a powered sub) | 1 h + ~$150–600 | All |
| Any | **Fix D** (replace the system) | — | All, with better sound |

### Fix A — AVR-managed bass *through* the module (no modifications)

Use this on powered models with an LFE input (AM6 III/V, AM10 III/IV/V, AM15 II, AM16).

1. Plug the input cable's **LFE RCA plug into the Denon's SUBWOOFER PRE OUT**. Remove the plug cap first.
2. In the Denon, set **all five channels to Small** and **Subwoofer = Yes**.
3. Set the **crossover to 200 Hz** (or 250 Hz; see §6). The 3806 offers 40/60/80/90/100/110/120/150/200/250 Hz, plus a per-speaker "Advanced" mode.
4. Set Subwoofer mode to **LFE** (not LFE+Main).
5. On the module, set **Bass/Room compensation to its detent** (center) and **LFE level to about the midpoint**. Leave them there.

Why it works: the Denon now high-passes every speaker channel at 200 Hz before the signal reaches the
module. The module's "bass extraction" low-pass then has almost nothing to extract. All the bass, from all
channels plus the LFE channel, arrives through the **LFE RCA**. That signal is Denon-managed, Audyssey-corrected, level-trimmed and time-aligned.

What's left over (limitations):
- The Denon's high-pass (typically 12 dB/oct, unverified for the 3806) still leaks some sub-200 Hz content into
  the speaker feeds. The module sums that leakage with the LFE feed, so a little residual bass is double-processed. It's minor.
- The module's fixed EQ, loudness compensation and limiter still apply to the LFE path (unverified whether the
  LFE input bypasses any of it).
- The module's passive high-pass stays in series with the Denon's before the cubes. That's harmless, because it sits near the cubes' natural rolloff.
- Some users report "lost all bass" after going to Small at 150 Hz. Almost always the LFE RCA isn't connected, the
  LFE knob is at minimum, or the Denon's Subwoofer setting is "No". Check those first.

### Fix B — module becomes a plain powered sub (cubes wired direct)

Use this on the same powered models. It's the cleanest option short of new speakers.

1. **Cubes → Denon directly.** Disconnect each cube cable from the module and connect it to the Denon's speaker terminals.
   - AM6 III/AM10 III/AM15 II/AM16: the module end is an RCA plug. Cut it off and strip the wire, or use an RCA-to-bare-wire adapter. Red collar/marked wire = +.
   - AM10 IV: the module end is a labeled plug. Cut it off and strip it, or buy Bose's "module-to-cube speaker cable adapter" or
     third-party pigtails (sold on eBay/Amazon). The cube end is already a spring clip.
   - AM10 V/AM6 V: plugs at both ends. Cut both, or buy aftermarket plug-to-bare-wire cables (unverified availability).
   - Or run fresh 16 AWG speaker wire to the cube spring clips. This is the simplest option, and cube clips take bare wire.
2. **Module → LFE only.** Keep the original system input cable plugged into the module. Connect **only the LFE RCA**
   to the Denon's sub pre-out, and leave the five speaker-level wire pairs **disconnected**. **Tape or cap every bare end
   so they can't touch each other or anything metal.** No DIY pinout needed.
   If the input cable is lost or damaged, see the pinout below.
3. Denon: all cubes **Small at 200 Hz** (250 Hz if you play loud), Subwoofer = **Yes**, mode **LFE**. Then run Audyssey.
4. **Cube protection.** Bose warns "never connect the cubes directly to a receiver output". The real risk is **driver over-excursion
   from full-range bass**. With the Denon's high-pass at 200–250 Hz and the cubes set Small, that risk is mostly
   gone at sane levels. Two rules:
   - **Never set a directly wired cube to Large**, and never pick a mode that bypasses bass management. **"PURE DIRECT/DIRECT"
     on many Denons ignores the speaker config, and in 2-channel analog Pure Direct the sub goes silent and
     L/R play full range.** Use "STEREO" for music instead (unverified exactly how the 3806 treats Small speakers in
     Direct: test at low volume first).
   - If you'd like belt-and-suspenders protection, add a **~200 Hz first-order high-pass capacitor** in series with each cube:
     about 150–160 µF bipolar/film for a ~5 Ω cube. That's a 6 dB/oct step on top of the Denon's electronic high-pass.
     It's optional, and it shifts the acoustic crossover, so re-run Audyssey afterwards.
5. **Auto-standby caveat.** Series IV/V modules go to standby when they detect no signal. With only the LFE input
   connected, quiet passages may not wake the module fast enough (unverified). If bass drops out after silence,
   raise the LFE knob a notch and lower the Denon's sub trim by the same amount.

**15-pin D-sub input pinout** (AM6 III/AM10 III, from a YouTube teardown; **unverified; confirm with a multimeter before use**):

| Pin | Signal | Pin | Signal |
|---|---|---|---|
| 1 | Left − | 9 | not used |
| 2 | Left + | 10 | Left surround − |
| 3 | Right − | 11 | Left surround + |
| 4 | Right + | 12 | Right surround − |
| 5 | Center − | 13 | Right surround + (listed as "−" in the source, almost certainly a typo) |
| 6 | Center + | 14 | **Subwoofer/LFE + (LINE LEVEL ONLY)** |
| 7 | not used (possibly center surround on AM15 II/AM16, unverified) | 15 | **Subwoofer/LFE −** |
| 8 | not used | | |

- **Pins 14/15 are a low-level input.** Putting amplified speaker-level signal on them "can burn the input preamplifier".
- Pin numbering depends on which face you're looking at (connector vs. plug). Ring each wire through to the unzipped
  pair at the receiver end before trusting the table.
- AM10 IV/V use the same style of connector, but no verified pinout was found. Ring it out the same way.
- Bose sold an "input cable adapter for in-wall wiring" (connector → terminals). It's the tidy, non-destructive way
  to reach the LFE pins if you don't have the original cable.

### Fix C — passive-module systems: retire the module, add a real sub

For AM5, AM6 I/II and AM10 I/II. A passive module has no LFE input. The Denon's sub pre-out
is line level and can't drive it. You have three options:

1. **Recommended.** Wire the cubes direct to the Denon (Small, 200–250 Hz, same rules as Fix B), then add a powered
   subwoofer on the sub pre-out. The sub has to reach **cleanly up to 200–250 Hz**, because it's covering the cubes' whole
   bottom end. Sealed 10–12" subs do this better than ported ones. Place it **near the front stage (close to the
   center cube)**, since bass above ~120 Hz is localizable. Budget: Dayton SUB-1200 (~$150–285), Monoprice/BIC
   (~$200–300), SVS SB-1000 Pro (~$600).
2. **Keep the passive module as a sub** by driving its woofers from an external amp fed by the sub pre-out. You'd need to open the module and wire directly
   to the woofers, bypassing its crossover. It's not worth it: the module is a tuned band-pass, and a cheap powered sub will beat it.
3. **Leave it as Bose intended** (Large, Sub Off, crossover 200 Hz, center Small on AM6 II/AM10 I). The Denon does no bass management. Audyssey still
   runs, but it's correcting a box that re-filters everything.

### Fix D — replace the system

See [§9](#9-honest-sound-quality-assessment-and-upgrade-path). Given the measured limits of 2.5" full-range
cubes, a ~$500 conventional package with a real sub is a bigger upgrade than any wiring trick.

---

## 6. Recommended Denon AVR-3806 settings

Verified against the AVR-3806 owner's manual:
- Crossover choices are **40, 60, 80, 90, 100, 110, 120, 150, 200, 250 Hz**, or **Advanced** (per-speaker).
- Subwoofer modes are **LFE** and **LFE+Main**.
- Speaker impedance is rated **6–16 Ω**.
- Audyssey MultEQ XT supports up to **6 mic positions**.

| Setting | Bose factory way (not recommended) | Fix A / Fix B / Fix C (recommended) |
|---|---|---|
| Front L/R size | Large | **Small** |
| Center size | Large (Small on AM6 II / AM10 I) | **Small** |
| Surround L/R size | Large | **Small** |
| Surround back | None | None (unless you add cubes) |
| Subwoofer | Off (passive) / On (powered) | **Yes** |
| Crossover | 200 Hz (AM10 I/II) / "lowest, e.g. 80 Hz" (powered) | **200 Hz** for all (use Advanced to set per-speaker if you want). **250 Hz** if you listen loud or the cubes sound strained. Never below 150 Hz |
| Subwoofer mode | — | **LFE**. LFE+Main only matters for Large speakers, and it double-counts bass here |
| Distances | Measure | Let Audyssey measure. The module's **sub distance will read longer than physical** because of internal filter/processing delay. The Denon manual says this is normal for "speakers with a built-in filter such as subwoofers". **Keep the measured value** |
| Channel levels | Test tones | Audyssey, then verify with an SPL meter/phone app at 75 dB C-weighted |
| Module knobs (powered) | Taste | **Bass/Room comp at the center detent, LFE at midpoint**. Set before calibration and don't touch afterward. Use the Denon's sub trim instead |
| Room EQ curve | — | "Audyssey" for movies. Try "Flat" for Qobuz music (Audyssey's curve rolls off the treble slightly, and the cubes already stop around 13 kHz) |
| Music mode | — | **STEREO** (bass managed), not PURE DIRECT, for 2-channel Qobuz |

> Why not 80–120 Hz? The cubes are -3 dB at about 280 Hz and roughly 30 dB down by 100 Hz. An 80 Hz crossover
> leaves a hole from about 80 to 220 Hz, which covers the whole male-vocal and upper-bass range. Directly wired cubes also get pushed into over-excursion.
> The downside of 200+ Hz is that bass becomes somewhat localizable to the module. Keep the module near the front.

---

## 7. Audyssey MultEQ XT with Bose

- **Before running it:** do Fix A or Fix B first. Running Audyssey on the factory "hub" wiring measures a mess:
  every channel includes the module, the module's loudness EQ varies with the test-tone level, and the result is often
  "no bass" (AVS thread "Audyssey with Bose Acoustimass = NO BASS").
- **Mic placement:** at seated ear height on a tripod or boom, not on a couch cushion. Position 1 is the main seat.
  Spread positions 2–6 **within about 2 ft** of the main seat rather than across the whole sofa. Audioholics
  regulars report this gives better results.
- **Expected results:**
  - Audyssey will likely detect the cubes as **Small with a 150–250 Hz crossover**, or wrongly call them Large.
    **Raising the crossover after calibration is fine. Lowering it below what Audyssey picked leaves the
    band in between uncorrected** (Audyssey guidance, echoed by Audioholics moderators). So set 200 Hz after
    the run if Audyssey picked lower.
  - A **long sub distance** (see §6) is normal.
  - The module's level may come back near the trim limits. Fix that with the module's LFE knob, then re-run.
  - Audyssey can smooth room modes in the module's range. It **can't** fix the cubes' ±10 dB response
    ripple or their 13 kHz top end.
- **Loudness compensation conflict:** the AVR-3806 predates Audyssey Dynamic EQ (unverified, but Dynamic EQ
  debuted on Denon's 2007-era models). So the only loudness processing in play is Bose's own, inside the module. Calibrate
  at normal volume (the Denon's auto setup handles test levels).
- **Crossover recommendation after Audyssey:** 200 Hz across the board. Center at 150 Hz is OK only if it's
  not directly wired (Fix A).

---

## 8. Known issues and used value (2026)

| Issue | Models | Notes |
|---|---|---|
| **Powered module amplifier failure** (no bass, no sound at all, dead after a surge) | AM6/AM10 III–V, AM15, AM16 | Common in the power supply and amp board (failed transistors, diodes, caps; see the diyAudio AM10 IV thread). Check the fuse first. Replacement amp boards exist (e.g., USAV "Replacement PCB Amplifier board for AM10 III"). Shop repair runs **~$100–200**, which is about what a used module costs. Bose itself recommends a surge suppressor |
| **Protection/limiter pumping** | Powered | Bose documents it: "At high volume levels, the circuit activates to reduce output". This is normal, not a fault |
| **Input cable/connector damage** | III–V (D-sub), I/II (RCA plugs) | Bent pins, broken thumbscrews, frayed "unzipped" pairs. Bose replacement cables sell on eBay for **~$30–40** |
| **Foam surround rot on module woofers** | Older units (AM5, AM6/10 I/II, 1990s) | Foam surrounds degrade in about 10–20 years. Symptoms are buzzing or flapping. Refoam kits for 5.25" drivers are cheap (unverified exact fit) |
| **Cube driver damage** | All | Grille cloth sits right on the drivers ("easily damaged"). Direct wiring without a high-pass kills them |
| **Auto-standby dropouts** | IV/V | Module sleeps on silence and is slow to wake at low levels (unverified; commonly reported) |
| **Magnetic shielding** | All | Cubes are shielded. Irrelevant for the LED Vizio |

**Used value (2026, rough; eBay/HiFiShark asking prices, unverified):**

| System | Complete, working | Module only |
|---|---|---|
| AM5 Series II/III | $40–100 | $25–60 |
| AM6 II / AM10 I/II (passive) | $50–120 | $30–60 |
| AM6 III–V | $75–175 | $50–100 |
| AM10 III–V | $100–250 | $60–175 |
| AM15 II / AM16 | $100–250 | $75–150 |

It holds resale value better than it deserves on sound quality alone, because of the brand. **Selling it funds most of a
~$500 replacement package.**

---

## 9. Honest sound-quality assessment and upgrade path

**Assessment:**
- **Good at:** being invisible, sounding "big" for the size in casual listening, dialogue at moderate volume, easy
  placement.
- **Poor at:** tonal accuracy (±10.5 dB), treble extension (stops around 13 kHz), the 200–300 Hz
  handoff (thin or boxy male voices, cellos, guitars), dynamics and headroom (limiter), deep bass (nothing below 40 Hz),
  imaging (Direct/Reflecting diffuses it on purpose), and transient "tightness" (band-pass module).
- **With a Qobuz hi-res source**, the cubes are the bottleneck by a wide margin. Hi-res content above 13 kHz is inaudible on them.
- **Verdict:** Fix A or B makes the Denon the brain and gets you a coherent, calibratable system. That's worth doing
  now for free. But **no wiring fix changes the fact that 2.5" full-range cubes can't cross over below ~200 Hz**, and
  that one handoff causes most of the sound problems. For real fidelity, replace the system.

**Upgrade packages that work cleanly with an AVR** (passive speakers with binding posts, plus a powered sub on the
LFE/sub pre-out; typical crossover 80–120 Hz). Prices are rough 2026 street prices. Verify before buying.

| Package | Type | Approx. price (2026) | Notes |
|---|---|---|---|
| **Pioneer SP-PK22BS / Andrew Jones 5.1** | Bookshelf + 8" powered sub | ~$450–500 (often discontinued, check stock or used) | Classic budget reference. Big step up in coherence |
| **Klipsch Reference Theater Pack 5.1** | Small satellites + 8" wireless sub | ~$500 | **Closest to the Bose footprint.** Horn-loaded tweeters sound bright. Sub is wireless (the transmitter plugs into the sub pre-out) |
| **Polk T15/T30 or Monitor XT + PSW10/MXT10 sub** | Bookshelf + 10" sub | ~$500–800 built piecemeal | Easy availability, forgiving |
| **Micca MB42X ×4 + MB42X-C + a sub** | Compact bookshelf | ~$350–500 with a Dayton SUB-1200 | Tiny, surprisingly good, great value |
| **ELAC Debut 2.0 (B5.2/B6.2 + C5.2/C6.2) + sub** | Bookshelf | ~$1,000–1,300 as 5.1 | Andrew Jones design. Much better music playback for Qobuz |
| **SVS Prime Satellite 5.1** | Small 2-way satellites + SB-1000 Pro 12" sealed sub | ~$1,000–1,400 | **Best small-footprint option.** Satellites are about 8.5" tall, the sub is excellent, crossover at 80–100 Hz |
| **Subs alone** | — | Dayton SUB-1200 ~$150–285, SVS SB-1000 Pro ~$600–700 | Use for Fix C, or reuse later with new speakers |

**Staged path (recommended):**
1. **Now, $0:** Fix A (or B). Set the Denon per §6 and run Audyssey.
2. **Next, ~$150–600:** buy a real powered sub (SB-1000 Pro if it fits the budget) and use it in place of the Bose module on the
   sub pre-out, with the cubes wired direct at 200 Hz. The sub carries over to any future speakers.
3. **Then, ~$300–800:** replace the cubes with small bookshelf/satellite speakers (Micca, SVS Prime Satellite, ELAC),
   drop the crossover to 80–100 Hz, and re-run Audyssey. Sell the Bose.

---

## 10. How it fits this system

- **Denon AVR-3806:** The Denon can run the whole show: 7 channels of amplification, a sub pre-out, crossover up to **250 Hz**, and Audyssey MultEQ XT.
  The Bose hub topology is the only thing stopping it. After Fix A/B, the Denon owns bass management, delay, levels and room EQ.
  Watch the impedance: the Denon is rated 6–16 Ω and Bose loads are about 5 Ω minimum. That's fine at normal levels, but
  sustained high volume may trip protection.
- **Xbox One (Dolby Digital / stereo uncompressed):** With Small + sub, Dolby Digital's LFE and all redirected bass go through the
  Denon to the module/sub consistently. The README's stereo-upmix complaint is separate: that's the Xbox's DD encode
  vs. PCM output. With cubes Small, stereo PCM from the Xbox still gets bass-managed to the sub in STEREO mode.
- **Dell OptiPlex / Qobuz:** Use **STEREO** mode, not PURE DIRECT, so the cubes stay high-passed and the sub plays. The cubes cap
  fidelity at about 13 kHz and have a ±10 dB response, so hi-res streams gain nothing audible until the speakers are upgraded.
- **Vizio VS420LF1A:** The cubes are magnetically shielded (irrelevant for LED anyway). The center double cube sits above or below the
  TV. Keep the module/sub near the front stage because of the 200 Hz crossover.
- **Future sound-reactive light:** Take audio from a **line-level tap**, such as the Denon's Zone 2 pre-out or a pre-out splitter, or use a mic.
  Don't take it from speaker wires. After Fix B, the module's **unused speaker-level pairs must stay insulated**. Don't repurpose them as a light's signal source.

---

## 11. Sources

**Bose owner's guides / spec sheets (primary)**
- Acoustimass 6 Series III / Acoustimass 10 Series IV owner's guide (AM294330): https://www.glenwarren.com/Manuals/Bose_Accoustimass_10_Series_IV_Surround_Sound_System_Manual_owg_en_am6_series3_am10_series4.pdf
- Acoustimass 6 Series III / 10 Series IV (Bose-hosted copy): https://products.bose.com/pdf/customer_service/owners/og_am6_10.pdf
- Acoustimass 6 Series III / Acoustimass 10 Series III owner's guide: https://products.bose.com/pdf/customer_service/owners/am6iii_am10iii_guide.pdf
- Acoustimass 10 (Series I) owner's guide: https://products.bose.com/pdf/customer_service/owners/am10_guide.pdf
- Acoustimass 10 Series II owner's guide: https://products.bose.com/pdf/customer_service/owners/am10ii_guide.pdf
- Acoustimass 6 Series II owner's guide: https://products.bose.com/pdf/customer_service/owners/am6ii_guide.pdf
- Acoustimass 5 Series III owner's guide: https://products.bose.com/pdf/customer_service/owners/og_am5iii.pdf
- Acoustimass 15 Series II / Acoustimass 16 owner's guide: https://products.bose.com/pdf/customer_service/owners/am15ii_am16_guide.pdf
- Acoustimass 15 Series II spec sheet (bass extraction, active EQ, loudness processing): https://content.abt.com/documents/26244/am15_specs.pdf
- Acoustimass 15 (Series I) Bose product copy (archived): http://www.bkjproductions.com/bose/browser/htm/am15copy.htm
- Acoustimass 6 Series V / 10 Series V owner's guide: https://assets.bose.com/content/dam/Bose_DAM/Web/consumer_electronics/global/products/speakers/acoustimass_10_series_v_home_theater_speaker_system/pdf/AM720420_02_OG_Acoustimass_6V_10V_ENGvo.pdf
- AM10 Series V guide summary: https://manuals.plus/bose/bose-acoustimass-10-series-v-stereo-speaker-system

**Denon**
- AVR-3806 owner's manual (crossover list, sub modes, impedance, Audyssey): https://www.denon.com/on/demandware.static/-/Library-Sites-denon_apac_shared/default/dwd8318111/downloads/archived/avr-3806-owners-manual-en.pdf

**Measurements / analysis**
- intellexual.net AM-15 review (quotes the Sound & Vision Aug 1999 measurements): http://www.intellexual.net/bose.html
- Audioholics, "Bose Speaker Measurements & Frequency Response Graphs": https://forums.audioholics.com/forums/threads/bose-speaker-measurements-frequency-response-graphs.38446/
- hifi-classic.net, Acoustimass 5 Series II (reprinted test data): https://www.hifi-classic.net/review/bose-acoustimass-5-series-ii-79.html
- Bose patent 5,659,157 (multi-chamber acoustic speaker): https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/5659157

**Forums / community mods**
- Audioholics, "bose acoustimass 10 serie II" (Denon X3100 setup, Small @ 200 Hz, TLS Guy on the module): https://forums.audioholics.com/forums/threads/bose-acoustimass-10-serie-ii.107567/
- Audioholics, "Audyssey set crossover to 200hz" (raising vs. lowering crossover after Audyssey, mic placement): https://forums.audioholics.com/forums/threads/audessey-set-crossover-to-200hz-time-to-manually-calibrate.98423/
- AVS Forum, "Audyssey with Bose Acoustimass = NO BASS": https://www.avsforum.com/threads/audyssey-with-bose-acoustimass-no-bass-help.3289213/
- AVS Forum, "bose acoustimass 10 Series IV settings": https://www.avsforum.com/threads/bose-acoustimass-10-series-iv-settings.924266/
- AVS Forum, "Small Or Large Bose Acoustimass 10": https://www.avsforum.com/threads/small-or-large-bose-acoustimass-10.1443006/
- AVS Forum, "bose cubes without acoustimass15 bass module": https://www.avsforum.com/threads/bose-cubes-without-acoustimass15-bass-module.1168309/
- YouTube, AM6 Series III module 15-pin pinout: https://www.youtube.com/watch?v=tA64mVYUGUU
- ecoustics, Acoustimass 9 / Lifestyle DIN pinout discussion: https://www.ecoustics.com/electronics/forum/home-audio/591057.html
- Home Theater Shack, AM10 III receiver cable: https://www.hometheatershack.com/threads/acoustimass-10-series-iii-subwoofer-to-receiver-connection-cable.72149/
- diyAudio, AM10 IV module "no sound" repair: https://www.diyaudio.com/community/threads/bose-acoustimass-10-iv-subwoofer-no-sound-help-with-burnt-component-identification.420039/
- USAV replacement AM10 III amp board: https://usavshop.com/Replacement-PCB-Amplifier-board-for-Bose-ACOUSTIMASS-10-Series-III-p634512325
- hifi-wiki, AM10 III (active module, 2 × 13 cm woofers): https://hifi-wiki.com/index.php/Bose_Acoustimass_10_III
- Bose Wikia, surround packages (history/years): https://bose.fandom.com/wiki/Surround_sound_speaker_packages

**Pricing (2026)**
- SVS Prime Satellite 5.1: https://www.svsound.com/products/prime-satellite-5-1
- SVS SB-1000 Pro: https://www.svsound.com/products/sb-1000-pro-subwoofer
- Klipsch Reference Theater Pack 5.1: https://www.klipsch.com/products/reference-theater-5-1-surround-sound-system
- Pioneer SP-PK22BS review: https://www.themasterswitch.com/review-pioneer-sp-pk22bs-andrew-jones-51
- Dayton Audio SUB-1200: https://www.parts-express.com/Dayton-Audio-SUB-1200-Powered-Subwoofer-300-629
- Used Acoustimass pricing: https://www.hifishark.com/model/bose-acoustimass-10 , https://www.ebay.com/b/Bose-Acoustimass-10-Series-IV-Home-Speakers-and-Subwoofers/14990/bn_7117196176
