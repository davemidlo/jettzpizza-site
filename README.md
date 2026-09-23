# Jett’z Pizza

Minimal static website for [jettzpizza.com](https://jettzpizza.com/). It uses plain HTML and CSS with no runtime dependencies, build tooling, analytics, or backend.

## Files

- `index.html` — page content and metadata
- `styles.css` — responsive presentation
- `favicon.svg` — favicon placeholder
- `_headers` — security and privacy-oriented response headers for Cloudflare Pages

## Local preview

From this repository's root directory:

```sh
python -m http.server 8000
```

Open <http://localhost:8000>. Stop the server with `Ctrl+C`.

Opening `index.html` directly also works, but a local server more closely matches deployment behavior.

## Deploy to Cloudflare Pages

These steps use Cloudflare Pages Git integration so pushes to `main` deploy automatically.

1. Push this repository to GitHub with `main` as the default branch.
2. In Cloudflare, open **Workers & Pages** and select **Create application**.
3. Select **Pages**, then **Import an existing Git repository**.
4. Choose `jettzpizza-site` and select **Begin setup**.
5. Use these build settings:
   - Production branch: `main`
   - Framework preset: `None`
   - Build command: `exit 0`
   - Build output directory: `.`
   - Root directory: leave blank
6. Save and deploy. Verify the generated `*.pages.dev` address before adding the custom domain.

Cloudflare Pages documentation: <https://developers.cloudflare.com/pages/framework-guides/deploy-anything/>

## Connect `jettzpizza.com`

`jettzpizza.com` is an apex domain. Cloudflare requires an apex domain used with Pages to be an active zone in the same Cloudflare account.

1. In the deployed Pages project, open **Custom domains**.
2. Select **Set up a domain** and enter `jettzpizza.com`.
3. Follow Cloudflare's validation prompts.
4. If the domain is not already using Cloudflare authoritative DNS, add the domain as a Cloudflare zone and update its registrar nameservers to those Cloudflare assigns.
5. Once Cloudflare reports the domain active, verify `https://jettzpizza.com/` and its certificate.

Cloudflare custom-domain documentation: <https://developers.cloudflare.com/pages/configuration/custom-domains/>

DNS, registrar, and Cloudflare account changes are intentionally not automated by this repository.
