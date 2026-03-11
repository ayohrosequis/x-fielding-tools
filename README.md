# Equis Research — Polling Tools

A collection of client-side HTML tools for survey data processing, quality control, and analysis. All tools run entirely in the browser — no server, no data uploads to external services.

---

## Tools

### 1. `polling-analyzer_AY.html` — Polling Crosstab Analyzer

A self-contained React app (bundled via esbuild) for exploratory analysis of weighted survey data.

**Features:**
- Upload a respondent-level CSV exported from Stata
- Auto-detects weight columns (prefixed `wgt_` or `weight`)
- **Frequencies tab** — weighted frequency distributions with bar charts
- **Net Favorability / Approval tab** — define positive and negative response values, compute net scores with a visual breakdown; auto-detects standard favorability/approval formats
- **Crosstabs tab** — weighted two-way crosstabs with any row × column combination
- **Comparison tab** — load up to 5 datasets side by side; per-dataset filters; two-proportion z-tests against a selected baseline dataset (significance flagged at p < 0.05)
- Searchable dropdown variable selector
- Per-dataset filter panels with multi-value selection and active filter badges

**Usage:** Open the file in a browser. Drag and drop (or click to browse) a CSV. No installation required.

---

### 2. `quota-tracker.html` — Survey Fielding Quota Tracker

A stateless dashboard for monitoring quota completion during live survey fielding.

**Features:**
- Upload a banner book CSV (tab-separated, fixed-width output from Stata)
- Tracks gender, age, education, vote recall, language, region, and competitive CD quotas
- Overview tab with N targets by region and overall completion
- Per-group quota panels with color-coded progress bars (green = on target, amber = slight deviation, red = off target)
- Hard-coded quota targets for the XSS State Series (national + CA/FL/TX/Mid-Atlantic/Midwest/Southwest/Competitive CDs)
- Resets on page refresh — no data persistence by design

**Usage:** Open in a browser. Upload the fielding output CSV. Share the file with teammates — each person processes their own local copy, no data leaves the machine.

---

### 3. `WEIGHTQC_AY.html` — Survey Weighting QC Tool

A tool for validating post-weighting proportions against pre-specified targets.

**Features:**
- Upload a weighted respondent-level CSV
- Select a weight variable and a scope (national or regional)
- Searchable dropdown to select any variable for QC
- Displays weighted proportions vs. targets with pass/warn/fail color coding
- Summary statistics bar (N, effective N, design effect)
- Supports exact string matching against target category labels

**Usage:** Open in a browser. Upload your weighted CSV. Select weight column and scope, then check each weighting variable against its targets.

---

### 4. `weight_qc_targets.html` — Weight QC Targets Reference

A companion reference file containing the target proportions used by the Weight QC Tool for the XSS State Series.

**Contents:**
- National and regional weighting targets (gender, age, education, vote recall, language, region, urbanicity)
- Formatted for direct use with `WEIGHTQC_AY.html`

---

## General Notes

**Data security:** All processing is client-side. CSV data is never sent to any server or third party.

**Stateless by design:** None of these tools use `localStorage` or cookies. Each page load starts fresh, making them safe for simultaneous use by multiple team members without conflict.

**CSV format:** Tools expect CSVs exported from Stata with a header row. Weight columns should be prefixed with `wgt_` or `weight` for auto-detection.

**Browser compatibility:** Tested in Chrome. Other modern browsers should work. No installation, plugins, or internet connection required (fonts load from Google Fonts if connected).

---

## Deployment

These files can be:
- Opened directly from a local file system
- Hosted on GitHub Pages
- Embedded in Google Sites via an iframe

For GitHub Pages deployment, push to the `main` branch and enable Pages in repository settings.
