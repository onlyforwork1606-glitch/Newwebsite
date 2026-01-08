# Newwebsite

![Repo size](https://img.shields.io/github/repo-size/onlyforwork1606-glitch/Newwebsite?style=flat) ![Top language](https://img.shields.io/github/languages/top/onlyforwork1606-glitch/Newwebsite?style=flat) ![License](https://img.shields.io/github/license/onlyforwork1606-glitch/Newwebsite?style=flat)

A polished, developer-friendly website starter built with Vite + React and organized for fast iteration, theming, and deployment. This README is tailored to the repository contents and includes practical, interactive steps so you can preview, edit, and ship quickly.

Live demo (if published)
- GitHub Pages (example): https://onlyforwork1606-glitch.github.io/Newwebsite
- Instant edit: open this repo in CodeSandbox or StackBlitz (see "Play online" below)

Table of contents
- About
- Quick interactive demo
- Quick start (local)
- Scripts & developer commands
- Project overview (what's in the repo)
- Key technologies & dependencies
- Theming & quick UI changes (interactive)
- Subprojects & deployment notes
- Contributing, issues & support
- License & acknowledgements

About
This repository is a modern frontend scaffold intended for landing pages, small SaaS sites, portfolio sites, or prototypes. The project is built with Vite and React, uses Tailwind-related tooling, and includes accessible, reusable UI patterns. It is intentionally lightweight but production-ready.

Quick interactive demo
- Open and edit in the browser:
  - CodeSandbox: https://codesandbox.io/s/github/onlyforwork1606-glitch/Newwebsite
  - StackBlitz: https://stackblitz.com/github/onlyforwork1606-glitch/Newwebsite
- Preview instantly locally:
  ```bash
  git clone https://github.com/onlyforwork1606-glitch/Newwebsite.git
  cd Newwebsite
  npm install
  npm run dev
  # Open http://localhost:5173 (Vite default) or the address shown in the terminal
  ```

Quick start (local)
1. Ensure Node.js (v18+) and npm are installed.
2. Clone and install:
   ```bash
   git clone https://github.com/onlyforwork1606-glitch/Newwebsite.git
   cd Newwebsite
   npm install
   ```
3. Run the development server:
   ```bash
   npm run dev
   ```
4. Build for production:
   ```bash
   npm run build
   ```
5. Preview a production build locally:
   ```bash
   npm run preview
   ```
If you prefer not to use Node, you can also open the root `index.html` directly or serve the folder with a static server:
```bash
python -m http.server 8000
# then open http://localhost:8000
```

Scripts & developer commands
These commands come directly from the repository package.json:
- npm run dev — start Vite dev server
- npm run build — build production bundle with Vite
- npm run preview — preview the production build (Vite preview)
- npm run lint — run ESLint (if set up)

Project overview (what's in this repo)
Top-level files & folders:
- index.html — root HTML (entry for static preview)
- package.json & package-lock.json — dependencies and scripts
- vite.config.js — Vite config
- src/ — React source code (components, pages, styles)
- public/ — static assets served as-is
- funkyfabrics/ and funckyfabrics/ — two related subprojects (each has its own package.json and Wrangler deploy scripts)
- Deployement.md — notes on deploying (typo preserved — consider renaming to DEPLOYMENT.md)
- README.md — this file

Open files worth reviewing first:
- package.json — lists main dependencies and scripts
- vite.config.js — check custom aliases, base path, or plugin config
- src/ — start here to edit pages & components
- public/ — add static images and assets here

Key technologies & dependencies (from package.json)
- Framework & tooling:
  - Vite (dev/build tooling)
  - React 19 (UI)
  - @vitejs/plugin-react
- Styling & UI:
  - tailwindcss (tailwind tooling)
  - @tailwindcss/vite
  - tw-animate-css
- Component primitives & utilities:
  - Radix UI (@radix-ui/*)
  - lucide-react (icons)
  - class-variance-authority, clsx
- State & data:
  - zustand (state)
  - react-hook-form (forms)
- Routing & integrations:
  - react-router-dom
  - axios
  - @googlemaps/react-wrapper + @types/google.maps
- Carousel & UI niceties:
  - embla-carousel-react, embla-carousel-autoplay
- Notifications:
  - sonner
- Dev & linting:
  - eslint, @eslint/js, eslint plugins

Theming & quick UI changes (interactive)
This project uses CSS variables (and likely Tailwind utilities). You can quickly change the brand colors and theme with these steps:

1. Locate the global CSS (likely in src/styles or public/css). Example theme variables:
```css
:root {
  --bg: #0b1220;
  --card: #0f172a;
  --accent: #7c3aed;
  --text: #e6eef8;
}
:root.light { --bg: #ffffff; --text: #0b1220; --accent: #0b69ff; }
```

2. Quick theme toggle (vanilla JS) — add this to a small script:
```html
<button id="themeToggle">Toggle theme</button>
<script>
const btn = document.getElementById('themeToggle');
btn.addEventListener('click', () => {
  document.documentElement.classList.toggle('light');
  localStorage.theme = document.documentElement.classList.contains('light') ? 'light' : 'dark';
});
if (localStorage.theme === 'light') document.documentElement.classList.add('light');
</script>
```

3. Tailwind users: change colors in tailwind.config.js or use CSS variables mapped to Tailwind via `theme.extend.colors`.

Subprojects & deployment notes
There are two subfolders with their own package.json:
- funkyfabrics/
- funckyfabrics/

Both contain scripts for Vite and Wrangler deployment:
- preview: builds and runs `wrangler pages dev`
- deploy: builds and runs `wrangler pages deploy`

If you plan to deploy to Cloudflare Pages (using Wrangler), make sure:
- You have wrangler configured (wrangler.toml / wrangler.jsonc)
- `wrangler` is installed and authenticated: `npm i -g wrangler && wrangler login`
- You may need to set the publish directory or build command in Cloudflare Pages settings.

Other common deployment targets:
- Vercel — connect GitHub repo and set build command: `npm run build`, output directory: `dist`
- Netlify — connect repo and set build command `npm run build` and publish `dist`
- GitHub Pages — use a GH Action or publish `dist` to `gh-pages` branch

Accessibility & performance checklist
- Use semantic HTML (header, nav, main, footer)
- Provide descriptive alt text for all images
- Ensure sufficient color contrast (WCAG AA)
- Test keyboard navigation and focus outlines
- Run Lighthouse and optimize images (WebP/AVIF), lazy-load offscreen images

Common tasks & examples
- Add a new page: create src/pages/YourPage.jsx and add a route in src/App.jsx (react-router)
- Add a global component: src/components/ui/Button.jsx (use class-variance-authority for variants)
- Add a font: add to index.html `<link>` to Google Fonts and reference in CSS variables

Contributing, issues & support
Contributions are welcome!
- Open an issue for bugs, enhancements, or questions: https://github.com/onlyforwork1606-glitch/Newwebsite/issues/new
- To contribute:
  1. Fork the repo
  2. Create a branch: `git checkout -b feat/your-feature`
  3. Commit, push, and open a Pull Request describing intent and screenshots

Suggested labels to add (for maintainers):
- good first issue
- help wanted
- enhancement
- bug

License & acknowledgements
This repo currently does not include a LICENSE file (confirm and add one if needed). Recommended: MIT.

Acknowledgements
- Built with Vite, React, Tailwind, and many open-source primitives (Radix, Embla, Sonner).
- Thanks to the open-source community for reusable components and examples.

What's next (recommended small improvements)
- Add a LICENSE file (MIT or your preferred license)
- Add screenshots to `/public/assets` and update README preview
- Add CONTRIBUTING.md + CODE_OF_CONDUCT.md for collaborators
- Enable GitHub Pages or add a CI deploy action for automated deploys
- Fix the filename typo: rename `Deployement.md` → `DEPLOYMENT.md`

Need me to:
- Add a polished screenshot block and auto-generated badges (I can create or update images),
- Add a LICENSE file (MIT) and open a pull request with the change,
- Or create a small GitHub Action workflow to auto-deploy the `build` to GitHub Pages or Cloudflare Pages.

Tell me which of those you'd like and I will prepare the files and the PR for you.
