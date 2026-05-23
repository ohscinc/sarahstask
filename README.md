# Sarah's T.A.S.K. — Website

A complete, production-ready website for **Sarah's Tactically Aligned Speech Know-How's**, a private speech therapy practice based in Central Florida serving clients in person and virtually across six states (FL, NY, CA, NC, MO, VA).

---

## What's in this folder

```
sarahstask/
├── index.html           Home page (hero, services preview, FAQ, CTA)
├── about.html           About Sarah Bipath & her credentials
├── services.html        Services (pediatric, adult, specialty, process)
├── contact.html         Contact options + Jane App intake card
├── faq.html             Frequently asked questions (7 categories, 31 Q&As)
├── zee.html             "Where is Zee?" — Sarah's children's book
├── 404.html             Custom not-found page
├── favicon.svg          Site icon (sage "s" monogram)
├── robots.txt           Search engine crawl instructions
├── sitemap.xml          Search engine sitemap
├── llms.txt             AI assistant context (ChatGPT, Claude, Perplexity, etc.)
├── netlify.toml         Netlify deployment config (clean URLs, caching)
├── README.md            This file
└── images/
    ├── sarah-hero.jpg         Sarah with child (homepage hero)
    ├── sarah-portrait.jpg     Headshot (About + homepage)
    └── sarah-with-zee.jpg     Sarah holding her book (Zee page)
```

**Total site size:** ~430 KB including all images. Loads in under 2 seconds on a typical mobile connection.

---

## How to deploy

### Easiest — Netlify Drop (recommended, free, ~2 minutes)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag this entire folder onto the page
3. Done — you'll get a free URL like `random-name.netlify.app`
4. Optional: in Netlify settings, point `sarahstask.com` to your new site (instructions in their docs)

The included `netlify.toml` automatically configures:
- Clean URLs (`/about` works, not just `/about.html`)
- Custom 404 page
- Security headers
- Image caching (faster repeat visits)

### Other hosting options

- **Vercel:** Drag-and-drop at [vercel.com/new](https://vercel.com/new). Same one-click experience as Netlify.
- **Cloudflare Pages:** Drag-and-drop at [pages.cloudflare.com](https://pages.cloudflare.com). Free, fast.
- **GitHub Pages:** Push the folder to a GitHub repo, enable Pages in settings.
- **Traditional web hosts (Bluehost, GoDaddy, etc.):** Upload the folder via FTP to your `public_html` or `www` directory.
- **Replace existing Squarespace site:** This site is fully self-contained HTML, so it can replace the current Squarespace site by pointing the `sarahstask.com` domain at any of the hosts above and canceling Squarespace.

---

## Updating the site

The site is plain HTML/CSS/JavaScript — no build step required. To make changes:

1. Open the `.html` file you want to edit in any text editor (VS Code, Sublime, even Notepad)
2. Find the text or section to change
3. Save the file
4. Re-upload to your host (or push to your GitHub repo if using Pages/Netlify with Git)

### Common updates

**Update Sarah's photos:** Replace files in `images/` with the same filenames. Keep them at roughly 666×1000 pixels and under 100 KB for best performance.

**Update the Jane App intake link:** In `contact.html`, search for `sarah-bipath.clientsecure.me` and replace with the specific intake form URL from Jane.

**Update the booking link site-wide:** Search across all `.html` files for `sarah-bipath.clientsecure.me` and update each occurrence.

**Update phone number:** Search across all files for `4074503418` (and `407-450-3418` for the display version).

**Update email:** Search across all files for `admin@sarahstask.com`.

**Add a testimonial:** I left the homepage ready for a testimonials section — happy to wire one up when Sarah collects 2-3 quotes from clients.

---

## Tech notes

- **No JavaScript framework** — pure HTML, CSS, and a tiny bit of vanilla JS for the mobile menu and FAQ accordion
- **No build step** — files work as-is when opened in a browser
- **No database, no backend** — all content is static, written into the HTML files
- **Google Fonts** loaded from CDN (Cormorant Garamond + Lato)
- **Fully responsive** — tested across iPhone SE, iPhone Pro Max, iPad, laptop, and large desktop sizes
- **Accessibility** — respects `prefers-reduced-motion`, has proper alt text on all images, semantic HTML structure, sufficient color contrast
- **SEO ready** — meta descriptions, Open Graph tags for social sharing, sitemap.xml, robots.txt

---

## Browser support

Works in all modern browsers:

- Chrome / Edge (last 2 versions)
- Safari (iOS 14+ and macOS Big Sur+)
- Firefox (last 2 versions)
- Mobile browsers on iPhone and Android

Internet Explorer is not supported (Microsoft retired it in 2022).

---

## Support

If you need to make changes you're not comfortable with — or want to add features like a blog, testimonials, online intake forms, or analytics — any web developer should be able to work with these files easily.

For Sarah's appointment system and patient management, refer to **Jane App** support directly: [jane.app/support](https://jane.app/support).
