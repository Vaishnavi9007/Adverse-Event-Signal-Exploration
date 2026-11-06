# Adverse Event Signal Exploration

Reproducible beginner-friendly notebook exploring de-identified FDA adverse-event reports from openFDA. The screenshot's dataset URL was not visible, so this project uses the official openFDA Drug Adverse Event API as a documented source.

## Run

Requires Python 3.10+ and internet access for the first download:

```bash
python -m venv .venv
# Windows PowerShell: .venv\Scripts\Activate.ps1
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook adverse_event_signal_exploration.ipynb
```

Run every cell from top to bottom. The notebook fetches up to 3,000 reports received in 2025 and saves the JSON snapshot under `data/`. Future runs reuse that file. Delete the snapshot to fetch again. The bounded API sample is deterministic by date sorting but is not random or complete.

## Included analyses

- Cleaning drug, reaction, age, seriousness, and outcome fields
- Overall serious-report proportion and report frequency by drug/reaction
- Age group and outcome summaries
- Bar charts and a co-reported drug/reaction view
- Printed summary generated from the notebook results

## Interpretation

FAERS/openFDA reports are spontaneous reports, not verified cases or population exposure data. A report may list multiple drugs and reactions without a validated pairing. Frequencies are not incidence rates, risks, or proof of causation. Findings are for descriptive learning only, not medical decisions.

Source and API caveats: [openFDA Drug Adverse Event API](https://open.fda.gov/apis/drug/event/).
