# Cortex AI Lab — UHG VBC Hands-On Lab

A Snowflake hands-on lab guide for building AI-powered analytics on value-based care (VBC) data using Cortex Analyst, Cortex Search, Cortex Agents, Snowflake Intelligence, and Cortex Code.

## Live lab guide

**https://sfc-gh-mwalli.github.io/Cortex-AI-Lab/**

The guide is a single static page (`index.html`) served via GitHub Pages.

## Repository layout

```
.
├── index.html                          # the lab guide (served at the site root)
├── images/                             # images used by the guide
│   └── cortex-code-ui-icon.png
└── assets/                             # lab asset files attendees use
    ├── Clinical_Notes_RAW.csv          # synthetic clinical notes dataset
    └── 02_enriched_loading_demo.ipynb  # PII-redaction + enriched-loading notebook
```

## Editing

Edit `index.html`, commit, and `git push` — GitHub Pages automatically redeploys the
live site within about a minute.
