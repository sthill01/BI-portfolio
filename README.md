# Steve Hill — BI Dashboard Portfolio

Four interactive BI dashboards rebuilt from my actual work — each styled in the brand palette and visual language of the company it was built for. Self-contained HTML + Chart.js, no build step.

## Dashboards

| Company | Dashboard | Layout Style |
|---|---|---|
| **Netgain** | [B2B SaaS Mid-Funnel](dashboards/netgain_b2b_saas_midfunnel.html) | Modern SaaS ops — top nav, hero metric card, asymmetric KPI grid |
| **Foxit** | [API Client Growth Funnel](dashboards/foxit_api_client_growth_funnel.html) | Dark dev-tools UI — sidebar navigation, signal panel, cohort heatmap |
| **Utah Transit Authority** | [Fare Revenue & Elasticity](dashboards/uta_fare_revenue_elasticity.html) | Formal policy report — serif headings, numbered sections, executive summary band |
| **Website Squirrel** | [Lead Segmentation & CAC](dashboards/website_squirrel_lead_segmentation_cac.html) | Playful modern — chunky borders, drop shadows, Webflow-style card grid |

Landing page: [dashboards/index.html](dashboards/index.html)

## Brand palettes used

- **Netgain** — Orange `#F26A2E` on navy `#0F1B2D` (matches netgain.tech brand)
- **Foxit** — Blaze Orange `#FF5F00` on deep ink `#0B0F1A` (matches Foxit official brand guide)
- **UTA** — Endeavour Blue `#0055A4`, Prussian Blue `#002A52`, red `#DA291C` (matches rideuta.com)
- **Website Squirrel** — Orange `#FF6B35`, navy `#1E3A5F`, yellow `#FFC857` (matches websitesquirrel.com)

## Typography

- Netgain: Inter (modern SaaS)
- Foxit: Barlow + Open Sans + JetBrains Mono (Foxit's declared brand fonts)
- UTA: Source Serif Pro + IBM Plex Sans (government/policy document aesthetic)
- Website Squirrel: Poppins + DM Sans (friendly, rounded)

## About the data

All numbers in these dashboards are illustrative. The **structure, metric selection, and analytical framing** mirror the actual work — the raw data itself is proprietary to each employer.

## Tech

- Vanilla HTML + CSS (CSS custom properties for theming)
- Chart.js 3.9.1 via CDN
- Google Fonts via `<link>` tag
- No build step, no dependencies, no localStorage — works from any static host

## Deploying

Any static host works — drag-and-drop the whole `Portfolio/` folder into:
- **Netlify** — drag folder onto app.netlify.com/drop
- **GitHub Pages** — push to repo, enable Pages in Settings
- **Vercel** — `vercel --prod` from this directory
- **Cloudflare Pages** — connect your GitHub repo
