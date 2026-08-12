# Pixelscue Bangalore — Website Project

Static site (plain HTML/CSS/JS, no build step). `index.html` is the whole
site; images live in `/images`. Ready to hand to Claude Code for git setup,
GitHub Pages hosting, and the custom domain connection.

## Business context (for Claude Code to keep in mind on future edits)

- Photo booth / 360° video booth / mirror booth rental company, Bangalore only.
- Founded in Bangalore in 2017. **Do not mention Chennai, Sri Lanka, Canada,
  or any other Pixelscue-branded location — this site speaks exclusively
  about Bangalore.**
- Legal/accounting entity is Jsquare Fincorp — **not to be mentioned on the
  site** unless the owner explicitly asks for it later (e.g. a terms page).
- Tagline: "Creating Cute Memories"
- Contact: +91 79750 91637 (call & WhatsApp) — already wired into all CTAs
  and the contact form via `wa.me` links.
- Domain already purchased: pixelscuebangalore.com (via GoDaddy)

## Design direction already applied

- White base background, vibrant accent colors (pink #FF3366, gold #FFB800,
  blue #00B8D9, violet #7C3AED) — deliberately moved away from an earlier
  dark-violet draft the owner didn't like.
- Fonts: Archivo Black (display), Space Grotesk (body), Caveat (handwritten
  accents) — loaded via Google Fonts CDN in `<head>`.
- Signature motif: torn-edge/film-strip section dividers + tilted photo
  collage in the hero.
- Real client photos already placed (Mr. Cooper Group, NatWest, Advisor360,
  Adecco/GBS Kids Day, two weddings, a birthday strip) — swap by replacing
  files in `/images` with the same filenames, or add new `<img>` entries.
- Pricing table reflects real packages (Classic Collage ₹14k, Classic Single
  Layout ₹16k, 360° Booth ₹14k, Mirror Booth ₹20k, all /3hrs + hourly extra).
  If pricing changes, edit the `.pkg-card` blocks in `index.html`.

## Known gaps / good next tasks for Claude Code

1. **Favicon** — not set up yet. Generate one from `images/logo-icon.png`
   and add the `<link rel="icon">` tag.
2. **Testimonials** — currently replaced with a factual "Trusted by" chip
   strip (real client names) rather than invented quotes. Swap in real
   testimonials once the owner collects them.
3. **Meta/OG tags** — add Open Graph tags (og:image, og:title, etc.) using
   `images/logo-horizontal.png` or a hero photo, for better link previews
   when shared on WhatsApp/social.
4. **Image optimization** — several source photos are 500-800KB; consider
   compressing/resizing for faster mobile load (e.g. `sharp` or `imagemin`).
5. **Git + GitHub Pages + domain setup** — see below.

## Suggested Claude Code setup steps

```bash
git init
git add .
git commit -m "Initial Pixelscue Bangalore site"
# create a new GitHub repo (via gh CLI or github.com), then:
git remote add origin https://github.com/<your-username>/pixelscue-bangalore.git
git branch -M main
git push -u origin main
```

Then enable GitHub Pages: repo → Settings → Pages → Deploy from branch →
`main` → `/ (root)`.

For the custom domain:
1. Add a file named `CNAME` in the repo root containing just:
   `pixelscuebangalore.com`
2. In GoDaddy DNS settings for the domain, add:
   - An `A` record pointing `@` to GitHub Pages' IPs (185.199.108.153,
     185.199.109.153, 185.199.110.153, 185.199.111.153)
   - A `CNAME` record pointing `www` to `<your-username>.github.io`
3. Back in GitHub Pages settings, enter `pixelscuebangalore.com` as the
   custom domain and enable "Enforce HTTPS" once it's verified (can take
   up to 24 hrs to propagate).
