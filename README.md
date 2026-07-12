# Caption Wala 🎙

Free, private, YouTube-ready captions for any video — right in your browser.
Built for long-form podcast content in **English and Hinglish** (Hindi in Roman script).

**Try it:** open the GitHub Pages link for this repo.

## How it works (hybrid design)

**Browser mode (default).** Transcription runs entirely on your device using OpenAI Whisper compiled for the web ([transformers.js](https://github.com/huggingface/transformers.js)), GPU-accelerated via WebGPU where available. **Your video is never uploaded anywhere** — audio is decoded and transcribed locally. The model (~40–250 MB) downloads once and is cached.

**Server mode (optional).** Point the same page at a running [`caption_studio.py`](../caption_studio.py) server (your own machine, exposed via e.g. `cloudflared tunnel --url http://localhost:5055`) to use bigger, more accurate models (medium / large-v3). Videos upload to that machine only.

## Features

- Drag & drop any video/audio; live progress with rolling transcript preview
- Video-synced caption editor: click any caption to jump, highlight follows playback
- Edit text and timestamps, split / merge / delete, ± timing nudges, find & replace
- Warnings when a caption breaks YouTube rules (>42 chars/line, >2 lines, too long on screen)
- Export SRT (YouTube-ready), VTT, plain transcript, auto-chapters + tags
- Captions autosave in your browser (localStorage), keyed to the exact file

## Language modes

- **Hinglish** — Hindi words in Roman script ("paisa kamana hai"), the standard for Hinglish YouTube captions
- **English** — pure English audio
- **हिन्दी** — Devanagari output

## Tips

- Chrome / Edge give the best speed (WebGPU). A 40-min episode ≈ 5–15 min on the Base model.
- For very long episodes, an audio export (m4a/mp3) decodes faster and more reliably than a huge video file — the timestamps are identical, so the SRT works with your video.
- Hinglish accuracy: browser **Small** model is decent; for best results use Server mode with medium/large-v3.

## License

MIT. Whisper models by OpenAI, ONNX conversions by the transformers.js community.
