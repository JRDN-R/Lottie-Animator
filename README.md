# Lottie Animator

A self-contained, browser-based animation studio for turning PNG, JPG, and WebP artwork into **Lottie** animations. Transparent pixels in uploaded PNGs are preserved.

## Use it

Open `index.html` in your browser, or enable GitHub Pages for **main / (root)** in **Settings → Pages** to publish the same page on the web. No build step, server, account, or external JavaScript dependency is needed.

1. Upload an image (or use the demo artwork).
2. Pick an animation preset: **speed-ramp spin**, **continuous spin**, float, pulse, sway, bounce, slide, fade, or pop.
3. Adjust the start hold, animation duration, end hold, acceleration/deceleration, turns/direction, FPS, canvas dimensions, and image fit. Continuous spin runs with zero holds at a constant speed.
4. Adjust the rotation **pivot X/Y** in percentages (50/50 = center), or use **Pick on preview** to select it directly on the image.
5. Press **Play** to preview or scrub the timeline. The phase bar shows the stationary and moving portions of each cycle.
6. Choose **Lottie JSON (.json)** or **dotLottie package (.lottie)**, then select **Export Lottie**.

### Default spin timing

- **0.0–2.0 s:** stationary at its initial orientation.
- **2.0–3.4 s:** three full clockwise rotations. The first 30% accelerates from rest, the middle 40% spins at constant speed, and the final 30% decelerates to rest.
- **3.4–4.4 s:** stationary at the original visible orientation.

All timings and easing proportions are adjustable, as is the turn count (1–8), direction, and rotation anchor. Initial and final holds are explicitly keyframed in the Lottie export. The **continuous spin** mode uses linear speed and no extra loop frame, and forces looping on. For other modes, the loop checkbox controls preview looping and is saved to the dotLottie manifest.

## File formats

- **Lottie JSON** embeds a PNG data URL within a standard Lottie image layer with keyframed transforms, real stationary holds, easing curves, and a customizable image anchor. It is a complete single file and has a transparent composition.
- **dotLottie (.lottie)** is a Deflate-compressed ZIP containing `manifest.json` and `animations/main.json`. The embedded PNG is included within the animation JSON, so there are no external image dependencies. Uses the broadly compatible dotLottie **v1** manifest.
- Uploaded files stay in the browser; image conversion, preview, and export happen on-device. Large images are downscaled to at most **1600 px** on their longest side to keep exported files reasonable. Upload limit: **25 MB**.

**Important:** This tool animates a raster PNG image in Lottie. It does *not* trace or convert pixels into vector paths. A consuming Lottie player determines looping for bare JSON files. Actual dotLottie package export requires a browser supporting `CompressionStream('deflate-raw')` (current Chrome, Safari, Edge, and Firefox).

## Repository

- `index.html` — full app, including HTML, CSS, preview renderer, keyframe editor, image handling, and exports.
- No build dependencies or third-party scripts.

