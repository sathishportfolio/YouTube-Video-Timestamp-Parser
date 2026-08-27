# YouTube Video Timestamp Parser

![Built with Claude Code](https://img.shields.io/badge/Built%20with-Claude%20Code-6366f1?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-38BDF8?style=flat-square&logo=tailwindcss&logoColor=white)
![No build step](https://img.shields.io/badge/No%20build%20step-10B981?style=flat-square)
![Zero dependencies](https://img.shields.io/badge/Zero%20dependencies*-D946EF?style=flat-square)
![License: MIT](https://img.shields.io/badge/License-MIT-EAB308?style=flat-square)

Turn your [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) export into a clean, clickable revision sheet — organized by video, sorted by recency, and ready to jump straight to the moment that matters.

## Why this exists

Long lecture videos and tutorials are painful to revisit. Scrubbing through a 2-hour video to find "that one part about auth" wastes time you don't have.

[YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) solves the *capture* problem — it lets you drop timestamped bookmarks (with notes and reactions) while watching, and export them all as a single JSON/text file.

This tool solves the *revision* problem. It takes that raw export — a wall of escaped JSON, one entry per video — and turns it into:

- 📼 A card per video, with thumbnail and real video title
- 🕒 Clickable timestamps that open the video at the **exact second** you bookmarked
- 📝 Your notes and reactions laid out clearly under each timestamp
- 🕓 Videos sorted by when you last bookmarked them, so recent study sessions float to the top
- 📋 One-click copy of a video's full timestamp list (e.g. to paste into notes, a doc, or a video description)

No installs, no accounts, no server — it's a single self-contained HTML file you can open in any browser. Great for building up a personal (or shared) library of "focused revision points" across a whole playlist or course.

## How it works

1. **Bookmark while watching** — Use the [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) extension to mark the important moments in any video (with an optional note and reaction emoji).
2. **Export your bookmarks** — From the extension, export your bookmarks. This gives you a `.txt`/`.json` file containing every bookmarked video, grouped by video ID, e.g.:
   ```json
   {
     "R76S0tfv36w": "[{\"time\":1602,\"desc\":\"Auth From DB\",\"reaction\":\"🥳\"},{\"time\":3060,\"desc\":\"Authentication Provider\",\"reaction\":\"🥳\"}]",
     "T0boiBk6-hY": "[{\"time\":20,\"desc\":\"Bookmark at 00:20\"}]",
     "lastModifiedByVideoId": "{\"R76S0tfv36w\":1787727577075,\"T0boiBk6-hY\":1787761358087}"
   }
   ```
3. **Open this tool** — Open `YouTube Video Timestamp Parser.html` in any browser (double-click it, no installation needed).
4. **Load your export** — Either:
   - Click **Upload File** and select your exported `.txt`/`.json` file, **or**
   - Paste the raw exported text directly into the textarea and click **Convert All Videos**.
5. **Revise** — You'll get a card per video with its title, thumbnail, and bookmarked timestamps. Click any timestamp to jump straight to that moment on YouTube. Click **Click to copy** on a card to copy that video's full timestamp list to your clipboard.

## Tips for organizing by group

Since the exported file is just plain text/JSON, you can keep separate export files per course, topic, or playlist (e.g. `dsa-course-bookmarks.txt`, `system-design-bookmarks.txt`) and load whichever one you need into the tool for a focused revision session on that group of related videos.

## Privacy

Everything runs locally in your browser. Your bookmarks file is never uploaded anywhere — the only network calls this tool makes are to YouTube's public oEmbed API (to fetch video titles) and YouTube's thumbnail CDN.

## Credits

Built to complement [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) — all bookmark capture happens there; this tool is purely for viewing and revising what you've already captured.

## About this tool

This is a single self-contained `index.html` file — plain HTML, vanilla JavaScript, and [Tailwind CSS](https://tailwindcss.com/) (loaded via CDN, marked with `*` above). There's no server, no framework, and no build tooling: open the file in a browser and it works.

It was designed and built end-to-end using [Claude Code](https://claude.com/claude-code), Anthropic's agentic coding CLI — from the original parsing logic through the Tailwind-based light/dark UI.

It also supports a light/dark theme toggle (defaults to light mode), remembered per-browser via `localStorage`.
