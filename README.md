# YouTube Video Timestamp Parser

### 🔗 [**Open the live tool →**](https://sathishportfolio.github.io/YouTube-Video-Timestamp-Parser/)

No setup needed — click the link above, then hit **Load Sample** in the tool to try it instantly with example data.

![Built with Claude Code](https://img.shields.io/badge/Built%20with-Claude%20Code-6366f1?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-38BDF8?style=flat-square&logo=tailwindcss&logoColor=white)
![No build step](https://img.shields.io/badge/No%20build%20step-10B981?style=flat-square)
![Zero dependencies](https://img.shields.io/badge/Zero%20dependencies*-D946EF?style=flat-square)
![License: MIT](https://img.shields.io/badge/License-MIT-EAB308?style=flat-square)

Turn your [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) export into a clean, clickable revision sheet — organized by video, sorted by recency, and ready to jump straight to the moment that matters.

## Why this exists

Long lecture videos and tutorials are painful to revisit. Scrubbing through a 2-hour video to find "that one part about auth" wastes time you don't have.

YouTube's built-in chapters help, but only at a coarse level — a single chapter can easily run 20-30 minutes, and there's no way to jump to the *specific* moment inside it that you actually cared about. That's the gap [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) and this tool fill together: bookmark the exact second within a chapter, and this tool turns those fine-grained bookmarks into clickable links — giving you precision native chapters can't.

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
      "lastModifiedByVideoId": "{\"qF20cAHKrXA\":1787797924676}",
      "qF20cAHKrXA": "[{\"time\":855,\"desc\":\"Need for Session\"},{\"time\":895,\"desc\":\"Session Factory\"},{\"time\":966,\"desc\":\"Open Session\"},{\"time\":1040,\"desc\":\"save vs persist\"},{\"time\":1124,\"desc\":\"JPA compatibility\"},{\"time\":1245,\"desc\":\"No Config\"},{\"time\":1288,\"desc\":\"Need for .cfg.xml file\"},{\"time\":1378,\"desc\":\"Added Config\"},{\"time\":1419,\"desc\":\"@Entity\"},{\"time\":1631,\"desc\":\"Need for Transaction \"},{\"time\":1740,\"desc\":\"Create Table Error\"},{\"time\":1810,\"desc\":\"Create Table DDL\"},{\"time\":1943,\"desc\":\"Hibernate Show SQL\"},{\"time\":1975,\"desc\":\"Hibernate DDL create vs update\"},{\"time\":2134,\"desc\":\"Session Close\"},{\"time\":2292,\"desc\":\"Read\"},{\"time\":2476,\"desc\":\"Lazy vs Eager\"},{\"time\":2632,\"desc\":\"Update\"},{\"time\":2699,\"desc\":\"Hibernate Merge Steps \"},{\"time\":2777,\"desc\":\"Delete\"},{\"time\":2985,\"desc\":\"Entity vs Table\"}]"
    }
   ```
3. **Open this tool** — Open `YouTube Video Timestamp Parser.html` in any browser (double-click it, no installation needed).
4. **Load your export** — Either:
   - Click **Upload File** and select your exported `.txt`/`.json` file,
   - Paste the raw exported text directly into the textarea and click **Convert All Videos**, **or**
   - Click **Load Sample** to instantly try the tool with example data — no file needed.
5. **Revise** — You'll get a card per video with its title, thumbnail, and bookmarked timestamps. Click any timestamp to jump straight to that moment on YouTube. Click **Click to copy** on a card to copy that video's full timestamp list to your clipboard.

## Tips for organizing by group

Since the exported file is just plain text/JSON, you can keep separate export files per course, topic, or playlist (e.g. `dsa-course-bookmarks.txt`, `system-design-bookmarks.txt`) and load whichever one you need into the tool for a focused revision session on that group of related videos.

## Privacy

Everything runs locally in your browser. Your bookmarks file is never uploaded anywhere — the only network calls this tool makes are to YouTube's public oEmbed API (to fetch video titles) and YouTube's thumbnail CDN.

## Credits

Built to complement [YouTube Bookmarker](https://chromewebstore.google.com/detail/youtube-bookmarker/fnpjllldbpafaicnbgakpokibefgdeim) — all bookmark capture happens there; this tool is purely for viewing and revising what you've already captured.

No copyright infringement intended. This project is not affiliated with, endorsed by, or promoted by YouTube, Google, or the YouTube Bookmarker extension developers — all trademarks and video content belong to their respective owners. It's an independent, unofficial utility built purely for educational purposes, to make personal video notes easier to revisit.

## About this tool

This is a single self-contained `index.html` file — plain HTML, vanilla JavaScript, and [Tailwind CSS](https://tailwindcss.com/) (loaded via CDN, marked with `*` above). There's no server, no framework, and no build tooling: open the file in a browser and it works.

It was designed and built end-to-end using [Claude Code](https://claude.com/claude-code), Anthropic's agentic coding CLI — from the original parsing logic through the Tailwind-based light/dark UI.

It also supports a light/dark theme toggle (defaults to light mode), remembered per-browser via `localStorage`.
