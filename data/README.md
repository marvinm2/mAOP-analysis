## Purpose
This folder holds processed GEO differential expression .tsv files used in our study. Each subfolder corresponds to a GEO Series accession.

## Expected Pipeline
**Reading input:** `.tsv` files with `GENE_SYMBOL`, `logFC`, `P.Value`, etc.

**Processing flow:**

- Expand multi-gene rows
- Combine duplicate measurements (average `logFC`, Fisher’s method)
- Adjust combined `P.Value` to `FDR`
- Filter/significance analysis

**Outputs generated per dataset in `/results/`:**

- Volcano plot (`*_volcano.png`)
- Boxplot of `logFC` (`*_logFC_boxplot.png`)
- Histogram of `P.Value` or `FDR` (`*_pvalue_histogram.png`)
- Processed gene-level CSV (`*_processed.csv`)

## Processing Script
Run the following from your notebook or Python script:

```python
all_results = batch_process_all_datasets(data_root, results_root)
```

This will create:

```rust
results/
├── GSE90122/
│   ├── …_volcano.png
│   ├── …_logFC_boxplot.png
│   ├── …_pvalue_histogram.png
│   └── …_processed.csv
… (similarly for GSE124053, GSE116280)
```

## Logging & Statistics
`Processing.log` is generated, logging start/end of each file and key statistics:

- Original gene counts
- Expanded row counts
- Number of duplicated genes
- Final cleaned gene count

## Notes
After combining probes, `FDR` is calculated **per gene-level**, ensuring accurate multiple-testing correction.

You can filter by significance (e.g., `FDR < 0.05`) during downstream analysis.