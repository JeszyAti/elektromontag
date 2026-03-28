# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static one-page website for **Elektromontag Autóvillamossági Szerviz** — an auto electrical workshop in Budapest, XX. district (Pesterzsébet), operating since 1990. Hungarian only, no CMS. Dark theme with amber/orange accents.

## Commands

- `npm run dev` — Start dev server (localhost:4321)
- `npm run build` — Build static site to `dist/`
- `npm run preview` — Preview built site locally

## Architecture

**Tech stack:** Astro (static output), Tailwind CSS v4 + vanilla CSS custom properties, no JS framework.

**Structure:**
- `src/pages/index.astro` — Single page, composes all section components
- `src/layouts/Layout.astro` — HTML shell with meta tags, SEO, LocalBusiness JSON-LD schema
- `src/components/` — One component per page section: Header, Hero, Services, About, Reviews, Contact, Footer, ScrollReveal
- `src/styles/global.css` — Tailwind import, CSS custom properties (theme colors, spacing, typography), utility classes
- `src/assets/logo/logo.svg` — V2 logo source (circle + bolt + sparks)
- `public/` — Static assets (favicon.svg, images/)
- `nginx/default.conf` — Nginx config for Docker deployment
- `docker-compose.yml` — Docker deployment with deploy sidecar + nginx container
- `astro.config.mjs` — Site config with Tailwind vite plugin, domain: elektromontag.hu

**Design system:** Dark theme — background `#1a1d21`, alt `#22262b`, accent `#f59e0b` (amber). CSS custom properties in `global.css` `:root`. Inter font. 768px mobile breakpoint.

**SEO:** LocalBusiness/AutoRepair JSON-LD in Layout.astro, Open Graph meta tags, canonical URLs. Keyword strategy in `SEO-KULCSSZAVAK.md`.

## Deployment

Docker-based deployment on Hostinger VPS (72.61.95.59):
- `elektromontag-deploy` container clones repo and copies dist/ to shared volume
- `elektromontag-web` nginx container serves static files on port 8080
- Nginx Proxy Manager on VPS handles domain routing and SSL
- `dist/` is committed to repo (required for Docker deployment)

Deploy process: build locally → commit dist/ → push to GitHub → delete project via Hostinger API (`VPS_deleteProjectV1`, virtualMachineId: 1227252) → recreate from GitHub (`VPS_createNewProjectV1`, content: https://github.com/JeszyAti/elektromontag) → verify (`VPS_getActionDetailsV1`). See TODO.md for detailed steps.

## Key Business Data

Contact and service details are hardcoded in components (no CMS). If business info changes, update directly in:
- `Hero.astro` — phone numbers, hours, address
- `Contact.astro` — phone numbers, hours, address, map embed
- `Services.astro` — service list and descriptions
- `Layout.astro` — JSON-LD structured data
- `Header.astro` — CTA phone link

## Tone

All content is in Hungarian, **tegező** (informal) tone. "Hívj" not "Hívjon", "Keress" not "Keressen".
