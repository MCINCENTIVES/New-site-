# MC Incentives — site (images embedded)

This version has **all images baked into the HTML files**, so there is **no `images/` folder to upload**. That avoids the GitHub folder-upload problem completely.

## What to upload to your repo
Just these flat files (no folders needed):
- `index.html` (home)
- `Article.html`, `Blog.html`, `Book-a-Call.html`, `Contact.html`, `Insights.html`, `Packages.html`
- `support.js`

## Steps (fixes your broken images)
1. In your GitHub repo, **delete** any loose image files (hero1.jpg, logo.png, etc.) and the old `.html` pages.
2. **Add file → Upload files** and drag in the 7 HTML files + `support.js` from this folder. They upload individually — that's fine now, because the images are already inside the HTML.
3. Commit. Vercel redeploys automatically.
4. Hard-refresh the live site (Cmd/Ctrl + Shift + R). Images now show.

That's it — no `images` folder, no folder-path issues.

> Note: the home/insights/blog/article pages are ~2 MB each because the photos are embedded. That's fine for a marketing site (loads once, caches). If you later want smaller files, we can switch back to a real `images/` folder.
