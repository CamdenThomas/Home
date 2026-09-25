# Xbox One (original / One S / One X)

> Role in this system: the source for **all streaming and all gaming**.
> Signal chain today: Xbox One → Denon AVR-3806 (HDMI 1.1, no Dolby Digital Plus, no Atmos, no CEC) → Vizio VS420LF1A (42" 1080p) and Bose Acoustimass speakers.
>
> Main complaint: you have to switch the Xbox between **Bitstream (Dolby Digital)** and **Stereo uncompressed** by hand. In Dolby Digital mode, stereo content plays only on the front L/R speakers and the Denon won't upmix it.
>
> Researched September 2026. Anything marked **(unverified)** came from forum reports or reasoning and has no primary source behind it. Test those items on your own gear.

---

## TL;DR: the fix for the DD / stereo switching problem

> **Update 2026-09-24 (owner tested):** with the Xbox on 5.1 uncompressed, stereo content arrives as 6-channel PCM with silent channels, and PLIIx is locked out, exactly as with DD. The current recommended fix (Xbox optical → DAC → the Xbox source's analog input, toggled with INPUT MODE) is in [SETUP.md](../../SETUP.md#3-xbox-one-the-stereo51-problem-solved-as-far-as-current-gear-allows).


1. **Why it happens.** The Xbox never passes audio through in its original channel count. It mixes *everything* (apps, games, menu sounds) into one fixed output format. In Bitstream/Dolby Digital mode that output is always a DD 5.1 stream, so stereo content becomes "5.1 with only L/R filled". The Denon sees **Dolby Digital 3/2.1**. On the AVR-3806, Pro Logic IIx is available only for **2-channel** sources, so it won't upmix. This is a limit of how the Xbox works, not a fault in your setup.
2. **The free fix, available today (recommended).** Connect the Xbox **by HDMI to the Denon** and set **HDMI audio = 5.1 uncompressed**, then leave it there. The Xbox decodes Netflix/Disney+/etc. Dolby Digital Plus into lossless multichannel PCM, which is better than re-encoding it to lossy DD. The AVR-3806 can't decode DD+ anyway. Games get discrete 5.1. When something is stereo-only (YouTube, Spotify, some streams), press the Denon's dedicated **7CH STEREO** button (it shows *5CH STEREO* if you have no surround-back speakers). The Denon manual's mode table lists 7CH STEREO and the other DSP modes as selectable for multichannel PCM **and** Dolby Digital 5.1 inputs. 7CH STEREO sends L to all left speakers, R to all right, and the in-phase (dialog) part to the center. The switch becomes one button on the Denon remote instead of a trip through the Xbox menus.
3. **Free, one-button, real Pro Logic IIx for stereo.** Use two audio paths into the Denon (Xbox HDMI → TV → TV optical → Denon for PCM stereo, plus Xbox optical → Denon for DD 5.1) and change Denon inputs instead of Xbox settings. See [Solution B](#solution-b-dual-path-one-button-input-switch).
4. **The only fix with no switching at all** is a streamer that sends **stereo as PCM 2.0 and surround as native DD 5.1**. An **Nvidia Shield TV** set to "Manual → AC3 only" with Dolby audio processing converting DD+ to DD does this, and a Fire TV set to "Dolby Digital" probably does too **(unverified)**. The Denon's *Auto Surround Mode* memory then applies PLIIx to stereo and Dolby Digital to 5.1 on its own. The Xbox stays for games. **Xbox Series X|S has the same audio pipeline and does not fix this.**

---

## 1. Which Xbox One do you have?

| Clue | Original Xbox One (2013) | Xbox One S (2016) / S All-Digital (2019) | Xbox One X (2017) |
|---|---|---|---|
| Model number (sticker on back/bottom) | **1540** | **1681** | **1787** |
| Look | Big "VCR" box, half glossy / half matte black, vent grille over the whole top | ~40% smaller; usually **white** ("Robot White"), with some black/blue/special editions; perforated right side of the top | Compact, **matte black**, flat top, "XBOX ONE X" text; the heaviest of the three |
| Power supply | **External brick** | Internal (figure-8 / C7 cord) | Internal (figure-8 / C7 cord) |
| Power / eject buttons | Capacitive (touch) | Physical buttons | Physical buttons |
| Kinect port | Proprietary port on back | None (needs USB adapter) | None (needs USB adapter) |
| Disc slot | Blu-ray | UHD Blu-ray (All-Digital: **no drive**, no eject button) | UHD Blu-ray |
| Software clue | No 4K / HDR options in video settings | 4K and HDR options appear (4K TV required) | Same as S; "4K" and "Xbox One X Enhanced" labels on games |

You can also look in **Settings > System > Console info**, which on current firmware reportedly shows the console type **(unverified)**.

## 2. Specs by variant

| Spec | Original Xbox One | Xbox One S | Xbox One X |
|---|---|---|---|
| Release (NA) | Nov 22, 2013 | Aug 2, 2016 (All-Digital: May 7, 2019) | Nov 7, 2017 |
| Discontinued | ~2016 (replaced by S) | End of 2020 | July 2020 |
| Launch price | $499 (with Kinect) | $299 (500 GB) | $499 |
| CPU | 8-core AMD Jaguar @ 1.75 GHz | 8-core Jaguar @ 1.75 GHz | 8-core "evolved" Jaguar @ 2.3 GHz |
| GPU | 12 CU @ 853 MHz, 1.31 TFLOPS | 12 CU @ 914 MHz, 1.4 TFLOPS | 40 CU @ 1172 MHz, 6.0 TFLOPS |
| RAM | 8 GB DDR3 + 32 MB ESRAM | 8 GB DDR3 + 32 MB ESRAM | 12 GB GDDR5 (326 GB/s) |
| Storage | 500 GB / 1 TB HDD | 500 GB / 1 TB / 2 TB HDD | 1 TB HDD |
| External storage | USB 3.0, ≥128 GB, games allowed | same | same |
| HDMI out | 1.4b, 1080p max | 2.0a, 4K60, HDR10 | 2.0b, 4K60, HDR10 |
| HDMI in (TV passthrough) | 1.4b (1080p) | 1.4b (1080p) | 1.4b (1080p; no 4K passthrough) |
| Optical (S/PDIF) out | Yes | Yes | Yes |
| IR | IR receiver; IR Out port on back; Kinect acts as IR blaster | Built-in **front IR blaster** + IR Out port | Built-in **front IR blaster** + IR Out port |
| USB | 3 × USB 3.0 (2 back, 1 side) | 3 × USB 3.0 (1 front, 2 back) | 3 × USB 3.0 (1 front, 2 back) |
| Disc | Blu-ray / DVD / CD | **UHD Blu-ray** / BD / DVD / CD (All-Digital: none) | **UHD Blu-ray** / BD / DVD / CD |
| 4K / HDR | No / No | 4K video + upscaled games; HDR10; Dolby Vision (Netflix, streaming only, 2018) | Native 4K games; HDR10; Dolby Vision streaming (2018) |
| 120 Hz / VRR / ALLM | No | 1080p/1440p 120 Hz, FreeSync VRR, ALLM (2018 updates) | same |
| HDMI-CEC | No | Not listed by Microsoft (see §6) | **Yes** (Microsoft lists One X) |
| Wi-Fi | 802.11n | 802.11ac | 802.11ac |
| Power draw (approx.) | ~70–120 W gaming, ~13–16 W "instant-on" standby | ~35–90 W gaming | ~55 W dashboard, up to ~172–180 W in enhanced games |
| Fan noise | Very quiet: big slow fan, oversized case | Quiet | Quiet for its power (vapor-chamber cooler); louder than the S under load |

Status in 2026: all three still get system updates and share the store and apps with Series X|S. First-party and big third-party games are leaving the platform (for example, Forza Horizon 6 dropped Xbox One, March 2026), and Social Clubs were removed in April 2026. Movies & TV stopped selling and renting in July 2025, though purchases still play. As a streaming box it still works. A used unit sells for about $99–199 (Pure Xbox).

---

## 3. Audio output settings (deep dive)

Path: **Xbox button → Profile & system → Settings → General → Volume & audio output.** Some items sit under an **Advanced** sub-page on newer firmware.

### 3.1 The key idea: the Xbox is a mixer, not a passthrough device

Games, apps, system sounds, notifications and party chat all go through the console's audio mixer, which outputs **one fixed format that you choose**. The format does **not** change with the content. That is why:

- In **Bitstream / Dolby Digital**, the Xbox runs a real-time DD encoder, so *everything* leaves as DD 5.1, including stereo YouTube. Nakamichi's Xbox support page says it directly: *"For YouTube and other content encoded in stereo 2.0, XBOX system is not able to upmix 2.0 to multiple channels audio when set to 'Bitstream'."* Their fix is to switch to Stereo uncompressed and let the soundbar upmix, which is exactly your manual workaround.
- In **5.1 / 7.1 uncompressed**, stereo content goes out as 6 or 8 channels of LPCM with only FL/FR carrying sound. The receiver shows "MULTI CH IN", and PLII-type upmixing isn't available. This matches an AVForums case (Xbox One S + Denon X3500) where Prime Video and All4 had no center channel unless the Xbox was set to stereo. The expert there explained that some streams even come as "5.1 with the centre and surround channels silent". **(Reported behavior; Microsoft doesn't document it.)**
- In **Stereo uncompressed**, *everything* is downmixed to 2-channel PCM, including games and real 5.1 movies. The receiver sees PCM 2.0 and can apply PLIIx or other upmixers, but you lose discrete surround.

The "Allow bitstream passthrough" option (2021) exempts some app content from this mixer (see 3.5). With your receiver it helps very little.

### 3.2 Speaker audio options

| Setting | Options | What it actually does | For the AVR-3806 |
|---|---|---|---|
| **HDMI audio** | Off / **Stereo uncompressed** / **5.1 uncompressed** / **7.1 uncompressed** / **Bitstream out** | Uncompressed = LPCM at the chosen channel count (48 kHz). The Xbox decodes every source (DD+, DTS, Atmos, TrueHD from Blu-ray) itself and remaps it. Bitstream out = the Xbox encodes its mix to the format picked under *Bitstream format*. | **5.1 uncompressed** (see §4). The 3806 accepts multichannel PCM over HDMI, but **7.1 PCM needed a firmware patch on some early 3806 units**, so use 5.1 unless you've confirmed 7.1 works. |
| **Optical audio** | Stereo uncompressed / Bitstream out | S/PDIF carries only 2-ch PCM or compressed DD/DTS (no multichannel PCM, no DD+/Atmos). Set separately from HDMI, and **both ports output at the same time**, so HDMI can be PCM while optical is DD. | Useful for Solution B. |
| **Bitstream format** | **Dolby Digital** / **DTS Digital Surround** / **Dolby Atmos for home theater** / **DTS:X for home theater** | One setting shared by HDMI and optical. DD and DTS are 5.1 real-time encodes. Atmos for home theater sends Dolby MAT/TrueHD-based Atmos over HDMI and needs the free *Dolby Access* app. DTS:X needs the *DTS Sound Unbound* app. | **Dolby Digital or DTS only.** The 3806 predates Atmos, DTS:X, DD+ and TrueHD, so Atmos or DTS:X output will give **no sound**. DTS is a higher-bitrate encode and some people prefer it **(subjective)**. Either way, stereo content still comes out as "5.1 with only fronts". |
| **Allow bitstream passthrough** | On / Off (only shown with Bitstream out) | Added in the May 2021 update. Lets apps that support it hand their native bitstream straight to the receiver instead of the Xbox's encoder. Forum reports show Netflix, Prime Video, Disney+, Apple TV, Plex, and Movies & TV (TrueHD / DTS-HD MA from local files) arriving at the AVR as "Dolby Atmos DD+" instead of "Multi-Ch PCM". Results vary by app and TV. | **Leave OFF.** The 3806 can't decode DD+ (the format streaming apps use), and the main benefit is Atmos. The one theoretical upside: native **DD 2.0** or **DTS** tracks from Plex/Kodi/discs would reach the Denon unchanged, and PLIIx works on DD 2.0. Whether the Xbox checks the receiver's EDID before sending DD+ it can't decode is **unverified**, which is a risk of silence. |
| **Blu-ray app passthrough** ("Let my receiver decode audio" in older UIs) | On / Off | Sends the disc's native track (DD, DTS, TrueHD, DTS-HD MA, Atmos, DTS:X) untouched. | **Off.** With 5.1 PCM the Xbox decodes TrueHD / DTS-HD MA to **lossless** PCM, which the 3806 plays. Passthrough would send formats it can't decode. |

### 3.3 Headset options (same page)

| Setting | Options / notes |
|---|---|
| Headset format | Stereo uncompressed, **Windows Sonic for Headphones** (free), **Dolby Atmos for Headphones** (paid license via Dolby Access), **DTS Headphone:X** (paid via DTS Sound Unbound). These are virtual-surround modes for a headset plugged into the controller, and they don't affect HDMI or optical. |
| Headset chat mixer | Balance between game audio and chat. |
| Mute speaker audio when headset connected | Handy at night. |
| Party chat output | Headset / Speakers / Both. |
| Mono output | Accessibility: sums everything to mono. |

### 3.4 How the Xbox "knows" what your receiver can do: EDID vs optical

- **HDMI:** the sink (TV, or the AVR acting as an HDMI repeater) sends an **EDID** block. Its *Short Audio Descriptors* list what it can decode, for example "LPCM up to 8 ch, 48/96 kHz; AC-3; DTS". The Xbox uses this for format decisions such as Atmos and passthrough availability. It doesn't strictly lock the menu: you can pick 5.1 uncompressed even if the EDID only says stereo, and then you may get silence or a downmix **(unverified in detail)**. With the Denon in the chain, set **HDMI In Assign → HDMI audio = AMP** so the Denon plays the audio. Early Denon HDMI receivers had known EDID quirks, so if the Xbox behaves as if it's connected to a TV (stereo only), check that the Denon is powered on before the Xbox.
- **Optical:** there is **no return channel and no EDID**. The Xbox can't detect anything about a device on the optical cable, so it simply sends what you choose. That is also why, in *Stereo uncompressed*, the Xbox doesn't "know" the Denon can do DD. It isn't detecting anything: stereo uncompressed means "decode and downmix everything to 2-ch PCM", by definition.
- **Vizio TV in the middle:** the Vizio's EDID advertises only 2-ch PCM **(likely; unverified)**. If the Xbox's HDMI goes to the TV, not the Denon, the Xbox only sees a stereo TV.

### 3.5 Per-app and per-content behavior (with the Xbox on 5.1 uncompressed and passthrough off)

| Source | Native audio | What the Denon receives | Denon mode |
|---|---|---|---|
| Games | Discrete 5.1/7.1 from the Xbox mixer | 5.1 PCM | MULTI CH IN (discrete) |
| Netflix / Disney+ / HBO Max / Prime / Paramount+ / Apple TV / Hulu 5.1 titles | DD+ 5.1 (Atmos on some titles/plans) | 5.1 PCM, decoded by the Xbox (Atmos heights folded in) | MULTI CH IN |
| Streaming stereo titles, YouTube, Spotify, Twitch | AAC / Opus stereo | 5.1 PCM with only FL/FR active | Press **7CH STEREO** |
| UHD/Blu-ray (disc app) | TrueHD / DTS-HD MA / DD / DTS | 5.1 PCM, lossless for TrueHD / DTS-HD | MULTI CH IN |
| DVD with DD 2.0 / mono | DD 2.0 | 5.1 PCM with fronts (or center) only | 7CH STEREO, or MONO MOVIE for mono |
| Plex / Kodi local files | Anything | 5.1 PCM (Plex/Kodi can bitstream only with Bitstream out + passthrough **(unverified per app)**) | as above |

---

## 4. Diagnosis of your problem

**Symptom 1: "In Dolby Digital mode stereo only plays on L/R and the Denon can't upmix."**
The Xbox encodes stereo into a **DD 5.1** stream with silent center and surrounds. The AVR-3806 mode table (owner's manual, pp. 96–97) shows that for **Dolby Digital 5.1** input you can choose DOLBY DIGITAL, DD+PLIIx (which only *adds surround-back* channels), DIRECT, or **DSP SIMULATION modes including 7CH STEREO / MATRIX / WIDE SCREEN**. **Pro Logic II/IIx Cinema/Music/Game are listed only for 2-channel sources** (analog, 2-ch PCM, DD 2.0, DTS 2.0). So PLIIx really isn't available, but **7CH STEREO is** and works as a one-button workaround.

**Symptom 2: "In Stereo uncompressed the Xbox doesn't know the Denon can do DD."**
Nothing is being detected. Stereo uncompressed means *always output 2-channel PCM*. The Xbox decodes Netflix's DD+ 5.1 and folds it down to stereo, and the Denon can only rebuild pseudo-surround with PLIIx. Whether the Xbox's downmix is matrix-encoded (Lt/Rt, which PLIIx decodes well) or plain Lo/Ro is **unverified**.

**The underlying limit:** the Denon's *Auto Surround Mode* remembers one surround mode for each of four signal types: (1) analog / PCM 2-ch, (2) DD/DTS 2-ch, (3) DD/DTS multichannel, (4) multichannel PCM (MULTI CH IN). Automatic "upmix stereo, play 5.1 as-is" works only if the **source changes format with the content**, and the Xbox never does.

### Denon AVR-3806 facts that matter here (from the manual and forums)

| Fact | Source |
|---|---|
| "The AVR-3806 is HDMI Ver. 1.1 compatible." 2 HDMI in / 1 out, HDCP supported | Owner's manual p. 20 |
| "The AVR-3806 cannot be controlled by another device via the HDMI connector" (**no CEC**) | Owner's manual p. 21 |
| HDMI audio: per-input **TV / AMP** setting | Owner's manual pp. 66–67 |
| Multichannel PCM over HDMI works (PS3 5.1 PCM confirmed, "Multi-Channel + PLIIx") | Audioholics / AVS owner reports |
| **Some early units needed a firmware patch (RS-232) for 7.1 PCM 24/96 over HDMI** | AVForums "New 3806 firmware", HiFiVision |
| No Dolby Digital Plus, TrueHD, DTS-HD, or Atmos decoding | Manual format list (DD, DD EX, DTS, DTS-ES, DTS 96/24, PLIIx, Neo:6) |
| HDMI video is passed at the source resolution; 1080p passthrough reported working | Manual p. 21; AVS thread |
| Per-input **Audio Delay** (lip sync) setting | Manual p. 68 |

---

## 5. Solutions, ranked

### Solution A (recommended, free): HDMI to the Denon, 5.1 uncompressed, and the 7CH STEREO button

1. Cable: **Xbox HDMI OUT → Denon HDMI IN 1 → Denon HDMI MONITOR OUT → Vizio**.
2. Denon: *Video Setup → HDMI In Assign*: assign HDMI 1 to the Xbox's input (for example "DBS" or "V.AUX"), **HDMI audio = AMP**.
3. Xbox: **HDMI audio = 5.1 uncompressed**, Optical = Off (or anything), passthrough off, Blu-ray passthrough off.
4. Check the Denon shows **MULTI CH IN** during a Netflix 5.1 title and all speakers play.
5. For stereo content, press **7CH STEREO** (front panel or remote). Go back with the STANDARD / MULTI CH IN mode button. Try **MATRIX** too: it sends the L−R "ambience" difference to the surrounds, which some people prefer for music.
6. If you have no surround-back speakers (likely with a Bose 5.1 Acoustimass), the button shows **5CH STEREO**.

Pros: best quality you can get from this receiver (lossless PCM from DD+/TrueHD/DTS-HD, discrete game audio). One button instead of a menu trip. No purchase.
Cons: still a manual press for stereo content, and 7CH STEREO isn't as refined as PLIIx for film.
Try 7.1 uncompressed only if you have 6.1/7.1 speakers and your 3806 handles it. If you get dropouts or silence, you need the firmware patch.

### Solution B: dual path, one-button input switch

Uses the Xbox's ability to send **different formats on HDMI and optical at the same time**, plus the Vizio's **S/PDIF digital audio out** (listed in the VS420LF1A service manual).

1. **Xbox HDMI → Vizio** directly (video). Xbox **HDMI audio = Stereo uncompressed**.
2. **Vizio optical out → Denon optical input A**, on a Denon source such as "TV". The Denon gets PCM 2.0, and its Auto Surround memory applies **PLIIx Cinema** to stereo automatically. Turn the TV speakers off.
3. **Xbox optical → Denon optical input B**, on a source such as "DBS". Xbox **Optical audio = Bitstream out, Bitstream format = Dolby Digital**. The Denon gets DD 5.1.
4. Content is stereo → press the Denon's "TV" input. Content is 5.1 or a game → press "DBS". Set **Audio Delay** per input if lip sync is off.

Pros: real PLIIx for stereo, switching is one input button, and the Denon remembers the mode for each input.
Cons: surround is lossy DD 640 kbps (a re-encode of DD+), not PCM. It depends on the Vizio's optical out passing PCM from HDMI **(verify)**. Two cables. It doesn't work with the Xbox's HDMI going through the Denon: the 3806 allows each HDMI terminal on only **one** source, so the second source would have no video.

### Solution C (only true zero-switching fix): a streamer that outputs native channel counts, with the Xbox kept for games

- **Nvidia Shield TV / Shield TV Pro ($149 / $199; the Pro is often out of stock in 2026):** *Settings → Device Preferences → Display & Sound → Advanced sound settings → Available formats → **Manual**, enable **AC3 (Dolby Digital) only***. Nvidia documents this for legacy AVRs. Dolby content is "decoded/converted to the best available format for your home theater" (DD+ → DD 5.1), DTS passes through, and stereo goes out as **PCM 2.0** with *Stereo upmix* left off **(stereo-as-PCM-2.0 reported, unverified)**. The Denon then plays PLIIx for stereo and Dolby Digital for 5.1 **automatically**.
- **Fire TV Cube (3rd gen, ~$110–140):** *Display & Sounds → Audio → Surround sound = Dolby Digital* converts DD+ to DD. Stereo as PCM 2.0 is **unverified**.
- **Apple TV 4K ($199/$249 after the 2026 price rise; a new model is expected fall 2026):** not recommended here. In "Auto" it sends multichannel LPCM (or Dolby MAT). Setting "Dolby Digital 5.1" reproduces the Xbox's problem. Apple forum users report trouble getting receivers to upmix stereo.
- **Xbox Series X ($799.99) / Series S ($499.99) as of Aug 2026:** **same audio pipeline** as the One (fixed output format, stereo inside DD 5.1), and **no optical out**. It doesn't fix this and costs a lot. Upgrade only for games.

### Solution D (long term): a modern AVR

A current Denon/Marantz decodes DD+ and Atmos (so "Allow bitstream passthrough" becomes useful), has HDMI-CEC for power control, and offers upmixers on more input types (Multi Ch Stereo works on any input). The Xbox would still wrap stereo inside its chosen format, so some manual mode choice may remain **(unverified)**. This belongs on the Denon's page.

---

## 6. Video output settings

Path: **Settings → General → TV & display options.**

| Setting | Options | For the Vizio VS420LF1A through the AVR-3806 |
|---|---|---|
| Resolution | 720p / 1080p (+ 1440p / 4K on S/X with a capable TV) | **1080p** |
| Refresh rate | 50 / 60 Hz (120 Hz on S/X with a capable TV) | **60 Hz** |
| TV connection | Auto-detect / HDMI / DVI | Auto. If audio is missing or colors look wrong, force **HDMI**. |
| Video fidelity & overscan → **Color depth** | 24-bit (8 bpc) / 30-bit / 36-bit | **24 bits per pixel.** The Vizio is an 8-bit panel, and HDMI 1.1 on the Denon carries no deep color. |
| **Color space** | Standard (recommended) / PC RGB | **Standard** (limited range, the TV standard). Only use PC RGB if the TV is set to full range. Check the Denon's HDMI Out Setup color format/range too. |
| **Allow 24 Hz** | on/off | **Off** unless you've confirmed the Vizio accepts 1080p24 (unverified). Otherwise Blu-ray/apps may switch to a mode the TV rejects. |
| Allow 50 Hz | on/off | Off (US) |
| Allow 4K / Allow HDR10 / Allow Dolby Vision / Allow YCC 4:2:2 | S/X only, shown only with a capable display | Not offered or not applicable. Leave off. |
| Allow VRR / ALLM (S/X) | on/off | Not supported by the Vizio or the Denon; harmless. |
| Display calibration | Built-in test patterns | Worth running once for brightness/contrast. |
| Overscan / "apply border" | on/off | Use the Vizio's "Just Scan"/1:1 mode if it has one; otherwise add a border. |

**HDMI through the old AVR:**

- The 3806 passes video at the source's resolution (it can't scale HDMI) and supports HDCP 1.x, which is enough for 1080p streaming.
- If you get a blank screen, turn devices on in this order: **TV → Denon → Xbox**.
- The Denon's own on-screen menu over HDMI requires "Analog to HDMI Convert = ON".
- Keep HDMI cables at 5 m or less (Denon's recommendation).

---

## 7. Power control: turning on the TV and the Denon

| Method | Original | One S | One X | Works with your gear? |
|---|---|---|---|---|
| **HDMI-CEC** (*TV & display options → Device control → HDMI-CEC*) | No | Microsoft lists only One X, Series S and Series X; some third-party guides show it on "One series" **(unverified for S)** | Yes | **No.** The AVR-3806 has no CEC (per its manual), and the Vizio almost certainly lacks it too (unverified). |
| **IR blaster** (Kinect on the original; built-in front blaster on S/X; IR Out port on all for an IR extension cable) | via Kinect or IR Out cable | Yes | Yes | **Yes, this is the answer.** |

Setup:

1. **Settings → General → TV & display options → Device control** (older UI: *TV & OneGuide → Device control*).
2. **TV** → choose Vizio → test the power code.
3. **Audio receiver** → choose Denon → test power and volume.
4. **Power** → *Device power options* → **TV / Audio receiver: On when Xbox turns on, Off when Xbox turns off**.

The Denon's remote has separate **ON** and **OFF** buttons (discrete codes), so the Xbox can switch it on without toggling it off by mistake. The blaster needs line of sight or a bounce to the Denon's and Vizio's IR windows. If the console is in a cabinet, plug an **IR emitter cable** into the IR Out port. Controller and media-remote volume keys can then send IR volume to the Denon.

**Power modes** (renamed 2023): **Sleep** (instant-on, about 10–15 W, gets updates, allows remote wake) vs **Shutdown (energy saving)** (about 0.5 W, boots in about 15 s; default since the 2023 change). Either works with IR power-on of the TV/AVR.

---

## 8. Streaming apps on Xbox One (2026)

| App | Available | Best audio on Xbox | Notes |
|---|---|---|---|
| Netflix | Yes | DD+ 5.1; Atmos on the Premium plan | Dolby Vision on S/X (added 2018) |
| Disney+ / Hulu | Yes | DD+ 5.1 (Atmos on some titles/devices, **unverified on One**) | |
| HBO Max | Yes | DD+ 5.1 (Atmos titles exist) | |
| Prime Video | Yes | DD+ 5.1 / Atmos (passthrough reports) | |
| Apple TV app | Yes | DD+ 5.1 / Atmos (**One support unverified**) | |
| Paramount+, Peacock, Crunchyroll, Tubi, Pluto, Twitch | Yes | Mostly stereo to 5.1, varies by title | |
| YouTube | Yes | **Stereo** | Needs the 7CH STEREO press |
| Plex, VLC, Kodi | Yes | Anything (local files); passthrough varies by app | Good for home media |
| Spotify, Apple Music, Amazon Music, Pandora, SoundCloud | Yes | Stereo | |
| **Qobuz** | **No Xbox app** | — | Keep using the PC for Qobuz |
| Movies & TV | Playback only | Up to TrueHD/DTS-HD from local files | Store closed July 2025 |

---

## 9. Tips, hidden settings, troubleshooting

- **Blank screen / wrong resolution reset:** with the console **off**, hold **Xbox (power) + Eject** for about 10–20 s until the **second** beep. It boots at **640×480**, and then you can set 1080p again. On the All-Digital model, use **Xbox + Pair**.
- **Full power cycle** (fixes most HDMI or audio glitches): hold the power button 10 s, unplug for 30 s, then turn on in the order TV → Denon → Xbox.
- **No sound after picking Atmos or DTS:X:** the 3806 can't decode them. Go back to Dolby Digital or PCM.
- **Dropouts on 7.1 uncompressed:** likely the 3806 firmware limit. Use 5.1.
- **Get to audio settings quickly:** Xbox button → Profile & system → Settings → General → Volume & audio output. You can pin *Settings* to Home.
- **Night listening:** the Denon's D.COMP works only on DD/DTS input, not on PCM.
- **Lip sync:** set the Denon's per-input Audio Delay (0–200 ms).
- **Ethernet** beats Wi-Fi for 4K/HDR streams (less relevant at 1080p).
- **Check what the Denon is receiving:** press **STATUS** or **ON SCREEN** on the Denon for the signal type (PCM / DOLBY DIGITAL / MULTI CH).
- **Slow dashboard on the HDD models:** an external USB 3.0 SSD for games helps load times. The internal drive swap is fiddly.

---

## 10. How it fits this system

- **Keep the Xbox One** as the game console and for streaming. It's still supported, and the 1080p Vizio makes S/X-only features (4K, HDR) irrelevant, so **any** variant is fine here.
- **Connect it by HDMI to the Denon, set 5.1 uncompressed, and use the Denon's 7CH STEREO button for stereo content** (Solution A). If you want PLIIx for stereo with one-button switching and don't mind lossy DD for surround, use Solution B.
- **Power:** set up the Xbox's IR blaster to switch the Vizio and the Denon on and off. CEC can't work with this TV and AVR. The PC (OptiPlex) can't do this over HDMI either, so the Xbox can be the "master" power device when it's in use.
- **Sound-reactive light (planned):** the Xbox has no API for that. A light that listens through a microphone, or one that takes a line-level feed from the Denon's pre-outs / Zone 2, works with any source, including the PC and Qobuz.
- **Bose Acoustimass:** with 5.1 PCM, set the Denon's speaker config and bass management (subwoofer, crossover) so the AVR does all the processing. See the Bose page.
- **Future:** before buying a Series X|S *for audio*, note that it doesn't solve this problem. A $110–200 streamer (Shield) or a newer AVR does.

---

## Sources

- Nakamichi USA Helpdesk: Xbox One S audio settings (bitstream can't upmix 2.0): https://www.helpdesk.nakamichi-usa.com/xbox-one-s-audio
- Nakamichi: Xbox One / One X audio: https://www.helpdesk.nakamichi-usa.com/xbox-one-audio , https://www.helpdesk.nakamichi-usa.com/xbox-one-x-audio
- AVForums: Xbox One S + Denon, silent center with 5.1/bitstream, fix = stereo: https://www.avforums.com/threads/ok-this-is-a-tricky-one-looking-for-anyone-who-can-help-with-center-channel-issues-w-xbox-denon-google-has-been-no-help-appreciate-help.2335426/
- AVForums: "Finally true audio passthrough on Xbox!" (May 2021 passthrough update): https://www.avforums.com/threads/finally-true-audio-passthrough-on-xbox.2357268/
- AVS Forum: Xbox optional passthrough bitstreaming: https://www.avsforum.com/threads/xbox-one-and-series-x-s-consoles-now-have-optional-passthrough-audio-bitstreaming.3199044/
- Xbox Support: speaker audio settings: https://support.xbox.com/en-US/help/hardware-network/display-sound/choosing-speaker-audio-output
- Xbox Support: audio passthrough: https://support.xbox.com/en-US/help/hardware-network/display-sound/audio-passthrough
- Xbox Support: HDMI-CEC (One X, Series X|S): https://support.xbox.com/en-US/help/hardware-network/display-sound/hdmi-cec
- Xbox Support: power modes: https://support.xbox.com/en-GB/help/hardware-network/power/learn-about-power-modes
- Xbox Support: IR extension cables: https://support.xbox.com/en-CA/help/hardware-network/oneguide-live-tv/use-external-ir-with-xbox-one
- Pureinfotech: Xbox auto power on TV/receiver via IR: https://pureinfotech.com/setup-xbox-one-automatically-turn-on-tv-audio-receiver/
- Pureinfotech: energy-saving default change (2023): https://pureinfotech.com/xbox-series-x-s-one-switch-energy-saving-power-mode-update/
- MakeUseOf: Shutdown vs Sleep watts: https://www.makeuseof.com/xbox-shutdown-vs-sleep-mode/
- waded/xbox-cec (Xbox One lacks CEC; IR→CEC bridge): https://github.com/waded/xbox-cec
- ResetEra: HDMI-CEC on Xbox: https://www.resetera.com/threads/hdmi-cec-finally-on-the-xbox-platform.322045/
- ResetEra: Xbox One Atmos upmixing (games): https://www.resetera.com/threads/xbox-one-getting-atmos-upmixing.101884/
- Windows Central: Blu-ray bitstream passthrough: https://www.windowscentral.com/bitstream-passthrough-available-xbox-insiders
- What Hi-Fi: Xbox One bitstream audio update: https://www.whathifi.com/news/xbox-one-gets-welcome-bitstream-audio-update
- What Hi-Fi: no 4K passthrough on HDMI in: https://www.whathifi.com/news/no-xbox-one-s-doesnt-support-4k-pass-through
- High-Def Digest: Dolby Vision streaming on One S/X (2018): https://www.highdefdigest.com/news/show/Microsoft/Xbox_One/Dolby_Vision/updates/Netflix/hdr/microsoft-launches-dolby-vision-streaming-support-on-xbox-one-s-xbox-one-x/42431
- Wikipedia: Xbox One (specs, dates): https://en.wikipedia.org/wiki/Xbox_One
- Wikipedia: Xbox One / Series app list: https://en.wikipedia.org/wiki/List_of_Xbox_One_and_Series_X/S_applications
- Screen Rant: Xbox One generation winding down (Mar 2026): https://screenrant.com/xbox-one-console-winding-down-support/
- Pure Xbox: Is it worth buying an Xbox One in 2026: https://www.purexbox.com/features/is-it-worth-buying-an-xbox-one-in-2026
- Windows Central: Social Clubs removed April 2026: https://www.windowscentral.com/gaming/xbox/xbox-is-quietly-shutting-down-a-pretty-major-console-feature-heres-when-its-going-away
- Tom's Guide: console power consumption: https://www.tomsguide.com/us/xbox-one-ps4-power-consumption,news-18882.html
- Stevivor: reset Xbox One display settings: https://stevivor.com/guides/reset-xbox-ones-display-settings/
- **Denon AVR-3806 Owner's Manual** (HDMI 1.1, no CEC, mode/input table, Auto Surround Mode, 7CH STEREO, Audio Delay): https://www.denon.com/on/demandware.static/-/Library-Sites-denon_apac_shared/default/dwd8318111/downloads/archived/avr-3806-owners-manual-en.pdf
- Audioholics: 3806 multichannel PCM from PS3: https://forums.audioholics.com/forums/threads/question-about-lpcm-and-dolby-truehd.35499/
- AVForums: 3806 firmware (7.1 PCM 24/96 over HDMI): https://www.avforums.com/threads/new-3806-firmware.467328/
- HiFiVision: 3806 firmware via RS-232: https://www.hifivision.com/threads/denon-3806-firmware-upgrade.18246/
- AVS Forum: Denon AVR-3806 (1080p HDMI): https://www.avsforum.com/threads/denon-avr-3806.3336018/
- Vizio VS420LF1A service manual (3× HDMI, SPDIF out): https://archive.org/stream/Vizio_VS420LF1A/Vizio_VS420LF1A_djvu.txt
- Nvidia: Shield AVR / surround setup (Manual → AC3 only for legacy AVRs): https://www.nvidia.com/en-gb/shield/support/shield-tv-pro/avr-surround-audio-setup
- Apple Support: Apple TV 4K audio formats: https://support.apple.com/en-us/102218
- Apple Community: Apple TV multichannel PCM issues: https://discussions.apple.com/thread/255839500
- AVForums: Xbox HDMI and optical outputs work at the same time: https://www.avforums.com/threads/xbox-one-audio-input-output.1995810/
- Qobuz apps list (no Xbox): https://help.qobuz.com/en/articles/10153-qobuz-apps
- Pure Xbox: Series X|S prices Aug 2026: https://www.purexbox.com/news/2026/08/heres-a-breakdown-of-the-new-prices-for-xbox-series-xs-consoles-as-of-august-2026
- 9to5Mac: Apple TV 4K price rise / new model 2026: https://9to5mac.com/2026/08/13/new-apple-tv-4k-2026-release-date-features-price/
- 9to5Toys: Fire TV Cube pricing (Sep 2026): https://9to5toys.com/2026/09/18/amazon-fire-tv-cube-3/
- BGR: Nvidia Shield TV Pro in 2026: https://www.bgr.com/2260284/is-nvidia-shield-worth-buying-2026/
