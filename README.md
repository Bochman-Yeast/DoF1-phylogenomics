# DoF1 Phylogenomics Pipeline

**Phylogenomic placement of *Saccharomyces cerevisiae* DoF1, a wild environmental isolate from Indiana University Bloomington, within the broader *S. cerevisiae* species tree.**

This repository accompanies the manuscript:

> *"Declaration of Fermentation: Community-Embedded Wild Yeast Bioprospecting as a Model for Place-Based CURE Design."*  
> Journal of Microbiology & Biology Education (JMBE), submitted 2025.

---

## About the Strain

**DoF1** (*S. cerevisiae* DoF1) is a wild environmental yeast isolate collected from the Indiana University Bloomington campus as part of a course-based undergraduate research experience (CURE). The genome was sequenced using Oxford Nanopore Technology (ONT) long-read sequencing and assembled into ~20 contigs (~11.92 Mb).

- **NCBI BioProject:** [PRJNA1477971](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA1477971)
- **NCBI BioSample:** SAMN60825368

---

## Analysis Overview

The pipeline places DoF1 within the *S. cerevisiae* population structure using a concatenated-gene phylogenomic approach:

| Step | Tool | Description |
|------|------|-------------|
| 1 | BUSCO v5.8.0 | Extract shared single-copy orthologs from all genomes |
| 2 | MAFFT | Align each ortholog independently |
| 3 | trimAl | Trim poorly aligned columns |
| 4 | Concatenation | Build a supermatrix from 500 shared orthologs |
| 5 | IQ-TREE2 | Maximum-likelihood tree inference (LG+G4, 500 ultrafast bootstrap) |
| 6 | Bio.Phylo + matplotlib | Root on *S. paradoxus* and visualize as cladogram |

**Key result:** DoF1 is sister to YJM993 (a human clinical isolate) with 91% bootstrap support, placing it within the broader wild/environmental clade of *S. cerevisiae*.

---

## Reference Strains

See [`reference_strains.csv`](reference_strains.csv) for the full table of strains, lineages, and NCBI accession numbers.

| Strain | Lineage | NCBI Accession |
|--------|---------|----------------|
| S288c | Laboratory | GCF_000146045.2 |
| W303 | Laboratory | GCA_002163515.1 |
| SK1 | Laboratory | GCA_001524775.2 |
| YJM993 | Clinical | GCA_000977955.1 |
| EC1118 | Wine | GCF_000218975.1 |
| AWRI1631 | Wine | GCA_000182765.2 |
| JAY291 | Bioethanol | GCA_000182745.2 |
| RM11-1a | Wild environmental | GCA_000149365.1 |
| CLIB89 | Beer | GCA_003054445.1 |
| CLIB324 | Beer | GCA_003054405.1 |
| *S. paradoxus* CBS432 | Outgroup | GCA_002079055.1 |
| *S. paradoxus* N44 | Outgroup | GCF_000292725.1 |

---

## Repository Contents

```
DoF1-phylogenomics/
├── DoF1_phylogenomics_pipeline.ipynb   # Fully documented Colab notebook
├── DoF1_phylo.rooted.nwk               # Rooted Newick tree file
├── reference_strains.csv               # Strain metadata and accessions
├── README.md                           # This file
└── LICENSE                             # MIT License
```

---

## How to Run

The notebook is designed to run entirely in **Google Colab** — no local installation required.

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste this repository URL and select `DoF1_phylogenomics_pipeline.ipynb`
4. Follow the cells in order — each section has a markdown explanation before the code
5. When prompted, upload the DoF1 genome FASTA (or substitute your own assembly)

**Runtime estimate:** ~2–3 hours total (BUSCO is the longest step at ~1–2 hours).  
**Recommended runtime:** Colab with GPU is not needed; standard CPU runtime is sufficient.

> **Tip:** Mount your Google Drive in Cell 2 so that results are preserved if the Colab session disconnects.

---

## Software Versions

| Software | Version |
|----------|---------|
| BUSCO | 5.8.0 |
| MAFFT | 7.x |
| trimAl | 1.5 |
| IQ-TREE2 | 2.x |
| Python | 3.11 |
| Biopython | 1.8x |
| matplotlib | 3.x |

---

## Citation

If you use this pipeline, please cite:

> [Authors]. (2025). DoF1 Phylogenomics Pipeline (Version 1.0) [Software]. Zenodo. https://doi.org/[DOI PENDING]

---

## License

MIT License — see [LICENSE](LICENSE) for details.
