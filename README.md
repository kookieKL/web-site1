# STRIDE — Nike-Style Fashion Storefront

A modern, single-page clothing & footwear storefront with bold typography, large
imagery, smooth scrolling, and scroll-triggered animations. Built as a frontend
showcase; the backend is an optional stub for future work.

## Tech stack

- **Next.js 16** (App Router) + **React 19** + **TypeScript**
- **Tailwind CSS v4** — utility styling with design tokens in `app/globals.css`
- **GSAP + ScrollTrigger** — parallax and reveal-on-scroll animations
- **Lenis** — smooth scrolling
- **lucide-react** — icons
- **FastAPI** — minimal backend stub (not connected to the UI yet)

## Getting started

```bash
npm install
npm run dev
```

Open http://localhost:3000.

## Project structure

```
app/                 # Next.js routes, layout, global styles
  layout.tsx         # Fonts (Inter + Oswald), providers, Header/Footer
  page.tsx           # Composes Hero / About / Collections / Catalog + modal
  globals.css        # Design tokens, base styles, animations
components/
  layout/            # Header (sticky + mobile drawer), Footer
  sections/          # Hero, About, Collections, Catalog
  product/           # ProductCard, ProductGrid, ProductModal (quick view)
  ui/                # Button, Badge, Modal, Toast
data/
  brand.ts           # Single source of truth for brand name, slogan, copy
  products.ts        # Static product catalog
lib/
  smooth-scroll.tsx  # Lenis + GSAP ticker wiring
  animations.ts      # Reusable reveal & parallax hooks
backend/             # FastAPI stub (optional)
```

## Rebranding

Change the brand name, tagline, hero copy, and social links in a single file:
[`data/brand.ts`](data/brand.ts). Everything (header logo, hero, footer, page
title) updates automatically.

## Editing products

Products live in [`data/products.ts`](data/products.ts). Each product has a
category (`clothing` / `footwear`), a collection, price, images, colors, and
sizes. Replace the Unsplash image URLs with your own assets when ready.

## Optional backend stub

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload   # http://localhost:8000
```

Exposes `GET /health` and a placeholder `GET /api/products`. The frontend does
not call it yet — wire it up when you add a real cart/checkout.

## Notes

- The "Add to Bag" buttons are demo-only and show a toast; there is no cart or
  checkout integration.
- Animations respect `prefers-reduced-motion`.
