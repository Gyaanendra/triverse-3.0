# Triverse 2.0 – IEEE Bennett University

Astro + Tailwind CSS + daisyUI powered landing site for **Triverse 2.0**, the flagship event of the IEEE Student Branch at Bennett University.

The site includes:

- Animated intro with diagonal bars + logo
- Floating dock navigation
- Event timeline and previous-editions gallery
- Teams and sponsors sections with image/logo placeholders
- Responsive light-theme design using your blue/cyan palette

---

## Tech Stack

- **Framework:** [Astro](https://astro.build/) (content-first, MPA style)
- **Styling:** Tailwind CSS + [daisyUI](https://daisyui.com/)
- **Icons / UI:** daisyUI components + custom utility classes
- **Images:** Astro `{ Image }` from `astro:assets` for optimized logos

Node and package versions are managed by `npm` (Astro starter defaults).

---

## Getting Started

```bash
# install dependencies
npm install

# start dev server
npm run dev

# build for production
npm run build

# preview production build locally
npm run preview
```

By default dev server runs at `http://localhost:4321` (Astro default).

---

## Project Structure

High-level structure (only key files shown):

```text
triverse-2.0/
├─ astro.config.mjs        # Astro + Tailwind/Vite config
├─ package.json
├─ public/
│  └─ favicon.svg          # Public assets served as-is
├─ src/
│  ├─ assets/
│  │  ├─ app.css           # Tailwind + daisyUI entry CSS + custom animations
│  │  ├─ astro.svg
│  │  └─ background.svg
│  ├─ components/
│  │  ├─ Header.astro      # Gradient header with IEEE + Bennett logos
│  │  └─ Footer.astro      # Thick footer with links, Linktree, contact, avatars
│  ├─ images/
│  │  ├─ bennettlogo.png   # University logo
│  │  └─ ieeelogo.png      # IEEE SB logo
│  ├─ layouts/
│  │  └─ Layout.astro      # Global layout: intro animation, header, dock, footer
│  └─ pages/
│     ├─ index.astro       # Home page (hero, overview, scrolling content)
│     ├─ events.astro      # Timeline + previous events gallery (placeholders)
│     ├─ teams.astro       # Team sections with image placeholders
│     └─ sponsers.astro    # Sponsor tiers with logo placeholders
└─ ...
```

---

## Key Implementation Details

### 1. Layout & Intro Animation

`src/layouts/Layout.astro`:

- Imports global CSS from `src/assets/app.css`.
- Wraps all pages with:
  - **Header** (gradient with real logos)
  - **Floating dock nav** (`Home / Events / Teams / Sponsers`)
  - **Main content** container (`#page-root`) with fade-in/out animations
  - **Footer** (links, contact, Linktree, team avatars)
- Contains:
  - **Intro overlay**: diagonal bar animation and “Triverse 2.0” + logo
  - **JavaScript hooks** for:
    - Playing intro on load
    - Fading page in
    - Fading out on navigation before going to the next page

### 2. Styling & Animations

`src/assets/app.css`:

- Imports Tailwind + daisyUI:

  ```css
  @import "tailwindcss";
  @plugin "daisyui";
  ```

- Defines custom utility classes:

  - `.page-fade-in` / `.page-fade-out` – smooth opacity transitions
  - `.page-overlay` – subtle radial glow on background
  - `intro-*` keyframes – diagonal bar intro animation
  - `.timeline-box` – card-like styling inside the events timeline

---

## Pages Overview

### `/` – Home (`src/pages/index.astro`)

- Hero section with:
  - Event name **Triverse 2.0**
  - Short intro text
  - CTA buttons: “Explore Events”, “Meet the Teams”
- Right-side card with **image placeholder** for club/event art.
- Long scrollable content:
  - “Why Triverse 2.0?”
  - Three feature cards: *Innovate, Collaborate, Celebrate*
  - “What to expect” section with paragraphs for future content.

### `/events` – Events (`src/pages/events.astro`)

- **Event Timeline** using daisyUI’s vertical timeline structure:
  - Inauguration, workshop, panel, hackathon, valedictory
  - Colored badges, dates, descriptions
- **Previous Editions** gallery:
  - Cards with **photo placeholders** for:
    - Triverse 1.0
    - Workshops
    - Hackathons
- Extra prose section: “More details coming soon” with filler text.

### `/teams` – Teams (`src/pages/teams.astro`)

- Sections for:
  - Core Team
  - Technical Team
  - Design & Media
- Each card includes a **group photo placeholder box** ready for a real image.
- “Volunteer Network” prose block with placeholder copy.

### `/sponsers` – Sponsors (`src/pages/sponsers.astro`)

- Grid of three sponsor tiers:
  - Gold, Silver, Community
- Each card includes a **logo placeholder box** to be replaced with real sponsor logos.
- “Why partner with Triverse 2.0?” section with placeholder text.

---

## Header & Footer

### Header – `src/components/Header.astro`

- Sticky gradient background using your colors:

  - `#00629B`, `#00B5E2`, `#009CA6`

- Uses Astro `<Image />` from `astro:assets` for optimized:

  - IEEE logo (`src/images/ieeelogo.png`)
  - Bennett logo (`src/images/bennettlogo.png`)

### Footer – `src/components/Footer.astro`

- Thicker multi-column footer with:

  - **Logo placeholder** + short description
  - **Links**: Events, Teams, Sponsers, Contact, **Linktree**
  - **Contact:** placeholder email
  - **Creators:** four avatar placeholders (A1–A4) for core team

- Linktree:

  ```text
  https://linktr.ee/ieee_bu_
  ```

---

## Customization Guide

- **Colors:**  
  Most custom colors use your palette:

  - Primary blue: `#00629B`
  - Teal: `#009CA6`
  - Cyan: `#00B5E2`
  - Base: `#FFFFFF`

  You can tweak/centralize these in Tailwind config later if desired.

- **Replace placeholders:**
  - Hero card image: replace the placeholder `<div>` with an `<Image />` or `<img>`.
  - Teams: replace team photo placeholders with real images.
  - Events: attach real photos for previous editions.
  - Sponsors: drop in real sponsor logos instead of placeholder boxes.

- **Intro Animation:**  
  The diagonal bars intro is controlled in `Layout.astro` + `app.css`. You can:

  - Turn it off entirely by removing the overlay + JS.
  - Adjust duration via the `intro-bar-*` and `intro-center` keyframes.

---

## Deployment

Typical Astro deployment flow:

```bash
npm run build
# then deploy contents of `dist/` to your static host (Netlify, Vercel, GitHub Pages, etc.)
```

Check Astro’s docs for specific platform adapters if you want SSR or advanced features.

---

## License / Ownership

This project is intended for **IEEE Student Branch, Bennett University** and the Triverse 2.0 event.  
Update this section with your chosen license or internal usage note.

# Astro Starter Kit: Basics

```sh
npm create astro@latest -- --template basics
```

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
/
├── public/
│   └── favicon.svg
├── src
│   ├── assets
│   │   └── astro.svg
│   ├── components
│   │   └── Welcome.astro
│   ├── layouts
│   │   └── Layout.astro
│   └── pages
│       └── index.astro
└── package.json
```

To learn more about the folder structure of an Astro project, refer to [our guide on project structure](https://docs.astro.build/en/basics/project-structure/).

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).
