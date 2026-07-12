# Caption Wala — Complete User Guide

Caption Wala creates YouTube-ready captions (SRT files) for any video or audio, free, in your web browser. It is built for long-form podcast content in **English and Hinglish** (Hindi spoken, written in Roman script), but works for any episode length or content type.

**The app:** https://kartikey-cloud.github.io/caption-wala/

There is nothing to install for normal use. Everything below works the same on **Mac and Windows** — the app runs in your browser, so the operating system barely matters. The few places where Mac and Windows differ are marked with 🍎 / 🪟. (The one exception is optional **Server mode**, which has its own OS-specific setup — see section 8.)

---

## 1. What you need

| Requirement | Details |
|---|---|
| A browser | **Chrome or Edge strongly recommended** (they support WebGPU, which makes transcription 5–10× faster). Brave also works. Firefox and Safari work but fall back to slower CPU processing. |
| Internet | Only for loading the page and downloading the speech model **once** (40 MB – 1 GB depending on the model you pick). After that, transcription itself is fully offline. |
| Your video/audio | Any common format: mp4, mov, mkv, webm, m4a, mp3, wav, and more. |
| Hardware | Any reasonably modern computer. A dedicated or Apple-silicon GPU makes things much faster but is not required. |

**Privacy, in one line:** in the default "This browser" mode, your video is never uploaded anywhere — audio is decoded and transcribed on your own machine.

🍎 **Mac:** Chrome and Edge both have WebGPU. Safari's support is limited — if the page says "no WebGPU", switch browsers.
🪟 **Windows:** Chrome and Edge both have WebGPU out of the box. Nothing extra to install.

---

## 2. Quick start (2 minutes)

1. Open **https://kartikey-cloud.github.io/caption-wala/** in Chrome or Edge.
2. Leave the settings on their defaults (**Hinglish**, **This browser**, **Base** model) for a first run.
3. Drag your video onto the big drop zone (or click it to browse).
4. Wait. The first run downloads the model (~80 MB), then transcription starts and you'll see a live transcript streaming in with a progress bar and ETA.
5. When it finishes you land in the **editor**: video on the left, every caption on the right.
6. Fix anything that needs fixing (see section 6).
7. Click **⬇ SRT for YouTube**. The .srt file downloads to your Downloads folder.
8. Upload it to YouTube (section 9). Done.

---

## 3. Choosing a language mode

Pick this **before** dropping your file.

| Mode | What you get | Use when |
|---|---|---|
| **Hinglish** (default) | Hindi words in Roman script: "paisa kamana hai, right?" | Mixed Hindi-English podcasts — the standard style for Hinglish YouTube captions |
| **English** | Standard English captions | Fully English audio |
| **हिन्दी** | Hindi in Devanagari: "पैसा कमाना है" | You specifically want Devanagari output |

Hinglish mode works by telling Whisper to treat the audio as English, which makes it write Hindi words phonetically in Roman letters — the way people actually type Hinglish.

---

## 4. Choosing a model

Bigger models are more accurate but slower to download and run. All of them are downloaded once and cached by your browser.

| Model | Download | Speed / accuracy | Best for |
|---|---|---|---|
| **Tiny** | ~40 MB | Fastest, rough | Quick previews only |
| **Base** | ~80 MB | Fast, decent | First run; clear English |
| **Small** | ~250 MB | Medium, good | **Everyday Hinglish choice** |
| **Turbo** | ~1 GB | Slow, best; needs good GPU | Final captions; tough audio |

**Where does the model download go?** Into your browser's internal cache for the Caption Wala site — not to your Downloads folder, which is why you're never asked to pick a location. It is **kept after the task finishes** (deliberately, so your next transcription starts instantly instead of re-downloading), and it stays until you clear it yourself: browser settings → Privacy → Clear browsing data → "Cached images and files", or the per-site data option for `kartikey-cloud.github.io`. Each model is stored once, so switching between Base and Small keeps both cached (~330 MB total, plus ~1 GB if you've used Turbo).

Rules of thumb:

- Clear English audio → Base is usually enough.
- Hinglish → use **Small** or **Turbo**; smaller models miss more Hindi words.
- A 40-minute episode takes roughly 5–15 minutes on Base with WebGPU; Turbo takes longer but produces noticeably cleaner Hinglish.
- No WebGPU (Safari/Firefox) → everything is several times slower; stick to Tiny/Base or use Chrome.

---

## 5. Transcribing

**Uploading:** drag and drop onto the zone, or click it and pick a file.

**A tip for very long episodes:** the browser has to decode your file's audio track in memory. A 2 GB video works in Chrome, but an **audio export of the same episode (m4a or mp3) decodes faster and more reliably**. Timestamps are identical, so the SRT you produce still matches the video perfectly. Most editors (Premiere, Final Cut, DaVinci, Descript) can export audio-only in seconds.

**During transcription** you'll see: a progress bar with percentage and ETA, elapsed time, how much audio has been processed, and a live rolling transcript so you can sanity-check quality early. If the first minute looks bad, hit **← New video**, pick a bigger model, and restart.

Keep the tab open while it works (background tabs are fine, closed tabs are not).

**Resume:** finished captions are saved in your browser automatically. If you drop **the exact same file** again later, Caption Wala offers to reopen your saved captions instead of re-transcribing.

---

## 6. The editor

The editor shows your video (left) and every caption block (right), fully synced.

**Navigation**

- The caption currently being spoken is **highlighted** and the list auto-scrolls to follow playback (toggle with **📍 Follow**).
- **Click any caption card** to jump the video to that exact moment.
- Click a **timestamp** to jump there. ▶ on a card plays that caption.
- Playback speed: click the **1×** label to cycle 1× → 1.25× → 1.5× → 2× → 0.75×.
- Keyboard: **Space** = play/pause, **← / →** = skip 5 s, **Esc** = leave a text box.

**Editing**

- Click **✎** on a card (or click its text directly) to edit. The card glows amber while editing; the video pauses.
- **Timing:** edit the timestamps directly (format `m:ss.mmm`), or use the **− / +** buttons to nudge start/end by 0.2 s.
- **✂ Split:** place your cursor where the caption should break, click ✂.
- **⤵ Merge:** joins a caption with the one below it.
- **🗑 Delete:** removes a caption (use for stray "um"/noise captions).
- **Find & replace** (top of the list): the fastest way to fix a name or Hindi word Whisper got wrong 30 times. Type the wrong version, the right version, click **Replace all**.
- A small amber **warning** appears under any caption that breaks YouTube rules: line longer than 42 characters, more than 2 lines, on screen longer than 7 s, or end-before-start.

**Saving:** every edit autosaves to your browser within a second ("Saved on this device ✓"). Saves survive closing the tab and restarting the computer. They are per-browser, per-computer — captions edited in Chrome on your Mac won't appear in Edge on a PC.

---

## 7. Exporting

| Button | File | What it's for |
|---|---|---|
| **⬇ SRT for YouTube** | `yourvideo.srt` | The main output — upload to YouTube |
| **VTT** | `yourvideo.vtt` | Web players, some other platforms |
| **Transcript** | `yourvideo_transcript.txt` | Clean paragraph transcript (show notes, blog) |
| **YT chapters + tags** | `yourvideo_youtube_details.txt` | Auto-generated chapter list for your description + suggested tags |

Files go to your browser's normal download location (usually **Downloads** on both Mac and Windows).

---

## 8. Server mode (optional, advanced)

Browser mode maxes out at the Turbo model. If you want captions from the **full-size Whisper models (medium / large-v3)** — the most accurate option for heavy Hinglish — you can run the companion **Caption Studio** server on a computer you own and point the web page at it. Videos then upload to **that computer only** (not to any cloud).

You need the two Caption Studio files (`caption_studio.py`, `caption_studio.html`) on the machine that will do the work.

### 🍎 Mac setup

```bash
# one time
brew install ffmpeg
pip3 install flask faster-whisper

# every session
cd ~/Documents/Claude/Projects/Podcast     # wherever the files live
python3 caption_studio.py
```

### 🪟 Windows setup

```powershell
# one time — install Python from python.org (tick "Add python.exe to PATH"), then:
winget install ffmpeg
pip install flask faster-whisper

# every session
cd C:\path\to\caption-studio-files
python caption_studio.py
```

(If `winget` isn't available, download ffmpeg from gyan.dev/ffmpeg, unzip, and add its `bin` folder to PATH.)

### Sharing the server beyond your own machine

On the same computer, you can just use http://localhost:5055 directly — that's the full Caption Studio app with the same editor.

To let the **hosted Caption Wala page** (or a friend elsewhere) use your machine, expose it with a tunnel:

```bash
# Mac
brew install cloudflared
cloudflared tunnel --url http://localhost:5055
```

```powershell
# Windows
winget install Cloudflare.cloudflared
cloudflared tunnel --url http://localhost:5055
```

cloudflared prints a URL like `https://something-random.trycloudflare.com`. On the Caption Wala page choose **Engine → Caption Studio server**, paste that URL, then upload as usual. The tunnel lives only while cloudflared is running; anyone with the URL can send videos to your machine while it's up, so share it carefully and Ctrl+C when done.

### Browser vs Server at a glance

| | This browser | Caption Studio server |
|---|---|---|
| Setup | None | Python + ffmpeg on one machine |
| Where video goes | Nowhere (stays on device) | To your server machine only |
| Models | tiny → turbo | small → **large-v3** |
| Hinglish accuracy | Good (Turbo) | Best (large-v3) |
| Cost | Free | Free (your hardware) |

---

## 9. Uploading captions to YouTube

1. Go to **YouTube Studio** → **Content** → click your video.
2. In the left sidebar choose **Subtitles**.
3. On the language row (add **English** if it isn't there — use English for Hinglish captions too), click **ADD** / the caption box.
4. Choose **Upload file** → **With timing** → select your `.srt` file → **Continue**.
5. Preview, then **Publish**.

For chapters: open `yourvideo_youtube_details.txt`, copy the chapter list (starting with `0:00`) into the top of your video description, and adjust the auto-generated titles to taste. YouTube needs at least 3 chapters, starting at 0:00, each 10+ seconds.

---

## 10. Troubleshooting

| Problem | Fix |
|---|---|
| "Could not decode audio from this file" | Export the episode as m4a/mp3 and drop that instead; or try Chrome; or use Server mode. |
| Transcription very slow | Check the settings card said "⚡ WebGPU detected". If not, switch to Chrome/Edge. Otherwise pick a smaller model. |
| Model download stuck | Check internet, reload the page (Cmd+Shift+R on Mac, Ctrl+Shift+R / Ctrl+F5 on Windows), try again — downloads resume from the browser cache. |
| Hinglish words wrong | Use Small or Turbo, then fix recurring mistakes with Find & replace. Server mode with large-v3 is the ceiling. |
| Tab crashed on a huge video | Use an audio export (m4a/mp3) — much lighter on memory. |
| Page looks outdated / a fix isn't there | Hard refresh: 🍎 Cmd+Shift+R · 🪟 Ctrl+Shift+R. |
| Saved captions disappeared | They're stored per-browser. Clearing site data deletes them — export your SRT as soon as editing is done. |
| "Could not reach the server" (Server mode) | Is `caption_studio.py` running? Is the tunnel URL current? cloudflared prints a new URL each launch. |
| Video preview missing after reopening saved captions | Click the dashed box and re-select the original file — captions are kept, video preview just needs the file again. |

---

## 11. FAQ

**Is it really free?** Yes. No account, no quota, no watermark. Browser mode uses your own computer's processing power.

**Is my content private?** In browser mode, yes — the file never leaves your machine; only the speech model is downloaded. In server mode, the video goes to the specific machine you point it at (yours), not to any third-party cloud.

**Does it work offline?** After the model has been downloaded once and the page has loaded, transcription itself runs offline.

**Where is the model stored, and is it deleted afterwards?** It's saved in your browser's cache storage for this site (inside the browser's own data folder — 🍎 `~/Library/Application Support/Google/Chrome/…` · 🪟 `%LocalAppData%\Google\Chrome\…` — never your Documents or Downloads). You aren't asked for a location because it isn't a normal file download. It is **not** auto-deleted when a task finishes — it's cached so future runs skip the download. To reclaim the space: browser settings → Clear browsing data → "Cached images and files" (or delete site data just for `kartikey-cloud.github.io`). Your edited captions are stored separately (localStorage), so clearing *cache only* keeps them; clearing *all site data* removes both.

**How long can my video be?** Tested with 40+ minute podcasts. For 1 hr+ files, use an audio export for the smoothest experience.

**Can two people use it at once?** Yes — it's a static page; every visitor's transcription runs on their own machine independently.

**Mac vs Windows — anything different?** For normal use, no: same page, same buttons, same output. Only three things differ: the hard-refresh shortcut (Cmd vs Ctrl+Shift+R), where Downloads live, and the optional Server-mode install commands (section 8).

**Phone/tablet?** It loads, but decoding and transcribing long videos needs desktop-class memory. Use a computer for full episodes.

**What powers it?** OpenAI's Whisper speech model, running in the browser via [transformers.js](https://github.com/huggingface/transformers.js) (ONNX + WebGPU), with caption formatting that follows YouTube best practice: ≤42 characters per line, ≤2 lines per caption, ≤6 seconds on screen, breaks at pauses and sentence ends.
