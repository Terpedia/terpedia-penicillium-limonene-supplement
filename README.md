# Terpedia Penicillium R-(+)-limonene transcriptomics audit

This forkable research project audits the published Table S7 candidate-gene expression and annotation data for [Zhang et al.'s limonene exposure study](https://www.frontiersin.org/journals/microbiology/articles/10.3389/fmicb.2020.00744/full). The [executed Jupyter notebook](notebooks/terputer-penicillium-limonene-supplement.ipynb), [generated white paper](research/penicillium-limonene-supplement/generated/white-paper.md), [claim ledger](research/penicillium-limonene-supplement/generated/claim-ledger.tsv), and [receipts](research/penicillium-limonene-supplement/generated/generation-receipt.json) are committed. See the [project methods and findings](research/penicillium-limonene-supplement/README.md).

The [publisher workbook](https://public-pages-files-2025.frontiersin.org/articles/527643/file/Data_Sheet_1.xlsx/527643_supplementary-materials_datasheets_1_xlsx/1) is restored from a checksum-pinned URL and kept out of Git. The audit finds 58 unique candidate rows: 31 higher and 27 lower author-provided expression values in the time-matched contrast, and 10 rows with explicit P450/CYP annotation text. Table S7 lacks per-gene adjusted p values and replicate measurements. These results are descriptive and do not establish independent differential expression, cross-study replication, or a direct limonene target.

## Reproduce

```sh
python -m pip install -r requirements.txt
python restore-inputs.py research/penicillium-limonene-supplement/report-spec.json
python notebook-runner.py notebooks/terputer-penicillium-limonene-supplement.ipynb . 120 '["research/penicillium-limonene-supplement/results/analysis_summary.json","research/penicillium-limonene-supplement/results/table_s7_audit.tsv"]' '["research/penicillium-limonene-supplement/data/Data_Sheet_1.xlsx"]'
node report-generator.mjs research/penicillium-limonene-supplement/report-spec.json
```

To attach a fork to your `terpedia-report` workspace, fork this repository into your GitHub account under the same repository name and use `add_research_project_submodule` with slug `penicillium-limonene-supplement`. The submodule path is `projects/penicillium-limonene-supplement`.
