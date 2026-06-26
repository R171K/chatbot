# Radheshyam Steel & Crokri — Reels Website

Instagram Reels product showcase, hosted on Vercel.

---

## Option A — Deploy in 2 minutes with Vercel CLI (easiest)

### 1. Install Node.js (if not already installed)
Download from https://nodejs.org — choose the LTS version.

### 2. Install Vercel CLI
```bash
npm install -g vercel
```

### 3. Open Terminal and go to this folder
```bash
cd ~/Downloads/reels-website
```

### 4. Deploy
```bash
vercel --prod
```

- It will ask you to log in (opens browser) — sign in with Google/GitHub/Email
- Accept all defaults (press Enter for every prompt)
- At the end it prints your live URL, e.g. `https://reels-website.vercel.app`

That's it. Every time you edit `index.html` and run `vercel --prod` again, it updates the live site.

---

## Option B — Auto-deploy via GitHub (every push goes live automatically)

This uses the `.github/workflows/deploy.yml` file already in this folder.

### Step 1 — Create a GitHub repository
1. Go to https://github.com/new
2. Name it `reels-website`, set it to **Private**
3. Click **Create repository**

### Step 2 — Push this folder to GitHub
Open Terminal in this folder and run:
```bash
git init
git add .
git commit -m "initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/reels-website.git
git push -u origin main
```
Replace `YOUR_USERNAME` with your GitHub username.

### Step 3 — Connect the repo to Vercel
1. Go to https://vercel.com → **Add New Project**
2. Click **Import Git Repository** → select `reels-website`
3. Click **Deploy** (leave all settings as default)
4. Note the **Project ID** and **Org ID** shown in the project settings (you'll need these next)

### Step 4 — Get your Vercel Token
1. Go to https://vercel.com/account/tokens
2. Click **Create Token** → name it `github-actions` → click **Create**
3. Copy the token — you only see it once

### Step 5 — Add secrets to GitHub
1. Go to your GitHub repo → **Settings** → **Secrets and variables** → **Actions**
2. Add these three secrets:

| Secret name       | Value                                  |
|-------------------|----------------------------------------|
| `VERCEL_TOKEN`    | The token you just copied              |
| `ORG_ID`          | Found in Vercel → Settings → General   |
| `PROJECT_ID`      | Found in Vercel → Project → Settings   |

### Step 6 — Done
Now every time you push a change to GitHub, the site updates automatically within ~30 seconds.

---

## Updating the site

Edit `index.html` then:

**CLI method:**
```bash
vercel --prod
```

**GitHub method:**
```bash
git add index.html
git commit -m "update reels"
git push
```

---

## File structure

```
reels-website/
├── index.html                   # The reels showcase page
├── vercel.json                  # Vercel routing config
├── README.md                    # This file
└── .github/
    └── workflows/
        └── deploy.yml           # GitHub Actions auto-deploy
```
