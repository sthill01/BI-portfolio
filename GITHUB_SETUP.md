# Push to GitHub — step-by-step

This folder isn't a git repo yet. Here's how to turn it into one and push it up.

## One-time GitHub setup

1. **Create a new GitHub repo** at https://github.com/new
   - Name suggestion: `dashboard-portfolio` or `bi-portfolio`
   - Visibility: **Public** (so Netlify/GitHub Pages can serve it and recruiters can see it)
   - Do NOT initialize with a README — we already have one

2. **GitHub will show you a command block.** You want the one under *"…or push an existing repository from the command line."*

## In a terminal on your computer

Open PowerShell or Terminal, then:

```bash
cd "C:/Users/<your-user>/<path-to-Career>/Portfolio"
# OR on Mac: cd ~/path-to-Career/Portfolio

git init -b main
git add .
git commit -m "Initial commit: BI dashboard portfolio with brand-styled layouts"
git remote add origin https://github.com/<your-github-username>/dashboard-portfolio.git
git push -u origin main
```

Replace `<your-github-username>` with your actual GitHub handle.

## Then connect Netlify to your GitHub repo

1. Go to https://app.netlify.com
2. **Add new site → Import an existing project → GitHub**
3. Pick your new `dashboard-portfolio` repo
4. **Base directory:** leave blank
5. **Build command:** leave blank (no build step)
6. **Publish directory:** `dashboards`
7. Deploy.

Your portfolio URL will look like `https://<random-name>.netlify.app/` — you can set a custom domain in Netlify site settings later.

## Updating the site

Any time you make a change:

```bash
git add .
git commit -m "Update <what you changed>"
git push
```

Netlify will auto-deploy within ~30 seconds.

## Sharing it

Pin the repo to your GitHub profile. Add the Netlify URL to:
- Your resume (under Portfolio / Projects)
- LinkedIn headline or About section
- Email signature

It works as a talking point in interviews: **"Here's four dashboards I rebuilt from past work — each matched to the company's brand language so recruiters see the range."**
