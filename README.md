<div align="center">

# 🩺 DevReady: landing page

### The website for [DevReady](https://github.com/Evalogical-Inc/devReady), the read-only environment doctor for developers and AI coding agents.

**Live site: [devready-ten.vercel.app](https://devready-ten.vercel.app/)**

[![Website](https://img.shields.io/badge/website-devready--ten.vercel.app-ff6a35)](https://devready-ten.vercel.app/)
[![PyPI](https://img.shields.io/pypi/v/devready-cli)](https://pypi.org/project/devready-cli/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/Evalogical-Inc/devReady/blob/main/LICENSE)
![Static site](https://img.shields.io/badge/build-none-brightgreen)

</div>

---

## What is DevReady?

DevReady is a free, open-source (MIT), zero-dependency CLI. It compares the Node, Python and Git on your machine with what a project declares (`.nvmrc`, `package.json` engines, `requires-python`, ...) and tells you exactly what to fix. It never installs, edits or deletes anything, makes no network calls and sends no telemetry.

It is built for humans, CI pipelines and AI coding agents (Claude Code, Codex, any MCP client).

```bash
pipx install devready-cli
devready check
```

| | |
|---|---|
| 🎯 **Project-aware** | Reads the versions your project pins, not just "is Node installed?" |
| 🔒 **Read-only** | No installs, no edits, no network, no telemetry |
| 🤖 **Agent-ready** | JSON output, Claude Code plugin, MCP server, `AGENTS.md` |
| 📦 **Zero dependencies** | Python standard library only, Python 3.10+ |

Full docs, usage, exit codes and roadmap live in the main repo: **[Evalogical-Inc/devReady](https://github.com/Evalogical-Inc/devReady)**. If it saves you an afternoon, a ⭐ there helps others find it.

## About this repo

This repo is only the marketing site. The CLI, plugin and MCP server live in the [main repo](https://github.com/Evalogical-Inc/devReady) and on [PyPI](https://pypi.org/project/devready-cli/).

The page covers:

- Hero with a copyable install command and a simulated terminal run (clearly labelled as a simulation)
- Feature overview, "use it with AI agents" setup, FAQ and a link to Evalogical
- SEO and sharing: Open Graph card, JSON-LD (software, organisation, FAQ), `sitemap.xml`, `robots.txt`

## Built with

| | |
|---|---|
| **HTML, CSS, vanilla JS** | A single static `index.html`. No framework, no bundler, no build step |
| **[Lucide](https://lucide.dev/)** | Icons, loaded from unpkg and pinned to 0.469.0 |
| **[DM Sans / DM Serif Display](https://fonts.google.com/)** | Typography via Google Fonts |
| **[Vercel](https://vercel.com/)** | Hosting; `vercel.json` serves `public/` and sets security headers (`nosniff`, `X-Frame-Options: DENY`, strict referrer policy) |

Animations (scroll reveals, terminal demo) are disabled under `prefers-reduced-motion`. The page is keyboard navigable and has a skip link.

## Project structure

```text
public/
  index.html     the whole site (markup, styles, scripts, JSON-LD)
  og.png         social share card
  favicon.svg
  robots.txt
  sitemap.xml
vercel.json      output directory + security headers
```

## Run locally

No install needed. Serve the folder with anything:

```bash
python -m http.server 8000 --directory public
# open http://localhost:8000
```

## Deploy

Deploys to Vercel from this repo with no build command; the output directory is `public` (set in `vercel.json`). Any static host works the same way: publish the contents of `public/`. Because the page uses root paths (`/og.png`), serve it from a domain root, not a sub-path.

## Contributing

Typos, accessibility fixes and copy improvements are welcome: open an issue or a PR. For anything about the CLI itself, use the [DevReady issue tracker](https://github.com/Evalogical-Inc/devReady/issues/new/choose) and see its [CONTRIBUTING.md](https://github.com/Evalogical-Inc/devReady/blob/main/CONTRIBUTING.md).

When you ship a new DevReady release, update `softwareVersion` in the JSON-LD block of `index.html` to match PyPI.

## About Evalogical

DevReady is built and maintained by [Evalogical](https://evalogical.com/), a software company offering AI-enabled product engineering, custom software and IT services.

## License

[MIT](https://github.com/Evalogical-Inc/devReady/blob/main/LICENSE) © Evalogical Inc
