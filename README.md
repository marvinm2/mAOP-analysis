# Molecular AOP Transcriptomic Analysis

This repository contains the code and workflows used in the manuscript **"Molecular Adverse Outcome Pathways: towards the implementation of transcriptomics data in risk assessments"**. he goal is to analyze GEO datasets in the context of molecular AOPs using pathway-based approaches, enabling more mechanistically informed transcriptomic interpretations for toxicological risk assessment.

## Structure
- `notebooks/`: Jupyter notebooks for parsing GEO2R output, preprocessing, and enrichment analysis
- `data/`: Contains per-dataset subfolders with `.tsv` differential expression results from GEO2R
- `results/`: Contains processed datasets and figures (e.g., volcano plots, filtered gene lists)

## GEO Datasets
Differential expression results were downloaded and processed using GEO2R. The following datasets were included:

### GSE90122
**Title:** Analysis of gene expression in human primary hepatocytes (HPPs) in response to the treatment of hPXR antagonist (SPA70) and agonists (rifampicin, SR12813, and TO90137)

**System:** Human primary hepatocytes

**Reference:** Lin W, Wang YM, Chai SC, Lv L et al. SPA70 is a potent antagonist of human pregnane X receptor. Nat Commun 2017 Sep 29;8(1):741. PMID: 28963450

### GSE124053
**Title:** System Analysis of The Functional Cross-Talk Between PPARα, LXR and FXR in HepaRG Liver Cells

**System:** HepaRG human liver-like cells

**Reference:** Wigger L, Casals-Casas C, Baruchet M, Trang KB et al. System analysis of cross-talk between nuclear receptors reveals an opposite regulation of the cell cycle by LXR and FXR in human HepaRG liver cells. PLoS One 2019;14(8):e0220894. PMID: 31437187

### GSE116280
**Title:** Acute and delayed transcriptomics changes in 3D LUHMES exposed to rotenone

**System:** LUHMES neuronal precursor cells

**Reference:** Harris G, Eschment M, Orozco SP, McCaffery JM et al. Toxicity, recovery, and resilience in a 3D dopaminergic neuronal in vitro model exposed to rotenone. Arch Toxicol 2018 Aug;92(8):2587-2606. PMID: 29955902

## Processing Workflow
Each dataset is:
- Parsed from `.tsv` files exported from GEO2R
- Expanded for multi-gene entries (e.g., `A///B`)
- Combined per gene (averaging `logFC`, Fisher-combined `P.Value`)
- FDR-adjusted using Benjamini–Hochberg method
- Visualized with volcano plots, p-value histograms, and logFC distributions

Processed data and plots are stored in `results/`, preserving the original dataset structure.

## Citation
If you use this repository, please cite the corresponding manuscript [once published].
Additionally, cite the dataset authors and GEO accessions.
A DOI from Zenodo will be provided here once available.

