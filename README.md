# Proofs / 复本: Part One serial site

A static site for GitHub Pages. No build step, no external libraries, no web fonts (so it loads in mainland China without blocked resources).

## What's here

- `index.html`: the reader (layout, styles and script in one file)
- `forum.html`: the readers' forum (case-file threads, exhibits, author questions)
- `chapters.js`: the PUBLIC book data. It holds the schedule for Part One (Prologue to Chapter Sixteen) but text, exhibits and questions only for chapters already released. It is rebuilt for each release from the private master; never upload the master
- `assets/img/`: covers and part images
- `assets/audio/`: chapter MP3s, added on each release day only

## Schedule (Part One only)

Two chapters every Friday at 20:00 Beijing time:

| Date | Chapters |
|---|---|
| 30 Oct (soft preview) | Prologue |
| 6 Nov (launch) | One, Two |
| 13 Nov | Three, Four |
| 20 Nov | Five, Six |
| 27 Nov | Seven, Eight |
| 4 Dec | Nine, Ten |
| 11 Dec | Eleven, Twelve |
| 18 Dec | Thirteen, Fourteen |
| 25 Dec | Fifteen, Sixteen (end of Part One) |

Parts Two and Three are not published here.

## Each release day

1. Upload the new `chapters.js` from that week's release pack (replace the old one).
2. Upload that week's MP3s (e.g. `ch01.mp3`, `ch02.mp3`) from your audio folder into `assets/audio/`.
3. Commit. Check the site with a hard refresh.

The page also counts down by date, but the text only exists online once its pack is uploaded, so nobody can read ahead.

Add `?preview` to the address to see every published chapter unlocked. Add `?lang=zh` to open in Chinese. The Chinese is labelled as a first-draft translation.

## Forum (forum.html)

Boards: Announcements (written in the `FORUM.announcements` list in `forum.html`), Chapter Discussions (one case file per chapter, with text, audio, exhibits and author questions), and Reader Threads. Posts are tagged observation / theory / question / outside the book; anything beyond a reader's furthest chapter is redacted until they choose to open it.

Posts are stored in Supabase (`store: ONLINE`). New installs run `supabase_setup.sql`; the existing project needs `supabase_update_2.sql` once. To remove a post, open **Table Editor > posts** in Supabase and tick `hidden`.

## Publishing on GitHub Pages

1. Create a public repository, e.g. `proofs`.
2. Upload everything in this folder to it (drag and drop on the GitHub website works).
3. Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. After a minute the site is live at `https://YOUR-NAME.github.io/proofs/`.

## Things to know

- `github.io` is slow or unreliable from some networks in mainland China. If most of your readers are in China, the same folder can be hosted on a Chinese static host (for example Gitee Pages or Alibaba Cloud OSS) with no changes.
- The reader remembers each visitor's language and last chapter in their own browser.
