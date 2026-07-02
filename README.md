# Midream Shopify Theme

Custom storefront theme for **Midream** (recovery & wellness — heated massagers, cervical traction pillows, fascia rollers), built on top of [Shopify Dawn](https://github.com/Shopify/dawn) 15.5.0.

It's a plain Liquid/JSON/CSS/JS theme — no build step, no framework, no bundler. Everything in this repo can be uploaded to Shopify as-is.

## What's customized vs. stock Dawn

- **Branding** (`config/settings_data.json`): Midream's color palette (deep teal `#0f4c4c`, soft coral `#ec8b6f`, warm off-white `#f4ede4`), Inter typography, slightly rounded buttons/cards.
- **Header** (`sections/header-group.json`, `sections/header.liquid`): logo left, centered nav, sticky on scroll, light scheme for logo legibility. Falls back to the bundled `assets/midream_logo.svg` until a logo is uploaded via the theme editor.
- **Homepage** (`templates/index.json`): hero banner, a featured "Massage & Recovery" grid, a brand-story block, a disabled-by-default "Fitness & Fascia Tools" grid, and a newsletter signup.
- **Footer** (`sections/footer-group.json`): brand description, quick links (from the store's existing "footer" navigation menu), policy links, payment icons.

All product/collection content is pulled live from Shopify — nothing is hardcoded. Section visibility, copy, images, and menu links are all editable from the theme editor after this is connected.

## Connecting this repo to Shopify

1. In the Shopify admin, go to **Online Store → Themes**.
2. Click **Add theme → Connect from GitHub**.
3. Authorize Shopify's GitHub app if you haven't already, then select this repository and the `main` branch.
4. Shopify pulls in the current state of the branch as a new (unpublished) theme. Preview it, then **Publish** when you're ready to go live.

Once connected, every push to the connected branch updates that theme automatically — there's no separate deploy step.

> Tip: use a separate branch (e.g. `staging`) connected to a second theme for previewing changes before they hit `main`/production, and open PRs into `main` to keep a clean history.

## Local development

Install the [Shopify CLI](https://shopify.dev/docs/api/shopify-cli) if you don't have it:

```bash
npm install -g @shopify/cli
```

From the theme folder, start a local dev server against your store:

```bash
shopify theme dev --store your-store.myshopify.com
```

This serves the theme locally with hot reload and a live preview URL, without publishing anything. Use `shopify theme check` to lint against Shopify's theme rules before pushing.

## Repo structure

Standard Dawn/Online Store 2.0 layout — `layout/`, `templates/`, `sections/`, `snippets/`, `assets/`, `config/`, `locales/`. See [Shopify's theme architecture docs](https://shopify.dev/docs/storefronts/themes/architecture) if any of this is unfamiliar.

## Known gaps / next steps

- **Hero image**: the homepage hero currently falls back to a teal/coral gradient (no image set). Drop a real image into the "Image banner" section via the theme editor whenever one's ready — no code change needed.
- **Logo**: ships with `assets/midream_logo.svg` as a fallback. Upload the final logo file via **Theme settings → Logo** in the editor to take full control of size/alt text.
- **Fitness & Fascia Tools grid**: built but disabled on the homepage (no sales data yet to justify surfacing two product grids). Toggle it on from the theme editor's section list whenever it's wanted.
- **Payments**: intentionally untouched — no payment-provider-specific code. Configure payment methods in Shopify admin as usual.
