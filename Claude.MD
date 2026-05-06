# CLAUDE.md — Project Instructions

## Project overview

This is a static web project built from a Claude artifact. It is deployed via GitHub → Vercel (auto-deploy on push to `main`).

## Tech stack

- **Frontend**: HTML
- **Hosting**: Vercel
- **Repo**: https://github.com/covifranklin/Glass-Squid-Systems-Website.git
- **Live URL**: 

## Project structure

```
/
├── CLAUDE.md          ← you are here
├── index.html         ← entry point (or src/App.jsx for React)
├── src/               ← source files
├── public/            ← static assets
├── package.json       ← if using Node/React
└── vercel.json        ← Vercel config (optional)
```

## Local dev

```bash
# Install deps (if applicable)
npm install

# Run dev server
npm run dev
# or for plain HTML: just open index.html in browser
```

## Deployment workflow

Every push to `main` triggers a Vercel auto-deploy. The workflow is:

1. Make changes
2. `git add .`
3. `git commit -m "describe your change"`
4. `git push origin main`
5. Vercel deploys automatically (takes ~30–60 seconds)

To deploy manually via Vercel CLI: `vercel --prod`

## When Claude Code is helping with this project

- Always commit working code — don't push broken states to `main`
- Run `npm run build` (if applicable) before pushing to catch build errors
- Keep `.env` files out of git — use Vercel's environment variable dashboard for secrets
- If adding new dependencies, run `npm install <package>` and commit the updated `package.json` and `package-lock.json`


## One-time setup checklist (do this once, then ignore)

- [ ] Create GitHub repo and push initial code
- [ ] Connect repo to Vercel (vercel.com → Add New Project)
- [ ] Install Vercel CLI: `npm i -g vercel` and run `vercel login`
- [ ] Set any environment variables in Vercel dashboard (not in code)
- [ ] Confirm auto-deploy is working by pushing a small change