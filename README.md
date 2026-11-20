# Preparing a cell matrix input for PreGame RNA-only model 
PreGame is a machine-learning algorithm capable of identifying TR γδ T cells from single-cell CITE sequencing data of tumour-infiltrating lymphocytes (TILs). Here, I document how I prepare a cell matrix for the PreGame RNA-only model with snRNA-seq data.

## Input file needed for PreGame:
a cell matrix (each row is a barcode/cell, either a .csv or .tsv) from each dataset containing:
- Barcode
- "S.Score”, “G2M.Score” and “Phase” values (from Seurat’s CellCycleScoring() function) 
- Normalized gene expression of the 19 PreGame genes 

## Outline of script:
1. Load CD8T obj (or your broad T cell obj where gdT is at), subset "NK/gdT", & prepare barcode of gdT
2. Normalize CD8T obj 
3. Cell Cycle Scoring (missing ABHD17A & TRDV1 genes in snRNAseq data)
4. Build the expression table from the SCT assay
5. Combine the expression with the barcodes and cell-cycle scores 
6. Session info


## References:
- St. Paul, M., Hendrikse, L.D., Ying, F. et al. Identification of broadly tumour-reactive γδ TCRs from multiple myeloma. Nature 659, 208–215 (2026). https://doi.org/10.1038/s41586-026-11055-9
- https://zenodo.org/records/20028241
- https://satijalab.org/seurat/articles/cell_cycle_vignette
- https://satijalab.org/seurat/reference/cc.genes.updated.2019

