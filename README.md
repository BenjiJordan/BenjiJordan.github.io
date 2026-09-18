# Keyguard Generator — deployable prototype

A static, client-side AAC keyguard generator. No backend, database, Fusion installation, or image-upload service is required.

## Run locally
JavaScript modules need HTTP serving. From this folder run:

    python -m http.server 8000

Then visit `http://localhost:8000`.

## Deploy
Upload this folder unchanged to any static web host such as GitHub Pages, Cloudflare Pages, or Netlify.

- Build command: none
- Runtime/server: none
- Publish directory: this folder / repository root

## Automatic cell recognition
The detector is intentionally conservative and local. It converts the vocabulary image to grayscale, measures horizontal/vertical edge energy, finds likely grid boundaries, and proposes rectangles between them. Clear screenshots with strong rectangular cell borders work best.

It is not computer-vision AI and should not be treated as infallible. The UI tells the user to review the detected openings. Detected openings can be selected, merged, or disabled before STL export.

## Privacy
Vocabulary images are read by browser APIs and processed in JavaScript on the user's device. This prototype contains no upload endpoint and no analytics.

## Architecture
- `js/geometry.js` — device/vocabulary presets and opening merge operations
- `js/detect.js` — local image-based rectangular cell detection
- `js/stl-export.js` — local STL generation
- `js/app.js` — UI/editor orchestration
- `css/app.css` — responsive UI
