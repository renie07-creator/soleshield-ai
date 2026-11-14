# SOLESHIELD AI — Thermal & Pressure Scanner

An interactive, single-file web dashboard that demonstrates an AI-assisted **diabetic foot monitoring** concept. It combines simulated plantar **thermal** and **pressure** maps with an explainable alert engine, longitudinal trends and a patient overview.

> ⚠️ **Demonstration only.** All patient data, temperatures and pressures are **simulated**. Thermal images are colourised, not radiometric. This project is **not a medical device**, has not been clinically validated, and must not be used for diagnosis, treatment or prediction of ulcer development.

How to use the SoleShield AI demo

Open the link and click ▶ Start thermal scan. The scan starts automatically and takes about 17 seconds.

1. Watch the scan. The status bar runs through acquisition, colour reconstruction, a scanning beam, segmentation into 9 regions per foot, and analysis. Pause scan, Replay animation or Skip animation are in the controls bar below the maps.

2. Choose a demo patient. At the top, Early warning or High-risk demonstration reloads the whole screen. The Patient chip on the right shows the demo ID and risk level.

3. Explore the 3D maps. All maps are 3D relief maps (height shows the simulated value):

Drag to rotate and tilt. Double-click to reset.
Click any region (heel, medial/lateral midfoot, metatarsal heads, or each toe) to select it. It highlights on both maps and in the tables.
The top-left map is the Thermal image. The Real thermogram button next to its title switches it to the real dataset thermograms (DM017 for early warning, DM023 for high risk), also in 3D.
The right map is the Pressure map. It is simulated and uses the standard kPa colour scale.

4. Read the results (scroll down).

Four cards: max temperature difference, peak pressure, status, and scan quality.
Two tables: regional temperature and pressure, each with left, right and left–right columns. A red ⚠ marks regions meeting the demo alert rules.
Selected-region card: shows the values and persistence for the clicked region.

5. Explore the detail tabs (below the controls, or use the left sidebar).

Explainable alerts: why a region was flagged, the suggested next step, and the clinical action pathway.
Longitudinal trends: pick a foot and region to see temperature, left–right difference and pressure across the two sessions against the patient’s baseline.
Patient overview: patient list, monitoring history, recent changes and quality.

Please note: The thermal images in the “Real thermogram” view are real, but all temperature and pressure values, patient histories and alert thresholds are simulated demonstration data. SoleShield AI is a decision-support prototype and not a diagnostic system.
## Features

- **Scan experience** – landing screen and animated scan sequence with progress stages
- **Dual-modality foot maps** – left/right thermal and pressure maps with 2D and interactive **3D** (Three.js) views; click a region to inspect it
- **Plantar region analysis** – per-region temperature vs. baseline, bilateral asymmetry, and simulated loading changes
- **Explainable alerts** – rule-based engine (persistent temperature elevation, increased plantar loading, combined findings, poor measurement quality) with a clinical action pathway table
- **Longitudinal trends** – temperature, bilateral difference and pressure charts across sessions
- **Patient overview** – demo patients, session history, quality indicators and review status
- **Demo scenarios** – e.g. "Early warning", switchable from the dashboard

### Alert engine defaults

| Parameter | Value | Meaning |
|-----------|-------|---------|
| `asym` | 2.2 °C | bilateral temperature difference threshold (demo) |
| `dT` | 1 °C | rise vs. personal baseline |
| `dP` | 15 % | pressure increase vs. baseline |
| `persist` | 2 | sessions required for a persistent finding |

These live in the `CFG` object inside `index.html`.

## Getting started

No build step or dependencies to install.

```bash
git clone https://github.com/<your-username>/soleshield-ai.git
cd soleshield-ai
# open index.html in a browser, or serve locally:
python3 -m http.server 8000   # then visit http://localhost:8000
```

Three.js (r128) is loaded from the cdnjs CDN, so an internet connection is needed for the 3D views. The rest of the dashboard works without it.

## Deploy with GitHub Pages

1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, then **Save**.
4. Your dashboard will be live at `https://<your-username>.github.io/soleshield-ai/`.

## Project structure

```
soleshield-ai/
├── index.html   # the entire app (HTML, CSS, JS, embedded assets)
├── README.md
├── LICENSE
└── .gitignore
```

## Tech stack

Vanilla HTML/CSS/JavaScript · Canvas 2D · SVG charts · [Three.js](https://threejs.org/) r128

## Disclaimer

SOLESHIELD AI identifies simulated signals only; a clinician determines clinical significance and intervention. Alert thresholds are illustrative demo values.

## License

MIT — see [LICENSE](LICENSE).
