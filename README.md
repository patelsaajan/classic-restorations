# Classic Restorations

A single-page landing site for **Classic Restorations** — a London workshop bringing classic cars
back to the road, one at a time. Built as a [Nuxt 4](https://nuxt.com) + [Tailwind CSS v4](https://tailwindcss.com)
implementation of a Claude Design handoff (Option D — "Big Frame").

## Stack

- **Nuxt 4** (Vue 3, file-based routing)
- **Tailwind CSS v4** via `@tailwindcss/vite` — theme tokens live in `app/assets/css/main.css`
  under `@theme`. Styling is utility-first; the only hand-written CSS is the two hatched
  `stripes` placeholder utilities and the `pulse-ring` / `drift` keyframes (things utilities
  can't express). No inline `style` attributes.
- Google Fonts: Anton (display), Oswald (UI), Lora (body), Special Elite (typewriter),
  Caveat (handwriting), loaded in `nuxt.config.ts`.

## Structure

```
app/
  assets/css/main.css     design tokens + custom utilities/keyframes
  components/
    SiteHeader.vue        magazine masthead nav
    HeroSection.vue       title + polaroid photo with 4 interactive hotspots
    WaitlistSection.vue   pre-launch waitlist form (red)
    AboutSection.vue      Sam's story + stats + footnote
    CtaSection.vue        minimal "last call" CTA
    SiteFooter.vue        socials + contact
  pages/index.vue         composes the page
```

## Develop

```bash
pnpm install
pnpm dev          # http://localhost:3000
```

Other scripts: `pnpm build`, `pnpm generate` (static), `pnpm preview`.

## Notes / TODO

- The hero car shot and Sam's portrait are hatched placeholders — drop real images into a
  `public/` folder and swap the placeholder blocks in `HeroSection.vue` / `AboutSection.vue`.
- The waitlist form is non-functional (`onSubmit` is a stub) — wire it to a real backend.
- Hotspot content (the four restoration notes) is data-driven in `HeroSection.vue`.
