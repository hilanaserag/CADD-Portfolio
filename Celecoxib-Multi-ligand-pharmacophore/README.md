# Multi-Ligand Pharmacophore Modeling and Virtual Screening of COX-2 Inhibitors

## Overview

This project investigates conserved pharmacophoric features among selected COX-2 inhibitors using multi-ligand flexible alignment and consensus pharmacophore modeling in MOE. The resulting pharmacophore query was subsequently used for pharmacophore-based virtual screening of a larger compound library.

## Objective

To identify the common pharmacophoric features shared by selected COX-2 inhibitors and use the resulting four-feature pharmacophore query (PH4) for virtual screening of a compound library.

## Training Set

Six selected COX-2 inhibitors were used as the training set. Their 3D conformer structures were obtained from PubChem in SDF format using their corresponding PubChem Compound IDs (CIDs).

| Compound   | PubChem CID |
| ---------- | ----------: |
| Celecoxib  |        2662 |
| Rofecoxib  |        5090 |
| Valdecoxib |      119607 |
| Etoricoxib |      123619 |
| Meloxicam  |    54677470 |
| Diclofenac |        3033 |

The downloaded SDF files were converted to MOL2 format using Open Babel before being imported into MOE.

## Computational Workflow

### 1. Ligand Preparation

The 3D conformer structures of the six selected COX-2 inhibitors were obtained from PubChem in SDF format and converted to MOL2 format using Open Babel. The prepared ligands were then imported into an MOE database for subsequent multi-ligand analysis.

### 2. Multi-Ligand Flexible Alignment

A flexible alignment procedure was performed to identify common structural arrangements among the six selected COX-2 inhibitors. The procedure generated **55 alignment configurations/entries**.

The selected configuration ranked **3rd out of 55** based on the F (fitness) score (**F = −117.82**). It also exhibited the **most favorable S score** among the generated configurations (**S = −61.99**), supporting its selection for subsequent consensus pharmacophore generation.

![flexible alignment result](Figures/flexible_alignment_result.png)

### 3. Consensus Pharmacophore Generation

The selected alignment configuration was subjected to pharmacophore consensus analysis using the aligned ligand structures. Pharmacophoric features occurring at a threshold of **>75%** were selected and loaded into the Pharmacophore Editor to generate the final four-feature pharmacophore query (PH4).

The resulting consensus pharmacophore consisted of:

* **F1:** Aro | Hyd — aromatic or hydrophobic feature
* **F2:** Aro — aromatic feature
* **F3:** Hyd | Aro — hydrophobic or aromatic feature
* **F4:** ML | Acc | Ani | Don — metal-ligand, hydrogen-bond acceptor, anionic, or hydrogen-bond donor feature

Thus, the final PH4 query contained **two aromatic/hydrophobic alternative features (F1 and F3), one aromatic-only feature (F2), and one chemically versatile interaction feature (F4).**

![pharmacophore consensus settings](Figures/pharmacophore_consensus_settings.png)

![selected pharmacophore features](Figures/selected_pharmacophore_features_on_aligned_ligands.png)

![COX-2 consensus pharmacophore](Figures/COX2_consensus_pharmacophore.png)

### 4. Pharmacophore-Based Virtual Screening

A larger library of COX-2 inhibitor-related compounds was obtained from PubChem and imported into a separate MOE database for pharmacophore-based virtual screening.

The generated PH4 query was used in **Compute → Pharmacophore Search → Query vs Database**. The screening retrieved **340 database entries** matching the pharmacophore requirements.

### 5. Representative Hit Inspection

One representative hit was selected from the 340 retrieved compounds for visual inspection. The final PH4 pharmacophore query was mapped onto the selected hit to assess whether the identified pharmacophoric requirements were geometrically satisfied.

![representative hit mapped to PH4](Figures/representative_hit_mapped_to_PH4.png)

## Results

* Six COX-2 inhibitors were analyzed using multi-ligand flexible alignment.
* **55 alignment configurations/entries** were generated.
* A configuration ranked **3rd out of 55** based on the F fitness score (**F = −117.82**) was selected for subsequent pharmacophore analysis.
* The selected configuration showed the **most favorable S score** among the generated configurations (**S = −61.99**).
* Consensus analysis identified conserved pharmacophoric features occurring at **>75%** frequency.
* A final **four-feature PH4 pharmacophore query** was generated.
* The PH4 query consisted of two aromatic/hydrophobic alternative features, one aromatic-only feature, and one chemically versatile interaction feature.
* Pharmacophore-based virtual screening retrieved **340 database entries**.
* A representative hit was successfully mapped onto the four-feature PH4 query for visual inspection.

## Software & Resources

* **MOE (Molecular Operating Environment)** — multi-ligand flexible alignment, consensus pharmacophore modeling, pharmacophore editing, and virtual screening.
* **PubChem** — retrieval of ligand structures and the screening compound library.
* **Open Babel** — molecular file format conversion from SDF to MOL2.
