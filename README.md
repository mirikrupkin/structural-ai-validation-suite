# Prediction-Validation 🧬

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/[YOUR-GITHUB-USERNAME]/Prediction-validation/blob/main/[YOUR-NOTEBOOK-NAME.ipynb])

An end-to-end computational biology pipeline for benchmarking and validating AI-generated protein models (such as AlphaFold) against experimental PDB crystal structures. 

This tool automates the complex validation process for multi-chain proteins. By utilizing dynamic sequence alignment under the hood, it gracefully handles common structural bioinformatics hurdles like crystal density gaps, numbering offsets, and unaligned expression tags.

## 🚀 Key Features

* **True Sequence Alignment Mapping:** Implements Needleman-Wunsch dynamic programming (`Bio.Align`) to map spatial coordinates perfectly. This guarantees accurate sequence identity calculations and sub-Angstrom RMSD alignments, even when the experimental PDB contains missing internal loops or numbering shifts.
* **Automated Construct Trimming:** Dynamically identifies and prunes unaligned N/C-terminal expression tags or excess predicted tails to perfectly match the experimental crystal construct.
* **Chain-Aware Spatial Alignment:** Handles complex multi-chain oligomers (like the HIV-1 RTase heterodimer) seamlessly across both `.pdb` and `.cif` formats.
* **API Integration & Parsing:** Fetches AlphaFold predictions directly via UniProt ID and pulls experimental reference PDBs using Biopython. 
* **Synchronized 3D Visualization:** Renders interactive, side-by-side Py3Dmol viewers comparing the aligned prediction model against the experimental reference.
* **Granular Metrics Export:** Generates and exports a comprehensive CSV detailing per-residue deviations (Å), pLDDT confidence scores, and SASA metrics.

## 💻 Quick Start (Recruiter / Demo Mode)

The easiest way to test this pipeline is to use the **Quick Demo Mode**, which automatically downloads and aligns the HIV-1 Reverse Transcriptase Heterodimer to demonstrate multi-chain mapping and construct trimming.

1. Click the **Open in Colab** badge at the top of this README.
2. In Google Colab, go to **Runtime -> Run all** (or press `Cmd/Ctrl + F9`).
3. When prompted in the output cell, press `Enter` to run the automated HIV-1 RTase Demo.
4. The pipeline will automatically fetch the files, trim the constructs, compute the true 100% sequence identity mapping, and generate the interactive 3D visualizer.

## 🔬 Advanced Usage

For custom analysis, simply decline the quick demo when prompted. You will be given an interactive menu to:
1. Input any **UniProt ID** to automatically fetch an AlphaFold model.
2. Provide an experimental **PDB code** for structural superimposition.
3. Drag-and-drop custom `.pdb` or `.cif` files directly into the Colab file panel for proprietary model validation.

### Outputs
Upon completion, the pipeline generates a `validation_metrics_output.csv` containing:
* Residue-by-residue Structural Deviation (Å)
* Local AlphaFold Confidence Scores (pLDDT)
* Solvent Accessible Surface Area (SASA)

## 🛠️ Built With

* **Python 3**
* **Biopython** (PDB/MMCIF Parsing, Superimposer, ShrakeRupley, PairwiseAligner, PDBList)
* **Pandas** (Data manipulation and metrics export)
* **Py3Dmol** (Interactive molecular visualization)
