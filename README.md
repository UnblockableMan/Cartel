# ReduX

<div align="center">

**static · fast · proxy**

A static, fast web proxy built by **viroda1** & **UnblockableMan**.
Runs entirely in your browser — **no server backend required**. Works on GitHub Pages, Cloudflare Pages, Netlify, Vercel, or any static host.

[![Version](https://img.shields.io/badge/version-1.0-00e5ff?style=flat-square)](#)
[![License](https://img.shields.io/badge/license-AGPL--3.0-3b82f6?style=flat-square)](#license)
[![Static](https://img.shields.io/badge/static-100%25-8b5cf6?style=flat-square)](#)
[![Authors](https://img.shields.io/badge/authors-viroda1%20%26%20UnblockableMan-00e5ff?style=flat-square)](#)

</div>

---

## ✦ What is ReduX?

ReduX is a single-page static web proxy. Everything runs in the browser — a Scramjet service worker intercepts requests and proxies them through a WISP transport, so ReduX can be hosted on **any static file host** (including GitHub Pages). No Node, no Express, no wisp server to run yourself.

Open the page, type a URL in the search bar, hit **Go** — you're in.

### Layout

```
┌──────────────────────────────────────┐
│           ReduX (title + tag)         │
│  built by viroda1 & UnblockableMan    │
├──────────────────────────────────────┤
│  [ 🔍 search the web or URL  ▾ DDG ]  │
├──────────────────────────────────────┤
│  Home · Games · Apps · Settings · ⚡  │  ← toolbar
├──────────────────────────────────────┤
│                                       │
│   active view (home / games / apps…)  │
│                                       │
└──────────────────────────────────────┘
```

### Features

- 🚀 **100% static** — works on GitHub Pages / Cloudflare Pages / Netlify / Vercel
- 🛡 **Scramjet + WISP** — service-worker-based proxy, no backend needed
- 🎮 **200+ games** — local Unity/HTML5 ports + remote titles via proxy
- 🧩 **Apps shelf** — PS5 UI, Spotify, Web Desktop, Arc AI, Chat, Files, Extensions, Anchor OS
- 🎨 **Theming** — accent color picker, dark/midnight/deep-blue/black modes
- ⚡ **Server switching** — ping WISP servers, auto-switch to the lowest-latency one, add your own
- 🔖 **Shortcuts** — quick links to YouTube, Reddit, Twitter, Discord, Spotify, Twitch, GitHub, Wikipedia
- 📦 **PWA installable** — manifest + icons + offline-capable SW

---

## 🚀 Deploy

### GitHub Pages (zero config)

1. Fork this repo
2. Settings → Pages → Source: `main` branch, `/` root
3. Wait ~30s, your ReduX is live at `https://<your-name>.github.io/<repo-name>/`

### Other static hosts

| Host | One-click |
|------|-----------|
| Cloudflare Pages | Connect repo, no build command, output dir = `/` |
| Netlify | Drag-and-drop the repo folder onto netlify.com/drop |
| Vercel | Import repo, framework = "Other", no build step |

### Run locally

```bash
git clone https://github.com/UnblockableMan/Cartel.git
cd Cartel
npx serve .
# → http://localhost:3000
```

> **Note**: You can also open `index.html` directly via `file://`, but service workers require http(s). Use `npx serve .` for the proxy to work.

---

## 🎮 Games

Browse **200+ games** in the Games tab. Filter by category (all / popular / multiplayer / 3d / apps), search by name, click to launch.

- **LOCAL** badge = the game runs as a static HTML file (Unity web player, HTML5 port) — opens in an in-page fullscreen viewer, no proxy roundtrip
- No badge = the game is on a remote URL and goes through the Scramjet proxy

Add your own: drop an HTML file in `games/` and append to `assets/g.json`:

```json
{
  "name": "My Game",
  "link": "games/my-game.html",
  "image": null,
  "categories": ["all"],
  "local": true
}
```

When `image` is `null`, ReduX renders a gradient placeholder with the game's initials.

---

## 🧩 Apps

Built-in apps live in `apps/`:

| App | File | Description |
|---|---|---|
| PS5 UI | `app-ps5.html` | PlayStation 5-style launcher chrome |
| Spotify | `app-spotify.html` | Embedded music player |
| Web Desktop | `app-web.html` | Full window manager in a tab |
| Arc AI | `arc-ai.html` | Quick AI assistant panel |
| Chat | `chat.html` | Embedded chat |
| Files | `files.html` | File browser |
| Extensions | `extensions.html` | Browser extensions manager |
| Anchor OS | `anchor.html` | Anchor desktop variant |

---

## ⚙️ Proxy Stack

| Layer | What | Source |
|---|---|---|
| Service worker | Scramjet SW intercepts all fetches, routes proxied ones | [`sw.js`](sw.js) |
| Transport | Bare-Mux → WISP websocket | [`bareworker.js`](bareworker.js) |
| Frontend | Single-file HTML/CSS/JS, no build step | [`index.html`](index.html) |
| Scramjet runtime | Loaded from CDN (no vendored bundles) | jsdelivr `Destroyed12121/Staticsj` |

Default WISP servers are listed in `index.html` (search for `DEFAULT_WISP_SERVERS`). Add your own in **Settings → Proxy Server**.

---

## 🎨 Brand

The ReduX mark is a stylized **R** with a cyan-to-violet gradient and three speed slashes.

Source files under `assets/brand/`:

- `logo.svg` / `logo.png` — main logo (PNG renders up to 512×512)
- `favicon.svg` / `favicon.ico` / `favicon-{16,32,48,64,180,192}.png`
- `banner.svg` / `banner.png` — OG / Twitter card (1200×400 / 2400×800)
- `icon-maskable-512.png` — PWA maskable icon
- `apple-touch-icon.png`

Accent palette: `#00e5ff → #3b82f6 → #8b5cf6`.

---

## 🤝 Contributing

PRs welcome. Keep dependencies minimal. Keep the front-end a single static file. Don't add a build step.

---

## 📜 License

AGPL-3.0-only. Fork it, host it, modify it — but keep the source open for the next person.

---

<div align="center">

**built by viroda1 & UnblockableMan**

*ReduX — static · fast · proxy*

</div>
