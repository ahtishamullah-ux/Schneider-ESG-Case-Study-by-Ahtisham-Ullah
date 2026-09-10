# Schneider Electric ESG Case Study + Telemetry Dashboards

**A Case Study on Improving Sustainable Strategies and Performance Through Implementation of Digital Transformation and ESG in Schneider Electric**

**Author:** Ahtisham Ullah
University of Salento (Università del Salento), Lecce, Italy
Email: [ahtisham.ullah@studenti.unisalento.it](mailto:ahtisham.ullah@studenti.unisalento.it)
LinkedIn: [linkedin.com/in/ahtisham-ullah-2763b2188](https://www.linkedin.com/in/ahtisham-ullah-2763b2188/)

---

## About

An interactive, single-page web publication combining academic research with a working demonstration rig:

1. **Case Study (full paper)** — 11-section manuscript with abstract, literature review, methodology, performance analysis, tables, figures and 16 Harvard-style references, presented as a professional white document sheet with a scrollspy table of contents and reading-progress bar.
2. **Live Telemetry Dashboard** — a simulated EcoStruxure-style monitoring rig streaming six sensor channels (temperature, humidity, pressure, CO₂, light, power draw) with sparklines, an interactive trend chart, threshold alerting and an event log.
3. **Test Dashboard (Data Collector)** — records every reading into a timestamped dataset with selectable sampling interval, live min/avg/max statistics per channel, anomaly injection for stress-testing, and one-click **CSV export** for analysis.

## Tech Stack

- Single-file `index.html` — no build step, no dependencies to install
- [Tailwind CSS](https://tailwindcss.com/) via CDN
- [Lucide](https://lucide.dev/) icons via CDN
- Google Fonts (Space Grotesk, JetBrains Mono, Newsreader)
- Vanilla JavaScript (canvas-based charts, simulation engine, CSV generator)

## Run Locally

Just open `index.html` in any modern browser — it works offline-first with no server required (internet needed only for the CDN assets).

## Deploy on GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch **`main`** and folder **`/ (root)`**, then **Save**.
5. Your site goes live within ~1 minute at:
   `https://<your-username>.github.io/<repository-name>/`

> The `.nojekyll` file included in this repo disables Jekyll processing so the site is served exactly as-is.

## Repository Structure

| File | Purpose |
|---|---|
| `index.html` | The complete application — paper + both dashboards (required) |
| `README.md` | This file — repository documentation |
| `.nojekyll` | Disables Jekyll on GitHub Pages (serve files as-is) |
| `.gitignore` | Excludes OS/editor artefacts from version control |
| `LICENSE` | MIT License |

## License

MIT © 2026 Ahtisham Ullah. The case study manuscript content remains the academic work of the author; Schneider Electric, EcoStruxure and Schneider Sustainability Impact are trademarks of Schneider Electric SE, referenced here for research purposes only.
