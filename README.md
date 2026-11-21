# Vrishank Warrier — Portfolio

My personal portfolio: a software engineer focused on systems and infrastructure, across backend, cloud and DevOps.

**Live site: [vrishank.shadovxw.me](https://vrishank.shadovxw.me/)**

![Portfolio preview](public/og-image.jpg)

The landing page is told as a build pipeline. Each section is one stage, from `boot` to `deploy`:

| Stage | Section | What's there |
| --- | --- | --- |
| `boot` | Hello | Who I am, in one screen |
| `build` | Projects | Things I've built and shipped |
| `install` | Stack | The tools behind them |
| `log` | Experience | Where I've put them to work |
| `whoami` | About | The person behind the commits |
| `deploy` | Contact | A terminal-style contact form |

## Features

- **Swarm rebuild:** a crowd of small agent cursors builds the real page in front of you. On a first visit it builds the first screen, then each section as you scroll to it. Built sections stay built. Run the full version any time from the command palette (**Rebuild**) or with <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>S</kbd>.
- **Command palette:** <kbd>Ctrl</kbd>/<kbd>⌘</kbd>+<kbd>K</kbd> opens it. Search sections, copy my email, download the resume, or open GitHub and LinkedIn. <kbd>G</kbd> then a letter jumps straight to a section (<kbd>P</kbd> projects, <kbd>S</kbd> stack, <kbd>E</kbd> experience, <kbd>A</kbd> about, <kbd>C</kbd> contact).
- **Boot intro:** a glitch-style preloader that plays once per session.
- **3D and motion:** three.js / React Three Fiber scenes, GSAP and Framer Motion animations, and Lenis smooth scrolling.
- **Terminal contact form:** type `help` in the footer terminal, or just send a message (delivered through Web3Forms).
- **UI sounds:** subtle hover and click sounds, mutable from the command palette.
- **Respects your settings:** with `prefers-reduced-motion` on, the intro and swarm rebuild are skipped and the 3D scenes fall back to lighter versions. Phones get the lighter versions too.

## Tech stack

| Area | Tools |
| --- | --- |
| Framework | React 19, React Router 7, Vite 7 |
| Styling | Tailwind CSS 4 |
| Motion | Framer Motion, GSAP, Lenis |
| 3D | three.js, React Three Fiber, Drei, Spline |
| Other | Web3Forms (contact form), use-sound, Lucide icons, Vercel Analytics |
| Hosting | Cloudflare Workers (static assets), or Docker + Nginx |

## Getting started

You need **Node.js 20.19 or newer** (Vite 7 requires it).

```bash
git clone https://github.com/shadovxw/portfolio.git
cd portfolio
npm install
```

Copy the example environment file and add a [Web3Forms](https://web3forms.com) access key so the contact form can send messages:

```bash
cp .env.example .env
```

```env
VITE_WEB3FORMS_KEY=your-access-key
```

Start the dev server:

```bash
npm run dev
```

### Scripts

| Command | What it does |
| --- | --- |
| `npm run dev` | Start the dev server with hot reload |
| `npm run build` | Build for production into `dist/` |
| `npm run preview` | Serve the production build locally |
| `npm run lint` | Run ESLint |

## Deployment

### Cloudflare Workers

`wrangler.jsonc` serves `dist/` as static assets, with single-page-app fallback so routes like `/projects` load correctly.

```bash
npm run build
npx wrangler deploy
```

### Docker

The `Dockerfile` builds the site with Node 22 and serves it with Nginx. `nginx.conf` adds gzip, long-lived caching for hashed assets, and the SPA fallback.

```bash
docker build -t portfolio .
docker run -p 8080:80 portfolio
```

The site is then at http://localhost:8080.

## Project structure

```text
src/
├── pages/           Landing page, project archive, 404
├── components/
│   ├── sections/    Projects, Stack, Experience, About
│   ├── story/       The build-pipeline stages and section rail
│   ├── effects/     Swarm rebuild, 3D scenes, text and scroll effects
│   ├── system/      Preloader, custom cursor, system monitor
│   ├── layout/      Nav, footer, terminal
│   └── ui/          Command palette, contact form, cards, buttons
├── hooks/           Shared state (sound, matrix mode)
└── utils/           Sound effects, view transitions, helpers
public/              Favicon, social preview image, sounds, robots.txt, sitemap
```

## Credits

UI sounds in `public/sounds/ui` are by [Kenney](https://kenney.nl) (see `LICENSE-kenney.txt`).

## Contact

- Website: [vrishank.shadovxw.me](https://vrishank.shadovxw.me/)
- GitHub: [@shadovxw](https://github.com/shadovxw)
- LinkedIn: [Vrishank Warrier](https://www.linkedin.com/in/vrishank-warrier-ab529628a/)

<details>
<summary>Psst</summary>

Type `matrix` anywhere on the page.

</details>
