# gsap-design-studio

> Agency-style landing page — GSAP letter-split nav animations, parallax video cursor tracking, Locomotive Scroll proxy sync, and interactive CSS rotation micro-interactions.

---

## What this demonstrates

A high-fidelity agency landing page built with zero framework overhead — just vanilla JS, GSAP, and Locomotive Scroll. The goal was to deeply understand scroll-driven animation mechanics: how GSAP's measurement system works, how virtual scrollers need to proxy their position, and how to combine stagger timing with cursor-based parallax for a premium feel.

---

## Techniques

**Letter-split nav animation**

`textContent.split("")` wraps each character in a `<span>` at runtime. GSAP then staggers each character with `y: -30`, `opacity: 1`, `ease: Expo.easeInOut`, and `stagger: 0.05` — the standard technique for the "raining letters" nav reveal seen on award-winning agency sites.

**Parallax video cursor**

A `mousemove` event listener maps `clientX` and `clientY` to a `translate()` transform at 0.2× scale. The result is a floating element that moves with the cursor but at a fraction of its speed, creating a foreground/background depth effect.

**Locomotive + ScrollTrigger bridge**

Locomotive Scroll hijacks the native scroll container, so GSAP's `ScrollTrigger` needs to be told where to read scroll position from. The `scrollerProxy` pattern proxies `scrollTop` and `getBoundingClientRect` from Locomotive's virtual container to GSAP — the correct pattern for combining both libraries without position jitter.

**Click-to-spin micro-interaction**

`.class` elements rotate `1440deg` (4 full turns) on click via CSS transition — a small detail that rewards exploration and signals attention to interaction design.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| GSAP 3.11 + ScrollTrigger | Timeline animation engine; `scrub` ties progress to scroll position |
| Locomotive Scroll 3.5 | Virtual scroll with inertia |
| Vanilla JavaScript | Zero framework overhead; direct DOM manipulation |
| HTML + CSS | Semantic markup, custom layout |

---

## Getting Started

No build step required. Open directly in a browser or serve with any static host.

```bash
git clone https://github.com/abhijeet-builds/gsap-design-studio.git
cd gsap-design-studio

# Option 1 — open directly
open index.html

# Option 2 — local dev server (VS Code Live Server or npx serve)
npx serve .
```

---

## Project Structure

```
gsap-design-studio/
├── index.html      # Markup + CDN script imports
├── style.css       # All styles
├── script.js       # GSAP animations + Locomotive Scroll setup
└── fav/            # Favicon assets
```

---

## Deploy

Drag and drop the entire folder to [Netlify](https://netlify.com) or [Vercel](https://vercel.com). No build command needed — set publish directory to `/`.

---

## License

MIT
