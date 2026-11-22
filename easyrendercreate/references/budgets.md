# Budgets and per-agent adjustments

Use this file in the machine round and when filling TARGET and VERIFICATION.

## Scene and game: device class

| Class | Examples | Max resolution | Average GPU time per frame | Worst frame |
|---|---|---|---|---|
| Strong PC | RTX 4070 or better, RX 7800 XT or better | 2560×1440 | ≤ 11 ms | ≤ 16.7 ms |
| Mid-range PC | RTX 3060 or 4060, RX 6600 or 7600, Arc A750 | 1920×1080 | ≤ 11 ms | ≤ 16.7 ms |
| Mac Pro or Max | Apple M2, M3 or M4 Pro, Max or Ultra | 2560×1600 | ≤ 11 ms | ≤ 16.7 ms |
| Base Mac | Apple M1 to M4 with no suffix | 1920×1200 | ≤ 16.7 ms | ≤ 25 ms |
| Laptop without a dedicated card | Intel Iris Xe or integrated Arc, Radeon 780M | 1920×1080, with dynamic internal resolution | ≤ 16.7 ms | ≤ 33 ms |
| Phone | a flagship from the last two years | 1280×720 internal, with dynamic scaling | ≤ 33 ms | ≤ 50 ms |

- **Resolution**: use the lower of the class's max resolution and the person's monitor (Full HD = 1920×1080, 2K = 2560×1440, 4K = 3840×2160). An RTX 4070 on a Full HD monitor stays at 1920×1080.
- Card the person doesn't know: use Mid-range PC and write `a mid-range desktop GPU such as an RTX 4060`. Monitor they don't know: Full HD, 60 Hz.
- Card not listed: match it by the closest generation and price range. When in doubt, go one class down.
- Reflex game: the worst frame matters more than the average, because a hitch becomes a player mistake. Recommend smoothness first in the priorities.

### Monitors at 120 Hz or more

On a Strong PC or a Mac Pro or Max, ask in half a line whether the person wants to use the whole refresh rate, warning that it takes budget away from the visuals. If yes: average ≤ 1000 ÷ rate ms and worst frame ≤ 2 × (1000 ÷ rate) ms. At 144 Hz that is 6.9 ms and 13.9 ms. For other classes, or if they say no, use the table.

### TARGET lines

- Line 1: only what the person told you, separated by commas (OS, browser, GPU, CPU, monitor with its refresh rate). Leave out whatever they don't know.
- Line 2: `{W×H} at native resolution. Average GPU frame time ≤ {avg} ms and no single frame above {worst} ms over a scripted 60 s fly-through.` On laptops and phones, replace `at native resolution` with `output, with dynamic internal resolution`.
- Line 3, only for laptops, phones or when the person asked for phone support: `Hold the frame rate here and on weaker devices by lowering internal resolution first, then draw distance, in small steps.`

## Video

### Output by destination

| Destination | Resolution | fps | File |
|---|---|---|---|
| Full screen or YouTube | 3840×2160 on a strong machine; 1920×1080 otherwise | 60 for fast motion, 30 for contemplative | MP4, high-bitrate H.264, AAC audio |
| Reels, TikTok or Shorts | 1080×1920 | 30 (60 for fast motion) | MP4, H.264, AAC audio |
| Square feed | 1080×1080 | 30 | MP4, H.264, AAC audio |
| Looping background for a website or big screen | 1920×1080 | 30 | MP4 H.264 and WebM VP9, no audio, seamless loop |

### Render time and quality

- Default: the full export finishes within 30 min on the reference machine. For 2 or 3 min at 60 fps, allow up to 60 min or suggest 30 fps.
- Frames = duration × fps (30 s at 30 fps is 900 frames).
- Default quality: 2×2 supersampling. If the camera flies through things or turns fast, add motion blur with 8 samples per frame.
- Live preview: average ≤ 33 ms per frame at half the final resolution in both dimensions (1080×1920 becomes 540×960).

### Export

- Default for agents that run on the person's machine: a capture script next to index.html records the frames from the browser and encodes them with ffmpeg. Sound, if any, is rendered with an OfflineAudioContext, saved as WAV and muxed by ffmpeg. CONSTRAINTS line: `export with a capture script next to index.html that encodes the frames and the offline-rendered audio with ffmpeg`.
- If the person wants the HTML itself to produce the file, with nothing installed: `export inside index.html with WebCodecs and a small inline muxer`. It's more work for the agent; say so.

## Critic and capture by agent

In the `Visual critic` item of VERIFICATION, the template says `a separate subagent` and `rendered … in GPU-accelerated {browser}`. Adjust them like this:

| Agent | Critic | How to capture |
|---|---|---|
| Claude Code | `a separate subagent` | `GPU-accelerated Chrome driven by Playwright or Chrome DevTools MCP` |
| Codex | `a separate subagent (or a fresh session)` | `GPU-accelerated Chrome driven by Playwright` |
| Antigravity | `a separate agent` | `the browser agent, which also records the video` |
| Cursor | `a fresh agent session` | `GPU-accelerated Chrome driven by Playwright` |
| Other | `a separate subagent or fresh session` | `GPU-accelerated {browser} driven by your browser automation` |

If the chosen agent's critic can't watch video, add: `If it can't watch video, give it a contact sheet with a frame every 0.5 s instead.`

In every case, end the critic item with `Make sure the captures come from real GPU rendering, not a software fallback.` Headless browsers often fall back to a software renderer, which makes everything slow and different from what the person will see.
