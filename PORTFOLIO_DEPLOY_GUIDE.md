# Portfolio Deploy Guide

A beginner-friendly, step-by-step for pushing updates to your portfolio and getting them live at `https://bi-portfolio.sthill01.workers.dev/`.

**Stack you're using:**

- **GitHub** — stores your code. Think of it as "Google Drive for developers," with version history.
- **GitHub Desktop** — a friendly app that lets you push code to GitHub without typing git commands.
- **Cloudflare Pages** — watches your GitHub repo and automatically publishes the site whenever you push.

The big idea: **you change files locally → GitHub Desktop pushes them to GitHub → Cloudflare Pages sees the push and rebuilds the live site automatically**. There's nothing to click on Cloudflare after the first setup.

---

## Part 1 — Pushing updates with GitHub Desktop

This is the workflow you'll use every time you change anything in the `Portfolio/` folder.

### Step 1. Open GitHub Desktop

- Launch **GitHub Desktop**.
- In the top-left, make sure the current repository is your portfolio repo (something like `dashboard-portfolio` or `bi-portfolio`).
  - If it isn't, click the dropdown and pick the right one.

### Step 2. Review your changes

- In the left sidebar you'll see a **Changes** tab. Click it.
- You should see a list of changed files (blue `M` = modified, green `+` = new file, red `−` = deleted).
- Click any file to see a side-by-side diff of what changed (red = removed, green = added).
- **This is your sanity check.** Scroll through to make sure:
  - Only files you meant to change show up
  - No files contain personal information you don't want public (passwords, API keys, etc.)

### Step 3. Write a commit message

At the bottom-left of GitHub Desktop you'll see two text fields:

- **Summary** (required) — one short sentence describing the change, e.g.
  - `Update Healthicity palette to real brand colors`
  - `Add new homepage and restructure to single index`
  - `Fix topbar links across all portfolio pages`
- **Description** (optional) — any extra detail. Usually leave blank.

Then click the blue **"Commit to main"** button. (`main` is the branch — it's fine to commit straight to main for a personal portfolio.)

### Step 4. Push to GitHub

- After committing, the top bar changes to show **"Push origin"** with a number next to it (e.g., `1 commit`).
- Click **"Push origin"**.
- Wait a few seconds. When it finishes, your changes are on GitHub.

That's the whole push flow. You just moved your local changes up to GitHub.

---

## Part 2 — Cloudflare Pages auto-deploys

This part is automatic — but you'll want to know how to check that it worked.

### Step 1. Log in to Cloudflare

- Go to https://dash.cloudflare.com/
- Log in with the account you used to set up the portfolio.

### Step 2. Find your Pages project

- In the left sidebar, click **Workers & Pages** (or **Compute** → **Workers & Pages** depending on the nav).
- Click your project — it'll be named something like `bi-portfolio`.

### Step 3. Watch the deployment

- You'll land on the **Deployments** tab.
- The top-most row is your latest deployment. When you just pushed, you'll see:
  - **Status:** `Building` (yellow) → then `Queued` → then `Success` (green), usually within 1–2 minutes.
- Click the deployment row to see build logs if you're curious (you rarely need to).

### Step 4. Verify on the live site

Once status is green:

1. Open `https://bi-portfolio.sthill01.workers.dev/` in a **private / incognito window** (so you're not seeing a cached version).
2. Hard-refresh anyway: **Ctrl + Shift + R** (Windows) or **Cmd + Shift + R** (Mac).
3. Click through the changes you made to confirm they're live.

---

## Post-deploy verification checklist

After any significant update, walk through this list:

**Navigation**

- Open `https://bi-portfolio.sthill01.workers.dev/` — the homepage loads with all 6 dashboard cards and 6 model cards.
- Click **Home** in the top bar from any inner page — it returns to the homepage.
- Click **Dashboards** — you land on the Dashboards category page with all 6 cards.
- Click **Models** — you land on the Models category page.
- Click **Accomplishments** — loads the accomplishments page.
- Click **60/90 Day Plan** — loads the plan page.

**Each dashboard and model opens**

- Netgain dashboard + model
- Foxit dashboard + model
- UTA dashboard + model
- Website Squirrel dashboard + model
- Healthicity dashboard + model (interactive calculator should recalculate when you change dropdowns)
- Hill Capital dashboard

**Look + feel**

- The topbar is dark and consistent across every page.
- The Healthicity pages use **coral red (#ff3d4d)** as the dominant color, with cyan accents — **not teal**.
- Fonts load (Source Serif Pro for headlines, Inter for body).

**Mobile**

- Open the site on your phone or resize your browser to ~400px wide. The topbar should collapse gracefully and dashboards should still be readable.

---

## Common pitfalls (and fixes)

**Pitfall: "I pushed but Cloudflare didn't deploy"**

- Open the Cloudflare Pages deployments list. Is there a row for your latest push? If no, the GitHub integration probably dropped. Go to **Settings → Builds & deployments** in your Pages project and reconnect the repo.
- If there is a row but it's **red / failed**: click it, read the build log. Usually it's a missing file or broken path.

**Pitfall: "I see my changes locally but the live site is unchanged"**

- You probably forgot to **Push** (commit only moves changes locally — push moves them to GitHub). Check GitHub Desktop's top bar for a "Push origin" button.
- Or your browser is cached: hard-refresh with **Ctrl/Cmd + Shift + R**, or open in incognito.

**Pitfall: "A link is broken on a dashboard"**

- Almost always a path-case issue. Cloudflare is case-sensitive, Windows file explorer is not. So `dashboards/index.html` and `Dashboards/index.html` are different on Cloudflare even though they look the same on your laptop.
- Our folders are **capitalized**: `Dashboards/`, `Models/`, `Accomplishments/`, `IHS/`. Always link with the capital letter.

**Pitfall: "I broke something and want to roll back"**

- On Cloudflare Pages, go to **Deployments** → find the previous green deployment → click the three-dot menu → **Rollback to this deployment**. The live site flips back within a minute.
- Then fix the bad version locally, push again, and the rollback is replaced automatically.

---

## The abbreviated workflow (once you've done it once)

Every future update is just:

1. Make your changes in the `Portfolio/` folder.
2. Open GitHub Desktop.
3. Write a short commit summary → click **Commit to main**.
4. Click **Push origin**.
5. Wait 1–2 minutes.
6. Hard-refresh the live site. Done.

You don't have to touch Cloudflare at all for routine updates.

---

## Where things live

| Thing | Location |
|---|---|
| Your local working copy | `Career/Portfolio/` on your computer |
| GitHub repo | `https://github.com/<your-username>/<repo-name>` |
| Live site | `https://bi-portfolio.sthill01.workers.dev/` |
| Cloudflare Pages dashboard | `https://dash.cloudflare.com/` → Workers & Pages → your project |

---

*Questions? Break something? Most issues are one of the "Common pitfalls" above. When in doubt: look at the Cloudflare Deployments tab — it will tell you whether the push arrived, whether the build passed, and why it failed if it didn't.*
