# Mike W Consulting LLC — static site

Plain HTML/CSS/JS. No build step, no npm, no frameworks, no Cloudflare Functions.

## Files

```
index.html          Home
services.html        Custom Software Development
our-software.html    Software We've Built (portfolio)
about.html           About
contact.html         Contact (Zoho Forms embed goes here)
styles.css           All styles for every page — one file
script.js            Mobile nav toggle + footer year
```

Each page is a complete, standalone HTML file with its own `<head>` and duplicated header/footer markup — that's normal for a plain static site with no templating. There's nothing to compile; open any `.html` file directly in a browser and it works.

## Editing

- **Copy:** edit the text directly inside the relevant `.html` file.
- **Colors, fonts, spacing:** all in `styles.css`, organized in sections with comments (Header/Nav, Home, Services, About, Contact, etc.). Change a `:root` variable at the top and it updates the whole site.
- **Nav links or footer:** since there's no shared template, update the header/footer block in **all five files** when you change something there (e.g. adding a new product link, changing the phone number).

## Adding the Zoho Forms embed

Open `contact.html` and find this block:

```html
<div class="zoho-embed-placeholder">
  Paste your Zoho Forms &lt;iframe&gt; embed code here
</div>
```

In Zoho Forms: open your form → **Share** → **Embed** → copy the `<iframe>` code it gives you, and paste it in place of that placeholder div. Submissions will flow into Zoho CRM the same way your other Zoho-connected forms already do — no server code needed on this site at all.

## Deploying to Cloudflare Pages

1. Push this folder to a GitHub repo (or use Cloudflare's direct file upload if you'd rather skip git for this one).
2. In Cloudflare: **Workers & Pages → Create → Pages → Connect to Git**, select the repo.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/` (repo root, since the HTML files live at the top level)
4. Deploy — you'll get a `*.pages.dev` URL immediately.
5. **Custom domain:** Pages project → **Custom domains** → add `mikewconsulting.com`, same flow you've used for epictools.net and docs.certms.com.
6. Every push to your main branch redeploys automatically.

No environment variables, no functions, nothing else to configure — it's pure static hosting.

## Notes

- The mobile menu (hamburger icon under 860px width) is handled by `script.js` — vanilla JS, no dependencies.
- If you ever want clean URLs without `.html` (e.g. `/services` instead of `/services.html`), Cloudflare Pages has a toggle for that under project settings, but the links in this site work correctly either way since they include the extension explicitly.
