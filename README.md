# 🛒 Gokul Electronics — Store Website

A modern, fully responsive, single-page website for **Gokul Electronics**, a trusted electronics & appliances store in Dhanori, Pune. Built with **pure HTML, CSS and vanilla JavaScript** — no frameworks, no build tools, no dependencies. Open `index.html` and it just works.

**Live site**: [gokul-sparkle-display.lovable.app](https://gokul-sparkle-display.lovable.app)

---

## 📑 Table of Contents

- [About the Store](#-about-the-store)
- [Features](#-features)
- [Screenshots](#-screenshots)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [How It Works](#-how-it-works)
  - [Product Catalogue & Search](#1-product-catalogue--search)
  - [Customer Reviews](#2-customer-reviews)
  - [Owner Product Management](#3-owner-product-management)
  - [Open / Closed Status](#4-open--closed-status)
  - [Custom Crosshair Cursor](#5-custom-crosshair-cursor)
- [Data & localStorage](#-data--localstorage)
- [Accessibility](#-accessibility)
- [Performance](#-performance)
- [Customization Guide](#-customization-guide)
- [Deployment](#-deployment)
- [Credits](#-credits)

---

## 🏪 About the Store

| | |
|---|---|
| **Name** | Gokul Electronics |
| **Tagline** | Your Trusted Electronics & Appliances Store in Dhanori |
| **Address** | Gokul Residency, Opp. Canara Bank, Madhav Nagar, Dhanori, Pune, Maharashtra 411015 |
| **Phone** | [077750 11155](tel:07775011155) |
| **Hours** | Open daily · Closes at 9:00 PM |
| **Products** | TVs, Refrigerators, Air Coolers, Washing Machines, Home Appliances & Accessories |

---

## ✨ Features

### For Customers
- 🦸 **Hero section** with headline, *Shop Now* & *Call Us* CTAs and a live **open/closed status indicator** based on shop timings
- 🛍️ **Product cards** with image, name, description, original vs. discounted price, bright **discount badges** (e.g. `50% OFF`) and an **Enquire Now** button
- 🔍 **Instant search** — filters products live by name or category as you type
- 🗂️ **Category filters** — TVs, Refrigerators, Coolers, Washing Machines, Accessories (and All)
- ⭐ **Customer reviews** — star ratings, review form, and submissions saved in the browser so they survive a refresh
- 📍 **Contact section** with address, Google Maps link, business hours and click-to-call buttons

### For the Shop Owner
- 🧰 **Built-in product management panel** — add new products, edit name / image URL / price / discount / description, delete products, and reset to the default catalogue. All changes persist via `localStorage`.

### Design & Polish
- 🌙 Premium dark theme with gradient orbs, soft glows and animated background effects
- 🖱️ **Custom animated crosshair cursor** on desktop (normal touch behavior on mobile)
- 🎞️ Scroll reveal animations, hover lifts, animated stat counters and smooth scrolling
- 📱 Fully responsive — mobile hamburger menu, fluid grids, touch-friendly targets

---

## 🖼️ Screenshots

> Add your own screenshots here after pushing to GitHub (e.g. `docs/screenshot-home.png`).

| Home | Products |
|------|----------|
| _Hero with open status & CTAs_ | _Filterable product grid_ |

---

## 🧰 Tech Stack

| Layer | Choice | Why |
|-------|--------|-----|
| Markup | Semantic **HTML5** | Accessibility & SEO out of the box |
| Styling | **CSS3** (custom properties, grid, flexbox, keyframes) | No framework overhead |
| Logic | **Vanilla JavaScript (ES6+)** | Zero dependencies, instant load |
| Storage | **Web localStorage** | Persistence without a backend |
| Images | Unsplash placeholders | Free, high-quality product photos |
| Fonts | Google Fonts — *Sora* (headings) & *Manrope* (body) | Modern, legible typography |

---

## 📁 Project Structure

```text
├── public/
│   └── site/
│       ├── index.html      # Page structure: hero, products, reviews, manage, contact, footer
│       ├── style.css       # Theme tokens, layout, animations, responsive & mobile styles
│       └── script.js       # Catalogue, search, filters, reviews, management, cursor, counters
├── src/
│   └── routes/
│       └── index.tsx       # Redirects "/" to the static site + SEO metadata
└── README.md
```

The website itself lives entirely in `public/site/` — three files, cleanly separated.

---

## 🚀 Getting Started

No build step required. Pick any option:

### Option 1 — Just open it
```bash
# double-click index.html, or
open public/site/index.html
```

### Option 2 — Local server (recommended)
```bash
npx serve public/site
# or
python3 -m http.server 8000 --directory public/site
```
Then visit the printed URL (e.g. `http://localhost:8000`).

### Option 3 — Clone the repo
```bash
git clone <this-repository-url>
cd <repository-name>
# then open public/site/index.html
```

---

## ⚙️ How It Works

### 1. Product Catalogue & Search
- The default catalogue ships as a JS array in `script.js` (12 products across 5 categories).
- On load, saved products from `localStorage` override the defaults.
- The search box filters by **name and category** on every keystroke; category chips narrow the grid further.
- Discount badges and sale prices are computed from `price` + `discount %`.

### 2. Customer Reviews
- Reviews render as cards with an interactive **star picker** (1–5).
- The form validates name, rating and message, then appends the review and saves it.
- Submissions persist across refreshes via `localStorage`.

### 3. Owner Product Management
- The **Manage** section provides an add/edit form plus delete buttons on each card.
- Editing pre-fills the form; saving recomputes the discount badge automatically.
- **Reset** restores the original default catalogue (useful if image URLs go stale).

### 4. Open / Closed Status
- The hero badge reads the browser clock and shows **Open Now · closes 9 PM** between 10:00 AM and 9:00 PM, otherwise **Closed · opens 10 AM**.

### 5. Custom Crosshair Cursor
- A crosshair + ring element follows the mouse with a smooth trail on pointer-fine devices only.
- Touch devices keep the default cursor/tap behavior — detected via media queries, not user-agent sniffing.

---

## 💾 Data & localStorage

| Key | Contents |
|-----|----------|
| `gokul.products.v2` | The full product catalogue (owner edits) |
| `gokul.reviews.v1` | Customer reviews |

- Data is per-browser — it lives on the visitor's device, not a server.
- Clearing site data resets the store to defaults. The **Reset catalogue** button does the same in one click.

---

## ♿ Accessibility

- Semantic landmarks (`header`, `main`, `nav`, `section`, `footer`) with skip-to-content link
- Visible keyboard focus styles and full keyboard operability for menus, forms and filters
- `aria-expanded` on the mobile menu toggle, labelled form controls, and decorative effects marked `aria-hidden`
- Sufficient color contrast in the dark theme

---

## ⚡ Performance

- **Zero frameworks** — the whole site is 3 static files
- Google Fonts loaded with `preconnect` + `display=swap`
- Images lazy-loaded from Unsplash; CSS animations are GPU-friendly (transform/opacity)
- No network calls at runtime beyond fonts and images

---

## 🎨 Customization Guide

| I want to… | Edit this |
|------------|-----------|
| Change store name, phone or address | `public/site/index.html` (header, contact, footer) |
| Change shop opening hours | `script.js` → the status-indicator hours check |
| Change colors / theme | `style.css` → CSS custom properties at the top |
| Change default products | `script.js` → `DEFAULT_PRODUCTS` array |
| Swap product photos | Owner panel → Edit → paste any image URL |

---

## 📦 Deployment

The site is static and deploys anywhere:

- **Lovable (current)**: auto-deployed to [gokul-sparkle-display.lovable.app](https://gokul-sparkle-display.lovable.app)
- **GitHub Pages**: push the repo → Settings → Pages → deploy from branch
- **Netlify / Vercel / Cloudflare Pages**: drag-and-drop the `public/site` folder, no config needed

---

## 📄 License

© Gokul Electronics, Dhanori, Pune. All rights reserved.

---

Built with ❤️ using [Lovable](https://lovable.dev) — continue developing this project in the [Lovable editor](https://lovable.dev/projects/c3444a01-cf0b-4443-91c3-2f8065ae54c2).
