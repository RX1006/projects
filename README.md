# Strumly — Ukulele Chord Generator

AI-powered ukulele chord charts with lyrics, diagrams, and strumming patterns.

## Project Structure

```
strumly/
├── api/
│   └── generate.js      ← Vercel serverless function (proxies Anthropic API)
├── public/
│   └── index.html       ← Frontend (all CSS + JS in one file)
├── vercel.json          ← Vercel config
└── README.md
```

## Deploying to Vercel

### 1. Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/strumly.git
git push -u origin main
```

### 2. Import to Vercel
- Go to https://vercel.com/new
- Import your GitHub repo
- Framework Preset: **Other**
- Root Directory: leave blank (uses project root)
- Click **Deploy**

### 3. Add your API Key ← THIS IS THE CRITICAL STEP
After deploy (or before), go to:

**Vercel Dashboard → Your Project → Settings → Environment Variables**

Add:
| Name | Value |
|------|-------|
| `ANTHROPIC_API_KEY` | `sk-ant-...your key...` |

Then **Redeploy** the project (Deployments tab → ··· → Redeploy).

> Get your API key at: https://console.anthropic.com/

### 4. Done!
Your app is live. The `/api/generate` serverless function handles all Anthropic API calls server-side, so your key is never exposed to the browser.

## Local Development

```bash
npm i -g vercel
vercel dev
```

This starts a local server with the serverless functions working. Set your key in a `.env.local` file:
```
ANTHROPIC_API_KEY=sk-ant-...
```
