# joerxc.org — landing page

Static single page. No build step, no dependencies.

```
index.html
assets/joerg-pod.jpg          hero photo (2000 px)
assets/joerg-pod-small.jpg    hero photo (1100 px, mobile)
assets/windfield-inflight.jpg  windfieldmap screenshot (in flight)
assets/windfield-decay.jpg     windfieldmap screenshot (expired thermals)
backlink-snippet.html         paste into project pages to link back
```

## 1. Put it on GitHub

Create a **new public repository named exactly `joergkorner.github.io`**
(github.com → New repository → Owner: joergkorner → Name: `joergkorner.github.io` → Public → Create).

Then: **Add file → Upload files** → drag `index.html`, the `assets` folder and
`README.md` in → Commit.

That repo is a GitHub *user site*: it is served at the root, so it goes live at
**https://joergkorner.github.io/** within a minute or two. Your existing project
repos are untouched and stay at `.../invisible-railway/`, `.../goms/` etc.

(No Pages settings needed — a repo with this exact name publishes automatically
from the default branch.)

## 2. The domain joerxc.org

The domain does not resolve yet, so register it first (any registrar; Cloudflare,
Namecheap, Gandi, Infomaniak are all fine).

Then, at the registrar's DNS panel:

| Type  | Name  | Value                  |
|-------|-------|------------------------|
| A     | @     | 185.199.108.153        |
| A     | @     | 185.199.109.153        |
| A     | @     | 185.199.110.153        |
| A     | @     | 185.199.111.153        |
| CNAME | www   | joergkorner.github.io. |

Then in the repo: **Settings → Pages → Custom domain** → `joerxc.org` → Save,
and tick **Enforce HTTPS** once the certificate is issued (can take an hour).
GitHub writes a `CNAME` file into the repo itself — don't add one by hand before
the DNS records exist, or the site goes offline in the meantime.

**Nice side effect:** once the custom domain is active on the user site, GitHub
redirects `joergkorner.github.io/<repo>/` to `joerxc.org/<repo>/`. So all your
project pages get the new domain automatically — `joerxc.org/goms/`,
`joerxc.org/juraplayer/`, and so on. Old links keep working.

## 3. Back links on the project pages

Open `backlink-snippet.html`, copy the block, and paste it directly after
`<body>` in each project page you want a way back from. It is one `<a>` with
inline styles — nothing to load, nothing to break.

## Editing the text

The page is bilingual. Every translatable bit is a pair:

```html
<span data-lang="en">English text</span><span data-lang="de">Deutscher Text</span>
```

CSS hides one of the two; the button in the top right flips them. It opens in
German for German browsers, English for everyone else. Edit both halves and
nothing else needs to change.
