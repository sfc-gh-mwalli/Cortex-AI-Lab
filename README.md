# Cortex AI Lab — Value-Based Care Hands-On Lab

A Snowflake hands-on lab guide for building AI-powered analytics on value-based care (VBC) data using Cortex Analyst, Cortex AI Functions (AISQL), Cortex Search, Cortex Agents, Snowflake CoWork (formerly Snowflake Intelligence), and CoCo (formerly Cortex Code).

## Live lab guide

**https://sfc-gh-mwalli.github.io/Cortex-AI-Lab/**

The guide is a single static page (`index.html`) served via GitHub Pages.

## What the lab covers

The guide walks attendees through 14 steps, grouped into setup plus three modules, all built on the Synthea synthetic healthcare dataset (no PHI):

- **Setup** — create a trial account, enable cross-region inference with CoCo, create the `snowcamp` workspace, database, and schema, and get the Synthea dataset from the Marketplace.
- **Module 1 · Cortex Analyst** — build a semantic view in Workspaces with Semantic View Autopilot (**Add new → Semantic View**), refine it with VBC metrics and dimensions via a `CREATE OR ALTER SEMANTIC VIEW` script, and ask natural-language questions.
- **Module 2 · Cortex Search** — load 1,500 clinical notes through a notebook that uses `AI_COMPLETE` and `AI_REDACT` to scan and redact PII in-flight, then build and query a Cortex Search service.
- **Module 3 · Cortex Agents** — create an agent with CoCo using Cortex Analyst and Cortex Search tools, register it with Snowflake CoWork, and test multi-tool reasoning.

## Repository layout

```
.
├── index.html                          # the lab guide (served at the site root)
├── README.md
├── .nojekyll                           # tells GitHub Pages to serve files as-is
├── .gitignore
├── .github/
│   └── workflows/
│       └── pages.yml                    # GitHub Pages deploy workflow (auto-stamps the header timestamp)
├── images/                             # images used by the guide
│   └── cortex-code-ui-icon.png         # CoCo icon
└── assets/                             # lab asset files attendees download/use
    ├── Clinical_Notes_RAW.csv          # synthetic clinical notes dataset (raw, pre-redaction)
    ├── Clinical_Notes_CLEAN.csv        # redacted CLINICAL_NOTES table dump — fallback if AI_COMPLETE/AI_REDACT are unavailable
    ├── 02_enriched_loading_demo.ipynb  # PII-redaction + enriched-loading notebook (Module 2)
    ├── vbc_analytics_sv_orig.sql       # Autopilot-generated semantic view DDL (reference)
    └── vbc_analytics_sv_updated.sql    # CREATE OR ALTER semantic view DDL with VBC metrics/dimensions
```

## Editing

The live site deploys from `main`, and people use it continuously, so changes are
made on a feature branch and merged via pull request only after testing:

1. Create a branch, edit `index.html` (and assets), and push the branch. Feature
   branches never deploy — the `github-pages` environment only accepts `main`.
2. Preview locally with `python3 -m http.server 8000` and open
   `http://localhost:8000/`.
3. Open a pull request to `main` and merge once testing is complete.

On merge, the `pages.yml` GitHub Actions workflow redeploys the live site within
about a minute and automatically stamps the header "Updated …" timestamp from the
latest commit date (America/New_York), so there's no need to edit the date by hand.
