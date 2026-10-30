# Proofs / 复本: weekly serial site

A static site for GitHub Pages. No build step, no external libraries, no web fonts (so it loads in mainland China without blocked resources).

## What's here

- `index.html`: the whole site (layout, styles and script in one file). You can open it straight from the folder to test it, no server needed
- `chapters.js`: the book, in English and Chinese, with a release date and audio path for each chapter
- `assets/img/`: covers and the three part images
- `assets/audio/`: put the chapter MP3s here (empty for now)

## How release works

Each entry in `chapters.js` has a `releaseDate`. When someone opens the site, the page compares that date with their clock:

- released: full text, an audio player (shown only if the MP3 exists), and a download link
- not yet released: the title, the date, and a live countdown

The schedule as built: Prologue and Chapter One on Friday 6 November 2026 at 20:00 Beijing time, then one chapter every Friday at 20:00. Chapter Thirty-Four lands on 25 June 2027. To change it, edit the dates in `chapters.js`.

When Chapter Thirty-Four (`"isFinal": true`) is released, a "complete audiobook" download box appears on the home page and at the end of the last chapter.

Add `?preview` to the address (e.g. `https://yourname.github.io/proofs/?preview`) to see every chapter unlocked for checking. Add `?lang=zh` to open in Chinese.

## Audio files

Name them like this and drop them in `assets/audio/`:

`prologue.mp3, ch01.mp3, ch02.mp3 … ch34.mp3`

A chapter's player appears automatically once its file is there. Keep each file under 100 MB (GitHub's per-file limit). A 64 kbps mono MP3 of a 20-minute chapter is about 10 MB.

The complete audiobook will be several hundred MB, too big for the repository. Upload it as a GitHub **Release** asset instead (Releases allow files up to 2 GB), then paste its download link into `fullAudiobook` at the top of `chapters.js`.

## Publishing on GitHub Pages

1. Create a public repository, e.g. `proofs`.
2. Upload everything in this folder to it (drag and drop on the GitHub website works).
3. Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. After a minute the site is live at `https://YOUR-NAME.github.io/proofs/`.

## Things to know

- The time lock is a reading schedule, not security. All the text is in `chapters.js`, which anyone technical can open. That's normal for serials; if you need a real lock, publish each chapter's text into the file on its release day instead.
- `github.io` is slow or unreliable from some networks in mainland China. If most of your readers are in China, the same folder can be hosted on a Chinese static host (for example Gitee Pages or Alibaba Cloud OSS) with no changes.
- The reader remembers each visitor's language and last chapter in their own browser.
