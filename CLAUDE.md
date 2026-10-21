# Novel Scraper Studio (static site)

Single-file `index.html` deployed on GitHub Pages: https://catwithasword.github.io/novel-scraper-studio/ (repo `catwithasword/novel-scraper-studio`, branch `master`). Deploy = commit + push.

- **Scrape tab**: client-side; fetches pages through public CORS proxies (allorigins → corsproxy.io → codetabs, with failover). Collects `chapter-N` links from a TOC URL (follows `?*page=N` pagination), writes one `.txt`.
- **Upload tab**: splits a `.txt` on `====` banner blocks (fallback: `Chapter N` lines); one Copy button per chapter showing only the number; Copy copies the body without title.
- **Output format**: each chapter is `====(60)\n<number + title>\n====(60)\n\nbody`. The banner title comes from the page heading (`.entry-title`, `.chapter-title`, `h1`, `h2`, first one containing a digit/`ตอน`/`chapter`), falling back to `<title>`, and gets the URL's chapter number prepended if it has no digit.
- Local server-side twin (no proxy limits): `/Users/xd/Downloads/novel-scraper/app.py` (Flask, port 5015). Keep `extract_chapter` / banner logic in sync between the two.
