# Magic of Marrakech — Edit Guide

**Domain:** magicofmarrakech.com
**GitHub Repo:** https://github.com/appofun/magicofmarrakech
**GitHub Pages:** https://appofun.github.io/magicofmarrakech
**Local Folder:** /Users/admin/magicofmarrakech

---

## What It Is

A premium Moroccan tourism and travel landing page for **Magic of Marrakech** — promoting private tours, cultural experiences, desert escapes, medina walks, Moroccan food, hammam experiences, photography tours, and day trips from Marrakech.

Hosted on **GitHub Pages** — fully static, zero backend, zero dependencies.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | Full page — all 12 sections |
| `style.css` | Warm Moroccan theme, all CSS placeholders |
| `script.js` | Navbar, hamburger, fade-in, form alert, counters, smooth scroll |
| `README.md` | This file |
| `CNAME` | magicofmarrakech.com (GitHub Pages custom domain) |

---

## How to Deploy on GitHub Pages

```bash
cd /Users/admin/magicofmarrakech
git init
git branch -m main
git add .
git commit -m "Initial launch: Magic of Marrakech"
gh repo create appofun/magicofmarrakech --public --source=. --remote=origin --push
gh api repos/appofun/magicofmarrakech/pages --method POST \
  -f "source[branch]=main" -f "source[path]=/"
```

Then add DNS at Namecheap + enable Enforce HTTPS in GitHub Pages settings.

---

## How to Update a Live Site

```bash
cd /Users/admin/magicofmarrakech
git add .
git commit -m "Update: describe changes"
git push
# Auto-redeploys in ~1–2 min
```

---

## How to Edit Text

### Logo / Brand Name
In `index.html` — find `<span class="logo-main">Magic of Marrakech</span>`

### Main Headline
```html
<h1 class="hero-title">
  Discover the
  <span class="text-gradient-gold">Magic of Marrakech</span>
</h1>
```

### Contact Email
Find `contact@magicofmarrakech.com` in `index.html` and `script.js` → replace.

### WhatsApp Button
Find in the Contact section:
```html
<!-- REPLACE href="#" WITH YOUR REAL WHATSAPP LINK -->
<a href="#" class="btn btn--whatsapp">Chat on WhatsApp</a>
```
Replace `href="#"` with:
```
href="https://wa.me/212XXXXXXXXX?text=Hello%2C%20I%27d%20like%20to%20book%20a%20Marrakech%20experience"
```
Morocco code = **212**. Example: `https://wa.me/212612345678`

### Experience Cards
Find `<div class="experiences-grid">` — each card has:
```html
<h3 class="exp-title">Experience Name</h3>
<p class="exp-desc">Description text here.</p>
<span class="exp-duration">Duration</span>
<span class="exp-highlight">Badge text</span>
```

### Day Trip Cards
Find `<div class="trips-grid">` — edit `.trip-name`, `.trip-desc`, `.trip-duration`

---

## How to Change Colors

All colors are CSS custom properties in `style.css` under `:root`:

```css
:root {
  --bg:         #FFF8F0;   /* Cream background */
  --terracotta: #C65D2E;   /* Primary warm accent */
  --gold:       #F4B942;   /* Gold accent */
  --red:        #B91C1C;   /* Marrakech red */
  --green:      #2F6B4F;   /* Palm green */
  --text:       #211A14;   /* Dark text */
  --muted:      #6B5E52;   /* Muted text */
}
```

---

## How to Change Fonts

Fonts loaded from Google Fonts in `index.html` `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display...Inter..." rel="stylesheet" />
```

In `style.css`:
```css
--font-display: 'Playfair Display', Arial, serif;  /* Big headings */
--font-head:    'Poppins', Arial, sans-serif;       /* Section titles */
--font-body:    'Inter',   Arial, sans-serif;       /* Body text */
```

---

## How to Replace CSS Placeholders with Real Photos

### Experience cards
Each experience card has a comment:
```html
<!-- REPLACE WITH REAL IMAGE: <img src="images/medina-tour.jpg" alt="..." /> -->
<div class="exp-img exp-img--medina"></div>
```
To replace:
1. Delete the `<div class="exp-img exp-img--medina"></div>`
2. Add: `<img src="images/medina-tour.jpg" alt="Marrakech Medina Walking Tour" style="width:100%;height:200px;object-fit:cover;" />`
3. Remove the related CSS class (e.g. `.exp-img--medina`) from `style.css`

### Gallery cards
Each gallery card has a comment:
```html
<!-- REPLACE WITH: <img src="images/gallery/medina-souks.jpg" alt="Medina Souks" /> -->
```

### Hero card image
Find `.tc-img-placeholder` div inside `.travel-card` — replace with a real photo.

### Trip cards
Each `.trip-img` div — replace with `<img>` and remove the CSS gradient class.

---

## Contact Form (No Backend)

Currently shows a JS alert. To connect Formspree:
1. Sign up at https://formspree.io
2. Create a form → get your Form ID
3. Update form tag: `action="https://formspree.io/f/YOUR_ID" method="POST"`
4. Replace the submit handler in `script.js` with a real fetch call.

---

## DNS Records (Namecheap)

| Type | Host | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | appofun.github.io |

After DNS propagates (~15–30 min) → GitHub Pages Settings → Enable **Enforce HTTPS**

---

## Tech Stack

- **HTML5** — semantic markup, no frameworks
- **CSS3** — custom properties, Grid, Flexbox, Moroccan pattern SVG, keyframe animations
- **Vanilla JS** — IntersectionObserver, smooth scroll
- **Google Fonts** — Playfair Display + Poppins + Inter
- **Hosting** — GitHub Pages (free, static)
- **Zero dependencies** — no npm, no build tools, no backend
