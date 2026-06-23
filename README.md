# Nikunj Zapadiya — Premium Portfolio

Awwwards-level portfolio built with Next.js 15, Three.js, GSAP, Framer Motion & Lenis.

## Tech Stack
- **Next.js 15** — App Router, Server Components, dynamic imports
- **TypeScript** — Strict mode
- **Tailwind CSS** — Custom design tokens, dark futuristic theme
- **Framer Motion** — Page transitions, scroll animations, reveals
- **Three.js / React Three Fiber** — Interactive 3D hero scene, 3D gallery
- **GSAP** — Text reveals, scroll-triggered effects
- **Lenis** — Buttery smooth scrolling

## Quick Start

```bash
# Install dependencies
npm install --legacy-peer-deps

# Development server
npm run dev

# Production build
npm run build && npm start
```

## Deploy to Vercel

### Option A — Vercel CLI (Recommended)
```bash
npm i -g vercel
vercel login
vercel --prod
```

### Option B — GitHub + Vercel Dashboard
1. Push this repo to GitHub
2. Go to vercel.com → New Project
3. Import your GitHub repo
4. Framework preset: **Next.js** (auto-detected)
5. No env vars needed for basic deployment
6. Click **Deploy**

## Project Structure

```
src/
├── app/
│   ├── layout.tsx       # Root layout with metadata + fonts
│   └── page.tsx         # Main page assembling all sections
├── components/
│   ├── 3d/
│   │   └── HeroScene.tsx        # Three.js interactive scene
│   ├── layout/
│   │   ├── Navigation.tsx       # Sticky nav with mobile menu
│   │   ├── SmoothScroll.tsx     # Lenis scroll provider
│   │   └── Footer.tsx
│   ├── sections/
│   │   ├── Hero.tsx             # Fullscreen 3D hero
│   │   ├── About.tsx            # Bio + skill bars
│   │   ├── Services.tsx         # 5 service cards
│   │   ├── Projects.tsx         # Project case-study grid
│   │   ├── Reel.tsx             # Motion reel video player
│   │   ├── UIUXCaseStudies.tsx  # Expandable case studies
│   │   ├── Gallery3D.tsx        # Interactive 3D viewer
│   │   └── Contact.tsx          # Contact form + social
│   └── ui/
│       ├── CustomCursor.tsx     # Magnetic custom cursor
│       ├── Loader.tsx           # Animated page loader
│       ├── MarqueeBand.tsx      # Scrolling text band
│       └── FloatingParticles.tsx # Canvas particle field
├── styles/
│   └── globals.css              # Design tokens, utilities
└── lib/                         # (utilities, if extended)
```

## Customization

### Colors
Edit `tailwind.config.ts` — the neon palette:
```ts
neon: {
  violet: '#7c3aed',   // primary brand
  cyan: '#06b6d4',     // secondary accent
  magenta: '#d946ef',  // highlight
  amber: '#f59e0b',    // warm accent
}
```

### Adding Real Projects
In `src/components/sections/Projects.tsx`, update the `projects` array with real titles, descriptions, and replace the placeholder visual divs with `<Image>` components pointing to your actual project screenshots.

### Adding Real Video
In `src/components/sections/Reel.tsx`, replace the placeholder div inside the video container with an actual `<video>` element or embed an iframe from YouTube/Vimeo.

### Contact Form
The current form simulates sending. To wire it up:
- Add a `POST /api/contact` route in `src/app/api/contact/route.ts`
- Use Resend, EmailJS, or Nodemailer to send emails

### Fonts
Currently loaded via Google Fonts CDN (Syne + Space Grotesk + JetBrains Mono). For production, use `next/font` for better performance:

```ts
import { Syne } from 'next/font/google'
const syne = Syne({ subsets: ['latin'], variable: '--font-display' })
```

## Performance Tips
- All heavy sections use `dynamic()` imports with lazy loading
- 3D canvas uses `dpr={[1, 1.5]}` to cap pixel ratio
- Particles canvas is lightweight canvas2D
- Images should use `next/image` with proper `sizes` props
- Target: 90+ Lighthouse score on desktop

## License
Personal portfolio — all design and code by Nikunj Zapadiya.
