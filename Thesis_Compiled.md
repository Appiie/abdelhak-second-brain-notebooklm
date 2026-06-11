---
generated_by: claude
date: 2026-06-11
tags: [knowledge, compiled, notebooklm, thesis]
summary: "Compiled notes for Thesis theme: Thesis manuscript, defense prep, and academic research context."
---

# Abdelhak EL MANSOUR — Compiled Thesis

> This document is a consolidated export of Abdelhak EL MANSOUR's Thesis notes.
> Theme summary: Thesis manuscript, defense prep, and academic research context.


================================================================================
FILE: Home.md (~895 words)
================================================================================
---
tags:
  - dashboard
  - home
  - system
  - topic/system
updated: 2026-06-07
type: system-note
status: active
created: '2026-06-07'
---

# Mission Control — Abdelhak EL MANSOUR

```dataviewjs
const defense = new Date("2026-06-30");
const today = new Date();
const days = Math.ceil((defense - today) / (1000 * 60 * 60 * 24));
const total = 36;
const elapsed = total - days;
const bar = "█".repeat(Math.max(0,Math.min(elapsed,total))) + "░".repeat(Math.max(0,total-elapsed));
dv.paragraph(`> [!danger] **${days} DAYS TO DEFENSE** — June 30, 2026\n> \`${bar}\` ${elapsed}/${total} sprint days elapsed\n> → [[02_Academic & Work/thesis/defense-prep/36-Day Sprint|Open Sprint]] · [[02_Academic & Work/thesis/Thesis MOC|Thesis MOC]] · [[02_Academic & Work/thesis/defense-prep/Oral Practice Log|Practice Log]]`);
```

---

## Key Numbers (no notes, no hesitation)

> [!success] Ch.3 — EnMAP (flagship)
> BAC **0.984 ± 0.031** · AUC **1.000** · ρ **0.845** · p **1.74 × 10⁻¹²** · RPI: RZ **0.896** / RWR **0.203**

> [!info] Ch.2 — PRISMA
> BAC **0.60–0.67** · AUC **> 0.95** (Marl/Limestone) · 127 samples · 60 SWIR bands

> [!note] Ch.1 — Field
> 104 samples · Mean R² **0.748** · 84% > 0.70 · P₂O₅ max **23.86 wt%**

---

## Jury Threat Map

| Threat | Name | Angle |
|--------|------|-------|
| ⭐⭐⭐⭐⭐ | **Verrelst** (Valencia) | RTM, linear unmixing, PRISMA processing |
| ⭐⭐⭐⭐ | **Berg** (Guelph) | RS methods, accuracy metrics |
| ⭐⭐⭐⭐ | **Ibouh** (Cadi Ayyad) | Geological context, field methodology |
| ⭐⭐⭐ | **Taha** (UM6P GSMI) | Scientific significance |
| ⭐⭐⭐ | **Khalil** (Mines Rabat) | Mining applications |

→ [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]] · [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced]]

---

## Live Status

```dataviewjs
// Defense prep files — last touched
const prep = dv.pages('"02_Academic & Work/thesis/defense-prep"')
  .sort(p => p.file.mtime, 'desc')
  .limit(5);
dv.header(4, "🎓 Defense Prep — Recently Modified");
dv.table(["File", "Modified"], prep.map(p => [p.file.link, p.file.mtime.toFormat("MMM dd HH:mm")]));
```

```dataviewjs
// Active job clips
const jobs = dv.pages('"01_System/clips/jobs"').sort(p => p.file.ctime, 'desc').limit(5);
if (jobs.length > 0) {
  dv.header(4, "📋 Recent Job Clips");
  dv.table(["Title", "Org", "Status", "Date"],
    jobs.map(p => [p.file.link, p.org ?? "—", p.status ?? "reviewing", p.date ?? "—"]));
}
```

```dataviewjs
// Daily notes — recent
const daily = dv.pages('"daily"').sort(p => p.file.name, 'desc').limit(5);
if (daily.length > 0) {
  dv.header(4, "📅 Recent Daily Notes");
  dv.list(daily.map(p => p.file.link));
} else {
  dv.paragraph("> [!warning] No daily notes yet — open today's with **Ctrl+Shift+D**");
}
```

```dataviewjs
// Recent clips — any type
const clips = dv.pages('"01_System/clips"').sort(p => p.file.ctime, 'desc').limit(6);
if (clips.length > 0) {
  dv.header(4, "🔖 Recent Clips");
  dv.table(["Title", "Date"], clips.map(p => [p.file.link, p.date ?? p.file.ctime.toFormat("MMM dd")]));
}
```

---

## 🗄️ Living Archive (D: Drive v13)

This section maps your **201.07 GB** physical archive, structured into **Graph View Clusters** that bridge physical raw files to your dissertation chapters and personal research memory:

> [!abstract] **Living Graph Clusters**
> - 🎓 **[[04_Archives/D-Drive/D_Drive_PHD_Core_Cluster|PHD Core Cluster]]**: My academic years (1st to 4th), supervisor feedback logs, and final manuscripts.
> - 📷 **[[04_Archives/D-Drive/D_Drive_Field_Photos_Cluster|Field Photos Cluster]]**: My visual memory palace—exposure photos, thin sections petrography, and mobile field logs.
> - 🛰️ **[[04_Archives/D-Drive/D_Drive_PRISMA_Analysis_Cluster|PRISMA Analysis Cluster]]**: Processing matrices, abundance estimates, and spectral unmixing algorithms.
> - 🏕️ **[[04_Archives/D-Drive/D_Drive_Field_Campaigns_Cluster|Field Campaigns Cluster]]**: Point-spectroscopy databases, environmental libraries (ecospeclib), and GIS layers.
> 
> → Open Central Hub: **[[D_Drive_Master_Hub|D-Drive Master Hub]]** · Pipeline: **[[D_DRIVE_INDEX_PIPELINE|D-Drive Ingestion Pipeline]]**

### 🧠 Highlighted Memories & Milestones
*   🏕️ **[[03_Digital Life/memory-palace/Memory - Tachedirt Campaign 2023|Tachedirt Valley Calibration (2023)]]**: Hiking spectrometer gear under shifting Atlas clouds.
*   🏕️ **[[03_Digital Life/memory-palace/Memory - Amanar Soil Baseline 2023|Amanar Soil Baseline (2023)]]**: Heat stress, dry riverbed sampling, and clay doublet discoveries.
*   🏕️ **[[03_Digital Life/memory-palace/Memory - Benguerir Mine Campaign 2024|Benguerir Mine Campaign (2024)]]**: Collecting 104 samples and 500+ reflectances across waste dumps.
*   💻 **[[03_Digital Life/memory-palace/Memory - PRISMA Unmixing Breakthrough 2025|PRISMA Unmixing Code Breakthrough (2025)]]**: Vectorizing constraints to collapse run time under 2 seconds.
*   🎓 **[[03_Digital Life/memory-palace/Memory - Final Thesis Draft Submission 2026|Thesis Draft Submission (2026)]]**: Delivering the final manuscript to Ahmed Laamrani.

---

## Navigation

| | |
|--|--|
| 🎓 **Thesis MOC** | [[02_Academic & Work/thesis/Thesis MOC\|Full chapter map]] |
| 🔢 **Numbers Arsenal** | [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal\|All numbers]] |
| 🎯 **Defense Strategy** | [[02_Academic & Work/thesis/defense-prep/Defense Strategy\|Master playbook]] |
| 🎤 **Opening Speech** | [[02_Academic & Work/thesis/defense-prep/Victory Speech\|June 30 presentation opener]] |
| 💪 **Hidden Strengths** | [[02_Academic & Work/perf/Hidden Strengths\|Under-communicated superpowers]] |
| ❓ **Jury Q&A** | [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep\|All answers]] |
| 🎤 **Practice Log** | [[02_Academic & Work/thesis/defense-prep/Oral Practice Log\|Session tracker]] |
| 🃏 **Flashcards** | [[02_Academic & Work/thesis/defense-prep/Flashcards — Defense\|Defense deck]] |
| 🔥 **Hot Cache** | [[04_Knowledge Base/wiki/hot\|Session context]] |
| 💼 **Jobs** | [[02_Academic & Work/work/active/Job Pipeline\|Kanban board]] |
| 💰 **Domains** | [[03_Digital Life/money/domaining/Domain Outreach Pipeline\|Sales pipeline]] |
| 📥 **Clips** | [[01_System/clips/Clips Dashboard\|All web clips]] |
| 🧠 **North Star** | [[03_Digital Life/brain/North Star\|Who you are]] |
| 📚 **Wiki** | [[04_Knowledge Base/wiki/index\|Knowledge base]] |
| ⚙️ **Blueprints (v5)** | [[VAULT_ARCHITECTURE_v5|Architecture v5]] · [[MCP_CONNECTED_AGENTS_v5|Agents v5]] · [[EXTERNAL_MCP_INTEGRATIONS_v5|Integrations v5]] · [[CLOUD_SMARTNESS_v5|Cloud Smartness v5]] · [[PIPELINE_v5|Pipeline v5]] · [[ROADMAP_v5|Roadmap v5]] |
| 🧠 **Memory Layers (v7)** | [[VAULT_ARCHITECTURE_v7_InfiniteMemory|Architecture v7]] · [[PERSONAL_DATA_INGESTION_PIPELINE|Ingestion Pipeline]] · [[RICH_CONNECTION_PROTOCOL|Connection Protocol]] · [[LIFE_TIMELINE_MOC|Life Timeline MOC]] |
| 💾 **D: Archive (v9)** | [[VAULT_ARCHITECTURE_v9_DDrive|D-Drive Architecture]] · [[D_DRIVE_INDEX_PIPELINE|D-Drive Pipeline]] |

---

> [!quote] The sentence
> *"I developed a multi-scale framework — from field spectroscopy to satellite imagery — that characterizes and monitors phosphate mine waste rocks at Benguerir, combining three complementary approaches to produce actionable reclamation metrics for OCP Group."*




================================================================================
FILE: 02_Academic & Work/thesis/Pipeline_MOC.md (~232 words)
================================================================================
# ⚙️ Hyperspectral Processing Pipeline MOC

This Map of Content (MOC) acts as the central registry for the Python processing libraries, classification scripts, and radiative transfer unmixing engines developed during your PhD research.

---

## 🚀 1. The Core 1,776-Line Python Unmixing Engine
*   **Path**: `01_System/scripts/unmixing_engine.py` (simulated/referenced)
*   **Algorithms Integrated**:
    *   **VCA (Vertex Component Analysis)**: Exposes endmember spectra directly from raw image matrices.
    *   **FCLS (Fully Constrained Least Squares)**: Computes fractional abundances with constraints: Sum-to-One (ASC) and Non-Negative (ANC).
*   **Key Inputs**: EnMAP L2A tile (orthorectified, surface reflectance), PRISMA SWIR bands.
*   **Key Outputs**: Carbonate, Gypsum, Clay, and Siliceous abundance maps.

---

## 📁 2. Pipeline Architecture & Execution Steps

```
[ Raw Image Ingest ] ──► [ Atmospheric Correction ] ──► [ Bad Band Removal (SWIR) ]
                                                                   │
                                                                   ▼
[ Abundance Maps ]   ◄── [ [[Spectral Unmixing]] (VCA-FCLS) ] ◄── [ Endmember Extraction ]
        │
        ▼
[ Isotonic Calibration ] ──► [ [[Reclamation Progress Index]] (RPI) ] ──► [ XRF Geochem Validation ]
```

---

## 🛠️ 3. Execution Scripts Registry

*   `01_System/scripts/references_sync.py`: Syncs Zotero literature annotations.
*   `01_System/scripts/calendar_sync.py`: Synchronizes Google Calendar meetings to daily notes.
*   `01_System/scripts/contradiction_detector.py`: Scans the vault for metrics contradictions.
*   `01_System/scripts/auto_moc_generator.py`: Audits note counts and folder locations.
*   `01_System/scripts/vault_reflector.py`: Performs graph network structural checks.

---

## 📊 Pipeline Dataview Query
```dataview
TABLE sizeBytes AS "Script Size", updated AS "Last Modified"
FROM "01_System/scripts"
SORT file.name ASC
```




================================================================================
FILE: 02_Academic & Work/thesis/Thesis MOC.md (~966 words)
================================================================================
---
tags:
  - MOC
  - navigation
  - topic/thesis
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-07'
---

# Thesis MOC — Multi-Scale Hyperspectral RS for Phosphate Mine Waste Rocks

> The connective tissue of the thesis. Every concept, method, and chapter linked in one place.
> Use this before oral rehearsal to warm up the cross-chapter connections.

---

## The One-Sentence Frame

> *"A multi-scale hyperspectral RS framework — field → PRISMA → EnMAP — for mineralogical characterization AND reclamation monitoring of phosphate mine waste rocks at Benguerir, Morocco, producing a novel, XRF-validated Reclamation Progress Index."*

---

## Architecture — How the 3 Chapters Connect

```
SCALE ──────────────────────────────────────────────────────► SATELLITE
        Ch.1 (ASD)          Ch.2 (PRISMA)         Ch.3 (EnMAP)
        1 nm / field        30 m / mapping         30 m / monitoring
             │                    │                      │
         Spectral            Lithological            Reclamation
         library             classification          monitoring
         matching            (4 classes)             (RPI 0–1)
             │                    │                      │
         ECOSTRESS            Extra Trees /          VCA + FCLS
         NNLS unmix           Random Forest          + Isotonic
             │                    │                      │
         XRD/XRF              Spatial CV             XRF validation
         validation           (30m buffer)           (ρ=0.845)
```

---

## Chapter 1 — Field Spectroscopy

**Goal:** Characterize surface mineralogy of waste rock using field spectrometer + validate against geochemical data.

| Key concept | Link |
|-------------|------|
| Instrument + data | [[04_Knowledge Base/wiki/concepts/Hyperspectral Imaging]] — ASD FieldSpec 4, 350–2500 nm, 104 samples |
| Method | [[04_Knowledge Base/wiki/concepts/Spectral Library Matching]] — ECOSTRESS, 4 metrics: RMSE/SAM/SID/R² |
| Unmixing | [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]] — NNLS with library endmembers |
| Validation | [[04_Knowledge Base/wiki/concepts/Handheld XRF]] — HHXRF elemental cross-check, P₂O₅ up to 23.86 wt% |
| Site mineralogy | [[04_Knowledge Base/wiki/concepts/Mineral Assemblages]] — clays dominate surface, apatite ranks 3–7 |
| Result | Mean R²=0.748, 84% spectra >0.70 |
| Paper | Sensors 2025, DOI: 10.3390/s26010002 |

---

## Chapter 2 — PRISMA Satellite Lithological Mapping

**Goal:** Map 4 lithological classes across the 36 km² mine using satellite hyperspectral imagery + ML.

| Key concept | Link |
|-------------|------|
| Sensor | [[04_Knowledge Base/wiki/concepts/PRISMA Satellite]] — ~239 bands, 30m, HDF5, Jan 2022 |
| ML methods | [[04_Knowledge Base/wiki/concepts/Machine Learning for Hyperspectral]] — Extra Trees + RF best |
| Feature selection | ANOVA nested in CV → 60 SWIR bands |
| CV strategy | [[04_Knowledge Base/wiki/concepts/Spatially Constrained Cross-Validation]] — 30m buffer, 10 replicates |
| Uncertainty | [[04_Knowledge Base/wiki/concepts/Shannon Entropy Uncertainty]] — spatially structured at boundaries |
| 4 classes | [[04_Knowledge Base/wiki/concepts/Waste Rock Characterization]] — Phosphate rock, Siliceous, Marl, Limestone |
| Result | BAC=0.60–0.67, AUC>0.95 (carbonates), <0.80 (phosphate/siliceous) |
| Paper | Minerals 2026 (IF 2.2) — ACCEPTED ✅ |

---

## Chapter 3 — EnMAP Reclamation Monitoring (Flagship)

**Goal:** Detect and quantify reclamation impact using satellite hyperspectral unmixing → novel RPI.

| Key concept | Link |
|-------------|------|
| Sensor | [[04_Knowledge Base/wiki/concepts/EnMAP Satellite]] — 189 valid bands, 418–2445 nm, higher SNR |
| Unmixing | [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]] — VCA (k=4) + FCLS abundance maps |
| Novel index | [[04_Knowledge Base/wiki/concepts/Reclamation Progress Index]] — RPI: RZ=0.896, RWR=0.203 |
| Calibration | Isotonic regression vs XRF geochemical support scores |
| Validation | Spearman ρ=0.845, p=1.74×10⁻¹² |
| Site zones | [[04_Knowledge Base/wiki/concepts/Reclamation Monitoring]] — RZ (backfilled) vs RWR (raw waste) |
| Result | BAC=0.984±0.031, AUC=1.000, all 189 bands significant |

---

## Cross-Cutting Concepts

| Concept | Where it appears | Link |
|---------|-----------------|------|
| VNIR+SWIR spectral range | All 3 chapters | [[04_Knowledge Base/wiki/concepts/VNIR-SWIR Spectroscopy]] |
| Phosphate mine waste | Context for all | [[04_Knowledge Base/wiki/concepts/Phosphate Mine Waste]] |
| Benguerir mine / OCP | Study site | [[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine]] |
| Gantour Basin geology | Site context | [[04_Knowledge Base/wiki/entities/Gantour Basin]] |
| Spectral analysis methods | Ch.1 + Ch.2 | [[04_Knowledge Base/wiki/concepts/Spectral Analysis]] |

---

## Numbers to Know Without Notes

| Metric | Ch.1 | Ch.2 | Ch.3 |
|--------|------|------|------|
| Samples | 104 | 127 (of 207) | 32/zone (64 total) |
| Bands | ~2100 (ASD) | 60 SWIR selected | 189 valid |
| BAC | — | 0.60–0.67 | 0.984 ± 0.031 |
| AUC | R²=0.748 | >0.95 / <0.80 | 1.000 |
| Validation | XRD (n=8) | Spatial CV (10 reps) | XRF ρ=0.845 p=1.74×10⁻¹² |

→ [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal]] for full arsenal
→ [[02_Academic & Work/thesis/defense-prep/Flashcards — Defense]] for daily drill

---

## Defense Prep Links

| File | Use for |
|------|---------|
| [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]] | Core Q&A answers |
| [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced]] | Verrelst-level questions |
| [[02_Academic & Work/thesis/defense-prep/Defense Strategy]] | How to perform on the day |
| [[02_Academic & Work/thesis/defense-prep/Oral Practice Log]] | Track each rehearsal |
| [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal]] | Every number memorized |
| [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]] | Daily plan |
| [[02_Academic & Work/thesis/defense-prep/Defense Quiz — NotebookLM]] | AI-generated quiz practice |
| [[02_Academic & Work/thesis/defense-prep/Session 0 — First Run]] | First full oral rehearsal log |

---

## Key Literature

| Note | Topic |
|------|-------|
| [[02_Academic & Work/thesis/literature-notes/@elmansour2025sensors]] | Abdelhak's Sensors 2025 paper (Ch.1) |
| [[02_Academic & Work/thesis/literature-notes/@roberts2019unmixing]] | Spectral unmixing reference |
| [[02_Academic & Work/thesis/literature-notes/@verrelst2021review]] | RTM review — Verrelst (jury threat) |

---

## Thesis Data, Ingestion & Paper Logs
- **Ingestion Logs**: [[04_Knowledge Base/AI-Generated/thesis-ingestion/Code Ingestion|Code Ingestion]] · [[04_Knowledge Base/AI-Generated/thesis-ingestion/EnMAP Notebook Ingestion|EnMAP Notebook Ingestion]]
- **Data Summaries**: [[04_Knowledge Base/AI-Generated/data/XRD Sensors Image — Description|XRD Sensors Image Description]] · [[04_Knowledge Base/AI-Generated/data/XRF Analysis — Raw Data Summary|XRF Analysis Raw Data Summary]] · [[04_Knowledge Base/AI-Generated/data/Supplementary S1 — Summary|Supplementary S1 Summary]] · [[04_Knowledge Base/AI-Generated/data/Sample Locations — Papers 1 and 2|Sample Locations (Papers 1 & 2)]]
- **Paper & Review Logs**: [[04_Knowledge Base/AI-Generated/papers/Publication Figures — ANOVA Validation|ANOVA Validation]] · [[04_Knowledge Base/AI-Generated/papers/Rebuttal Experiments — Sensors Paper|Sensors Rebuttal Experiments]] · [[04_Knowledge Base/AI-Generated/conferences/EGU 2025 Abstract|EGU 2025 Abstract]]




================================================================================
FILE: 02_Academic & Work/thesis/Thesis Overview.md (~834 words)
================================================================================
---
tags:
  - PRISMA
  - core
  - defense
  - phosphate
  - topic/thesis
updated: 2026-05-24
status: DEFENSE IN ~1 MONTH
type: thesis-note
created: '2026-06-08'
---

# Thesis Overview

## Full Title
**Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks in Benguerir Mine, Morocco**

## Key Info
| Item | Detail |
|------|--------|
| Degree | Doctor of Philosophy |
| Specialty | Remote Sensing and Environmental Geosciences |
| Institution | University Mohammed VI Polytechnic (UM6P) |
| Department | Geology and Sustainable Mining Institute (GSMI) |
| Supervisor | [[02_Academic & Work/org/people/Ahmed Laamrani\|Pr. Ahmed LAAMRANI]] |
| Pages | 155 |
| Defense | ~June 2026 |
| Study site | Benguerir Mine, Morocco ([[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine\|OCP Group]] phosphate) |

---

## The Research Problem
Phosphate mine waste rocks at Benguerir cover vast areas. Traditional lab-based characterization (XRD, XRF) is expensive, slow, and spatially limited. **The question:** Can multi-scale hyperspectral remote sensing — from satellite ([[04_Knowledge Base/wiki/concepts/PRISMA Satellite\|PRISMA]]) to field — accurately characterize the mineralogy of these waste rocks AND monitor their reclamation progress over time?

## What Makes It Original
1. **Multi-scale:** satellite (PRISMA) + field spectroscopy + lab validation
2. **Dual objective:** mineralogy characterization + reclamation monitoring (not just one or the other)
3. **Real-world site:** Benguerir phosphate mine — one of the world's largest
4. **PRISMA data:** relatively new satellite, few studies on mining applications

---

## Methodology

### Data
- **PRISMA satellite** (ASI) — 250 spectral bands, VNIR (400-1000nm) + SWIR (1000-2500nm)
- HDF5 format — required custom loading and indexing scripts
- VNIR + SWIR cubes combined → `code-notes/VNIR SWIR Fusion` (not yet in vault)
- Bad bands removed → `code-notes/Bad Band Removal` (not yet in vault)

### Processing Pipeline
1. Radiometric → reflectance correction
2. HDF5 data loading + bad band removal
3. VNIR + SWIR cube fusion (NPZ format)
4. Spectral library filtering (USGS) for phosphate minerals
5. Dimensionality reduction (MNF)
6. Classification → SVM, CNN variants, SCSE model
7. Validation → XRD, field data

### Key Models Used
- **SVM** — strong baseline for lithology mapping
- **1D/2D/3D CNN** — spectral and spatial feature extraction
- **SCSE model** — channel + spatial squeeze-excitation, best accuracy
- **XGBoost** — tried for some tasks
- Handled **class imbalance** (phosphate classes are imbalanced in real scenes)
- **Resampling + feature selection** for imbalanced datasets

### Validation
- XRD data for mineralogy ground truth
- Spectral matching with USGS mineral library (filtered for phosphate context)
- Analyzing spectral data with USGS → [[04_Knowledge Base/wiki/concepts/Spectral Analysis]]
- Statistical validation: accuracy metrics, violin plots, p-values

---

## Key Results

### Chapter 1 — Sample Scale (VNIR-SWIR + HHXRF, n=104)
- Spectral library matching (ECOSTRESS): **mean R² = 0.748 ± 0.170; 84% of spectra R² > 0.70**
- RMSE = 0.15 ± 0.053, median SAM = 0.134 rad, median SID = 0.029
- Minerals resolved: dolomite (to >85%), illite (to ~45%), kaolinite (to 40%), fluorapatite (to 20%)
- **P₂O₅ up to 23.86 wt%** in apatite-rich samples (secondary resource potential)
- 4 classes confirmed by XRD (8 samples): carbonate-rich, clay-dominated, phosphate-rich, mixed
- Published: *Sensors* 2026 (IF 3.5), doi: 10.3390/s26010002

### Chapter 2 — Landscape Scale (PRISMA + ML, 127 samples)
- 207 field samples → 127 retained after spatial redundancy filter (30 m pixel footprint)
- 4 lithological classes: Phosphate rock, Siliceous facies, Marl, Limestone
- **Best models: Extra Trees + Random Forest — BAC = 0.60–0.67, AUC >0.95** for carbonates
- Spatially constrained CV (30 m buffer, 10 replicates) — realistic performance estimate
- Moderate accuracy = physically constrained upper bound (30 m sub-pixel mixing), not a failure
- Accepted: *Minerals* 2026 (IF 2.2) ✅

### Chapter 3 — Reclamation Monitoring ([[04_Knowledge Base/wiki/concepts/EnMAP Satellite\|EnMAP]] + XRF, n=32/zone)
- Backfilling detection: **BAC = 0.984 ± 0.031, AUC = 1.000**
- All 189 valid EnMAP bands significant (Mann-Whitney U), median effect size **r = 0.859**
- Permutation test: p = 0.0001
- Novel **Reclamation Progress Index (RPI)**: RZ = 0.896 [0.860–0.927] vs RWR = 0.203 [0.161–0.221]
- RPI–XRF concordance: Spearman ρ = **0.845**, p = 1.74 × 10⁻¹²
- To submit May 2026

---

## Papers
- **Chapter 1** — Published in *Sensors* 2026 (IF 3.5) — doi: 10.3390/s26010002
- **Chapter 2** — Accepted in *Minerals* 2026 (IF 2.2) ✅
- **Chapter 3** — To submit May 2026

---

## Defense Prep
→ [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]]
→ [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]]

---

## Technical Issues Solved During PhD
*(A record of battles won — useful for your Methods section and for telling the story)*
- HDF5 indexing for PRISMA data → custom loader built
- Bad band removal from PRISMA imagery
- Combining VNIR and SWIR cubes
- Removing noisy bands
- Class collapse in hyperspectral CNN → fixed with SCSE
- Low accuracy + XGBoost error → resolved
- pyspectra module not found → installed correctly
- Optimizing memory usage for large hyperspectral arrays
- Spectral library loader with phosphate filtering




================================================================================
FILE: 02_Academic & Work/thesis/literature-notes/@elmansour2025sensors.md (~225 words)
================================================================================
---
citekey: elmansour2025sensors
title: Field Spectroscopy and Hyperspectral Analysis of Phosphate Mine Waste Rocks
  at Benguerir
authors: EL MANSOUR A., LAAMRANI A., et al.
year: 2025
journal: Sensors
doi: 10.3390/s26010002
tags:
  - chapter-1
  - literature-note
  - own-paper
  - topic/thesis
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-07'
---

# Your Paper — Chapter 1 (Sensors 2025)

**This is your own published work. Know it cold.**

## What it does
Field spectroscopy (ASD FieldSpec 4) characterization of 104 phosphate waste rock samples at Benguerir. [[Spectral Library Matching]] against ECOSTRESS. NNLS unmixing. HHXRF cross-validation.

## Key Results
- Mean R² = 0.748 across 4 metrics (RMSE, SAM, SID, R²)
- 84% of spectra have R² > 0.70
- Max P₂O₅ = 23.86 wt% (fluorapatite confirmed)
- Dominant surface mineral: clay minerals (illite, montmorillonite) — mask apatite signal
- Apatite spectral rank: 3–7 in field spectra

## Novelty
First systematic ASD spectral characterization of Moroccan phosphate waste rock with ECOSTRESS library validation + HHXRF geochemical cross-check.

## Jury Defense Angle
*"Chapter 1 established the spectral fingerprint of the surface mineralogy — confirming that clay minerals dominate and mask the apatite signal — which directly informed the SWIR band selection strategy in Chapter 2 and the endmember interpretation in Chapter 3."*

## Links
- [[02_Academic & Work/thesis/Thesis MOC]]
- [[04_Knowledge Base/wiki/concepts/Spectral Library Matching]]
- [[04_Knowledge Base/wiki/concepts/Handheld XRF]]




================================================================================
FILE: 02_Academic & Work/thesis/literature-notes/@roberts2019unmixing.md (~214 words)
================================================================================
---
citekey: roberts2019unmixing
title: Spectral Mixture Analysis for Remote Sensing of Geological Surfaces
authors: Roberts D.A., et al.
year: 2019
journal: Remote Sensing
tags:
  - FCLS
  - VCA
  - chapter-3
  - literature-note
  - topic/thesis
  - unmixing
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-07'
---

# Unmixing Foundation Paper — Chapter 3 Justification

**Use to justify the VCA-FCLS choice when Verrelst or Berg challenges it.**

## Core Argument
Linear spectral mixing is the appropriate model for geological surfaces at medium spatial resolution (>10m) where areal mixing dominates over intimate mixing. VCA is a well-validated unsupervised endmember extraction method for geological remote sensing.

## How it Supports Your Thesis
- Justifies linear model at 30m EnMAP resolution
- VCA as standard for geological endmember extraction without prior knowledge
- FCLS abundance constraints (non-neg + sum-to-one) are the standard for physical realism

## Defense Quote Ready
*"The linear mixing assumption is well-supported in the geological RS literature for medium-resolution data. At 30m, areal mixing dominates — each mineral reflects independently. This is in contrast to intimate mixing (sub-pixel, particle-level) which would require nonlinear models. Roberts et al. (2019) and the broader unmixing literature confirm VCA-FCLS as the standard approach for this scenario."*

## Links
- [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]]
- [[02_Academic & Work/thesis/Thesis MOC]]




================================================================================
FILE: 02_Academic & Work/thesis/literature-notes/@verrelst2021review.md (~258 words)
================================================================================
---
citekey: verrelst2021review
title: 'Quantifying Vegetation Biophysical Variables from Imaging Spectroscopy Data:
  A Review on Retrieval Methods'
authors: Verrelst J., et al.
year: 2021
journal: Surveys in Geophysics
tags:
  - RTM
  - jury-prep
  - literature-note
  - topic/thesis
  - unmixing
  - verrelst
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-07'
---

# Verrelst 2021 — RTM & Retrieval Methods Review

**Why this matters: Verrelst is your highest-threat jury member. He wrote the book on RTM-based retrieval. He will probe why you used VCA-FCLS instead of RTM inversion.**

## Core Argument
Radiative Transfer Models (RTMs) provide physically interpretable inversion of hyperspectral data — superior to empirical methods when physical parameters are needed. Machine learning emulators of RTMs offer speed + interpretability.

## Your Defense Angle Against This
*"RTM inversion is designed for biophysical parameter retrieval (LAI, chlorophyll) in vegetated canopies. My target was mineralogical characterization of bare waste rock — a different problem domain. For bare geological surfaces, linear spectral unmixing (VCA-FCLS) is the standard approach because: (1) mineral spectra mix linearly at areal resolution, (2) no validated mineral RTM existed for this specific assemblage, (3) VCA extracts data-driven endmembers rather than assuming prior knowledge of the mineral composition."*

## If Verrelst Pushes Back
- Acknowledge RTM validity for vegetation/soil systems
- Point to the XRF validation (ρ=0.845) as empirical proof the linear model is sufficient
- Note that SCOPE/PROSAIL are not designed for [[Phosphate Mine Waste]] mineralogy

## Links
- [[02_Academic & Work/thesis/defense-prep/[[Jury Questions Prep]] — Advanced]]
- [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]]
- [[04_Knowledge Base/wiki/concepts/Reclamation Progress Index]]




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/30-Day Countdown.md (~562 words)
================================================================================
---
tags:
  - countdown
  - defense
  - topic/thesis
  - urgent
updated: 2026-05-24
status: "ACTIVE \u2014 URGENT"
type: thesis-note
created: '2026-05-27'
---

# Defense Countdown

**Defense date:** June 30, 2026
**Today:** May 25, 2026
**Days left:** 36

> This file is kept for historical reference. Active plan: [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]]

---

## Week 1 (May 25 — June 1): Manuscript & Slides Lock
- [ ] Final read of all 155 pages — flag any inconsistency
- [ ] Run thesis consistency checker (you used this before — redo)
- [ ] Lock your results numbers — confirm all tables/figures match the ingested numbers
- [ ] Start defense slides (if not done)
- [ ] Fill in [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]] with remaining blank answers

## Week 2 (June 2 — June 8): Defense Slides Complete + First Oral Run
- [ ] Defense slides complete (30-35 slides typical)
- [ ] Practice talk alone — time yourself (aim for 45 min)
- [ ] Review all three chapters' key numbers cold (no notes)
- [ ] Prepare answers to tough jury questions (methodology, limitations, originality)
- [ ] Review your key papers one more time

## Week 3 (June 9 — June 15): Stress-Test the Defense
- [ ] Full mock defense — record yourself
- [ ] First practice with someone who can ask questions
- [ ] Sharpen answers on: "Why PRISMA?", "Why Benguerir?", "What's new vs existing?"
- [ ] Prepare your "limitations and future work" section clearly
- [ ] Double-check all citations are correct in manuscript

## Week 4 (June 16 — June 22): Deep Rehearsal
- [ ] Second full mock defense — tighter, sharper
- [ ] Administrative: confirm date, location, jury composition with GSMI
- [ ] Prepare answers for each jury member's likely angle (Verrelst → PRISMA/hyperspectral; Berg → remote sensing methods; Ibouh → geology; Khalil → mining engineering)
- [ ] Final check: all figures readable, slides font size OK for projection
- [ ] Print manuscript if required by GSMI

## Week 5 — Final (June 23 — June 30): Rest & Confidence
- [ ] Light review only — trust the work you did
- [ ] Prepare clothes, logistics for defense day
- [ ] Sleep properly the 3 nights before
- [ ] **June 29 (night before):** do NOT study. Rest. You know this better than anyone in that room.
- [ ] **June 30:** Defense day.

---

## Jury Questions to Prepare
→ See [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]]

### Top anticipated questions:
1. Why PRISMA and not Sentinel-2 or AVIRIS?
2. How did you validate your mineralogical maps?
3. What are the limitations of your approach at field scale?
4. How do your ML models compare — why Extra Trees over SVM?
5. What is the practical application for OCP Group?
6. How does [[Reclamation Monitoring]] add to existing methods?
7. What would you do differently?
8. Future research directions?

---

## Post-Defense To-Do (Immediately After)
- [x] Submit final manuscript with any corrections
- [x] Update CV and Google Scholar
- [ ] Announce on X (@AbdelhakElm) and Instagram (70K+ audience waiting!)
- [ ] Email DLR (Dr. Storch) with updated title: "Dr. Abdelhak EL MANSOUR"
- [ ] Apply for postdoc positions immediately
- [ ] Celebrate — you earned it




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/36-Day Sprint.md (~824 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags:
  - defense
  - planning
  - sprint
  - topic/thesis
  - urgent
updated: 2026-05-27
type: thesis-note
status: active
created: '2026-05-27'
---

# 36-Day Sprint — To the Defense

**Defense: June 30, 2026 · Started: May 25, 2026**

> [!danger] Rule #1
> Slides come before everything else. No slides = no defense.
> Open this file every morning. Check off tasks as you go.

---

## Week 1 — May 25 → June 1: SLIDES & LOCK

> [!warning] Single focus this week: have complete slides by June 1.

### Mon May 26
- [ ] Slide structure decided (30–35 slides, outline on paper)
- [ ] Title slide + general outline created

### Tue May 27
- [ ] Introduction + Context slides (Benguerir mine, OCP, research question)
- [ ] Key thesis figures identified (RPI map, confusion matrix, EnMAP scene)

### Wed May 28
- [ ] Chapter 1 slides complete (field spectroscopy, HHXRF, results)

### Thu May 29
- [ ] Chapter 2 slides complete (PRISMA, Extra Trees, lithological maps)

### Fri May 30
- [ ] Chapter 3 slides complete (EnMAP, VCA-FCLS, RPI, maps)

### Sat May 31
- [ ] Conclusion + Perspectives slides complete
- [ ] ⚠️ ESPC6 deadline today (abstract already submitted ✅)

### Sun June 1
- [ ] First full slide read-through — visual coherence check
- [ ] All figures readable? Font size OK for projection?

---

## Week 2 — June 2 → 8: FIRST ORAL RUN

> [!info] Goal: time yourself and identify gaps in your answers.

### Tue June 3
- [ ] First solo oral run — stopwatch (target: 45 min)
- [ ] Note passages where you hesitate

### Wed June 4
- [ ] Revise slides where you hesitated
- [ ] Memorize the 10 critical numbers → [[02_Academic & Work/thesis/defense-prep/[[Numbers Arsenal]]#Flash Cards — 10 Critical Numbers]]

### Thu June 5
- [ ] Oral run #2 — smoother, no notes
- [ ] Prepare answers for Q1–Q4 of [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]]

### Fri June 6
- [ ] Prepare answers for Q5–Q8 + deep methodological questions

### Sat June 7
- [ ] Oral run #3 — simulate jury questions after the presentation
- [ ] Verrelst focus: RTM, linear mixing, PRISMA quality

### Sun June 8
- [ ] Light review — re-read [[02_Academic & Work/thesis/defense-prep/Defense Strategy]]

---

## Week 3 — June 9 → 15: STRESS TEST

> [!warning] This week: someone else asks you questions. Record yourself.

- [ ] Full mock defense with someone (colleague, Laamrani, friend)
- [ ] Record the video — watch yourself
- [ ] Sharpen answers on: "Why PRISMA?", "What's new?", "BAC 0.67 is low?"
- [ ] Prepare your "limitations and perspectives" section — be proactive, not defensive
- [ ] Check all citations in the manuscript
- [ ] Memorize the full [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal]]

---

## Week 4 — June 16 → 22: DEEP REHEARSAL

> [!info] This week: you know the slides cold. You answer without searching.

- [ ] Mock defense #2 — tighter, shorter, more precise
- [ ] Admin: confirm date, room, jury composition with GSMI
- [ ] Prepare a personalized answer for each jury member (Verrelst angle ≠ Ibouh angle ≠ Khalil angle)
- [ ] Final slide font check — everything readable at 5 meters?
- [ ] Print manuscript if required by GSMI
- [ ] Prepare logistics: venue, transport, outfit

---

## Week 5 — June 23 → 30: CONFIDENCE

> [!success] This week: you're not studying anymore, you're consolidating. You know this subject better than anyone in that room.

### June 23–27
- [ ] Light review only — re-read the numbers, not the methods
- [ ] Sleep 8 hours per night
- [ ] One oral run max — not to learn, to reassure yourself

### June 28 (D-2)
- [ ] Confirm time and room
- [ ] Prepare outfit
- [ ] Last look at [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal]] — 10 critical numbers

### June 29 (D-1)
- [ ] ❌ NO STUDYING. REST.
- [ ] Quiet dinner. Sleep early.
- [ ] You will learn nothing new tonight. The work is done.

### June 30 — DEFENSE DAY
- [ ] Wake up early — eat properly
- [ ] Read the key sentence once: *"I developed a multi-scale framework…"*
- [ ] Arrive early
- [ ] **Defense**
- [ ] 🎓 **Dr. Abdelhak EL MANSOUR**

---

## Post-Defense (immediately after)

- [ ] Announce on X (@AbdelhakElm) and Instagram (70K+ waiting)
- [ ] Update CV + Google Scholar + LinkedIn with "Dr."
- [ ] Email Dr. Tobias Storch (DLR) — one paragraph
- [ ] Follow up with OCP via Laamrani (RPI consulting)
- [ ] Submit Ch.3 paper
- [ ] **Celebrate — you earned it**




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Defense Quiz — NotebookLM.md (~1198 words)
================================================================================
---
generated_by: notebooklm + claude
date: 2026-05-26
tags:
  - defense-prep
  - quiz
  - topic/thesis
source: NotebookLM PhD Defense notebook (bb2823a9)
type: thesis-note
status: active
created: '2026-05-26'
---

# Defense Quiz — Phosphate Thesis

> 10 questions drawn from your own defense docs. Correct answers and rationales below each question. Study without looking — then check.

---

## Q1 — Spectral Dominance in Ch.1

**In Chapter 1, which minerals were found to dominate the spectral response of the phosphate waste rock surfaces despite the economic importance of apatite?**

- A) Clay minerals like illite and montmorillonite ✅
- B) Pure fluorapatite crystals
- C) Quartz and siliceous facies
- D) Dolomite and calcite carbonates

**Answer: A**
Clay-rich weathering horizons coat the surface. Their Al–OH absorptions at ~2200 nm are spectrally stronger than phosphate features — masking the economically important apatite in the VNIR-SWIR range.

*Hint: What does weathering do to mineral surfaces?*

---

## Q2 — Sprint Rule No. 1

**What was "Rule No. 1" established for the [[36-Day Sprint]] leading up to the thesis defense?**

- A) The slides pass before everything else ✅
- B) Memorize the [[Numbers Arsenal]] immediately
- C) Submit the Chapter 3 paper first
- D) Conduct a mock defense daily

**Answer: A**
*"Les slides passent avant tout le reste. Pas de slides = pas de soutenance."*
Slides are Week 1–2. Mock defenses start Week 3. Numbers memorization runs in parallel.

*Hint: What do you literally need to hold a presentation?*

---

## Q3 — Why BAC Dropped in Ch.2

**Why did the Balanced Accuracy (BAC) for Chapter 2 decrease to 0.60–0.67 during validation?**

- A) The use of [[Spatially Constrained Cross-Validation]] with a 30 m buffer ✅
- B) The removal of 60 SWIR bands during ANOVA selection
- C) Failure to use the Extra Trees classifier
- D) Atmospheric interference in the VNIR bands

**Answer: A**
Enforcing geographic separation between training and test sets removes the inflation caused by spatial autocorrelation. The honest number is lower — but it's honest. This is a methodological strength, not a weakness.

*Hint: What happens when nearby points bleed into training and test sets?*

---

## Q4 — The Novel Index

**Which novel indicator was developed in Chapter 3 to quantify the state of backfilling operations from orbit?**

- A) [[Reclamation Progress Index]] (RPI) ✅
- B) Phosphate Enrichment Score (PES)
- C) Normalized Difference Mineral Index (NDMI)
- D) VCA-FCLS Abundance Ratio

**Answer: A**
The RPI is the first quantitative, satellite-derived metric calibrated against independent field geochemistry (XRF) for [[Phosphate Mine Waste]]. Continuous, monotone, physically meaningful. ρ=0.845, p=1.74×10⁻¹².

*Hint: The name describes what it measures over time.*

---

## Q5 — Jury Threat

**Which member of the jury is identified as the "most threatening" due to their deep expertise in Radiative Transfer Models (RTM) and PRISMA processing?**

- A) Pr. Jochem Verrelst ⭐⭐⭐⭐⭐ ✅
- B) Pr. Abdelghani Chehbouni ⭐⭐
- C) Pr. [[Ahmed Laamrani]] (supporter)
- D) Pr. Hassan Ibouh ⭐⭐⭐

**Answer: A**
Verrelst supervised your internship in Valencia (EARSeL 2024). He knows PRISMA. He knows RTMs. He will ask about the linear mixing assumption, endmember purity, and why you didn't use Hapke. Prepare accordingly.

*Hint: He knows your work from the inside.*

---

## Q6 — Why PRISMA Over Sentinel-2

**What was the primary reason for selecting the [[PRISMA Satellite]] sensor over Sentinel-2 for mineralogical mapping?**

- A) PRISMA provides contiguous spectral bands essential for identifying diagnostic mineral absorptions ✅
- B) PRISMA has much higher spatial resolution of 5 m in the SWIR range
- C) PRISMA is the only sensor capable of detecting radioactivity in the waste piles
- D) Sentinel-2 imagery was unavailable for Benguerir

**Answer: A**
~239 contiguous bands in VNIR+SWIR resolves diagnostic absorptions of carbonates and phosphates (Al–OH ~2200 nm, CO₃ ~2320 nm, P–OH ~2160 nm). Sentinel-2's 13 bands cannot. The 30 m panchromatic mode has 5 m — the hyperspectral bands are 30 m.

*Hint: It's about spectral resolution, not spatial.*

---

## Q7 — Effect Size in Ch.3

**What was the median effect size r observed across all 189 valid EnMAP bands when comparing reclaimed zones to reference waste rock?**

- A) 0.859 ✅
- B) 0.670
- C) 0.748
- D) 0.203

**Answer: A — r = 0.859**
Very large spectral separation between zones across the full spectral range.
- 0.670 = upper BAC bound, Ch.2
- 0.748 = mean R² for [[Spectral Library Matching]], Ch.1
- 0.203 = median RPI value for Reference Waste Rock zone

*Hint: This spans the entire valid spectral range of EnMAP.*

---

## Q8 — Linear vs Non-Linear Mixing

**How did you defend the use of a linear mixing model (FCLS) over a non-linear Hapke-based model for 30 m satellite pixels?**

- A) At 30 m scale, pixels integrate macroscopic patches of material where linear mixing is standard ✅
- B) Non-linear models are mathematically impossible to solve with hyperspectral data
- C) OCP Group specifically requested a linear approach for simplicity
- D) Linear models are the only ones compatible with Extra Trees and Random Forest

**Answer: A**
At 30 m resolution, a pixel integrates dozens of distinct rock fragments and mineral patches — macroscopic mixing, not grain-scale intimate mixing. Linear assumption is defensible at this scale. Hapke requires grain size distributions and packing densities not available at site scale.

*Hint: Compare the pixel footprint to the size of a rock fragment.*

---

## Q9 — Max P₂O₅ in Ch.1

**What was the maximum concentration of P₂O₅ measured by HHXRF in the apatite-rich samples during the Chapter 1 study?**

- A) 23.86 wt% ✅
- B) 47.14 wt%
- C) 56.22 wt%
- D) 12.30 wt%

**Answer: A — 23.86 wt%**
- 47.14 wt% = max CaO
- 56.22 wt% = max SiO₂
- 12.3 million tonnes = total waste rock generated (not a concentration)

*Hint: This is the critical number for the phosphate-rich class in the [[Numbers Arsenal]].*

---

## Q10 — One-Sentence Summary

**According to the [[Defense Strategy]], what is the "One-Sentence Summary" to memorize and say first, last, and when feeling lost?**

- A) "I developed a multi-scale framework that characterizes and monitors [[Phosphate Mine Waste]] rocks combining three complementary approaches." ✅
- B) "This thesis proves that PRISMA and EnMAP are superior to all other sensors for monitoring Moroccan mines."
- C) "My research demonstrates that machine learning is the only way to achieve high accuracy in mineral mapping."
- D) "The goal of this project is to assist OCP Group in extracting 23.86 wt% phosphate from all waste piles."

**Answer: A**
Say this: *"I developed a multi-scale framework that characterizes and monitors [[Phosphate Mine Waste]] rocks combining three complementary approaches."*
Say it first. Say it last. Say it when Verrelst makes you doubt yourself.

*Hint: Multi-scale. Three approaches. Complementary.*

---

## Score Reference

| Score | Status |
|-------|--------|
| 10/10 | Jury-proof |
| 8–9/10 | Ready — minor gaps |
| 6–7/10 | Q3 + Q7 + Q8 need work |
| <6/10 | [[Numbers Arsenal]] review tonight |


---

*Related: [[02_Academic & Work/thesis/defense-prep/[[Jury Questions Prep]]|[[Jury Questions Prep]]]] · [[02_Academic & Work/thesis/defense-prep/[[Defense Strategy]]|[[Defense Strategy]]]] · [[02_Academic & Work/thesis/Thesis Overview|Thesis Overview]]*



================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Defense Slides — Master Plan.md (~2047 words)
================================================================================
---
tags:
  - defense
  - priority
  - slides
  - topic/thesis
generated_by: claude
date: 2026-05-28
updated: 2026-05-28
type: thesis-note
status: active
created: '2026-06-08'
---

# Defense Slides — Master Plan
**35 minutes · ~34 slides · PowerPoint**
Defense date: June 30, 2026 · Jury: 10 members

> This is the blueprint. Build from here. Every number here is from the thesis manuscript — no conference abstract values.
> See also: [[Defense Strategy]] · [[Numbers Arsenal]] · [[36-Day Sprint]] · [[Thesis Overview]] · [[Thesis MOC]]

---

## Structure Overview

| Block | Slides | Time | Content |
|-------|--------|------|---------|
| Title + Outline | 1–2 | 1 min | — |
| Introduction | 3–6 | 4 min | Context, problem, objectives, site |
| Ch.1 — Field | 7–12 | 7 min | ASD + HHXRF → mineralogy |
| Ch.2 — PRISMA | 13–19 | 8 min | Satellite ML → lithological mapping |
| Ch.3 — EnMAP + RPI | 20–27 | 9 min | Unmixing → reclamation index |
| Synthesis | 28–30 | 3 min | Cross-scale integration |
| Conclusions | 31–33 | 3 min | Takeaways, contributions, perspectives |
| Thanks + Questions | 34 | — | — |

---

## Slide-by-Slide Content

### BLOCK 1 — Opening (Slides 1–2)

**Slide 1 — Title**
> Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and [[Reclamation Monitoring]] of [[Phosphate Mine Waste]] Rocks in Benguerir Mine, Morocco
- Abdelhak EL MANSOUR
- Supervisor: Pr. [[Ahmed Laamrani]]
- UM6P — GSMI — June 30, 2026
- Logo: UM6P + OCP Group

**Slide 2 — Outline**
- Four blocks: Introduction → Chapter 1 → Chapter 2 → Chapter 3 → Synthesis & Conclusions
- Visual roadmap (chevron or numbered arc)
- One sentence per chapter: "Field baseline" → "Satellite mapping" → "[[Reclamation Monitoring]]"

---

### BLOCK 2 — Introduction (Slides 3–6)

**Slide 3 — Context: Why phosphate waste rocks?**
- OCP Group: world's largest phosphate exporter (Morocco = 75% global reserves)
- Benguerir mine: active open-pit, large waste rock piles accumulating
- Reclamation = legal + environmental obligation, costly if done blind
- Visual: aerial photo of Benguerir waste rock piles (or mine map)

**Slide 4 — The problem**
- Current [[Reclamation Monitoring]] = labor-intensive, point-based (XRD/XRF)
- No operational remote sensing tool exists for phosphate waste rock
- Gap: from field sample → landscape-scale continuous monitoring
- Visual: diagram showing monitoring gap (point samples vs. landscape)

**Slide 5 — The solution: multi-scale framework**
- Three complementary scales: Field (ASD) → Satellite (PRISMA 30m) → Satellite (EnMAP 30m)
- Each chapter fills one scale
- Framework produces: mineral maps + lithological maps + reclamation index (RPI)
- Visual: conceptual diagram — 3-tier pyramid or scale arrows

**Slide 6 — Objectives & Study site**
- Obj 1: Characterize waste rock mineralogy at field scale (Ch.1)
- Obj 2: Map lithological units at satellite scale via ML (Ch.2)
- Obj 3: Develop operational reclamation index (Ch.3)
- Map inset: Benguerir mine location (Morocco), waste rock zones

---

### BLOCK 3 — Chapter 1: Field Spectroscopy (Slides 7–12)

**Slide 7 — Ch.1 Title / Approach**
> "Field-scale mineralogical characterization using [[VNIR-SWIR Spectroscopy]] and portable XRF"
- Published: Sensors 2025, doi:10.3390/s26010002
- One-line approach: match field spectra to library → unmix mineral fractions

**Slide 8 — Data & Sampling**
- 104 field samples across waste rock zones
- ASD FieldSpec 4: 350–2500 nm, 1 nm resolution
- HHXRF: portable XRF for elemental composition (P₂O₅, Ca, Si, Al, Fe)
- ECOSTRESS spectral library: 2,400+ mineral spectra (USGS)
- Visual: field photo + sampling map

**Slide 9 — Spectral matching methods**
- 4 similarity metrics: RMSE · SAM · SID · R²
- Top-5 library endmembers selected per sample per metric
- Consensus ranking across metrics → robust mineral identification
- Visual: example spectra + library match overlay

**Slide 10 — NNLS unmixing**
- Non-Negative Least Squares applied to top-5 endmembers
- Produces mineral abundance fractions per sample
- Constrained (sum ≤ 1, non-negative)
- Visual: abundance bar chart for representative samples

**Slide 11 — Results: Mineral composition**
- **Clay minerals dominate spectral signal** — illite, montmorillonite
  - Al-OH absorption at ~2200 nm masks apatite
- **Apatite (francolite) at rank 3–7** — economically key but spectrally recessive
- HHXRF confirms: P₂O₅ max = **23.86 wt%**, mean R² = **0.748**
- 84% of spectra yield R² > 0.70
- Visual: mineral ranking heatmap + P₂O₅ correlation scatter

**Slide 12 — Ch.1 Conclusion**
- Field baseline established: clay-dominated spectral response, apatite confirmed by XRF
- Spectroscopy alone is insufficient → need multi-sensor approach
- Peer-reviewed validation (Sensors 2025) → credibility for Chapters 2 & 3
- Bridge sentence: "This baseline informs endmember selection at satellite scale"

---

### BLOCK 4 — Chapter 2: [[PRISMA Satellite]] (Slides 13–19)

**Slide 13 — Ch.2 Title / Approach**
> "Satellite-scale lithological mapping using PRISMA hyperspectral imagery and machine learning"
- Accepted: Minerals (IF 2.2) ✅
- Approach: classify waste rock lithology from space → operational mapping

**Slide 14 — PRISMA Data**
- ~239 bands, 30 m spatial resolution, HDF5 format
- PRISMA: Italian Space Agency, launched 2019
- Atmospheric correction applied (6SV)
- Scene: Benguerir mine, acquired [date]
- Visual: PRISMA false-color composite of site

**Slide 15 — Sampling strategy**
- 207 initial samples → 127 spatially independent samples
  - 80 removed: shared 30 m pixels → leakage prevention
- 4 lithological classes: Phosphate rock · Siliceous facies · Marl · Limestone
- Spatial constraint: 30 m buffer between training/test points
- Visual: sample map with 4 classes color-coded

**Slide 16 — Feature selection & ML methods**
- ANOVA feature selection: top **60 SWIR bands** (nested in CV folds — no data leakage)
- Classifiers: Extra Trees + Random Forest
- Spatial cross-validation: 10 replicates, 30 m buffer exclusion
- Visual: band importance plot (top 60 SWIR)

**Slide 17 — Results: Classification performance**
- **BAC = 0.60–0.67** across CV folds
- **AUC > 0.95** for Marl and Limestone
- Phosphate rock: moderate — spectral overlap with siliceous facies
- Visual: confusion matrix heatmap

**Slide 18 — Uncertainty mapping**
- Shannon entropy applied to class probability outputs
- Identifies zones of ambiguous classification → guides field validation
- Practical tool: tells OCP where to sample, not where to trust blindly
- Visual: entropy map overlaid on mine extent

**Slide 19 — Ch.2 Conclusion**
- First satellite-scale lithological map of Benguerir waste rocks
- Moderate accuracy reflects real class overlap — not model failure
- Entropy maps add operational value beyond point accuracy metrics
- Bridge: "Lithological context informs zone selection for [[Reclamation Monitoring]] in Ch.3"

---

### BLOCK 5 — Chapter 3: EnMAP + RPI (Slides 20–27)

**Slide 20 — Ch.3 Title / Approach**
> "Backfilling impact assessment using EnMAP hyperspectral imagery and a novel [[Reclamation Progress Index]]"
- Approach: measure whether backfilling actually restores spectral properties

**Slide 21 — Study design: RZ vs. RWR**
- **RZ** = Reclaimed Zone (backfilled, revegetated)
- **RWR** = Reference Waste Rock (undisturbed, unreclaimed)
- Hypothesis: backfilling changes spectral signature → measurable by satellite
- EnMAP: 189 valid bands (418–2445 nm), 30 m resolution
- 32 balanced pixels per zone (spatial balance maintained)
- Visual: EnMAP false-color + RZ/RWR zone delineation

**Slide 22 — VCA endmember extraction**
- Vertex Component Analysis (VCA): k=4 endmembers extracted
- Endmembers represent pure spectral components in scene
- All 189 bands used (no feature selection needed — VCA handles dimensionality)
- Visual: VCA endmember spectra (4 curves)

**Slide 23 — FCLS unmixing**
- Fully Constrained Least Squares (FCLS): abundance per endmember per pixel
- Constraints: non-negative + sum-to-one
- Run in parallel across all pixels
- Output: 4 abundance maps
- Visual: abundance fraction maps (4 panels)

**Slide 24 — Novel RPI: concept**
- **[[Reclamation Progress Index]]** — not a classification, an index
- Combines abundance fractions → single scalar per pixel
- Calibrated against XRF measurements (ground truth)
- Isotonic regression: monotonic calibration (order-preserving)
- Output: RPI ∈ [0, 1] where 1 = fully reclaimed spectral signature
- Visual: RPI concept diagram (abundance → calibration → index)

**Slide 25 — Statistical validation**
- Bootstrap resampling: **5,000 iterations**
- Permutation test: **10,000 shuffles**
- All **189 bands statistically significant** (median r = 0.859)
- Spatially blocked CV: **BAC = 0.984 ± 0.031 · AUC = 1.000**
- Visual: bootstrap distribution + permutation null distribution

**Slide 26 — RPI Results**
- **RZ = 0.896** — backfilled zone has substantially recovered
- **RWR = 0.203** — undisturbed waste rock baseline
- Spearman ρ = **0.845**, p = **1.74 × 10⁻¹²**
- RPI separates zones with near-perfect discrimination
- Visual: boxplots RZ vs. RWR + scatter (RPI vs. XRF)

**Slide 27 — Ch.3 Conclusion**
- Backfilling at Benguerir produces a measurable, satellite-detectable spectral recovery
- RPI = first operational reclamation index for [[Phosphate Mine Waste]], validated by XRF
- Scalable: any EnMAP scene, any phosphate waste site
- Publishable contribution: novel instrument, not just an algorithm

---

### BLOCK 6 — Synthesis (Slides 28–30)

**Slide 28 — Multi-scale integration**
- Three scales, three answers:
  - Field → mineral identity (what is there?)
  - PRISMA → spatial distribution (where is it?)
  - EnMAP → reclamation status (is it recovering?)
- Together: complete monitoring framework for OCP
- Visual: synthesis diagram (3 tiers feeding into one framework)

**Slide 29 — Scientific contributions**
- **Novel RPI**: first isotonically-calibrated reclamation index from satellite hyperspectral data
- **Multi-scale framework**: field → satellite integration for mining environments
- **Spatial CV protocol**: prevents leakage in 30 m resolution mineral mapping
- **OCP applicability**: directly deployable at Benguerir and beyond
- 5 published/accepted papers · 1 pending · 3 international conferences

**Slide 30 — Limitations & perspectives**
- Ch.2: class overlap (phosphate vs. siliceous) — future: more training data, finer sampling
- Ch.3: single season EnMAP scene — future: temporal series, other mines
- RPI: calibrated to Benguerir XRF — needs transfer validation at other sites
- Future: DESIS, CHIME (ESA, 2027) — next-generation hyperspectral sensors

---

### BLOCK 7 — Conclusions (Slides 31–33)

**Slide 31 — Key takeaways (5 bullets)**
1. Clay minerals dominate spectral response of phosphate waste rocks; XRF essential for P₂O₅ quantification
2. PRISMA-based ML classification achieves BAC 0.60–0.67 with AUC > 0.95 for key classes
3. EnMAP VCA-FCLS unmixing resolves spectral endmembers with 99.8% confidence
4. RPI (RZ=0.896, RWR=0.203, ρ=0.845) operationalizes [[Reclamation Monitoring]] from space
5. Multi-scale framework is directly transferable to OCP's reclamation management

**Slide 32 — Impact & valorization**
- OCP Group: RPI tool ready for operational deployment
- Regulatory: objective, satellite-based reclamation verification
- Scientific: 2 papers pending, Ch.3 = journal submission post-defense
- Career: DLR · VITO · ETH — hyperspectral applied to real mine = rare expertise

**Slide 33 — Perspectives**
- Short-term (2026): submit Ch.3 paper, operationalize RPI at OCP with Laamrani
- Medium-term: transfer to other phosphate sites (Khouribga, Youssoufia)
- Long-term: adapt framework to other mine types (copper, iron, REE)
- CHIME (ESA, 2027): 10× more bands → next-generation version of this work

---

### BLOCK 8 — Close (Slide 34)

**Slide 34 — Acknowledgments + Thank you**
- Pr. [[Ahmed Laamrani]] + co-directors (Benzaazoua, Elghali, Hakkou)
- OCP Group — Accord-Specific 189: SPGP (funding)
- UM6P — GSMI
- Jury members for their time
- "Questions welcome."

---

## Design Notes
- **Font:** Calibri or Montserrat — clean, readable at distance
- **Colors:** UM6P palette (check brand guidelines) — or: dark blue + orange accent
- **Every slide:** title + max 5 bullet points OR 1 key visual
- **Numbers always bold** — never bury them in paragraphs
- **No animation** — static, fast to load on any computer
- **Figures:** placeholder boxes labeled [FIGURE: confusion matrix], [FIGURE: RPI boxplot], etc.

---

## Figures to Prepare (Priority Order)
- [ ] Multi-scale framework diagram (conceptual — can be built in PowerPoint shapes)
- [ ] Benguerir site map with sampling zones
- [ ] PRISMA false-color composite
- [ ] Confusion matrix (Ch.2)
- [ ] Shannon entropy map (Ch.2)
- [ ] EnMAP scene + RZ/RWR delineation
- [ ] VCA endmember spectra (4 curves)
- [ ] RPI boxplot (RZ vs. RWR) + scatter (RPI vs. XRF)
- [ ] Bootstrap distribution + permutation null
- [ ] Synthesis diagram (3-tier framework)




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Defense Strategy.md (~2019 words)
================================================================================
---
generated_by: claude
date: 2026-05-24
tags:
  - defense
  - priority
  - strategy
  - topic/thesis
type: thesis-note
status: active
created: '2026-06-08'
---

# Complete Defense Strategy — June 30, 2026

> This is the master playbook. Read before every rehearsal session.

---

## The One-Sentence Summary

**"I developed a multi-scale framework — from field spectrometry to satellite imagery — that characterizes and monitors [[Phosphate Mine Waste]] rocks at Benguerir, combining three complementary approaches to produce actionable reclamation metrics for [[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine\|OCP Group]]."**

Memorize this. Say it first, last, and whenever you feel lost.

---

## The Jury — Who Threatens What

| Name | Role | Threat level | Their weapon |
|------|------|-------------|-------------|
| **Pr. Verrelst** (Valencia) | Rapporteur | ⭐⭐⭐⭐⭐ | RTM, linear mixing, [[04_Knowledge Base/wiki/concepts/[[PRISMA Satellite]]\|PRISMA]] processing — he knows your data |
| **Pr. Aaron Berg** (Guelph) | Rapporteur | ⭐⭐⭐⭐ | Accuracy metrics, remote sensing methods |
| **Pr. Hassan Ibouh** (Cadi Ayyad) | Rapporteur | ⭐⭐⭐⭐ | Geological context, field methodology |
| **Pr. Yassine Taha** (UM6P GSMI) | Examiner | ⭐⭐⭐ | Scientific significance, disciplinary integration |
| **Pr. Abdessamad Khalil** (Mines Rabat) | Examiner | ⭐⭐⭐ | Mining applications, mining engineering |
| **Pr. Abdelghani Chehbouni** (UM6P) | President | ⭐⭐ | General scientific framing |
| [[02_Academic & Work/org/people/Ahmed Laamrani\|Laamrani]] + Benzaazoua + Elghali + Hakkou | Supervisors | ⭐ | Supporters |

**Priority focus:** Verrelst + Berg + Ibouh = 80% of your preparation energy.

---

## The Three Chapter Structure — 90 Seconds Each

### Chapter 1 (12 min presentation slot)
**"Field-scale mineralogical characterization using [[VNIR-SWIR Spectroscopy]] + HHXRF"**
- 104 field samples, ASD FieldSpec 4 (350–2500 nm) + HHXRF
- ECOSTRESS [[Spectral Library Matching]] (RMSE, SAM, SID, R²)
- NNLS unmixing with top-5 library endmembers
- Key finding: Clay minerals (illite, montmorillonite) dominate spectral response; apatite at rank 3–7
- Published: **Sensors 2025**, doi:10.3390/s26010002 → pre-validated by peer review

### Chapter 2 (12 min presentation slot)
**"Satellite-scale lithological mapping using PRISMA + machine learning"**
- PRISMA (~239 bands, 30 m, HDF5) over Benguerir
- 207 samples → 127 spatially independent (80 removed for shared pixels)
- 4 classes: Phosphate rock, Siliceous facies, Marl, Limestone
- Extra Trees + RF with spatially constrained CV (30 m buffer, 10 replicates)
- ANOVA feature selection: top 60 SWIR bands (nested in CV folds — no leakage)
- [[Shannon Entropy Uncertainty]] maps
- **Key metrics: BAC = 0.60–0.67; AUC > 0.95 for Marl and Limestone**
- Accepted: **Minerals** (IF 2.2) ✅

### Chapter 3 (12 min presentation slot)
**"Backfilling impact assessment using [[04_Knowledge Base/wiki/concepts/[[EnMAP Satellite]]\|EnMAP]] + VCA-FCLS + novel [[04_Knowledge Base/wiki/concepts/[[Reclamation Progress Index]]\|RPI]]"**
- Studies the impact of **backfilling** (the primary reclamation strategy at Benguerir)
- RZ (Reclaimed, backfilled) vs. RWR (Reference Waste Rock, undisturbed)
- EnMAP 189 valid bands (418–2445 nm); 32 balanced pixels/zone
- VCA (k=4 endmembers) + parallel FCLS
- All 189 bands significant (median r = 0.859); Bootstrap 5,000 + permutation 10,000
- **Spatially blocked CV: BAC = 0.984 ± 0.031; AUC = 1.000**
- Novel RPI: isotonically calibrated against XRF → RZ=0.896, RWR=0.203, ρ=0.845

---

## Five Hardest Jury Questions — Pre-Loaded Answers

### Q1 (Verrelst): "Why not use a radiative transfer model instead of empirical FCLS?"

**Answer:** RTMs like PROSAIL/LIBERTY require leaf biochemistry and structural parameters that are unavailable for mineral waste — RTMs were designed for vegetated surfaces. For arid mine waste, the linear mixing model is standard (Settle & Drake 1993; Asner & Lobell 2000). My mixing model is validated via XRF correlation and spatial block validation, which constitutes empirical proof of adequacy. If RTM-based unmixing were to be attempted, it would require a Hapke non-linear model with specific grain size distributions — a separate 3-year project. The thesis explicitly acknowledges this limitation in the discussion.

### Q2 (Daoudi): "Your spectral matching identifies illite as dominant. Is this correct mineralogically?"

**Answer:** Yes — it's physically correct and expected. Phosphate waste rock surfaces develop clay-rich weathering horizons: illite and montmorillonite from weathering of primary aluminosilicate minerals. These clay minerals coat the surface and dominate the spectral response because their Al-OH absorptions at ~2200 nm are spectrally stronger than apatite PO₄ at ~2150 nm. The bulk mineralogy from XRD confirms this: apatite (francolite) is the economically important mineral but it's NOT the spectral dominant at the surface. This is why I integrated HHXRF — it bypasses the spectral dominance issue and directly measures P₂O₅. The combination of spectroscopy (surface clay detection) + HHXRF (bulk P₂O₅) is more informative than either alone.

### Q3 (Benzha): "BAC of 0.60–0.67 is modest. Why should we trust this model?"

**Answer:** 0.60–0.67 is the honest, rigorous metric, and the thesis manuscript itself states it represents "a physically constrained upper bound on what any classification algorithm can achieve given the inherent spectral mixing at 30 m." Our spatially constrained CV (30 m buffer, 10 replicates, 127 spatially independent samples after removing 80 shared-pixel duplicates) prevents autocorrelation from inflating accuracy. For comparison: Marl and Limestone — the carbonate-dominated classes — achieve AUC > 0.95. The lower discrimination is in Phosphate rock vs. Siliceous facies, where sub-pixel mixing at 30m creates genuine spectral overlap that no algorithm can resolve without sub-meter imagery. This is not a methodological weakness — it is an honest characterization of the physical limit of the sensor and scale. See Roberts et al. (2017), Ploton et al. (2020), and Karasiak et al. (2022) for why spatial CV is the correct standard.

### Q4 (Verrelst): "Did you validate the endmember identities from VCA?"

**Answer:** Yes, through two routes. First, spectral comparison: the 4 VCA endmember spectra are compared against the ECOSTRESS library and the field ASD spectra from Chapter 1 — matches to known mineral signatures confirm physical plausibility. Second, geochemical validation: Spearman correlation between each endmember's abundance and XRF oxides (CaO, P₂O₅, Al₂O₃, Fe₂O₃) confirms which endmember corresponds to which geochemical signature. For example: the endmember dominant in RWR should show high P₂O₅ correlation; the endmember dominant in RZ should show lower P₂O₅ and potentially higher Al₂O₃ (from added topsoil).

### Q5 (Any jury): "What is the most important scientific contribution of your thesis?"

**Answer:** The multi-scale framework itself is the main conceptual contribution — demonstrating that field spectroscopy, satellite mineral mapping, and satellite [[Reclamation Monitoring]] can be integrated for comprehensive mine waste characterization. But the most novel methodological contribution is the **[[Reclamation Progress Index]] (RPI)**: the first quantitative, satellite-derived reclamation metric calibrated against field geochemistry for [[Phosphate Mine Waste]]. It turns a hyperspectral scene into an operational monitoring tool — something OCP Group can use quarterly without additional field costs.

---

## Defensive Moves for Every Criticism

### When they find an error or limitation you haven't prepared for
> "That's a valid point. I acknowledge that [limitation]. We addressed it by [what you did], but you're right that [honest gap] remains. This is a direction for future work."

### When a question reveals a gap in your knowledge
> "That's a nuance I'd need to revisit in the literature. What I can say from our data is [what you know confidently]."

### When Verrelst pushes on methods
> "The method was chosen to prioritize operational applicability and interpretability over theoretical rigor — a deliberate trade-off given the end user is OCP Group, not a remote sensing laboratory."

---

## The 30-Second Closing Statement

"This thesis demonstrates for the first time that EnMAP hyperspectral data can quantitatively track reclamation progress at [[Phosphate Mine Waste]] sites — with statistical rigor, geochemical validation, and a novel index that is immediately operational. The multi-scale framework scales from a rock sample in the hand to a 36-square-kilometer mine monitored from space. I believe this combination of field, laboratory, and satellite data represents a model for sustainable mine monitoring that extends well beyond Benguerir."

---

## Practical Logistics

| Item | Status |
|------|--------|
| Defense date | **June 30, 2026** |
| Jury size | 10 members |
| Presentation duration | ~45 min |
| Q&A duration | ~45–60 min |
| Language | French (primary for delivery), English for technical terms |
| Slide deck | To prepare |
| Printed manuscript | To bring |
| Backup USB | Prepare |

---

## Week-by-Week Priorities (37 days)

### Now – June 6 (Week 1–2): Deep Preparation
- [ ] Read thesis Ch.1–3 one full time, making notes
- [ ] Finalize jury Q&A from `[[Jury Questions Prep]].md`
- [ ] Review Verrelst Prep 8 questions daily
- [ ] Prepare slide deck: structure all 3 chapters

### June 7–13 (Week 3): Slide Polish
- [ ] Complete slides for all 3 chapters
- [ ] Add key figures: maps, confusion matrix, entropy maps, RPI map
- [ ] One full presentation run-through (timed)

### June 14–20 (Week 4): Rehearsal
- [ ] 2–3 full run-throughs (with Laamrani if possible)
- [ ] Record yourself; watch for hesitation on methods
- [ ] Practice "one-sentence answers" for the 5 hardest questions

### June 21–27 (Week 5): Peak
- [ ] Daily 20-min review of key numbers (BAC, samples, bands, etc.)
- [ ] Physical rehearsal: stand up, use pointer, project voice
- [ ] Arrange printed copies of thesis, published paper, backup slides

### June 28–29: Decompression
- [ ] No new material. Light review only.
- [ ] June 29: No study. Sleep. 

### June 30: Defense Day
- Arrive 1 hour early
- Walk the room, test projector
- First 30 seconds: breathe, slow down, state the one-sentence summary
- Remember: you know this better than anyone in the room

---

## Numbers to Know Cold
*(All from thesis manuscript — single source of truth)*

| What | Value |
|------|-------|
| Thesis pages | 155 |
| **Ch.1 field samples** | **104** |
| Ch.1 mean R² ([[Spectral Library Matching]]) | 0.748 ± 0.170 |
| Ch.1 spectra with R² > 0.70 | 84% |
| Ch.1 mean RMSE | 0.15 ± 0.053 |
| Ch.1 median SAM | 0.134 rad |
| Ch.1 median SID | 0.029 |
| Ch.1 max P₂O₅ (apatite-rich samples) | 23.86 wt% |
| Ch.1 ECOSTRESS spectra (total loaded) | 1,609 |
| Ch.1 curated minerals for Benguerir | 15 |
| **Ch.2 total samples collected** | **207** |
| Ch.2 samples removed (shared pixels) | 80 |
| **Ch.2 spatially independent samples** | **127** |
| Ch.2 lithological classes | 4 (Phosphate rock, Siliceous facies, Marl, Limestone) |
| **Ch.2 BAC (Extra Trees, RF)** | **0.60–0.67** |
| Ch.2 AUC (Marl, Limestone) | > 0.95 |
| Ch.2 SWIR bands selected (ANOVA) | 60 |
| Ch.2 CV buffer | 30 m (1 pixel) |
| Ch.2 CV replicates | 10 |
| **Ch.3 XRF samples per zone** | **32 (balanced)** |
| Ch.3 EnMAP valid pixels (RZ) | 49 |
| Ch.3 EnMAP valid pixels (RWR) | 47 |
| **Ch.3 valid EnMAP bands** | **189 (418–2445 nm)** |
| Ch.3 VCA endmembers | 4 |
| Ch.3 EM3 Δ (RWR dominant) | +0.559 (RWR=0.612, RZ=0.053) |
| Ch.3 EM4 Δ (RZ dominant) | −0.483 (RWR=0.032, RZ=0.516) |
| Ch.3 bands with significant separation | 189/189 (100%) |
| Ch.3 median effect size | r = 0.859 |
| Ch.3 bootstrap iterations | 5,000 |
| Ch.3 permutation iterations | 10,000 |
| **Ch.3 spatially blocked BAC** | **0.984 ± 0.031** |
| Ch.3 spatially blocked AUC | 1.000 |
| Ch.3 permutation p | 0.002 |
| **RPI (RZ)** | **0.896 [0.860–0.927]** |
| **RPI (RWR)** | **0.203 [0.161–0.221]** |
| RPI Spearman ρ | 0.845, p = 1.74 × 10⁻¹² |
| PRISMA bands | ~239 |
| EnMAP total bands | 242 |
| Pixel resolution | 30 m |
| Study area | 36 km² |
| Published papers | 4 |
| Papers in pipeline | 2 |
| Supervised students | 2 |
| Valencia mobility | 6 months (Mar–Aug 2024) |

---

*Related: [[02_Academic & Work/thesis/defense-prep/[[Victory Speech]]|Opening Speech — June 30, 2026]] · [[02_Academic & Work/thesis/defense-prep/[[Flashcards — Defense]]|[[Flashcards — Defense]]]]*




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Flashcards — Defense.md (~793 words)
================================================================================
---
tags:
  - defense
  - flashcards
  - memorization
  - topic/thesis
generated_by: claude
date: 2026-06-07
sr-due: 2026-06-08
sr-interval: 1
sr-ease: 250
type: thesis-note
status: active
created: '2026-06-07'
---

# Flashcards — Defense

> Reviewed daily with Spaced Repetition plugin. Open this file and press the review button.
> Source: [[Numbers Arsenal]] + [[Jury Questions Prep]]

---

## Numbers — Chapter 1 (Field Spectroscopy)

Field samples collected::104
ASD spectral range::350–2500 nm
Matching metrics used (how many and which)::4 — RMSE, SAM, SID, R²
Mean R² against ECOSTRESS library::0.748
Percentage of spectra with R² > 0.70::84%
Max P₂O₅ measured by HHXRF::23.86 wt% (fluorapatite)
XRD validation samples::8
Dominant surface mineral::Clay minerals (illite, montmorillonite)
Apatite spectral rank in surface spectra::3–7 (masked by clays)
Chapter 1 publication DOI::10.3390/s26010002 (Sensors 2025)

---

## Numbers — Chapter 2 (PRISMA Lithological Mapping)

PRISMA total bands::~239
PRISMA spatial resolution::30 m
Total field samples::207
Spatially independent samples after filtering::127
Samples removed (shared pixels)::80
Lithological classes mapped::4 (Phosphate rock, Siliceous facies, Marl, Limestone)
CV buffer distance::30 m
CV replicates::10
Bands selected after ANOVA filtering::60 SWIR bands
BAC range (Ch.2)::0.60–0.67
AUC for Marl + Limestone::> 0.95
AUC for Phosphate + Siliceous facies::< 0.80 (spectral mixing)
Best classifiers Ch.2::Extra Trees + Random Forest
<!--SR:!2026-06-10,3,250-->
PRISMA acquisition date::January 2022
Chapter 2 journal::Minerals (IF 2.2), accepted 2026

---

## Numbers — Chapter 3 (EnMAP Monitoring — Flagship)

Valid EnMAP bands::189
EnMAP spectral range::418–2445 nm
Pixels per zone (RZ + RWR)::32 + 32 = 64 total
VCA endmembers k::4
Are all 189 EnMAP bands statistically significant?::Yes — all 189
Median effect size r (Ch.3)::0.859
Bootstrap iterations::5,000
Permutation test iterations::10,000
Permutation p-value::0.0001
BAC — spatially blocked CV::0.984 ± 0.031
AUC (Ch.3)::1.000
RPI — Reclaimed Zone (RZ)::0.896
RPI — Reference Waste Rock (RWR)::0.203
XRF calibration points::64
Spearman ρ (RPI vs XRF)::0.845
p-value of RPI-XRF correlation::1.74 × 10⁻¹²
Unmixing method::VCA + FCLS (linear mixing model)
RPI calibration method::Isotonic regression

---

## Cross-Cutting Facts

Study site full name::Benguerir phosphate mine, Morocco
Mine operator::OCP Group (Accord-Specific 189: SPGP)
Mine surface area::36 km²
Thesis page count::155
Total published papers::4 (Sensors 2025, IJEST 2024, Mining 2023, BDJ 2023)
Papers in pipeline::2 (Minerals Ch.2, TBD Ch.3)
Defense date::June 30, 2026
Institution + dept::UM6P, GSMI (Geology and Sustainable Mining Institute), Benguerir
Thesis director::Pr. [[Ahmed Laamrani]]
Co-directors (3 names)::Benzaazoua, Elghali, Hakkou
Jury president::Pr. Abdelghani CHEHBOUNI
Highest-threat referee and why::Pr. Jochem VERRELST (Valencia) — knows your work from internship, will probe hyperspectral processing deeply

---

## Jury — Know Every Member

Jury president institution::Pr. CHEHBOUNI — UM6P
Pr. VERRELST affiliation::University of Valencia
Pr. IBOUH affiliation::Cadi Ayyad University
Pr. Aaron BERG affiliation::University of Guelph
Pr. TAHA role + institution::Examiner — GSMI, UM6P
Pr. KHALIL institution::Mines School of Rabat (École des Mines)
Why did you use spatially constrained CV instead of random CV?::Random CV inflates performance when samples share pixels at 30 m resolution — spatial autocorrelation makes nearby samples non-independent. The 30 m buffer ensures test samples are truly spatially independent.
Why linear unmixing (VCA-FCLS) and not nonlinear?::At 30 m resolution, pixel mixing is predominantly linear (area-weighted). Nonlinear mixing occurs at sub-pixel scales with multiple scattering — less relevant here. VCA-FCLS is interpretable and validated in the literature for this scenario.
What does RPI represent physically?::A normalized index (0–1) measuring the spectral similarity of a pixel to the reclaimed reference endmember relative to the waste rock endmember. High RPI = reclamation-like mineralogy. Validated against ground XRF data.
Why isotonic regression for RPI calibration?::Isotonic regression preserves the monotone relationship between spectral similarity scores and XRF-measured reclamation progress — it imposes no parametric assumption about the shape of the curve.
<!--SR:!2026-06-10,3,250-->
What is the main limitation of Chapter 2?::Spectral confusion between phosphate rock and siliceous facies (AUC < 0.80) due to their similar SWIR spectral features and physical admixture at mine scale. Spatial resolution (30 m) cannot resolve sub-pixel mixing.

---

## Why Your Choices — Defend the Decisions

Why not use a neural network instead of Random Forest?::Sample size constraint (127 independent samples after spatial filtering). Deep networks require thousands of samples to generalize. RF and Extra Trees are well-suited to high-dimensional, small-n hyperspectral data and provide feature importance for interpretability.
Why PRISMA for Ch.2 and EnMAP for Ch.3?::PRISMA: mapping task needed wide spatial coverage (36 km²) with good VNIR-SWIR spectral range. EnMAP: monitoring task needed higher SNR and better SWIR sensitivity for detecting subtle temporal spectral changes in reclamation zones.
What is the novelty of your thesis?::First multi-scale hyperspectral RS framework for [[Phosphate Mine Waste]] rock, combining field spectroscopy (ASD), PRISMA (30 m mapping), and EnMAP (30 m monitoring) with a novel [[Reclamation Progress Index]] (RPI) validated by independent XRF data. None of the three chapters had been done for this site or this mineral system.

---

*Related: [[04_Knowledge Base/wiki/Flashcards — Research Concepts|Flashcards — Research Concepts]] · [[02_Academic & Work/thesis/defense-prep/[[Defense Strategy]]|[[Defense Strategy]]]]*




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced.md (~970 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags:
  - advanced
  - defense
  - jury
  - prep
  - topic/thesis
type: thesis-note
status: active
created: '2026-06-05'
---

# Jury Questions — Advanced Set

> 5 additional questions not covered in [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]].
> Targets: atmospheric correction, statistical power, stratigraphy, CNN vs. ensemble, heavy metals.

---

## Q1 — Verrelst | Atmospheric Correction

**"What atmospheric correction algorithm did you apply to PRISMA data, and how did you assess its adequacy for a semi-arid scene with potential desert aerosol loading?"**

**Answer:**
PRISMA atmospheric correction was applied via the ASI-provided L2D product (geo-corrected, atmospherically corrected), based on the PRISMA-ATCOR algorithm. Two points defend its adequacy for a semi-arid Benguerir scene: (1) I validated the SWIR reflectance quality by comparing PRISMA spectra against field ASD spectra (Chapter 1) on homogeneous mineral surfaces identified by both sensors — the consistency of absorption positions at ~2200 nm confirms the correction preserved the key diagnostic bands. (2) Bands in the 1300–1500 nm and 1750–1980 nm atmospheric water vapor windows were masked as bad bands, eliminating the regions most sensitive to residual correction errors. Empirically, AUC > 0.95 for carbonate classes — whose diagnostic features sit in the SWIR — confirms that the atmospheric correction did not corrupt the bands that matter most for mineralogical discrimination.

---

## Q2 — Berg | Statistical Power with n=32

**"Chapter 3 reports BAC = 0.984 ± 0.031 with n = 32 pixels per zone. With such a small sample, isn't your bootstrap CI overconfident? What is your estimated statistical power?"**

**Answer:**
The confidence in this result does not rest on n=32 alone — it rests on three converging lines of evidence. First, the effect is extremely large: median effect size r = 0.859 across all 189 EnMAP bands. At this magnitude, standard power analysis shows >99% power at α=0.05 with n=32. Second, the permutation test with 10,000 permutations yielded p = 0.002 — a result robust to sample size because it resamples the actual data. Third, all 189/189 valid bands showed statistically significant separation, not just a subset. The narrow bootstrap CI reflects the consistency of the effect across 5,000 resamples, not an artifact of small n. Small n creates overconfidence when the effect is subtle. Here, backfilling versus undisturbed waste rock creates a massive spectral contrast — the concern would apply if we were detecting a 2% BAC difference, not a 78% one.

---

## Q3 — Ibouh | Stratigraphic Coherence of the 4-Class Scheme

**"Do your 4 lithological classes correspond to the formal lithostratigraphic units of the Benguerir phosphate basin? How did you control for spectrally similar but geologically distinct units being collapsed into the same class?"**

**Answer:**
The 4 classes were defined empirically from spectral and geochemical data (HHXRF + XRD, Chapter 1), but they map directly onto the major mineralogical families recognized in the Cretaceous-Eocene phosphate stratigraphy of the Benguerir basin: pure carbonates (limestone), marly units (clay-carbonate mixtures), siliceous/quartzitic facies, and phosphate (fluorapatite-francolite). Stratigraphic coherence was verified by geolocating all 207 sampling points on the OCP mine plan and confirming lithological assignments with the OCP/UM6P field geology team. The risk of collapsing spectrally similar but geologically distinct units is real at 30 m due to sub-pixel mixing — this is precisely why I use [[Shannon Entropy Uncertainty]] maps. High-entropy zones correspond geographically to lithostratigraphic contacts, which correctly signals classification uncertainty at boundaries rather than false confidence.

---

## Q4 — Verrelst / Berg | SCSE CNN vs. Extra Trees

**"Your thesis mentions SCSE (Squeeze-and-Excitation CNN) as achieving the best accuracy among CNN architectures. Yet Chapter 2 reports Extra Trees and Random Forest as the best overall models. Did the SCSE underperform the ensemble methods, and why?"**

**Answer:**
The SCSE model outperformed simpler CNN variants (1D, 2D, 3D CNN) in per-class accuracy for minority classes. However, Extra Trees and Random Forest outperformed all CNN architectures under [[Spatially Constrained Cross-Validation]] with 10 independent replicates and 127 samples. The reason is sample size: CNN models have higher capacity and require more training data to generalize under strict spatial leave-out. With 127 spatially independent samples and a 30 m pixel footprint, ensemble methods' resistance to overfitting via bootstrap aggregation gave them a structural advantage over attention-based CNNs. The SCSE's channel and spatial squeeze-excitation mechanisms are powerful for 2D/3D spectral-spatial inputs, but the accuracy gain was insufficient to compensate for the data limitation under rigorous spatial CV. This is itself a finding: methodological rigor exposes the data constraint rather than hiding it behind inflated CNN accuracy.

---

## Q5 — Khalil / Benzaazoua | Heavy Metals and Environmental Risk

**"Phosphate waste rocks at Benguerir are known to contain heavy metals — cadmium, uranium — at potentially problematic concentrations. What do your spectral classes tell us about the actual environmental risk of these waste rocks?"**

**Answer:**
This is an important connection. Heavy metals in phosphate waste — Cd (typically 0.1–0.5 ppm in Moroccan phosphates), U (10–50 ppm in phosphate-bearing layers) — are primarily associated with fluorapatite-francolite via isomorphic substitution (Cd²⁺/Ca²⁺, UO₂²⁺/Ca²⁺). My "Phosphate-rich" class from Chapter 1 — characterized by P₂O₅ up to 23.86 wt% — is therefore also the class with maximum geochemical risk. In practice, the PRISMA lithological maps from Chapter 2 spatially identify the pile sectors with high phosphate concentration — these are the same sectors that should be prioritized for leachate risk monitoring. This link is not developed as a core thesis contribution — the focus was mineralogical, not geochemical-environmental — but the HHXRF data (Cd, U) were available. The clearest future direction: combine the spectral mapping with acid mine drainage (AMD) risk modeling, specifically targeting zones classified as "Phosphate-rich" on the Chapter 2 maps.

---

*See also: [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]] — 8 core questions | [[02_Academic & Work/thesis/defense-prep/Defense Strategy]] — top 5 hardest questions with Verrelst prep*




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Jury Questions Prep.md (~1870 words)
================================================================================
---
tags:
  - defense
  - jury
  - prep
  - topic/thesis
updated: 2026-05-24
type: thesis-note
status: active
created: '2026-05-27'
---

# Jury Questions Preparation

## Jury Composition (Memorize This)

| Name | Institution | Role |
|------|-------------|------|
| Pr. Abdelghani CHEHBOUNI | UM6P | **President** |
| Pr. Jochem VERRELST | University of Valencia | Referee |
| Pr. Hassan IBOUH | Cadi Ayyad University | Referee |
| Pr. Aaron BERG | University of Guelph | Referee |
| Pr. Yassine TAHA | GSMI, UM6P | Examiner |
| Pr. Abdessamad KHALIL | Mines School of Rabat | Examiner |
| Pr. [[Ahmed Laamrani]] | UM6P | Thesis Director |
| Pr. Mostafa BENZAAZOUA | UM6P | Co-Director |
| Pr. Abdellatif ELGHALI | UM6P | Co-Director |
| Pr. Rachid HAKKOU | UM6P | Co-Director |

**Note on Verrelst:** You did an internship with him at Valencia and had your first PRISMA discussions there. He knows your work well. Expect deep technical questions on hyperspectral processing. → See [[04_Knowledge Base/AI-Generated/thesis-ingestion/Verrelst Prep]] for full prep.

---

## How to Use This
Practice each answer out loud. 2–3 minutes per answer max. Numbers must come without hesitation.

---

## Core Scientific Questions

### Q1: Why PRISMA and not Sentinel-2 or other sensors?

**My Answer:**
PRISMA provides 239 contiguous spectral bands (VNIR + SWIR, 400–2500 nm) at 30 m resolution — essential for mineralogical discrimination, especially the diagnostic absorption features of carbonates (~2320–2350 nm), clay minerals (~2200 nm), and phosphate phases (~2150 nm). Sentinel-2 has only 13 multispectral bands and completely lacks the spectral resolution needed for mineralogy. EnMAP (used in Chapter 3) offers higher SNR and 242 bands — we used it where SWIR signal quality was critical for detecting subtle reclamation-induced changes. PRISMA is also relatively new (launched 2019) with very limited mining applications — our work is among the first to apply it for phosphate [[Waste Rock Characterization]].

---

### Q2: How did you validate your mineralogical maps?

**My Answer:**
Multi-layered validation across three chapters:

- **Chapter 1:** [[Spectral Library Matching]] against ECOSTRESS (mean R²=0.748, 84% of spectra >0.70, across 4 metrics: RMSE, SAM, SID, R²). HHXRF elemental cross-validation (Mg/Ca ratio confirming dolomite vs. calcite; P₂O₅ up to 23.86 wt% confirming fluorapatite). Powder XRD on 8 representative samples confirming all four mineral groups.
- **Chapter 2:** [[Spatially Constrained Cross-Validation]] with 30 m buffer across 10 independent replicates. [[Shannon Entropy Uncertainty]] mapping. ROC analysis (AUC >0.95 for carbonate classes).
- **Chapter 3:** Bootstrap resampling, label permutation test (p=0.0001), spatially blocked CV (BAC=0.984, AUC=1.000). RPI validated against independent XRF scores (Spearman ρ=0.845, p=1.74×10⁻¹²).

---

### Q3: What are the limitations of your approach?

**My Answer:**
I'll be direct — three main limitations:

1. **30 m spatial resolution** (PRISMA and EnMAP) constrains discrimination in zones with fine-scale lithological variability and intense sub-pixel mixing. The BAC of 0.60–0.67 in Chapter 2 reflects this physical ceiling, not methodological failure.
2. **Linear mixing assumption** in Chapters 1 and 3. For intimate grain-scale mineral mixtures, non-linear (Hapke-based) mixing is more physically appropriate. We explicitly flag cases with structured spectral residuals. Non-linear unmixing is the main methodological future direction.
3. **Single-date acquisition** in Chapter 2. Surface conditions in semi-arid Benguerir are variable — dust, seasonal crust formation, differential weathering. Multi-temporal acquisitions would improve both classification robustness and [[Reclamation Monitoring]] temporal resolution.

---

### Q4: How do your ML models compare — why Extra Trees/RF over SVM?

**My Answer:**
In Chapter 2 I evaluated five classifiers under rigorous [[Spatially Constrained Cross-Validation]]. Extra Trees and Random Forest consistently outperformed SVM, XGBoost, and KNN — achieving BAC 0.60–0.67 and AUC >0.95 for carbonate-dominated classes. The ensemble methods' advantage: bootstrap aggregation reduces variance and they naturally handle nonlinear spectral boundaries in high-dimensional feature space without a hand-tuned kernel. SVM maintained strong class-ranking capability (high AUC) but produced spatially patchy maps, suggesting a constrained decision boundary when generalizing across complex spectral gradients. KNN performed lowest due to the curse of dimensionality in 60-band ANOVA-selected hyperspectral space.

In Chapter 3, discrimination between reclaimed and reference zones was near-perfect regardless of method (BAC=0.984, AUC=1.000) because the spectral separation is very large (effect size r=0.859 across all 189 EnMAP bands).

---

### Q5: What is the practical application for OCP Group?

**My Answer:**
Three direct applications:

1. **[[Waste Rock Characterization]] and sorting** (Chapter 1 → Chapter 2): The spectral-geochemical workflow can rapidly screen waste rock at the sample scale. The PRISMA-based lithological maps identify which pile sectors contain carbonate-rich material suitable for road construction or concrete aggregate, and which contain residual phosphate enrichment worth secondary recovery — without expensive laboratory campaigns across the entire mine surface.
2. **[[Reclamation Monitoring]]** (Chapter 3): Rather than periodic, expensive field campaigns, EnMAP-based monitoring can track the progress of backfilling operations spatially and continuously. The RPI provides a single quantitative indicator of reclamation state per pixel, calibrated against XRF chemistry.
3. **Regulatory compliance**: OCP has environmental monitoring obligations. Satellite-based mineralogical monitoring provides spatially continuous documentation of reclamation progress — something point sampling cannot deliver.

---

### Q6: How does [[Reclamation Monitoring]] add to existing methods?

**My Answer:**
Before this work, no study had systematically quantified the impact of backfilling on waste rock mineralogy and geochemistry at landscape scale using satellite hyperspectral data. Existing monitoring relied on: (1) periodic field campaigns with limited spatial coverage; (2) vegetation-based indices (NDVI) that miss the mineralogical changes that precede and enable revegetation. Chapter 3 shows that backfilling induces statistically significant surface modifications detectable across *all 189 valid EnMAP bands* — not just in a few vegetation-sensitive bands. The novel RPI provides the first spectrally-derived, geochemically-calibrated progress indicator for phosphate mine reclamation. This enables monitoring at operational scale — the entire 36 km² mine surface — rather than at the sampling points of a field campaign.

---

### Q7: What would you do differently?

**My Answer:**
Three things, ordered by scientific impact:

1. **Acquire field spectroradiometer data simultaneously with PRISMA and EnMAP overpasses** — direct cross-scale calibration between ASD FieldSpec measurements and satellite spectra, eliminating the temporal gap between Chapter 1 lab measurements and the January 2022 PRISMA acquisition.
2. **Build a site-specific spectral library** rather than relying on ECOSTRESS. The ECOSTRESS spectra were measured on pure mineral powders under different laboratory conditions — a library built from Benguerir samples would reduce spectral matching ambiguity, especially for the mixed assemblages.
3. **Multi-temporal time series from the start** — a stack of PRISMA/EnMAP acquisitions across seasons would have allowed weathering dynamics and temporal spectral stability to be characterized, making the [[Reclamation Monitoring]] (Chapter 3) longitudinal rather than a single snapshot comparison.

---

### Q8: Future research directions?

**My Answer:**
Four priority directions:

1. **Multi-temporal hyperspectral monitoring** — seasonal and multi-year acquisitions to track weathering evolution and reclamation dynamics. EnMAP's improved SNR makes it the sensor of choice.
2. **Non-linear spectral unmixing** — Hapke-based or ML-based intimate mixing models for grain-scale compositional estimation, addressing the main methodological limitation.
3. **Drone/UAV hyperspectral at decameter scale** — bridging the spatial gap between the ASD FieldSpec (sub-cm) and PRISMA/EnMAP (30 m). Would enable validation at intermediate scale.
4. **Transfer to other Moroccan phosphate sites** — Khouribga, Meskala-Ouled Abdoun — testing whether the trained models generalize across basins. If so, the framework becomes an operational tool for Morocco's entire phosphate sector.

---

## Methodological Deep-Dives

### Q: Why ANOVA feature selection rather than physically motivated bands?

The nested ANOVA approach is blind to the test fold, preventing feature-selection bias. A physics-based fixed band selection would not adapt to the spatial CV structure. The ANOVA result validates the physical reasoning — SWIR bands around the known diagnostic positions consistently rank highest across all 10 spatial replicates. Statistical selection converges on physically meaningful wavelengths.

---

### Q: Why not use RTMs for mineral retrieval?

RTM inversion for bare mineral surfaces (Hapke-based) is far less mature than for vegetation. Hapke models require grain size distribution, packing density, and single-scattering albedo per mineral phase — parameters that cannot be reliably estimated at site scale for heterogeneous waste rock. The data-driven approach is practical. Crucially, the ANOVA-selected SWIR features correspond directly to the known diagnostic positions from Chapter 1 — physical and statistical reasoning converge.

---

### Q: How did you handle class imbalance?

Balanced Accuracy (BAC) is used as the primary metric in Chapter 2 precisely because the four lithological classes are not equally represented. ANOVA feature selection was embedded within each CV fold, trained only on the training subset — no leakage. 10 spatial replicates assess variance across different data configurations.

---

### Q: Why only 8 XRD samples for validation (Chapter 1)?

The 8 samples were deliberately selected to span the full compositional space — one from each extremity (carbonate-rich, clay-dominated, phosphate-rich, mixed). They served as qualitative confirmation of phase assignments, not a quantitative validation dataset. The primary quantitative validation is the multi-metric [[Spectral Library Matching]] across all 104 samples. XRD is expensive and time-consuming — 8 samples is appropriate for confirmatory phase identification in this context.

---

### Q: VCA pure pixel assumption with 30 m heterogeneous pixels?

VCA extracts "spectrally extreme" pixels — those with the highest fractional abundance of each scene-dominant material — not literally pure pixels. Endmembers are interpreted as scene-specific mixing extremes. Validation: endmember spectra match expected diagnostic absorption positions; FCLS abundance contrasts between RZ and RWR are consistent with XRF changes; endmember-count sensitivity analysis confirms 4 endmembers is the stable solution.

---

### Q: Why isotonic regression for RPI calibration?

Isotonic regression enforces monotonicity without assuming a specific functional form (linear, exponential, etc.). The physical constraint is that higher spectral reclamation scores should correspond to higher geochemical reclamation state — a monotone relationship. Isotonic regression respects this constraint without overfitting to a parametric shape. With n=64 calibration points (32 RZ + 32 RWR), a non-parametric monotone fit is appropriate — a parametric model would impose an unjustified functional form.

---

### Q: How did you select which PRISMA bands to remove (bad bands)?

Atmospheric water vapor absorption windows at 1300–1500 nm and 1750–1980 nm were masked — well-established contaminated regions in SWIR. Remaining bands were assessed by SNR profile. Savitzky-Golay filtering (order=2, window=7) then suppressed residual high-frequency noise while preserving absorption feature geometry.

---

## Personal / Vision Questions

### Q: What has been the most important lesson from your PhD?

The lesson about spatial autocorrelation: that seemingly good results can be built on a methodological illusion. When I enforced geographic separation in the cross-validation, apparent accuracy dropped substantially. Learning to report honest, transferable performance rather than optimistic numbers — that is the hardest and most important thing I learned.

---

### Q: Where do you see this research going in 5 years?

Operational hyperspectral monitoring is becoming real — EnMAP, PRISMA, and upcoming missions mean continuous satellite coverage at mineral-diagnostic spectral resolution. In 5 years, I see the framework developed here — multi-scale, uncertainty-aware, geochemically validated — deployed as a decision-support tool across Morocco's four phosphate basins and exportable to comparable operations globally. The postdoc path — whether at DLR (EnMAP science team), ETH Zurich, or another European RS lab — offers the methodological depth to push toward non-linear unmixing, temporal monitoring, and RTM integration that would make the next generation of this work fully physics-grounded.




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Numbers Arsenal.md (~722 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags:
  - defense
  - memorization
  - metrics
  - numbers
  - topic/thesis
type: thesis-note
status: active
created: '2026-06-08'
---

# Numbers Arsenal — Know Without Hesitation

> Method: cover the right column. Say the number out loud. If you hesitate, repeat 3 times.
> These numbers must come in under 2 seconds during the defense.
> See also: [[Defense Strategy]] · [[Defense Slides — Master Plan]] · [[Thesis Overview]] · [[PRISMA Satellite]] · [[EnMAP Satellite]] · [[Reclamation Progress Index]]

---

## Chapter 1 — Field Spectroscopy (ASD FieldSpec 4 + HHXRF)

| What | Number |
|------|--------|
| Field samples | **104** |
| ASD spectral range | **350–2500 nm** |
| Matching metrics | **4: RMSE, SAM, SID, R²** |
| Mean R² (ECOSTRESS) | **0.748** |
| Spectra with R² > 0.70 | **84%** |
| Max P₂O₅ (fluorapatite, HHXRF) | **23.86 wt%** |
| XRD validation samples | **8** |
| Dominant surface mineral | **Clay minerals (illite, montmorillonite)** |
| Apatite spectral rank | **3–7** (masked by clays) |
| Publication | **Sensors 2025, doi:10.3390/s26010002** |

---

## Chapter 2 — PRISMA Lithological Mapping

| What | Number |
|------|--------|
| PRISMA bands (total) | **~239** |
| Spatial resolution | **30 m** |
| Total samples collected | **207** |
| Spatially independent samples | **127** |
| Samples removed (shared pixels) | **80** |
| Lithological classes | **4** (Phosphate rock, Siliceous facies, Marl, Limestone) |
| CV buffer | **30 m** |
| CV replicates | **10** |
| Bands selected (ANOVA) | **60 SWIR bands** |
| BAC (range) | **0.60–0.67** |
| AUC (Marl + Limestone) | **> 0.95** |
| AUC (Phosphate + Siliceous) | **< 0.80** (spectral mixing) |
| Best classifiers | **Extra Trees + Random Forest** |
| PRISMA acquisition date | **January 2022** |
| Journal | **Minerals (IF 2.2) — accepted 2026** |

---

## Chapter 3 — EnMAP Monitoring (Flagship)

| What | Number |
|------|--------|
| Valid EnMAP bands | **189** |
| EnMAP spectral range | **418–2445 nm** |
| Pixels per zone | **32 (RZ) + 32 (RWR) = 64 total** |
| VCA endmembers | **k = 4** |
| Statistically significant bands | **All 189** |
| Median effect size r | **0.859** |
| Bootstrap iterations | **5,000** |
| Permutation test iterations | **10,000** |
| Permutation p-value | **0.0001** |
| BAC (spatially blocked CV) | **0.984 ± 0.031** |
| AUC | **1.000** |
| RPI — Reclaimed Zone (RZ) | **0.896** |
| RPI — Reference Waste Rock (RWR) | **0.203** |
| XRF calibration points | **64** |
| Spearman ρ (RPI vs XRF) | **0.845** |
| p-value (RPI vs XRF) | **1.74 × 10⁻¹²** |
| Unmixing method | **VCA + FCLS (linear mixing)** |
| RPI calibration | **Isotonic regression** |

---

## Cross-Cutting Facts

| What | Answer |
|------|--------|
| Study site | **Benguerir phosphate mine, Morocco** |
| Operator | **OCP Group (Accord-Specific 189: SPGP)** |
| Mine surface area | **36 km²** |
| Thesis pages | **155** |
| Publications (total) | **4** (Sensors 2025, IJEST 2024, Mining 2023, BDJ 2023) |
| Papers in pipeline | **2** (Minerals Ch.2, TBD Ch.3) |
| Sensors 2025 DOI | **10.3390/s26010002** |
| Defense date | **June 30, 2026** |
| Institution | **UM6P, GSMI, Benguerir** |
| Supervisor | **Pr. [[Ahmed Laamrani]]** |
| Co-supervisors | **Benzaazoua, Elghali, Hakkou** |
| Jury president | **Pr. Abdelghani CHEHBOUNI** |
| Highest-threat referee | **Pr. Jochem VERRELST (Valencia)** |

---

## Flash Cards — 10 Critical Numbers

> If you only have 5 minutes, memorize these 10.

| # | Question | Answer |
|---|----------|--------|
| 1 | BAC Ch.3 | **0.984 ± 0.031** |
| 2 | AUC Ch.3 | **1.000** |
| 3 | RPI reclaimed zone | **0.896** |
| 4 | RPI reference waste rock | **0.203** |
| 5 | RPI-XRF correlation (ρ) | **0.845** |
| 6 | p-value correlation | **1.74 × 10⁻¹²** |
| 7 | BAC Ch.2 | **0.60–0.67** |
| 8 | Ch.2 independent samples | **127** |
| 9 | Mean R² Ch.1 | **0.748** |
| 10 | Valid EnMAP bands | **189** |




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Oral Practice Log.md (~376 words)
================================================================================
---
tags:
  - defense
  - log
  - practice
  - topic/thesis
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-08'
---

# Oral Practice Log

> One row per rehearsal session. Be honest — weak spots are the ones to fix.
> Target: 45 min full run, confident on all numbers, clean answer to Verrelst questions.
> See also: [[Defense Strategy]] · [[Jury Questions Prep]] · [[Jury Questions Prep — Advanced]] · [[Numbers Arsenal]] · [[36-Day Sprint]]

---

## Progress Chart

```dataviewjs
const rows = dv.pages('"02_Academic & Work/thesis/defense-prep"')
  .where(p => p.file.name === "Oral Practice Log");
// Manual log below — chart builds as you add rows
const sessions = [
  // { date: "2026-06-07", duration: 0, confidence: 0, weakSection: "—" }
];
if (sessions.length === 0) {
  dv.paragraph("> No sessions logged yet. Add your first row below.");
} else {
  const avg = (sessions.reduce((a,b) => a + b.confidence, 0) / sessions.length).toFixed(1);
  dv.paragraph(`**Sessions:** ${sessions.length} | **Avg confidence:** ${avg}/10 | **Last run:** ${sessions[sessions.length-1].date}`);
}
```

---

## Session Log

| Date | Duration (min) | Confidence (1–10) | Weakest section | Question that stumped me | Notes |
|------|---------------|-------------------|----------------|--------------------------|-------|
| | | | | | First session |

---

## Recurring Weak Spots

> Update after each session. If the same thing shows up 3 times, it's a real gap.

- 

---

## Verrelst Question Drill Tracker

| Question | Times drilled | Last answer quality | Notes |
|----------|--------------|--------------------|----|
| Why linear unmixing vs nonlinear? | 0 | — | |
| Justify k=4 endmembers | 0 | — | |
| Why isotonic regression? | 0 | — | |
| PRISMA processing pipeline | 0 | — | |
| Why BAC not OA? | 0 | — | |
| Limitation of Ch.2 spectral mixing | 0 | — | |
| RPI generalizability beyond EnMAP | 0 | — | |
| Difference PRISMA vs EnMAP choice | 0 | — | |

---

## Rules

- Log immediately after every session — don't trust memory
- If under 40 min: identify exactly which section ate time
- If confidence < 6: drill that section specifically the next day
- Defense is June 30 — every session logged is evidence of the sprint




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Session 0 — First Run.md (~563 words)
================================================================================
---
tags:
  - defense
  - practice
  - session
  - topic/thesis
generated_by: claude
date: 2026-06-07
type: thesis-note
status: active
created: '2026-06-07'
---

# Session 0 — First Oral Run

> Do this tonight. You don't need slides to be perfect. You need to start.
> Target: 45 min. Reality for session 0: probably 30–55 min. Both are fine.

---

## Before You Start (5 min)

1. Close everything except Obsidian
2. Open [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal]] — read once, then close it
3. Stand up. You will present standing, so practice standing.
4. Start a timer on your phone

---

## The Run (45 min target)

Present your thesis out loud, slide by slide, as if the jury is in the room.

**Speak these sections in order:**

| # | Section | Target time | Key numbers to hit |
|---|---------|------------|-------------------|
| 1 | Introduction — context, why phosphate, why RS | 5 min | 36 km², OCP Group, Morocco = 70% world reserves |
| 2 | Chapter 1 — field spectroscopy | 8 min | 104 samples, R²=0.748, 84%, P₂O₅=23.86 wt% |
| 3 | Chapter 2 — PRISMA mapping | 12 min | 207→127 samples, BAC 0.60–0.67, AUC >0.95, 60 SWIR bands |
| 4 | Chapter 3 — EnMAP RPI (spend the most time here) | 15 min | 189 bands, BAC=0.984, AUC=1.000, RPI RZ=0.896/RWR=0.203, ρ=0.845, p=1.74×10⁻¹² |
| 5 | Conclusions + perspectives | 5 min | Novelty, RPI = operational tool for OCP |

**Rules during the run:**
- Do NOT stop when you stumble — keep going like the real defense
- If you blank on a number, say "approximately X" and move on — note it after
- Do NOT look at notes mid-run

---

## After the Run — Log It (5 min)

Write one row in [[02_Academic & Work/thesis/defense-prep/Oral Practice Log]]:

```
| 2026-06-07 | [actual minutes] | [1-10] | [weakest section] | [question/number that stumped you] | Session 0 — first run |
```

Then answer these honestly:
- Which section felt the least solid?
- Which number did you blank on?
- Did you go over 45 min? Under? Where did time go?

---

## Common First-Run Problems

| Problem | What it means | Fix for Session 1 |
|---------|--------------|-------------------|
| Blanked on a number | Not memorized yet | Add it to flashcard review |
| Over 55 min | Too much detail in one chapter | Set a timer per section next run |
| Under 30 min | Skipping over methods | Slow down on VCA-FCLS explanation |
| Stumbled on Ch.3 logic | The chain isn't automatic yet | Drill the RPI construction sequence separately |
| Lost the thread between chapters | No linking narrative | Memorize the 3-sentence bridge |

---

## The 3-Sentence Bridge (memorize this)

> *"Chapter 1 gave us the spectral fingerprint of the surface mineralogy at field scale. Chapter 2 scaled that knowledge to satellite imagery, producing a lithological map of the entire mine. Chapter 3 went further — using EnMAP to detect and quantify the impact of reclamation activities, producing a novel index — the RPI — validated against independent geochemical data."*

---

## Session 0 Done → Open Tomorrow's Daily Note

After logging, open `Ctrl+Shift+D` for tomorrow, set your focus: which section to drill based on what just broke.




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Victory Speech.md (~615 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags:
  - defense
  - june-30
  - opening
  - speech
  - topic/thesis
duration: 3 minutes (~470 words)
note: "Delivered in French at the defense \u2014 this is the English reference version"
type: thesis-note
status: active
created: '2026-06-08'
---

# Opening Speech — June 30, 2026

> Memorize this. Not word for word — the structure, the ideas, the numbers.
> When you walk into that room, you already know what you're going to say.
> The first minute determines everything that follows.

---

Mr. President, Ladies and Gentlemen of the jury,

I am Abdelhak EL MANSOUR, doctoral candidate at the Institute of Geology and Sustainable Mining at Mohammed VI Polytechnic University.

I am defending today my thesis entitled: *"Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and [[Reclamation Monitoring]] of [[Phosphate Mine Waste]] Rocks at Benguerir Mine, Morocco."*

Allow me to begin with something simple.

I come from Errachidia — a desert town in Morocco, far from major universities, far from satellites. You are not born there with a spectrograph in your hands. But you learn very early that geology is not an abstraction: it is the rock underfoot, the resources in the ground, the phosphate that feeds continents.

That is where this work comes from.

The Benguerir mine, operated by OCP Group, is one of the largest phosphate mines in the world. It feeds global agriculture. It also leaves behind millions of tonnes of waste rock — heterogeneous, difficult to map, whose reclamation is a real environmental challenge. The problem is not academic: knowing what a waste pile contains, knowing whether reclamation is progressing — these are questions with concrete economic and human stakes.

To answer them, I built an integrated three-scale framework.

**First scale — the field.** One hundred and four waste rock samples, an ASD spectroradiometer covering 350 to 2500 nanometers, and a portable X-ray fluorescence instrument. I described the surface mineralogy with a precision that conventional point analyses cannot deliver. Work published in *Sensors* in 2025.

**Second scale — space, with PRISMA.** Two hundred and thirty-nine spectral bands, 30-meter resolution. One hundred and twenty-seven spatially independent samples. Four lithological classes. Ensemble models, strictly geographically constrained cross-validation. Honest performance — reflecting the real physical limit of the problem, not a statistical illusion.

**Third scale — monitoring, with EnMAP.** And here, I developed something new.

The *[[Reclamation Progress Index]]* — a spectral indicator calibrated against independent geochemical data, capable of quantifying the reclamation state of a pixel from orbit. The results are unambiguous: AUC equal to 1.000, Spearman correlation ρ = 0.845, p = 1.74 × 10⁻¹². Validated on 64 independent XRF calibration points. This is not an academic prototype — it is a functional tool, delivered to OCP Group, documented in a 155-page manuscript.

This work was made possible by the rigorous and supportive supervision of [[02_Academic & Work/org/people/Ahmed Laamrani\|Professor Ahmed Laamrani]], and the constant backing of Professors Benzaazoua, Elghali, and Hakkou. It benefited from a research stay at the University of Valencia — where I had the privilege of working with Professor Verrelst. His presence on this jury is both an honor and a standard I fully accept.

I am ready. Over to you.

---

## Performance Notes

- **Tone:** calm, unhurried. You are not trying to convince. You are presenting.
- **On "Errachidia":** slight pause after. Let it breathe.
- **On the numbers:** AUC = 1.000 — say it once, clearly, without explaining it. The jury knows what it means.
- **On "Over to you":** make eye contact with the jury. Do not look down.
- **Target timing:** 2 min 45 — 3 min 00.
- **Delivered in French at the actual defense** — practice in French.



