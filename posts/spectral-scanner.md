---
title: Building a spectral archival scanner for decaying film
author: Matthieu
date: 2024-03
lede: Why commercial scanners fail on vinegar syndrome film, and how to build something that doesn't — for about EUR 7,000 and a lot of weekends.
---

When cellulose acetate film decomposes, it releases acetic acid. You can smell it before you open the can — that faint vinegar note that means you're already too late to prevent damage. The question is whether you can still save what's left. Most commercial scanners aren't built for this. They assume film that still has its original geometry, its original dye density, its perforations intact. Film with vinegar syndrome has none of those things.

This is a writeup of what I built to handle it.

## Why standard scanners fail on damaged film

### Vinegar syndrome: what actually happens

Cellulose acetate, used from the 1930s through most of the 1990s, undergoes deacetylation as it ages. The acetate base breaks down, releasing acetic acid, which accelerates further breakdown. It's autocatalytic — bad film stored next to good film will accelerate the good film's decay too. The reaction also causes the base to **shrink**, typically by 1–3% but sometimes up to 5% linearly.

A standard 35mm Full Aperture frame is 18.7mm tall (across the film strip) and 24.9mm wide (along the film). At 5% linear shrinkage, the vertical height drops to 17.8mm — a reduction of about 0.9mm. That sounds trivial. It isn't, because sprocket teeth are machined to assume 4.75mm perforation pitch. Run shrunken film through a sprocket drive and the teeth sit slightly off-center in each hole. The film is brittle. The sprocket turns. Something tears.

> **Brittleness note:** Even without active tearing, the plasticizers in deteriorated film have migrated out, leaving the base prone to edge cracking when bent around tight capstans or through any mechanism that concentrates stress. Film that looks fine can develop cracks propagating across the image area from a single rough transport event.

### Color fading: a three-dye problem

Color motion picture film has three dye layers — cyan, magenta, yellow — and they don't fade at the same rate. Cyan almost always goes first, often losing 70–90% of its density while the yellow layer is still relatively intact. The result is a pink-orange image that looks ruined but actually contains recoverable information — if you have the right tools to read it.

<!-- widget: dye-fading -->

An RGB scanner has no way to distinguish "faded cyan dye" from "no image data." Both look like low density in the blue-green channel. You'd need to probe the film at multiple wavelengths to see the shape of what remains. That's what this scanner does.

## Optics: sensors, lenses, and why not a DSLR

### The Bayer filter problem

Consumer cameras use a Bayer filter array — a mosaic of red, green, and blue filters over the sensor, with each photosite capturing only one color channel. The camera guesses the other two via demosaicing algorithms. This is fine for photography. For spectral work, it's a fundamental obstacle.

If you illuminate the film at 580nm (yellow) to probe the cyan dye, that light hits both green and red photosites, each with their own spectral response curves that aren't sharp cutoffs. You can't cleanly isolate your illumination band. The Bayer filter system is making the same kind of broad-band measurement we're trying to move away from.

The solution is a **monochrome sensor with no color filter array**. Every photosite captures raw luminance. Illuminate at 580nm, and every pixel records exactly what the film transmitted at 580nm. You have clean, unambiguous spectral data to work with.

### Rolling shutter and how we mitigate it

Global shutter sensors capture the entire frame simultaneously — ideal for a scanner, where you want the whole image grabbed at a single instant. Rolling shutter sensors read line by line, top to bottom, which means the top of the frame was technically captured at a slightly different moment than the bottom. With any movement in the gate, that can introduce skew.

We're using the **FLIR Blackfly S BFS-U3-200S6M**, which uses Sony's IMX183 — a 20MP APS-C monochrome sensor with 2.4µm pixels. It's a rolling shutter part. The reason we accept that tradeoff is resolution: 20 megapixels across an APS-C chip translates to roughly 5440×3648 pixels over a 35mm frame, which pushes us into genuine archival territory — around 4000 DPI on the image area. A global shutter sensor with comparable resolution doesn't exist at this budget.

The mitigation is strobe illumination. Rather than leaving the LEDs on continuously, each capture fires the LED for a very short duration — typically 500–1000µs — synchronized to the exposure. Even though the sensor is reading out line by line, if the light only exists for a fraction of a millisecond, the film is effectively frozen for the entire readout sequence. Rolling skew on a stationary, settled film in a well-designed gate is negligible at these strobe durations.

### Enlarger lenses over the telecentric alternative

A telecentric lens would be ideal — they ensure light hits the sensor perpendicular to its surface even at the edges, eliminating vignetting and ensuring consistent magnification. They also cost EUR 3,000–5,000 for suitable coverage. That's most of the build budget on one part.

Enlarger lenses are a reasonable alternative. The Rodenstock Rodagon series and Schneider Componon-S series were designed to project a flat film plane onto flat paper — which is essentially what a scanner does in reverse. High flat-field performance, minimal distortion, and available used for EUR 200–400. The trick is mounting them **reversed**, element-facing-sensor, since they're designed to project away from the glass side.

**Current lens:** Rodenstock Rodagon 50mm f/2.8, operated at f/5.6 for optimal corner sharpness. Covers the 35mm action area with room to spare.

The IMX183 is APS-C format, so it covers the full 35mm image area at roughly 1:1 magnification. This is actually the Rodagon's optimal working range — the lens was designed to project at reduction ratios around 1:1 to 4:1, and running it near 1:1 means you're getting the best of its flat-field and resolution performance.

> **UV channel caveat:** Standard optical glass — including the Rodagon and the IMX183's sensor cover glass — blocks UV below roughly 380nm. The 365nm UV channel therefore requires either a quartz-fused silica lens or UV-passing optics, plus removal of the sensor's standard AR coating or use of a UV-transparent cover glass. In the current build, the UV channel is experimental: we substitute a Hoya U-340 filter on a short-path lens for initial testing, accepting reduced throughput. If UV fluorescence mapping isn't required for a particular batch, this channel is simply skipped.

```
Lens:            Rodenstock Rodagon 50mm f/2.8 (reversed)
Aperture:        f/5.6
Sensor:          FLIR Blackfly S BFS-U3-200S6M
Sensor type:     Sony IMX183, monochrome, rolling shutter (strobe-mitigated)
Resolution:      5440 × 3648 (20 MP effective)
Pixel pitch:     2.4 µm
Format:          APS-C
Magnification:   ~1:1
Coverage:        Full 35mm Full Aperture image area
DPI (approx):    ~4000 DPI on film image area
```

## Mechanical design: moving film without destroying it

### No sprocket teeth

The core constraint of the entire transport design: no sprockets. Not soft ones, not adjustable ones. The perforations on shrunken film are no longer a reliable reference. They've gotten smaller, often cracked at the edges, sometimes partially missing. Any mechanism that engages them as a drive surface risks propagating those cracks across the image area.

Instead: a **capstan drive**. The film is held against a smooth cylinder by a compliant roller. The cylinder's rotation advances the film by friction alone. No mechanical engagement with the perforations whatsoever.

**Capstan drive (chosen):**
- Works at any shrinkage
- No stress at perforations
- Handles partial or missing perfs
- Requires tension feedback loop

**Sprocket drive (rejected):**
- Assumes standard 4.75mm pitch
- Tears shrunken perforations
- Concentrates stress at edges

### Tension management: the dancer arm

A capstan drive doesn't inherently know how much film is on the supply reel or how taut the loop is. Without feedback, it either slacks the film (creating a pile on the floor) or over-tensions it (snapping brittle stock). The solution is a **dancer arm** — a spring-loaded pivoting roller the film wraps around. When the loop slackens, the arm swings out. When the film tightens, it gets pushed back. An optical encoder on the pivot reads position in real time and feeds a proportional control loop that trims capstan speed to maintain constant tension.

**Tension targets:** 20–30g for healthy stock. 10–15g for severely shrunken or brittle film. The dancer arm spring constant and pivot geometry are calibrated so the mid-travel position corresponds to target tension.

### Closed-loop motor

Standard steppers are open-loop — you command a step and assume it happened. If the film jams, the motor keeps trying to step. For this application, that's unacceptable. We use a **closed-loop stepper with integrated encoder** (Teknic ClearPath). The motor knows its shaft position at all times. Unexpected resistance triggers an immediate stop and error signal to the control software. The film survives the jam rather than getting chewed through it.

### The pressure gate

Warped film at the gate creates focus errors and illumination unevenness. The film needs to be flat. A floating design with a small air gap sounds appealing — nothing touching the emulsion — but in practice a 0.2mm gap is enough for moderately warped film to bow out of the focal plane and introduce focus errors that no amount of software correction can fix.

The solution is a **pressure gate**: the film is gently sandwiched between the ANR glass on top and float glass below, with the ANR glass applying just enough pressure to flatten the film into the focal plane. To prevent scratching, a small amount of FilmGuard fluid is applied to the base (non-emulsion) side, acting as a lubricant and providing just enough compliance to avoid micro-abrasion during transport.

<!-- widget: gate-diagram -->

The ANR (anti-Newton ring) glass is specifically textured to prevent the interference fringes that appear when two nearly-flat surfaces almost contact. Standard glass on top would turn every frame into a rainbow bullseye.

### Frame registration without sprockets

Sprocket drives do one thing well: they know exactly where each frame is, because the pitch is mechanically defined. Without them, you need another way to find the frame boundaries. The approach here is **optical perforation detection**. The software analyzes a strip of the captured image at the expected perforation locations and identifies the edge transitions. Even on damaged film where perforations are partially cracked or deformed, the geometry is usually recognizable enough to extract a reliable center position. The frame window is then aligned relative to that detected position in software, rather than relying on the mechanical transport to land the frame precisely.

### Vibration isolation

At 2.4µm pixel pitch, vibration is a real problem. The motor is mounted on its own sub-frame with Sorbothane feet, mechanically isolated from the optical path. The stepper driver runs in SpreadCycle mode rather than StealthChop to reduce high-frequency ringing. And there's a 100ms settle delay programmed after each frame advance before triggering the strobe exposure — long enough for any residual vibration to damp out, at which point the film is essentially stationary for the sub-millisecond strobe duration.

## The spectral light engine

### Seven bands instead of three

Standard RGB illumination uses three broad bands — roughly 100nm wide each, overlapping. For faded film, this means you're capturing a muddy average across the range where the cyan dye used to absorb. You can't tell whether low density in the blue-green range means "faded cyan" or "no image here."

Narrow-band LEDs at specific wavelengths let you see the *shape* of the dye's absorption curve rather than an average. If there's still residual cyan absorption in the 580nm range, we'll capture it as its own channel. We can then reconstruct the original density mathematically based on what the curve looks like, not just how low it got.

<!-- widget: spectral-channels -->

The dye physics here are worth being explicit about, because it's easy to get backwards. Blue light at 450nm is absorbed by yellow dye, not cyan. Cyan dye peaks in red — around 625nm — which is why cyan-faded film scanned under standard red-channel illumination produces barely any signal. The 580nm band is particularly useful for recovery work. Even badly faded cyan dye has a long tail into the yellow-orange range — it doesn't just cut off at its peak. Capturing 580nm as a separate channel gives the reconstruction algorithm a foothold that the 525nm green band alone wouldn't provide.

### Infrared for dust removal

The 850nm channel is where a lot of the practical value lives. At near-infrared wavelengths, the organic dye layers are mostly transparent, but physical damage — dust, scratches, fingerprints — is still opaque. If you capture a frame in IR and compare it to the visible-light capture, the damage lights up as a mask you can use to automatically inpaint defects in the color image.

This is essentially the same approach as Nikon and Minolta's old Digital ICE feature, implemented from scratch. It automates roughly 90% of what would otherwise be manual dust spotting in post.

> **Limitation:** IR dust removal only works on chromogenic (dye-based) color film. Traditional black and white film uses metallic silver, which is opaque to IR just like dust is. The channel becomes useless for silver-based stocks.

### Remote illumination and heat isolation

LEDs placed directly at the gate transfer heat to the film. For chemically unstable stock, elevated temperature speeds up the deacetylation reaction — the thing you're trying to stop is accelerated by your scanning equipment. So the LEDs are physically separated from the gate and light is delivered via a **fused silica (quartz) fiber optic bundle**. This is a critical material choice: liquid light guides and conventional glass fibers block both UV (below ~380nm) and near-IR (above ~800nm), which would defeat two of our seven spectral channels. Fused silica transmits from below 300nm to beyond 2000nm, covering the full range we need. It also provides thermal isolation — the photons get through, the heat doesn't.

The gate end of the fiber bundle feeds an integrating chamber — a machined aluminum box coated with barium sulfate (99% reflectance in visible and near-IR), which outputs spatially uniform illumination through an opal diffuser. Uniformity is better than 1% across the field, which matters because non-uniform illumination would look like density variation in the film.

## Software and processing pipeline

### The capture loop

For each frame: advance film, wait 100ms, confirm dancer arm position is within tolerance, then cycle through all seven wavelength bands in sequence — turn on LED for strobe duration, trigger camera, save raw file, turn off LED, move to next band. Then verify: check file sizes and basic image statistics, flag and retry if anything looks wrong.

All capture writes to an SSD RAID array. Spinning hard drives introduce enough vibration, even on rubber mounts, to cause micro-blur at this resolution. Data moves to archival HDD storage during post-processing when the film is safely put away.

### Registration: a problem RGB scanners pretend doesn't exist

Chromatic aberration means the 450nm image and the 625nm image don't focus at exactly the same plane. They need to be registered to sub-pixel accuracy before any color reconstruction can happen. The software detects feature points in each monochrome band, matches them to a reference (525nm, usually), and computes the per-band affine transform needed for alignment. With a good enlarger lens this is mostly shift and a small amount of scaling, but it's not zero.

### Spectral-to-color reconstruction

Six of the seven monochrome images go into color reconstruction; one does not. The IR channel at 850nm is reserved exclusively for defect masking — it detects dust and scratches, but including it in the color matrix would corrupt the output, since IR carries no meaningful dye information. The transformation from the remaining six bands is a 3×6 matrix — three output channels (RGB or ACES), six input bands, matrix coefficients determined by calibration against a reference target with known spectral reflectances:

```
R_out = M_R1·D_365 + M_R2·D_450 + M_R3·D_525 + M_R4·D_580 + M_R5·D_625 + M_R6·D_660
G_out = M_G1·D_365 + M_G2·D_450 + M_G3·D_525 + M_G4·D_580 + M_G5·D_625 + M_G6·D_660
B_out = M_B1·D_365 + M_B2·D_450 + M_B3·D_525 + M_B4·D_580 + M_B5·D_625 + M_B6·D_660
```

The 850nm IR channel runs in parallel as a defect mask: it detects dust and scratches and generates an inpainting mask applied to the composite color image. It never enters the color math directly.

For faded film, the calibration matrix is adjusted based on measured density loss per dye layer. If cyan is 80% gone, the matrix weights the 580nm and 660nm channels higher to extract whatever signal remains. The result isn't perfect — it can't be, information was genuinely destroyed — but it's considerably better than what an RGB scan produces on the same material.

## What it actually costs

The honest answer is EUR 6,500–7,500, depending on what you already have and how much machining you can do yourself.

<!-- widget: cost-breakdown -->

For context: the **Lasergraphics ScanStation** — the industry standard for sprocketless archival scanning — runs EUR 40,000–50,000. It handles edge-to-edge coverage, full production throughput, and optical audio track capture, which this build does not. If you're a commercial facility scanning significant audio releases or need certified provenance documentation, this build isn't a replacement for that. But it's roughly 6–8× cheaper, trades off soundtrack scanning capability and some throughput, and requires genuine engineering effort to build and commission. For a small archive, an independent lab, or someone with the right background and enough stubbornness, it's viable.

The other cost is time. The mechanical design alone took several CAD iterations before the gate geometry was right. The software pipeline — capture, registration, HDR merge, matrix reconstruction, IR inpainting — is a substantial codebase. Expect 200+ hours before you're scanning anything archival.

**What you're buying:** Sprocketless transport that can handle film shrunken to any degree. Optical perf detection for software frame alignment. Seven spectral channels for faded dye recovery and UV fluorescence mapping. IR dust removal that eliminates most manual spotting. Strobe illumination that mitigates rolling shutter on a 20MP APS-C sensor. Pressure gate that actually constrains warped film to the focal plane. A platform you can modify and repair indefinitely rather than wait on vendor support.

---

*If you're building something similar or have questions about specific design decisions, I'm reachable via the contact page. I'll continue updating this as the build progresses and I find things that don't work as planned.*
