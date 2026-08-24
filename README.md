# 🧬 Structural Integrity & Validation Pipeline

An interactive, Python-based pipeline designed to benchmark and validate AlphaFold structural predictions against experimental PDB crystal structures. Built with **Biopython**, **Pandas**, and **py3Dmol**, this tool bridges the gap between raw AI predictions and structural biology reality.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mirikrupkin/structural-ai-validation-suite/blob/main/structural_validation_pipeline.ipynb)

---

## ✨ Key Features

1. **Smith-Waterman Local Alignment:** Switched from global to local alignment to ensure accurate mapping even in the presence of missing internal loops or repetitive protein domains.
2. **Chain-Aware Spatial Superimposition:** Automatically maps multi-chain assemblies and calculates global coordinate RMSD and per-residue deviations.
3. **AI Confidence & Solvation Metrics (pLDDT & SASA):** Extracts per-residue AlphaFold confidence scores (pLDDT) from B-factors and computes Solvent Accessible Surface Area (SASA) using Shrake-Rupley to evaluate structural packing.
4. **Automated Construct Trimming & Heteroatom Stripping:** Intelligently prunes unaligned prediction tails, isolates matching reference chains, and strips out non-protein heteroatoms (waters, ions, ligands) to ensure clean 1-to-1 visual comparisons.
5. **Interactive 3D Visualization:** Renders synchronized, side-by-side Py3Dmol cartoon views comparing your prediction against the experimental crystal structure.
6. **Interactive CLI & Sandbox Mode:** Features pre-configured case studies highlighting classic bioinformatics edge cases, plus a custom sandbox mode for any UniProt ID.

---

## 🏛️ Modular Architecture

Designed with a clean, production-ready software structure rather than a monolithic script:
```text
structural-ai-validation-suite/
│
├── src/
│   ├── fetcher.py        # AlphaFold API integration & PDB downloading
│   ├── alignment.py      # Smith-Waterman mapping, trimming, & Superimposer
│   └── metrics.py        # pLDDT extraction & Shrake-Rupley SASA calculation
│
└── structural_validation_pipeline.ipynb  # Interactive execution notebook

```
---

## 🔬 Built-In Biological Case Studies

The interactive menu guides users through four distinct structural biology challenges:
* **[1] HIV-1 RTase:** Validates multi-chain asymmetry in a heterodimer (p66/p51).
* **[2] Lysozyme C:** Demonstrates automated N-terminal signal peptide cleavage handling (18 residues pruned).
* **[3] Polyubiquitin-C:** Showcases repeat domain extraction, finding a single 76-residue monomer within a massive ~685-residue repeating chain.
* **[4] KRAS Oncology Target:** Isolates a matching monomer from an asymmetric crystal dimer and strips interfering heteroatoms.
* **[5] Custom Sandbox:** Input any AlphaFold UniProt ID and optional experimental PDB code for custom validation.

---

## 🛠️ Tech Stack
* **Language:** Python
* **Structural Biology:** Biopython (`Bio.PDB`, `Bio.Align`)
* **Data Processing:** Pandas
* **Visualization:** py3Dmol
* **Environment:** Google Colab / Jupyter Notebooks

---

## 🚀 Quick Start
Click the **"Open in Colab"** badge above to launch the pipeline instantly in your browser. No local installation required—the notebook dynamically initializes its own modular architecture on the fly!
