# Faizaan Portfolio (Astro + Tailwind)

Minimal, placeholder-first portfolio site with a bold newsletter CTA.

## Tech Stack

- Astro (static site generator)
- Tailwind CSS
- Astro Sitemap integration

## Local Setup

1. Install dependencies:
   - Ensure Node.js LTS is installed and `npm` is available in your terminal PATH (or use the “Node.js command prompt” on Windows).
   - `npm install`
2. Start development server:
   - `npm run dev`
3. Build production files:
   - `npm run build`
4. Preview production build:
   - `npm run preview`

## Project Structure

```text
src/
  pages/
    index.astro
    about.astro
    projects.astro
  components/
    Header.astro
    Footer.astro
    NewsletterForm.astro
    ProjectCard.astro
  styles/
    globals.css
public/
  favicon.svg
  robots.txt
  images/
```

## Cloudflare Pages Deployment

1. Push this repository to GitHub (or Git provider connected to Cloudflare).
2. In Cloudflare Dashboard, go to **Workers & Pages** > **Create application** > **Pages**.
3. Connect the repository and configure:
   - **Framework preset**: `Astro`
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
4. Deploy.

## Important Placeholder Notes

- All page content is placeholder text and should be replaced.
- Newsletter form is frontend-only and has no backend integration yet.
- Update `site` URL in `astro.config.mjs` and `Sitemap` URL in `public/robots.txt` before launch.
