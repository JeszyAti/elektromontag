# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static one-page website for **Elektromontag Autóvillamossági Szerviz** — an auto electrical workshop in Budapest, XX. district (Pesterzsébet), operating since 1990. Hungarian only, no CMS.

## Commands

- `npm run dev` — Start dev server (localhost:4321)
- `npm run build` — Build static site to `dist/`
- `npm run preview` — Preview built site locally

## Architecture

**Tech stack:** Astro (static output), vanilla CSS with custom properties, no JS framework.

**Structure:**
- `src/pages/index.astro` — Single page, composes all section components
- `src/layouts/Layout.astro` — HTML shell with meta tags, SEO, LocalBusiness JSON-LD schema
- `src/components/` — One component per page section: Header, Hero, Services, About, Reviews, Contact, Footer
- `src/styles/global.css` — Design tokens (CSS custom properties), reset, utility classes
- `public/` — Static assets (favicon.svg, fonts)
- `astro.config.mjs` — Site config, domain: elektromontag.hu

**Design system:** CSS custom properties defined in `global.css` — colors (`--color-primary`: dark blue, `--color-accent`: amber/orange), spacing scale, typography (Inter font), shadows, radii. Mobile-first responsive with 768px breakpoint.

**SEO:** LocalBusiness/AutoRepair JSON-LD in Layout.astro, Open Graph meta tags, canonical URLs. Target keywords: autóvillamosság Budapest, autóvillamossági szerviz XX. kerület.

## Key Business Data

Contact and service details are hardcoded in components (no CMS). If business info changes, update directly in:
- `Hero.astro` — phone numbers, hours, address
- `Contact.astro` — phone numbers, hours, address, map embed
- `Services.astro` — service list and descriptions
- `Layout.astro` — JSON-LD structured data
- `Header.astro` — CTA phone link

## Language

All content is in Hungarian. No i18n setup.
