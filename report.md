# Adverse Event Signal Exploration Report

## Objective

Explore de-identified adverse-event reports using cautious descriptive analysis. The analysis follows the task steps: clean drug, reaction, severity, age group, and outcome fields; calculate reporting frequencies and serious-report proportions; and visualize frequent reported drug names, reactions, and co-reported drug–event terms.

## Data source and scope

This reproducible project uses the official FDA openFDA Drug Adverse Event API (FAERS). Because the task screenshot did not expose its “Dataset resource” URL, the source is documented here and in the notebook. The notebook queries reports with receipt dates from January 1 through December 31, 2025, and downloads at most 3,000 records in receipt-date order. It stores the retrieved JSON snapshot locally so later runs use the same input. This is a bounded, non-random sample, not a complete or representative dataset.

## Method

Each source report is represented once for report-level summaries. Drug and reaction terms are deduplicated within each report before frequency counts. Seriousness is read from the report-level serious flag. Age is converted to years where the submitted age and unit are usable and grouped into 0–17, 18–44, 45–64, 65+, or Unknown. Outcome codes are summarized as submitted. The notebook prints the sample size, date range, overall serious-report proportion, most frequent terms, and creates bar charts and a table/heatmap of co-reported product names and reaction terms.

## Results

Run all cells in `adverse_event_signal_exploration.ipynb` to generate the sample-specific numbers and visualizations. The final notebook cell prints an automatically generated summary from the downloaded snapshot. Values are intentionally generated from the data at run time because the API may update historical records and the screenshot did not include the dataset itself.

## Interpretation and limitations

These results describe reporting patterns in the downloaded sample only. They do not measure event incidence or comparative risk. Spontaneous reports may be incomplete, duplicated, unverified, and affected by reporting practices. A report can include multiple products and multiple reactions; co-reporting does not establish a drug–event causal link. Seriousness and outcomes are as submitted, not independently validated. This analysis is educational and must not be used for diagnosis, treatment, or clinical/product safety decisions.

## Reproduction

Install dependencies with `pip install -r requirements.txt`, launch Jupyter, and run the notebook from top to bottom. Keep `data/openfda_faers_2025_sample.json` with the notebook to reproduce the same analysis input. See `README.md` for full setup details.

## References

- https://open.fda.gov/apis/drug/event/
- https://api.fda.gov/drug/event.json
