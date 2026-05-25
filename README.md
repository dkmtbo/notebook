# Notebook — Private Password-Protected Pages

**Live URL:** https://dkmtbo.github.io/notebook/

## How the password works

Every page on this site is encrypted using StatiCrypt (AES-256). The HTML files
in this repo contain only encrypted gibberish — no one can read them without the
password, even though the repo is public. When you open a page on your phone or
computer, you'll see a password prompt. Enter your password and tick "Remember me"
so you don't have to type it again for 30 days.

## How to publish on demand

If a source page changes and you don't want to wait until the next morning, run:

```
~/Desktop/CLAUDE/05_Book/bojanov_sto/publish-pages.sh
```

This re-encrypts all pages from their source files, commits, and pushes. The site
updates within a minute or two.

## How the daily auto-update works

A macOS launchd job runs the publish script every morning at 6:35 AM. If your Mac
was asleep at that time, it runs as soon as the Mac wakes up. Logs go to
`/tmp/bojanov-pages.log`.

To check the job is installed: `launchctl list com.bojanov.pages`

## How to add a new page

1. Open `~/Desktop/CLAUDE/05_Book/bojanov_sto/publish-pages.sh` in a text editor.
2. Find the `PAGES=( ... )` section near the top.
3. Add a new line following the same pattern:
   ```
   "my-new-page.html|/full/path/to/source.html|My Page Title"
   ```
   The three parts separated by `|` are:
   - The filename it will have on the website
   - The full path to the source HTML file on your Mac
   - The title shown on the password prompt
4. Run the publish script: `~/Desktop/CLAUDE/05_Book/bojanov_sto/publish-pages.sh`

The landing page updates automatically — the new page will appear in the list.

## Current pages

| Page | Source file |
|------|------------|
| Books - Daily Digest | `~/Desktop/CLAUDE/05_Book/bojanov_sto/today.html` |
| Book Ideas Tracker | `~/Desktop/CLAUDE/05_Book/bojanov_sto/book-ideas.html` |
