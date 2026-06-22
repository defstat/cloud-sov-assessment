# Cloud Sovereignty Self-Assessment

A single-page tool that scores a cloud provider against the European Commission's
**Cloud Sovereignty Framework** — eight sovereignty objectives (SOV-1…SOV-8), the
overall **SEAL** level (0–4, set by the weakest objective), and a weighted
**Sovereignty Score** out of 100.

Everything runs in the browser. No server, no build step, no dependencies.

Available in **English and Greek** — use the EN/EL toggle at the top right; the choice
is remembered between visits.

## Two tabs

- **Quick assessment** — rate each of the eight objectives at a single SEAL level (0–4).
  Fast, indicative; per-objective score comes from a calculator-derived SEAL→score curve.
- **Detailed calculation** — the faithful reproduction of the Commission's calculator
  across its **48 specific objectives** (the guidance narrative cites 43). Each answer
  carries the official **value** (0→max per objective) and a **SEAL tag**; the
  **Sovereignty Score** is the weighted sum of each objective's values as a share of its
  maximum, and the **overall SEAL** is the lowest-tagged answer selected (answers where
  every option is SEAL-4 never bind). A *Load guidance example* button reproduces the
  guidance's worked **Sovereignty Score of 68%**. Binding objectives/questions are
  highlighted with "what raises my SEAL" hints, plus a delta against the Quick estimate.

Category weights are shared between tabs and editable on the Quick tab.

## Put it online (GitHub Pages)

1. Create a new repository on GitHub, e.g. `cloud-sovereignty-assessment`.
2. Upload **`index.html`** to the root of the repo (drag-and-drop in the web UI works).
3. Go to **Settings → Pages**.
4. Under *Build and deployment → Source*, choose **Deploy from a branch**, branch
   `main`, folder `/ (root)`, then **Save**.
5. Wait ~1 minute. Your live link appears at the top of the Pages settings, e.g.
   `https://<your-username>.github.io/cloud-sovereignty-assessment/`.

To run it locally instead, just double-click `index.html`.

## How the scoring works

- Each objective is rated **SEAL-0 to SEAL-4** using the descriptions from the
  Commission's Implementation Guidance.
- **Overall SEAL = the lowest level** reached across all eight objectives (the
  framework's "weakest link" rule). The gold ceiling line shows this in the panel.
- **Weighted score** = each objective's score multiplied by its weight, summed to a
  value out of 100. The weights are the **exact values from the Commission's official
  Sovereignty Assessment Calculator** — SOV-1 20%, SOV-2 10%, SOV-3 10%, SOV-4 15%,
  SOV-5 10%, SOV-6 15%, SOV-7 15%, SOV-8 5% — and remain editable per objective.
- The per-objective score for a given SEAL level is **derived from the calculator's real
  per-answer values** (each objective normalised so its maximum ≈ 1000), not a flat
  `level/4×100`. Because the calculator scores 43 separate questions while this tool rates
  each objective at one SEAL level, each level's score is the mean of that objective's
  answer values grouped by the SEAL the framework tags them with.
- Set a **minimum required SEAL** (default SEAL-2, the tender threshold) to flag any
  objective below target and generate priority-gap notes.
- **Download report (PDF)** renders a purpose-built A4 report (not a screenshot of
  the UI): a titled cover with provider/assessor/date/method, a result block (overall
  SEAL + its verbatim definition, weighted score, pass/fail vs the minimum), a
  per-objective results table with the binding objective highlighted, priority gaps,
  and — for the Detailed tab — a full appendix listing every specific objective, the
  chosen answer, its value and SEAL. Bilingual, generated via the browser's
  print-to-PDF (no libraries, works offline). **Copy data** exports the assessment
  (both tabs) as JSON.

## Note on accuracy

Objective definitions, SEAL levels and the lowest-level-wins rule follow the published
guidance. The **category weights** are taken verbatim from the Commission's official
spreadsheet calculator, and the per-objective score curve is derived from that
calculator's actual per-answer values. The calculator itself notes that the example
answer scores in its score column are fictitious, and it evaluates 43 questions rather
than one SEAL level per objective — so this tool is an indicative aid that mirrors the
weighting and value scale, not a question-by-question reproduction or a formal compliance
determination.

Source: European Commission — *Cloud Sovereignty Framework, Implementation guidance*
(June 2026). Independent build; not affiliated with or endorsed by the Commission.
