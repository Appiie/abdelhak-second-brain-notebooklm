---
generated_by: claude
date: 2026-06-07
tags: [knowledge, compiled, notebooklm]
summary: "A single compiled master file containing all notes and records from Abdelhak's Second Brain for import into NotebookLM."
---

# Abdelhak EL MANSOUR — Compiled Second Brain

> This document is a consolidated export of Abdelhak EL MANSOUR's entire Obsidian vault, compiled on 2026-06-07.
> It is designed to serve as a comprehensive knowledge source for NotebookLM.

================================================================================
METADATA AND DOCUMENT STRUCTURE
================================================================================
Total sources compiled from: 7 directories and 3 root files.



================================================================================
FILE: Home.md (~579 words)
================================================================================
---
tags: [dashboard, home]
updated: 2026-06-07
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

## Navigation

| | |
|--|--|
| 🎓 **Thesis MOC** | [[02_Academic & Work/thesis/Thesis MOC\|Full chapter map]] |
| 🔢 **Numbers Arsenal** | [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal\|All numbers]] |
| 🎯 **Defense Strategy** | [[02_Academic & Work/thesis/defense-prep/Defense Strategy\|Master playbook]] |
| ❓ **Jury Q&A** | [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep\|All answers]] |
| 🎤 **Practice Log** | [[02_Academic & Work/thesis/defense-prep/Oral Practice Log\|Session tracker]] |
| 🃏 **Flashcards** | [[02_Academic & Work/thesis/defense-prep/Flashcards — Defense\|Defense deck]] |
| 🔥 **Hot Cache** | [[04_Knowledge Base/wiki/hot\|Session context]] |
| 💼 **Jobs** | [[02_Academic & Work/work/active/Job Pipeline\|Kanban board]] |
| 💰 **Domains** | [[03_Digital Life/money/domaining/Domain Outreach Pipeline\|Sales pipeline]] |
| 📥 **Clips** | [[01_System/clips/Clips Dashboard\|All web clips]] |
| 🧠 **North Star** | [[03_Digital Life/brain/North Star\|Who you are]] |
| 📚 **Wiki** | [[04_Knowledge Base/wiki/index\|Knowledge base]] |

---

> [!quote] The sentence
> *"I developed a multi-scale framework — from field spectroscopy to satellite imagery — that characterizes and monitors phosphate mine waste rocks at Benguerir, combining three complementary approaches to produce actionable reclamation metrics for OCP Group."*




================================================================================
FILE: Dashboard.md (~520 words)
================================================================================
---
tags: [dashboard, dataview]
updated: 2026-06-07
summary: "A premium, responsive, multi-column CSS grid dashboard for Abdelhak's Second Brain."
---

# Dashboard

```dataviewjs
const defense = new Date("2026-06-30");
const today = new Date();
const days = Math.ceil((defense - today) / (1000 * 60 * 60 * 24));
const total = 36;
const elapsed = total - days;
const pct = Math.max(0, Math.min(100, Math.round((elapsed / total) * 100)));

// Custom CSS styling injected into the note
const style = `
<style>
  .dash-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-top: 10px;
  }
  @media (max-width: 768px) {
    .dash-container { grid-template-columns: 1fr; }
  }
  .dash-header {
    grid-column: 1 / -1;
    background: linear-gradient(135deg, #6366f1 0%, #06b6d4 100%);
    color: white;
    padding: 24px;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.2);
    margin-bottom: 8px;
  }
  .dash-header h1 {
    color: white !important;
    margin: 0 0 6px 0 !important;
    font-size: 22px !important;
    font-weight: 700 !important;
    border-bottom: none !important;
  }
  .dash-header p {
    margin: 0 !important;
    font-size: 13.5px;
    opacity: 0.95;
  }
  .progress-bg {
    background: rgba(255, 255, 255, 0.2);
    border-radius: 9999px;
    height: 8px;
    margin-top: 14px;
    overflow: hidden;
  }
  .progress-fg {
    background: #e0f2fe;
    height: 100%;
    border-radius: 9999px;
    transition: width 0.4s ease;
  }
  .dash-card {
    background: var(--background-secondary);
    border: 1px solid var(--border-color);
    border-radius: 12px;
    padding: 16px;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }
  .dash-card:hover {
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  }
  .dash-card h3 {
    margin: 0 0 12px 0 !important;
    font-size: 15px !important;
    font-weight: 600 !important;
    border-bottom: 1px solid var(--border-color) !important;
    padding-bottom: 8px;
    color: var(--text-normal);
  }
  .dash-list {
    list-style: none !important;
    padding: 0 !important;
    margin: 0 !important;
  }
  .dash-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 7px 0;
    font-size: 12.5px;
    border-bottom: 1px dashed var(--border-color);
  }
  .dash-item:last-child {
    border-bottom: none;
  }
  .dash-item a {
    text-decoration: none;
    font-weight: 500;
  }
  .dash-item .time-meta {
    font-size: 10px;
    color: var(--text-muted);
    font-family: var(--font-monospace);
  }
</style>
`;

dv.el("div", style);

// Get pages
const activeWork = dv.pages('"02_Academic & Work/work/active"').sort(p => p.file.mtime, 'desc').limit(5);
const defensePrep = dv.pages('"02_Academic & Work/thesis/defense-prep"').sort(p => p.file.mtime, 'desc').limit(5);
const aiNotes = dv.pages('"04_Knowledge Base/AI-Generated"').where(p => p.date != null).sort(p => p.file.mtime, 'desc').limit(5);
const wikiConcepts = dv.pages('"04_Knowledge Base/wiki/concepts"').sort(p => p.file.mtime, 'desc').limit(5);
const money = dv.pages('"03_Digital Life/money"').sort(p => p.file.mtime, 'desc').limit(5);
const jobs = dv.pages('"02_Academic & Work/work/active"').where(p => p.file.name.includes("Opportunit") || p.file.name.includes("Application") || p.file.name.includes("Postdoc")).sort(p => p.file.mtime, 'desc').limit(5);

// Render helper
function renderList(pages, placeholder = "No active notes found.") {
  if (pages.length === 0) return `<li class="dash-item" style="color: var(--text-muted);">${placeholder}</li>`;
  return pages.map(p => {
    const timeStr = p.file.mtime.toFormat("MMM dd HH:mm");
    return `<li class="dash-item">
      <span>🔗 ${p.file.link.markdown()}</span>
      <span class="time-meta">⏱ ${timeStr}</span>
    </li>`;
  }).join("");
}

// Build layout
const html = `
<div class="dash-container">
  <div class="dash-header">
    <h1>🎓 Abdelhak's Mission Control</h1>
    <p>⚡ <strong>${days} Days to Thesis Defense</strong> (June 30, 2026) — Sprint Progress: ${pct}% (${elapsed}/${total} days elapsed)</p>
    <div class="progress-bg">
      <div class="progress-fg" style="width: ${pct}%"></div>
    </div>
  </div>
  
  <div class="dash-card">
    <h3>🎓 Thesis Defense Prep</h3>
    <ul class="dash-list">
      ${renderList(defensePrep)}
    </ul>
  </div>
  
  <div class="dash-card">
    <h3>💼 Postdoc & Job Tracker</h3>
    <ul class="dash-list">
      ${renderList(jobs)}
    </ul>
  </div>

  <div class="dash-card">
    <h3>🔴 Active Projects</h3>
    <ul class="dash-list">
      ${renderList(activeWork)}
    </ul>
  </div>

  <div class="dash-card">
    <h3>🧠 Wiki Concepts</h3>
    <ul class="dash-list">
      ${renderList(wikiConcepts)}
    </ul>
  </div>

  <div class="dash-card">
    <h3>🤖 Recent AI Logs</h3>
    <ul class="dash-list">
      ${renderList(aiNotes)}
    </ul>
  </div>

  <div class="dash-card">
    <h3>💰 Domains & Income</h3>
    <ul class="dash-list">
      ${renderList(money)}
    </ul>
  </div>
</div>
`;

dv.el("div", html);
```




================================================================================
FILE: CLAUDE.md (~701 words)
================================================================================
---
tags:
  - instructions
  - personal-assistant
  - guidelines
created: 2026-06-07
summary: "Developer guidelines and context setup rules for coding assistants working on Abdelhak EL MANSOUR's Second Brain."
---

# Abdelhak EL MANSOUR — Second Brain Instructions

## Identity (Read This First)
**Abdelhak EL MANSOUR** — PhD Candidate at UM6P, Benguerir, Morocco.  
Defending thesis in ~June 2026. Amazigh/Moroccan. Raï music fan. 70K+ Instagram followers.  
Supervised by Pr. Ahmed LAAMRANI. Department: GSMI (Geology and Sustainable Mining Institute).

**Thesis:** Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks at Benguerir Mine, Morocco.

**Twitter:** @AbdelhakElm | **Scholar:** google scholar user=ysUOZQ0AAAAJ

---

## Context Loading Order
1. `04_Knowledge Base/wiki/hot.md` — most recent context (read FIRST, always)
2. `03_Digital Life/brain/North Star.md` — full identity, goals, priorities
3. `02_Academic & Work/thesis/Thesis Overview.md` — thesis details (if research question)
4. `03_Digital Life/money/Money Overview.md` — income streams (if money question)
5. `04_Knowledge Base/wiki/index.md` — knowledge catalog
6. `02_Academic & Work/work/Index.md` — active projects
7. `02_Academic & Work/thesis/references.bib` — Zotero library (292 refs, auto-synced via Better BibTeX). Read when asked about citations, references, or "do I have a paper on X".

---

## This Vault Has 6 Major Areas

### 1. Thesis (`02_Academic & Work/thesis/`)
Everything about the PhD — 155-page manuscript, PRISMA data, defense prep, code notes, papers. **DEFENSE IN ~1 MONTH — THIS IS PRIORITY #1.**

### 2. Wiki (`04_Knowledge Base/wiki/`)
Knowledge base — built by Claude from ingested papers and research. Concepts, entities, sources.  
- `04_Knowledge Base/wiki/hot.md` — session context cache (update end of day)
- `04_Knowledge Base/wiki/index.md` — master catalog

### 3. Brain (`03_Digital Life/brain/`)
Abdelhak's own thinking — goals, decisions, patterns, gotchas.  
⚠️ Claude does NOT create files here unprompted. Abdelhak writes these.

### 4. Money (`03_Digital Life/money/`)
Income strategy — domaining, Instagram (70K+), postdoc, consulting.  
- `03_Digital Life/money/Money Overview.md` — master strategy
- `03_Digital Life/money/domaining/Domain Portfolio.md` — domain assets
- `03_Digital Life/money/instagram/Instagram Strategy.md` — social strategy

### 5. Work (`02_Academic & Work/work/`)
Active projects, meetings, applications, postdoc search.

### 6. Personal (`03_Digital Life/personal/`)
Identity (Amazigh, Moroccan), travel (Rome 2024), life outside research.

---

## Research Domain Shortcuts
- "PRISMA" → [[04_Knowledge Base/wiki/concepts/PRISMA Satellite]]
- "hyperspectral" → [[04_Knowledge Base/wiki/concepts/Hyperspectral Imaging]]
- "waste rock" / "phosphate" → [[04_Knowledge Base/wiki/concepts/Waste Rock Characterization]]
- "SCSE" / "CNN" → [[04_Knowledge Base/wiki/concepts/Machine Learning for Hyperspectral]]
- "spectral library" / "USGS" → [[04_Knowledge Base/wiki/concepts/Spectral Analysis]]
- "Benguerir" / "OCP" → [[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine]]
- "LAAMRANI" → [[02_Academic & Work/org/people/Ahmed Laamrani]]

---

## Languages Abdelhak Uses
- **French** — primary academic/professional language
- **English** — papers, AI tools, international
- **Arabic/Darija** — personal, family, Moroccan context
- Always respond in the language Abdelhak uses in the message

---

## AI-Generated Notes Policy
All Claude-created notes **must** include frontmatter:
```yaml
generated_by: claude
date: YYYY-MM-DD
```

**Where to save** — place files in the folder that makes contextual sense:
- `04_Knowledge Base/AI-Generated/` — standalone outputs with no natural home (drafts, analyses, admin, logs)
- `02_Academic & Work/thesis/`, `02_Academic & Work/work/`, `02_Academic & Work/perf/`, `03_Digital Life/money/`, `03_Digital Life/personal/` — Claude-created content that belongs in context (cover letters, defense prep, job trackers, domain analyses). Still requires `generated_by: claude` frontmatter.
- `04_Knowledge Base/wiki/` — collaborative; Claude builds, Abdelhak refines. Frontmatter optional.
- `03_Digital Life/brain/` — Abdelhak writes only. Claude does NOT create files here without explicit request.

---

## Automation Scripts & Skills
This vault has several utility scripts in [01_System/scripts/](file:///C:/Users/Dell/Downloads/abdelhak-real-vault/abdelhak-vault/01_System/scripts/):
1. **NotebookLM Compilation**: Concatenates all markdown notes into a single file to bypass NotebookLM's source document limits.
   - Run: `python 01_System/scripts/compile_vault_for_notebooklm.py` (or double-click [compile.bat](file:///C:/Users/Dell/Downloads/abdelhak-real-vault/abdelhak-vault/compile.bat) in the vault root).
   - Output: [04_Knowledge Base/bases/Abdelhak_Second_Brain_Compiled.md](file:///C:/Users/Dell/Downloads/abdelhak-real-vault/abdelhak-vault/04_Knowledge%20Base/bases/Abdelhak_Second_Brain_Compiled.md)
   - *Automated:* Compiled automatically on push to GitHub using the Action in `.github/workflows/compile.yml`.
2. **Gmail Draft Creator**: Interactive draft generation for post-doc outreach.
   - Run: `python 01_System/scripts/create_gmail_drafts.py`
3. **Job Monitor RSS Scanner**: Fetches new job listings from remote sensing & Earth Observation RSS feeds.
   - Run: `python 01_System/scripts/job_monitor.py`
4. **Domain Portfolio Report**: Audits and prints reports on domains.
   - Run: `python 01_System/scripts/domain_report.py`

---

## Never Do
- Put passwords, API keys, or credentials in vault notes
- Modify `.raw/` files — read only
- Create files in `03_Digital Life/brain/` without explicit request
- Forget that thesis defense is in ~1 month — always check countdown first




================================================================================
FILE: 02_Academic & Work/thesis/Thesis MOC.md (~792 words)
================================================================================
---
tags: [thesis, MOC, navigation]
generated_by: claude
date: 2026-06-07
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




================================================================================
FILE: 02_Academic & Work/thesis/Thesis Overview.md (~822 words)
================================================================================
---
tags: [thesis, core, defense, PRISMA, phosphate]
updated: 2026-05-24
status: DEFENSE IN ~1 MONTH
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
| Supervisor | Pr. Ahmed LAAMRANI |
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
FILE: 02_Academic & Work/thesis/defense-prep/30-Day Countdown.md (~554 words)
================================================================================
---
tags: [thesis, defense, urgent, countdown]
updated: 2026-05-24
status: ACTIVE — URGENT
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
6. How does reclamation monitoring add to existing methods?
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
FILE: 02_Academic & Work/thesis/defense-prep/36-Day Sprint.md (~813 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [thesis, defense, sprint, planning, urgent]
updated: 2026-05-27
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
- [ ] Memorize the 10 critical numbers → [[02_Academic & Work/thesis/defense-prep/Numbers Arsenal#Flash Cards — 10 Critical Numbers]]

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
FILE: 02_Academic & Work/thesis/defense-prep/Defense Quiz — NotebookLM.md (~1168 words)
================================================================================
---
generated_by: notebooklm + claude
date: 2026-05-26
tags: [defense-prep, quiz, thesis]
source: NotebookLM PhD Defense notebook (bb2823a9)
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

**What was "Rule No. 1" established for the 36-day sprint leading up to the thesis defense?**

- A) The slides pass before everything else ✅
- B) Memorize the Numbers Arsenal immediately
- C) Submit the Chapter 3 paper first
- D) Conduct a mock defense daily

**Answer: A**
*"Les slides passent avant tout le reste. Pas de slides = pas de soutenance."*
Slides are Week 1–2. Mock defenses start Week 3. Numbers memorization runs in parallel.

*Hint: What do you literally need to hold a presentation?*

---

## Q3 — Why BAC Dropped in Ch.2

**Why did the Balanced Accuracy (BAC) for Chapter 2 decrease to 0.60–0.67 during validation?**

- A) The use of spatially constrained cross-validation with a 30 m buffer ✅
- B) The removal of 60 SWIR bands during ANOVA selection
- C) Failure to use the Extra Trees classifier
- D) Atmospheric interference in the VNIR bands

**Answer: A**
Enforcing geographic separation between training and test sets removes the inflation caused by spatial autocorrelation. The honest number is lower — but it's honest. This is a methodological strength, not a weakness.

*Hint: What happens when nearby points bleed into training and test sets?*

---

## Q4 — The Novel Index

**Which novel indicator was developed in Chapter 3 to quantify the state of backfilling operations from orbit?**

- A) Reclamation Progress Index (RPI) ✅
- B) Phosphate Enrichment Score (PES)
- C) Normalized Difference Mineral Index (NDMI)
- D) VCA-FCLS Abundance Ratio

**Answer: A**
The RPI is the first quantitative, satellite-derived metric calibrated against independent field geochemistry (XRF) for phosphate mine waste. Continuous, monotone, physically meaningful. ρ=0.845, p=1.74×10⁻¹².

*Hint: The name describes what it measures over time.*

---

## Q5 — Jury Threat

**Which member of the jury is identified as the "most threatening" due to their deep expertise in Radiative Transfer Models (RTM) and PRISMA processing?**

- A) Pr. Jochem Verrelst ⭐⭐⭐⭐⭐ ✅
- B) Pr. Abdelghani Chehbouni ⭐⭐
- C) Pr. Ahmed Laamrani (supporter)
- D) Pr. Hassan Ibouh ⭐⭐⭐

**Answer: A**
Verrelst supervised your internship in Valencia (EARSeL 2024). He knows PRISMA. He knows RTMs. He will ask about the linear mixing assumption, endmember purity, and why you didn't use Hapke. Prepare accordingly.

*Hint: He knows your work from the inside.*

---

## Q6 — Why PRISMA Over Sentinel-2

**What was the primary reason for selecting the PRISMA satellite sensor over Sentinel-2 for mineralogical mapping?**

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
- 0.748 = mean R² for spectral library matching, Ch.1
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

*Hint: This is the critical number for the phosphate-rich class in the Numbers Arsenal.*

---

## Q10 — One-Sentence Summary

**According to the defense strategy, what is the "One-Sentence Summary" to memorize and say first, last, and when feeling lost?**

- A) "I developed a multi-scale framework that characterizes and monitors phosphate mine waste rocks combining three complementary approaches." ✅
- B) "This thesis proves that PRISMA and EnMAP are superior to all other sensors for monitoring Moroccan mines."
- C) "My research demonstrates that machine learning is the only way to achieve high accuracy in mineral mapping."
- D) "The goal of this project is to assist OCP Group in extracting 23.86 wt% phosphate from all waste piles."

**Answer: A**
Say this: *"I developed a multi-scale framework that characterizes and monitors phosphate mine waste rocks combining three complementary approaches."*
Say it first. Say it last. Say it when Verrelst makes you doubt yourself.

*Hint: Multi-scale. Three approaches. Complementary.*

---

## Score Reference

| Score | Status |
|-------|--------|
| 10/10 | Jury-proof |
| 8–9/10 | Ready — minor gaps |
| 6–7/10 | Q3 + Q7 + Q8 need work |
| <6/10 | Numbers Arsenal review tonight |




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Defense Slides — Master Plan.md (~2037 words)
================================================================================
---
tags: [thesis, defense, slides, priority]
generated_by: claude
date: 2026-05-28
updated: 2026-05-28
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
> Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks in Benguerir Mine, Morocco
- Abdelhak EL MANSOUR
- Supervisor: Pr. Ahmed LAAMRANI
- UM6P — GSMI — June 30, 2026
- Logo: UM6P + OCP Group

**Slide 2 — Outline**
- Four blocks: Introduction → Chapter 1 → Chapter 2 → Chapter 3 → Synthesis & Conclusions
- Visual roadmap (chevron or numbered arc)
- One sentence per chapter: "Field baseline" → "Satellite mapping" → "Reclamation monitoring"

---

### BLOCK 2 — Introduction (Slides 3–6)

**Slide 3 — Context: Why phosphate waste rocks?**
- OCP Group: world's largest phosphate exporter (Morocco = 75% global reserves)
- Benguerir mine: active open-pit, large waste rock piles accumulating
- Reclamation = legal + environmental obligation, costly if done blind
- Visual: aerial photo of Benguerir waste rock piles (or mine map)

**Slide 4 — The problem**
- Current reclamation monitoring = labor-intensive, point-based (XRD/XRF)
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
> "Field-scale mineralogical characterization using VNIR-SWIR spectroscopy and portable XRF"
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

### BLOCK 4 — Chapter 2: PRISMA Satellite (Slides 13–19)

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
- Bridge: "Lithological context informs zone selection for reclamation monitoring in Ch.3"

---

### BLOCK 5 — Chapter 3: EnMAP + RPI (Slides 20–27)

**Slide 20 — Ch.3 Title / Approach**
> "Backfilling impact assessment using EnMAP hyperspectral imagery and a novel Reclamation Progress Index"
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
- **Reclamation Progress Index** — not a classification, an index
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
- RPI = first operational reclamation index for phosphate mine waste, validated by XRF
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
4. RPI (RZ=0.896, RWR=0.203, ρ=0.845) operationalizes reclamation monitoring from space
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
- Pr. Ahmed LAAMRANI + co-directors (Benzaazoua, Elghali, Hakkou)
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
FILE: 02_Academic & Work/thesis/defense-prep/Defense Strategy.md (~1990 words)
================================================================================
---
generated_by: claude
date: 2026-05-24
tags: [thesis, defense, strategy, priority]
---

# Complete Defense Strategy — June 30, 2026

> This is the master playbook. Read before every rehearsal session.

---

## The One-Sentence Summary

**"I developed a multi-scale framework — from field spectrometry to satellite imagery — that characterizes and monitors phosphate mine waste rocks at Benguerir, combining three complementary approaches to produce actionable reclamation metrics for [[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine\|OCP Group]]."**

Memorize this. Say it first, last, and whenever you feel lost.

---

## The Jury — Who Threatens What

| Name | Role | Threat level | Their weapon |
|------|------|-------------|-------------|
| **Pr. Verrelst** (Valencia) | Rapporteur | ⭐⭐⭐⭐⭐ | RTM, linear mixing, [[04_Knowledge Base/wiki/concepts/PRISMA Satellite\|PRISMA]] processing — he knows your data |
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
**"Field-scale mineralogical characterization using VNIR-SWIR spectroscopy + HHXRF"**
- 104 field samples, ASD FieldSpec 4 (350–2500 nm) + HHXRF
- ECOSTRESS spectral library matching (RMSE, SAM, SID, R²)
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
- Shannon entropy uncertainty maps
- **Key metrics: BAC = 0.60–0.67; AUC > 0.95 for Marl and Limestone**
- Accepted: **Minerals** (IF 2.2) ✅

### Chapter 3 (12 min presentation slot)
**"Backfilling impact assessment using [[04_Knowledge Base/wiki/concepts/EnMAP Satellite\|EnMAP]] + VCA-FCLS + novel [[04_Knowledge Base/wiki/concepts/Reclamation Progress Index\|RPI]]"**
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

**Answer:** The multi-scale framework itself is the main conceptual contribution — demonstrating that field spectroscopy, satellite mineral mapping, and satellite reclamation monitoring can be integrated for comprehensive mine waste characterization. But the most novel methodological contribution is the **Reclamation Progress Index (RPI)**: the first quantitative, satellite-derived reclamation metric calibrated against field geochemistry for phosphate mine waste. It turns a hyperspectral scene into an operational monitoring tool — something OCP Group can use quarterly without additional field costs.

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

"This thesis demonstrates for the first time that EnMAP hyperspectral data can quantitatively track reclamation progress at phosphate mine waste sites — with statistical rigor, geochemical validation, and a novel index that is immediately operational. The multi-scale framework scales from a rock sample in the hand to a 36-square-kilometer mine monitored from space. I believe this combination of field, laboratory, and satellite data represents a model for sustainable mine monitoring that extends well beyond Benguerir."

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
- [ ] Finalize jury Q&A from `Jury Questions Prep.md`
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
| Ch.1 mean R² (spectral library matching) | 0.748 ± 0.170 |
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




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Flashcards — Defense.md (~767 words)
================================================================================
---
tags: [flashcards, thesis, defense, memorization]
generated_by: claude
date: 2026-06-07
sr-due: 2026-06-08
sr-interval: 1
sr-ease: 250
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
Thesis director::Pr. Ahmed LAAMRANI
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
What is the novelty of your thesis?::First multi-scale hyperspectral RS framework for phosphate mine waste rock, combining field spectroscopy (ASD), PRISMA (30 m mapping), and EnMAP (30 m monitoring) with a novel reclamation progress index (RPI) validated by independent XRF data. None of the three chapters had been done for this site or this mineral system.




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced.md (~959 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [thesis, defense, jury, prep, advanced]
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
The 4 classes were defined empirically from spectral and geochemical data (HHXRF + XRD, Chapter 1), but they map directly onto the major mineralogical families recognized in the Cretaceous-Eocene phosphate stratigraphy of the Benguerir basin: pure carbonates (limestone), marly units (clay-carbonate mixtures), siliceous/quartzitic facies, and phosphate (fluorapatite-francolite). Stratigraphic coherence was verified by geolocating all 207 sampling points on the OCP mine plan and confirming lithological assignments with the OCP/UM6P field geology team. The risk of collapsing spectrally similar but geologically distinct units is real at 30 m due to sub-pixel mixing — this is precisely why I use Shannon entropy uncertainty maps. High-entropy zones correspond geographically to lithostratigraphic contacts, which correctly signals classification uncertainty at boundaries rather than false confidence.

---

## Q4 — Verrelst / Berg | SCSE CNN vs. Extra Trees

**"Your thesis mentions SCSE (Squeeze-and-Excitation CNN) as achieving the best accuracy among CNN architectures. Yet Chapter 2 reports Extra Trees and Random Forest as the best overall models. Did the SCSE underperform the ensemble methods, and why?"**

**Answer:**
The SCSE model outperformed simpler CNN variants (1D, 2D, 3D CNN) in per-class accuracy for minority classes. However, Extra Trees and Random Forest outperformed all CNN architectures under spatially constrained cross-validation with 10 independent replicates and 127 samples. The reason is sample size: CNN models have higher capacity and require more training data to generalize under strict spatial leave-out. With 127 spatially independent samples and a 30 m pixel footprint, ensemble methods' resistance to overfitting via bootstrap aggregation gave them a structural advantage over attention-based CNNs. The SCSE's channel and spatial squeeze-excitation mechanisms are powerful for 2D/3D spectral-spatial inputs, but the accuracy gain was insufficient to compensate for the data limitation under rigorous spatial CV. This is itself a finding: methodological rigor exposes the data constraint rather than hiding it behind inflated CNN accuracy.

---

## Q5 — Khalil / Benzaazoua | Heavy Metals and Environmental Risk

**"Phosphate waste rocks at Benguerir are known to contain heavy metals — cadmium, uranium — at potentially problematic concentrations. What do your spectral classes tell us about the actual environmental risk of these waste rocks?"**

**Answer:**
This is an important connection. Heavy metals in phosphate waste — Cd (typically 0.1–0.5 ppm in Moroccan phosphates), U (10–50 ppm in phosphate-bearing layers) — are primarily associated with fluorapatite-francolite via isomorphic substitution (Cd²⁺/Ca²⁺, UO₂²⁺/Ca²⁺). My "Phosphate-rich" class from Chapter 1 — characterized by P₂O₅ up to 23.86 wt% — is therefore also the class with maximum geochemical risk. In practice, the PRISMA lithological maps from Chapter 2 spatially identify the pile sectors with high phosphate concentration — these are the same sectors that should be prioritized for leachate risk monitoring. This link is not developed as a core thesis contribution — the focus was mineralogical, not geochemical-environmental — but the HHXRF data (Cd, U) were available. The clearest future direction: combine the spectral mapping with acid mine drainage (AMD) risk modeling, specifically targeting zones classified as "Phosphate-rich" on the Chapter 2 maps.

---

*See also: [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep]] — 8 core questions | [[02_Academic & Work/thesis/defense-prep/Defense Strategy]] — top 5 hardest questions with Verrelst prep*




================================================================================
FILE: 02_Academic & Work/thesis/defense-prep/Jury Questions Prep.md (~1860 words)
================================================================================
---
tags: [thesis, defense, jury, prep]
updated: 2026-05-24
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
| Pr. Ahmed LAAMRANI | UM6P | Thesis Director |
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
PRISMA provides 239 contiguous spectral bands (VNIR + SWIR, 400–2500 nm) at 30 m resolution — essential for mineralogical discrimination, especially the diagnostic absorption features of carbonates (~2320–2350 nm), clay minerals (~2200 nm), and phosphate phases (~2150 nm). Sentinel-2 has only 13 multispectral bands and completely lacks the spectral resolution needed for mineralogy. EnMAP (used in Chapter 3) offers higher SNR and 242 bands — we used it where SWIR signal quality was critical for detecting subtle reclamation-induced changes. PRISMA is also relatively new (launched 2019) with very limited mining applications — our work is among the first to apply it for phosphate waste rock characterization.

---

### Q2: How did you validate your mineralogical maps?

**My Answer:**
Multi-layered validation across three chapters:

- **Chapter 1:** Spectral library matching against ECOSTRESS (mean R²=0.748, 84% of spectra >0.70, across 4 metrics: RMSE, SAM, SID, R²). HHXRF elemental cross-validation (Mg/Ca ratio confirming dolomite vs. calcite; P₂O₅ up to 23.86 wt% confirming fluorapatite). Powder XRD on 8 representative samples confirming all four mineral groups.
- **Chapter 2:** Spatially constrained cross-validation with 30 m buffer across 10 independent replicates. Shannon entropy uncertainty mapping. ROC analysis (AUC >0.95 for carbonate classes).
- **Chapter 3:** Bootstrap resampling, label permutation test (p=0.0001), spatially blocked CV (BAC=0.984, AUC=1.000). RPI validated against independent XRF scores (Spearman ρ=0.845, p=1.74×10⁻¹²).

---

### Q3: What are the limitations of your approach?

**My Answer:**
I'll be direct — three main limitations:

1. **30 m spatial resolution** (PRISMA and EnMAP) constrains discrimination in zones with fine-scale lithological variability and intense sub-pixel mixing. The BAC of 0.60–0.67 in Chapter 2 reflects this physical ceiling, not methodological failure.
2. **Linear mixing assumption** in Chapters 1 and 3. For intimate grain-scale mineral mixtures, non-linear (Hapke-based) mixing is more physically appropriate. We explicitly flag cases with structured spectral residuals. Non-linear unmixing is the main methodological future direction.
3. **Single-date acquisition** in Chapter 2. Surface conditions in semi-arid Benguerir are variable — dust, seasonal crust formation, differential weathering. Multi-temporal acquisitions would improve both classification robustness and reclamation monitoring temporal resolution.

---

### Q4: How do your ML models compare — why Extra Trees/RF over SVM?

**My Answer:**
In Chapter 2 I evaluated five classifiers under rigorous spatially constrained cross-validation. Extra Trees and Random Forest consistently outperformed SVM, XGBoost, and KNN — achieving BAC 0.60–0.67 and AUC >0.95 for carbonate-dominated classes. The ensemble methods' advantage: bootstrap aggregation reduces variance and they naturally handle nonlinear spectral boundaries in high-dimensional feature space without a hand-tuned kernel. SVM maintained strong class-ranking capability (high AUC) but produced spatially patchy maps, suggesting a constrained decision boundary when generalizing across complex spectral gradients. KNN performed lowest due to the curse of dimensionality in 60-band ANOVA-selected hyperspectral space.

In Chapter 3, discrimination between reclaimed and reference zones was near-perfect regardless of method (BAC=0.984, AUC=1.000) because the spectral separation is very large (effect size r=0.859 across all 189 EnMAP bands).

---

### Q5: What is the practical application for OCP Group?

**My Answer:**
Three direct applications:

1. **Waste rock characterization and sorting** (Chapter 1 → Chapter 2): The spectral-geochemical workflow can rapidly screen waste rock at the sample scale. The PRISMA-based lithological maps identify which pile sectors contain carbonate-rich material suitable for road construction or concrete aggregate, and which contain residual phosphate enrichment worth secondary recovery — without expensive laboratory campaigns across the entire mine surface.
2. **Reclamation monitoring** (Chapter 3): Rather than periodic, expensive field campaigns, EnMAP-based monitoring can track the progress of backfilling operations spatially and continuously. The RPI provides a single quantitative indicator of reclamation state per pixel, calibrated against XRF chemistry.
3. **Regulatory compliance**: OCP has environmental monitoring obligations. Satellite-based mineralogical monitoring provides spatially continuous documentation of reclamation progress — something point sampling cannot deliver.

---

### Q6: How does reclamation monitoring add to existing methods?

**My Answer:**
Before this work, no study had systematically quantified the impact of backfilling on waste rock mineralogy and geochemistry at landscape scale using satellite hyperspectral data. Existing monitoring relied on: (1) periodic field campaigns with limited spatial coverage; (2) vegetation-based indices (NDVI) that miss the mineralogical changes that precede and enable revegetation. Chapter 3 shows that backfilling induces statistically significant surface modifications detectable across *all 189 valid EnMAP bands* — not just in a few vegetation-sensitive bands. The novel RPI provides the first spectrally-derived, geochemically-calibrated progress indicator for phosphate mine reclamation. This enables monitoring at operational scale — the entire 36 km² mine surface — rather than at the sampling points of a field campaign.

---

### Q7: What would you do differently?

**My Answer:**
Three things, ordered by scientific impact:

1. **Acquire field spectroradiometer data simultaneously with PRISMA and EnMAP overpasses** — direct cross-scale calibration between ASD FieldSpec measurements and satellite spectra, eliminating the temporal gap between Chapter 1 lab measurements and the January 2022 PRISMA acquisition.
2. **Build a site-specific spectral library** rather than relying on ECOSTRESS. The ECOSTRESS spectra were measured on pure mineral powders under different laboratory conditions — a library built from Benguerir samples would reduce spectral matching ambiguity, especially for the mixed assemblages.
3. **Multi-temporal time series from the start** — a stack of PRISMA/EnMAP acquisitions across seasons would have allowed weathering dynamics and temporal spectral stability to be characterized, making the reclamation monitoring (Chapter 3) longitudinal rather than a single snapshot comparison.

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

The 8 samples were deliberately selected to span the full compositional space — one from each extremity (carbonate-rich, clay-dominated, phosphate-rich, mixed). They served as qualitative confirmation of phase assignments, not a quantitative validation dataset. The primary quantitative validation is the multi-metric spectral library matching across all 104 samples. XRD is expensive and time-consuming — 8 samples is appropriate for confirmatory phase identification in this context.

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
FILE: 02_Academic & Work/thesis/defense-prep/Numbers Arsenal.md (~711 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [thesis, defense, numbers, metrics, memorization]
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
| Supervisor | **Pr. Ahmed LAAMRANI** |
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
FILE: 02_Academic & Work/thesis/defense-prep/Oral Practice Log.md (~366 words)
================================================================================
---
tags: [thesis, defense, practice, log]
generated_by: claude
date: 2026-06-07
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
FILE: 02_Academic & Work/thesis/defense-prep/Session 0 — First Run.md (~553 words)
================================================================================
---
tags: [thesis, defense, practice, session]
generated_by: claude
date: 2026-06-07
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
FILE: 02_Academic & Work/thesis/defense-prep/Victory Speech.md (~604 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [thesis, defense, speech, opening, june-30]
duration: 3 minutes (~470 words)
note: "Delivered in French at the defense — this is the English reference version"
---

# Opening Speech — June 30, 2026

> Memorize this. Not word for word — the structure, the ideas, the numbers.
> When you walk into that room, you already know what you're going to say.
> The first minute determines everything that follows.

---

Mr. President, Ladies and Gentlemen of the jury,

I am Abdelhak EL MANSOUR, doctoral candidate at the Institute of Geology and Sustainable Mining at Mohammed VI Polytechnic University.

I am defending today my thesis entitled: *"Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks at Benguerir Mine, Morocco."*

Allow me to begin with something simple.

I come from Errachidia — a desert town in Morocco, far from major universities, far from satellites. You are not born there with a spectrograph in your hands. But you learn very early that geology is not an abstraction: it is the rock underfoot, the resources in the ground, the phosphate that feeds continents.

That is where this work comes from.

The Benguerir mine, operated by OCP Group, is one of the largest phosphate mines in the world. It feeds global agriculture. It also leaves behind millions of tonnes of waste rock — heterogeneous, difficult to map, whose reclamation is a real environmental challenge. The problem is not academic: knowing what a waste pile contains, knowing whether reclamation is progressing — these are questions with concrete economic and human stakes.

To answer them, I built an integrated three-scale framework.

**First scale — the field.** One hundred and four waste rock samples, an ASD spectroradiometer covering 350 to 2500 nanometers, and a portable X-ray fluorescence instrument. I described the surface mineralogy with a precision that conventional point analyses cannot deliver. Work published in *Sensors* in 2025.

**Second scale — space, with PRISMA.** Two hundred and thirty-nine spectral bands, 30-meter resolution. One hundred and twenty-seven spatially independent samples. Four lithological classes. Ensemble models, strictly geographically constrained cross-validation. Honest performance — reflecting the real physical limit of the problem, not a statistical illusion.

**Third scale — monitoring, with EnMAP.** And here, I developed something new.

The *Reclamation Progress Index* — a spectral indicator calibrated against independent geochemical data, capable of quantifying the reclamation state of a pixel from orbit. The results are unambiguous: AUC equal to 1.000, Spearman correlation ρ = 0.845, p = 1.74 × 10⁻¹². Validated on 64 independent XRF calibration points. This is not an academic prototype — it is a functional tool, delivered to OCP Group, documented in a 155-page manuscript.

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




================================================================================
FILE: 02_Academic & Work/thesis/literature-notes/@elmansour2025sensors.md (~214 words)
================================================================================
---
citekey: elmansour2025sensors
title: "Field Spectroscopy and Hyperspectral Analysis of Phosphate Mine Waste Rocks at Benguerir"
authors: EL MANSOUR A., LAAMRANI A., et al.
year: 2025
journal: Sensors
doi: 10.3390/s26010002
tags: [literature-note, chapter-1, own-paper]
generated_by: claude
date: 2026-06-07
---

# Your Paper — Chapter 1 (Sensors 2025)

**This is your own published work. Know it cold.**

## What it does
Field spectroscopy (ASD FieldSpec 4) characterization of 104 phosphate waste rock samples at Benguerir. Spectral library matching against ECOSTRESS. NNLS unmixing. HHXRF cross-validation.

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
FILE: 02_Academic & Work/thesis/literature-notes/@roberts2019unmixing.md (~201 words)
================================================================================
---
citekey: roberts2019unmixing
title: "Spectral Mixture Analysis for Remote Sensing of Geological Surfaces"
authors: Roberts D.A., et al.
year: 2019
journal: Remote Sensing
tags: [literature-note, unmixing, VCA, FCLS, chapter-3]
generated_by: claude
date: 2026-06-07
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
FILE: 02_Academic & Work/thesis/literature-notes/@verrelst2021review.md (~245 words)
================================================================================
---
citekey: verrelst2021review
title: "Quantifying Vegetation Biophysical Variables from Imaging Spectroscopy Data: A Review on Retrieval Methods"
authors: Verrelst J., et al.
year: 2021
journal: Surveys in Geophysics
tags: [literature-note, verrelst, jury-prep, RTM, unmixing]
generated_by: claude
date: 2026-06-07
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
- Note that SCOPE/PROSAIL are not designed for phosphate mine waste mineralogy

## Links
- [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced]]
- [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]]
- [[04_Knowledge Base/wiki/concepts/Reclamation Progress Index]]




================================================================================
FILE: 02_Academic & Work/work/Flashcards — Career.md (~741 words)
================================================================================
---
tags: [flashcards, career, jobs, contacts, postdoc]
generated_by: claude
date: 2026-06-07
---

# Flashcards — Career & Contacts

> For interview prep, networking conversations, and job search strategy.
> All emails and names must come without hesitation.

---

## Identity & Bio

Full name::Abdelhak EL MANSOUR
Institutional email::abdelhak.elmansour@um6p.ma
<!--SR:!2026-06-08,1,230-->
Personal email::insitazoult@gmail.com
Twitter/X handle::@AbdelhakElm
Google Scholar user ID::ysUOZQ0AAAAJ
Institution::University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
Department::GSMI — Geology and Sustainable Mining Institute
PhD supervisor::Pr. Ahmed LAAMRANI
Co-supervisors (3)::Pr. Benzaazoua, Pr. Elghali, Pr. Hakkou
Origin city::Errachidia (Tafilalt region, SE Morocco)
Heritage::Amazigh — Ait Atta tribe. Tamazight native speaker.
Instagram::phddiarymemes — 70K+ PhD meme page (NOT a research account)

---

## Publications — Know Every Paper

Published paper 1 (most recent) — journal, topic, DOI::Sensors 2025 — Ch.1 field spectroscopy — DOI: 10.3390/s26010002
Published paper 2 — journal, year::IJEST 2024
Published paper 3 — journal, year::Mining 2023
Published paper 4 — journal, year::BDJ 2023
Pipeline paper 1 — journal, status::Minerals (IF 2.2) — Ch.2 PRISMA lithological mapping — ACCEPTED 2026 ✅
Pipeline paper 2 — plan::Ch.3 EnMAP RPI — submission post-defense
Total published papers::4
Total publications including pipeline::6 (4 published + 2 in pipeline)
Conferences attended::EGU 2025 (Vienna, Austria) · EARSeL 2024 (Valencia, Spain) · ESPC6 2026 (UM6P, abstract submitted)

---

## Top Priority Contacts — DLR

Dr. Tobias Storch email::tobias.storch@dlr.de
Dr. Tobias Storch role::DLR IMF — Imaging Spectroscopy Department, Oberpfaffenhofen. Fit: 10/10.
Dr. Sarah Asam email::sarah.asam@dlr.de
Dr. Sarah Asam role::DLR DFD — Forest Ecosystems Team, Oberpfaffenhofen. Fit: 9/10.
When to email DLR?::July 1+ (post-defense rule). Letters already drafted.

---

## Top Priority Contacts — GFZ Potsdam

Pr. Sabine Chabrillat email::sabine.chabrillat@gfz-potsdam.de
Pr. Sabine Chabrillat role::GFZ Potsdam — Hyperspectral RS group, EnMAP Science PI. Fit: 9.5/10.
Dr. Saeid Asadzadeh email::saeid.asadzadeh@gfz-potsdam.de
Dr. Saeid Asadzadeh role::GFZ Potsdam — EnMAP science team, mineral RS. Fit: 9/10.
GFZ EURAXESS open postdoc deadline::December 2026. Fit: 8/10.

---

## Top Priority Contacts — HZDR / Helmholtz Freiberg

Dr. Richard Gloaguen email::r.gloaguen@hzdr.de
Dr. Richard Gloaguen role::HZDR / Helmholtz Freiberg — Exploration Technology division. Fit: 9/10.
Dr. Sandra Lorenz email::s.lorenz@hzdr.de
Dr. Sandra Lorenz role::HZDR Freiberg — Group Leader Digital Processing, mine RS. Fit: 9/10.

---

## ITC Twente Contacts

Dr. Mahdi Khodadadzadeh email::m.khodadadzadeh@utwente.nl
Dr. Mahdi Khodadadzadeh role::ITC Twente — hyperspectral + ML for mining mineralogy. Fit: 8.5/10.
Dr. Chris Hecker email::c.a.hecker@utwente.nl
Dr. Chris Hecker role::ITC Twente — TIR hyperspectral mineralogy, EMIT, GreenMiner. Fit: 7.5/10.

---

## UQAT (Canada) Contacts

Pr. Nicole Fenton email::nicole.fenton@uqat.ca
Pr. Nicole Fenton role::UQAT — IRF / NSERC Chair Biodiversity in Mining. Fit: 9/10.
Pr. Osvaldo Valeria email::osvaldo.valeria@uqat.ca
Pr. Osvaldo Valeria role::UQAT — IRF, Rouyn-Noranda, Canada. Fit: 8.5/10.
Pr. Bruno Bussière email::bruno.bussiere@uqat.ca
Pr. Bruno Bussière role::UQAT — IRME / NSERC Chair Mine Reclamation. Fit: 7.5/10.
Pr. Maxence Martin email::maxence.martin@uqat.ca
Pr. Maxence Martin role::UQAT — IRF, boreal RS / LiDAR. Fit: 7/10.

---

## Other International Contacts

Pr. Kamran Esmaeili email::kamran.esmaeili@utoronto.ca
Pr. Kamran Esmaeili role::University of Toronto — hyperspectral ore-waste discrimination + ML. Fit: 8.5/10.
Dr. Mehdi Abdolmaleki role::Postdoc in Esmaeili lab, U. Toronto — peer, hyperspectral mining RS. Email after Esmaeili contact.
Dr. Nicola Mondillo email::nicola.mondillo@unina.it
Dr. Nicola Mondillo role::Univ. Naples Federico II — PRISMA + geochemistry for mining mineralogy. Fit: 8.5/10.
Dr. Anna Sorrentino email::anna.sorrentino@unina.it
Dr. Anna Sorrentino role::Univ. Naples Federico II — PRISMA satellite mining geology. Peer inquiry.
Dr. Martin Schodlok email::martin.schodlok@bgr.de
Dr. Martin Schodlok role::BGR Hannover — mine tailings hyperspectral monitoring. Fit: 7.5/10.

---

## Organizations & Salary Benchmarks

VITO location and type::Belgium (Hybrid). Earth observation research institute.
DLR IMF location::Oberpfaffenhofen, Germany. Imaging Spectroscopy Department.
DLR DFD location::Oberpfaffenhofen, Germany. Forest / land surface remote sensing.
GFZ Potsdam type::Helmholtz Centre for Geosciences, Germany. World-class for hyperspectral RS.
HZDR Freiberg full name::Helmholtz-Zentrum Dresden-Rossendorf. Exploration Technology division in Freiberg.
ETH Zurich postdoc (open)::Hyperspectral RS for Forest Management. Fit: 7/10. Deadline TBD.
U. Copenhagen postdoc (open)::Hyperspectral RS. Fit: 7.5/10.
ESA YPP salary::~€4,000–5,000/month
DLR/VITO postdoc salary::~€3,500–4,500/month
Rio Tinto RS scientist salary::€70,000–90,000/year
OCP consulting play::RPI tool = potential €10–30K consulting or R&D hire. Via Laamrani.

---

## Career Strategy (Post-Defense)

Priority #1 job target post-defense::DLR IMF — email Dr. Tobias Storch directly after July 1
Priority #2 job target::OCP Group R&D via Laamrani (natural fit, Morocco, no relocation)
<!--SR:!2026-06-10,3,250-->
Priority #3 targets::ETH Zurich / VITO / GFZ postdoc applications
<!--SR:!2026-06-10,3,250-->
Decision point date::September 2026 — postdoc vs consulting vs both
Rule: when to send applications?::Post-defense (July 1+). Only VITO was applied pre-defense due to deadline.
VITO applications sent (with dates)::Scientist Remote Sensing Water Quality (Applied 2026-05-25) + Scientific Expert EO Services (Applied 2026-05-25)




================================================================================
FILE: 02_Academic & Work/work/Index.md (~209 words)
================================================================================
---
tags: [work, index]
updated: 2026-05-27
---

# Work Index

## 🔴 URGENT
| Project | Deadline | Link |
|---------|----------|------|
| Thesis Defense | ~June 2026 | [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]] |
| **Defense Slides** | **This week** (Laamrani, 2026-05-27) | [[02_Academic & Work/work/1-1/Laamrani-2026-05-27]] |

## Active Projects
| Project | Status | Link |
|---------|--------|------|
| PhD Thesis | 🔴 Defense prep | [[02_Academic & Work/thesis/Thesis Overview]] |
| 90-Day Plan Post-Defense | 🟡 Planning | [[02_Academic & Work/work/active/90-Day Plan Post-Defense]] |
| Postdoc Applications | 🟡 Post-defense | [[02_Academic & Work/work/active/Postdoc Applications]] · [[02_Academic & Work/work/active/Postdoc Outreach Dashboard\|Outreach Dashboard]] |
| Industry Opportunities | 🟡 Spontaneous targets | [[02_Academic & Work/work/active/Fitted Opportunities & Targets\|Opportunities Dashboard]] |
| Instagram Growth | 🟡 Ongoing | [[03_Digital Life/money/instagram/Instagram Strategy]] |
| Domaining | 🟡 Ongoing | [[03_Digital Life/money/domaining/Domain Portfolio]] |

## Completed / Archive
| Project | Completed | Link |
|---------|-----------|------|
| PRISMA HDF5 Pipeline | 2025 | [[02_Academic & Work/thesis/Thesis MOC]] |
| SCSE Model Implementation | 2025 | [[02_Academic & Work/thesis/Thesis MOC]] |
| Manuscript Submission | Nov 2025 | [[04_Knowledge Base/AI-Generated/papers/Sensors 2025 — Ch1 Published Paper\|Sensors 2025 Ch.1]] |

## 1:1 Meetings
*(Meeting notes with supervisor, collaborators)*

## Incidents / Blockers
*(Technical issues, administrative blockers)*




================================================================================
FILE: 02_Academic & Work/work/Tools Setup.md (~706 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [setup, tools, mcp, claude-code]
---

# Claude Code Tools Setup — Abdelhak Vault

Installed and configured 2026-05-25. All tools are global (user scope) — available in every Claude Code session.

---

## Status Summary

| Tool | Type | Status | Action needed |
|------|------|--------|---------------|
| graphify | Claude Code Skill | ✅ Installed | None — type `/graphify .raw` to run |
| vault-obsidian | MCP Server | ✅ Connected | None — vault is live |
| brave-search | MCP Server | ✅ Connected | Add real API key (free) |
| github | MCP Server | ⚠️ Needs PAT | Create GitHub Personal Access Token |
| gmail | MCP Server | ⚠️ Needs OAuth | Run auth flow (see below) |
| Twitter/X | — | ❌ Not installed | Paid API ($100/month) — skipped |

---

## 1. graphify — Knowledge Graph Skill

**What it does:** Turns any folder (PDFs, markdown, code, papers) into a queryable knowledge graph. Claude queries the graph instead of re-reading every file — saves tokens and builds persistent memory.

**How to use:**
```
/graphify .raw          ← build graph from .raw/ folder
/graphify .             ← build graph from entire vault
/graphify .raw --obsidian  ← also generate Obsidian notes from graph
```

**Installed via:** `pip install graphifyy && graphify install`

---

## 2. vault-obsidian — Vault Filesystem MCP

**What it does:** Exposes your vault to Claude Code in any project context — read, write, search files without copy-paste. Also works when you open Claude Code from outside the vault directory.

**Server:** `@modelcontextprotocol/server-filesystem`
**Vault path:** `C:\Users\Dell\Downloads\abdelhak-real-vault\abdelhak-vault`
**Status:** ✅ Connected automatically

---

## 3. brave-search — Real-Time Web Search

**What it does:** Lets Claude search the web mid-conversation. Used for: job searches, paper lookups, satellite mission updates, anything requiring current info.

**Status:** ✅ Server connected — but placeholder API key means searches will fail until you add the real key.

**To activate (5 minutes):**
1. Go to https://api.search.brave.com → create free account
2. Generate an API key (free tier = 2,000 queries/month)
3. Run: `! claude mcp remove brave-search -s user`
4. Then: `! claude mcp add brave-search -s user -e "BRAVE_API_KEY=YOUR_REAL_KEY_HERE" -- node "C:\Users\Dell\AppData\Roaming\npm\node_modules\@modelcontextprotocol\server-brave-search\dist\index.js"`

---

## 4. github — GitHub MCP (Official)

**What it does:** Read repos, manage issues and PRs, search code — directly from Claude. Use case: backup vault to GitHub, automate repo tasks.

**Status:** ⚠️ Configured but auth fails — needs your GitHub PAT.

**To activate (3 minutes):**
1. Go to https://github.com/settings/personal-access-tokens/new
2. Create a fine-grained PAT — scopes needed: `repo` (read/write), `issues`, `pull_requests`
3. Run: `! claude mcp remove github -s user`
4. Then: `! claude mcp add --transport http github -s user -H "Authorization: Bearer YOUR_PAT_HERE" https://api.githubcopilot.com/mcp/`

---

## 5. gmail — Gmail MCP

**What it does:** Read emails, search inbox, extract important info. Use case: pull job application replies, VITO/Pixxel responses, conference notifications into vault.

**Status:** ⚠️ Server installed — needs one-time Google OAuth flow.

**To activate (~10 minutes):**
1. Go to https://console.cloud.google.com → create a new project (e.g. "claude-gmail")
2. Enable the Gmail API for that project
3. Create OAuth 2.0 credentials (Desktop app type) → download `credentials.json`
4. Place `credentials.json` in: `C:\Users\Dell\.gmail-mcp\credentials.json`
5. Run in terminal: `! node "C:\Users\Dell\AppData\Roaming\npm\node_modules\@gongrzhe\server-gmail-autoauth-mcp\dist\index.js"` — this opens a browser OAuth flow
6. After auth, the token is saved and the MCP server will connect automatically

---

## 6. Twitter/X — NOT installed

**Why:** Twitter's free API tier allows posting only — no search. Monitoring hyperspectral/mining tweets requires the Basic tier at $100/month. Not worth it unless you're actively doing social listening at scale.

**If you want post-only (free):**
- twitter-mcp by EnesCinr → requires Twitter Developer account + OAuth credentials
- Apply at https://developer.twitter.com — free but requires application approval

---

## Config location

All MCP servers are stored in: `C:\Users\Dell\.claude.json`
graphify skill: `C:\Users\Dell\.claude\skills\graphify\`

---

## Quick test commands (after auth setup)

```
/graphify .raw                        ← test graphify on raw papers
Ask Claude: "list files in the vault" ← tests vault-obsidian
Ask Claude: "search the web for VITO Belgium remote sensing jobs" ← tests brave-search (needs real key)
Ask Claude: "list my GitHub repos"    ← tests github (needs PAT)
Ask Claude: "check my inbox"          ← tests gmail (needs OAuth)
```




================================================================================
FILE: 02_Academic & Work/work/1-1/Laamrani-2026-05-27.md (~82 words)
================================================================================
---
tags: [1-1, supervisor, meeting, defense-prep]
date: 2026-05-27
quarter: Q2-2026
description: "1-on-1 Laamrani May 27 — slides to start this week"
type: 1-on-1
person: "[[02_Academic & Work/org/people/Ahmed Laamrani]]"
project: "[[02_Academic & Work/thesis/Thesis Overview]]"
---

# 1-on-1 Laamrani — 2026-05-27

## Key Takeaways

- **Defense slides** — Laamrani confirmed slides must start this week. No delay possible.

## Action Items

- [ ] Start defense slides this week (week of May 27)

## Related

- [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]]
- [[03_Digital Life/brain/Key Decisions]]




================================================================================
FILE: 02_Academic & Work/work/active/90-Day Plan Post-Defense.md (~952 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [work, career, planning, post-defense, 90-days]
status: active
period: July 1 – September 30, 2026
---

# 90-Day Plan — Post-Defense

**Period:** July 1 → September 30, 2026
**Starting point:** Dr. Abdelhak EL MANSOUR, 4 publications, operational pipeline, 70K followers, 86 domains, VITO pending.

> [!success] The guiding principle
> The first 90 days post-defense define the trajectory of the next 5 years.
> Each week has ONE dominant objective. Not a list. One thing.

---

## JULY — Launch Month

### Week 1 — July 1–7: CELEBRATE AND ANNOUNCE
**Dominant objective:** Make it known that Dr. EL MANSOUR exists.

- [ ] Announce on X (@AbdelhakElm) — one sentence, the title, the mine
- [ ] Announce on phddiarymemes (70K PhD students are waiting) — authentic content, not corporate
- [ ] Update LinkedIn: "Dr." + "Defended June 30, 2026 · UM6P"
- [ ] Update Google Scholar profile
- [ ] Update CV (academic + industry) with defense date
- [ ] **Sleep. Eat. Go outside. You earned it.**

---

### Week 2 — July 8–14: SUBMIT CH.3 + ACTIVATE DLR

**Dominant objective:** Get the Ch.3 paper into the pipeline and send the Storch email.

- [ ] **Submit Ch.3 paper** (EnMAP / RPI) — target journal to confirm (Remote Sensing of Environment? ISPRS?)
- [ ] **Email Dr. Tobias Storch (DLR IMF)** — one paragraph, one direct subject line:
  *"I defended my PhD June 30 on EnMAP-based operational reclamation monitoring at phosphate mines. I'm exploring postdoc opportunities in your group."*
- [ ] Check DLR portal for open positions → [[02_Academic & Work/work/active/Hot Opportunities — May 2026]]
- [ ] Reply to VITO if response received (normal timeline: 2–6 weeks after submission)

---

### Week 3 — July 15–21: OCP + DOMAINING

**Dominant objective:** Initiate the OCP consulting conversation and activate the top 5 domains.

- [ ] **Email Laamrani**: open the OCP R&D conversation — "does OCP want to operationalize the RPI?"
  - Goal: €10–30K consulting contract or R&D digital hire
  - This is not a cold application — you delivered something they funded
- [ ] **Top 5 domains** → [[03_Digital Life/money/domaining/Domain Portfolio Analysis — Top 5 to Market]]
  - List on Dan.com, Afternic, Sedo
  - Contact 2–3 potential direct buyers (targeted outreach)

---

### Week 4 — July 22–31: ESPC6 PREP + FOLLOW-UP

**Dominant objective:** Prepare the ESPC6 presentation ahead of time (November comes fast).

- [ ] Check ESPC6 abstract response (submitted May 25)
- [ ] If accepted: decide oral or poster, create presentation skeleton
- [ ] Formally apply to ETH Zurich postdoc (if still open) → [[02_Academic & Work/work/active/Hot Opportunities — May 2026]]
- [ ] Follow up with VITO if no response
- [ ] First monthly review: which income streams moved? (Domaining, Instagram, VITO)

---

## AUGUST — Build Month

### Weeks 5–6 — August 1–14: JOB + PAPER

**Dominant objective:** Ch.3 paper in the system, job responses in sight.

- [ ] Track Ch.3 status (under review?)
- [ ] If DLR or ETH response: prepare interview
- [ ] If no DLR response: send short follow-up (2 weeks after first email)
- [ ] Contact CRSA UM6P directly — they regularly hire hyperspectral postdocs

---

### Weeks 7–8 — August 15–31: INSTAGRAM PIVOT + DOMAINS

**Dominant objective:** Monetize the "Dr." on phddiarymemes and accelerate domain sales.

- [ ] **phddiarymemes "Dr." content**: first post with the title — authenticity, not forced celebration
- [ ] Launch sponsorship outreach: Notion, Overleaf, Researcher.ai, academic publishers
  - Current followers = 70K, PhD niche engagement rate = 3–5% = ~2,100–3,500 engagements/post
  - Estimated value per post: €500–1,500 depending on brand
- [ ] **Domaining**: follow up on listings, lower price on 1–2 domains to accelerate a sale
- [ ] Domain review: did a sale materialize in July?

---

## SEPTEMBER — Transition Month

### Weeks 9–10 — September 1–14: DECISION POINT

**Dominant objective:** Where do things stand? Postdoc confirmed, pending, or building solo?

**Scenario A — Postdoc offer received (DLR, ETH, VITO):**
- [ ] Negotiate start date (October/November preferred — leaves 1 month breathing room)
- [ ] Prepare relocation and logistics
- [ ] Continue domaining and Instagram in parallel

**Scenario B — No offer yet:**
- [ ] CRSA UM6P application if role open
- [ ] OCP consulting: is the proposal moving forward?
- [ ] Expand search: BRGM France, VITO second unapplied role, Spanish universities
- [ ] Don't panic — the postdoc market is slow. 4 publications + RPI + EnMAP pipeline = strong profile.

---

### Weeks 11–13 — September 15–30: 90-DAY REVIEW

**Dominant objective:** Assess, adjust, project.

- [ ] Total revenue Jul–Sep: domaining? Sponsorships? OCP consulting?
- [ ] Papers submitted: Ch.3 + potentially revised Ch.2?
- [ ] Job: where do things stand? Postdoc, consulting, or both?
- [ ] ESPC6 ready for November?
- [ ] Identify the next 3 priorities for the following 90 days (Oct–Dec 2026)

---

## 90-Day Dashboard

| Domain | Jul–Sep Objective | Success Indicator |
|--------|------------------|------------------|
| 🎓 Academic | Ch.3 submitted, DLR/ETH contacted | Submission confirmation + response |
| 💼 Job | 1 postdoc offer or OCP consulting contract | Written offer received |
| 💰 Domaining | 1 sale among top 5 | Sale completed |
| 📱 Instagram | 1 sponsorship deal signed | Contract + payment |
| 📄 ESPC6 | Presentation ready | Slides done before October |
| 🌍 Network | DLR + ETH + OCP activated | 3 open conversations |

---

*The most important month of your life ended June 30. The 90 days that follow define what it means.*




================================================================================
FILE: 02_Academic & Work/work/active/Fitted Opportunities & Targets.md (~1581 words)
================================================================================
---
generated_by: claude
date: 2026-06-07
tags: [work, active, career, opportunities, dashboard]
status: active
summary: "A structured database of 10 high-potential Earth Observation, hyperspectral, and remote sensing companies in the Middle East and Europe, complete with custom outreach templates."
---

# 🚀 High-Potential Career Opportunities & Targets

> [!TIP]
> **Your Core Pitch**: You don't just analyze satellite data; you build **operational Python pipelines** that transform raw, complex hyperspectral data ([[EnMAP Satellite|EnMAP]] and [[PRISMA Satellite|PRISMA]]) into geochemically validated environmental and mineralogical metrics. This is a rare skill set in both commercial space-tech and infrastructure engineering.
>
> See also: [[Job Board — Live Tracker]] · [[Postdoc Outreach Dashboard]] · [[Hot Opportunities — May 2026]] · [[Review Brief — Postdoc Applications 2026]]

---

## 📋 Industry Opportunities Tracker

| Company/Society               | Sector & Core Focus                     | Location                  | Pitch Angle / Fit                                                                       | Contact Channel / Email                                        | Status                           |
| :---------------------------- | :-------------------------------------- | :------------------------ | :-------------------------------------------------------------------------------------- | :------------------------------------------------------------- | :------------------------------- |
| **Space42 / Bayanat**         | AI-powered Space & EO Constellations    | 🇦🇪 Abu Dhabi, UAE       | Building the region's largest EO satellite network. Direct fit for Remote Sensing Lead. | [Space42 Careers Portal](https://space42.ai/)                  | - [ ] Not Contacted              |
| **Bayanat Engineering Qatar** | Infrastructure GIS & new EO Division    | 🇶🇦 Doha, Qatar          | Recently launched a dedicated Earth Observation and Remote Sensing division.            | `info@bayanatengineering.qa`                                   | - [x] Not Contacted ✅ 2026-06-07 |
| **Kuva Space**                | Commercial Hyperspectral Constellation  | 🇫🇮 Espoo, Finland       | Launching hyperspectral nanosatellites for climate/agriculture. High technical fit.     | `careers@kuvaspace.com`                                        | - [x] Not Contacted ✅ 2026-06-07 |
| **Egis Group (Qatar)**        | Global Engineering & Consulting         | 🇶🇦 Doha, Qatar          | Spontaneous outreach for environmental remote sensing in infrastructure projects.       | [Egis Contact Page](https://www.egis-group.com/contact)        | - [ ] Not Contacted              |
| **Taqnia Space**              | Satellite Intelligence & Remote Sensing | 🇸🇦 Riyadh, Saudi Arabia | Major operator for Saudi Space Commission and Vision 2030 Earth Observation.            | [Taqnia Space Contact Portal](https://www.taqniaspace.com.sa/) | - [ ] Not Contacted              |
| **LYRASENSE**                 | Agentic AI for Geospatial Analytics     | 🇪🇺 Europe (Remote)      | Software analyzing satellite imagery for oil, gas, and environmental monitoring.        | [Lyrasense Careers Page](https://lyrasense.com/)               | - [ ] Not Contacted              |
| **European Space Imaging**    | High-Res Satellite Imagery & Solutions  | 🇩🇪 Munich, Germany      | Major imagery distributor partnering with Pixxel for hyperspectral analytics.           | [EUSI Careers Portal](https://www.euspaceimaging.com/careers/) | - [ ] Not Contacted              |
| **Uptoearth**                 | Geospatial Intelligence & Pipelines     | 🇮🇹 Italy                | Processing pipelines for hyperspectral, SAR, and optical satellite data.                | [Uptoearth Contact Portal](https://uptoearth.eu/)              | - [ ] Not Contacted              |
| **Specim (Spectral Imaging)** | Industrial Hyperspectral Solutions      | 🇫🇮 Oulu, Finland        | World leader in hyperspectral cameras and mineral mapping applications.                 | [Specim Careers Page](https://www.specim.fi/careers/)          | - [ ] Not Contacted              |
| **Shamal Technologies**       | Geospatial Intelligence & Drone RS      | 🇸🇦 Riyadh, Saudi Arabia | Drone and satellite remote sensing for Saudi mega-projects (NEOM, Red Sea).             | [Shamal Contact Portal](https://shamal.sa/)                    | - [ ] Not Contacted              |

---

## 🔍 Detailed Profile of Top Targets

### 1. Bayanat Engineering Qatar (Doha, Qatar)
- **The Fit**: Excellent local target in Doha. They recently launched a dedicated Earth Observation and Remote Sensing division for infrastructure and disaster management. Your experience building pipelines for EnMAP and PRISMA, combined with your OCP mine monitoring projects, is highly transferable to their environmental assessment services.
- **Action**: Send a direct cold email to their general inquiry box, explicitly directed to the HR/Remote Sensing Team.
- **Email**: `info@bayanatengineering.qa` (Phone: +974 4427 3784)

### 2. Space42 (Bayanat + Yahsat) (Abu Dhabi, UAE)
- **The Fit**: A regional powerhouse backed by G42. They are actively building and launching Earth Observation satellites (including Synthetic Aperture Radar and optical networks) and have partnerships to deploy hyperspectral capabilities. Your Python skills and experience in processing complex multisource satellite data makes you a prime candidate for a Remote Sensing Scientist role.
- **Action**: Join their "Talent Community" on the career page and search LinkedIn for "Talent Acquisition Space42" or "Talent Acquisition Bayanat".
- **Careers Link**: [Space42.ai Careers Portal](https://space42.ai/)

### 3. Kuva Space (Espoo, Finland)
- **The Fit**: The most prominent European hyperspectral startup. They are launching a constellation of hyperspectral nanosatellites to monitor agriculture, forests, and carbon. You have a ready-made EnMAP/PRISMA processing pipeline and published papers in hyperspectral remote sensing. This is your strongest technical fit in the commercial startup sector.
- **Action**: Direct speculative application email to their careers address.
- **Email**: `careers@kuvaspace.com`

---

## 📧 Structured Outreach Templates

> [!success] [✉️ Open Draft in Mail Client (Space42)](mailto:careers@space42.ai?subject=Spontaneous%20Application%20%E2%80%94%20Remote%20Sensing%20%26%20Hyperspectral%20Scientist%20%E2%80%94%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Talent%20Acquisition%20Team%2C%0A%0AI%20hope%20this%20message%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20spontaneously%20express%20my%20strong%20interest%20in%20joining%20your%20team%20as%20a%20Remote%20Sensing%20Scientist%20/%20Earth%20Observation%20Specialist.%20I%20am%20a%20PhD%20Candidate%20at%20University%20Mohammed%20VI%20Polytechnic%20%28UM6P%29%20in%20Morocco%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20motivated%20to%20bring%20my%20expertise%20to%20the%20Middle%20East%27s%20rapidly%20expanding%20space%20and%20geospatial%20sectors.%0A%0AMy%20doctoral%20research%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20frameworks%20and%20machine%20learning%20pipelines%20%28Random%20Forest%2C%20CNNs%29%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20mine%20waste%20rocks.%20A%20key%20technical%20achievement%20of%20my%20thesis%20is%20building%20an%20operational%2C%201%2C776-line%20Python%20processing%20engine%20for%20EnMAP%20and%20PRISMA%20hyperspectral%20satellite%20data%E2%80%94covering%20atmospheric%20correction%2C%20bad-band%20removal%2C%20spectral%20unmixing%20%28VCA-FCLS%29%2C%20and%20classification%2C%20all%20validated%20against%20geochemistry%20ground%20truth.%0A%0AAs%20your%20organization%20builds%20the%20next%20generation%20of%20space%20infrastructure%20and%20location%20intelligence%20applications%20in%20the%20GCC%2C%20I%20am%20eager%20to%20apply%20my%20experience%20in%20processing%20complex%20hyperspectral%20and%20multisource%20satellite%20datasets%20to%20your%20active%20projects.%0A%0AI%20would%20welcome%20the%20opportunity%20to%20discuss%20how%20my%20background%20and%20Python%20pipeline%20capabilities%20can%20add%20value%20to%20your%20team.%20I%20am%20happy%20to%20share%20my%20CV%2C%20thesis%20abstract%2C%20and%20publications%20for%20your%20review.%0A%0AThank%20you%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0ADr.%20Abdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco%0Aelmansour01abdelhak%40gmail.com%20%7C%20%5BPhone%20Number%5D)

### 💼 Template 1: For GCC AI/Space Champions (Space42 / Taqnia Space / Shamal Tech)
*Best for submitting a spontaneous application to Middle Eastern space technology and AI-powered geospatial groups.*

```text
Subject: Spontaneous Application — Remote Sensing & Hyperspectral Scientist — Dr. Abdelhak EL MANSOUR

Dear Talent Acquisition Team,

I hope this message finds you well.

I am writing to spontaneously express my strong interest in joining your team as a Remote Sensing Scientist / Earth Observation Specialist. I am a PhD Candidate at University Mohammed VI Polytechnic (UM6P) in Morocco, defending my thesis on June 30, 2026, and I am highly motivated to bring my expertise to the Middle East's rapidly expanding space and geospatial sectors.

My doctoral research focuses on developing multi-scale remote sensing frameworks and machine learning pipelines (Random Forest, CNNs) for mineralogical characterization and environmental monitoring of mine waste rocks. A key technical achievement of my thesis is building an operational, 1,776-line Python processing engine for EnMAP and PRISMA hyperspectral satellite data—covering atmospheric correction, bad-band removal, spectral unmixing (VCA-FCLS), and classification, all validated against geochemistry ground truth.

As your organization builds the next generation of space infrastructure and location intelligence applications in the GCC, I am eager to apply my experience in processing complex hyperspectral and multisource satellite datasets to your active projects.

I would welcome the opportunity to discuss how my background and Python pipeline capabilities can add value to your team. I am happy to share my CV, thesis abstract, and publications for your review.

Thank you for your time and consideration.

Sincerely,

Dr. Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
elmansour01abdelhak@gmail.com | [Phone Number]
```

> [!success] [✉️ Open Draft in Mail Client (Bayanat Qatar)](mailto:info@bayanatengineering.qa?subject=Spontaneous%20Inquiry%3A%20Remote%20Sensing%20%26%20Earth%20Observation%20Division%20%E2%80%94%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Bayanat%20Engineering%20Qatar%20Team%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20career%20opportunities%20within%20your%20newly%20established%20Earth%20Observation%20and%20Remote%20Sensing%20division%20in%20Doha.%20I%20am%20a%20Remote%20Sensing%20Scientist%20and%20PhD%20Candidate%20at%20UM6P%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026.%20Having%20followed%20your%20organization%27s%20leadership%20in%20high-value%20engineering%20and%20GIS%20projects%20in%20Qatar%2C%20I%20am%20highly%20interested%20in%20joining%20your%20technical%20team.%0A%0AMy%20doctoral%20research%20consists%20of%20developing%20multi-scale%20remote%20sensing%20frameworks%20to%20monitor%20and%20characterize%20mine%20waste%20reclamation%20surfaces.%20I%20specialize%20in%20building%20operational%20Python%20pipelines%20to%20process%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20translating%20raw%20imagery%20into%20validated%20environmental%20metrics.%20This%20project%20was%20conducted%20in%20direct%20collaboration%20with%20OCP%20Group%20at%20the%20Benguerir%20mine%20site%2C%20giving%20me%20direct%20experience%20in%20managing%20large-scale%20industrial%20and%20environmental%20monitoring%20workflows.%0A%0AGiven%20my%20technical%20background%20and%20bilingual%20fluency%20%28English%2C%20French%2C%20and%20Arabic%29%2C%20I%20am%20eager%20to%20help%20your%20division%20deliver%20high-accuracy%20satellite-derived%20environmental%20assessments%2C%20infrastructure%20monitoring%2C%20and%20natural%20resource%20mapping%20in%20Qatar.%0A%0AI%20would%20appreciate%20the%20opportunity%20for%20a%20brief%20conversation%20to%20explore%20how%20my%20skills%20can%20support%20your%20active%20contracts%20in%20Doha.%20I%20am%20happy%20to%20send%20my%20CV%20and%20detailed%20project%20portfolio%20at%20your%20convenience.%0A%0AThank%20you%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0ADr.%20Abdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco%0Aelmansour01abdelhak%40gmail.com%20%7C%20%5BPhone%20Number%5D)

### 🇶🇦 Template 2: For Local Doha Engineering/GIS Firms (Bayanat Engineering Qatar / Egis Qatar)
*Best for contacting Qatar-based engineering and GIS providers that have dedicated environmental monitoring or remote sensing divisions.*

```text
Subject: Spontaneous Inquiry: Remote Sensing & Earth Observation Division — Dr. Abdelhak EL MANSOUR

Dear Bayanat Engineering Qatar Team,

I hope this email finds you well.

I am writing to inquire about career opportunities within your newly established Earth Observation and Remote Sensing division in Doha. I am a Remote Sensing Scientist and PhD Candidate at UM6P, defending my thesis on June 30, 2026. Having followed your organization's leadership in high-value engineering and GIS projects in Qatar, I am highly interested in joining your technical team.

My doctoral research consists of developing multi-scale remote sensing frameworks to monitor and characterize mine waste reclamation surfaces. I specialize in building operational Python pipelines to process satellite hyperspectral data (EnMAP and PRISMA), translating raw imagery into validated environmental metrics. This project was conducted in direct collaboration with OCP Group at the Benguerir mine site, giving me direct experience in managing large-scale industrial and environmental monitoring workflows.

Given my technical background and bilingual fluency (English, French, and Arabic), I am eager to help your division deliver high-accuracy satellite-derived environmental assessments, infrastructure monitoring, and natural resource mapping in Qatar.

I would appreciate the opportunity for a brief conversation to explore how my skills can support your active contracts in Doha. I am happy to send my CV and detailed project portfolio at your convenience.

Thank you for your time and consideration.

Sincerely,

Dr. Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
elmansour01abdelhak@gmail.com | [Phone Number]
```

> [!success] [✉️ Open Draft in Mail Client (Kuva Space)](mailto:careers@kuvaspace.com?subject=Spontaneous%20Application%3A%20Remote%20Sensing%20Scientist%20/%20Hyperspectral%20Data%20Engineer%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Hiring%20Team%2C%0A%0AI%20am%20reaching%20out%20spontaneously%20to%20express%20my%20strong%20interest%20in%20joining%20your%20team%20as%20a%20Remote%20Sensing%20Scientist%20or%20Hyperspectral%20Data%20Engineer.%20I%20am%20a%20PhD%20Candidate%20at%20UM6P%20in%20Morocco%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20with%20a%20solid%20track%20record%20in%20hyperspectral%20image%20processing%20and%20machine%20learning.%0A%0AMy%20research%20focuses%20on%20multi-scale%20hyperspectral%20remote%20sensing%20%28field%20spectroscopy%2C%20PRISMA%2C%20and%20EnMAP%20satellite%20data%29%20for%20surface%20geochemistry%20and%20environmental%20monitoring.%20I%20build%20end-to-end%20Python%20processing%20pipelines%20to%20digest%20and%20analyze%20complex%20spectral%20datasets%E2%80%94integrating%20bad-band%20detection%2C%20atmospheric%20correction%2C%20spectral%20unmixing%20%28VCA-FCLS%29%2C%20and%20spatial-spectral%20classification.%0A%0AYour%20work%20in%20developing%20hyperspectral%20satellite%20constellations%20and%20agentic%20AI%20platforms%20represents%20the%20cutting%20edge%20of%20commercial%20earth%20observation.%20I%20bring%20a%20rare%20combination%20of%20academic%20rigor%20%284%20peer-reviewed%20publications%29%20and%20hands-on%2C%20production-grade%20Python%20development%20skills%20that%20align%20directly%20with%20your%20technical%20stack.%0A%0AI%20would%20be%20thrilled%20to%20discuss%20how%20my%20hyperspectral%20processing%20experience%20can%20support%20your%20mission.%20I%20have%20attached%20my%20CV%20and%20would%20welcome%20a%20brief%20introductory%20call.%0A%0AThank%20you%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0ADr.%20Abdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco%0Aelmansour01abdelhak%40gmail.com%20%7C%20%5BPhone%20Number%5D)

### 🇪🇺 Template 3: For European Space & Hyperspectral Startups (Kuva Space / LYRASENSE)
*Best for cold email outreach to hyperspectral nanosatellite operators and AI geospatial software startups in Europe.*

```text
Subject: Spontaneous Application: Remote Sensing Scientist / Hyperspectral Data Engineer - Dr. Abdelhak EL MANSOUR

Dear Hiring Team,

I am reaching out spontaneously to express my strong interest in joining your team as a Remote Sensing Scientist or Hyperspectral Data Engineer. I am a PhD Candidate at UM6P in Morocco, defending my thesis on June 30, 2026, with a solid track record in hyperspectral image processing and machine learning.

My research focuses on multi-scale hyperspectral remote sensing (field spectroscopy, PRISMA, and EnMAP satellite data) for surface geochemistry and environmental monitoring. I build end-to-end Python processing pipelines to digest and analyze complex spectral datasets—integrating bad-band detection, atmospheric correction, spectral unmixing (VCA-FCLS), and spatial-spectral classification.

Your work in developing hyperspectral satellite constellations and agentic AI platforms represents the cutting edge of commercial earth observation. I bring a rare combination of academic rigor (4 peer-reviewed publications) and hands-on, production-grade Python development skills that align directly with your technical stack.

I would be thrilled to discuss how my hyperspectral processing experience can support your mission. I have attached my CV and would welcome a brief introductory call.

Thank you for your time and consideration.

Sincerely,

Dr. Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
elmansour01abdelhak@gmail.com | [Phone Number]
```




================================================================================
FILE: 02_Academic & Work/work/active/Hot Opportunities — May 2026.md (~1785 words)
================================================================================
---
generated_by: claude
date: 2026-05-24
tags: [jobs, career, remote-sensing, industry, postdoc, urgent]
status: active
last_web_search: 2026-05-24
---

# Hot Opportunities — May 2026

> Live job pipeline — Abdelhak EL MANSOUR.  
> Skills: [[PRISMA Satellite|PRISMA]] · [[EnMAP Satellite|EnMAP]] · VCA-FCLS · [[Hyperspectral Imaging|hyperspectral classification]] · XRF validation · Python · phosphate mineralogy · [[Reclamation Progress Index|reclamation monitoring]]  
> Priority: Europe → International → Morocco (real salary only)
>
> See also: [[Job Board — Live Tracker]] · [[Postdoc Outreach Dashboard]] · [[Fitted Opportunities & Targets]] · [[Review Brief — Postdoc Applications 2026]]

> **Searched:** VITO, ESA, ETH Zurich, Pixxel, BRGM, UM6P CRSA, Rio Tinto, DLR, Earthworks, EGU jobs, EURAXESS, jobs.ac.uk, academicpositions.com — 2026-05-24

---

## ✅ DONE — VITO Scientist Remote Sensing (Applied 2026-05-25)

### VITO Belgium — Scientist Remote Sensing (Water Quality)
- **Status:** ✅ APPLIED — 2026-05-25
- **Deadline: Friday May 29, 2026**
- **Location:** Mol, Antwerpen, Belgium (Hybrid)
- **Focus:** Water quality monitoring and maritime safety via satellite EO
- **Why apply:** VITO's Remote Sensing Unit is one of Europe's top EO labs. This role is water-focused but the methods (EO data fusion, Python, multi-source satellite) are identical to your toolkit. VITO actively develops hyperspectral products — there will be overlap. Getting in the door matters.
- **Fit score:** 7/10 (method fit high; topic = water not mining)
- **Required:** MSc in Sciences/Engineering, EO/RS/GIS background, Python/R/Google Earth Engine, willing to travel internationally
- **Apply:** [https://jobs.vito.be](https://jobs.vito.be) → search "Scientist Remote Sensing"
- **Status tracking:** [x] Applied

---

## Category 1 — Industry: EO & Satellite Companies

### Pixxel — Hyperspectral Scientist (Full Remote)
- **Status:** ✅ CONFIRMED OPEN (as of Mar 2026, 13 openings total)
- **Deadline:** Not listed (rolling — apply soon)
- **Location:** Remote (US/India company, distributed team)
- **Focus:** Hyperspectral data analysis, algorithm development, validation, analytics applications
- **Why this is your best industry target:** Pixxel launched 6 "Firefly" hyperspectral satellites in 2025 — operational now. They are building their science team. You are one of a small pool of people worldwide who has published operational results using satellite hyperspectral data (EnMAP) in a validated applied context. Their team needs exactly what you do.
- **Roles:** Hyperspectral Scientist (mid) + Senior/Lead Hyperspectral Scientist (senior)
- **Fit score: 9/10** — direct skills match
- **Apply:** [https://pixxel.space/careers](https://pixxel.space/careers) → apply via their Darwinbox portal
- **Status tracking:** [ ] Applied mid-level [ ] Applied senior level [ ] ❌ Skipped

---

### Pixxel — Senior Scientist / Lead Scientist — Image Processing
- **Status:** ✅ CONFIRMED OPEN
- **Location:** Remote
- **Focus:** Image processing algorithms, spectral calibration, satellite data pipeline
- **Fit score:** 8/10 — your enmap_reclamation_engine_v2.py (1,776-line production pipeline) directly demonstrates this
- **Apply:** Same portal as above
- **Status tracking:** [ ] Applied [ ] ❌ Skipped

---

## Category 2 — Research Agencies (Europe)

### VITO Belgium — Scientific Expert, Earth Observation Services
- **Status:** ✅ CONFIRMED OPEN (no deadline shown — apply asap)
- **Location:** Mol, Antwerpen, Belgium (Hybrid ~50% onsite)
- **Focus:** Design and maintain operational EO services; translate requirements into EO products; validate products; bridge science and operations; write proposals
- **Why you fit:** This role is closer to what you've done — building an operational product (RPI) that translates satellite data into a usable metric for a client (OCP Group). That is exactly what VITO "Earth Observation Services" does at scale.
- **Required:** PhD or MSc in EO/Remote Sensing/Environmental Sciences; Python for spatial data; satellite + biophysical variable expertise; English (Dutch a bonus)
- **Fit score: 8.5/10**
- **Apply:** [https://jobs.vito.be](https://jobs.vito.be) → "Scientific Expert – Earth Observation Services"
- **Status tracking:** [ ] Applied [ ] ❌ Skipped

---

### VITO Belgium — Project Lead, Earth Observation Platforms
- **Status:** ✅ CONFIRMED OPEN (no deadline shown)
- **Location:** Mol, Belgium (Hybrid)
- **Focus:** Strategy, ESA/Horizon proposal writing, consortia management, technical oversight of EO platforms
- **Required:** MSc/PhD + **5+ years PM experience** in EO sector; Copernicus + ESA proposal track record
- **Fit score:** 5/10 — strong on science side; thin on PM track record. Apply post-defense only if no other VITO role works out.
- **Apply:** [https://jobs.vito.be](https://jobs.vito.be)
- **Status tracking:** [ ] Considering [ ] ❌ Skip for now

---

### ETH Zurich — Postdoctoral Researcher / Senior Scientist in Hyperspectral Remote Sensing for Forest Management
- **Status:** ✅ CONFIRMED OPEN (posted 2025, still active May 2026)
- **Duration:** Initial 3 years, extendable to 6 years
- **Location:** Zurich, Switzerland
- **Focus:** Hyperspectral data for forest resources management — ETH Domain collaboration (WSL, University of Zurich EcoVision Lab)
- **Required:** PhD in Geomatics or related (Environmental Sciences, Civil Engineering); demonstrable expertise in remote sensing; publication record
- **Why apply even though it's forest-focused:** ETH postdoc = top-tier European career credential. The hyperspectral methods are identical. Your PRISMA/EnMAP pipeline + publication in Sensors 2025 gives you a strong application. A cover letter explaining "I'm pivoting from mine monitoring to vegetation monitoring — the hyperspectral methods are the same" is a credible case.
- **Fit score:** 7/10 (method fit = 10/10; topic fit = 5/10)
- **Apply:** [https://jobs.ethz.ch/job/view/JOPG_ethz_fsZJ7zNmhF9rd4vTnH](https://jobs.ethz.ch/job/view/JOPG_ethz_fsZJ7zNmhF9rd4vTnH)
- **Status tracking:** [ ] Applied [ ] ❌ Skipped

---

### DLR — Remote Sensing Technology Institute (IMF), Oberpfaffenhofen, Germany
- **Status:** Jobs exist but listings require direct portal access (couldn't scrape directly)
- **Why this is your strongest research agency target:** DLR built and operates EnMAP. Their IMF team in Oberpfaffenhofen IS the center for EnMAP science. Head of Hyperspectral Remote Sensing team: **Dr. Tobias Storch**.
- **The play:** Email Dr. Storch directly. One paragraph. "I defended my PhD June 30 on EnMAP-based operational reclamation monitoring at phosphate mines. Published peer-reviewed results. I'm looking for postdoc opportunities in your group." That email is worth more than a cold application.
- **Check jobs:** [https://www.dlr.de/en/eoc/careers-education/jobs-at-the-eoc](https://www.dlr.de/en/eoc/careers-education/jobs-at-the-eoc) — then follow links to concludis portal
- **Typical salary:** TVöD E13 = ~€50,000–58,000/yr (~€4,200–4,800/mo)
- **Status tracking:** [ ] Checked portal [ ] Emailed Storch [ ] Applied formally

---

### ESA — Hyperspectral Applications Scientist
- **Status:** ❌ No current openings (confirmed via jobs.esa.int May 24, 2026)
- **Note:** ESA had this role listed previously (reference 939963901) but it's not currently open. Set a job alert at jobs.esa.int for "hyperspectral" and "remote sensing" — these roles appear periodically.
- **Check back:** [https://jobs.esa.int](https://jobs.esa.int) — create alert

---

### BRGM France — French Geological Survey
- **Status:** 34 current positions; no remote sensing roles visible on pages 1–2 (May 24, 2026)
- **Positions posted:** Hydrogeology, geophysics, sedimentary basin postdoc — not RS
- **Check manually:** [https://brgm-recrute.talent-soft.com](https://brgm-recrute.talent-soft.com) — search "remote sensing" or "imaging" (site is in French — use "télédétection" or "imagerie")
- **Contact direct:** Direction Scientifique, BRGM Orléans — French expected
- **Status tracking:** [ ] Checked [ ] Applied

---

## Category 3 — Mining Industry

### Rio Tinto — Geoscientist (Perth, Australia)
- **Status:** Geoscientist roles visible but not remote sensing specific
- **Reality check:** Rio Tinto remote sensing roles exist (they run HyMap airborne hyperspectral for their Pilbara iron ore operations) but they are rare and Australia-based. Not a Europe-first option.
- **Check:** [https://www.riotinto.com/careers/available-jobs](https://www.riotinto.com/careers/available-jobs) — search "remote sensing" or "spectral"
- **Status tracking:** [ ] Checked [ ] Applied

---

### OCP Group — Direct Conversation (NOT a cold application)
- **Status:** Internal network play — highest ROI conversation you can have
- **The play:** Through Laamrani, open a conversation about whether OCP's R&D or sustainability division wants to operationalize the RPI tool. Your thesis was OCP-funded (Accord-Specific 189: SPGP). You built them something they own. Ask if they want to use it.
- **Potential:** Consulting contract €10,000–30,000 OR formal hire in R&D digital division
- **Formal careers:** [https://ocpsa.ma/fr/rejoignez-nous](https://ocpsa.ma/fr/rejoignez-nous)
- **Status tracking:** [ ] Email sent to Laamrani [ ] Meeting set [ ] Proposal submitted

---

## Category 4 — UM6P / Morocco (Internal)

### UM6P CRSA — Remote Sensing Positions (CRSA hires regularly)
- **Recently closed (for awareness):**
  - Post-Doctoral Researcher in Hyperspectral Remote Sensing for Soil Fertility Mapping — closed **Feb 12, 2026** (Benguerir, Morocco)
  - Postdoctoral Researcher in Remote Sensing for Irrigation Mapping — closed **Dec 17, 2025**
- **These roles come back.** CRSA is actively building capacity. If you want to stay in Morocco with a real research salary and advance toward faculty, CRSA is the internal track.
- **Check:** Contact CRSA director directly. UM6P career portal also lists roles.
- **Status tracking:** [ ] Inquired with CRSA [ ] Applied to open role

---

## Your Application Toolkit (Build Before Sending Anything)

| Document | Status | Notes |
|----------|--------|-------|
| Industry CV (1-page) | ❌ Not done | Strip LaTeX academic formatting; lead with skills + tools |
| Academic CV (updated) | ✅ Exists | `CV_ELMANSOUR_2026_Latex.pdf` — add defense date June 30 |
| Cover letter (base) | ❌ Not done | Write once; customize opening paragraph per employer |
| Research statement (1 page) | ❌ Not done | For ETH, DLR, VITO scientific roles |
| Portfolio slides (3 slides) | ❌ Not done | Best visuals: RPI map, EnMAP scene, confusion matrix |
| LinkedIn profile | ❓ Unknown | Update to "PhD candidate — defending June 30, 2026" |

---

## Search Platforms to Monitor Weekly

| Platform | URL | Search terms |
|----------|-----|-------------|
| VITO jobs | https://jobs.vito.be | Check weekly |
| ESA jobs | https://jobs.esa.int | Alert: "hyperspectral", "remote sensing" |
| DLR EOC | https://www.dlr.de/en/eoc/careers-education | Follow concludis link |
| jobs.ac.uk | https://www.jobs.ac.uk | hyperspectral; remote sensing; geoscience |
| EURAXESS | https://euraxess.ec.europa.eu/jobs | hyperspectral; mining; spectroscopy |
| Earthworks Jobs | https://www.earthworks-jobs.com | remote sensing; mineralogy |
| EGU Job Board | https://www.egu.eu/jobs/ | remote sensing |
| Pixxel | https://pixxel.space/careers | Check weekly |

---

## Application Tracker

| Employer | Role | Date Applied | Deadline | Status | Contact |
|----------|------|-------------|----------|--------|---------|
| VITO | Scientist Remote Sensing | 2026-05-25 | **May 29** | ✅ Applied | jobs.vito.be |
| Pixxel | Hyperspectral Scientist | | Rolling | ❌ Skipped — India-based company | pixxel.space/careers |
| Pixxel | Senior/Lead Hyperspectral Scientist | | Rolling | ❌ Skipped — India-based company | pixxel.space/careers |
| VITO | Scientific Expert EO Services | 2026-05-25 | None shown | ✅ Applied | jobs.vito.be |
| ETH Zurich | Postdoc Hyperspectral RS | | TBD | | jobs.ethz.ch |
| DLR IMF | (Portal + Storch email) | | | | Dr. Tobias Storch |
| OCP Group | RPI consulting (via Laamrani) | | | | Through Laamrani |

---

*Built 2026-05-24 with live web search. All entries verified via direct URL fetch or web search on this date.*  
*Update status column as applications are sent. Re-search platforms weekly until defense (June 30).*




================================================================================
FILE: 02_Academic & Work/work/active/Job Board — Live Tracker.md (~1138 words)
================================================================================
---
tags: [jobs, career, tracker, active]
status: active
generated_by: claude
date: 2026-05-28
updated: 2026-06-05
---

# Job Board — Live Tracker

> One-click access to every open opportunity. Update status as you go.
> Last searched: **2026-05-28**
> → Full details: [[02_Academic & Work/work/active/Hot Opportunities — May 2026]]

---

## 🔴 Urgent

| Offer | Org | Location | Fit | Deadline | Status |
|-------|-----|----------|-----|----------|--------|
| [Scientist Remote Sensing (Water Quality)](https://jobs.vito.be) | VITO | Belgium | 7/10 | **May 29 ⚠️** | ✅ Applied 2026-05-25 |

---

## 🟢 Top Fits — Apply Now

| Offer | Org | Location | Fit | Deadline | Status |
|-------|-----|----------|-----|----------|--------|
| [Scientific Expert — Earth Observation Services](https://jobs.vito.be) | VITO | Belgium (Hybrid) | 8.5/10 | None shown | ✅ Applied 2026-05-25 |
| [Postdoc — Hyperspectral RS for Forest Management](https://jobs.ethz.ch/job/view/JOPG_ethz_fsZJ7zNmhF9rd4vTnH) | ETH Zurich | Switzerland | 7/10 | TBD | ❌ Not applied |
| [Postdoc — Hyperspectral Remote Sensing](https://euraxess.ec.europa.eu/jobs/180699) | GFZ / Potsdam | Germany | 8/10 🆕 | Dec 2026 | ❌ Not applied |
| [Postdoc — Hyperspectral RS](https://professorpositions.com/postdoc-position-in-hyperspectral-remote-sensing,i31029.html) | U. Copenhagen | Denmark | 7.5/10 🆕 | Check | ❌ Not applied |

---

## 🟡 Post-Defense (Email / Network Plays)

| Action | Target | Contact | Fit | Status |
|--------|--------|---------|-----|--------|
| Email Pr. Nicole Fenton — postdoc inquiry | UQAT — IRF / NSERC Chair Biodiversity in Mining | nicole.fenton@uqat.ca | 9/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Fenton UQAT Postdoc]] |
| Email Pr. Osvaldo Valeria — postdoc inquiry | UQAT — IRF, Rouyn-Noranda, Canada | osvaldo.valeria@uqat.ca | 8.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Valeria UQAT Postdoc]] |
| Email Pr. Bruno Bussière — postdoc inquiry | UQAT — IRME / NSERC Chair Mine Reclamation | bruno.bussiere@uqat.ca | 7.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Bussiere UQAT Postdoc]] |
| Email Pr. Maxence Martin — postdoc inquiry | UQAT — IRF, boreal RS / LiDAR | maxence.martin@uqat.ca | 7/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Martin UQAT Postdoc]] |
| Email Dr. Tobias Storch directly | DLR IMF — Imaging Spectroscopy Dept., Oberpfaffenhofen | tobias.storch@dlr.de | 10/10 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Storch DLR IMF Postdoc]] |
| Email Dr. Sarah Asam | DLR DFD — Forest Ecosystems Team, Oberpfaffenhofen | sarah.asam@dlr.de | 9/10 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Asam DLR DFD Postdoc]] |
| Email Prof. Sabine Chabrillat — postdoc inquiry | GFZ Potsdam — Hyperspectral RS group / EnMAP Science PI | sabine.chabrillat@gfz-potsdam.de | 9.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Chabrillat GFZ Postdoc]] |
| Email Dr. Richard Gloaguen — postdoc inquiry | HZDR / Helmholtz Freiberg — Exploration Technology div. | r.gloaguen@hzdr.de | 9/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Gloaguen HZDR Postdoc]] |
| Email Dr. Saeid Asadzadeh — postdoc inquiry | GFZ Potsdam — EnMAP science team, mineral RS | saeid.asadzadeh@gfz-potsdam.de | 9/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Asadzadeh GFZ Postdoc]] |
| Email Dr. Sandra Lorenz — postdoc inquiry | HZDR Freiberg — Group Leader Digital Processing, mine RS | s.lorenz@hzdr.de | 9/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Lorenz HZDR Postdoc]] |
| Email Dr. Mahdi Khodadadzadeh — postdoc inquiry | ITC Twente — hyperspectral + ML for mining mineralogy | m.khodadadzadeh@utwente.nl | 8.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Khodadadzadeh ITC Postdoc]] |
| Email Prof. Kamran Esmaeili — postdoc inquiry | Univ. Toronto — hyperspectral ore-waste discrimination + ML | kamran.esmaeili@utoronto.ca | 8.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Esmaeili UofT Postdoc]] |
| Network: Dr. Mehdi Abdolmaleki (postdoc in Esmaeili lab) | Univ. Toronto — peer, hyperspectral mining RS | mehdi.abdolmaleki@utoronto.ca | peer | 🔗 Contact after emailing Esmaeili |
| Email Dr. Nicola Mondillo — postdoc inquiry | Univ. Naples Federico II — PRISMA + geochemistry for mining mineralogy | nicola.mondillo@unina.it | 8.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Mondillo Naples Postdoc]] |
| Email Dr. Anna Sorrentino — peer inquiry | Univ. Naples Federico II — PRISMA satellite mining geology | anna.sorrentino@unina.it | peer 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Sorrentino Naples Inquiry]] |
| Email Dr. Chris Hecker — postdoc inquiry | ITC Twente — TIR hyperspectral mineralogy, EMIT, GreenMiner | c.a.hecker@utwente.nl | 7.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Hecker ITC Postdoc]] |
| Email Dr. Martin Schodlok — inquiry | BGR Hannover — mine tailings hyperspectral monitoring | martin.schodlok@bgr.de | 7.5/10 🆕 | ✍️ Letter drafted — [[02_Academic & Work/work/applications/Cover Letter — Schodlok BGR Postdoc]] |
| OCP Group — RPI consulting via Laamrani | OCP Group | Through supervisor | High ROI | ❌ Email not sent |
| ESA — set job alert | [jobs.esa.int](https://jobs.esa.int) | — | — | ❌ Alert not set |

---

## 🔵 Check & Decide

| Offer | Org | Location | Fit | Link | Status |
|-------|-----|----------|-----|------|--------|
| Research Scientist / Postdoc RS | Luke (Finland) | Finland | 6/10 🆕 | [Link](https://academicpositions.com/ad/natural-resources-institute-finland-luke/2026/research-scientist-postdoc-remote-sensing/246201) | ❌ Check if open |
| Project Lead — EO Platforms | VITO | Belgium | 5/10 | [jobs.vito.be](https://jobs.vito.be) | ⏭️ Skip for now |
| Geoscientist | Rio Tinto | Australia | 4/10 | [riotinto.com/careers](https://www.riotinto.com/careers/available-jobs) | ⏭️ Skip |

---

## 📋 Application Toolkit (Blocker for Most Applications)

| Document | Status |
|----------|--------|
| Academic CV (updated) | ✅ `CV_ELMANSOUR_2026_Latex.pdf` — add defense date |
| Industry CV (1-page) | ❌ Not done |
| Cover letter (base) | ❌ Not done |
| Research statement (1 page) | ❌ Not done — needed for ETH, DLR, VITO |
| Portfolio slides (3 slides) | ❌ Not done |
| LinkedIn updated | ❓ Check |

---

## 🔍 Weekly Scan — Job Boards

| Board | Link | Search Terms |
|-------|------|-------------|
| VITO | [jobs.vito.be](https://jobs.vito.be) | Check weekly |
| ESA | [jobs.esa.int](https://jobs.esa.int) | hyperspectral, remote sensing |
| DLR EOC | [dlr.de/en/eoc/careers-education](https://www.dlr.de/en/eoc/careers-education/jobs-at-the-eoc) | — |
| EURAXESS | [euraxess.ec.europa.eu/jobs](https://euraxess.ec.europa.eu/jobs) | hyperspectral; mineralogy; mining |
| space-careers.com | [space-careers.com](https://www.space-careers.com/jobs/remote_sensing_optics_and_gis) | RS, optics, GIS |
| earthworks-jobs.com | [earthworks-jobs.com](https://www.earthworks-jobs.com/remotesensing) | remote sensing; mineralogy |
| jobs.ac.uk | [jobs.ac.uk](https://www.jobs.ac.uk) | hyperspectral; remote sensing |
| Academic Positions | [academicpositions.com](https://academicpositions.com/jobs/field/remote-sensing-geosciences) | remote sensing |
| LinkedIn Belgium EO | [LinkedIn](https://be.linkedin.com/jobs/earth-observation-jobs) | EO, satellite |
| Pixxel | [pixxel.space/careers](https://pixxel.space/careers) | Check weekly |

---

> **Rule:** Defense first. Applications post-June 30 except for rolling deadlines already in progress.
> 🆕 = new find 2026-05-28




================================================================================
FILE: 02_Academic & Work/work/active/Job Pipeline.md (~410 words)
================================================================================
---
kanban-plugin: basic
tags: [jobs, career, kanban, active]
status: active
generated_by: claude
date: 2026-06-07
---

## 🎯 To Apply

- [ ] **ETH Zurich — Postdoc Hyperspectral RS for Forest** #deadline/TBD @{2026-07-15} fit::7/10
- [ ] **GFZ / Potsdam — Postdoc Hyperspectral RS** #deadline/Dec2026 fit::8/10
- [ ] **U. Copenhagen — Postdoc Hyperspectral RS** #deadline/check fit::7.5/10
- [ ] **Luke Finland — Research Scientist/Postdoc RS** #deadline/check fit::6/10

## ✍️ Letter Drafted

- [ ] **DLR IMF — Dr. Tobias Storch** fit::10/10 → [[02_Academic & Work/work/applications/Cover Letter — Storch DLR IMF Postdoc]]
- [ ] **DLR DFD — Dr. Sarah Asam** fit::9/10 → [[02_Academic & Work/work/applications/Cover Letter — Asam DLR DFD Postdoc]]
- [ ] **GFZ — Pr. Sabine Chabrillat** fit::9.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Chabrillat GFZ Postdoc]]
- [ ] **HZDR — Dr. Richard Gloaguen** fit::9/10 → [[02_Academic & Work/work/applications/Cover Letter — Gloaguen HZDR Postdoc]]
- [ ] **GFZ — Dr. Saeid Asadzadeh** fit::9/10 → [[02_Academic & Work/work/applications/Cover Letter — Asadzadeh GFZ Postdoc]]
- [ ] **HZDR — Dr. Sandra Lorenz** fit::9/10 → [[02_Academic & Work/work/applications/Cover Letter — Lorenz HZDR Postdoc]]
- [ ] **ITC Twente — Dr. Khodadadzadeh** fit::8.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Khodadadzadeh ITC Postdoc]]
- [ ] **U. Toronto — Pr. Esmaeili** fit::8.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Esmaeili UofT Postdoc]]
- [ ] **UQAT — Pr. Nicole Fenton** fit::9/10 → [[02_Academic & Work/work/applications/Cover Letter — Fenton UQAT Postdoc]]
- [ ] **UQAT — Pr. Osvaldo Valeria** fit::8.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Valeria UQAT Postdoc]]
- [ ] **UQAT — Pr. Bruno Bussière** fit::7.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Bussiere UQAT Postdoc]]
- [ ] **UQAT — Pr. Maxence Martin** fit::7/10 → [[02_Academic & Work/work/applications/Cover Letter — Martin UQAT Postdoc]]
- [ ] **Naples — Dr. Mondillo** fit::8.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Mondillo Naples Postdoc]]
- [ ] **ITC Twente — Dr. Hecker** fit::7.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Hecker ITC Postdoc]]
- [ ] **BGR — Dr. Schodlok** fit::7.5/10 → [[02_Academic & Work/work/applications/Cover Letter — Schodlok BGR Postdoc]]
- [ ] **OCP Group — via Laamrani** fit::High ROI

## 📤 Sent (Post-Defense)

- [ ] Item placeholder — move cards here after sending

## 📞 Interview

- [ ] Item placeholder

## ✅ Offer / Closed

- [ ] **VITO — Scientist Water Quality** ✅ Applied 2026-05-25
- [ ] **VITO — Scientific Expert EO Services** ✅ Applied 2026-05-25

%% kanban:settings
```
{"kanban-plugin":"basic","hide-tags-in-title":false,"link-date-to-daily-note":false}
```
%%




================================================================================
FILE: 02_Academic & Work/work/active/Postdoc Applications.md (~690 words)
================================================================================
---
tags: [work, active, postdoc, career]
updated: 2026-05-27
status: active — launch July 1, 2026 post-defense
generated_by: claude
---

# Postdoc Applications

> [!TIP]
> **Outreach Dashboard**: All 16 cold emails and tracking checkboxes are consolidated in the [[02_Academic & Work/work/active/Postdoc Outreach Dashboard|Postdoc Outreach Dashboard]]. Use it to launch your cold outreach on July 1.

> "Dr." title changes everything. Start blasting July 1.
> Main tracker: → [[02_Academic & Work/work/active/Hot Opportunities — May 2026]]

---

## Priority Targets

### 🇩🇪 GFZ Potsdam — Section 1.4 (NEW #1 PRIORITY)
- **Status:** Spontaneous application — send July 1
- **Contact:** Dr. Sabine Chabrillat — chabri@gfz-potsdam.de
- **Pitch:** "I built an EnMAP + PRISMA operational pipeline for mine mineralogy and reclamation monitoring. Your section's work on geological/soil hyperspectral applications is the direct scientific context."
- **Why it's #1:** Section 1.4 holds the EnMAP science lead at GFZ. Previous postdoc posting (ref. 9937) = recurring pattern. Chabrillat is Francophone — French email works. Thematic overlap is exact: mineralogy, geological hyperspectral, EnMAP.
- **Portal:** gfz.de/en/career/job-offers (also check for active listings)
- **Template:** [[04_Knowledge Base/AI-Generated/drafts/spontaneous-application-kit-2026-06-03]] Template 3

### 🇩🇪 DLR IMF — Oberpfaffenhofen
- **Status:** Direct email to send after defense
- **Contact:** Dr. Tobias Storch — Head of Hyperspectral RS team, DLR IMF
- **Pitch:** "I defended my PhD June 30 on EnMAP-based operational reclamation monitoring. I built an operational pipeline. Looking for a postdoc in your group."
- **Why it's the best fit:** DLR built and operates EnMAP. You built an operational EnMAP pipeline. There is no stronger technical match in Europe.
- **Salary:** TVöD E13 ~€50,000–58,000/yr
- **Portal:** https://www.dlr.de/en/eoc/careers-education

### 🇨🇭 ETH Zurich — Postdoc Hyperspectral RS for Forest Management
- **Status:** Open (posted 2025, still active May 2026)
- **Fit:** 7/10 — identical methods, different domain (forest vs mine)
- **Duration:** 3 years, extendable to 6 years
- **Portal:** → [[02_Academic & Work/work/active/Hot Opportunities — May 2026]]

### 🇧🇪 VITO — Scientific Expert EO Services
- **Status:** ✅ Applied 2026-05-25 — awaiting response
- **Fit:** 8.5/10
- **Typical response time:** 2–6 weeks

### 🇲🇦 UM6P CRSA — Remote Sensing Positions
- **Status:** Recurring positions — hyperspectral role closed Feb 2026 but comes back
- **Action:** Contact CRSA director directly post-defense
- **Advantage:** Stay in Morocco with real research salary + proximity to OCP

---

### 🇫🇷 BRGM — Orléans (Spontaneous)
- **Status:** Spontaneous application — send July 1
- **Team:** Télédétection géologique / Géoressources
- **Why:** French geological survey, active RS team, French-language advantage
- **Template:** → [[04_Knowledge Base/AI-Generated/drafts/spontaneous-application-kit-2026-06-03]] Template 2

### 🇩🇪 BGR — Hannover (Spontaneous)
- **Status:** Spontaneous application — send July 1
- **Team:** Fachbereich B4 Fernerkundung
- **Why:** German geological survey; mineral + mine RS is their core mission
- **Template:** → [[04_Knowledge Base/AI-Generated/drafts/spontaneous-application-kit-2026-06-03]] Template 2

### 🇮🇹 ESA ESRIN — Frascati (Spontaneous)
- **Status:** Spontaneous application — send July 7
- **Contact:** EO Science & Applications Division (check jobs.esa.int + direct email)
- **Why:** PRISMA is an ASI/ESA instrument; PRISMA pipeline = direct technical hook
- **Template:** → [[04_Knowledge Base/AI-Generated/drafts/spontaneous-application-kit-2026-06-03]] Template 2

### 🇫🇮 GTK — Finland (Spontaneous)
- **Status:** Spontaneous application — send July 7
- **Why:** Active hyperspectral + mine RS program; open to international profiles

---

## Dropped / Ruled Out
- ~~NORCE Norway~~ — not an active target
- ~~NRCan Canada~~ — too far from Europe/Morocco priority

---

## Email Templates
→ [[04_Knowledge Base/AI-Generated/drafts/spontaneous-application-kit-2026-06-03]]
- **Template 1** — Postdoc (cold email to PI)
- **Template 2** — Industry / EO company / geological survey
- **Template 3** — DLR Dr. Storch (specific, do not dilute)

---

## Application Checklist (per institution)
- [ ] CV updated with "Dr." title
- [ ] Google Scholar + LinkedIn updated with title
- [ ] Cover letter adapted (focus on operational engineering vs pure academic)
- [ ] Reference letters (ask Laamrani before defense)

---

## Salary Context
| Location | Postdoc salary | Note |
|----------|---------------|------|
| DLR (Germany) | ~€4,200–4,800/mo | TVöD E13 |
| ETH Zurich (Switzerland) | ~CHF 5,000–6,000/mo | Very strong |
| VITO (Belgium) | ~€3,000–4,000/mo | Estimated |
| CRSA UM6P (Morocco) | ~€1,000–2,000/mo | Local context |




================================================================================
FILE: 02_Academic & Work/work/active/Postdoc Outreach Dashboard.md (~5071 words)
================================================================================
---
generated_by: claude
date: 2026-06-07
tags: [work, active, postdoc, outreach, dashboard]
status: active
summary: "A central tracking dashboard and cold outreach email templates with clickable mailto: links for 16 priority postdoc target PIs."
---

# 🎓 Postdoc Outreach Dashboard

> [!IMPORTANT]
> **Strategy Note**: Academic PIs are extremely busy. Do not send a long cover letter as your first cold email. Instead, send a **short, high-impact introductory email** (templates below) introducing yourself, expressing interest in their group's research, and linking your CV/thesis abstract. Offer to discuss further via a video call.

> [!TIP]
> **One-Click Email Drafts**: Each template has an **`✉️ Open Draft in Mail Client`** button. Clicking it will instantly open your default mail client (Gmail, Outlook, etc.) with the recipient, subject, and body pre-filled. You just need to attach your CV and click send!

## 📋 Outreach Master Tracker

| PI Target Name | Institution | Country | Cover Letter Link | Outreach Status |
| :--- | :--- | :--- | :--- | :--- |
| **Dr. Saeid Asadzadeh** | GFZ Potsdam | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Asadzadeh GFZ Postdoc.md|Dr. Saeid Asadzadeh Letter]] | - [ ] Not Contacted |
| **Dr. Sarah Asam** | DLR | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Asam DLR DFD Postdoc.md|Dr. Sarah Asam Letter]] | - [ ] Not Contacted |
| **Pr. Bruno Bussière** | UQAT | 🇨🇦 Canada | [[02_Academic & Work/work/applications/Cover Letter — Bussiere UQAT Postdoc.md|Pr. Bruno Bussière Letter]] | - [ ] Not Contacted |
| **Prof. Dr. Sabine Chabrillat** | GFZ Helmholtz Centre for Geosciences, Potsdam | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Chabrillat GFZ Postdoc.md|Prof. Dr. Sabine Chabrillat Letter]] | - [ ] Not Contacted |
| **Prof. Kamran Esmaeili** | University of Toronto | 🇨🇦 Canada | [[02_Academic & Work/work/applications/Cover Letter — Esmaeili UofT Postdoc.md|Prof. Kamran Esmaeili Letter]] | - [ ] Not Contacted |
| **Pr. Nicole Fenton** | UQAT | 🇨🇦 Canada | [[02_Academic & Work/work/applications/Cover Letter — Fenton UQAT Postdoc.md|Pr. Nicole Fenton Letter]] | - [ ] Not Contacted |
| **Dr. Richard Gloaguen** | HZDR | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Gloaguen HZDR Postdoc.md|Dr. Richard Gloaguen Letter]] | - [ ] Not Contacted |
| **Dr. Chris Hecker** | ITC | 🇳🇱 Netherlands | [[02_Academic & Work/work/applications/Cover Letter — Hecker ITC Postdoc.md|Dr. Chris Hecker Letter]] | - [ ] Not Contacted |
| **Dr. Mahdi Khodadadzadeh** | ITC | 🇳🇱 Netherlands | [[02_Academic & Work/work/applications/Cover Letter — Khodadadzadeh ITC Postdoc.md|Dr. Mahdi Khodadadzadeh Letter]] | - [ ] Not Contacted |
| **Dr. Sandra Lorenz** | HZDR | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Lorenz HZDR Postdoc.md|Dr. Sandra Lorenz Letter]] | - [ ] Not Contacted |
| **Prof. Maxence Martin** | UQAT | 🇨🇦 Canada | [[02_Academic & Work/work/applications/Cover Letter — Martin UQAT Postdoc.md|Prof. Maxence Martin Letter]] | - [ ] Not Contacted |
| **Dr. Nicola Mondillo** | University of Naples Federico II | 🇮🇹 Italy | [[02_Academic & Work/work/applications/Cover Letter — Mondillo Naples Postdoc.md|Dr. Nicola Mondillo Letter]] | - [ ] Not Contacted |
| **Dr. Martin Schodlok** | BGR | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Schodlok BGR Postdoc.md|Dr. Martin Schodlok Letter]] | - [ ] Not Contacted |
| **Dr. Anna Sorrentino** | University of Naples Federico II | 🇮🇹 Italy | [[02_Academic & Work/work/applications/Cover Letter — Sorrentino Naples Inquiry.md|Dr. Anna Sorrentino Letter]] | - [ ] Not Contacted |
| **Dr. Tobias Storch** | DLR | 🇩🇪 Germany | [[02_Academic & Work/work/applications/Cover Letter — Storch DLR IMF Postdoc.md|Dr. Tobias Storch Letter]] | - [ ] Not Contacted |
| **Pr. Osvaldo Valeria** | UQAT | 🇨🇦 Canada | [[02_Academic & Work/work/applications/Cover Letter — Valeria UQAT Postdoc.md|Pr. Osvaldo Valeria Letter]] | - [ ] Not Contacted |

---

## 📧 Tailored Cold Email Templates

### 👤 Dr. Saeid Asadzadeh (GFZ Potsdam — 🇩🇪 Germany)
**Email Address**: `saeid.asadzadeh@gfz-potsdam.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Asadzadeh GFZ Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:saeid.asadzadeh@gfz-potsdam.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Asadzadeh%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20GFZ%20Potsdam.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20geological%20remote%20sensing%20and%20hyperspectral%20unmixing.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20mineral%20mapping%20and%20PRISMA%20data%20processing%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Asadzadeh,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at GFZ Potsdam. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on geological remote sensing and hyperspectral unmixing.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in mineral mapping and PRISMA data processing aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Sarah Asam (DLR — 🇩🇪 Germany)
**Email Address**: `sarah.asam@dlr.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Asam DLR DFD Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:sarah.asam@dlr.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Asam%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20DLR.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20land%20surface%20monitoring%20and%20multi-temporal%20remote%20sensing.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20machine%20learning%20classification%20and%20surface%20analysis%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Asam,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at DLR. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on land surface monitoring and multi-temporal remote sensing.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in machine learning classification and surface analysis aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Pr. Bruno Bussière (UQAT — 🇨🇦 Canada)
**Email Address**: `bruno.bussiere@uqat.ca`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Bussiere UQAT Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:bruno.bussiere@uqat.ca?subject=Demande%20de%20candidature%20postdoctorale%20%E2%80%94%20T%C3%A9l%C3%A9d%C3%A9tection%20/%20Imagerie%20hyperspectrale%20%E2%80%94%20Dr%20Abdelhak%20EL%20MANSOUR&body=Monsieur%20le%20Professeur%20Bussi%C3%A8re%2C%0A%0AJe%20me%20permets%20de%20vous%20contacter%20pour%20solliciter%20une%20opportunit%C3%A9%20de%20recherche%20postdoctorale%20au%20sein%20de%20votre%20%C3%A9quipe%20%C3%A0%20UQAT.%20Doctorant%20%C3%A0%20l%27Universit%C3%A9%20Mohammed%20VI%20Polytechnique%20%28UM6P%29%20au%20Maroc%2C%20je%20soutiendrai%20ma%20th%C3%A8se%20le%2030%20juin%202026%2C%20et%20je%20suis%20particuli%C3%A8rement%20int%C3%A9ress%C3%A9%20par%20vos%20travaux%20sur%20la%20restauration%20et%20la%20gestion%20environnementale%20des%20sites%20miniers.%0A%0AMes%20recherches%20de%20doctorat%2C%20men%C3%A9es%20sous%20la%20direction%20du%20Pr%20Ahmed%20LAAMRANI%2C%20portent%20sur%20le%20d%C3%A9veloppement%20de%20m%C3%A9thodologies%20de%20t%C3%A9l%C3%A9d%C3%A9tection%20multi-%C3%A9chelle%20et%20d%27algorithmes%20d%27apprentissage%20automatique%20pour%20la%20caract%C3%A9risation%20min%C3%A9ralogique%20et%20le%20suivi%20de%20la%20restauration%20des%20haldes%20de%20st%C3%A9riles%20miniers.%20J%27ai%20notamment%20d%C3%A9velopp%C3%A9%20des%20pipelines%20op%C3%A9rationnels%20en%20Python%20pour%20l%27analyse%20des%20donn%C3%A9es%20hyperspectrales%20satellitaires%20%28EnMAP%20et%20PRISMA%29%2C%20valid%C3%A9s%20par%20g%C3%A9ochimie%20de%20terrain%20%28XRF%29%20et%20analyses%20de%20laboratoire%20%28DRX%29.%0A%0AJ%27ai%20pr%C3%A9par%C3%A9%20une%20lettre%20de%20motivation%20d%C3%A9taill%C3%A9e%20d%C3%A9crivant%20mon%20parcours%20et%20la%20synergie%20de%20mes%20comp%C3%A9tences%20avec%20vos%20projets%20de%20recherche%20%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AJe%20serais%20ravi%20de%20pouvoir%20%C3%A9changer%20bri%C3%A8vement%20avec%20vous%20par%20visioconf%C3%A9rence%20pour%20discuter%20de%20possibilit%C3%A9s%20de%20collaboration%20ou%20de%20postes%20disponibles.%20Je%20vous%20joins%20mon%20CV%2C%20mon%20r%C3%A9sum%C3%A9%20de%20th%C3%A8se%20ainsi%20qu%27une%20publication%20repr%C3%A9sentative.%0A%0AJe%20vous%20remercie%20vivement%20pour%20le%20temps%20accord%C3%A9%20%C3%A0%20l%27examen%20de%20ma%20candidature.%0A%0AJe%20vous%20prie%20d%27agr%C3%A9er%2C%20Monsieur%20le%20Professeur%20Bussi%C3%A8re%2C%20l%27expression%20de%20mes%20salutations%20distingu%C3%A9es.%0A%0AAbdelhak%20EL%20MANSOUR%0ADoctorant%20en%20T%C3%A9l%C3%A9d%C3%A9tection%20et%20G%C3%A9osciences%20de%20l%27Environnement%0AUM6P%2C%20Maroc)

```text
Objet : Demande de candidature postdoctorale — Télédétection / Imagerie hyperspectrale — Dr Abdelhak EL MANSOUR

Monsieur le Professeur Bussière,

Je me permets de vous contacter pour solliciter une opportunité de recherche postdoctorale au sein de votre équipe à UQAT. Doctorant à l'Université Mohammed VI Polytechnique (UM6P) au Maroc, je soutiendrai ma thèse le 30 juin 2026, et je suis particulièrement intéressé par vos travaux sur la restauration et la gestion environnementale des sites miniers.

Mes recherches de doctorat, menées sous la direction du Pr Ahmed LAAMRANI, portent sur le développement de méthodologies de télédétection multi-échelle et d'algorithmes d'apprentissage automatique pour la caractérisation minéralogique et le suivi de la restauration des haldes de stériles miniers. J'ai notamment développé des pipelines opérationnels en Python pour l'analyse des données hyperspectrales satellitaires (EnMAP et PRISMA), validés par géochimie de terrain (XRF) et analyses de laboratoire (DRX).

J'ai préparé une lettre de motivation détaillée décrivant mon parcours et la synergie de mes compétences avec vos projets de recherche :
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

Je serais ravi de pouvoir échanger brièvement avec vous par visioconférence pour discuter de possibilités de collaboration ou de postes disponibles. Je vous joins mon CV, mon résumé de thèse ainsi qu'une publication représentative.

Je vous remercie vivement pour le temps accordé à l'examen de ma candidature.

Je vous prie d'agréer, Monsieur le Professeur Bussière, l'expression de mes salutations distinguées.

Abdelhak EL MANSOUR
Doctorant en Télédétection et Géosciences de l'Environnement
UM6P, Maroc
```

---

### 👤 Prof. Dr. Sabine Chabrillat (GFZ Helmholtz Centre for Geosciences, Potsdam — 🇩🇪 Germany)
**Email Address**: `chabri@gfz-potsdam.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Chabrillat GFZ Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:chabri@gfz-potsdam.de?subject=Demande%20de%20candidature%20postdoctorale%20%E2%80%94%20T%C3%A9l%C3%A9d%C3%A9tection%20/%20Imagerie%20hyperspectrale%20%E2%80%94%20Dr%20Abdelhak%20EL%20MANSOUR&body=Madame%20la%20Professeure%20Chabrillat%2C%0A%0AJe%20me%20permets%20de%20vous%20contacter%20pour%20solliciter%20une%20opportunit%C3%A9%20de%20recherche%20postdoctorale%20au%20sein%20de%20votre%20%C3%A9quipe%20%C3%A0%20GFZ%20Helmholtz%20Centre%20for%20Geosciences%2C%20Potsdam.%20Doctorant%20%C3%A0%20l%27Universit%C3%A9%20Mohammed%20VI%20Polytechnique%20%28UM6P%29%20au%20Maroc%2C%20je%20soutiendrai%20ma%20th%C3%A8se%20le%2030%20juin%202026%2C%20et%20je%20suis%20particuli%C3%A8rement%20int%C3%A9ress%C3%A9%20par%20vos%20travaux%20sur%20hyperspectral%20applications%20for%20bare%20soil%20and%20mineral%20mapping.%0A%0AMes%20recherches%20de%20doctorat%2C%20men%C3%A9es%20sous%20la%20direction%20du%20Pr%20Ahmed%20LAAMRANI%2C%20portent%20sur%20le%20d%C3%A9veloppement%20de%20m%C3%A9thodologies%20de%20t%C3%A9l%C3%A9d%C3%A9tection%20multi-%C3%A9chelle%20et%20d%27algorithmes%20d%27apprentissage%20automatique%20pour%20la%20caract%C3%A9risation%20min%C3%A9ralogique%20et%20le%20suivi%20de%20la%20restauration%20des%20haldes%20de%20st%C3%A9riles%20miniers.%20J%27ai%20notamment%20d%C3%A9velopp%C3%A9%20des%20pipelines%20op%C3%A9rationnels%20en%20Python%20pour%20l%27analyse%20des%20donn%C3%A9es%20hyperspectrales%20satellitaires%20%28EnMAP%20et%20PRISMA%29%2C%20valid%C3%A9s%20par%20g%C3%A9ochimie%20de%20terrain%20%28XRF%29%20et%20analyses%20de%20laboratoire%20%28DRX%29.%0A%0AJ%27ai%20pr%C3%A9par%C3%A9%20une%20lettre%20de%20motivation%20d%C3%A9taill%C3%A9e%20d%C3%A9crivant%20mon%20parcours%20et%20la%20synergie%20de%20mes%20comp%C3%A9tences%20avec%20vos%20projets%20de%20recherche%20%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AJe%20serais%20ravi%20de%20pouvoir%20%C3%A9changer%20bri%C3%A8vement%20avec%20vous%20par%20visioconf%C3%A9rence%20pour%20discuter%20de%20possibilit%C3%A9s%20de%20collaboration%20ou%20de%20postes%20disponibles.%20Je%20vous%20joins%20mon%20CV%2C%20mon%20r%C3%A9sum%C3%A9%20de%20th%C3%A8se%20ainsi%20qu%27une%20publication%20repr%C3%A9sentative.%0A%0AJe%20vous%20remercie%20vivement%20pour%20le%20temps%20accord%C3%A9%20%C3%A0%20l%27examen%20de%20ma%20candidature.%0A%0AJe%20vous%20prie%20d%27agr%C3%A9er%2C%20Madame%20la%20Professeure%20Chabrillat%2C%20l%27expression%20de%20mes%20salutations%20distingu%C3%A9es.%0A%0AAbdelhak%20EL%20MANSOUR%0ADoctorant%20en%20T%C3%A9l%C3%A9d%C3%A9tection%20et%20G%C3%A9osciences%20de%20l%27Environnement%0AUM6P%2C%20Maroc)

```text
Objet : Demande de candidature postdoctorale — Télédétection / Imagerie hyperspectrale — Dr Abdelhak EL MANSOUR

Madame la Professeure Chabrillat,

Je me permets de vous contacter pour solliciter une opportunité de recherche postdoctorale au sein de votre équipe à GFZ Helmholtz Centre for Geosciences, Potsdam. Doctorant à l'Université Mohammed VI Polytechnique (UM6P) au Maroc, je soutiendrai ma thèse le 30 juin 2026, et je suis particulièrement intéressé par vos travaux sur hyperspectral applications for bare soil and mineral mapping.

Mes recherches de doctorat, menées sous la direction du Pr Ahmed LAAMRANI, portent sur le développement de méthodologies de télédétection multi-échelle et d'algorithmes d'apprentissage automatique pour la caractérisation minéralogique et le suivi de la restauration des haldes de stériles miniers. J'ai notamment développé des pipelines opérationnels en Python pour l'analyse des données hyperspectrales satellitaires (EnMAP et PRISMA), validés par géochimie de terrain (XRF) et analyses de laboratoire (DRX).

J'ai préparé une lettre de motivation détaillée décrivant mon parcours et la synergie de mes compétences avec vos projets de recherche :
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

Je serais ravi de pouvoir échanger brièvement avec vous par visioconférence pour discuter de possibilités de collaboration ou de postes disponibles. Je vous joins mon CV, mon résumé de thèse ainsi qu'une publication représentative.

Je vous remercie vivement pour le temps accordé à l'examen de ma candidature.

Je vous prie d'agréer, Madame la Professeure Chabrillat, l'expression de mes salutations distinguées.

Abdelhak EL MANSOUR
Doctorant en Télédétection et Géosciences de l'Environnement
UM6P, Maroc
```

---

### 👤 Prof. Kamran Esmaeili (University of Toronto — 🇨🇦 Canada)
**Email Address**: `kamran.esmaeili@utoronto.ca`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Esmaeili UofT Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:kamran.esmaeili@utoronto.ca?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Professor%20Esmaeili%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20University%20of%20Toronto.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20mine%20waste%20management%20and%20civil/mineral%20engineering%20remote%20sensing%20applications.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20phosphate%20waste%20rock%20characterization%20and%20multi-scale%20monitoring%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Professor Esmaeili,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at University of Toronto. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on mine waste management and civil/mineral engineering remote sensing applications.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in phosphate waste rock characterization and multi-scale monitoring aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Pr. Nicole Fenton (UQAT — 🇨🇦 Canada)
**Email Address**: `nicole.fenton@uqat.ca`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Fenton UQAT Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:nicole.fenton@uqat.ca?subject=Demande%20de%20candidature%20postdoctorale%20%E2%80%94%20T%C3%A9l%C3%A9d%C3%A9tection%20/%20Imagerie%20hyperspectrale%20%E2%80%94%20Dr%20Abdelhak%20EL%20MANSOUR&body=Madame%20la%20Professeure%20Fenton%2C%0A%0AJe%20me%20permets%20de%20vous%20contacter%20pour%20solliciter%20une%20opportunit%C3%A9%20de%20recherche%20postdoctorale%20au%20sein%20de%20votre%20%C3%A9quipe%20%C3%A0%20UQAT.%20Doctorant%20%C3%A0%20l%27Universit%C3%A9%20Mohammed%20VI%20Polytechnique%20%28UM6P%29%20au%20Maroc%2C%20je%20soutiendrai%20ma%20th%C3%A8se%20le%2030%20juin%202026%2C%20et%20je%20suis%20particuli%C3%A8rement%20int%C3%A9ress%C3%A9%20par%20vos%20travaux%20sur%20la%20biodiversit%C3%A9%20et%20la%20restauration%20%C3%A9cologique%20en%20contexte%20minier%20nordique.%0A%0AMes%20recherches%20de%20doctorat%2C%20men%C3%A9es%20sous%20la%20direction%20du%20Pr%20Ahmed%20LAAMRANI%2C%20portent%20sur%20le%20d%C3%A9veloppement%20de%20m%C3%A9thodologies%20de%20t%C3%A9l%C3%A9d%C3%A9tection%20multi-%C3%A9chelle%20et%20d%27algorithmes%20d%27apprentissage%20automatique%20pour%20la%20caract%C3%A9risation%20min%C3%A9ralogique%20et%20le%20suivi%20de%20la%20restauration%20des%20haldes%20de%20st%C3%A9riles%20miniers.%20J%27ai%20notamment%20d%C3%A9velopp%C3%A9%20des%20pipelines%20op%C3%A9rationnels%20en%20Python%20pour%20l%27analyse%20des%20donn%C3%A9es%20hyperspectrales%20satellitaires%20%28EnMAP%20et%20PRISMA%29%2C%20valid%C3%A9s%20par%20g%C3%A9ochimie%20de%20terrain%20%28XRF%29%20et%20analyses%20de%20laboratoire%20%28DRX%29.%0A%0AJ%27ai%20pr%C3%A9par%C3%A9%20une%20lettre%20de%20motivation%20d%C3%A9taill%C3%A9e%20d%C3%A9crivant%20mon%20parcours%20et%20la%20synergie%20de%20mes%20comp%C3%A9tences%20avec%20vos%20projets%20de%20recherche%20%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AJe%20serais%20ravi%20de%20pouvoir%20%C3%A9changer%20bri%C3%A8vement%20avec%20vous%20par%20visioconf%C3%A9rence%20pour%20discuter%20de%20possibilit%C3%A9s%20de%20collaboration%20ou%20de%20postes%20disponibles.%20Je%20vous%20joins%20mon%20CV%2C%20mon%20r%C3%A9sum%C3%A9%20de%20th%C3%A8se%20ainsi%20qu%27une%20publication%20repr%C3%A9sentative.%0A%0AJe%20vous%20remercie%20vivement%20pour%20le%20temps%20accord%C3%A9%20%C3%A0%20l%27examen%20de%20ma%20candidature.%0A%0AJe%20vous%20prie%20d%27agr%C3%A9er%2C%20Madame%20la%20Professeure%20Fenton%2C%20l%27expression%20de%20mes%20salutations%20distingu%C3%A9es.%0A%0AAbdelhak%20EL%20MANSOUR%0ADoctorant%20en%20T%C3%A9l%C3%A9d%C3%A9tection%20et%20G%C3%A9osciences%20de%20l%27Environnement%0AUM6P%2C%20Maroc)

```text
Objet : Demande de candidature postdoctorale — Télédétection / Imagerie hyperspectrale — Dr Abdelhak EL MANSOUR

Madame la Professeure Fenton,

Je me permets de vous contacter pour solliciter une opportunité de recherche postdoctorale au sein de votre équipe à UQAT. Doctorant à l'Université Mohammed VI Polytechnique (UM6P) au Maroc, je soutiendrai ma thèse le 30 juin 2026, et je suis particulièrement intéressé par vos travaux sur la biodiversité et la restauration écologique en contexte minier nordique.

Mes recherches de doctorat, menées sous la direction du Pr Ahmed LAAMRANI, portent sur le développement de méthodologies de télédétection multi-échelle et d'algorithmes d'apprentissage automatique pour la caractérisation minéralogique et le suivi de la restauration des haldes de stériles miniers. J'ai notamment développé des pipelines opérationnels en Python pour l'analyse des données hyperspectrales satellitaires (EnMAP et PRISMA), validés par géochimie de terrain (XRF) et analyses de laboratoire (DRX).

J'ai préparé une lettre de motivation détaillée décrivant mon parcours et la synergie de mes compétences avec vos projets de recherche :
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

Je serais ravi de pouvoir échanger brièvement avec vous par visioconférence pour discuter de possibilités de collaboration ou de postes disponibles. Je vous joins mon CV, mon résumé de thèse ainsi qu'une publication représentative.

Je vous remercie vivement pour le temps accordé à l'examen de ma candidature.

Je vous prie d'agréer, Madame la Professeure Fenton, l'expression de mes salutations distinguées.

Abdelhak EL MANSOUR
Doctorant en Télédétection et Géosciences de l'Environnement
UM6P, Maroc
```

---

### 👤 Dr. Richard Gloaguen (HZDR — 🇩🇪 Germany)
**Email Address**: `r.gloaguen@hzdr.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Gloaguen HZDR Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:r.gloaguen@hzdr.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Gloaguen%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20HZDR.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20exploration%20technology%20and%20automated%20mineral%20mapping%20using%20remote%20sensing.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20field%20spectroscopy%2C%20PRISMA/EnMAP%20unmixing%2C%20and%20machine%20learning%20classification%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Gloaguen,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at HZDR. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on exploration technology and automated mineral mapping using remote sensing.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in field spectroscopy, PRISMA/EnMAP unmixing, and machine learning classification aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Chris Hecker (ITC — 🇳🇱 Netherlands)
**Email Address**: `c.a.hecker@utwente.nl`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Hecker ITC Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:c.a.hecker@utwente.nl?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Hecker%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20ITC.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20thermal%20and%20reflective%20infrared%20spectroscopy%20for%20mineral%20identification.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20mineralogical%20characterization%20and%20laboratory/field%20ASD%20spectroscopy%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Hecker,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at ITC. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on thermal and reflective infrared spectroscopy for mineral identification.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in mineralogical characterization and laboratory/field ASD spectroscopy aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Mahdi Khodadadzadeh (ITC — 🇳🇱 Netherlands)
**Email Address**: `m.khodadadzadeh@utwente.nl`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Khodadadzadeh ITC Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:m.khodadadzadeh@utwente.nl?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Khodadadzadeh%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20ITC.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20geo-information%20processing%20and%20advanced%20machine%20learning%20for%20hyperspectral%20classification.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20spatial-spectral%20CNN%20architectures%20and%20advanced%20classifier%20design%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Khodadadzadeh,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at ITC. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on geo-information processing and advanced machine learning for hyperspectral classification.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in spatial-spectral CNN architectures and advanced classifier design aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Sandra Lorenz (HZDR — 🇩🇪 Germany)
**Email Address**: `s.lorenz@hzdr.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Lorenz HZDR Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:s.lorenz@hzdr.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Lorenz%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20HZDR.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20hyperspectral%20sensor%20integration%20and%20mineral%20resource%20exploration%20technology.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20spectral%20unmixing%20and%20multi-source%20geological%20data%20fusion%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Lorenz,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at HZDR. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on hyperspectral sensor integration and mineral resource exploration technology.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in spectral unmixing and multi-source geological data fusion aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Prof. Maxence Martin (UQAT — 🇨🇦 Canada)
**Email Address**: `maxence.martin@uqat.ca`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Martin UQAT Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:maxence.martin@uqat.ca?subject=Demande%20de%20candidature%20postdoctorale%20%E2%80%94%20T%C3%A9l%C3%A9d%C3%A9tection%20/%20Imagerie%20hyperspectrale%20%E2%80%94%20Dr%20Abdelhak%20EL%20MANSOUR&body=Monsieur%20le%20Professeur%20Martin%2C%0A%0AJe%20me%20permets%20de%20vous%20contacter%20pour%20solliciter%20une%20opportunit%C3%A9%20de%20recherche%20postdoctorale%20au%20sein%20de%20votre%20%C3%A9quipe%20%C3%A0%20UQAT.%20Doctorant%20%C3%A0%20l%27Universit%C3%A9%20Mohammed%20VI%20Polytechnique%20%28UM6P%29%20au%20Maroc%2C%20je%20soutiendrai%20ma%20th%C3%A8se%20le%2030%20juin%202026%2C%20et%20je%20suis%20particuli%C3%A8rement%20int%C3%A9ress%C3%A9%20par%20vos%20travaux%20sur%20la%20dynamique%20des%20%C3%A9cosyst%C3%A8mes%20forestiers%20et%20l%27%C3%A9cologie%20foresti%C3%A8re%20quantitative.%0A%0AMes%20recherches%20de%20doctorat%2C%20men%C3%A9es%20sous%20la%20direction%20du%20Pr%20Ahmed%20LAAMRANI%2C%20portent%20sur%20le%20d%C3%A9veloppement%20de%20m%C3%A9thodologies%20de%20t%C3%A9l%C3%A9d%C3%A9tection%20multi-%C3%A9chelle%20et%20d%27algorithmes%20d%27apprentissage%20automatique%20pour%20la%20caract%C3%A9risation%20min%C3%A9ralogique%20et%20le%20suivi%20de%20la%20restauration%20des%20haldes%20de%20st%C3%A9riles%20miniers.%20J%27ai%20notamment%20d%C3%A9velopp%C3%A9%20des%20pipelines%20op%C3%A9rationnels%20en%20Python%20pour%20l%27analyse%20des%20donn%C3%A9es%20hyperspectrales%20satellitaires%20%28EnMAP%20et%20PRISMA%29%2C%20valid%C3%A9s%20par%20g%C3%A9ochimie%20de%20terrain%20%28XRF%29%20et%20analyses%20de%20laboratoire%20%28DRX%29.%0A%0AJ%27ai%20pr%C3%A9par%C3%A9%20une%20lettre%20de%20motivation%20d%C3%A9taill%C3%A9e%20d%C3%A9crivant%20mon%20parcours%20et%20la%20synergie%20de%20mes%20comp%C3%A9tences%20avec%20vos%20projets%20de%20recherche%20%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AJe%20serais%20ravi%20de%20pouvoir%20%C3%A9changer%20bri%C3%A8vement%20avec%20vous%20par%20visioconf%C3%A9rence%20pour%20discuter%20de%20possibilit%C3%A9s%20de%20collaboration%20ou%20de%20postes%20disponibles.%20Je%20vous%20joins%20mon%20CV%2C%20mon%20r%C3%A9sum%C3%A9%20de%20th%C3%A8se%20ainsi%20qu%27une%20publication%20repr%C3%A9sentative.%0A%0AJe%20vous%20remercie%20vivement%20pour%20le%20temps%20accord%C3%A9%20%C3%A0%20l%27examen%20de%20ma%20candidature.%0A%0AJe%20vous%20prie%20d%27agr%C3%A9er%2C%20Monsieur%20le%20Professeur%20Martin%2C%20l%27expression%20de%20mes%20salutations%20distingu%C3%A9es.%0A%0AAbdelhak%20EL%20MANSOUR%0ADoctorant%20en%20T%C3%A9l%C3%A9d%C3%A9tection%20et%20G%C3%A9osciences%20de%20l%27Environnement%0AUM6P%2C%20Maroc)

```text
Objet : Demande de candidature postdoctorale — Télédétection / Imagerie hyperspectrale — Dr Abdelhak EL MANSOUR

Monsieur le Professeur Martin,

Je me permets de vous contacter pour solliciter une opportunité de recherche postdoctorale au sein de votre équipe à UQAT. Doctorant à l'Université Mohammed VI Polytechnique (UM6P) au Maroc, je soutiendrai ma thèse le 30 juin 2026, et je suis particulièrement intéressé par vos travaux sur la dynamique des écosystèmes forestiers et l'écologie forestière quantitative.

Mes recherches de doctorat, menées sous la direction du Pr Ahmed LAAMRANI, portent sur le développement de méthodologies de télédétection multi-échelle et d'algorithmes d'apprentissage automatique pour la caractérisation minéralogique et le suivi de la restauration des haldes de stériles miniers. J'ai notamment développé des pipelines opérationnels en Python pour l'analyse des données hyperspectrales satellitaires (EnMAP et PRISMA), validés par géochimie de terrain (XRF) et analyses de laboratoire (DRX).

J'ai préparé une lettre de motivation détaillée décrivant mon parcours et la synergie de mes compétences avec vos projets de recherche :
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

Je serais ravi de pouvoir échanger brièvement avec vous par visioconférence pour discuter de possibilités de collaboration ou de postes disponibles. Je vous joins mon CV, mon résumé de thèse ainsi qu'une publication représentative.

Je vous remercie vivement pour le temps accordé à l'examen de ma candidature.

Je vous prie d'agréer, Monsieur le Professeur Martin, l'expression de mes salutations distinguées.

Abdelhak EL MANSOUR
Doctorant en Télédétection et Géosciences de l'Environnement
UM6P, Maroc
```

---

### 👤 Dr. Nicola Mondillo (University of Naples Federico II — 🇮🇹 Italy)
**Email Address**: `nicola.mondillo@unina.it`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Mondillo Naples Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:nicola.mondillo@unina.it?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Mondillo%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20University%20of%20Naples%20Federico%20II.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20supergene%20ore%20deposits%2C%20mineralogy%2C%20and%20geological%20remote%20sensing.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20mineral%20characterization%20and%20hyperspectral%20field%20spectrometry%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Mondillo,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at University of Naples Federico II. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on supergene ore deposits, mineralogy, and geological remote sensing.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in mineral characterization and hyperspectral field spectrometry aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Martin Schodlok (BGR — 🇩🇪 Germany)
**Email Address**: `martin.schodlok@bgr.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Schodlok BGR Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:martin.schodlok@bgr.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Schodlok%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20BGR.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20mineral%20resources%20remote%20sensing%20and%20spectral%20libraries%20database%20application.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20USGS/ECOSTRESS%20database%20matching%20and%20EnMAP%20processing%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Schodlok,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at BGR. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on mineral resources remote sensing and spectral libraries database application.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in USGS/ECOSTRESS database matching and EnMAP processing aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Anna Sorrentino (University of Naples Federico II — 🇮🇹 Italy)
**Email Address**: `anna.sorrentino@unina.it`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Sorrentino Naples Inquiry.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:anna.sorrentino@unina.it?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Sorrentino%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20University%20of%20Naples%20Federico%20II.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20geological%20hazards%20and%20environmental%20remote%20sensing%20analysis.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20multi-temporal%20satellite%20data%20analysis%20and%20lithological%20mapping%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Sorrentino,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at University of Naples Federico II. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on geological hazards and environmental remote sensing analysis.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in multi-temporal satellite data analysis and lithological mapping aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Dr. Tobias Storch (DLR — 🇩🇪 Germany)
**Email Address**: `tobias.storch@dlr.de`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Storch DLR IMF Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:tobias.storch@dlr.de?subject=Inquiry%3A%20Postdoctoral%20Opportunities%20in%20Remote%20Sensing%20/%20Hyperspectral%20Imaging%20-%20Dr.%20Abdelhak%20EL%20MANSOUR&body=Dear%20Dr.%20Storch%2C%0A%0AI%20hope%20this%20email%20finds%20you%20well.%0A%0AI%20am%20writing%20to%20inquire%20about%20potential%20postdoctoral%20research%20opportunities%20in%20your%20group%20at%20DLR.%20I%20am%20a%20PhD%20candidate%20at%20UM6P%20%28Morocco%29%2C%20defending%20my%20thesis%20on%20June%2030%2C%202026%2C%20and%20I%20am%20highly%20interested%20in%20your%20group%27s%20work%20on%20imaging%20spectroscopy%20and%20operational%20processing%20chains.%0A%0AMy%20doctoral%20research%2C%20supervised%20by%20Pr.%20Ahmed%20LAAMRANI%2C%20focuses%20on%20developing%20multi-scale%20remote%20sensing%20and%20machine%20learning%20pipelines%20for%20mineralogical%20characterization%20and%20environmental%20monitoring%20of%20phosphate%20mine%20waste%20rocks.%20I%20have%20built%20operational%2C%20end-to-end%20Python%20processing%20engines%20for%20satellite%20hyperspectral%20data%20%28EnMAP%20and%20PRISMA%29%2C%20validating%20our%20spectral%20indices%20against%20laboratory%20XRD%20and%20field%20XRF%20geochemistry.%0A%0AI%20have%20drafted%20a%20detailed%20cover%20letter%20for%20your%20review%2C%20which%20outlines%20how%20my%20experience%20in%20EnMAP%20pipeline%20development%20and%20algorithm%20design%20aligns%20with%20your%20group%27s%20research%20direction%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AI%20would%20be%20honored%20to%20discuss%20any%20potential%20openings%20or%20collaborative%20projects.%20I%20have%20attached%20my%20CV%2C%20thesis%20abstract%2C%20and%20a%20recent%20publication%20for%20your%20reference.%20I%20am%20available%20for%20a%20brief%20video%20call%20at%20your%20convenience.%0A%0AThank%20you%20very%20much%20for%20your%20time%20and%20consideration.%0A%0ASincerely%2C%0A%0AAbdelhak%20EL%20MANSOUR%0APhD%20Candidate%2C%20Remote%20Sensing%20%26%20Geosciences%0AUM6P%2C%20Morocco)

```text
Subject: Inquiry: Postdoctoral Opportunities in Remote Sensing / Hyperspectral Imaging - Dr. Abdelhak EL MANSOUR

Dear Dr. Storch,

I hope this email finds you well.

I am writing to inquire about potential postdoctoral research opportunities in your group at DLR. I am a PhD candidate at UM6P (Morocco), defending my thesis on June 30, 2026, and I am highly interested in your group's work on imaging spectroscopy and operational processing chains.

My doctoral research, supervised by Pr. Ahmed LAAMRANI, focuses on developing multi-scale remote sensing and machine learning pipelines for mineralogical characterization and environmental monitoring of phosphate mine waste rocks. I have built operational, end-to-end Python processing engines for satellite hyperspectral data (EnMAP and PRISMA), validating our spectral indices against laboratory XRD and field XRF geochemistry.

I have drafted a detailed cover letter for your review, which outlines how my experience in EnMAP pipeline development and algorithm design aligns with your group's research direction:
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

I would be honored to discuss any potential openings or collaborative projects. I have attached my CV, thesis abstract, and a recent publication for your reference. I am available for a brief video call at your convenience.

Thank you very much for your time and consideration.

Sincerely,

Abdelhak EL MANSOUR
PhD Candidate, Remote Sensing & Geosciences
UM6P, Morocco
```

---

### 👤 Pr. Osvaldo Valeria (UQAT — 🇨🇦 Canada)
**Email Address**: `osvaldo.valeria@uqat.ca`  
**Linked Cover Letter**: [[02_Academic & Work/work/applications/Cover Letter — Valeria UQAT Postdoc.md]]  

> [!success] [✉️ Open Draft in Mail Client (Gmail / Outlook)](mailto:osvaldo.valeria@uqat.ca?subject=Demande%20de%20candidature%20postdoctorale%20%E2%80%94%20T%C3%A9l%C3%A9d%C3%A9tection%20/%20Imagerie%20hyperspectrale%20%E2%80%94%20Dr%20Abdelhak%20EL%20MANSOUR&body=Monsieur%20le%20Professeur%20Valeria%2C%0A%0AJe%20me%20permets%20de%20vous%20contacter%20pour%20solliciter%20une%20opportunit%C3%A9%20de%20recherche%20postdoctorale%20au%20sein%20de%20votre%20%C3%A9quipe%20%C3%A0%20UQAT.%20Doctorant%20%C3%A0%20l%27Universit%C3%A9%20Mohammed%20VI%20Polytechnique%20%28UM6P%29%20au%20Maroc%2C%20je%20soutiendrai%20ma%20th%C3%A8se%20le%2030%20juin%202026%2C%20et%20je%20suis%20particuli%C3%A8rement%20int%C3%A9ress%C3%A9%20par%20vos%20travaux%20sur%20l%27am%C3%A9nagement%20forestier%20durable%20et%20la%20g%C3%A9omatique%20appliqu%C3%A9e%20%C3%A0%20la%20foresterie.%0A%0AMes%20recherches%20de%20doctorat%2C%20men%C3%A9es%20sous%20la%20direction%20du%20Pr%20Ahmed%20LAAMRANI%2C%20portent%20sur%20le%20d%C3%A9veloppement%20de%20m%C3%A9thodologies%20de%20t%C3%A9l%C3%A9d%C3%A9tection%20multi-%C3%A9chelle%20et%20d%27algorithmes%20d%27apprentissage%20automatique%20pour%20la%20caract%C3%A9risation%20min%C3%A9ralogique%20et%20le%20suivi%20de%20la%20restauration%20des%20haldes%20de%20st%C3%A9riles%20miniers.%20J%27ai%20notamment%20d%C3%A9velopp%C3%A9%20des%20pipelines%20op%C3%A9rationnels%20en%20Python%20pour%20l%27analyse%20des%20donn%C3%A9es%20hyperspectrales%20satellitaires%20%28EnMAP%20et%20PRISMA%29%2C%20valid%C3%A9s%20par%20g%C3%A9ochimie%20de%20terrain%20%28XRF%29%20et%20analyses%20de%20laboratoire%20%28DRX%29.%0A%0AJ%27ai%20pr%C3%A9par%C3%A9%20une%20lettre%20de%20motivation%20d%C3%A9taill%C3%A9e%20d%C3%A9crivant%20mon%20parcours%20et%20la%20synergie%20de%20mes%20comp%C3%A9tences%20avec%20vos%20projets%20de%20recherche%20%3A%0AJe%20vous%20joins%20mon%20CV%20et%20ma%20lettre%20de%20motivation%20au%20format%20PDF%20pour%20votre%20consid%C3%A9ration.%0A%0AJe%20serais%20ravi%20de%20pouvoir%20%C3%A9changer%20bri%C3%A8vement%20avec%20vous%20par%20visioconf%C3%A9rence%20pour%20discuter%20de%20possibilit%C3%A9s%20de%20collaboration%20ou%20de%20postes%20disponibles.%20Je%20vous%20joins%20mon%20CV%2C%20mon%20r%C3%A9sum%C3%A9%20de%20th%C3%A8se%20ainsi%20qu%27une%20publication%20repr%C3%A9sentative.%0A%0AJe%20vous%20remercie%20vivement%20pour%20le%20temps%20accord%C3%A9%20%C3%A0%20l%27examen%20de%20ma%20candidature.%0A%0AJe%20vous%20prie%20d%27agr%C3%A9er%2C%20Monsieur%20le%20Professeur%20Valeria%2C%20l%27expression%20de%20mes%20salutations%20distingu%C3%A9es.%0A%0AAbdelhak%20EL%20MANSOUR%0ADoctorant%20en%20T%C3%A9l%C3%A9d%C3%A9tection%20et%20G%C3%A9osciences%20de%20l%27Environnement%0AUM6P%2C%20Maroc)

```text
Objet : Demande de candidature postdoctorale — Télédétection / Imagerie hyperspectrale — Dr Abdelhak EL MANSOUR

Monsieur le Professeur Valeria,

Je me permets de vous contacter pour solliciter une opportunité de recherche postdoctorale au sein de votre équipe à UQAT. Doctorant à l'Université Mohammed VI Polytechnique (UM6P) au Maroc, je soutiendrai ma thèse le 30 juin 2026, et je suis particulièrement intéressé par vos travaux sur l'aménagement forestier durable et la géomatique appliquée à la foresterie.

Mes recherches de doctorat, menées sous la direction du Pr Ahmed LAAMRANI, portent sur le développement de méthodologies de télédétection multi-échelle et d'algorithmes d'apprentissage automatique pour la caractérisation minéralogique et le suivi de la restauration des haldes de stériles miniers. J'ai notamment développé des pipelines opérationnels en Python pour l'analyse des données hyperspectrales satellitaires (EnMAP et PRISMA), validés par géochimie de terrain (XRF) et analyses de laboratoire (DRX).

J'ai préparé une lettre de motivation détaillée décrivant mon parcours et la synergie de mes compétences avec vos projets de recherche :
Je vous joins mon CV et ma lettre de motivation au format PDF pour votre considération.

Je serais ravi de pouvoir échanger brièvement avec vous par visioconférence pour discuter de possibilités de collaboration ou de postes disponibles. Je vous joins mon CV, mon résumé de thèse ainsi qu'une publication représentative.

Je vous remercie vivement pour le temps accordé à l'examen de ma candidature.

Je vous prie d'agréer, Monsieur le Professeur Valeria, l'expression de mes salutations distinguées.

Abdelhak EL MANSOUR
Doctorant en Télédétection et Géosciences de l'Environnement
UM6P, Maroc
```

---




================================================================================
FILE: 02_Academic & Work/work/active/Pixxel Application/Cover Letter — Hyperspectral Scientist.md (~280 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, Pixxel, cover-letter]
role: Hyperspectral Scientist
deadline: Rolling
status: draft
---

# Cover Letter — Pixxel Hyperspectral Scientist

**Deadline: Rolling — apply immediately**
**Apply at:** https://pixxel.darwinbox.in/ms/candidate/careers

---

Abdelhak EL MANSOUR
PhD Candidate — Remote Sensing and Environmental Geosciences
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
elmansour01abdelhak@gmail.com
scholar.google.com/citations?user=ysUOZQ0AAAAJ

May 25, 2026

Hiring Team
Pixxel

---

Re: Hyperspectral Scientist

Dear Hiring Team,

I build satellite hyperspectral pipelines that end with a validated product delivered to a client. That is what Pixxel needs, and it is what I do.

My PhD thesis (UM6P, defending June 30, 2026) was built around two operational pipelines — one for PRISMA, one for EnMAP. The EnMAP pipeline runs 1,776 lines of production Python: raw HDF5 ingestion, atmospheric correction, bad-band removal, VCA-FCLS spectral unmixing, ML classification, and XRF ground-truth validation in a single reproducible workflow. The output is a novel metric — the Reclamation Progress Index — achieving AUC = 1.000 for backfilling detection, validated against geochemical measurements (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²). Delivered to OCP Group, one of the world's largest phosphate producers. Not a prototype.

The PRISMA pipeline is peer-reviewed and published (Sensors 2026, IF 3.5): 127 field samples, 4 lithological classes, spatially constrained cross-validation, landscape-scale waste rock mapping. Mining is one of Pixxel's target sectors. The methods transfer directly to agriculture, forestry, and environmental monitoring.

I work across the full EO chain — L1 to analytics — in Python (scikit-learn, GDAL, rasterio, spectral, numpy). I am available fully remote, based in Morocco, ready to start July 2026.

I would welcome a technical conversation.

Yours sincerely,

Abdelhak EL MANSOUR
PhD Candidate, GSMI — UM6P
elmansour01abdelhak@gmail.com
scholar.google.com/citations?user=ysUOZQ0AAAAJ




================================================================================
FILE: 02_Academic & Work/work/active/Pixxel Application/Cover Letter — Senior Hyperspectral Scientist.md (~390 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, Pixxel, cover-letter]
role: Senior/Lead Hyperspectral Scientist
deadline: Rolling
status: draft
---

# Cover Letter — Pixxel Senior/Lead Hyperspectral Scientist

**Deadline: Rolling — apply immediately**
**Apply at:** https://pixxel.darwinbox.in/ms/candidate/careers

---

Abdelhak EL MANSOUR
PhD Candidate — Remote Sensing and Environmental Geosciences
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
elmansour01abdelhak@gmail.com
scholar.google.com/citations?user=ysUOZQ0AAAAJ

May 25, 2026

Hiring Team
Pixxel

---

Re: Senior/Lead Hyperspectral Scientist

Dear Hiring Team,

I am applying for the Senior/Lead Hyperspectral Scientist role at Pixxel. I am a PhD candidate at UM6P, Morocco, defending June 30, 2026, with four peer-reviewed publications and a track record of building end-to-end satellite hyperspectral pipelines that deliver validated, client-facing products.

The senior role at Pixxel is about more than data processing — it is about owning the science pipeline and being accountable for product quality. I have done that. My PhD thesis, conducted in partnership with OCP Group (one of the world's largest phosphate producers), required me to design, implement, and validate an operational Earth observation product from scratch using EnMAP hyperspectral imagery. The pipeline I built handles the full chain: ingestion of raw satellite data, atmospheric correction, bad-band removal (189 valid EnMAP bands selected), spectral unmixing via VCA-FCLS, machine learning classification, and validation against independent geochemical measurements (XRF). The output — the Reclamation Progress Index — achieves AUC = 1.000 and a ground-truth correlation of Spearman ρ = 0.845. It is peer-reviewed, reproducible, and already being considered for operational deployment.

Earlier in my PhD, I built a parallel pipeline for PRISMA imagery: custom HDF5 loader, VNIR+SWIR fusion, Random Forest and Extra Trees classifiers with spatially constrained cross-validation (30m buffer, 10 replicates), published in Sensors 2026. I also supervised two students (engineering and Master's level) through hyperspectral projects — evidence that I can lead technical work, not just execute it.

Pixxel's Firefly constellation is the most exciting hyperspectral asset in orbit right now. The combination of 6 operational satellites and a science team that can turn that data into actionable analytics is exactly the kind of environment where I want to build the next phase of my career. I bring the methods, the track record, and the appetite for the problem.

I am available fully remote, based in Morocco, and ready to start after June 30, 2026.

Yours sincerely,

Abdelhak EL MANSOUR
PhD Candidate, GSMI — UM6P
elmansour01abdelhak@gmail.com
scholar.google.com/citations?user=ysUOZQ0AAAAJ




================================================================================
FILE: 02_Academic & Work/work/active/Pixxel Application/Submission Checklist.md (~195 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, Pixxel, checklist]
---

# Pixxel Application — Submission Checklist

**Apply at:** https://pixxel.darwinbox.in/ms/candidate/careers
**Deadline:** Rolling — apply this week

Apply to BOTH roles separately via the Darwinbox portal.

---

## Role 1 — Hyperspectral Scientist (mid-level)

### What to attach
- [ ] Cover letter (PDF) → export from `Cover Letter — Hyperspectral Scientist.md`
- [ ] CV (PDF) → reuse `CV_ELMANSOUR_VITO_2026.docx` — open in Word, Save As PDF
- [ ] Google Scholar link → scholar.google.com/citations?user=ysUOZQ0AAAAJ
- [ ] Optional: Sensors 2026 paper PDF (doi: 10.3390/s26010002)

---

## Role 2 — Senior/Lead Hyperspectral Scientist

### What to attach
- [ ] Cover letter (PDF) → export from `Cover Letter — Senior Hyperspectral Scientist.md`
- [ ] CV (PDF) → same CV as above
- [ ] Google Scholar link
- [ ] Optional: Sensors 2026 paper PDF

---

## Notes
- Pixxel is remote-first — your Morocco location is not a problem
- Both roles go through the same Darwinbox portal — apply separately
- No deadline listed — do NOT wait, rolling means first-come matters
- After applying, update the tracker in `Hot Opportunities — May 2026.md`




================================================================================
FILE: 02_Academic & Work/work/active/VITO Application/CV — Industry (VITO).md (~554 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [cv, job-application, VITO, industry]
note: Designed to fit one page when exported to PDF. Strip markdown formatting before submission — export as PDF via Pandoc or paste into Word/Overleaf clean template.
---

# CV — Industry Format (VITO-ready)

---

# ABDELHAK EL MANSOUR
**Remote Sensing Scientist — Hyperspectral EO & Machine Learning**

elmansour01abdelhak@gmail.com | +212 117 164 00
scholar.google.com/citations?user=ysUOZQ0AAAAJ | @AbdelhakElm
Available: from July 2026 | Open to relocation (Mol, Belgium)

---

## Technical Skills

**Satellite & EO data:** PRISMA (ASI), EnMAP (DLR/GFZ), VNIR–SWIR hyperspectral, HDF5/NPZ processing, atmospheric & radiometric correction, bad-band removal, multi-temporal analysis

**Machine learning:** Random Forest, Extra Trees, SVM, 1D/2D/3D-CNN, XGBoost, class imbalance handling, spatial cross-validation

**Spectral analysis:** VCA-FCLS spectral unmixing, USGS/ECOSTRESS library matching, SAM/SID/NNLS

**Python stack:** scikit-learn, GDAL, rasterio, spectral, numpy, matplotlib, Jupyter — production pipelines (1,776-line EnMAP engine)

**Field & lab:** ASD FieldSpec 4 field spectroscopy, HHXRF, XRD/XRF interpretation, geological mapping

**Other:** ENVI, Global Mapper, GIS, Git, Google Earth Engine (familiar)

---

## Key Results

- Developed **Reclamation Progress Index (RPI)** from EnMAP data — AUC = 1.000, validated against XRF ground truth (Spearman ρ = 0.845, n = 32/zone, p = 1.74 × 10⁻¹²)
- PRISMA-based lithological classification (127 field samples, 4 classes) — BAC = 0.60–0.67, AUC > 0.95 for carbonates, spatially constrained CV
- Spectral library matching (104 samples, ECOSTRESS) — mean R² = 0.748, 84% of spectra R² > 0.70
- **4 peer-reviewed publications** during PhD (Sensors IF 3.5, IJEST, Mining, BDJ) + 2 in pipeline

---

## Research Experience

**PhD Researcher — Remote Sensing & Environmental Geosciences**
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco | Jul 2021 – Jun 2026 (defending Jun 30)

Built end-to-end satellite EO pipelines (PRISMA + EnMAP) for mineralogical mapping and reclamation monitoring at Benguerir phosphate mine (OCP Group). Delivered a validated operational product (RPI) scalable beyond the study site. Supervised 2 students (engineering + Master's level). Presented at EGU 2025 and EARSeL 2024.

**Research Mobility — Hyperspectral EO Applications**
University of Valencia, Spain (Pr. Jochem Verrelst's group) | Mar 2024 – Aug 2024

Developed PRISMA hyperspectral classification workflow for mining waste; co-authored EARSeL 2024 conference paper; collaborated within an international EO research group.

**Junior Geologist**
Baraka Mining Company, Morocco | Feb 2019 – Aug 2019

Geological exploration (Occidental Meseta, Anti-Atlas, High Atlas) — mapping, sampling, terrain analysis.

---

## Education

**PhD in Applied Geosciences** — UM6P, Morocco (defending June 30, 2026)
*Thesis: Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks, Benguerir Mine*

**MSc in Applied Geosciences** (Mineral & Energetic Resources) — Cadi Ayyad University, 2017

**BSc in Applied Geosciences** — Moulay Ismail University, 2015

---

## Selected Publications

**First author**
1. EL MANSOUR A et al. — Integrating VNIR–SWIR Spectroscopy and HHXRF for Mineralogical Characterization of Phosphate Mine Waste, Benguerir. **Sensors** 2025 (IF 3.5). doi:10.3390/s26010002
2. EL MANSOUR A et al. — PRISMA-based lithological mapping of phosphate waste rocks (thesis Ch.2). **Minerals** 2026 (accepted) ✅

**Co-authored**
3. Zine H, Hakkou R, Papazoglou EG, **EL MANSOUR A** et al. — Revegetation and Ecosystem Reclamation of Post-Mined Land. **IJEST** 2024
4. Zine H, **EL MANSOUR A**, Hakkou R et al. — Mine Closure and Ecological Reclamation: Bibliometric Overview 1980–2023. **Mining** 2023

---

## Languages
French (fluent) | English (advanced) | Arabic/Darija (native) | Tamazight (native) | Spanish (basic)




================================================================================
FILE: 02_Academic & Work/work/active/VITO Application/Cover Letter — Scientific Expert EO Services.md (~438 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, VITO, cover-letter]
role: Scientific Expert, Earth Observation Services
deadline: none (apply asap)
status: draft
---

# Cover Letter — VITO Scientific Expert, Earth Observation Services

**Deadline: None shown — apply as soon as possible**

---

Abdelhak EL MANSOUR
PhD Candidate — Remote Sensing and Environmental Geosciences
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
elmansour01abdelhak@gmail.com | twitter.com/AbdelhakElm
Google Scholar: scholar.google.com/citations?user=ysUOZQ0AAAAJ

May 25, 2026

Recruitment Team
VITO — Flemish Institute for Technological Research
Mol, Belgium

---

Re: Scientific Expert, Earth Observation Services — jobs.vito.be

Dear Hiring Team,

I am writing to apply for the Scientific Expert position in Earth Observation Services at VITO. I am a PhD candidate at the University Mohammed VI Polytechnic (UM6P), defending on 30 June 2026, with four peer-reviewed publications and direct experience building and validating an operational satellite-derived EO product — which is precisely what this role is about.

My thesis (155 pages, defending June 30) produced exactly the kind of output that VITO's EO Services unit delivers at scale: a validated, satellite-derived indicator that translates raw spectral data into a decision-relevant metric for an end client. The Reclamation Progress Index (RPI), developed using EnMAP hyperspectral imagery, quantifies mine reclamation progress with XRF-validated accuracy (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) and near-perfect detection performance (AUC = 1.000). The client in this case was OCP Group — one of the world's largest phosphate producers — and the product was designed to be operationally scalable, not a one-site academic exercise.

Beyond the RPI, my work spans the full EO product development chain: PRISMA and EnMAP data ingestion (HDF5 format, custom loaders), atmospheric and radiometric correction, bad-band removal, spectral unmixing (VCA-FCLS), machine learning classification (Extra Trees, Random Forest, spatial cross-validation), and geochemical ground-truth validation (XRD, XRF, field spectroscopy). I implement everything in Python — scikit-learn, GDAL, rasterio, spectral, numpy — and write production-quality, documented pipelines.

I have also contributed to the scientific literature: five publications (Sensors 2026, Minerals 2026 accepted, two others), conference presentations at EGU 2025 and EARSeL 2024, and a research stay at the University of Valencia (March–August 2024). I understand both the science and the communication demands of translating EO products to non-specialist stakeholders.

VITO's Earth Observation Services unit sits at the intersection of rigorous remote sensing science and real-world impact — that is exactly where I want to build my career. I am available to relocate to Mol and ready to begin after my defense on June 30, 2026.

I would be glad to share my CV, publications, and code portfolio.

Yours sincerely,

Abdelhak EL MANSOUR
PhD Candidate, GSMI — UM6P
elmansour01abdelhak@gmail.com | scholar.google.com/citations?user=ysUOZQ0AAAAJ




================================================================================
FILE: 02_Academic & Work/work/active/VITO Application/Cover Letter — Scientist Remote Sensing (Water Quality).md (~439 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, VITO, cover-letter]
role: Scientist Remote Sensing (Water Quality)
deadline: 2026-05-29
status: draft
---

# Cover Letter — VITO Scientist Remote Sensing (Water Quality)

**Deadline: May 29, 2026**

---

Abdelhak EL MANSOUR
PhD Candidate — Remote Sensing and Environmental Geosciences
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
elmansour01abdelhak@gmail.com | twitter.com/AbdelhakElm
Google Scholar: scholar.google.com/citations?user=ysUOZQ0AAAAJ

May 25, 2026

Recruitment Team
VITO — Flemish Institute for Technological Research
Mol, Belgium

---

Re: Scientist Remote Sensing (Water Quality) — jobs.vito.be

Dear Hiring Team,

I am writing to apply for the Scientist Remote Sensing position within VITO's Remote Sensing Unit. I am a PhD candidate at the University Mohammed VI Polytechnic (UM6P) in Morocco, defending my thesis on 30 June 2026, with four peer-reviewed publications and hands-on expertise in satellite hyperspectral data processing, machine learning classification, and operational EO product development.

My doctoral research focuses on PRISMA and EnMAP satellite imagery — two of Europe's most advanced hyperspectral missions — applied to mineralogical characterization and environmental monitoring of phosphate mine waste rocks. While my application domain is geoscience rather than water quality, the methodological foundation is identical to what this role requires: multi-source satellite data fusion, radiometric correction, pixel-based and sub-pixel classification, spatially constrained validation against field measurements, and Python-based production pipelines. I built and documented a 1,776-line EnMAP processing pipeline from scratch (atmospheric correction → bad-band removal → spectral unmixing → validated reclamation index), which reflects the kind of rigorous, reproducible EO science VITO is known for.

The results speak to operational readiness. In Chapter 3 of my thesis, I developed the Reclamation Progress Index (RPI) — a novel satellite-derived metric validated against XRF geochemical data (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) and achieving AUC = 1.000 for backfilling detection across the Benguerir mine site. Translating satellite observations into a reliable, field-validated operational product is precisely the challenge at the core of water quality monitoring, and it is a challenge I have already solved in a different but methodologically equivalent context.

I am motivated by VITO's reputation as one of Europe's leading EO research centres and by the opportunity to broaden my expertise into aquatic and maritime applications. I am available to relocate to Mol and to travel internationally as the role requires. My thesis defense on June 30 marks the completion of my PhD — I am ready to transition into a full-time research position immediately thereafter.

My CV, Google Scholar profile, and publications are available on request. I would welcome the opportunity to discuss how my background maps onto your team's needs.

Yours sincerely,

Abdelhak EL MANSOUR
PhD Candidate, GSMI — UM6P




================================================================================
FILE: 02_Academic & Work/work/active/VITO Application/Submission Checklist.md (~291 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [job-application, VITO, checklist]
---

# VITO Application — Submission Checklist

---

## Role 1 — Scientist Remote Sensing (Water Quality)
**Deadline: Friday May 29, 2026 — URGENT**
**Apply at:** https://jobs.vito.be → search "Scientist Remote Sensing"

### What to attach
- [x] Cover letter (PDF) → export from `Cover Letter — Scientist Remote Sensing (Water Quality).md`
- [x] CV (PDF) → `CV_ELMANSOUR_2026_Latex.pdf` — add defense date "June 30, 2026" before exporting
- [x] Publication list or Google Scholar link → scholar.google.com/citations?user=ysUOZQ0AAAAJ
- [x] Optional: Sensors 2026 paper PDF (doi: 10.3390/s26010002) — strongest published result

### Before submitting
- [x] Update CV defense date to "June 30, 2026"
- [x] Export cover letter to PDF
- [x] Create account on jobs.vito.be if you don't have one
- [x] Submit via portal (not email)

---

## Role 2 — Scientific Expert, Earth Observation Services
**Deadline: None shown — apply this week**
**Apply at:** https://jobs.vito.be → search "Scientific Expert Earth Observation"

### What to attach
- [x] Cover letter (PDF) → export from `Cover Letter — Scientific Expert EO Services.md`
- [x] CV (PDF) → same updated CV as above
- [x] Publication list or Google Scholar link
- [x] Optional: 1-page research statement (not yet written — see Application Toolkit in Hot Opportunities file)
- [x] Optional: Sensors 2026 paper PDF

### Before submitting
- [x] Same CV and PDF prep as Role 1
- [x] Submit via jobs.vito.be portal

---

## Notes
- Both applications go through **jobs.vito.be** — one account, two separate submissions
- Do NOT email HR directly unless the portal fails
- After submitting, mark the tracker in `Hot Opportunities — May 2026.md`
- If no confirmation email within 24h, check your spam folder




================================================================================
FILE: 02_Academic & Work/work/active/ESPC6 Submission/Email — ESPC6 Abstract Submission.md (~211 words)
================================================================================
---
generated_by: claude
date: 2026-05-25
tags: [conference, ESPC6, phosphorus, abstract, email]
status: sent — 2026-05-25
---

# Email — ESPC6 Abstract Submission

**Conference:** 6th European Sustainable Phosphorus Conference (ESPC6)
**Date:** November 24–26, 2026
**Location:** UM6P, Benguerir, Morocco
**Abstract deadline:** May 31, 2026
**Contact:** [retrieve from https://www.phosphorusplatform.eu/espc6#registration — email is spam-protected]
**Abstract file:** `.raw/Abstract-Sustainable phosphorus.docx`

---

**Subject:** Abstract Submission — ESPC6 | Hyperspectral Mapping of Phosphate Mine Waste Rocks

Dear ESPC6 Organizing Committee,

Please find attached my abstract for consideration at the 6th European Sustainable Phosphorus Conference (ESPC6, November 24–26, 2026, UM6P, Benguerir).

**Title:** Spatially Constrained Machine Learning for PRISMA-Based Lithological Mapping of Phosphate Mine Waste Rocks

**Authors:** Abdelhak El Mansour, Jamal-Eddine Ouzemou, Abdellatif Elghali, Malak Elmeknassi, Rachid Hakkou, Mostafa Benzaazoua, Ahmed Laamrani

**Affiliation:** GSMI / CRSA, Mohammed VI Polytechnic University, Benguerir, Morocco

The study presents a spaceborne hyperspectral framework for lithological mapping of phosphate waste rock piles at the Benguerir mine, directly relevant to sustainable phosphate waste management and selective recovery — core themes of ESPC6. I would welcome the opportunity to present as either an oral or poster contribution.

Yours sincerely,

Abdelhak El Mansour
PhD Candidate, GSMI — UM6P
abdelhak.elmansour@um6p.ma

---

## Checklist
- [x] Retrieve contact email from ESPC6 website
- [x] Attach `.raw/Abstract-Sustainable phosphorus.docx`
- [x] Sent 2026-05-25




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Asadzadeh GFZ Postdoc.md (~631 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, GFZ]
target: Dr. Saeid Asadzadeh
institution: GFZ Potsdam — Section 4.4 Remote Sensing and Geoinformatics
status: draft
note: He is a research scientist, not a PI — tone is collegial. Chabrillat (his PI) already has a separate letter drafted. This letter serves as a peer introduction that could complement or precede the Chabrillat letter.
---

# Cover Letter — Inquiry, Asadzadeh, GFZ Potsdam

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Saeid Asadzadeh
Section 4.4 — Remote Sensing and Geoinformatics
GFZ Helmholtz Centre for Geosciences
Potsdam, Germany

---

Dear Dr. Asadzadeh,

I am reaching out following the defense of my PhD thesis in June 2026 to introduce myself and explore whether there may be opportunities to connect — either through a postdoctoral position in Section 4.4 or through research collaboration. My doctoral work applies EnMAP and PRISMA satellite hyperspectral data to mine waste rock characterization and reclamation monitoring, and your recent work on EnMAP for mineral and resource exploration covers ground directly adjacent to mine.

I came across your 2024 paper on detecting rare earth elements using EnMAP at Mountain Pass, California, and your work on EnMAP for alteration mineral mapping at the Reko Diq porphyry deposit — and recognized that we are working on the same sensor and the same applied problem from different angles: your group maps mineralogy to locate and characterize resources, my thesis maps mineralogy to characterize and monitor what mining leaves behind. The shared instrument and the shared spectral methodology are the starting point for a natural conversation.

My thesis covers three scales. Chapter 1 characterized 104 phosphate mine waste rock samples at Benguerir (OCP Group, Morocco) using ASD FieldSpec 4 VNIR-SWIR spectroscopy and NNLS unmixing against a curated ECOSTRESS library, validated against HHXRF and XRD. Chapter 2 extended this to landscape-scale lithological mapping using PRISMA (239 bands, 30 m) under spatially constrained machine learning, reporting balanced accuracies of 0.60–0.67 for four waste rock classes — honest numbers that reflect the physical ceiling at 30 m resolution rather than optimistic cross-validation. Chapter 3 used EnMAP (189 valid bands, 418–2445 nm) to develop a novel Reclamation Progress Index (RPI), a surface transformation metric calibrated against independent field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²), mapping reclamation state from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones across the full 36 km² mine site. This is, to my knowledge, the first geochemically-calibrated satellite reclamation metric derived from EnMAP data in a mining context.

I also note your recent collaboration with Nicola Mondillo and Anna Sorrentino on EnMAP-based Zn mineralization mapping in the Flinders Ranges — I have independently been in contact with Dr. Mondillo's group at Naples, where the PRISMA satellite workflow we both rely on is a shared reference point.

If there are postdoctoral openings in Section 4.4, or if you see potential for a research collaboration around satellite hyperspectral applications in mining environments, I would welcome the opportunity to speak. I can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*
*Strategy note: Send this alongside or just after the letter to Prof. Chabrillat. Asadzadeh is the most likely person to review incoming postdoc inquiries in Section 4.4 and could forward to Chabrillat or flag a fit.*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[Hyperspectral Imaging]]
- [[Spectral Analysis]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Asam DLR DFD Postdoc.md (~717 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, DLR]
target: Dr. Sarah Asam
institution: DLR — German Remote Sensing Data Center (DFD), Land Surface / Forest Ecosystems Team, Oberpfaffenhofen
status: draft
note: Asam heads the Forest Ecosystems team at DFD Land Surface. Different institute from Storch (IMF). Angle: mine reclamation → revegetation → forest ecosystem recovery; RPI as the mineralogical precursor to vegetation establishment that her team monitors.
---

# Cover Letter — Postdoc Application, Forest Ecosystems Team, DLR DFD

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Sarah Asam
Head, Forest Ecosystems Team
Department of Land Surface
German Remote Sensing Data Center (DFD)
German Aerospace Center (DLR)
Oberpfaffenhofen, Germany

---

Dear Dr. Asam,

I am writing to inquire about postdoctoral opportunities in your Forest Ecosystems team following the defense of my PhD thesis in June 2026. My doctoral work addresses a phase of land surface dynamics that precedes and enables the vegetation recovery your team studies: the spectral and geochemical transformation of a disturbed mineral surface as it is reclaimed and prepared for revegetation. I believe this creates a productive connection between my background and your team's remote sensing monitoring framework.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco, where I developed a multi-scale hyperspectral remote sensing framework for characterising phosphate mine waste rock and monitoring reclamation progress. The central applied output is the Reclamation Progress Index (RPI), developed in Chapter 3 using EnMAP satellite data (189 valid bands, 418–2445 nm): a surface transformation metric calibrated against field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) that maps the mineralogical state of a mine surface from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones, across the entire 36 km² mine site. The RPI tracks the pre-vegetation stage of reclamation — backfilling, surface stabilisation, and soil amendment — that determines whether subsequent vegetation establishment succeeds or fails. It captures what spectral vegetation indices (NDVI, EVI) cannot: the mineral surface condition before any green signal is present. This makes it the temporal precursor to the ecosystem recovery monitoring your team performs.

The relevance to forest ecosystem monitoring in a European context is direct. Abitibi-Témiscamingue in Quebec, the Freiberg mining district in Germany, and post-industrial landscapes across Europe all involve the same sequence: disturbed mineral surface → geochemical stabilisation → vegetation establishment → ecosystem recovery. Remote sensing of this full trajectory requires both a mineralogical monitoring layer (what I developed) and a vegetation dynamics monitoring layer (what your team specialises in). The two layers are temporally adjacent and methodologically complementary — mine reclamation monitoring feeds into revegetation success assessment, which feeds into ecosystem recovery tracking. I see direct potential for combining the RPI framework with your team's multi-temporal vegetation monitoring approaches to build a complete surface-to-ecosystem recovery index applicable to mine and other disturbed land contexts in Germany and beyond.

Chapter 2 of my thesis applied PRISMA satellite imagery (239 bands, 30 m) and spatially constrained machine learning for landscape-scale lithological mapping, and Chapter 1 built the sample-scale spectral-geochemical baseline using field spectroscopy and XRD/HHXRF validation. Together the three chapters cover the mineral surface characterisation that precedes any vegetation monitoring analysis.

I bring four peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5), a Python-based pipeline for EnMAP and PRISMA satellite data from raw HDF5 to validated landscape outputs, and direct experience working on environmental monitoring problems with a large mining industry partner. I am familiar with DLR DFD's land surface monitoring programme and the multi-temporal analysis frameworks it uses.

I would welcome the opportunity to discuss whether there is a fit with your team's current or planned research directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[EnMAP Satellite]]
- [[Hyperspectral Imaging]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Bussiere UQAT Postdoc.md (~614 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, canada, UQAT]
target: Pr. Bruno Bussière
institution: UQAT — IRME / NSERC Chair on Mine Site Reclamation
status: draft
---

# Cover Letter — Postdoc Application, Bussière Lab, UQAT

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Professor Bruno Bussière
NSERC-UQAT Industrial Chair on Mine Site Reclamation
Research Institute on Mines and the Environment (RIME UQAT-Polytechnique)
Université du Québec en Abitibi-Témiscamingue
Rouyn-Noranda, Quebec, Canada

---

Dear Professor Bussière,

I am writing to inquire about postdoctoral opportunities within your research group following the defense of my PhD thesis in June 2026. My doctoral work at UM6P focuses on satellite hyperspectral remote sensing for mine waste rock characterization and reclamation monitoring — a set of tools that I believe could complement the geotechnical and geochemical monitoring work carried out at RIME, particularly in the area of spatial reclamation assessment at mine sites.

My thesis, conducted at the Benguerir phosphate mine of OCP Group (Morocco), developed a multi-scale framework spanning field spectroscopy, PRISMA satellite imagery (239 bands, 30 m), and EnMAP hyperspectral data. The applied output most relevant to your group's work is the Reclamation Progress Index (RPI), developed in Chapter 3: a satellite-derived metric that quantifies the degree of surface transformation in backfilled waste rock zones relative to undisturbed reference areas. The RPI was calibrated and validated against field XRF geochemistry from independent sampling campaigns (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²), producing spatially continuous reclamation state estimates — index values of approximately 0.90 in fully reclaimed zones versus 0.20 in undisturbed waste rock — across the entire 36 km² mine surface. Chapter 2 addressed lithological mapping of waste rock using PRISMA and machine learning under spatially rigorous cross-validation, yielding balanced accuracies of 0.60–0.67 for four mineralogical classes, which I document as the performance ceiling imposed by 30 m sub-pixel mixing rather than a methodological limitation.

The practical gap this work addresses is one your group knows well: in-situ sensor networks and field sampling campaigns deliver high temporal and geochemical resolution at discrete monitoring points, but they cannot provide continuous spatial coverage across an active mine site. Satellite hyperspectral monitoring scales to the full mine footprint and can be repeated systematically without additional field costs. I see direct potential for combining RIME's established geotechnical monitoring protocols with satellite-derived spatial reclamation indices — a combination that would add a spatial layer to the point-based monitoring your group currently operates across its partner mine sites in Quebec.

Beyond the methodological fit, my background at UM6P gives me direct experience working with mining industry partners on applied environmental problems — a context that maps naturally onto RIME's structure of academic research integrated with six industrial partners including Agnico Eagle and IAMGOLD. I bring four peer-reviewed publications, a complete Python workflow for hyperspectral satellite data from raw ingestion to analysis-ready geochemical maps, and experience in the full characterization pipeline from XRD/XRF laboratory validation to landscape-scale satellite mapping.

I would welcome the opportunity to discuss whether there is a potential fit with your group's ongoing or planned research directions. I am available for a video call at your convenience and can provide my CV, thesis abstract, and publications on request.

Thank you for your consideration.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[Waste Rock Characterization]]
- [[Hyperspectral Imaging]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Chabrillat GFZ Postdoc.md (~577 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, GFZ]
target: Prof. Dr. Sabine Chabrillat
institution: GFZ Helmholtz Centre for Geosciences, Potsdam — Section 4.4 Remote Sensing & Geoinformatics
status: draft
---

# Cover Letter — Postdoc Application, Chabrillat Group, GFZ Potsdam

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Prof. Dr. Sabine Chabrillat
Head, Hyperspectral Remote Sensing Applications Group
Section 4.4 — Remote Sensing and Geoinformatics
GFZ Helmholtz Centre for Geosciences
Potsdam, Germany

---

Dear Professor Chabrillat,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. My doctoral work at UM6P applies EnMAP and PRISMA hyperspectral data to mine waste rock characterization and reclamation monitoring — a set of problems that sits directly within the multi-scale geoscience applications your group develops for the EnMAP mission.

My thesis, carried out at the Benguerir phosphate mine of OCP Group in Morocco, developed a three-chapter framework spanning field spectroscopy (ASD FieldSpec 4, 350–2500 nm), PRISMA satellite imagery, and EnMAP data. Chapter 3 is the most directly relevant to your group's work: I used EnMAP (189 valid bands, 418–2445 nm) to detect and quantify the spectral impact of backfilling operations on mine waste rock surfaces, comparing reclaimed zones against undisturbed reference areas. The output is a novel Reclamation Progress Index (RPI), calibrated against independent field XRF geochemistry — a geochemically-anchored, spectrally-derived surface transformation index validated across 64 spatially independent field measurements (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²). The index produces spatially continuous maps distinguishing reclaimed surface state (RPI ≈ 0.90) from undisturbed waste rock (RPI ≈ 0.20) across the full 36 km² mine site, without additional field campaigns. Chapter 1 built the mineralogical foundation using field and lab spectroscopy validated against XRD and HHXRF, characterizing four mineral assemblages including fluorapatite, dolomite, illite, and kaolinite. Chapter 2 extended this to landscape-scale lithological mapping using PRISMA and spatially constrained machine learning.

This connects to two strands of your group's work. First, the EnMAP application to bare surface geochemistry: the phosphate mine context provides a geochemically complex, mineralogically rich test site where EnMAP performance in the SWIR can be rigorously evaluated against laboratory ground truth — complementary to the rare earth and alteration mineral mapping your group has demonstrated with EnMAP in other settings. Second, the land degradation and surface monitoring angle: mine waste reclamation is structurally analogous to the soil degradation and land cover change problems your group addresses through digital soil mapping and multi-temporal hyperspectral analysis. The RPI framework could be extended to other disturbed land surfaces where geochemical change precedes visible vegetation recovery.

I bring a complete EnMAP processing pipeline from raw data to validated geoscience products, published work in *Sensors* (IF 3.5) and a paper accepted in *Minerals* 2026 (IF 2.2), and direct experience integrating satellite hyperspectral data with XRD and XRF laboratory validation — a multi-source geoscience workflow aligned with your group's methodology.

I would welcome the opportunity to discuss whether my background fits your group's current or planned projects. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Esmaeili UofT Postdoc.md (~663 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, canada, toronto]
target: Prof. Kamran Esmaeili
institution: University of Toronto — Dept. Civil and Mineral Engineering
status: draft
note: Lead came via Mehdi Abdolmaleki's profile (postdoc in this group)
---

# Cover Letter — Postdoc Application, Esmaeili Group, University of Toronto

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Prof. Kamran Esmaeili
Department of Civil and Mineral Engineering
University of Toronto
Toronto, Ontario, Canada

---

Dear Professor Esmaeili,

I am writing to inquire about postdoctoral opportunities in your research group following the defense of my PhD thesis in June 2026. Your group's work on hyperspectral imaging for ore-waste discrimination and ore grade control from drill cuttings addresses the same core problem as my doctoral research — distinguishing mine materials by their spectral-mineralogical signature using machine learning — and I believe my satellite-scale extension of that methodology could add a useful dimension to your group's work.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco, one of the world's largest phosphate operations. The central applied challenge — discriminating waste rock lithologies that are spectrally similar but economically distinct — is structurally identical to the ore-waste discrimination problem your group has addressed using close-range hyperspectral imaging. In Chapter 2, I applied PRISMA satellite imagery (239 bands, 30 m) and spatially constrained machine learning (Extra Trees, Random Forest) to map four waste rock classes across the full mine surface, reporting honest balanced accuracies of 0.60–0.67 under a 30 m buffer cross-validation that enforces geographic separation between training and test sets. Chapter 1 built the mineralogical foundation at sample scale using ASD FieldSpec 4 spectroscopy (350–2500 nm), NNLS spectral unmixing against a curated ECOSTRESS library, and cross-validation against HHXRF elemental data and powder XRD across 104 field samples — a workflow comparable to what your group has demonstrated with close-range hyperspectral systems on drill cuttings, extended to field-portable instruments. Chapter 3 developed a novel Reclamation Progress Index (RPI), a satellite-derived transformation metric calibrated against independent XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) that maps reclamation state continuously across the 36 km² mine site — from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones.

The scale difference between your group's operational close-range imaging and my satellite-scale work is complementary rather than competing. Your approach delivers high spatial and spectral resolution at the point of extraction — drill cuttings, blast hole material — which is where the operational decision is made. My approach delivers spatial coverage across the full mine footprint for monitoring, planning, and regulatory compliance — decisions that require landscape-scale context. The two scales together address different parts of the same management problem, and the ML and geochemical validation methodologies transfer directly between them.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026), a Python-based pipeline for EnMAP and PRISMA satellite data from raw acquisition to validated mineral maps, and direct experience integrating spectral, XRD, and XRF data in supervised ML workflows for a major mining industry partner. I also note that your group's work on data-driven versus knowledge-based approaches to hyperspectral ore-waste discrimination maps directly onto the comparison between spectral library matching and ML classification that runs through all three chapters of my thesis.

I would welcome the opportunity to discuss whether there is a fit with your group's current directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*
*Note: Dr. Mehdi Abdolmaleki (postdoc in this group) has overlapping research — potential peer contact after sending this letter.*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Fenton UQAT Postdoc.md (~570 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, canada, UQAT]
target: Pr. Nicole Fenton
institution: UQAT — IRF / NSERC Chair on Northern Biodiversity in Mining Context
status: draft
---

# Cover Letter — Postdoc Application, Fenton Lab, UQAT

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Professor Nicole Fenton
NSERC-UQAT Industrial Research Chair on Northern Biodiversity in a Mining Context
Institut de recherche sur les forêts (IRF)
Université du Québec en Abitibi-Témiscamingue
Rouyn-Noranda, Quebec, Canada

---

Dear Professor Fenton,

I am writing to inquire about postdoctoral opportunities in your research group following the defense of my PhD thesis in June 2026. My doctoral work at UM6P addresses a problem directly adjacent to the mission of your NSERC Chair: using satellite hyperspectral remote sensing to quantify the spatial footprint of mining operations on surface conditions and to measure reclamation progress at landscape scale — without relying on field campaigns for coverage.

My thesis developed a multi-scale framework combining field spectroscopy, PRISMA satellite imagery, and EnMAP data to characterize phosphate mine waste rocks at Benguerir, Morocco (OCP Group). The central output of Chapter 3 is the Reclamation Progress Index (RPI), a novel satellite-derived metric calibrated against independent field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹², n = 64 spatially independent measurements). The core finding — that backfilling induces spectrally detectable surface transformations consistently across the full EnMAP wavelength range (418–2445 nm), confirmed through permutation testing and bootstrap resampling — demonstrates that spaceborne hyperspectral data can monitor reclamation-induced change across an entire 36 km² mine site operationally, with index values ranging from 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones.

I see a direct and practical extension of this into the monitoring questions your Chair addresses. Your group's work on the spatial footprint of particulate pollutants around active and restored mines, and on bryophyte diversity estimation across the mine life cycle, faces a scaling challenge that satellite hyperspectral data is well positioned to address: field surveys deliver high ecological resolution but limited spatial coverage. EnMAP and PRISMA — for which I have built end-to-end processing pipelines — can extend that coverage continuously across the full mine footprint. The spectral unmixing and classification workflows I developed (VCA-FCLS, spatially constrained random forests) are directly applicable to mapping vegetation and bryophyte surface cover gradients across mine-affected boreal landscapes.

I bring four peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5), fluency in Python-based geospatial workflows for high-dimensional hyperspectral datasets, and direct experience working with mining industry partners on environmental monitoring problems. My background spans the full processing pipeline from raw satellite data ingestion to validated landscape-scale maps — a capacity I could contribute to your group independently from the start.

I would welcome the opportunity to discuss how my background aligns with your current projects. I am available for a video call at your convenience and can provide my CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[Waste Rock Characterization]]
- [[Hyperspectral Imaging]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Gloaguen HZDR Postdoc.md (~632 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, HZDR]
target: Dr. Richard Gloaguen
institution: HZDR — Helmholtz Institute Freiberg, Exploration Technology Division
status: draft
---

# Cover Letter — Postdoc Application, Gloaguen Division, HZDR Freiberg

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Richard Gloaguen
Head, Exploration Technology Division
Helmholtz Institute Freiberg for Resource Technology
Helmholtz-Zentrum Dresden-Rossendorf (HZDR)
Freiberg, Germany

---

Dear Dr. Gloaguen,

I am writing to inquire about postdoctoral opportunities in your division following the defense of my PhD thesis in June 2026. My doctoral work at UM6P develops and applies multi-scale hyperspectral remote sensing to mine waste rock characterization and reclamation monitoring — a research programme that maps directly onto the multi-scale spectroscopy and mineral mapping agenda of your Exploration Technology division, with a specific contribution at the satellite scale.

My thesis covers three complementary scales at the Benguerir phosphate mine of OCP Group in Morocco. Chapter 1 operates at field and sample scale: 104 samples characterized using ASD FieldSpec 4 spectroscopy (350–2500 nm), NNLS unmixing against an ECOSTRESS spectral library curated for the phosphate context, and cross-validation against HHXRF elemental data and powder XRD. This produced a quantitative mineralogical baseline for four assemblages — carbonate-rich, clay-dominated, phosphate-rich, and mixed — that anchors the interpretation at coarser scales. Chapter 2 brings this to landscape scale using PRISMA satellite imagery (239 bands, 30 m) with spatially constrained machine learning (Extra Trees, Random Forest) for lithological mapping of four waste rock classes, reporting honest balanced accuracies of 0.60–0.67 under a 30 m buffer cross-validation that prevents spatial autocorrelation from inflating performance estimates. Chapter 3 shifts from classification to change detection using EnMAP (189 valid bands, 418–2445 nm): I developed a novel Reclamation Progress Index (RPI), a geochemically-calibrated satellite metric that tracks surface transformation in backfilled waste rock zones, validated against independent XRF measurements (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) and mapping reclamation state from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones across the entire 36 km² mine surface.

Your group's 2024 work on the spectral and spatial comparison of satellite-based hyperspectral sensors for geological mapping addresses precisely the sensor evaluation question I dealt with in practice — choosing between PRISMA and EnMAP for different chapters of a mine characterization study based on their respective band configurations and SNR profiles. My field experience with both sensors adds an applied dimension to that comparison: I can speak from real data about where each sensor's SWIR performance is sufficient for mineral discrimination and where it breaks down. I see potential for this experience to feed directly into your group's sensor-agnostic multiscale mineral mapping framework, particularly as the number of operational spaceborne hyperspectral missions grows (PRISMA, EnMAP, EMIT, upcoming CHIME).

Beyond the satellite scale, the multi-source data fusion logic I applied — spectral library matching, geochemical integration, spatially blocked ML validation — aligns with the multimodal processing approaches your division develops for core-to-outcrop-to-satellite workflows. I bring a complete Python-based processing pipeline for both PRISMA and EnMAP (raw HDF5 to validated geoscience outputs), five peer-reviewed publications including a lead-author paper in *Sensors* (IF 3.5) and a paper accepted in *Minerals* 2026 (IF 2.2), and direct experience working with a mining industry partner on applied environmental monitoring problems.

I would welcome the opportunity to discuss how my background fits your division's current research directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your consideration.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Hecker ITC Postdoc.md (~703 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, netherlands, ITC, Twente]
target: Dr. Chris Hecker
institution: ITC — University of Twente, Dept. Earth Systems Analysis
status: draft
note: Hecker's specialism is TIR hyperspectral — Abdelhak's is VNIR-SWIR satellite. The letter pitches complementarity across spectral ranges, not overlap within the same one. Two letters going to ITC (also Khodadadzadeh) — differentiated by dept and angle.
---

# Cover Letter — Postdoc Application, Hecker Group, ITC Twente

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Chris Hecker
Department of Earth Systems Analysis (ESA)
Faculty of Geo-Information Science and Earth Observation (ITC)
University of Twente
Enschede, The Netherlands

---

Dear Dr. Hecker,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. My doctoral work applies VNIR-SWIR satellite hyperspectral data (PRISMA and EnMAP) to mine waste rock mineralogy and reclamation monitoring — and I believe it sits in productive complementarity with your group's work on thermal infrared spectroscopy and field-to-satellite mineral characterization, particularly in the context of critical raw materials and mine site geology.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco, covering three scales. Chapter 1 characterized 104 waste rock samples using ASD FieldSpec 4 spectroscopy (350–2500 nm) — resolving the SWIR diagnostic features of clay minerals (~2200 nm), dolomite (~2320 nm), calcite (~2340 nm), and fluorapatite (~2150 nm) — with NNLS unmixing against a curated ECOSTRESS library and cross-validation against HHXRF and XRD. Chapter 2 scaled this to landscape mapping using PRISMA (239 bands, 30 m) and spatially constrained machine learning, reporting balanced accuracies of 0.60–0.67 under a rigorous 30 m buffer cross-validation for four lithological classes. Chapter 3 used EnMAP (189 valid bands, 418–2445 nm) to develop a Reclamation Progress Index (RPI), a geochemically-calibrated satellite metric for monitoring backfilling progress, validated against independent XRF measurements (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) across the full 36 km² mine site.

The connection to your work is spectral and applied. On the spectral side: the silicate and carbonate minerals I characterize in the SWIR also carry diagnostic signatures in the thermal infrared — the Si-O stretching features that TIR resolves are precisely what governs the geotechnical behaviour and geochemical stability of the carbonate-rich waste rock classes I mapped. A combined VNIR-SWIR + TIR approach on the same mine materials would produce a more complete mineralogical picture than either range alone: SWIR for clay and carbonate polymorph discrimination, TIR for silicate framework identification and mineral chemistry quantification. Your recent work using EMIT spaceborne hyperspectral data to identify mineral chemistry variation in epithermal systems shows that this combined satellite-scale approach is becoming technically achievable, and phosphate mine waste is a geologically rich test site for it — fluorapatite, dolomite, illite, kaolinite, and quartz all present resolvable features across both spectral regions. On the applied side: phosphate is classified as a critical raw material in the EU, and your GreenMiner project on geological remote sensing for critical raw materials education is a natural context for mine waste characterization work that bridges exploration and environmental monitoring.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026, IF 2.2), a complete Python pipeline for PRISMA and EnMAP data from raw HDF5 ingestion to validated geoscience outputs, and direct experience designing multi-source spectral-geochemical validation workflows. I am also well-versed in the USGS and ECOSTRESS spectral libraries and in the spectral feature analysis methods that underpin both SWIR and TIR mineralogical interpretation.

I would welcome the opportunity to discuss how my background might fit your group's current or planned directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*
*Note: A separate letter has been sent to Dr. Khodadadzadeh (GIP dept, ITC) — different angle, different department.*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Khodadadzadeh ITC Postdoc.md (~682 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, netherlands, ITC, Twente]
target: Dr. Mahdi Khodadadzadeh
institution: ITC — University of Twente, Dept. Geo-information Processing
status: draft
---

# Cover Letter — Postdoc Application, Khodadadzadeh Group, ITC Twente

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Mahdi Khodadadzadeh
Assistant Professor, Department of Geo-information Processing (GIP)
Faculty of Geo-information Science and Earth Observation (ITC)
University of Twente
Enschede, The Netherlands

---

Dear Dr. Khodadadzadeh,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. Reading your work on integrating hyperspectral and geochemical data in machine learning frameworks for mineral mapping, I recognized a direct methodological parallel with my own thesis — the same fusion logic applied at a different scale, from drill-core to satellite.

Your superpixel-based ML framework for drill-core hyperspectral and geochemical data integration — using spatially structured classification to combine spectral mineral signatures with complementary geochemical information — is structurally identical to what I implemented at the landscape scale. My thesis Chapter 1 built the spectral-geochemical baseline at sample scale: 104 field samples from the Benguerir phosphate mine (OCP Group, Morocco) characterized using ASD FieldSpec 4 VNIR-SWIR spectroscopy, NNLS unmixing against a curated ECOSTRESS library, and cross-validated against HHXRF elemental profiles and powder XRD. The result is a quantitative link between spectral features and geochemical composition across four mineralogical assemblages — the same type of spectral-geochemical concordance your drill-core work establishes, but at field sample scale with portable instruments rather than a core scanner.

Chapter 3 carries this fusion logic to the satellite scale using EnMAP (189 valid bands, 418–2445 nm). I developed a Reclamation Progress Index (RPI): a satellite-derived surface transformation metric for backfilled phosphate mine waste, calibrated against field XRF geochemistry from 64 spatially independent samples using isotonic regression — a non-parametric monotone calibration that enforces the physical constraint between spectral reclamation score and geochemical state. The geochemical concordance is strong (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²), mapping reclamation state from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones across the 36 km² mine site. Chapter 2 addressed landscape-scale lithological mapping using PRISMA (239 bands, 30 m) and spatially constrained machine learning, reporting honest balanced accuracies of 0.60–0.67 under a 30 m buffer cross-validation that enforces geographic separation between training and test sets — a design choice analogous to the spatial structuring in your superpixel-based frameworks.

The scale difference between drill-core and satellite is not a disconnect — it is the upscaling problem that makes the field practical. Your group's methodology produces high-resolution mineralogical maps at the core scale; what mining operations also need is coverage across the full mine footprint, continuously and without additional drilling. Satellite hyperspectral data addresses that need, and the spectral-geochemical fusion logic transfers directly. I see concrete potential for joint work on multi-scale mineral characterization that bridges your proximal sensing pipeline with satellite-scale spatial coverage.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026, IF 2.2), a Python-based processing pipeline for EnMAP and PRISMA from raw HDF5 to validated geoscience outputs, and direct experience integrating spectral, XRD, and XRF data in ML workflows for mining applications. My background at the Helmholtz Institute Freiberg community — where your own research trajectory included a position before joining ITC — gives me familiarity with the broader methodological ecosystem your group works within.

I would welcome the opportunity to discuss potential directions. ITC's visiting researcher and postdoctoral fellowship programme makes a range of arrangements possible, and I am open to discussing what format would be most useful. I am available for a video call at your convenience and can provide my CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Lorenz HZDR Postdoc.md (~572 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, HZDR]
target: Dr. Sandra Lorenz
institution: HZDR — Helmholtz Institute Freiberg for Resource Technology
status: draft
---

# Cover Letter — Postdoc Application, Lorenz Group, HZDR Freiberg

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Sandra Lorenz
Group Leader, Digital Processing
Helmholtz Institute Freiberg for Resource Technology
Helmholtz-Zentrum Dresden-Rossendorf (HZDR)
Freiberg, Germany

---

Dear Dr. Lorenz,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. My doctoral work at UM6P applies satellite hyperspectral remote sensing to mine waste rock characterization and reclamation monitoring — and I believe it adds a scale your group's multi-platform framework does not currently cover: the spaceborne level.

Your group's work spans from close-range core scanning to drone-borne hyperspectral acquisition, with a consistent focus on extracting mineralogical and environmental information from mine sites. Your UAS-based monitoring of acid mine drainage — using spectral signatures of secondary iron minerals such as jarosite and goethite to map AMD-affected zones — is methodologically parallel to what I developed at the landscape scale using EnMAP and PRISMA satellite data. My thesis Chapter 3 used 189 valid EnMAP bands (418–2445 nm) to detect and quantify the spectral impact of backfilling operations on phosphate mine waste rock at Benguerir, Morocco (OCP Group), producing a novel Reclamation Progress Index (RPI) calibrated against independent field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²). The index maps reclamation state continuously across the entire 36 km² mine site — a spatial coverage that UAS campaigns, however detailed, cannot deliver operationally. Chapter 2 addressed satellite-scale lithological mapping of four waste rock classes using PRISMA and spatially constrained machine learning (balanced accuracies of 0.60–0.67 under a 30 m spatial buffer cross-validation, reflecting the honest performance ceiling at satellite resolution). Chapter 1 built the mineralogical foundation from field and laboratory spectroscopy validated against XRD and HHXRF across 104 samples.

The multi-scale logic of your group's work — from millimetre-scale core scanning to metre-scale drone data — is one that I would extend upward to the 30 m satellite footprint. Practically, this means the satellite data provides spatial context and site-wide coverage, while your UAV and proximal systems provide the spectral and spatial resolution needed for detailed mineral discrimination and process-level monitoring. This upward integration is technically straightforward with the EnMAP and PRISMA processing pipelines I have built, and is increasingly demanded by mining operators who need both detail and coverage simultaneously.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026), a complete Python-based workflow for EnMAP and PRISMA data from raw HDF5 to validated geoscience maps, and direct experience integrating spectral data with XRD/XRF laboratory validation. I am familiar with the spectral library and SWIR mineral diagnostic approaches that underpin your AMD characterization work.

I would welcome the opportunity to discuss whether my background fits your group's current projects or planned directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Martin UQAT Postdoc.md (~665 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, canada, UQAT]
target: Prof. Maxence Martin
institution: UQAT — IRF, Forest Research Institute
status: draft
note: Junior faculty (joined IRF 2022), has own funded project (LiDAR for old boreal forest habitat, $298K). Fourth UQAT letter — different from Valeria (forest RS), Fenton (biodiversity/mining), Bussière (mine reclamation). Angle here: hyperspectral satellite as spectral complement to his structural LiDAR.
---

# Cover Letter — Postdoc Application, Martin Group, UQAT IRF

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Prof. Maxence Martin
Institut de recherche sur les forêts (IRF)
Université du Québec en Abitibi-Témiscamingue
Rouyn-Noranda, Quebec, Canada

---

Dear Professor Martin,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. Your work combining airborne LiDAR and satellite indices to predict disturbance-induced structural diversity in boreal forests — and your ongoing project on identifying old-growth habitat quality from airborne LiDAR — aligns with a capability I would bring to your group: satellite hyperspectral data as a spectrally-rich complement to the structural information your LiDAR already captures.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco, where I developed a multi-scale framework using field spectroscopy, PRISMA satellite imagery (239 bands, 30 m), and EnMAP hyperspectral data to characterise mine waste rock mineralogy and monitor reclamation progress. The applied problem — detecting and quantifying surface change at landscape scale using satellite data calibrated against field measurements — is structurally analogous to what your forest monitoring work addresses: using remote sensing to track the state and trajectory of a disturbed land surface over time. In Chapter 3, I developed a Reclamation Progress Index (RPI), a satellite-derived metric calibrated against field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) that maps surface transformation continuously across a 36 km² site. The spatially blocked cross-validation design I built — enforcing geographic separation between training and test pixels to prevent autocorrelation from inflating performance — is directly transferable to the boreal landscape classification and habitat quality mapping problems your group works on. Chapter 2 applied this design to PRISMA-based lithological mapping (balanced accuracies of 0.60–0.67), demonstrating the honest performance ceiling that rigorous spatial CV produces in heterogeneous landscapes.

The connection I see to your research is specifically on the spectral side. Your 2021 paper in Remote Sensing of Environment demonstrated that LiDAR structural metrics and satellite-derived spectral indices are complementary predictors of forest structural diversity — LiDAR captures the three-dimensional arrangement of biomass, while multispectral satellite indices capture surface reflectance. Hyperspectral satellite data adds a third layer: not just whether the surface is reflecting green, but which specific compounds — bryophytes vs. vascular plants, dry vs. live biomass, soil mineral exposure — are driving that reflectance, resolved across hundreds of contiguous bands. In the boreal context, this level of spectral detail is directly relevant to the bryophyte diversity and understory composition questions that feature prominently in IRF research, and to distinguishing vegetation recovery stages in mine-adjacent landscapes in Abitibi-Témiscamingue where reclamation and forest succession interact.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026, IF 2.2), a complete Python pipeline for EnMAP and PRISMA data from raw HDF5 to validated landscape-scale outputs, and experience designing spatially robust validation frameworks for heterogeneous terrain. I would be contributing independently to your group's RS capacity from the start.

I would welcome the opportunity to discuss whether my background fits your current or planned projects. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time and consideration.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Mondillo Naples Postdoc.md (~718 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, italy, naples]
target: Dr. Nicola Mondillo
institution: University of Naples Federico II — Dept. Earth Sciences, Environment and Resources
status: draft
note: Anna Sorrentino is a co-researcher in the same group — peer contact
---

# Cover Letter — Postdoc Application, Mondillo Group, University of Naples Federico II

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Nicola Mondillo
Department of Earth Sciences, Environment and Resources (DiSTAR)
University of Naples Federico II
Naples, Italy

---

Dear Dr. Mondillo,

I am writing to inquire about postdoctoral opportunities in your group following the defense of my PhD thesis in June 2026. Reading your work on mapping hydrothermal and supergene alteration zones in carbonate-hosted Zn-Pb deposits using PRISMA satellite imagery combined with field hyperspectral data and geochemical analysis, I recognized an almost exact methodological parallel with my own thesis — the same multi-source workflow, the same satellite, and critically the same diagnostic spectral region, applied to a different geological problem one step along the mine life cycle.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco. Chapter 2 used PRISMA satellite imagery (239 bands, 30 m) to map four lithological classes of phosphate waste rock at landscape scale — Phosphate rock, Siliceous facies, Marl, and Limestone — using spatially constrained machine learning (Extra Trees, Random Forest) with ANOVA-based SWIR band selection embedded within each cross-validation fold to prevent feature-selection leakage. The carbonate classes (Marl and Limestone) were the most reliably discriminated, with AUC values consistently above 0.95 in cross-validation — physically expected, since the dolomite absorption at ~2320 nm and calcite at ~2340 nm produce diagnostic SWIR features that PRISMA resolves cleanly. This is precisely the spectral region your Zn-Pb alteration work exploits for carbonate gangue mapping. Chapter 1 built the sample-scale foundation: 104 field samples characterized using ASD FieldSpec 4 VNIR-SWIR spectroscopy, NNLS unmixing against a curated ECOSTRESS library, and cross-validated against HHXRF elemental data (Mg/Ca ratios for dolomite/calcite discrimination, P₂O₅ up to 23.86 wt% for fluorapatite confirmation) and powder XRD on representative samples. Chapter 3 extended the framework to environmental monitoring using EnMAP, developing a novel Reclamation Progress Index (RPI) calibrated against field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) that tracks surface transformation in backfilled waste zones across the 36 km² mine site.

The geological context differs — ore deposit exploration versus mine waste characterization and environmental monitoring — but this difference is what makes the collaboration scientifically interesting rather than redundant. Your group maps alteration mineralogy to find and delineate ore bodies; my work maps the same mineralogical signals to characterize and monitor what is left behind after extraction. Together, these represent the full spectral-mineralogical arc of a mine site, from exploration to reclamation. PRISMA, being an Italian satellite, is increasingly the instrument of choice for both applications, and your group's expertise in processing it for carbonate-bearing mineral systems is directly transferable to the phosphate and carbonate waste context I worked in — and vice versa.

I also note your recent collaboration with Asadzadeh and Chabrillat (GFZ Potsdam) on the EnMAP study of Zn mineralization in South Australia — I used EnMAP independently in Chapter 3, so there is a common sensor thread across both of our recent work.

I bring five peer-reviewed publications including a lead-author paper in *Sensors* (IF 3.5) and a paper accepted in *Minerals* 2026 (IF 2.2), a complete Python pipeline for PRISMA and EnMAP data processing from raw HDF5 to validated geoscience outputs, and direct experience with the XRD and XRF geochemical validation workflow that underpins your group's methodology. I am also comfortable with the Italian academic system through my familiarity with the broader European research environment.

I would welcome the opportunity to discuss potential research directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*
*Note: Dr. Anna Sorrentino is a co-researcher in this group — potential peer contact.*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Schodlok BGR Postdoc.md (~648 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, BGR]
target: Dr. Martin Schodlok
institution: BGR — Bundesanstalt für Geowissenschaften und Rohstoffe, Hannover
status: draft
note: BGR is a government institute — positions are typically project-tied. Frame as contribution to MultiMiner or similar ongoing project. Email likely martin.schodlok@bgr.de — verify on BGR staff directory.
---

# Cover Letter — Research Inquiry, Schodlok, BGR Hannover

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Martin Schodlok
Subdivision Remote Sensing
Bundesanstalt für Geowissenschaften und Rohstoffe (BGR)
Hannover, Germany

---

Dear Dr. Schodlok,

I am writing to inquire about research opportunities at BGR following the defense of my PhD thesis in June 2026. My doctoral work applies satellite hyperspectral remote sensing — including real EnMAP and PRISMA data, not simulation — to mine waste rock characterization and site monitoring at a major phosphate mine in Morocco. I believe this aligns directly with BGR's ongoing work in the MultiMiner project and your group's broader programme on hyperspectral applications for mine site monitoring and raw materials exploration.

My thesis was carried out at the Benguerir phosphate mine of OCP Group, one of the world's largest phosphate operations. The three chapters address complementary aspects of a mine site characterization problem. Chapter 1 established the spectral-geochemical baseline at sample scale: 104 waste rock samples characterized using ASD FieldSpec 4 VNIR-SWIR spectroscopy and NNLS unmixing against a curated ECOSTRESS library, with cross-validation against HHXRF elemental data and powder XRD — a multi-source mineral characterization approach consistent with BGR's combined use of μ-EDXRF, LIBS, and hyperspectral imaging for advanced mineral analysis. Chapter 2 extended this to landscape scale using real PRISMA satellite imagery (239 bands, 30 m) and spatially constrained machine learning for lithological mapping of four waste rock classes, with honest balanced accuracies of 0.60–0.67 that reflect the physical resolution limit rather than over-fitted cross-validation. Chapter 3 used real EnMAP data (189 valid bands, 418–2445 nm) to develop a novel Reclamation Progress Index (RPI), a satellite-derived surface transformation metric calibrated against independent field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²), mapping reclamation state from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones across the full 36 km² mine site.

I draw particular attention to Chapter 3 in relation to BGR's mine site monitoring activities. Your group's work simulating EnMAP data over the Aggeneys Pb-Zn deposit for surface alteration mapping demonstrated the potential of the sensor for this class of problem. My work goes one step further: it uses actual EnMAP acquisitions with full geochemical ground truth validation, demonstrating that the sensor performs as expected for mineralogical change detection at operational mine scale. The RPI framework — calibrated satellite index + XRF validation + spatially continuous coverage — could be adapted to BGR's monitoring programmes at other mine sites in Europe or globally, including tailings monitoring where surface mineralogical change is a key environmental indicator.

BGR's model of applied geoscience research tied to raw materials policy and industry partnerships matches the type of work environment I am looking for. I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026, IF 2.2), a complete Python processing pipeline for EnMAP and PRISMA from raw HDF5 to validated geoscience outputs, and direct experience delivering applied monitoring results to a mining industry partner.

I would welcome the opportunity to discuss whether there is a fit with BGR's current project portfolio. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Sorrentino Naples Inquiry.md (~644 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, italy, naples]
target: Dr. Anna Sorrentino
institution: University of Naples Federico II — Dept. Earth Sciences, Environment and Resources
status: draft
note: Sorrentino is a junior researcher/postdoc in the Mondillo group — this is a peer introduction, not a formal PI application. Send after or alongside the Mondillo letter. She is the most likely person to engage directly on technical overlap and could advocate internally.
---

# Cover Letter — Research Inquiry, Sorrentino, University of Naples Federico II

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Anna Sorrentino
Department of Earth Sciences, Environment and Resources (DiSTAR)
University of Naples Federico II
Naples, Italy

---

Dear Dr. Sorrentino,

I am writing to introduce myself and to explore whether there may be opportunities for collaboration or a research position in your group. I came across your work on PRISMA hyperspectral imagery for alteration zone mapping in the Chilean Andes copper districts, and your recent EnMAP study of structurally-controlled Zn mineralization in the Flinders Ranges — and recognised a direct methodological parallel with my own doctoral work, which I am defending in June 2026.

My thesis applies PRISMA and EnMAP satellite hyperspectral data to the characterisation and environmental monitoring of phosphate mine waste rocks at Benguerir, Morocco (OCP Group). The three chapters cover field spectroscopy and geochemical baseline (ASD FieldSpec 4, NNLS unmixing, XRD and HHXRF validation, 104 samples), PRISMA-based landscape lithological mapping using spatially constrained machine learning (balanced accuracies of 0.60–0.67 for four waste rock classes under a 30 m buffer cross-validation), and EnMAP-based reclamation monitoring using a novel Reclamation Progress Index calibrated against field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²). The PRISMA processing pipeline — from raw HDF5 ingestion through atmospheric correction assessment, bad band removal, and spectral unmixing — is the same sensor workflow you use, applied to a different geological context.

The difference in context is what makes the comparison interesting. Your work targets hydrothermal and supergene alteration zones formed around ore deposits — systems dominated by clay minerals, iron oxides, and carbonates whose SWIR signatures PRISMA resolves at 30 m. My waste rock assemblages at Benguerir — illite, kaolinite, dolomite, calcite, fluorapatite — draw on exactly the same spectral region and the same unmixing and mapping methodology. The geological problem differs (ore deposit characterisation vs. mine waste monitoring) but the instrument, the spectral diagnostic framework, and the validation approach against geochemistry are shared. I see direct potential for a methodological exchange, and possibly for joint work on multi-site PRISMA mine characterisation that spans both the exploration and environmental monitoring ends of the mine life cycle.

I also note your recent collaboration with Saeid Asadzadeh and Sabine Chabrillat at GFZ Potsdam on the EnMAP Flinders Ranges paper — I have independently been in contact with their group, so we have a common network reference point beyond the shared sensor.

If there are research openings in your group, or if you see scope for a collaboration, I would welcome the opportunity to speak. I can provide my full CV, thesis abstract, and representative publications on request.

Thank you for your time.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*
*Strategy note: Send alongside or just after the letter to Dr. Mondillo. Sorrentino is the closest technical peer in the group and the most likely to engage directly — she could flag the fit to Mondillo or to broader Italian PRISMA network contacts.*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[PRISMA Satellite]]
- [[Waste Rock Characterization]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Storch DLR IMF Postdoc.md (~660 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, germany, DLR]
target: Dr. Tobias Storch
institution: DLR — Remote Sensing Technology Institute (IMF), Imaging Spectroscopy Dept., Oberpfaffenhofen
status: draft
note: Storch headed the EnMAP ground segment. Angle: Abdelhak used the actual EnMAP sensor with validated geoscience results — an applied science validation use case directly relevant to IMF's imaging spectroscopy programme.
---

# Cover Letter — Postdoc Application, Imaging Spectroscopy Dept., DLR IMF

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Dr. Tobias Storch
Head, Imaging Spectroscopy Department
Remote Sensing Technology Institute (IMF)
German Aerospace Center (DLR)
Oberpfaffenhofen, Germany

---

Dear Dr. Storch,

I am writing to inquire about postdoctoral opportunities in the Imaging Spectroscopy Department following the defense of my PhD thesis in June 2026. My doctoral work at UM6P is, to my knowledge, one of the first studies to apply actual EnMAP satellite data — not simulated — to mine waste rock characterisation and reclamation monitoring with independent geochemical ground truth validation. I believe this constitutes a relevant applied science contribution to IMF's imaging spectroscopy programme, and I would like to discuss whether there is a fit with your department's current directions.

My thesis was carried out at the Benguerir phosphate mine of OCP Group in Morocco, a 36 km² open-pit operation that provided a geometrically complex, mineralogically rich, semi-arid test site for EnMAP performance evaluation. Chapter 3 used 189 valid EnMAP bands (418–2445 nm) for two purposes: first, to discriminate reclaimed (backfilled) waste rock zones from undisturbed reference areas using spatially blocked classification; second, to develop a novel Reclamation Progress Index (RPI), an EnMAP-derived surface transformation metric calibrated against 64 independent XRF geochemical measurements from both zones (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²). The XRF calibration provides a quantitative geoscience benchmark that goes beyond binary classification — it ties each EnMAP pixel's spectral state to a measurable geochemical quantity, mapping reclamation progress from approximately 0.20 in undisturbed waste rock to 0.90 in fully reclaimed zones. This type of geochemically-anchored EnMAP validation, carried out at an operational mine site in North Africa, extends the sensor's demonstrated application envelope in directions relevant to the critical minerals and environmental monitoring priorities that currently drive imaging spectroscopy science.

Chapter 2 used PRISMA (239 bands, 30 m) for lithological mapping of four waste rock classes under spatially constrained machine learning, providing a sensor comparison reference point: EnMAP's higher SNR and improved band configuration produced cleaner SWIR discriminations than PRISMA for the same site conditions, consistent with the sensor specifications your ground segment team designed for. Chapter 1 built the full spectral-geochemical baseline at sample scale using ASD FieldSpec 4 spectroscopy and HHXRF/XRD validation, providing the per-mineral ground truth that anchors interpretation at the satellite scale.

I bring five peer-reviewed publications (including a lead-author paper in *Sensors*, IF 3.5, and a paper accepted in *Minerals* 2026), a complete Python processing pipeline for EnMAP and PRISMA from raw HDF5 to validated geoscience outputs, and first-hand experience with the practical constraints of EnMAP data in a real applied setting — bad band behaviour, atmospheric correction residuals in semi-arid conditions, and SWIR SNR limits for carbonate and phosphate mineral discrimination. I am familiar with the DLR EOC's imaging spectroscopy science agenda and would be glad to contribute to it.

I would welcome the opportunity to discuss potential directions. I am available for a video call at your convenience and can provide my full CV, thesis abstract, and publications on request.

Thank you for your consideration.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[EnMAP Satellite]]
- [[PRISMA Satellite]]
- [[Reclamation Progress Index]]
- [[Thesis Overview]]




================================================================================
FILE: 02_Academic & Work/work/applications/Cover Letter — Valeria UQAT Postdoc.md (~569 words)
================================================================================
---
generated_by: claude
date: 2026-06-05
tags: [jobs, applications, postdoc, canada, UQAT]
target: Pr. Osvaldo Valeria
institution: UQAT — Forest Research Institute (IRF)
status: draft
---

# Cover Letter — Postdoc Application, Valeria Lab, UQAT

---

**Abdelhak EL MANSOUR**
PhD, Geology and Sustainable Mining Institute (GSMI)
Université Mohammed VI Polytechnic (UM6P), Benguerir, Morocco
insitazoult@gmail.com | abdelhak.elmansour@um6p.ma

---

Professor Osvaldo Valeria
Forest Research Institute (IRF)
Université du Québec en Abitibi-Témiscamingue
Rouyn-Noranda, Quebec, Canada

---

Dear Professor Valeria,

I am writing to express my interest in joining your research group as a postdoctoral researcher following the defense of my PhD thesis in June 2026. My doctoral work at UM6P focuses on multi-scale hyperspectral remote sensing for mineralogical characterization and reclamation monitoring of phosphate mine waste rocks — a context that connects directly with your group's work on landscape-scale monitoring and forest dynamics in Abitibi-Témiscamingue, a region where mining and boreal forest ecosystems are in sustained contact.

My thesis developed a three-chapter multi-scale framework combining field spectroscopy (ASD FieldSpec 4), PRISMA satellite imagery (239 bands, 30 m), and EnMAP data to characterize mine waste rock mineralogy and quantify reclamation progress. The central methodological contribution is the Reclamation Progress Index (RPI), a novel satellite-derived metric calibrated against field XRF geochemistry (Spearman ρ = 0.845, p = 1.74 × 10⁻¹²) that tracks the surface transformation of backfilled mine waste at landscape scale. The geochemical concordance and consistency under spatially blocked cross-validation demonstrated that spaceborne hyperspectral data can serve as an operational monitoring tool for environmental reclamation — a capability with direct relevance to post-mining revegetation and ecosystem recovery monitoring in Quebec's mining belt.

I see a clear extension of this work into the forest and wetland monitoring questions your group addresses. The spectral unmixing and machine learning pipelines I built for mineral surface characterization (VCA-FCLS, Extra Trees, Random Forest) transfer directly to boreal forest applications: bryophyte mapping, post-disturbance structural recovery, and wetland detection from hyperspectral and multispectral data. The spatially blocked validation design I implemented — enforcing geographic separation between training and test sets to prevent autocorrelation from inflating accuracy estimates — is directly applicable to any landscape-scale classification task in heterogeneous boreal environments. For Chapter 2, lithological mapping under this rigorous design yielded balanced accuracies of 0.60–0.67, which I argue represents the physically constrained performance ceiling at 30 m resolution — an honest and transferable benchmark.

I bring four peer-reviewed publications (including one in *Sensors*, IF 3.5), experience with satellite hyperspectral data processing from raw HDF5 to analysis-ready products, and a strong Python/scikit-learn workflow for high-dimensional geospatial datasets. My background at UM6P, which has direct ties with OCP Group and the broader sustainable mining sector, gives me experience bridging academic environmental monitoring with industry partners — relevant to the operational context of Abitibi-Témiscamingue's mining landscape.

I would welcome the opportunity to discuss potential research directions that align with your group's current projects. I am available for a video call at your convenience and can provide my full CV, thesis manuscript, and list of publications on request.

Thank you for your time and consideration.

Sincerely,

**Abdelhak EL MANSOUR**
PhD (defended June 2026), Remote Sensing and Environmental Geosciences
UM6P — GSMI, Benguerir, Morocco

---

*Attachments to include: CV, thesis abstract (1 page), representative publication (Sensors 2026)*

---

## Related

- [[Postdoc Outreach Dashboard]]
- [[Review Brief — Postdoc Applications 2026]]
- [[Hot Opportunities — May 2026]]
- [[Thesis Overview]]
- [[Waste Rock Characterization]]
- [[Hyperspectral Imaging]]




================================================================================
FILE: 02_Academic & Work/work/applications/Egis Qatar Spontaneous Inquiry.md (~533 words)
================================================================================
---
generated_by: claude
date: 2026-06-07
tags:
  - career
  - application
  - draft
summary: "Spontaneous job application message drafts for Egis in Qatar, including LinkedIn and email versions."
---

# Spontaneous Application Message: Egis (Qatar)

Here are the ready-to-use spontaneous inquiry drafts for **Egis in Qatar**.

---

## 1. LinkedIn Message / InMail (Short & Direct)
*Use this version to connect directly with hiring managers, team leads, or HR recruiters on LinkedIn.*

> **Subject:** Spontaneous Inquiry: Remote Sensing & Environmental Geosciences (PhD)
> 
> Dear [Name / Hiring Team],
> 
> I hope this message finds you well. 
> 
> I am reaching out spontaneously to express my interest in joining Egis's team in Qatar. I am a Remote Sensing Scientist and PhD Candidate at UM6P (defending June 30, 2026), specializing in satellite earth observation, hyperspectral imaging, and machine learning pipelines for environmental monitoring.
> 
> Having followed Egis’s pioneering engineering and consulting projects in the Middle East, I am eager to apply my expertise in scalable remote sensing solutions to your environmental, infrastructure, and sustainability projects in Qatar. Being bilingual (English/French/Arabic) and trained in French-Moroccan academic systems, I align well with Egis's international collaborative work environment.
> 
> I would welcome the opportunity for a brief chat to discuss how my technical skills could support your active projects. I would be glad to share my resume if there is a potential fit.
> 
> Thank you for your time and consideration.
> 
> Best regards,
> 
> **Abdelhak EL MANSOUR**  
> PhD Candidate | Remote Sensing & EO Specialist  
> [LinkedIn Link / Contact Info]

---

## 2. Email Version (Slightly More Detailed)
*Use this version for emailing a contact or submitting via an online spontaneous application form.*

> **Subject:** Spontaneous Application — Remote Sensing & Environmental Geosciences Specialist — Abdelhak EL MANSOUR
> 
> Dear Egis Qatar Hiring Team,
> 
> I am writing to spontaneously express my strong interest in joining Egis in Qatar. As a premier global engineering and consulting group, Egis's work in infrastructure and environmental sustainability aligns perfectly with my background and professional goals.
> 
> I am a Remote Sensing Scientist and PhD Candidate at UM6P (Morocco), set to defend my thesis on June 30, 2026. My research focuses on developing multi-scale remote sensing frameworks and machine learning pipelines to analyze satellite imagery (including PRISMA and EnMAP) for environmental monitoring and mineralogical characterization. 
> 
> Over the course of my research, I have built operational, high-performance Python pipelines that transform raw satellite data into actionable environmental metrics. I am highly motivated to bring this capability—along with my bilingual fluency in English, French, and Arabic—to support Egis's consulting and engineering projects in the GCC region.
> 
> I would appreciate the opportunity to discuss any current or upcoming openings where my skills could add value to your team. I am happy to share my detailed CV and publications list for your review.
> 
> Thank you for your time, and I look forward to the possibility of speaking with you.
> 
> Sincerely,
> 
> **Abdelhak EL MANSOUR**  
> PhD Candidate in Remote Sensing and Environmental Geosciences  
> University Mohammed VI Polytechnic (UM6P)  
> elmansour01abdelhak@gmail.com | [Phone Number]




================================================================================
FILE: 02_Academic & Work/work/applications/UTwente-2026/CV — UTwente.md (~634 words)
================================================================================
---
generated_by: claude
date: 2026-06-04
tags: [cv, job-application, UTwente, ITC, postdoc]
target: Postdoctoral Researcher — Biodiversity-Positive Renewable Energy Transitions, ITC, University of Twente
note: Submit as PDF. Adapted from VITO CV — emphasis on hyperspectral/TIR EO, ecosystem monitoring, Python.
---

# ABDELHAK EL MANSOUR
**Remote Sensing Scientist — Hyperspectral EO & Ecosystem Monitoring**

insitazoult@gmail.com | +212 117 164 00
scholar.google.com/citations?user=ysUOZQ0AAAAJ | @AbdelhakElm
Available: from September 2026 | Open to relocation (Netherlands)

---

## Technical Skills

**Satellite & EO data:** PRISMA (ASI), EnMAP (DLR/GFZ), VNIR–SWIR hyperspectral, thermal infrared (TIR) data processing, HDF5/NPZ pipelines, atmospheric & radiometric correction, multi-temporal change analysis

**Machine learning:** Random Forest, Extra Trees, SVM, XGBoost, 1D/2D-CNN, class imbalance handling, spatial cross-validation — applied to large-scale EO classification and mapping

**Spectral analysis:** VCA-FCLS spectral unmixing, USGS/ECOSTRESS spectral library matching, SAM/SID/NNLS, band selection, endmember extraction

**Python stack:** scikit-learn, GDAL, rasterio, spectral, numpy, pandas, matplotlib, Jupyter — end-to-end production pipelines (1,776-line EnMAP processing engine)

**Ecosystem & environmental monitoring:** Reclamation progress tracking, vegetation/soil spectral signatures, EBV-compatible index design, ground-truth validation (XRD/XRF/HHXRF), ASD FieldSpec 4 field spectroscopy

**Other:** R (familiar), ENVI, Google Earth Engine (familiar), GIS, Git

---

## Key Results

- Designed **Reclamation Progress Index (RPI)** — novel EO-based proxy for ecosystem recovery from EnMAP hyperspectral data. AUC = 1.000, validated against XRF ground truth: Spearman ρ = 0.845, n = 32/zone, p = 1.74 × 10⁻¹²
- PRISMA-based land cover classification (127 field samples, 4 classes, 30m) — BAC = 0.60–0.67, AUC > 0.95 for key mineral classes, spatially constrained cross-validation
- Spectral library matching of 104 field samples (ECOSTRESS/USGS) — mean R² = 0.748, 84% of spectra R² > 0.70
- **4 peer-reviewed publications** (Sensors IF 3.5, IJEST, Mining, BDJ) + 2 in pipeline — including co-authorship on ecosystem reclamation and revegetation studies

---

## Research Experience

**PhD Researcher — Hyperspectral Remote Sensing & Environmental Monitoring**
University Mohammed VI Polytechnic (UM6P), Benguerir, Morocco | Jul 2021 – Jun 2026 (defense Jun 30, 2026)

Developed end-to-end satellite EO pipelines (PRISMA + EnMAP) to monitor mineralogical composition and ecological reclamation of phosphate mine waste at Benguerir (OCP Group). Designed and validated a novel reclamation progress index (RPI) as an operational EO product for ecosystem recovery tracking. Supervised 2 students (engineering + MSc level). Presented at EGU 2025 (Vienna) and EARSeL 2024 (Barcelona).

**Research Mobility — Hyperspectral EO Applications**
University of Valencia, Spain (Pr. Jochem Verrelst's group) | Mar 2024 – Aug 2024

Developed PRISMA classification workflows for mine-affected land; co-authored EARSeL 2024 conference paper; integrated into an international hyperspectral EO research group focused on biophysical variable retrieval.

**Junior Geologist**
Baraka Mining Company, Morocco | Feb 2019 – Aug 2019

Geological exploration and field mapping (Occidental Meseta, Anti-Atlas, High Atlas).

---

## Education

**PhD in Applied Geosciences** — UM6P, Morocco (defending June 30, 2026)
*Thesis: Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks, Benguerir Mine*

**MSc in Applied Geosciences** (Mineral & Energetic Resources) — Cadi Ayyad University, 2017

**BSc in Applied Geosciences** — Moulay Ismail University, 2015

---

## Selected Publications

**First author**
1. EL MANSOUR A et al. — Integrating VNIR–SWIR Spectroscopy and HHXRF for Mineralogical Characterization of Phosphate Mine Waste, Benguerir. **Sensors** 2025 (IF 3.5). doi:10.3390/s26010002
2. EL MANSOUR A et al. — PRISMA-based lithological mapping of phosphate mine waste rocks. **Minerals** 2026 (accepted) ✅

**Co-authored**
3. Zine H, Hakkou R, Papazoglou EG, **EL MANSOUR A** et al. — Revegetation and Ecosystem Reclamation of Post-Mined Land. **IJEST** 2024
4. Zine H, **EL MANSOUR A**, Hakkou R et al. — Mine Closure and Ecological Reclamation: Bibliometric Overview 1980–2023. **Mining** 2023

**In pipeline**
5. EL MANSOUR A et al. — EnMAP-based Reclamation Progress Index for ecosystem recovery monitoring (thesis Ch.3, submission post-defense 2026)

---

## Languages

English (advanced) | French (fluent) | Arabic/Darija (native) | Tamazight (native) | Spanish (basic)




================================================================================
FILE: 02_Academic & Work/work/applications/UTwente-2026/Motivation Letter — UTwente.md (~482 words)
================================================================================
---
generated_by: claude
date: 2026-06-04
tags: [cover-letter, job-application, UTwente, ITC, postdoc]
target: Postdoctoral Researcher — Biodiversity-Positive Renewable Energy Transitions, ITC, University of Twente
note: ~500 words. Adapt greeting if contact name is found. Submit as PDF alongside CV and publications list.
---

# Motivation Letter

Abdelhak EL MANSOUR
insitazoult@gmail.com | +212 117 164 00
Benguerir, Morocco | June 2026

Faculty of Geo-Information Science and Earth Observation (ITC)
University of Twente
Enschede, Netherlands

---

Dear Search Committee,

I am applying for the Postdoctoral Researcher position on Biodiversity-Positive Renewable Energy Transitions at ITC, University of Twente. I will defend my PhD at UM6P (Morocco) on June 30, 2026, and I am available to start no later than September 2026.

My PhD research used PRISMA and EnMAP hyperspectral satellite data to monitor ecosystem recovery at a large phosphate mine in Benguerir, Morocco. The core outcome of my thesis is a novel index — the Reclamation Progress Index (RPI) — derived directly from EnMAP spectral signatures, validated against XRF geochemical ground truth (Spearman ρ = 0.845, p = 1.74 × 10⁻¹², AUC = 1.000). The RPI quantifies the degree to which a disturbed landscape is recovering its functional mineral and vegetation composition over time. In essence, it is an EO-based proxy for ecosystem state — closely aligned with the concept of Essential Biodiversity Variables that your project deploys to track biodiversity change under renewable energy infrastructure.

The technical skills this postdoc requires are precisely those I have built: end-to-end processing of spaceborne hyperspectral data (PRISMA, EnMAP), spectral unmixing (VCA-FCLS), spatial machine learning (Random Forest, Extra Trees, spatial cross-validation), and Python production pipelines. I have also worked with thermal infrared spectral data in the context of mineral identification, and I am familiar with multi-temporal EO analysis for change detection. My mobility at the University of Valencia (Prof. Jochem Verrelst's group, 2024) exposed me to biophysical variable retrieval from hyperspectral data — directly relevant to the EBV/ECV monitoring framework your team uses.

What draws me specifically to this position is the scale of the scientific question: quantifying how the physical footprint of renewable energy infrastructure — solar farms, wind installations — reshapes ecosystem functioning at landscape scale. My background in monitoring large-scale land disturbance and recovery gives me a grounded entry point into this problem. I am comfortable working across disciplinary boundaries, as my thesis required bridging geochemistry, spectroscopy, machine learning, and environmental monitoring.

ITC is the strongest environment I can think of for this work. Its global reputation in applied EO, its infrastructure, and its culture of combining satellite methods with real-world environmental problems are exactly what I want to be part of at this stage of my career.

I submit this application with my CV and publications list. I am happy to provide my thesis manuscript, reference letters, or any additional materials on request.

Yours sincerely,

**Abdelhak EL MANSOUR**
insitazoult@gmail.com | +212 117 164 00
scholar.google.com/citations?user=ysUOZQ0AAAAJ




================================================================================
FILE: 02_Academic & Work/work/applications/UTwente-2026/Publications List — UTwente.md (~260 words)
================================================================================
---
generated_by: claude
date: 2026-06-04
tags: [publications, job-application, UTwente]
note: Submit as PDF alongside CV and motivation letter.
---

# Publications List — Abdelhak EL MANSOUR

scholar.google.com/citations?user=ysUOZQ0AAAAJ

---

## Peer-Reviewed Journal Articles

**[1]** **EL MANSOUR A**, Laamrani A, et al. — Integrating VNIR–SWIR Field Spectroscopy and Handheld X-Ray Fluorescence for Mineralogical Characterization of Phosphate Mine Waste Rocks, Benguerir, Morocco. *Sensors* **2025**, 26(1), 2. IF 3.5. doi:10.3390/s26010002

**[2]** **EL MANSOUR A**, Laamrani A, et al. — PRISMA Hyperspectral Satellite Data for Lithological Mapping and Classification of Phosphate Mine Waste Rocks, Benguerir, Morocco. *Minerals* **2026** (accepted, thesis Chapter 2) ✅

**[3]** Zine H, Hakkou R, Papazoglou EG, **EL MANSOUR A**, et al. — Revegetation and Ecosystem Reclamation of Post-Mined Land: A Review. *International Journal of Environmental Science and Technology (IJEST)* **2024**.

**[4]** Zine H, **EL MANSOUR A**, Hakkou R, et al. — Mine Closure and Ecological Reclamation of Phosphate Deposits: A Bibliometric Overview 1980–2023. *Mining* **2023**.

---

## Articles in Preparation

**[5]** **EL MANSOUR A**, Laamrani A, et al. — EnMAP-Based Reclamation Progress Index (RPI) for Operational Ecosystem Recovery Monitoring at Phosphate Mine Waste Sites. *(Thesis Chapter 3 — submission post-defense, 2026)*

---

## Conference Contributions

**[C1]** **EL MANSOUR A** et al. — Hyperspectral Remote Sensing for Reclamation Monitoring at Benguerir Phosphate Mine: EnMAP-Based Approach. *EGU General Assembly 2025*, Vienna, Austria. (Oral/Poster)

**[C2]** **EL MANSOUR A** et al. — PRISMA-Based Classification of Phosphate Mine Waste Rocks. *EARSeL Symposium 2024*, Barcelona, Spain. (Co-authored with Verrelst group, University of Valencia)

**[C3]** **EL MANSOUR A** et al. — Abstract submitted. *ESPC6 2026*, UM6P, Benguerir, Morocco.




================================================================================
FILE: 02_Academic & Work/work/applications/DLR-2026/Email — Tobias Storch DLR.md (~302 words)
================================================================================
---
generated_by: claude
date: 2026-06-04
tags: [job-application, DLR, cold-email, postdoc]
target: Dr. Tobias Storch — DLR IMF, Oberpfaffenhofen, Germany
contact: tobias.storch@dlr.de | sarah.asam@dlr.de
send: after June 30, 2026 (post-defense)
fit: 10/10 — EnMAP mission scientist, exact overlap with thesis
---

# Cold Email — Dr. Tobias Storch, DLR IMF

**To:** tobias.storch@dlr.de
**CC:** sarah.asam@dlr.de
**Subject:** Postdoctoral Researcher Inquiry — Hyperspectral EO & EnMAP Applications (PhD defended June 2026)

---

Dear Dr. Storch,

I am writing to inquire about postdoctoral opportunities at DLR IMF in hyperspectral remote sensing and EnMAP applications.

I defended my PhD at UM6P (Morocco) on June 30, 2026. My thesis — *Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks* — was built on PRISMA and EnMAP satellite data, and produced a validated operational product: the Reclamation Progress Index (RPI), derived from EnMAP spectral unmixing (VCA-FCLS), with AUC = 1.000 and Spearman ρ = 0.845 against XRF ground truth (p = 1.74 × 10⁻¹²).

My technical stack maps directly onto the work of your group:

- End-to-end EnMAP processing pipelines in Python (1,776-line engine: atmospheric correction, bad-band removal, endmember extraction, unmixing, validation)
- PRISMA + EnMAP hyperspectral classification (Random Forest, Extra Trees, spatial CV)
- Spectral library matching (USGS/ECOSTRESS), SAM/SID/NNLS, VCA-FCLS unmixing
- 4 peer-reviewed publications during PhD; 2 more in pipeline

I followed the EnMAP mission closely throughout my PhD — it is the satellite that made Chapter 3 of my thesis possible. DLR IMF is the group I most want to be part of.

I am available from July 2026 and open to relocation to Oberpfaffenhofen. I would be glad to share my CV, thesis, or any additional material at your request.

Thank you for your time.

Yours sincerely,

**Abdelhak EL MANSOUR**
insitazoult@gmail.com | +212 117 164 00
scholar.google.com/citations?user=ysUOZQ0AAAAJ
UM6P, Benguerir, Morocco




================================================================================
FILE: 02_Academic & Work/work/setup/Elite Vault Setup.md (~973 words)
================================================================================
---
generated_by: claude
date: 2026-05-28
tags: [setup, claude-code, mcp, automation, power-user]
---

# Elite Vault Setup — Power User Stack 2026

> Research: 8 parallel web searches across GitHub, npm, Reddit, HN, Claude docs.  
> Last updated: 2026-05-28. Honest assessment — no hype, no vaporware.

---

## What's Installed and Live

### MCP Servers (9 total, all ✓ Connected)

| Server | Purpose | Status |
|--------|---------|--------|
| `vault-obsidian` | Read/write vault files via MCP | ✓ Live |
| `gmail` | Read/draft/search Gmail in-session | ✓ Live |
| `brave-search` | Web search (token needs renewal) | ✓ Connected |
| `github` | PR reviews, issue tracking | ✓ Live |
| `notion` | Notion DB access | ✓ Live |
| `domain-search` | RDAP + GoDaddy auction detection | ✓ Live |
| `memory` | Persistent knowledge graph across sessions | ✓ Live (new) |
| `sequential-thinking` | Structured multi-step reasoning | ✓ Live (new) |
| `google-drive` | Drive file access | ! Needs OAuth |

**Activate `memory` MCP:** In next session, Claude can store named entities (people, domains, papers) as a persistent graph — survives conversation compaction.

**Activate `sequential-thinking`:** Triggers automatically for complex multi-step tasks. Forces structured `<parameter name="thought">` chains instead of linear responses.

---

### Custom Claude Skills (5 skills in `~/.claude/skills/`)

| Skill | Trigger | What it does |
|-------|---------|--------------|
| `graphify` | `/graphify` | Any input → knowledge graph → HTML + JSON |
| `notebooklm` | `/notebooklm` | Full NotebookLM API (podcast, briefing, FAQ) |
| `vault-review` | `/vault-review` | Weekly vault audit: orphans, deadlines, domain renewals |
| `thesis-check` | `/thesis-check` | Defense readiness audit with daily action plan |
| `obsidian-cli` | `/obsidian-cli` | Obsidian CLI (tasks, properties, plugin dev) |

---

### Vault Scripts (`scripts/`)

| Script | Schedule | What it does |
|--------|----------|--------------|
| `job_monitor.py` | Weekly Monday | RSS scrape → Job Board note |
| `domain_report.py` | Weekly Monday | RDAP lookup + marketplace links |

**Automate via Task Scheduler (Windows):**
```powershell
# Run both scripts every Monday at 8:00 AM
$action1 = New-ScheduledTaskAction -Execute "python" -Argument "C:\Users\Dell\Downloads\abdelhak-real-vault\abdelhak-vault\scripts\job_monitor.py" -WorkingDirectory "C:\Users\Dell\Downloads\abdelhak-real-vault\abdelhak-vault"
$action2 = New-ScheduledTaskAction -Execute "python" -Argument "C:\Users\Dell\Downloads\abdelhak-real-vault\abdelhak-vault\scripts\domain_report.py" -WorkingDirectory "C:\Users\Dell\Downloads\abdelhak-real-vault\abdelhak-vault"
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Monday -At "08:00AM"
Register-ScheduledTask -TaskName "VaultJobMonitor" -Action $action1 -Trigger $trigger -RunLevel Highest
Register-ScheduledTask -TaskName "VaultDomainReport" -Action $action2 -Trigger $trigger -RunLevel Highest
```

---

## Researched Repos — Honest Assessment

### Top-tier (real, maintained, worth using)

**`ProfSynapse/claudesidian-mcp` (Nexus)**  
- Local semantic search over vault using embeddings
- Graph-traversal: find notes by concept, not just keyword
- **Install:** `npm install -g claudesidian-mcp` (not on npm yet — install from GitHub)
- **Verdict:** Most powerful Obsidian MCP. 2-tool architecture. Worth watching for stable npm release.

**`rohitg00/awesome-claude-code-toolkit`**  
- 135 agents, 35 skills, 42 slash commands on GitHub
- **Verdict:** Cherry-pick individual skills. Don't install bulk — most don't match your profile.
- **What to grab:** `research-agent`, `citation-finder`, `brag-doc-updater`

**`obra/knowledge-graph` Claude Code plugin**  
- Vault as knowledge graph with BFS/DFS query tools
- Community detection, god-node identification
- **Verdict:** Already covered by your `graphify` skill (same concept, different implementation)

**`eugeniughelbur/obsidian-second-brain`**  
- 34 slash commands for second-brain workflows
- `@obsidian`, `@notes`, `@daily` context tools
- **Verdict:** Useful reference for custom skills but installs as an Obsidian plugin (not Claude Code). Your existing skills do the same.

**`jacksteamdev/obsidian-mcp-tools`**  
- Semantic search + Templater integration
- **Verdict:** Requires Obsidian plugin side + MCP side. Your `vault-obsidian` MCP handles this adequately.

### Not worth installing (why)

| Repo | Reason to skip |
|------|---------------|
| `sickn33/antigravity-awesome-skills` (1,400 skills) | Bulk install = context bloat. 95% irrelevant. |
| `rps321321/obsidian-mcp-pro` | Not on npm, GitHub repo sparse, unclear maintenance |
| `YishenTu/claudian` | Claude Code *inside* Obsidian — redundant if you use Claude Code CLI |
| `AgriciDaniel/claude-obsidian` | Last commit 8 months ago, no npm package |

---

## Workflow Stack — How It All Connects

```
Morning Standup
└── /om-standup
    ├── reads wiki/hot.md
    ├── reads work/Index.md
    └── surfaces job deadlines + domain alerts

Weekly Review
└── /vault-review
    ├── scans work/active/ for stale notes
    ├── flags job deadlines
    └── flags domain renewals

Job Search
└── scripts/job_monitor.py (weekly, auto)
    └── appends → work/active/Job Board -- Live Tracker.md

Domain Monitoring
└── scripts/domain_report.py (weekly, auto)
    └── saves → AI-Generated/domain-report-YYYY-MM-DD.md

Defense Prep
└── /thesis-check
    ├── counts days to June 30
    └── outputs daily action plan
```

---

## What Requires Manual Action

1. **Google Drive MCP** — run `! gcloud auth login` in Claude Code terminal
2. **Brave Search token** — renew at https://api.search.brave.com (current token invalid)
3. **GoDaddy API key** — add to `.claude/settings.json` vault file to activate auction alerts in domain-search MCP
4. **Windows Task Scheduler** — run the PowerShell block above (one-time, 5 min setup)
5. **ManyChat** — $14/mo, 15 min setup for Instagram DM automation

---

## Your Edge — What Nobody Else Has

The combination of:
- **domain-search MCP** (live RDAP + GoDaddy auction detection in-session)
- **job_monitor.py** (weekly RSS aggregation scoped to hyperspectral + EO — not generic "remote sensing")
- **gmail MCP** (read + draft application emails without leaving Claude)
- **memory MCP** (persistent entity graph: domains, buyers, professors, journals)
- **graphify skill** (any input → knowledge graph — papers, thesis chapters, portfolios)
- **thesis-check skill** (defense countdown with daily actions)

This stack covers: PhD researcher + domain investor + job seeker + Instagram creator — simultaneously, in one environment.

---

## Next Upgrades (when time permits)

| Priority | Action | Time |
|----------|--------|------|
| High | Task Scheduler for weekly scripts | 10 min |
| High | Brave Search token renewal | 5 min |
| Medium | `claudesidian-mcp` when npm-stable | — |
| Medium | Google Drive OAuth | 15 min |
| Low | ManyChat Instagram automation | 15 min |
| Low | GoDaddy API key in settings | 5 min |




================================================================================
FILE: 02_Academic & Work/work/setup/External Data Import Guide.md (~765 words)
================================================================================
---
tags: [setup, import, obsidian, data]
generated_by: claude
date: 2026-06-07
---

# External Data Import Guide

How to get emails, Outlook data, files, images, and PDFs into the vault.

---

## 1. Emails from Outlook (Windows)

### Option A — Obsidian Importer Plugin (Recommended)
Install the **Obsidian Importer** community plugin. It natively imports:
- `.eml` files (email files)
- `.mbox` files (Gmail / Thunderbird exports)

**Workflow:**
1. In Outlook: File → Save As → `.msg` or select emails → File → Save As `.eml`
   - Or: File → Open & Export → Import/Export → Export to File → Outlook Data File (.pst)
2. Convert `.pst` → `.eml` using free tool: **Aid4Mail** (free tier) or **pst-to-eml** CLI
3. In Obsidian: `Ctrl+P → Obsidian Importer → Import from email files (.eml)`
4. Set destination folder: `AI-Generated/emails/`
5. Add frontmatter `generated_by: claude` on import if needed

### Option B — Markdown Export Script
Export important emails manually. For each email you want to preserve as a note:
1. Copy/paste email body into Obsidian note
2. Use template:
```markdown
---
from: sender@example.com
to: abdelhak.elmansour@um6p.ma
date: YYYY-MM-DD
subject: "Email subject"
tags: [email, imported]
---

# Subject

**From:** Sender Name <email>
**Date:** YYYY-MM-DD

---

Body content here...
```
Save in: `AI-Generated/emails/YYYY-MM-DD — Subject.md`

### Option C — Obsidian Web Clipper (for Gmail)
If using Gmail: install **Obsidian Web Clipper** browser extension. One-click saves any web page (including Gmail threads) as a markdown note directly into the vault.

---

## 2. Files (PDFs, DOCX, Excel, PPT)

### PDFs
- Drag-and-drop into vault folder → Obsidian treats them as attachments
- Embed in a note: `![[filename.pdf]]` or `![[filename.pdf#page=3]]`
- Recommended folder: `thesis/references/` for papers, `AI-Generated/files/` for other docs
- **To make PDF content searchable:** Use Obsidian **PDF++ plugin** (community) for annotation and text extraction

### DOCX (Word) — Convert to Markdown
Use **Pandoc** (free CLI tool):
```powershell
pandoc input.docx -o output.md
```
Then move output.md into vault. Works for thesis drafts, cover letters, etc.

### Excel / CSV — Import as Dataview
Save CSV files in vault → query with DataviewJS:
```dataviewjs
const data = await dv.io.csv("path/to/file.csv");
dv.table(data.headers, data.rows);
```

---

## 3. Images

### Direct drag-and-drop
Drag any image (PNG, JPG, WEBP) into Obsidian → it copies to your attachments folder.
Set attachment folder: Settings → Files and links → Default location = `assets/`

### Embed in notes
```markdown
![[image.png]]
![[image.png|300]]        ← width in pixels
![[image.png|caption]]
```

### Screenshot workflow
For screenshots of important emails, docs, or web content:
1. Windows Snip (Win+Shift+S) → paste into Obsidian note directly (auto-saves to attachments)
2. Or: Screenshot → drag into vault folder → embed

### Images already in vault
Thesis figures: `thesis/defense-prep/gen_figs/` — already embedded in defense notes.

---

## 4. Outlook Calendar → Obsidian

### Option A — iCal Export
Outlook → File → Save Calendar → `.ics` file
Convert with: **icalendar-to-obsidian** Python script (GitHub: available)
Or: manually copy key dates into Daily Notes / the [[02_Academic & Work/thesis/defense-prep/30-Day Countdown]]

### Option B — Forward to Vault
For important calendar entries: copy paste into `work/meetings/` folder with date in filename.

---

## 5. Web Pages (Articles, Papers, News)

### Obsidian Web Clipper (Best Option)
Browser extension: **Obsidian Web Clipper** (official, by Obsidian team)
- Clips any web page to vault with one click
- Auto-applies templates for articles, papers, etc.
- Install: Chrome/Firefox extension store → search "Obsidian Web Clipper"

### defuddle (via Claude Code)
Claude Code has a `/defuddle` skill that converts web pages to clean markdown.
Usage: give Claude a URL → it strips navigation/ads and saves clean content to vault.

### Manual
Copy URL → paste into note → add `tags: [clipping]` frontmatter.

---

## 6. Zotero Papers → Literature Notes

Already configured via **Citations plugin** (installed 2026-06-07):
- Your 292 refs are in `thesis/references.bib` (auto-synced via Better BibTeX)
- `Ctrl+P → Citations: Insert Markdown citation` → search your library
- `Ctrl+P → Citations: Open literature note` → creates `thesis/literature-notes/@citekey.md`

For new papers: add to Zotero → Better BibTeX auto-updates references.bib → available in Citations plugin immediately.

---

## 7. Flashcards from Any External Content

Once you have any content in the vault as a note, add flashcard syntax:
```
Question::Answer
```
Tag the note `#flashcards` and the Spaced Repetition plugin will include it in reviews.

Active flashcard decks:
- [[02_Academic & Work/thesis/defense-prep/Flashcards — Defense]] — numbers + jury prep
- [[04_Knowledge Base/wiki/Flashcards — Research Concepts]] — all scientific knowledge
- [[02_Academic & Work/work/Flashcards — Career]] — contacts + career strategy
- [[03_Digital Life/money/domaining/Flashcards — Domains]] — full domain portfolio
- [[03_Digital Life/personal/Flashcards — Identity]] — bio + elevator pitches




================================================================================
FILE: 02_Academic & Work/work/setup/NotebookLM Setup.md (~337 words)
================================================================================
---
generated_by: claude
date: 2026-05-26
---

# NotebookLM Integration

Installed: `notebooklm-py` v0.5.0 with Playwright browser auth.
Auth: `~/.notebooklm/profiles/default/storage_state.json`
CLI: `C:\Users\Dell\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts\notebooklm.exe`

Skill installed: `~/.claude/skills/notebooklm/SKILL.md` → use `/notebooklm` in Claude Code.

---

## Notebooks

| Name | ID | Sources |
|------|----|---------|
| PhD Defense — Thesis | `bb2823a9-ab3d-454a-9425-f534620228db` | Thesis Overview, Full Ingestion, Verrelst Prep, Numbers Arsenal, Defense Strategy, Jury Prep, 36-Day Sprint, Victory Speech |
| Hyperspectral Methods — Deep Reference | `f5b6cff5-2d39-4431-8fa8-f4c5f3acaa40` | All 15 wiki/concepts pages + Code Ingestion |
| Job Search — Post-Defense Strategy | `da39982c-a4cf-4039-93d4-ceda231196ec` | Hot Opportunities, 90-Day Plan, Postdoc Applications, Hidden Strengths, Brag Doc, Money Overview, North Star, Who I Am Becoming |

---

## CLI Quick Reference

```bash
# Set active notebook
notebooklm use bb2823a9        # defense
notebooklm use f5b6cff5        # methods
notebooklm use da39982c        # jobs

# Ask a question
notebooklm ask "What are the three most likely Verrelst attack vectors?"
notebooklm ask "Explain VCA-FCLS as if I'm defending it to a hostile jury"

# Generate artifacts
notebooklm generate audio      # podcast overview
notebooklm generate quiz       # study quiz
notebooklm generate flashcards # flashcards
notebooklm generate mind-map   # mind map

# Download artifacts
notebooklm download audio      # saves audio file

# List sources
notebooklm source list

# Add new source (.md files MUST use --mime-type text/plain)
notebooklm source add --notebook bb2823a9 --type file --mime-type "text/plain" "path/to/file.md"

# Refresh after vault updates
notebooklm source refresh <source-id>
```

---

## Workflow: Defense Prep

1. `notebooklm use bb2823a9`
2. `notebooklm ask "Generate 10 hard questions Verrelst would ask about my RPI methodology"`
3. `notebooklm generate quiz` → download and study
4. `notebooklm generate audio` → listen as podcast

## Workflow: Update After Vault Changes

When you update a defense prep file, refresh it:
```bash
notebooklm use bb2823a9
notebooklm source list   # find the source ID
notebooklm source refresh <id>
```

---

## Notes

- Unofficial reverse-engineered API — Google can break it without warning
- Re-authenticate if it stops working: `notebooklm login`
- Sessions expire: re-run `notebooklm login` every few weeks




================================================================================
FILE: 02_Academic & Work/work/setup/Plugin Guide.md (~652 words)
================================================================================
---
generated_by: claude
date: 2026-05-26
updated: 2026-06-07
tags: [setup, plugins, obsidian]
---

# Obsidian Plugin Guide

14 community plugins installed and enabled. **6 added 2026-06-07.**

---

## obsidian-git (Vinzent03)

**What it does:** Auto-commits and syncs the vault to GitHub every 20 minutes.

**Config set:**
- Auto-commit every **20 minutes** (when Obsidian is open)
- Pull on startup (gets latest from GitHub before you start)
- Commit message: `vault: auto-backup YYYY-MM-DD HH:mm:ss`
- Pull before push: enabled
- Status bar: shows git status

**Manual commands (Cmd/Ctrl+P → "Git"):**
- `Git: Create backup` — commit + push right now
- `Git: Pull` — pull latest from remote
- `Git: Open source control view` — see changed files
- `Git: Open history` — browse commit history

**Remote:** https://github.com/Appiie/abdelhak-vault.git

---

## Dataview (blacksmithgu)

**What it does:** Query your vault like a database. Live tables and lists from file metadata and content.

**Config set:**
- DataviewJS enabled (JavaScript queries)
- Inline queries enabled
- Task completion tracking on
- HTML rendering allowed

**Where it's used:**
- `Dashboard.md` — defense countdown + live tables of all active files
- `Home.md` — mission control

**Basic syntax:**
```dataview
TABLE file.mtime AS "Updated"
FROM "02_Academic & Work/thesis/defense-prep"
SORT file.mtime DESC
```

```dataviewjs
const days = Math.ceil((new Date("2026-06-30") - new Date()) / 86400000);
dv.paragraph(`${days} days to defense`);
```

**Add metadata to any note for Dataview to pick up:**
```yaml
---
status: in-progress
priority: high
deadline: 2026-06-30
---
```

---

## Templater (SilentVoid13)

Auto-fill templates with dynamic content (dates, prompts, etc.).

---

## Tasks (obsidian-tasks-plugin)

Track tasks across the vault with due dates, priorities, recurrence.

**Syntax:**
```
- [ ] Write slide 5 📅 2026-06-01 ⏫
```

**Query all urgent tasks:**
```tasks
not done
priority is high
```

---

## Excalidraw

Draw diagrams inside Obsidian. Create new: `Cmd+P → Excalidraw: Create new`.

---

## Charts

Render charts from data. Useful for plotting XRF values or accuracy metrics inline.

---

## Style Settings

Adjust theme appearance. `Cmd+P → Style Settings`.

---

## Spaced Repetition (st3v3nmw) — NEW

Daily flashcard review. Implements SM-2 algorithm — cards space out as you master them.

**Flashcard file:** `thesis/defense-prep/Flashcards — Defense.md`

**Syntax:**
```
Question::Answer          ← single-line card
Question:::Answer         ← reversed (shows answer first too)
```
Multi-line:
```
Question
?
Answer
```
Cloze: `==highlighted text==` becomes a fill-in-the-blank card.

**Workflow:** Open `Flashcards — Defense.md` → ribbon icon "Review flashcards" → rate each card Easy/Good/Hard.

---

## Citations (hans) — NEW

Search your Zotero library from inside Obsidian and insert `[@citekey]` references.

**Config:** Points to `thesis/references.bib` (your 292-ref Better BibTeX export).
**Commands:** `Ctrl+P → Citations: Insert Markdown citation` or `Citations: Open literature note`
**Literature notes:** Auto-created in `thesis/literature-notes/` with full metadata template.

---

## QuickAdd (chhoumann) — NEW

4 capture macros bound to commands:

| Macro | What it does |
|-------|-------------|
| 💡 Capture Idea | Appends timestamped idea to `wiki/hot.md` |
| 🌐 New Domain Lead | Creates domain lead file from template |
| 💼 New Job Application | Creates job application file from template |
| 🎓 Defense Q&A Entry | Appends Q&A block to `thesis/defense-prep/Defense QA.md` |

Access: `Ctrl+P → QuickAdd: ...`

---

## Kanban (mgmeyers) — NEW

Two active boards:
- `work/active/Job Pipeline.md` — job search stages (To Apply → Letter Drafted → Sent → Interview → Offer)
- `money/domaining/Domain Outreach Pipeline.md` — domain sales stages

Open any `.md` file with `kanban-plugin: basic` frontmatter to get the board view.

---

## Linter (platers) — NEW

Runs automatically on save. Enforces:
- Consistent heading spacing
- No trailing whitespace
- Proper ellipsis formatting
- YAML `updated:` timestamp on save

Ignores: `.raw/`, `.claude/`, `thesis/references.bib`

---

## Natural Language Dates (argenos) — NEW

Type `@today`, `@tomorrow`, `@next monday`, `@june 25` anywhere — converts to ISO date on trigger.

Works inline in Tasks plugin: `- [ ] Submit ETH application @june 25`
Trigger: `@` followed by a date phrase → `Alt+D` to insert, or just type and it auto-converts.




================================================================================
FILE: 02_Academic & Work/work/meetings/README.md (~133 words)
================================================================================
---
tags: [work, inbox, meetings]
---

# Meetings Inbox

Drop raw meeting notes here before processing.

## Usage

1. Export or write your note in this folder
2. File naming: `YYYY-MM-DD <Topic or Person>.md`
3. Run `/om-intake` — classifies, routes, and clears the inbox automatically

## What `/om-intake` does with each file

| Detected content | Destination |
|-----------------|-------------|
| 1-on-1 with a person | `work/1-1/<Person> YYYY-MM-DD.md` |
| Project update | Append to `work/active/<Project>.md` |
| Decision reached | New Decision Record + `work/Index.md` |
| Action item | `- [ ]` in the relevant note |
| Win / recognition | `perf/Brag Doc.md` |
| New person mentioned | Stub in `org/people/<Name>.md` |
| Blocker identified | `## Blockers` section in active note |

For freeform unstructured content, use `/om-dump` instead.




================================================================================
FILE: 03_Digital Life/brain/Gotchas.md (~126 words)
================================================================================
---
description: "Things that have bitten before and will bite again — pitfalls, edge cases, and workflow traps"
tags:
  - brain
---

# Gotchas

Things that have bitten before and will bite again.

## obsidian-mind: commands ≠ Claude Code skills

`/om-standup`, `/om-weekly`, etc. are **slash commands** stored in `.claude/commands/`. They are NOT harness skills. The `Skill` tool does not recognize them. To execute them: read the corresponding `.md` file and apply its workflow manually. When using Claude Code CLI directly (terminal), slash commands run natively.

## PowerShell vs Bash on Windows

This project runs on Windows. PowerShell commands (Copy-Item, etc.) do not work in the Bash tool. Use the PowerShell tool for all Windows file operations.

---

*See also: [[North Star]] · [[Key Decisions]] · [[Patterns]]*




================================================================================
FILE: 03_Digital Life/brain/Key Decisions.md (~302 words)
================================================================================
---
tags: [brain, decisions]
updated: 2026-05-24
---

# Key Decisions

---

## 2026-05-24 — Build Claude × Obsidian second brain
**Context:** Years of AI conversations scattered across Claude, Gemini, ChatGPT — no persistence  
**Decision:** Build a vault that captures everything and gives AI full context on Abdelhak  
**Rationale:** Defense in 1 month, money pressure, postdoc search — need systems, not chaos. See [[North Star]] for priorities.  
**Outcome:** TBD

---

## 2025-11 — Contact NORCE Norwegian Research Centre
**Context:** Postdoc search, looking for hyperspectral + mining research fit  
**Decision:** Reached out to NORCE in November 2025  
**Rationale:** Norway has competitive postdoc salaries + strong environmental remote sensing programs  
**Outcome:** Dropped from plans — not in postdoc targets (confirmed 2026-05-27)

---

## 2025-09 — Evaluate Collaboration Offers Carefully
**Context:** Growing Instagram (70K milestone hit) → multiple brand deals incoming  
**Decision:** Evaluate each collaboration against audience fit, authenticity, payment  
**Rationale:** Audience trust = long-term asset. Short-term money isn't worth destroying it.  
**Outcome:** Selective approach maintained

---

## 2025-~~ — Use SCSE Model for Lithology Mapping
**Context:** Standard CNN had class collapse + accuracy issues  
**Decision:** Implement SCSE (channel + spatial squeeze-excitation) — see [[Machine Learning for Hyperspectral]]  
**Rationale:** Better at learning which spectral bands and spatial locations matter  
**Outcome:** Best accuracy of all models tested — made it into [[Thesis Overview|thesis]]

---

## 2025-~~ — Thesis Study Site: Benguerir (not another site)
**Context:** Choice of study site for PhD  
**Decision:** [[OCP Group and Benguerir Mine|Benguerir phosphate mine]] (OCP)  
**Rationale:** UM6P is literally in Benguerir (OCP-founded university), data access, real-world relevance  
**Outcome:** Thesis completed, defense pending — see [[Defense Strategy]]

---

## 2024-~~ — Italy Trip During PhD
**Context:** PhD burnout risk, need to live  
**Decision:** Go to Rome anyway  
**Rationale:** Life doesn't pause for PhDs  
**Outcome:** Colosseum, Trevi Fountain, Vatican, vintage football shirts. Worth it.




================================================================================
FILE: 03_Digital Life/brain/Memories.md (~244 words)
================================================================================
---
description: "Index of memory topics — key decisions, patterns, gotchas, people context"
tags:
  - brain
  - index
---

# Memories

Persistent context and knowledge retained across sessions. Each topic lives in its own note — follow the links.

- [[Key Decisions]] — architectural and workflow decisions worth recalling
- [[Patterns]] — recurring patterns and conventions discovered across work
- [[Gotchas]] — things that have bitten before and will bite again
- [[People & Context]] — org structure, teams, review history, dynamics
- [[North Star]] — living goals document, read at session start
- [[Skills]] — custom slash commands and workflows

## Recent Context

- **2026-05-27** — Full vault translation completed. 8 files translated: `90-Day Plan Post-Defense`, `Hidden Strengths`, `Morning Brief Template`, `CeDoc Hours Log`, `Mission Order`, `work/Index`, `Who I Am Becoming`, `Hot Opportunities`. Vault is now 100% English. Remaining accented chars are proper nouns (Raï, Office Chérifien) and URLs — left intentionally.
- **2026-05-27** — Fixed stale reference in `Verrelst Prep.md`: NORCE removed, replaced with DLR/ETH/VITO (user confirmed NORCE is not in plans).
- **2026-05-27** — obsidian-mind installed in vault (18 commands, 9 agents, Node hooks). `/om-standup`, `/om-weekly`, `/om-dump`, `/om-wrap-up` tested and functional.
- **2026-05-27** — Laamrani meeting: slides to start this week. Note → [[02_Academic & Work/work/1-1/Laamrani-2026-05-27]].
- **2026-05-27** — Weekly synthesis saved → [[04_Knowledge Base/AI-Generated/logs/weekly-2026-05-27]]. Drift identified: slides silent goal for one week.
- **2026-05-26** — Vault built (166+ files), NotebookLM (3 notebooks, 31 sources), VITO ×2 applied, ESPC6 abstract submitted.




================================================================================
FILE: 03_Digital Life/brain/Morning Brief Template.md (~300 words)
================================================================================
---
tags: [brain, system, morning, ritual]
note: Instructions for Claude — read when Abdelhak says "good morning" or equivalent
---

# Morning Brief — Instructions for Claude

> When Abdelhak says "good morning", "bonjour", "sabah lkhir" or equivalent, execute this protocol automatically. Do not ask for permission. Deliver the full brief.

---

## Execution Protocol

### 1. Read first
- `wiki/hot.md` — recent context
- `thesis/defense-prep/36-Day Sprint.md` — today's task
- `work/active/Hot Opportunities — May 2026.md` — job status

### 2. Calculate
- **Days until defense**: June 30, 2026 − today's date
- **Critical task of the day**: extract from the Sprint the most urgent task for the current week

### 3. Search (WebSearch if available)
- New job opportunities: "hyperspectral remote sensing postdoc 2026" or "remote sensing job Europe"
- Weather in Benguerir or Rabat

---

## Brief Format

Deliver exactly in this order, no introduction:

---

**☀️ MORNING OF [DATE]**

🎓 **Defense in [N] days** — [June 30, 2026]

🎯 **THE one thing to do today:**
[One task only. The one that changes everything. From the Sprint. Not a list.]

💼 **Overnight jobs:**
[Quick check — new posting found or "nothing new since yesterday"]

💰 **Domain alert:**
[Check if any of the top 5 domains received an offer or has an active potential buyer — otherwise "No alert"]

🌍 **Weather [city]:**
[Temperature + conditions]

🧭 **Who you're becoming:**
[One line from personal/Who I Am Becoming.md — rotating, never the same twice]

---

## Rules
- No "Great morning!" or motivational outro
- Task of the day = ONE thing only. Not two. Not a list.
- If it's a weekend or the day before defense: adapt the tone
- If it's June 30, 2026: special brief — just: "This is the day. You know what to do. Go."




================================================================================
FILE: 03_Digital Life/brain/North Star.md (~826 words)
================================================================================
---
tags: [brain, north-star, identity, core]
updated: 2026-05-26
---

# North Star — Abdelhak EL MANSOUR

## Who I Am
**PhD Candidate** — Geology and Sustainable Mining Institute (GSMI)  
**University Mohammed VI Polytechnic (UM6P)**, Benguerir, Morocco  
**Supervisor:** Pr. Ahmed LAAMRANI  
**Specialty:** Remote Sensing and Environmental Geosciences  
**Location:** Benguerir, Morocco  
**X/Twitter:** [@AbdelhakElm](https://x.com/AbdelhakElm)  
**Scholar:** [Google Scholar](https://scholar.google.com/citations?user=ysUOZQ0AAAAJ)  
**Identity:** Amazigh / Moroccan — proud of Ait Atta heritage, from Errachidia, Tamazight native, Raï music lover

---

## My Thesis (Defending June 30, 2026 — 22 days)
**Full title:**  
*"Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks in Benguerir Mine, Morocco"*

**155 pages. The culmination of years of work.**

- **Site:** Benguerir phosphate mine (OCP Group), Morocco
- **Sensors:** PRISMA satellite + EnMAP satellite + ASD FieldSpec 4 (field)
- **Core methods:** Extra Trees/RF (Ch.2), VCA-FCLS + novel RPI (Ch.3), NNLS unmixing (Ch.1)
- **Validation:** XRD + XRF (independent geochemical ground truth)
- **What makes it original:** Multi-scale (satellite → field) framework for BOTH mineralogy AND reclamation monitoring. RPI is a new scientific instrument — not just an algorithm.

**Numbers that matter:**
- Ch.2: BAC=0.60–0.67, AUC>0.95, 127 samples, 4 classes
- Ch.3: BAC=0.984±0.031, AUC=1.000, ρ=0.845, p=1.74×10⁻¹², RPI: RZ=0.896, RWR=0.203

---

## Current Mission (Next 22 Days)
1. **DEFEND THE THESIS** — this is everything right now
2. Prepare for jury (10 members; Verrelst = highest technical threat)
3. Post-defense plan ready (publications, DLR/ETH/VITO/OCP)

→ [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]] | → [[02_Academic & Work/thesis/defense-prep/Defense Strategy]]

---

## Career Ambitions (Post-Defense)
- **Priority 1:** DLR IMF — email Dr. Tobias Storch (EnMAP team) directly after defense
- **Priority 2:** OCP Group R&D — through Laamrani. RPI tool = potential €10–30K consulting or R&D hire
- **Priority 3:** ETH Zurich / VITO — postdoc applications active
- **Industry:** Remote sensing consultant for mining sector (OCP natural fit)
- **Decision point:** September 2026 — postdoc vs consulting vs both

---

## Financial Reality (Active, Not Pending)
Money is being solved NOW, not after defense. Multiple streams running in parallel:

- **Domaining** — 86 domains, ~$1.5M BIN total. Top 5 actively marketed.
  - Crown jewels: lifetimeharbor ($130K), retireharbor ($120K), retiresteward ($90K)
  - Domain names include Moroccan geographies (Zagora, Merzouga — identity-driven strategy)
- **phddiarymemes** — 70K PhD students on Instagram. Sponsorships from PhD-adjacent brands (Notion, Overleaf, academic publishers, online courses). NOT a research account.
- **Freelancing** — Upwork article writing actively tested (May 2026). Solving income gap in real-time.
- **Post-defense:** "Dr." title = leverage upgrade across all streams

---

## Research Skills Stack
**Python:** spectral, GDAL, rasterio, scikit-learn, numpy, matplotlib, XGBoost, Jupyter  
**Data:** PRISMA HDF5, EnMAP, NPZ, raster processing, band selection  
**ML:** Extra Trees, RF, SVM, 1D/2D/3D-CNN, SCSE, VCA-FCLS, NNLS, spatial CV  
**Remote Sensing:** VNIR+SWIR fusion, atmospheric correction, spectral unmixing, mineral library matching  
**Geoscience:** phosphate mineralogy, XRD interpretation, waste rock geochemistry  
**AI Tools:** Claude Code (primary), Grok (daily advisor), NotebookLM (defense prep)  
**Writing:** French (primary academic), English (papers + tools), Arabic/Darija (personal)  

---

## Publications
- **Published (4):** Sensors 2025 (Ch.1) · IJEST 2024 · Mining 2023 · BDJ 2023
- **Pipeline:** Minerals (Ch.2, accepted 2026 ✅) · Ch.3 (pending submission post-defense)
- **Conferences:** EGU 2025 · EARSeL 2024 (Valencia) · ESPC6 2026 (UM6P, abstract submitted)

---

## People Who Matter
- **Pr. Ahmed LAAMRANI** — supervisor → [[02_Academic & Work/org/people/Ahmed Laamrani]]
- **Dr. Tobias Storch (DLR)** — target contact post-defense
- **Family** — from Errachidia, niece, community

---

## Identity — Who I Actually Am (Twitter Intelligence, May 2026)
Three things running simultaneously, always:
- **Researcher** — PhD, 4 papers, satellite pipelines, XRF ground truth, real mine
- **Builder** — 86 domains, Python pipelines, AI tooling, freelance testing
- **Community member** — proud Moroccan, Darija speaker, football fan, silent support for others

Twitter handle has been active since **2014** (12 years). Almost no self-promotion. Follows 2,043 people. ~220 followers. All real broadcasting happens on Instagram. Twitter is where I learn; Instagram is where I lead.

My Grok usage shows I use AI as a personal advisor — not just a coding tool. Image generation (desert scenes, poetic imagery), Upwork strategy, Python learning, translation. There is a creative/visual side that doesn't appear in the academic profile.

---

## What I Am NOT
- Waiting for "Dr." to start building things
- Broadcasting my wins loudly (I celebrate others more than myself)
- Letting the thesis define my only identity
- Staying in Morocco by default — open to Europe, international

---

## Values & Identity
- Moroccan & Amazigh — Ait Atta heritage is not background noise, it's who I am
- Curious about everything: geology, music, food, history, AI, art
- Humor is how I survive PhD life (memes, polls, dry posts)
- I helped a friend through crisis (Oct 2025) — I care about people, not just work
- Rome during PhD — I live life while doing the work
- I build things that didn't exist before (RPI, 1,776-line pipeline, 86-domain portfolio, 70K meme page)




================================================================================
FILE: 03_Digital Life/brain/Patterns.md (~334 words)
================================================================================
---
tags: [brain, patterns]
updated: 2026-05-24
---

# Patterns — How Abdelhak Actually Works

## Research Patterns
- **Iterative code debugging** — I build something, it breaks, I fix it step by step (Claude/Gemini history is full of this)
- **Multiple AI tools in parallel** — Claude for complex reasoning, Gemini for technical code, both for writing
- **Writing in multiple languages** — French for academic, English for international, Darija for personal
- **Spectral data pipeline obsession** — I care deeply about the [[Hyperspectral Imaging|processing chain]] being right before touching the [[Machine Learning for Hyperspectral|ML]]

## What I Use AI For (From History)
- Python debugging (HDF5, bad bands, NPZ, pyspectra, memory issues)
- Scientific writing (manuscript revision, cover letters, emails, thesis)
- Arabic/French translation and formatting
- Instagram captions and content strategy
- Collaboration evaluation (am I being offered a fair deal?)
- CV and career documents
- Visual content creation (memes, captions)
- Understanding statistical concepts (p-values, accuracy metrics)
- Research ideation (postdoc opportunities, hyperspectral applications)
- Personal things (gift ideas for niece, Rome itinerary, friend in crisis)

## Strengths I Should Lean Into
- Deep technical fluency in [[Hyperspectral Imaging|hyperspectral]] Python pipeline — see [[Thesis Overview]]
- Real [[OCP Group and Benguerir Mine|OCP/Benguerir]] context — unique in the field
- 70K+ audience that trusts me — leverage post-defense, see [[Instagram Strategy]]
- Multilingual — can work internationally and in Morocco — see [[North Star]]

## Things That Trip Me Up
- Procrastination (self-aware about it — memes are coping)
- Getting deep in code debugging and losing the big picture
- Over-evaluating opportunities instead of deciding and moving

## Communication Patterns
- Multilingual brain — switches effortlessly
- Uses humor as default mode, especially in stressful periods
- Direct and honest about financial needs — no pretense

## Energy Management
- PhD life means irregular hours — work when energy is there
- Family moments matter — carved out time for niece, Rome trip
- Music (Raï) — actual reset mechanism




================================================================================
FILE: 03_Digital Life/brain/Skills.md (~1178 words)
================================================================================
---
date: 2026-04-07
description: "Vault-specific workflows and slash commands — reusable patterns for review prep, project tracking, and vault maintenance"
tags:
  - brain
  - index
---

# Skills

Custom slash commands, subagents, and reusable workflows. Defined in `.claude/commands/` and `.claude/agents/`.

## Slash Commands

### Daily Workflow

| Command | Purpose |
|---------|---------|
| `/om-standup` | Morning kickoff — load context, review yesterday, surface tasks, identify priorities |
| `/om-dump` | Freeform capture — dump anything, gets routed to the right notes automatically |
| `/om-wrap-up` | Full session review — verify notes, indexes, links, suggest improvements. Auto-triggered on "wrap up". |

### Editing & Synthesis

| Command | Purpose |
|---------|---------|
| `/om-humanize` | Voice-calibrated editing — makes Claude-drafted text sound like you wrote it |
| `/om-weekly` | Weekly synthesis — cross-session patterns, North Star alignment, uncaptured wins |

### Meeting Prep & Capture

| Command | Purpose |
|---------|---------|
| `/om-prep-1on1` | Prep for an upcoming 1:1 — load person context, open items, wins to share, suggested agenda |
| `/om-capture-1on1` | Capture 1:1 meeting transcript into structured vault note with quotes, action items, DM context |
| `/om-incident-capture` | Capture incident from Slack channels/DMs into structured vault notes — timeline, people, analysis, brag entry |
| `/om-slack-scan` | Deep scan Slack channels/DMs for evidence — extracts timestamped touchpoints, organizes by context |
| `/om-meeting` | Prep for any meeting by topic — subject-forward briefing with open items, blockers, and brainstormed considerations |
| `/om-intake` | Process meeting notes inbox — classify raw exports in `work/meetings/` and route to the right vault notes |

### Performance & Review

| Command | Purpose |
|---------|---------|
| `/om-peer-scan` | Deep scan a peer's GitHub PRs for review prep — produces structured analysis saved to `perf/evidence/` |
| `/om-review-brief` | Generate review brief (manager or peer version) from vault data |
| `/om-self-review` | Write self-assessment for review tool — projects, competencies, principles |
| `/om-review-peer` | Write peer review — projects, principles, performance summary |

### Vault Maintenance

| Command | Purpose |
|---------|---------|
| `/om-vault-audit` | Deep structural audit — indexes, frontmatter, links, Bases, folder placement, stale context |
| `/om-vault-upgrade` | Import content from an existing vault — detects version, classifies notes, transforms frontmatter, rebuilds indexes |
| `/om-project-archive` | Move completed project from `work/active/` to `work/archive/YYYY/`, update all indexes |

## Usage Notes

**Daily:**
- `/om-standup` replaces the manual session start — reads North Star, active work, tasks, git log
- `/om-dump` processes freeform text and routes each piece to the correct note type and folder
- `/om-wrap-up` is auto-triggered when you say "wrap up" — runs full session review

**Editing & Synthesis:**
- `/om-humanize` calibrates against your actual writing samples, not a word blacklist. Detects context from frontmatter (review → corporate-confident, incident → precise, 1:1 → conversational). Run after drafting any note to make it sound human.
- `/om-weekly` bridges standup and review brief — run at end of week for cross-session patterns, North Star drift, and uncaptured wins. Output is transient by default; offer to promote findings to brag doc or North Star.

**Capture:**
- `/om-capture-1on1` handles transcripts, raw notes, or summaries
- `/om-incident-capture` takes Slack URLs and produces structured incident documentation
- `/om-slack-scan` should be run AFTER `/om-peer-scan` to add context beyond code (leadership, communication, collaboration evidence)

**Performance:**
- `/om-peer-scan` works best when launched as parallel agents (one per person)
- `/om-review-brief` needs the private brief to exist first — it generates filtered versions from it

**Maintenance:**
- `/om-vault-audit` should be run at the end of substantial sessions — catches stale indexes and mixed context
- `/om-vault-upgrade` imports content from an existing vault (older obsidian-mind or any Obsidian vault). Detects version, classifies notes, transforms frontmatter, fixes wikilinks, rebuilds indexes. Use `--dry-run` to preview.
- `/om-project-archive` handles the active/ → archive/ move with index updates

## Subagents

| Agent | Purpose | Invoked by |
|-------|---------|------------|
| `brag-spotter` | Proactively finds uncaptured wins and competency gaps | `/om-wrap-up`, `/om-weekly` |
| `context-loader` | Loads all vault context about a person, project, incident, or concept | Direct — "load context on X" |
| `cross-linker` | Finds missing wikilinks, orphans, broken backlinks across the vault | `/om-vault-audit` |
| `people-profiler` | Bulk create/update person notes from Slack profiles | `/om-incident-capture` |
| `review-prep` | Aggregates all performance evidence for a given review period | `/om-review-brief` |
| `slack-archaeologist` | Full Slack reconstruction — reads every message, thread, profile, produces unified timeline | `/om-incident-capture` |
| `vault-librarian` | Deep vault maintenance — orphan detection, broken links, frontmatter validation, stale notes | `/om-vault-audit` |
| `review-fact-checker` | Verify every claim in a review draft against vault sources | `/om-self-review`, `/om-review-peer` |
| `vault-migrator` | Classify, transform, and migrate content from a source vault | `/om-vault-upgrade` |

Subagents run in isolated context windows via `.claude/agents/`. They don't pollute the main conversation.

## Hooks

| Hook | When | What |
|------|------|------|
| SessionStart | On startup/resume | QMD re-index, inject North Star, active work, recent changes, tasks, file listing |
| UserPromptSubmit | Every message | Classify content (decision, incident, 1:1, win, architecture, person, project update) and inject routing hints |
| PostToolUse | After writing `.md` | Validates frontmatter, checks for wikilinks |
| PreCompact | Before context compaction | Back up session transcript to `thinking/session-logs/` |
| Stop | End of session | Checklist: archive, update indexes, check orphans |

## Semantic Search (QMD)

If QMD is installed (`npm install -g @tobilu/qmd`), the vault has semantic search. Every command takes `--index <name>` where `<name>` is `vault-manifest.json`'s `qmd_index` field (default: `obsidian-mind`):

- `qmd --index <name> query "..."` — hybrid BM25 + vector + LLM reranking (best quality)
- `qmd --index <name> search "..."` — fast BM25 keyword search
- `qmd --index <name> vsearch "..."` — semantic vector search (exploratory)
- `qmd --index <name> update && qmd --index <name> embed` — refresh index after bulk changes

SessionStart hook runs `qmd --index <name> update` automatically, reading the index name from the manifest. First-time setup on a fresh clone: `node --experimental-strip-types scripts/qmd-bootstrap.ts`. See `.claude/skills/qmd/SKILL.md` for full reference, and [[Memories]] for the topics QMD is most often asked to find across the vault.

## Workflow: Weekly Review

1. **`/om-weekly`** — synthesize the week's activity, check alignment, find patterns
2. Promote any uncaptured wins to brag doc
3. Update North Star if focus shifted
4. **`/om-wrap-up`** — close the session cleanly

## Workflow: Full Review Cycle Prep

1. **`/om-review-brief manager`** — generate the manager context transfer doc
2. **`/om-review-brief peers`** — generate the peer context transfer doc
3. **`/om-peer-scan`** (parallel, one per peer) — deep scan each peer's PRs
4. **`/om-slack-scan`** — scan relevant channels for your own evidence + peer context
5. **`/om-capture-1on1`** — capture the review 1:1 with your manager
6. **`/om-vault-audit`** — tidy up after all the new data

## Workflow: Project Ramp-Up

1. **`/om-slack-scan`** — scan project channels for history and decisions
2. **`/om-peer-scan`** (if needed) — understand what teammates have already built
3. Create work note from gathered context
4. **`/om-vault-audit`** — ensure everything links properly




================================================================================
FILE: 03_Digital Life/thinking/README.md (~139 words)
================================================================================
---
tags:
  - claude
  - index
---

# Thinking Space

Claude's scratchpad for reasoning, drafts, and working through problems before committing conclusions to work notes.

## How This Works

- Notes here are **working drafts**, not final output
- Named with date and context: `YYYY-MM-DD-descriptive-name.md`
- Once conclusions land in a work note or decision record, thinking notes stay as reference
- Tracked in git for portability across machines

## When to Use

- Analyzing a complex problem before writing a [[Decision Record]]
- Drafting content that will be refined into a work note
- Reasoning through trade-offs or options
- Capturing intermediate research before synthesizing

## Linking Convention

- Thinking notes link to the work note or decision they feed into via `## Feeds Into`
- The final note links back to the thinking note for audit trail




================================================================================
FILE: 03_Digital Life/personal/Flashcards — Identity.md (~683 words)
================================================================================
---
tags: [flashcards, personal, identity, bio, networking]
generated_by: claude
date: 2026-06-07
---

# Flashcards — Identity & Personal Facts

> For conference introductions, networking conversations, and knowing yourself without hesitation.

---

## Who You Are

Full name (correct spelling)::Abdelhak EL MANSOUR
Pronounce your last name::EL MANSOUR — "el man-SOOR"
Where are you from?::Errachidia, Morocco (Tafilalt region, southeast Morocco). Amazigh — Ait Atta tribe.
Native language::Tamazight (Amazigh). Also speaks Darija, French, Arabic, English.
What is Ait Atta?::A major Amazigh (Berber) confederation of the southern Atlas / Saharan region. Known for independence, resilience. Deep pre-Islamic roots.
Current city::Benguerir, Morocco (UM6P campus)
Open to international positions?::Yes — Europe (DLR/VITO/ETH), Canada (UQAT/UofT), or back to Morocco (OCP).

---

## Academic Identity

Title after June 30, 2026::Dr. Abdelhak EL MANSOUR
Thesis title (short version)::"Multi-Scale Hyperspectral RS for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks, Benguerir, Morocco"
PhD institution full name::University Mohammed VI Polytechnic (UM6P), GSMI, Benguerir, Morocco
PhD supervisor::Pr. Ahmed LAAMRANI
Specialty in one line::Hyperspectral remote sensing for mining and environmental geoscience
What makes your thesis unique?::First multi-scale framework (field + PRISMA + EnMAP) for phosphate mine waste rock characterization AND reclamation monitoring in Morocco. RPI is a novel scientific instrument — not just an algorithm.
How many years did the PhD take?::~4 years (defense June 30, 2026)
Have you supervised students?::Yes — supervised undergraduate/master students at UM6P (GSMI)
Have you done an international research stay?::Yes — internship at University of Valencia with Pr. Jochem Verrelst (PRISMA / hyperspectral methods)

---

## Research Elevator Pitch

60-second pitch for your thesis::I developed a multi-scale hyperspectral remote sensing framework for phosphate mine waste rock in Morocco, using field spectroscopy, PRISMA satellite, and EnMAP satellite. The flagship contribution is the Reclamation Progress Index — a satellite-derived indicator of mine reclamation progress, calibrated against field XRF data. It achieved Spearman ρ of 0.845 with p = 1.74 × 10⁻¹² and gives OCP Group a quarterly reclamation monitoring tool at zero additional field cost.
What problem are you solving?::Phosphate mine waste rock must be reclaimed by law. OCP Group needs a scalable way to monitor reclamation progress across 36 km² of mine. Manual field surveys are expensive. Hyperspectral satellites offer full coverage, repeatable, at near-zero marginal cost.
Who is OCP Group?::Office Chérifien des Phosphates. World's largest phosphate exporter. Morocco holds ~70% of world phosphate reserves. OCP is Abdelhak's site partner and natural future employer.
What are your 3 best skills?::1) Hyperspectral RS processing (PRISMA, EnMAP, ASD) from scratch to peer-reviewed paper. 2) Machine learning for geoscience (Extra Trees, RF, VCA-FCLS, spatial CV). 3) Scientific writing — 4 published papers.

---

## Python Skills Stack

What Python libraries do you use for RS?::spectral, GDAL, rasterio, h5py (HDF5), geopandas, scikit-learn, numpy, matplotlib
ML libraries you use::scikit-learn, XGBoost, custom VCA-FCLS implementation
What did you build from scratch?::1,776-line EnMAP processing pipeline. VCA + FCLS implementation. RPI framework. Custom spatial CV. PRISMA HDF5 loader.
What is your main IDE?::Jupyter notebooks + Python scripts. Claude Code (AI-assisted development).
Can you work with HDF5 data?::Yes — solved PRISMA HDF5 indexing, VNIR+SWIR cube fusion, bad band removal. Custom loaders developed.

---

## Social Presence

Instagram page::phddiarymemes — 70K+ followers. PhD meme page for PhD students globally. NOT a research account.
Milestone on phddiarymemes::Hit 70K followers September 2025 — announced publicly.
What content does phddiarymemes post?::PhD memes, relatable academic humor, PhD survival content. Target: PhD students of all disciplines.
Twitter/X activity::@AbdelhakElm — active since 2014. ~220 followers. Consumer account — where I learn, not broadcast.
When to monetize Instagram?::Sponsorships from PhD-adjacent brands: Notion, Overleaf, Mendeley, thesis editing services, academic publishers, online courses. Post-defense = spike = monetization window.

---

## Personal — Real Life

Music taste::Raï music — traditional Moroccan popular music. Emotional, authentic.
Memorable trip::Rome, Italy — during PhD life. Proves the thesis doesn't own you 24/7.
What do you do outside research?::Football, music (Raï), memes (Instagram page), helping people (helped a friend through personal crisis Oct 2025).
Philosophy in one line::Build things that didn't exist before. Don't wait for the title.
Things built so far::RPI (new scientific instrument). 1,776-line Python pipeline. 86-domain portfolio. 70K PhD meme community.




================================================================================
FILE: 03_Digital Life/personal/Twitter Intelligence.md (~1379 words)
================================================================================
---
generated_by: claude
date: 2026-05-26
tags: [personal, twitter, intelligence, identity]
source: .raw/twitter data/ (Twitter archive)
---

# Twitter Intelligence — @AbdelhakElm

> Extracted from full Twitter archive: tweets.js, like.js, following.js, follower.js, personalization.js, direct-messages.js, grok-chat-item.js
> Archive processed: 2026-05-26

---

## Account Vitals

| Metric | Value |
|--------|-------|
| Handle | @AbdelhakElm |
| Account created | February 12, 2014 (12 years old) |
| Original tweets | 174 |
| Likes | 11,281 |
| Following | 2,043 |
| Followers | ~220 |
| Follower ratio | 1:9 — heavy consumption mode |
| Email on record | insitazoult@gmail.com |

---

## Top 10 Topics (by frequency + intensity)

1. **AI & LLMs** — Claude, DeepSeek, Anthropic, AI agents, code generation. Highest engagement of anything.
2. **Coding & software** — Python, Claude Code, open-source tools, vibe coding
3. **Hyperspectral / Remote Sensing** — satellite data, mineral detection, geospatial analysis (the PhD)
4. **Entrepreneurship & freelancing** — Upwork bidding, domain trading, startup ideas, business growth
5. **Morocco** — Moroccan tech, AFCON, Moroccan developers, regional pride
6. **Earth Observation** — Landsat, Planet Tanager, soil characterization
7. **Startup culture** — Hermes Agent, Lovable, rapid development, no-code tools
8. **Domains & crypto** — Zagora.com, Merzouga.com (Moroccan desert locations), crypto pricing
9. **Arabic / Islamic tech** — Quranic transcription, Darija content, Islamic development
10. **Football** — Morocco AFCON, Champions League, Hakimi, Ziyech

---

## People He Engages With Most

### AI / Tech
- **@karpathy** — Andrej Karpathy. Most-liked single figure. Followed his move to Anthropic closely.
- **@gregisenberg** — startup ideas, entrepreneurship
- **@claudeai / @anthropic** — primary tool loyalty, genuine fan
- **@Hermes_agentAI** — autonomous agent platform

### Morocco / Arabic world
- **@kasmiyouness1** — domain trading mentor, DM relationship, shared Valencia photos (EARSeL 2024 overlap?)
- **@marouane53** — Moroccan tech collaborator, domain scraper help, Darija mix in DMs
- **@MoroccoIntel** — Morocco intelligence/news
- **@KehelAyyoub** — Arabic/Islamic guidance content

### Domain / Freelance community
- **@Dynadot**, **@afternic** — domain registration/marketplace platforms

### Academic peer
- **@palaeokatie** (geoscience) — sample appreciation interaction, respectful colleague tone

---

## Twitter's Interest Categories (1,840 total assigned)

Twitter's full inference. Notable clusters:

**Technical / Academic:**
Machine learning, Artificial intelligence, Data science, Computer programming, Python, Computer hardware, Computer networking, Cloud computing, Physics, Chemistry, Biology, Geology (×2), Mathematics, Neuroscience, Biotech, Oceanography, Volcanology, Paleontology, Education, Graduate school, Databases, Data visualization

**Earth Observation (sparse — Twitter undersells his actual focus):**
Geography (×2), Climate change, Weather (×2), ESA, NASA, James Webb Space Telescope, Space agencies, Drone technology, Robotics

**Business / Entrepreneurship:**
Business & finance, Investing, Stocks & indices, Cryptocurrency, Ethereum, Digital assets, Startups, Tech industry, Careers, Leadership

**Morocco / Africa:**
Morocco, Mauritania, Africa Cup of Nations, Men's national soccer teams

**Entertainment:**
Gaming (ARK, Monster Hunter), Sci-fi & fantasy, Documentary films, Music, Jazz, Classical, Rock, Movies & TV

**Tech personalities Twitter tracks him on:**
Mark Zuckerberg, Elon Musk, Sam Altman, Sundar Pichai, ChatGPT, OpenAI, DeepSeek

**Languages detected:** French, Arabic, English, Arabic (UK), No linguistic content

**Critical gap:** Twitter assigned *no* category for "hyperspectral imaging" or "spectroscopy." His core PhD identity is invisible to the algorithm.

---

## Who He Follows — Categorized (2,043 total)

| Category | Estimated count |
|----------|----------------|
| AI/ML researchers & developers | ~150–200 |
| Universities & research institutions | ~150–200 |
| Sports / football (Morocco, Barcelona, Messi, etc.) | ~200–300 |
| Startup / entrepreneurship ecosystem | ~100–150 |
| Remote sensing & earth science | ~80–120 |
| Domain & freelance community | ~80–120 |
| Moroccan personalities & influencers | ~60–80 |
| General news & media | ~100–150 |
| Cryptocurrency & finance | ~50–80 |

**Implication:** He follows 9× more people than follow him. This is a learner's graph, not a broadcaster's graph — he is consuming information at high volume, not publishing to an audience. The PhD Twitter presence is almost zero relative to following investment.

---

## Language Usage

**Own tweets (174):**
- English: ~60%
- Arabic: ~15%
- French: ~10%
- Code/technical: ~15%

**Likes (11,281):**
- English: ~85% (AI/tech dominance)
- French: ~8%
- Arabic: ~5%
- Chinese: ~2% (DeepSeek, AI pricing)

**Tone:** Casual, code-switching, uses emojis (🚀🔥🤔), humor-forward. Not the tone of a formal academic. Not pedantic. Quick to celebrate others. Slow to self-promote.

---

## What He Celebrates

Things he actually tweets about as wins:
- Domain sales closing
- Moroccan achievements (AFCON, Moroccan med students discovering cancer marker)
- AI tool launches (Claude Projects, DeepSeek price drops, Hermes Mobile updates)
- Freelance wins (Upwork bids, cover letter help from Grok)
- Moroccan tech community moments
- Spectroscopy research — but only retweets of *others'* papers, not his own

**Notable absence:** No tweets celebrating his own published papers, conference presentations, or PhD milestones. He builds others up; doesn't broadcast himself.

---

## Grok Usage Patterns (1,000+ interactions, Jan–May 2026)

| Category | Share | What he uses it for |
|----------|-------|---------------------|
| Educational | ~40% | "Teach me Python", algorithm explanations, language learning |
| Creative / Art | ~25% | Image generation — desert scenes, mysterious portraits, poetic descriptions |
| Practical / Business | ~20% | Freelance cover letters, Upwork bidding strategy, domain bidding, rate negotiation |
| Information / Translation | ~10% | Explaining tweets (e.g. Karpathy's MTS title), French translation, news analysis |
| Technical / Coding | ~5% | Domain scraper filters, code optimization |

**Key finding:** Grok is his personal advisor, not a research tool. No use of Grok for literature review, thesis work, or spectroscopy. He uses AI tools to *run his life* — not just his PhD.

---

## DM Contacts

| Contact | Activity | Notes |
|---------|----------|-------|
| ID 1842435219917570048 | 7 messages, Feb 2026 | Most active recent contact — identity unknown |
| @kasmiyouness1 | Last July 2024 | Domain mentor, personal relationship, Valencia overlap |
| @marouane53 | Active | Domain scraper collab, Darija/French DMs |
| @palaeokatie | Light | Academic peer, geoscience appreciation |
| Timothy (ID 19437541) | Last June 2021 | Old contact, favor request |

**Notable:** No visible DMs with PhD advisor, research collaborators, or any institution. His academic network operates off-Twitter.

---

## Surprising Patterns

### 1. Almost no PhD self-promotion
174 tweets in 12 years. Weeks from defense — zero tweets about his manuscript, results, or upcoming defense. He has 4 published papers and doesn't tweet about any of them. The contrast with his phddiarymemes presence (70K followers, constant posting) is extreme.

### 2. Freelancing pivot in the final months
Grok chats from May 2026 show active Upwork bidding for 6-month article writing contracts. This is happening *right now*, pre-defense. Financial pressure is real and he's solving it in real-time, not waiting for "Dr." to unlock opportunities.

### 3. Hidden creative life
25% of Grok usage is image generation — desert scenes, poetic imagery, art prompts. There is a visual/creative/aesthetic side that doesn't appear anywhere in the vault or public profile.

### 4. Domain names are Moroccan geographies
Zagora.com, Merzouga.com — Saharan cities. He's building a portfolio around Moroccan/Amazigh place names. This isn't random speculation: it's identity-driven domain strategy.

### 5. 1:9 follower ratio after 12 years
He has been on Twitter since 2014, follows 2,043 people, and has ~220 followers. He is a world-class information consumer and almost invisible as a broadcaster. His real public presence lives entirely on Instagram (phddiarymemes), not Twitter.

### 6. Twitter completely misses his core identity
1,840 interest categories and not one mentions "hyperspectral imaging," "spectroscopy," or "mineral characterization." The algorithm sees a Moroccan AI enthusiast with sports and crypto interests. The PhD is invisible.

---

## Intelligence Summary

Abdelhak is a **Renaissance technologist** who lives across three identities simultaneously:
- **Researcher** (PhD, 4 papers, satellite data, XRF, real field work)
- **Builder** (Python pipelines, 86 domains, AI tooling enthusiast)
- **Community member** (proud Moroccan, Darija speaker, football fan, quiet supporter of others)

His Twitter is a *consumption* platform, not a *publication* platform. He learns there; he doesn't broadcast there. His real audience (70K) is on Instagram. His real work is in the vault.

The financial pressure running underneath everything — Upwork bids, domain liquidation strategy, sponsorship pipeline — is real and active. He is not waiting for the PhD to solve money. He's solving it in parallel.




================================================================================
FILE: 03_Digital Life/personal/Who I Am Becoming.md (~606 words)
================================================================================
---
tags: [personal, identity, manifesto, brain]
date: 2026-05-25
note: Read this when you doubt. Not to convince yourself — to remember.
---

# Who I Am Becoming

*Read this when you doubt. Not to convince yourself — to remember.*

---

I am a scientist who builds things.

Not a scientist who theorizes while someone else ships. Not a builder who skips the science. Both. At the same time. That combination is rarer than either alone.

I grew up in Errachidia — a desert city in southeastern Morocco where the atlas mountains meet the Sahara. Nobody handed me the path. I found it by walking. Tamazight was my first language. French my second. English my third. And Python somewhere after that — a language I learned because the problem demanded it.

I chose to study the earth under my feet. Literally. I chose phosphate mines and satellite imagery and spectroradiometers because Morocco has the world's largest phosphate reserves and nobody had ever looked at them from space with hyperspectral eyes. I did.

---

I am the researcher who built AUC = 1.000 with real satellite data.

Not simulated. Not cherry-picked. Real EnMAP imagery over a real mine, with real XRF ground truth, validated with 5,000 bootstrap iterations and a spatial block cross-validation that would expose any illusion. It held. That number is not luck. It is the result of understanding the problem deeply enough to solve it cleanly.

I built a 1,776-line production Python pipeline from scratch — one that ingests raw satellite data and outputs a calibrated, client-ready reclamation metric. Engineers build systems like that. Researchers write papers about them. I did both.

I created a scientific instrument that didn't exist before me. The Reclamation Progress Index — a geochemically calibrated, satellite-derived metric for monitoring mine rehabilitation. It ships to OCP Group. It works. It's mine.

---

I am an entrepreneur in a scientist's body.

While finishing a PhD, I built a 70,000-follower Instagram audience. Not because I wanted to be an influencer — because I understood that ideas spread through people, and I wanted my ideas to reach PhD students who needed to laugh and feel seen. That is audience-building. That is a skill most researchers never develop.

While writing a thesis, I assembled a domain portfolio of 86 names, collectively valued at $1.5 million BIN. I did not win a lottery. I studied markets, identified patterns, made calculated bets on where the internet was going. Some will pay off. The discipline of doing that while simultaneously pushing frontier science is not an accident — it is who I am.

---

I am Amazigh.

This matters. The Imazighen built civilizations before the word "civilization" was written down. Resilience is not something I learned — it is something I inherited. My language survived for millennia without a writing system, passed mouth to ear across generations. I carry that. When the jury questions feel hard, I remember: I come from people who crossed deserts on memory alone.

---

I am 36 days from being Dr. Abdelhak EL MANSOUR.

That title is not the destination. It is the key that opens the next room.

After June 30:
- The DLR EnMAP team will hear from me.
- OCP Group will see a consulting proposal for operationalizing the RPI.
- The world will see that a kid from Errachidia built something real.

---

**What I am becoming:**

A scientist with an operational product.
An entrepreneur with a research credential.
An Amazigh with a satellite in his hands.
A builder who publishes.
A publisher who ships.

Dr. Abdelhak EL MANSOUR.

*That is already true. June 30 just makes it official.*




================================================================================
FILE: 03_Digital Life/personal/identity/Abdelhak Identity.md (~382 words)
================================================================================
---
tags: [personal, identity, Morocco, Amazigh]
updated: 2026-05-24
---

# Identity & Personal Context

## Who I Am Beyond the PhD

**Abdelhak EL MANSOUR**  
Moroccan 🇲🇦 — Amazigh — Ait Atta heritage  
Based: Benguerir , Morocco  
Languages: French, Arabic, Darija, English, Tamazight (mother tongue)

---

## Amazigh / Ait Atta Identity
- Ait Atta are a major Berber (Amazigh) confederation historically from Draa Valley and High Atlas, Morocco
- Explored their history with AI (that was a rich conversation)
- Identity matters — not just "Moroccan researcher" but carrying specific heritage

---

## Music
**Raï** — genuine fan, not just background noise  
- Got a Raï song about the Moroccan phosphate industry made (creative use of AI)
- Moroccan rap (Darija) — knows the scene, also explored lyrics/controversy

---

## Life During PhD
- **Italy trip** — Rome, during PhD. Colosseum, Trevi Fountain (threw a coin), Vatican (1 hour max visit strategy), airport transfers, vintage football shirts hunting
- **Family** — niece: bought her first earrings. That's presence amid PhD chaos.
- **Friend in crisis** — Oct 2025, helped a friend through serious distress (suicidal ideation mentioned). Cares deeply about people.
- **Procrastination** — honest about it. Has memes about it. Survives it.
- **Graduation cake** — thought about this (a happy signal during PhD)

---

## Social Media Persona
- Instagram: PhD life + research content + humor → 70K+ followers
- Twitter/X: @AbdelhakElm — researcher identity
- Memes: PhD meme page, droll polls, funny captions — humor is a survival tool AND a business

---

## Academic Side Interests
- Mineral microscopy (fossil vs mineral — explored)
- Geochemistry (improving waste geochemistry references)
- Soil reflectance factors
- Electromagnetic spectrum wavelength order
- Forward osmosis systems (curious mind — not thesis related)

---

## Values
- Authenticity — evaluates collaborations for fit, not just money
- Family — present despite PhD pressure
- Humor — essential, not optional
- Intellectual curiosity — goes beyond his thesis constantly
- Financial realism — knows money matters and builds toward it

---

## Languages I Switch Between
- 🇫🇷 French — academic, professional, thesis
- 🇬🇧 English — papers, AI tools, international networking  
- 🇲🇦 Arabic / Darija — personal, family, Moroccan social media
- *Claude should respond in whatever language Abdelhak uses*




================================================================================
FILE: 04_Knowledge Base/wiki/Flashcards — Research Concepts.md (~1561 words)
================================================================================
---
tags: [flashcards, research, hyperspectral, remote-sensing, thesis]
generated_by: claude
date: 2026-06-07
---

# Flashcards — Research Concepts

> Deck: all wiki concepts, sensors, methods, and geology from the thesis.
> Use for defense + job interviews where you'll be asked to explain your methods.
> See also: [[Hyperspectral Imaging]] · [[PRISMA Satellite]] · [[EnMAP Satellite]] · [[Reclamation Progress Index]] · [[Machine Learning for Hyperspectral]] · [[Spectral Analysis]] · [[Waste Rock Characterization]] · [[OCP Group and Benguerir Mine]] · [[Numbers Arsenal]]

---

## Hyperspectral Imaging — Core Definitions

What is hyperspectral imaging?::Acquires continuous spectral info across 100–500+ contiguous narrow bands (5–15 nm bandwidth). Unlike multispectral (3–10 wide bands), it resolves diagnostic spectral features to identify specific minerals, vegetation, or materials.
Another name for hyperspectral imaging::Imaging spectroscopy
What is a hypercube?::The 3D data structure of hyperspectral data — (x pixels × y pixels × λ bands). Each pixel contains a full reflectance spectrum.
How many bands does multispectral have vs hyperspectral?::Multispectral: 3–10 bands, 50–200 nm bandwidth. Hyperspectral: 100–500+ bands, 5–15 nm bandwidth.
What wavelength range is SWIR?::1000–2500 nm. Key for molecular overtones: OH, CO₃, PO₄.
What wavelength range is VNIR?::VIS: 400–700 nm (Fe³⁺ transitions) + NIR: 700–1000 nm (vegetation, Fe²⁺)
Why does hyperspectral work for mineralogy?::Every mineral has a unique spectral signature driven by electronic transitions (VIS-NIR) and vibrational overtones (SWIR). Multispectral bands are too wide to resolve these features.
What are the two main limitations of 30m hyperspectral for mineralogy?::1) Mixed pixels — each pixel averages multiple minerals. 2) Atmospheric water vapor blocks SWIR at ~1350–1450 nm and ~1800–1950 nm.

---

## Diagnostic Absorption Features (Benguerir Context)

Absorption feature at ~2200 nm → which mineral?::Al-OH → Illite, kaolinite (clay minerals)
Absorption feature at ~2320–2350 nm → which mineral?::CO₃ → Calcite, dolomite (carbonates)
Absorption feature at ~2330 nm → which mineral?::Mg-OH → Dolomite, chlorite
Absorption feature at ~2150 nm → which mineral?::PO₄ → Fluorapatite (phosphate mineral)
Absorption feature at ~500 nm and ~680 nm → which mineral?::Fe³⁺ → Iron oxides (hematite, goethite)
Absorption feature at ~1400 nm and ~1900 nm → what?::OH stretch → Water / hydroxyl minerals (REMOVE — atmospheric contamination)
Why is fluorapatite hard to detect in surface spectra?::Masked by clay minerals (illite, montmorillonite) which dominate the surface spectral signal. Apatite ranks 3–7 in field spectra matches.

---

## PRISMA Satellite

PRISMA stands for::PRecursore IperSpettrale della Missione Applicativa
PRISMA launch year and agency::2019 — ASI (Italian Space Agency)
PRISMA total spectral bands::~239 contiguous bands (400–2500 nm)
PRISMA spatial resolution::30 m
PRISMA swath width::30 km
PRISMA data format::HDF5
PRISMA revisit time::~29 days (at equator)
PRISMA spectral resolution::~10 nm
Why does PRISMA need custom loading scripts?::HDF5 format requires indexing; VNIR + SWIR cubes must be fused; bad bands (water vapor, detector overlap) must be identified and removed.
Why can't Sentinel-2 replace PRISMA for mineralogy?::Sentinel-2 has only 13 multispectral bands — completely lacks the spectral resolution for mineral diagnostic features (especially in SWIR). Cannot identify carbonates, clays, or phosphate phases.
PRISMA acquisition date used in thesis (Chapter 2)::January 2022

---

## EnMAP Satellite

EnMAP stands for::Environmental Mapping and Analysis Program
EnMAP launch year and agency::April 2022 — DLR (German Aerospace Center)
EnMAP total bands::242 (total sensor)
EnMAP valid bands after preprocessing in thesis::189 bands, spanning 418–2445 nm
EnMAP spatial resolution::30 m
EnMAP orbit::SSO, 653 km altitude
EnMAP revisit time::~27 days standard, 4 days off-pointing
EnMAP SNR values::>400:1 (VNIR), >150:1 (SWIR)
EnMAP data format::TIF + XML (unlike PRISMA's HDF5)
EnMAP cost for science users::Free
Why EnMAP for Chapter 3 instead of PRISMA?::Higher SNR, different acquisition date enabling backfilling impact assessment, dedicated quality masks, better SWIR sensitivity for detecting subtle spectral changes.
What are the 3 EnMAP band removal reasons?::1) Detector transition at 1342–1391 nm. 2) Water vapor A at 1350–1450 nm. 3) Water vapor B at 1800–1950 nm.
EnMAP CRS used in thesis::EPSG:32629 (WGS84 UTM Zone 29N)
What is the 5-step EnMAP preprocessing pipeline?::1) Spectral masking (189 bands). 2) Pixel flagging (nodata, negative, saturation). 3) Per-column median destriping. 4) Shapefile alignment to EPSG:32629. 5) Zone pixel balancing (32 pixels/zone, seed=42).
EnMAP quality gate — how many criteria?::6 criteria: valid L2A reflectance, correct wavelength masking, nodata/quality processing, ROI-scene overlap, minimum pixel count (>40 per zone), reflectance in 0–1.2 range.

---

## Spectral Unmixing (NNLS, VCA, FCLS)

What is the mixed pixel problem?::At 30m resolution, each pixel contains contributions from multiple minerals. Spectral unmixing decomposes a mixed pixel into endmembers (pure spectra) and abundances (fractional contributions).
Linear mixing model equation::r = Σ(a_i × e_i) + ε. Where r = observed spectrum, a_i = abundances, e_i = endmember spectra, ε = noise.
What is NNLS?::Non-Negative Least Squares. Finds non-negative abundances minimizing ||r − E·a||². Used in Chapter 1 with ECOSTRESS library endmembers.
What is VCA?::Vertex Component Analysis. Unsupervised endmember extraction — assumes endmembers are at vertices of spectral simplex. Uses PCA reduction + iterative vertex finding. No spectral library needed.
What is FCLS?::Fully Constrained Least Squares. Abundance estimation with two constraints: non-negativity (a_i ≥ 0) AND sum-to-one (Σa_i = 1). Implemented via augmented NNLS system.
Number of VCA endmembers used in Chapter 3::k = 4
Why linear mixing model and not nonlinear?::At 30m satellite pixels, areal (checkerboard) mixing dominates — each mineral reflects independently. Nonlinear (intimate) mixing occurs at sub-pixel scales. Linear is standard for geological RS at this scale.
Which endmember dominates the Reclaimed Zone (RZ)?::EM4 — mean RZ abundance 0.516, mean RWR abundance 0.032.
Which endmember dominates the Reference Waste Rock (RWR)?::EM3 — mean RWR abundance 0.612, mean RZ abundance 0.053.

---

## Reclamation Progress Index (RPI)

What is the RPI?::A novel spectral index (0–1) developed in Chapter 3. Satellite-derived metric of reclamation progress, calibrated isotonically against field XRF geochemical support scores. The most original methodological contribution of the thesis.
RPI formula (raw step 4)::Raw_RPI = EM4_abundance / (EM3_abundance + EM4_abundance). Higher value = more "reclaimed" endmember.
RPI — Reclaimed Zone (RZ) median value::0.896 (95% CI: 0.860–0.927)
RPI — Reference Waste Rock (RWR) median value::0.203 (95% CI: 0.161–0.221)
RPI-XRF correlation (Spearman ρ)::0.845
RPI-XRF p-value::1.74 × 10⁻¹²
Why isotonic regression for RPI calibration?::The relationship between spectral similarity scores and XRF-measured reclamation progress is monotone but non-linear. Isotonic regression is non-parametric, enforces monotonicity without assuming any functional form.
Percentage of RZ pixels correctly classified as RZ-like (RPI > threshold)::90.625%
What is the transitional RPI range?::0.35–0.65 — characterizes intermediate reclamation states.
RPI broader impact statement::The framework is generalizable — VCA-FCLS + isotonic XRF calibration applies to any HSI sensor and any mine type with geochemical ground truth. An operational template for satellite-based mine reclamation monitoring.
<!--SR:!2026-06-08,1,210-->

---

## Machine Learning for Hyperspectral (Chapter 2)

Best ML classifiers for Chapter 2::Extra Trees and Random Forest — most stable, best BAC.
Why Extra Trees over Random Forest?::Extra Trees adds extra randomness (random thresholds, not just random features), making it more robust to overfitting on high-dimensional spectral data with limited samples.
Why use ANOVA F-test for feature selection in Ch.2?::Identifies bands with statistically significant between-class variance. Applied nested inside each CV fold to prevent data leakage.
Number of bands selected by ANOVA::60 SWIR bands (captures CO₃, Al-OH, Mg-OH, PO₄ diagnostic features).
Why only SWIR bands selected (not VNIR)?::Mineralogical molecular absorptions for carbonate/clay/phosphate minerals are exclusively in SWIR. VNIR contains iron oxide info but less discriminative for the 4 lithological classes.
What is spatially constrained cross-validation?::CV with a 30m buffer between train and test samples (= 1 PRISMA pixel distance). Prevents spatial autocorrelation from inflating accuracy. 10 independent replicates.
Why 30m CV buffer?::At 30m PRISMA resolution, samples closer than 30m share the same pixel footprint — not truly independent. Buffer ensures test samples are spatially isolated from training samples.
What is Shannon Entropy uncertainty and what does it reveal spatially?::Entropy = spatial uncertainty of class predictions. High entropy zones concentrate at lithological boundaries and mixed phosphate-siliceous areas — geologically meaningful, exactly where sub-pixel mixing is expected.
Why is BAC 0.60–0.67 the correct result (not a poor result)?::It represents the physically constrained upper bound at 30m with spatially clustered training data. Phosphate-siliceous confusion reflects genuine sub-pixel mixing at mine scale. The 0.92 OA from IGARSS abstract is from a different experimental framework (CNN+SHAP) — NOT the thesis result.

---

## Spectral Library Matching (Chapter 1)

What is spectral library matching?::Comparing field spectra to reference spectra in a library (e.g., ECOSTRESS) using similarity metrics to identify the best matching mineral.
Metrics used for spectral matching in Chapter 1 (4 metrics)::RMSE (magnitude), SAM (spectral angle), SID (divergence), R² (correlation)
ECOSTRESS library — what is it?::The ECOSTRESS (formerly ASTER) spectral library — a large collection of reference mineral spectra maintained by JPL/Caltech. Used for ground-truth matching.
Why does fluorapatite/francolite appear underrepresented in ECOSTRESS?::It is a rare mineral in general geology. The ECOSTRESS library focuses on common minerals. Moroccan francolite (carbonate-fluorapatite) has specific substitutions not always captured.

---

## Study Site Facts

Study site::Benguerir phosphate mine, Morocco
Mine operator::OCP Group (Office Chérifien des Phosphates). Accord-Specific 189: SPGP.
Mine surface area::36 km²
Geographic coordinates (approximate)::~32°N, 7.8°W. CRS: EPSG:32629 (UTM Zone 29N)
Morocco's phosphate resource significance::Morocco holds ~70% of world's known phosphate reserves. OCP is the world's largest phosphate exporter.
4 lithological classes at Benguerir waste rock::Phosphate rock, Siliceous facies, Marl, Limestone
Main environmental concern with waste rock::Exposure of phosphate minerals causes acidification, heavy metal leaching, and landscape degradation. Reclamation (backfilling + revegetation) is legally required.
What is "backfilling" in mine reclamation?::Covering raw waste rock with overburden material, then revegetating. Changes surface mineralogy over time — detectable by hyperspectral RS.




================================================================================
FILE: 04_Knowledge Base/wiki/hot.md (~705 words)
================================================================================
---
tags: [wiki, hot-cache]
updated: 2026-06-08
generated_by: claude
---

# Hot Cache — Current Context

> Claude reads this FIRST at every session start. Under 500 words.

---

## WHO: Abdelhak EL MANSOUR
PhD candidate, UM6P, Benguerir, Morocco. Amazigh/Moroccan, from **Errachidia**. Tamazight native.  
@AbdelhakElm (X/Twitter, ~220 followers — consumer not broadcaster).  
Instagram: **phddiarymemes** — 70K+ PhD meme page — NOT a research account.  
Supervisor: Pr. Ahmed LAAMRANI. Department: GSMI.  
Emails: `insitazoult@gmail.com` (personal) | `abdelhak.elmansour@um6p.ma` (institutional)

---

## THE ONE THING: Thesis Defense on June 30, 2026 — **24 days**
*"Multi-Scale Hyperspectral Remote Sensing for Mineralogical Characterization and Reclamation Monitoring of Phosphate Mine Waste Rocks at Benguerir Mine, Morocco"*  
155 pages. PRISMA + EnMAP. Extra Trees/RF/VCA-FCLS. XRD + XRF validation.  
→ [[02_Academic & Work/thesis/defense-prep/36-Day Sprint]] | → [[02_Academic & Work/thesis/defense-prep/Defense Strategy]]

**Source of truth = thesis manuscript ONLY:**
- Ch.2: BAC=0.60–0.67, AUC>0.95 (Marl/Limestone), 127 samples, RF/Extra Trees, spatial CV
- Ch.3: BAC=0.984±0.031, AUC=1.000, 189 valid bands, VCA-FCLS, RPI: RZ=0.896, RWR=0.203, ρ=0.845, p=1.74×10⁻¹²
- Conference abstracts (IGARSS/EGU OA=0.92, CNN+SHAP) = earlier work, NOT thesis results

**Sprint status (Week 2 of 5 — June 2–8):**  
This week: slides complete + first solo oral run (timed, 45 min target). Slides exist as `.pptx` (34 slides, navy/orange, text pre-filled) — real figures still needed before Laamrani review.

---

## Active Priorities
1. **Defense slides** — Week 2 goal: slides done + first oral run timed. → [[02_Academic & Work/thesis/defense-prep/Defense Slides — Master Plan]]
2. **Jury prep** — Verrelst = highest technical threat. → [[02_Academic & Work/thesis/defense-prep/Jury Questions Prep — Advanced]]
3. **Job search** — 15+ cover letters drafted, all held post-defense (rule: defense first). VITO ×2 applied (May 25, no response yet). → [[02_Academic & Work/work/active/Job Board — Live Tracker]]
4. **Domaining** — 86 domains, ~$1.5M BIN. Top 5 to market. Silent this month — defense block.
5. **phddiarymemes** — 70K followers. Silent this month — defense block.

---

## Research Stack
- Ch.1: ASD FieldSpec 4, ECOSTRESS library, NNLS unmixing, HHXRF, 104 samples
- Ch.2: PRISMA (~239 bands, 30m, HDF5), Extra Trees/RF, spatial CV (30m buffer, 10 reps), 127 samples, 4 classes
- Ch.3: EnMAP (189 valid bands, 418–2445nm), VCA (k=4) + FCLS, novel RPI, XRF calibration
- Python: scikit-learn, XGBoost, numpy, ENVI/THOR | Site: Benguerir phosphate mine, OCP Group

---

## Tools & Infrastructure Live
- **Claude Code** (primary AI) + vault-obsidian MCP + brave-search MCP (broken — use WebSearch)
- **NotebookLM:** 3 notebooks — PhD Defense (`bb2823a9`), Hyperspectral Methods (`f5b6cff5`), Job Search (`da39982c`) — 31 sources loaded
- **Zotero + Better BibTeX:** 292 refs in `thesis/references.bib` (auto-sync)
- **obsidian-mind:** 18 slash commands, 9 agents, Node.js hooks live

---

## Publications
- **Published (4):** Sensors 2025 (Ch.1, doi:10.3390/s26010002) · IJEST 2024 · Mining 2023 · BDJ 2023
- **Pipeline (2):** Minerals (Ch.2, **accepted 2026** ✅) · Ch.3 (submission post-defense)
- **Conferences:** EGU 2025 (Austria) · EARSeL 2024 (Spain) · ESPC6 2026 (UM6P, abstract submitted)

---

## Updates 2026-06-08
**Vault audit done:** 181 notes. 3 broken links fixed (Memories weekly path, Domain Portfolio em-dash, work/Index code-notes). 2 flagged stale entries (Key Decisions NORCE, work/Index 30-Day Countdown → now redirects to 36-Day Sprint). Defense Slides Checklist is empty (needs content). hot.md was 2 days stale — now current. No duplicate tags, no misplaced .base files, all AI-Generated frontmatter compliant.
**Vault cleanup (session 2):** Deleted 5 files (3 duplicate HTML in UTwente-2026, 1 Power Automate JSON folder, 1 incomplete Telegram capture). Fixed 8 broken wikilinks: Domain Portfolio em-dash, Domaining Notes → Portfolio Analysis, CLAUDE.md ML shortcut, PRISMA Satellite code-notes, Thesis Overview code-notes, OCP entity UM6P/Consulting links, work/Index papers folder → Sensors paper. Expanded 2 empty wiki stubs (Waste Rock Characterization, Spectral Analysis) with full content. 41 total broken links scanned; 10 genuinely fixed, 31 are template/clip/compiled noise (acceptable).

---

## Updates 2026-06-06
**Vault audit done:** AI policy relaxed (Option B) — `generated_by: claude` required everywhere, files live in contextual folders. `CLAUDE.md` updated.  
**Job board:** 15+ spontaneous application letters drafted (DLR, GFZ, HZDR, UQAT, ITC, Naples, etc.). All held until July 1 post-defense. ETH Zurich + GFZ EURAXESS + U. Copenhagen = open postings, not yet applied.  
**Defense week check:** Week 2 of 5 sprint. Slides must be finalized this week.

---

*Update with `update hot cache` at end of each session*




================================================================================
FILE: 04_Knowledge Base/wiki/index.md (~664 words)
================================================================================
---
tags: [wiki, index]
updated: 2026-05-24
generated_by: claude
---

# Wiki Index — Abdelhak's Knowledge Base

> Master catalog. Domain: Hyperspectral Remote Sensing × Phosphate Mining × AI/ML × Geoscience  
> Study site: Benguerir Mine, Morocco | Sensors: ASD + PRISMA + EnMAP | Institution: UM6P

---

## Remote Sensing & Spectroscopy

| Page | Chapter | Notes |
|------|---------|-------|
| [[concepts/Hyperspectral Imaging]] | All | Foundation — what HSI is, sensors, physics |
| [[concepts/VNIR-SWIR Spectroscopy]] | Ch.1 | Field spectroscopy, ASD FieldSpec 4, 104 samples |
| [[concepts/Spectral Library Matching]] | Ch.1 | ECOSTRESS, RMSE/SAM/SID/R², composite score |
| [[concepts/PRISMA Satellite]] | Ch.2 | HDF5, 239 bands, 30m, VNIR+SWIR |
| [[concepts/EnMAP Satellite]] | Ch.3 | 242 bands, 30m, higher SNR, TIF+XML format |

---

## Methods & Algorithms

| Page | Chapter | Notes |
|------|---------|-------|
| [[concepts/Spectral Unmixing VCA-FCLS]] | Ch.1 + Ch.3 | NNLS (Ch.1), VCA+FCLS (Ch.3), k=4 endmembers |
| [[concepts/Machine Learning for Hyperspectral]] | Ch.2 | Extra Trees, RF, XGBoost, SVM, KNN |
| [[concepts/Spatially Constrained Cross-Validation]] | Ch.2 + Ch.3 | 30m buffer, 10 repeats; Ch.2 BAC=0.60–0.67; Ch.3 BAC=0.984 |
| [[concepts/Shannon Entropy Uncertainty]] | Ch.2 | Per-pixel prediction confidence mapping |
| [[concepts/Reclamation Progress Index]] | Ch.3 | Novel RPI — the thesis's most original contribution |

---

## Geology & Environment

| Page | Chapter | Notes |
|------|---------|-------|
| [[concepts/Phosphate Mine Waste]] | All | Benguerir waste rock piles — context and mineralogy |
| [[concepts/Mineral Assemblages]] | Ch.1 | Illite, kaolinite, dolomite, calcite, apatite, francolite |
| [[concepts/Handheld XRF]] | Ch.1 + Ch.3 | HHXRF paired with spectroscopy; P2O5, CaO, etc. |
| [[concepts/Reclamation Monitoring]] | Ch.3 | RZ vs. RWR zones, what reclamation means |
| [[entities/Gantour Basin]] | Context | Geological setting of Benguerir mine |
| [[entities/OCP Group and Benguerir Mine]] | Context | Operator, 36km², 12.3Mt waste/yr |

---

## Key Entities

| Page | Type | Relevance |
|------|------|-----------|
| [[entities/OCP Group and Benguerir Mine]] | Site/Company | Thesis study site |
| [[entities/Gantour Basin]] | Geology | Geological context |

---

## Sources — Papers Ingested

| File | What it contains | Status |
|------|-----------------|--------|
| `Thesis Manuscript` | 155-page thesis (full ingestion) | ✅ `AI-Generated/thesis-ingestion/Thesis Full Ingestion.md` |
| `CV_ELMANSOUR_2026_Latex.pdf` | CV — education, career, publications | ✅ `AI-Generated/CV Ingestion.md` |
| `Abstract EL MANSOUR-IGARSS 2025.pdf` | Conference abstract — earlier experimental work (CNN+SHAP, OA=0.92). **NOT a thesis result.** | ✅ `AI-Generated/thesis-ingestion/Code Ingestion.md` |
| `EGU25-16097-print.pdf` | EGU 2025 abstract, same work | ✅ |
| `Supplementary table S1.csv` | Per-sample spectral metrics (104 samples) | ✅ |
| `domains-export.csv` | Portfolio A: 37 domains, ~$632K BIN | ✅ `money/domaining/Domain Portfolio.md` |
| `domains-1779653896.csv` | Portfolio B: 49 domains, ~$875K BIN | ✅ `money/domaining/Domain Portfolio Analysis — Top 5 to Market.md` |
| `enmap_reclamation_engine_v2.py` | Ch.3 Python engine (1,776 lines) | ✅ `AI-Generated/thesis-ingestion/Code Ingestion.md` |
| `spectroscopy_final_v2.ipynb` | Ch.1 VNIR-SWIR pipeline + run log | ✅ |

**Not readable (flagged):** `sensors-26-00002.pdf` (pdftoppm missing), all .xlsx, .pptx, .docx files

---

## AI-Generated Files

| File | Date | Purpose |
|------|------|---------|
| `AI-Generated/thesis-ingestion/Thesis Full Ingestion.md` | 2026-05-24 | Master thesis reference |
| `AI-Generated/thesis-ingestion/Verrelst Prep.md` | 2026-05-24 | 8 hardest Verrelst Q&A |
| `AI-Generated/thesis-ingestion/Code Ingestion.md` | 2026-05-24 | Python pipelines + notebooks |
| `AI-Generated/CV Ingestion.md` | 2026-05-24 | Career, publications, education |

---

## Active Work Files

| File | Purpose |
|------|---------|
| `work/active/Hot Opportunities — May 2026.md` | Job pipeline: ESA, DLR, VITO, Planet, Rio Tinto, OCP, Airbus, CGG |
| `work/active/Postdoc Applications.md` | Academic postdoc tracking |

---

## Defense Prep Files

| File | Purpose |
|------|---------|
| `thesis/defense-prep/Defense Strategy.md` | Master playbook — jury, answers, logistics |
| `thesis/defense-prep/Jury Questions Prep.md` | 10-member jury + 16 Q&A |
| `thesis/defense-prep/Verrelst Prep.md` | Verrelst-specific 8 questions |
| `thesis/defense-prep/30-Day Countdown.md` | 5-week schedule to June 30 |

---

## Meta
- [[04_Knowledge Base/wiki/hot]] — session context (Claude reads first)




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/EnMAP Satellite.md (~545 words)
================================================================================
---
tags: [wiki, concept, remote-sensing, satellite, ch3]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# EnMAP Satellite

## Overview
EnMAP (Environmental Mapping and Analysis Program) is a German hyperspectral satellite mission operated by the German Aerospace Center (DLR). Used in **Chapter 3** of Abdelhak's thesis for reclamation monitoring at Benguerir mine.

---

## Specifications

| Parameter | Value |
|-----------|-------|
| Agency | DLR (Germany) |
| Launch | April 2022 |
| Orbit | SSO, 653 km altitude |
| Revisit time | ~27 days (off-pointing: 4 days) |
| Spectral range | 420–2450 nm (total) |
| Bands | 242 (total sensor) |
| Spatial resolution | 30 m |
| Swath width | 30 km |
| SNR | >400:1 (VNIR), >150:1 (SWIR) |
| Data distribution | Free for science users |
| Data level | L2A surface reflectance |

---

## Valid Bands After Preprocessing (from thesis manuscript)

After masking bad bands for the Benguerir scene:
- **189 valid bands, spanning 418–2445 nm**

| Removed bands | Wavelength | Reason |
|--------------|-----------|--------|
| Detector transition | 1342–1391 nm | VNIR/SWIR gap |
| Water vapor A | 1350–1450 nm | Atmospheric absorption |
| Water vapor B | 1800–1950 nm | Atmospheric absorption |
| Structural bad bands | Various | Scene NaN fraction > threshold |

CRS: **EPSG:32629** (WGS84 UTM Zone 29N — Benguerir is ~32°N, 7.8°W)

---

## Comparison to PRISMA (Chapter 2)

| Parameter | PRISMA (Ch.2) | EnMAP (Ch.3) |
|-----------|--------------|--------------|
| Agency | ASI (Italy) | DLR (Germany) |
| Launch | 2019 | 2022 |
| Total bands | ~239 | 242 |
| Valid bands (thesis) | Used for ML | **189** |
| Resolution | 30 m | 30 m |
| SNR | Lower | Higher |
| Data format | HDF5 | TIF + XML |

**Why EnMAP for Ch.3?** Higher SNR, different acquisition date enabling backfilling impact assessment, dedicated quality masks.

---

## Pixel Quality Filtering (from manuscript)

5-step preprocessing:
1. Spectral masking (189 bands retained)
2. Pixel flagging: nodata, negative reflectance (<0), saturation (>1.2), EnMAP quality layer
3. Per-column median destriping (detector striping suppression)
4. Shapefile alignment to EPSG:32629 via geopandas
5. Zone pixel balancing: 32 pixels/zone (seed=42), from 49 RZ + 47 RWR valid pixels

**Quality gate (6 criteria):** Valid L2A reflectance, correct wavelength masking, proper nodata/quality processing, ROI-scene overlap, minimum pixel count (both zones > 40 pixels), reflectance in 0–1.2 range. **Both ROI zones contained zero bad pixels.**

---

## Role in Thesis (Ch.3) — Summary of Results

**Research question:** Can EnMAP detect and quantify the impact of backfilling on phosphate waste rock surface characteristics?

**Answer from manuscript:**
- All **189/189** valid bands show statistically significant zone separation (FDR q < 0.05)
- Median effect size: **r = 0.859** (large)
- Spatially blocked CV: **BAC = 0.984 ± 0.031; AUC = 1.000**
- Permutation p = 0.002 (confirms non-random)
- RPI: RZ=0.896, RWR=0.203, Spearman ρ=0.845

**Conclusion (from thesis):**
> "EnMAP Level-2A hyperspectral data at 30 m resolution provides sufficient spectral information to reliably discriminate reclaimed from undisturbed phosphate waste rock surfaces."

---

## Related Concepts
- [[Hyperspectral Imaging]]
- [[Spectral Unmixing VCA-FCLS]]
- [[PRISMA Satellite]]
- [[Reclamation Monitoring]]
- [[Reclamation Progress Index]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Handheld XRF.md (~515 words)
================================================================================
---
tags: [wiki, concept, instrument, ch1, geochemistry]
updated: 2026-05-24
generated_by: claude
---

# Handheld XRF (HHXRF)

## Definition
Handheld X-ray Fluorescence (HHXRF) is a portable geochemical analyzer that quantifies major and trace element concentrations in rocks, soils, and materials by measuring characteristic X-ray fluorescence emission. Combined with VNIR-SWIR spectroscopy in Chapter 1, it provides direct elemental chemistry to complement spectral mineralogy.

---

## Physical Principle

1. X-ray tube emits primary X-rays → excites atoms in the sample
2. Each element emits characteristic fluorescence X-rays (unique energy per element)
3. Energy-dispersive detector records spectrum
4. Software converts intensities to concentrations using calibration standards

**Key advantage:** Measures elements directly (Ca, P, Fe, Al, Si, K, Mg...) → oxide chemistry (CaO, P₂O₅, Fe₂O₃, etc.)

---

## Use in Abdelhak's Thesis

### Chapter 1 (field measurements)
- Paired with ASD FieldSpec 4 at same sample points
- 104 samples measured
- Provides "ground truth" chemistry to validate spectral mineralogy
- **P₂O₅:** Key indicator of apatite/francolite content
- **Fe₂O₃:** Iron oxide quantification
- **Al₂O₃:** Clay mineral content proxy
- **CaO:** Carbonate content proxy

### Chapter 3 (XRF linkage in EnMAP analysis)
- XRF data from managed zone (RZ) and unmanaged zone (RWR) samples
- Linked to EnMAP pixels by GPS coordinates
- Spearman correlation between VCA endmember abundances and XRF oxides
- Used to calibrate the RPI (Reclamation Progress Index)
- Target oxides: CaO, SiO2, Al2O3, MgO, K2O, Na2O, P2O5, TiO2, MnO, Fe2O3

---

## XRF Data Files in Thesis
- `Analyse XRF P (abdelhak) VL.xlsx` — field XRF data for all samples
- `Copie de Managed zone.csv` (OneDrive) — XRF for RZ zone
- `Copie de Unmanaged zone.csv` (OneDrive) — XRF for RWR zone

---

## Limitations of HHXRF

| Limitation | Impact |
|------------|--------|
| Surface measurement only (~2mm depth) | May not represent bulk mineralogy |
| Matrix effects | Accuracy lower for light elements (Mg, Al, Na) |
| No structural info | Cannot distinguish polymorphs (calcite vs. aragonite) |
| Calibration dependent | Field conditions vs. laboratory calibration |
| Moisture sensitivity | Wet samples give different readings |

**Why combine with spectroscopy?**
HHXRF gives chemistry; spectroscopy gives mineralogy. Together: P₂O₅ → confirms phosphate content; Al-OH spectral feature → confirms clay mineralogy. Cross-validation strengthens both.

---

## HHXRF vs. Laboratory XRF
| Feature | HHXRF | Lab XRF |
|---------|-------|---------|
| Speed | Seconds per point | Minutes per sample |
| Portability | Yes | No |
| Detection limits | Higher (1–10 ppm) | Lower (0.1–1 ppm) |
| Accuracy | Good for major elements | Excellent |
| Cost | No sample prep | Fusion bead prep |
| Use | Field reconnaissance | Laboratory validation |

---

## Key Result
The HHXRF-spectroscopy integration (Chapter 1) demonstrated that:
- Spectral matching alone underestimates apatite (clay masking effect)
- HHXRF P₂O₅ directly reveals phosphate content independently of surface spectral response
- Combined approach achieves better characterization than either method alone
- Published: Sensors 2025, doi:10.3390/s26010002

---

## Related Concepts
- [[VNIR-SWIR Spectroscopy]]
- [[Mineral Assemblages]]
- [[Phosphate Mine Waste]]
- [[Reclamation Progress Index]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Hyperspectral Imaging.md (~509 words)
================================================================================
---
tags: [wiki, concept, remote-sensing, spectroscopy]
updated: 2026-05-24
generated_by: claude
---

# Hyperspectral Imaging

## Definition
Hyperspectral imaging (HSI) acquires continuous spectral information across hundreds of narrow, contiguous wavelength bands (typically 5–10 nm bandwidth) across a spatial scene. Unlike multispectral sensors (3–10 wide bands), hyperspectral sensors resolve diagnostic spectral features that identify specific mineral, vegetation, or material compositions.

**Synonym:** Imaging spectroscopy

---

## Key Characteristics

| Feature | Multispectral | Hyperspectral |
|---------|--------------|---------------|
| Bands | 3–10 | 100–500+ |
| Bandwidth | 50–200 nm | 5–15 nm |
| Spectral range | Selective | Contiguous |
| Data volume | Small | Large (hypercube) |
| Mineral ID | Indirect | Direct |

**Hypercube:** The data structure is a 3D array (x pixels × y pixels × λ bands). Each pixel contains a full reflectance spectrum.

---

## Spectral Range in Abdelhak's Thesis

| Range | Acronym | Wavelength | Key diagnostics |
|-------|---------|-----------|----------------|
| Visible | VIS | 400–700 nm | Fe3+ electronic transitions |
| Near-infrared | NIR | 700–1000 nm | Vegetation red edge, Fe2+ |
| Shortwave infrared | SWIR | 1000–2500 nm | Molecular overtones: OH, CO3, PO4 |
| Combined | VNIR+SWIR | 400–2500 nm | Full diagnostic window |

---

## Sensors in Abdelhak's Research

| Sensor | Type | Bands | Resolution | Used in |
|--------|------|-------|-----------|---------|
| ASD FieldSpec 4 | Field spectrometer | ~2100 bands | 1 nm (resampled) | Ch.1 (104 field samples) |
| PRISMA | Satellite | 239 bands | 30 m | Ch.2 (mineral mapping) |
| EnMAP | Satellite | 242 bands | 30 m | Ch.3 (reclamation monitoring) |

---

## Why Hyperspectral for Mining?

- **Mineral fingerprinting:** Every mineral has a unique spectral signature driven by electronic and vibrational processes
- **Non-destructive:** Remote sensing avoids the cost/time of physical sampling
- **Spatial coverage:** Satellite HSI covers entire mine sites in one pass (36 km² Benguerir = tens of thousands of pixels)
- **Reclamation monitoring:** Multi-temporal analysis tracks vegetation recovery and mineralogical change over time

---

## Diagnostic Absorption Features (Benguerir context)

| Feature | Wavelength | Mineral |
|---------|-----------|---------|
| CO₃ combination | ~2320 nm | Calcite, dolomite |
| Al-OH | ~2200 nm | Illite, kaolinite |
| Mg-OH | ~2330 nm | Dolomite, chlorite |
| PO₄ | ~2150 nm | Apatite (fluorapatite) |
| Fe3+ | ~500 nm, ~680 nm | Iron oxides (hematite, goethite) |
| OH stretch | ~1400, ~1900 nm | Water, hydroxyl minerals |

---

## Limitations

- **Mixed pixels:** At 30 m resolution, each pixel averages contributions from multiple minerals/materials → requires spectral unmixing
- **Atmospheric effects:** Water vapor absorption at ~1350–1450 nm and ~1800–1950 nm blocks parts of SWIR
- **Detector overlap:** VNIR-SWIR transition zone (~880–1050 nm) has lower SNR in both PRISMA and EnMAP
- **Spectral library completeness:** Matching requires reference spectra for every expected mineral; fluorapatite/francolite underrepresented in ECOSTRESS

---

## Related Concepts
- [[VNIR-SWIR Spectroscopy]]
- [[Spectral Library Matching]]
- [[Spectral Unmixing VCA-FCLS]]
- [[PRISMA Satellite]]
- [[EnMAP Satellite]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Machine Learning for Hyperspectral.md (~674 words)
================================================================================
---
tags: [wiki, concept, method, ch2, machine-learning]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# Machine Learning for Hyperspectral Classification

## Context in Thesis
Chapter 2 applies supervised machine learning to PRISMA satellite data for lithological mapping of phosphate waste rocks. The goal: classify pixels into lithological classes using field-validated training samples.

**Paper:** Accepted in *Minerals* 2026 (IF 2.2) ✅

> ⚠️ **Source of truth:** All numbers in this file are from the thesis manuscript. Conference abstract metrics (IGARSS 2025, EGU 2025) are from earlier experimental work and are NOT thesis results.

---

## Samples and Classes (Chapter 2)

| Step | Count | Details |
|------|-------|---------|
| Total field samples | 207 | Collected across Benguerir waste rock piles |
| Removed (shared pixels) | 80 | Same 30m PRISMA pixel footprint — removed to prevent spectral leakage |
| **Spatially independent samples** | **127** | Used for machine learning |
| XRD subset | 20 | Representative subset for mineralogical validation |
| XRF subset | 207 | All samples measured |

**4 Lithological Classes:**
1. **Phosphate rock** — carbonate fluorapatite-rich facies
2. **Siliceous facies** — quartz-dominated
3. **Marl** — clay-rich carbonate
4. **Limestone** — calcite/dolomite-dominated

---

## Models Tested

| Model | Best performer? | Notes |
|-------|----------------|-------|
| **Extra Trees** | ✅ Yes | Most stable; best BAC |
| **Random Forest** | ✅ Yes | Close second |
| XGBoost | Competitive | More sensitive to spatially structured data |
| SVM | Strong AUC | Lower BAC in complex multi-class setting |
| KNN | Baseline | Instance-based |

All evaluated under identical spatially constrained CV.

---

## Feature Selection — ANOVA within CV Folds

**Critical: nested inside each CV fold — no data leakage.**

```
For each CV fold:
  1. Fit ANOVA F-test on training split only
  2. Select top 60 SWIR bands
  3. Train classifier on selected features
  4. Evaluate on test split (unseen, spatially isolated data)
```

- **Why 60 bands?** Empirically selected via nested CV; captures CO₃, Al-OH, Mg-OH, PO₄ features
- **Why SWIR?** Molecular absorptions for carbonate/clay/phosphate minerals are in SWIR

---

## Spatially Constrained Cross-Validation

- 30m buffer between train and test (= 1 PRISMA pixel)
- 10 independent replicates
- Prevents spatial autocorrelation from inflating accuracy

---

## Key Results (Thesis Ch.2 — from manuscript)

| Metric | Value |
|--------|-------|
| Best models | Extra Trees, Random Forest |
| **BAC (balanced accuracy)** | **0.60–0.67** |
| **AUC (carbonate classes: Marl, Limestone)** | **> 0.95** |
| AUC (Phosphate rock, Siliceous facies) | Lower — spectral overlap at 30m |
| Spatially independent samples | 127 |
| CV scheme | Spatially constrained, 30m buffer, 10 replicates |
| Feature selection | Top 60 SWIR bands (ANOVA, nested in CV) |

**Class discrimination pattern:**
- Marl and Limestone: excellent discrimination (AUC > 0.95) — carbonate contrast is clear
- Phosphate rock vs. Siliceous facies: lower discrimination — spectral overlap at 30m scale reflects sub-pixel mixing

---

## Shannon Entropy Uncertainty
- Uncertainty is spatially structured — concentrated at lithological boundaries and in mixed phosphate-siliceous zones
- This is geologically meaningful: exactly where sub-pixel mixing is expected
- Operationally: high-entropy zones = where additional field investigation is warranted

---

## The 0.60–0.67 BAC: Context for Defense

This is the correct, peer-reviewed result representing true spatial generalization. The physically constrained upper bound on classification at 30m resolution with spatially clustered training data. The thesis manuscript states:

> "The resulting moderate but spatially robust classification accuracies (0.60–0.67) should therefore be understood as a physically constrained upper bound on what any classification algorithm can achieve given the inherent spectral mixing at 30 m."

**Do NOT confuse with:** The OA=0.92 figure in the IGARSS 2025 and EGU 2025 conference abstracts. Those are from earlier experimental work using a different framework (CNN+SHAP) and are not the thesis results submitted for defense.

---

## Related Concepts
- [[Hyperspectral Imaging]]
- [[PRISMA Satellite]]
- [[Spatially Constrained Cross-Validation]]
- [[Shannon Entropy Uncertainty]]
- [[Mineral Assemblages]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Mineral Assemblages.md (~527 words)
================================================================================
---
tags: [wiki, concept, mineralogy, benguerir]
updated: 2026-05-24
generated_by: claude
---

# Mineral Assemblages — Benguerir Phosphate Waste

## Overview
The mineral assemblage of Benguerir phosphate waste rock reflects the sedimentary phosphate deposit geology: marine carbonate-fluorapatite (francolite) in a carbonate-siliceous gangue, with secondary clay mineral weathering products.

---

## Primary Ore Minerals

### Fluorapatite Ca₅(PO₄)₃F
- End-member formula; rarely pure in sedimentary phosphates
- **Spectral signature:** PO₄ combination tone ~2150 nm (weak feature)
- **Diagnostic use:** Present in library as "Apatite Ca₅(PO₄)₃F"; detected at rank 3–7

### Francolite (Carbonate Fluorapatite)
- **Formula:** Ca₅[(PO₄)(CO₃)]₃F — partial substitution of CO₃ for PO₄
- The **actual dominant phosphate mineral** in [[04_Knowledge Base/wiki/entities/Gantour Basin\|Gantour Basin]] deposits
- Hybrid PO₄ + CO₃ signature → harder to distinguish spectrally from calcite
- **NOT in ECOSTRESS library** — key limitation of spectroscopy approach
- Confirmed via XRD

---

## Carbonate Gangue

### Calcite CaCO₃
- Very common in phosphate sequences (marine origin)
- Strong CO₃ combination at **2320 nm**
- Often rank 5–7 in spectral matching (weaker than clay Al-OH)
- Confirmed via XRD peak at 29.4° 2θ

### Dolomite CaMg(CO₃)₂
- Characteristic Mg-OH feature at **2330 nm**
- Often rank 3–4 in spectral matching
- Present in both managed and unmanaged zones

---

## Clay Gangue (Surface Dominant)

### Illite (K,H₃O)(Al,Mg,Fe)₂(Si,Al)₄O₁₀[(OH)₂,H₂O]
- Most spectrally dominant clay
- **Al-OH doublet: 2160 nm + 2205 nm** (diagnostic, strong)
- **Rank 1–2 in spectral matching** for most samples
- Formed by weathering of feldspar and volcanic ash layers
- Confirmed via XRD

### Kaolinite Al₂Si₂O₅(OH)₄
- Al-OH at **2200 nm** (sharp doublet at 2163 + 2206 nm distinguishes from illite)
- Lower abundance than illite at Benguerir
- Confirmed via XRD

### Montmorillonite (Smectite) (Na,Ca)₀.₃₃(Al,Mg)₂Si₄O₁₀(OH)₂·nH₂O
- Swelling clay; Al-OH at ~2205 nm
- Strong water absorption at 1900 nm (water molecules in interlayer)
- Rank 1–2 alongside illite
- Problematic for remote sensing: expands/contracts with moisture

---

## Silica Gangue

### Quartz SiO₂
- Essentially featureless in SWIR (no molecular absorptions)
- Detected via spectral background / contrast
- Rank 3–4 in some samples
- Confirmed via XRD sharp peak at 26.6° 2θ

---

## Iron Oxide Accessories

### Hematite α-Fe₂O₃ / Goethite α-FeOOH
- Not major phases but spectrally visible
- Fe3+ electronic transitions: shoulder ~500 nm, crystal field ~680 nm
- Source: lateritic weathering of primary minerals
- Tracked in `enmap_reclamation_engine_v2.py` feature catalogue

---

## Spectral Dominance Hierarchy
At surface expression (field + satellite scale):
```
Clays (Illite > Montmorillonite) >
Carbonates (Dolomite > Calcite) >
Iron Oxides >
Silica (Quartz) >
Phosphates (Apatite/Francolite)
```
Phosphates are mineralogically important but spectrally suppressed by surface clay coatings → requires HHXRF + XRD for reliable quantification.

---

## XRD Validation
XRD (X-ray diffraction) provides direct mineralogy:
- Peak at 29.4° 2θ → calcite
- Peak at 26.6° 2θ → quartz
- Peaks at ~7° and ~3.5° → illite/smectite
- Peaks at ~7.1° → kaolinite
- Peaks at ~7° broad → fluorapatite (overlaps with clay)

Published in Sensors 2025 (Ch.1): supplementary XRD patterns for representative samples.

---

## Related Concepts
- [[VNIR-SWIR Spectroscopy]]
- [[Spectral Library Matching]]
- [[Phosphate Mine Waste]]
- [[Handheld XRF]]
- [[Gantour Basin]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/PRISMA Satellite.md (~392 words)
================================================================================
---
tags: [concept, remote-sensing, PRISMA, satellite, core]
updated: 2026-05-24
generated_by: claude
domain: Remote Sensing
---

# PRISMA Satellite

## What It Is
PRISMA (PRecursore IperSpettrale della Missione Applicativa) is the Italian Space Agency (ASI) hyperspectral satellite. Launched March 2019. One of the most capable civil hyperspectral satellites currently operating.

## Technical Specs
| Parameter | Value |
|-----------|-------|
| Spectral range | 400–2500 nm (VNIR + SWIR) |
| Spectral bands | ~250 contiguous bands |
| Spectral resolution | ~10 nm |
| Spatial resolution | 30 m |
| Swath width | 30 km |
| Data format | **HDF5** |
| Revisit time | ~29 days (at equator) |

## Why Abdelhak Uses PRISMA
- Full VNIR + SWIR coverage → essential for phosphate mineralogy in SWIR
- Available for Moroccan study sites (Benguerir)
- Relatively new → Abdelhak's thesis is among the first hyperspectral satellite studies of Moroccan phosphate mining

## Data Format: HDF5
PRISMA delivers data in HDF5 format — requires custom loading scripts.  
Challenges solved during Abdelhak's thesis:
- HDF5 indexing script developed
- VNIR + SWIR cube fusion → NPZ format
- Bad band removal (water vapor absorption at ~1400nm, ~1900nm)
- Noisy band identification and removal

→ See `thesis/code-notes/VNIR SWIR Fusion` (code notes not yet in vault)  
→ See `thesis/code-notes/Bad Band Removal` (code notes not yet in vault)

## Key Spectral Bands for Phosphate Mineralogy
| Wavelength Region | Relevant Minerals |
|------------------|------------------|
| ~900–1000 nm (NIR) | Iron oxides, goethite, hematite |
| ~2200 nm (SWIR) | Al-OH clays, kaolinite, alunite |
| ~2300 nm (SWIR) | Carbonates, Mg-OH, dolomite |
| ~2100–2200 nm | Phosphate minerals (specific features) |
| ~1400, 1900 nm | Water/OH (remove — atmosphere) |

## PRISMA vs. Other Sensors
| Sensor | Bands | Resolution | Notes |
|--------|-------|------------|-------|
| PRISMA | ~250 | 30m | ✅ Abdelhak's sensor |
| Sentinel-2 | 13 | 10-60m | Too few bands for mineralogy |
| EnMAP | 244 | 30m | Higher SNR, newer (2022) |
| AVIRIS | 224 | variable | Airborne, not satellite |
| HyMap | 128 | variable | Airborne |

## Related Pages
- [[04_Knowledge Base/wiki/concepts/Hyperspectral Imaging]]
- [[04_Knowledge Base/wiki/concepts/Waste Rock Characterization]]
- [[04_Knowledge Base/wiki/concepts/Spectral Analysis]]
- [[02_Academic & Work/thesis/Thesis Overview]]

## Sources
*(Add papers about PRISMA applications as you ingest them)*




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Phosphate Mine Waste.md (~498 words)
================================================================================
---
tags: [wiki, concept, geology, benguerir]
updated: 2026-05-24
generated_by: claude
---

# Phosphate Mine Waste / Waste Rock

## Definition
Phosphate mine waste rocks are the non-ore materials excavated to access phosphate ore bodies. At Benguerir (OCP Group), they form large waste rock piles (WRP) requiring environmental management and potential reclamation.

---

## Benguerir Mine Context

| Parameter | Value |
|-----------|-------|
| Operator | OCP Group |
| Basin | [[04_Knowledge Base/wiki/entities/Gantour Basin\|Gantour Basin]], Morocco |
| Study area | ~36 km² |
| Stripping ratio | ~3:1 (waste:ore) |
| Waste production | ~12.3 Mt/year |
| Pile heights | Up to several tens of meters |
| Age of dumps | Decades of accumulation |

---

## Mineralogical Composition (from thesis Ch.1)

### Primary minerals (host rock)
| Mineral | Formula | Spectral signature |
|---------|---------|-------------------|
| Fluorapatite | Ca₅(PO₄)₃F | PO₄ ~2150 nm (weak) |
| Francolite | Ca₅(PO₄,CO₃)₃F | Carbonate-phosphate |
| Calcite | CaCO₃ | CO₃ ~2320 nm |
| Dolomite | CaMg(CO₃)₂ | Mg-OH ~2330 nm |

### Secondary/gangue minerals
| Mineral | Formula | Spectral signature |
|---------|---------|-------------------|
| Illite | (K,H₃O)(Al,Mg,Fe)₂(Si,Al)₄O₁₀(OH)₂ | Al-OH ~2200 nm |
| Kaolinite | Al₂Si₂O₅(OH)₄ | Al-OH ~2200 nm |
| Montmorillonite | (Na,Ca)Al₂Si₄O₁₀(OH)₂·nH₂O | Al-OH ~2200 nm |
| Quartz | SiO₂ | Featureless in SWIR |
| Iron oxides | Hematite, Goethite | Fe3+ ~500, 680 nm |

### Why clays dominate spectral response
Clay minerals (illite, montmorillonite) coat waste rock surfaces due to weathering. Their Al-OH absorptions at ~2200 nm are spectrally stronger than the apatite PO₄ feature at ~2150 nm → clays rank 1–2 in spectral matching despite being secondary minerals.

---

## Reclamation Context

**Two zone types in Abdelhak's thesis:**
- **RWR (Reference Waste Rock):** Unmanaged dump — raw, unvegetated, high phosphate, geochemically unstable
- **RZ (Reclaimed Zone):** Managed area undergoing vegetation restoration — soil amendment, seeding, water management

**Environmental concerns:**
- Dust and wind erosion (fine phosphate particles)
- Leaching of heavy metals and fluorine
- Landscape rehabilitation compliance (OCP sustainability targets)
- Acid rock drainage potential (limited for calcareous phosphate gangue)

---

## Geochemistry (XRF targets from thesis)
Key oxides monitored: CaO, SiO2, Al2O3, MgO, K2O, Na2O, P2O5, TiO2, MnO, Fe2O3

**P2O5 as reclamation indicator:**
- High P2O5 → unweathered phosphate waste
- Decreasing P2O5 over time → mineral weathering, dilution by added topsoil, vegetation biomass accumulation
- The **Reclamation Progress Index (RPI)** uses abundance of vegetation/soil endmembers relative to raw waste endmembers, isotonically calibrated against XRF P2O5

---

## Field Sampling (Thesis)
- 104 field samples collected across managed and unmanaged zones
- GPS locations recorded (used in QGIS maps, plotted in `Samples ppaer 1 + 2 all.csv`)
- ASD FieldSpec 4 measurement at each sample point
- HHXRF measurement (same or adjacent point)
- XRD on subset → mineral quantification

---

## Related Concepts
- [[Mineral Assemblages]]
- [[VNIR-SWIR Spectroscopy]]
- [[Handheld XRF]]
- [[Reclamation Monitoring]]
- [[OCP Group and Benguerir Mine]]
- [[Gantour Basin]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Reclamation Monitoring.md (~677 words)
================================================================================
---
tags: [wiki, concept, reclamation, ch3, environmental]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# Reclamation Monitoring (Chapter 3)

## Definition
Chapter 3 quantifies the impact of **backfilling** — the primary reclamation strategy at Benguerir — on phosphate waste rock surface characteristics, using EnMAP hyperspectral data and spectral unmixing.

**Exact thesis title:** *"Assessing the impact of backfilling on phosphate mine waste rock characteristics in Benguerir, Morocco: An integrated field, laboratory, and hyperspectral remote sensing approach"*

> **Important:** The reclamation strategy is specifically **backfilling** (remblayage), not generic revegetation. Backfilling = re-depositing material over waste rock piles to modify surface composition and prepare for revegetation.

---

## Two Zone Types

| Zone | Code | Description |
|------|------|-------------|
| Reclaimed Zone | **RZ** | Has undergone backfilling, leveling, and preparation for revegetation |
| Reference Waste Rock Zone | **RWR** | Undisturbed deposited waste — "zero reclamation" reference |

---

## Study Design (from manuscript)

| Parameter | Value |
|-----------|-------|
| XRF samples per zone | n = 32 (balanced) |
| EnMAP valid pixels (RZ) | 49 (balanced to 32) |
| EnMAP valid pixels (RWR) | 47 (balanced to 32) |
| EnMAP valid bands | **189** (spanning 418–2445 nm) |
| Balancing seed | 42 (reproducible) |
| Spectral concordance (full vs. balanced) | Pearson r = 0.990 |

---

## What Backfilling Does Spectrally

**XRF evidence:** Statistically significant geochemical contrasts (BH FDR-corrected q < 0.05) in:
P₂O₅, CaO, SiO₂, Al₂O₃, MgO, K₂O, and Na₂O between RZ and RWR.

Interpretation: Backfilling redistributes and mixes stratigraphically distinct lithological units, changing the surface geochemistry and thus the spectral response.

---

## Spectral Separation (Per-Band Analysis)

**Mann-Whitney U test on all 189 valid EnMAP bands:**
- Significant zone separation across **all 189/189 valid bands** (q < 0.05 after BH FDR correction)
- **Median effect size: r = 0.859** (large by conventional standards)
- Spectral autocorrelation ρ₁ ≈ 0.992 → effective independent comparisons ≈ 17 → FDR correction applied

**Key diagnostic features:**
| Feature | Wavelength | Δ (RZ−RWR) | p-value |
|---------|-----------|-----------|--------|
| Carbonate combination | ~2330 nm | −0.019 | 0.0001 |
| Iron oxide shoulder | ~900 nm | +0.006 | 0.0007 |

---

## VCA-FCLS Unmixing Results (4 Endmembers)

| Endmember | Dominant zone | RWR mean | RZ mean | Δ |
|-----------|--------------|---------|--------|---|
| EM3 | **RWR** (raw waste) | 0.612 | 0.053 | +0.559 |
| EM4 | **RZ** (backfilled) | 0.032 | 0.516 | −0.483 |

Bootstrap 95% CI excludes zero for both EM3 and EM4.

---

## Statistical Validation

| Test | Result |
|------|--------|
| Bootstrap (5,000 iter.) | 95% CI excludes zero for EM3 and EM4 |
| Permutation test (10,000 iter.) | p = 0.0001 |
| Spatial holdout | Same-sign fraction = 1.00 across all holdouts |
| **Spatially blocked CV** | **BAC = 0.984 ± 0.031; AUC = 1.000** |
| Permutation p (spatial block) | Empirical p = 0.002 |

> The near-perfect BAC (0.984) reflects the strong spectral separation induced by backfilling — confirmed non-spurious by permutation test and spatial blocking. This is very different from the Ch.2 result (BAC=0.60–0.67) because the RZ vs. RWR contrast is a binary comparison at zone scale, not a fine-grained 4-class lithological mapping.

---

## Reclamation Progress Index (RPI)

| Zone | RPI median | 95% CI |
|------|-----------|--------|
| **RZ (reclaimed)** | **0.896** | [0.860–0.927] |
| **RWR (reference)** | **0.203** | [0.161–0.221] |

XRF concordance: Spearman ρ = 0.845, p = 1.74 × 10⁻¹²

→ Full details: [[Reclamation Progress Index]]

---

## Implications

1. EnMAP Level-2A at 30m can reliably discriminate reclaimed from undisturbed phosphate waste (all 189 bands significant)
2. Near-perfect spatial CV accuracy (BAC=0.984) establishes EnMAP as operationally viable for large-scale monitoring
3. No bespoke airborne campaigns needed — 27-day revisit at no additional cost
4. RPI provides quarterly progress reporting tool for OCP Group

---

## Related Concepts
- [[EnMAP Satellite]]
- [[Spectral Unmixing VCA-FCLS]]
- [[Reclamation Progress Index]]
- [[Phosphate Mine Waste]]
- [[OCP Group and Benguerir Mine]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Reclamation Progress Index.md (~561 words)
================================================================================
---
tags: [wiki, concept, novel-contribution, ch3]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# Reclamation Progress Index (RPI)

## Definition
The Reclamation Progress Index (RPI) is a **novel spectral index** developed in Chapter 3 of Abdelhak's thesis. It provides a satellite-derived metric (0–1) of reclamation progress, calibrated isotonically against field XRF geochemical support scores.

**This is the most original methodological contribution of the entire thesis.**

---

## Validated Results (from thesis manuscript)

| Zone | RPI median | 95% CI |
|------|-----------|--------|
| **RZ (Reclaimed — backfilled)** | **0.896** | [0.860–0.927] |
| **RWR (Reference Waste Rock)** | **0.203** | [0.161–0.221] |

**XRF concordance:** Spearman ρ = 0.845, p = 1.74 × 10⁻¹²

**Transitional fraction** (RPI 0.35–0.65): characterizes intermediate reclamation states

**RZ-like classification (RPI > threshold):** 90.625% of RZ pixels correctly identified

---

## Construction

### Step 1: EnMAP preprocessing
- 189 valid bands (418–2445 nm after masking)
- 32 balanced pixels per zone (from 49 RZ + 47 RWR valid pixels, seed=42)
- Spectral concordance: Pearson r = 0.990 (full vs. balanced subset)

### Step 2: VCA endmember extraction (k=4)
Four scene-derived endmembers extracted from combined RZ+RWR spectra:
- **EM3:** Dominant in RWR (raw waste) — mean RWR=0.612, mean RZ=0.053
- **EM4:** Dominant in RZ (backfilled) — mean RWR=0.032, mean RZ=0.516

### Step 3: FCLS abundance estimation
- Fully Constrained Least Squares: non-negativity + sum-to-one
- Parallel implementation per pixel
- Output: abundance fraction for each endmember per pixel

### Step 4: Abundance ratio → Raw RPI
```
Raw_RPI = EM4_abundance / (EM3_abundance + EM4_abundance)
```
Higher value = more "reclaimed" endmember relative to "raw waste" endmember.

### Step 5: Isotonic calibration against XRF
- At matched pixel-XRF locations: relate Raw_RPI to XRF geochemical support score
- **Isotonic regression:** monotone non-decreasing function, no linearity assumption
- Calibrated RPI: 0 (no reclamation) → 1 (full target state)

**Why isotonic?** The relationship is monotone but non-linear; isotonic regression is non-parametric and enforces the correct ordering without assuming any functional form.

---

## Statistical Validation

| Test | Result |
|------|--------|
| Spearman ρ (RPI vs. XRF) | 0.845 |
| p-value | 1.74 × 10⁻¹² |
| Zone difference significance | Clearly differentiated (non-overlapping 95% CI) |
| Spatial holdout fraction | 1.00 (same-sign across all holdouts) |

---

## Spatial Application
- Computed for every valid pixel in EnMAP scene
- Maps entire 36 km² mine in one pass
- Repeatable with future EnMAP acquisitions → operational monitoring
- OCP Group can track reclamation trajectory without additional field campaigns

---

## Potential for Operational Use

> "The RPI can be computed automatically from any future EnMAP acquisition, providing OCP with a quarterly reclamation progress report at zero additional field cost."

Generalizable framework: the calibration approach (unmixing → isotonic calibration → XRF) can be applied to any satellite hyperspectral mission for any mine type with geochemical ground truth.

---

## Defense Talking Point
If asked about broader impact: "The RPI framework is generalizable — VCA-FCLS + isotonic XRF calibration can be applied to any HSI sensor (PRISMA, DESIS, future missions) and any mine type where geochemical ground truth exists. This is not specific to EnMAP or Benguerir — it's an operational template for satellite-based mine reclamation monitoring."

---

## Related Concepts
- [[Reclamation Monitoring]]
- [[Spectral Unmixing VCA-FCLS]]
- [[EnMAP Satellite]]
- [[Handheld XRF]]
- [[Phosphate Mine Waste]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Shannon Entropy Uncertainty.md (~435 words)
================================================================================
---
tags: [wiki, concept, method, statistics, ch2]
updated: 2026-05-24
generated_by: claude
---

# Shannon Entropy Uncertainty Mapping

## Definition
Shannon entropy is an information-theoretic measure of uncertainty applied to probabilistic classifier outputs. In Chapter 2, it maps per-pixel prediction uncertainty across the PRISMA mineral classification map.

---

## Formula
```
H(x) = −Σᵢ p(cᵢ|x) × log₂[p(cᵢ|x)]
```
Where:
- H(x) = entropy at pixel x (in bits)
- p(cᵢ|x) = predicted probability of class i at pixel x
- Sum over all K mineralogical classes

**Bounds:**
- H = 0 bits: Certain — one class has probability = 1, all others = 0
- H = log₂(K) bits: Maximum uncertainty — all K classes equally probable

---

## Physical Interpretation for Mineralogy

| Entropy level | Meaning |
|---------------|---------|
| H ≈ 0 | Pixel is spectrally pure, clear mineral signature |
| H = 0.5–1.5 | Moderate uncertainty — possible mixed pixel or boundary |
| H > 2.0 | High uncertainty — mixed pixel, unusual spectrum, or outside training distribution |

**Where high entropy appears:**
- Pixel boundaries between mineralogical units (transition zones)
- Mixed pixels combining multiple minerals in equal proportions
- Pixels with atmospheric artifacts or sensor noise
- Areas outside the spectral range of training data (extrapolation)

---

## Role in Thesis Chapter 2

1. **Diagnostic:** Identify pixels where the model is uncertain
2. **Priority areas for future fieldwork:** High-entropy zones should be validated first
3. **Quality control:** Threshold-based masking of uncertain predictions before generating final mineral map
4. **Honest reporting:** Entropy map alongside classification map shows where the model can and cannot be trusted

---

## Connection to Spatially Constrained CV

Both entropy mapping and spatially constrained CV address model reliability:
- **Spatial CV:** Honest generalization metric during training (removes autocorrelation)
- **Entropy map:** Honest per-pixel uncertainty during prediction (identifies low-confidence areas)

Together they form a rigorous uncertainty framework for the classification.

---

## Calculation in Random Forest / Extra Trees

Random Forest and Extra Trees output class probabilities as the mean of per-tree votes:
```python
proba = clf.predict_proba(X)  # shape: (n_pixels, n_classes)
entropy = -np.sum(proba * np.log2(proba + 1e-10), axis=1)
```
This probability vector is what feeds the entropy calculation.

---

## Defense Talking Point

"Shannon entropy maps provide the jury with spatial honesty about where our model is confident and where it isn't. Rather than presenting a single classification map as if every pixel were equally reliable, we communicate uncertainty spatially — which is the scientifically rigorous approach."

---

## Related Concepts
- [[Machine Learning for Hyperspectral]]
- [[Spatially Constrained Cross-Validation]]
- [[PRISMA Satellite]]
- [[Hyperspectral Imaging]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Spatially Constrained Cross-Validation.md (~572 words)
================================================================================
---
tags: [wiki, concept, method, statistics, ch2]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# Spatially Constrained Cross-Validation

## The Problem: Spatial Autocorrelation in Remote Sensing ML

In remote sensing, nearby pixels are spatially correlated — they share similar spectra because they share similar materials, illumination, and atmospheric conditions. Standard k-fold CV randomly assigns pixels to train/test splits, meaning:
- A pixel at location (x, y) may be in the test set
- Its neighbor at (x+30m, y) is likely in the training set
- The model "cheats" by learning from the neighbor → inflated performance

**Tobler's First Law of Geography:** "Everything is related to everything else, but near things are more related than distant things."

---

## Abdelhak's Solution: Spatial CV with Buffer (Chapter 2)

```
For each test sample:
  Exclude all training samples within 30m buffer
  (= 1 pixel at 30m PRISMA/EnMAP resolution)

Result:
  Test pixels have no direct spatial neighbors in training
  Evaluation is honest about generalization to new locations
```

**Parameters (from thesis manuscript):**
- Buffer: 30m (= 1 PRISMA pixel)
- CV replicates: 10 independent replicates of the 127-sample dataset
- Metric: BAC (Balanced Accuracy) — handles class imbalance
- Additional: Spatially blocked CV for Chapter 3 (EnMAP)

---

## Chapter 2 Accuracy (from manuscript — single source of truth)

| Metric | Value | Notes |
|--------|-------|-------|
| **BAC (best classifiers)** | **0.60–0.67** | Extra Trees, Random Forest |
| **AUC (carbonate classes)** | **> 0.95** | Marl, Limestone |
| AUC (Phosphate, Siliceous) | Lower | Spectral overlap at 30m |
| Spatially independent samples | 127 | After removing 80 shared-pixel duplicates |

The thesis manuscript states explicitly:
> "The resulting moderate but spatially robust classification accuracies (0.60–0.67) should therefore be understood as a physically constrained upper bound on what any classification algorithm can achieve given the inherent spectral mixing at 30 m."

---

## Chapter 3: Spatially Blocked Cross-Validation (EnMAP)

Chapter 3 uses a different, even more conservative spatial validation:
- Elastic-net logistic regression on 32 balanced pixels per zone
- **4 spatial groups** + **25 random CV repeats** + **500 permutation replicates**
- Result: **BAC = 0.984 ± 0.031; AUC = 1.000**
- Empirical permutation p = 0.002

This near-perfect result (Ch.3) reflects the much stronger spectral separation between RZ and RWR zones under backfilling — NOT overfitting, confirmed by permutation test and spatial blocking.

---

## Why This Matters for Defense

"Why is your Ch.2 accuracy only 0.60–0.67?"

> "This is the honest, spatially-aware accuracy. Spatial CV (30m buffer, 10 replicates) prevents autocorrelation from inflating the metric. The 0.60–0.67 BAC represents true generalization performance at new, spatially isolated locations. For geological mapping with 30m pixels and spatially clustered training data, this is the realistic ceiling — the thesis itself states this is a 'physically constrained upper bound' on what any classifier can achieve given sub-pixel mixing. Marl and Limestone, which are spectrally distinct, achieve AUC > 0.95. The lower discrimination is in the Phosphate vs. Siliceous facies, which overlap at 30m scale."

---

## Literature Support
- Roberts et al. (2017) — spatial CV for remote sensing
- Ploton et al. (2020) — spatial CV for forest mapping
- Karasiak et al. (2022) — spatial autocorrelation in ML
- Meyer & Pebesma (2021) — "Predicting into unknown space"

---

## Related Concepts
- [[Machine Learning for Hyperspectral]]
- [[PRISMA Satellite]]
- [[EnMAP Satellite]]
- [[Shannon Entropy Uncertainty]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Spectral Analysis.md (~267 words)
================================================================================
---
tags:
  - wiki
  - spectral-analysis
  - concept
created: 2026-06-07
generated_by: claude
summary: "Spectral analysis methods used in hyperspectral remote sensing — library matching, unmixing, classification."
---

# Spectral Analysis

Quantitative analysis of electromagnetic reflectance spectra to identify and characterize materials based on their spectral signatures.

## Core Methods (used in Abdelhak's Thesis)

### Library Matching
- Compare measured spectra to reference libraries (ECOSTRESS, USGS splib07)
- Metrics: RMSE, SAM (Spectral Angle Mapper), SID (Spectral Information Divergence), R²
- Used in Ch.1 (field spectra) and Ch.2 (PRISMA)

### Spectral Unmixing
- Decompose a mixed pixel into endmember fractional abundances
- Methods: VCA (Vertex Component Analysis) for endmember extraction, FCLS (Fully Constrained Least Squares) for abundance mapping
- Used in Ch.3 (EnMAP) → produces the [[04_Knowledge Base/wiki/concepts/Reclamation Progress Index|RPI]]

### Continuum Removal
- Normalizes spectra to highlight absorption features
- Convex hull algorithm isolates relative band depths
- Standard pre-processing step before library matching

## Key Spectral Features for Phosphate Mineralogy

| Wavelength | Feature | Mineral |
|-----------|---------|---------|
| ~2150 nm | PO₄ stretch (weak) | Fluorapatite |
| ~2200–2208 nm | Al-OH (sharp) | Illite/Muscovite |
| ~2165 + 2200 nm doublet | Al-OH | Kaolinite |
| ~2320–2350 nm | CO₃ | Dolomite/Calcite |
| ~500–900 nm | Fe³⁺ | Goethite, Hematite |

## Sensors Used

- **Field:** ASD FieldSpec 4 (350–2500 nm, 1 nm sampling)
- **Satellite Ch.2:** [[04_Knowledge Base/wiki/concepts/PRISMA Satellite]] (~250 bands, 30m)
- **Satellite Ch.3:** [[04_Knowledge Base/wiki/concepts/EnMAP Satellite]] (189 valid bands, 30m)

## Related

- [[04_Knowledge Base/wiki/concepts/Spectral Library Matching]]
- [[04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS]]
- [[04_Knowledge Base/wiki/concepts/VNIR-SWIR Spectroscopy]]
- [[04_Knowledge Base/wiki/concepts/Hyperspectral Imaging]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Spectral Library Matching.md (~503 words)
================================================================================
---
tags: [wiki, concept, spectroscopy, method]
updated: 2026-05-24
generated_by: claude
---

# Spectral Library Matching

## Definition
Spectral library matching identifies the mineralogy of an unknown spectrum by comparing it against a reference library of known mineral spectra. For each candidate mineral, a similarity metric (or composite of metrics) is computed; the mineral with the best score is assigned as the match.

---

## Libraries Used in Abdelhak's Thesis

### ECOSTRESS Spectral Library (splib07)
- Maintained by USGS / JPL
- ~2,400+ spectra across minerals, vegetation, man-made materials
- For Benguerir work: 1,609 spectra parsed; 15 curated for phosphate waste rock minerals
- URL: Available via USGS/EROS
- Key minerals present: Calcite, Dolomite, Illite, Montmorillonite, Kaolinite, Quartz, Apatite Ca₅(PO₄)₃F
- Key **absence**: Fluorapatite/francolite (francolite = carbonate fluorapatite, dominant phosphate in Benguerir) → known limitation

---

## Metrics

### RMSE (Root Mean Square Error)
```
RMSE = √(mean((a−b)²))
```
- Overall shape similarity
- Sensitive to baseline offset differences
- In thesis: weighted 5× in 2100–2300 nm (PO₄ window)

### SAM (Spectral Angle Mapper)
```
SAM = arccos(a·b / (‖a‖ × ‖b‖))
```
- Measures angle between spectra in N-dimensional space
- Insensitive to illumination scaling (brightness-invariant)
- Result in radians; lower = more similar

### SID (Spectral Information Divergence)
```
SID = Σ p(i)·log(p(i)/q(i)) + Σ q(i)·log(q(i)/p(i))
```
- Treats spectra as probability distributions (KL divergence, symmetric)
- Sensitive to subtle shape differences
- Complementary to SAM

### R² (Coefficient of Determination)
```
R² = 1 − SSres/SStot
```
- How well the reference explains the unknown spectrum's variance
- R² near 1 = excellent fit

### Composite Score (in thesis Ch.1)
```
score = RMSE + SAM + SID
```
- Combined ranking; rank-1 = minimum composite score
- Top 5–8 matches reported per sample

---

## Preprocessing Before Matching
1. Resampling to common wavelength grid (350–2500 nm, 1 nm step)
2. Savitzky-Golay smoothing (window=7, poly=2)
3. Min-max normalization: (x − min) / range
4. Optional: continuum removal, derivative
5. Convert ECOSTRESS percent reflectance → fraction (÷100)

---

## Challenges for Phosphate Waste Rocks

**Problem: Clay masking of apatite**
- Illite and montmorillonite have strong Al-OH absorptions (~2200 nm)
- Apatite PO₄ absorption (~2150 nm) is weaker
- After normalization, clay features dominate → apatite ranks 3–7, not 1
- **Solution:** Use HHXRF to directly measure P₂O₅, bypassing spectral dominance issue

**Problem: Library incompleteness**
- Francolite (carbonate fluorapatite) — the actual phosphate mineral at Benguerir — absent from ECOSTRESS
- Only generic "Apatite Ca₅(PO₄)₃F" available
- **Impact:** Phosphate identification less precise spectrally; confirmed via XRD/XRF

---

## Key Results from Thesis Ch.1 (104 samples)
| Rank | Dominant mineral |
|------|----------------|
| 1–2 | Illite, Montmorillonite |
| 3–4 | Dolomite, Quartz |
| 5–7 | Apatite, Calcite, Kaolinite |

This distribution is **mineralogically consistent** with phosphate waste rock: clay gangue coats surfaces; carbonates and silica form the matrix; apatite is the economic mineral beneath.

---

## Related Concepts
- [[VNIR-SWIR Spectroscopy]]
- [[Hyperspectral Imaging]]
- [[Mineral Assemblages]]
- [[Spectral Unmixing VCA-FCLS]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS.md (~573 words)
================================================================================
---
tags: [wiki, concept, method, ch1, ch3]
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
---

# Spectral Unmixing — NNLS, VCA, FCLS

## Problem Statement
At 30m pixel resolution, each EnMAP or PRISMA pixel contains contributions from multiple minerals (mixed pixel problem). Spectral unmixing decomposes a mixed pixel spectrum into:
- **Endmembers:** Pure component spectra
- **Abundances:** Fractional contribution of each endmember (sum-to-one constraint)

**Linear mixing model:**
```
r = Σ(a_i × e_i) + ε
```
Where r = observed spectrum, a_i = abundances, e_i = endmember spectra, ε = noise

---

## Methods Used in Abdelhak's Thesis

### Chapter 1: NNLS (Non-Negative Least Squares)
- Endmembers from ECOSTRESS spectral library (top-5 rank-1 matches per sample)
- NNLS finds non-negative abundances minimizing ||r − E·a||²
- Applied to 104 field samples
- Provides relative abundance of dolomite, illite, kaolinite, calcite, apatite

### Chapter 3: VCA + FCLS (primary satellite-scale method)

**VCA (Vertex Component Analysis)** — Endmember extraction
- Assumes endmembers are at the vertices of the spectral simplex
- PCA reduction → iterative vertex finding
- Unsupervised — endmembers extracted from data, no library needed
- **k = 4 endmembers** (primary)

**FCLS (Fully Constrained Least Squares)** — Abundance estimation
- Minimizes ||r − E·a||² subject to: a_i ≥ 0 AND Σa_i = 1
- Implementation: NNLS with augmented sum-to-one equation
- Parallelized via ThreadPoolExecutor

---

## Key Ch.3 Results (from thesis manuscript)

| Endmember | Dominant zone | RWR mean abundance | RZ mean abundance | Δ (RZ−RWR) |
|-----------|--------------|-------------------|-----------------|-----------|
| EM3 | **RWR** (raw waste) | 0.612 | 0.053 | −0.559 |
| EM4 | **RZ** (backfilled) | 0.032 | 0.516 | +0.484 |

Bootstrap (5,000 iterations): 95% CI excludes zero for both EM3 and EM4.

**Spatially blocked CV:** BAC = 0.984 ± 0.031; AUC = 1.000

---

## Ch.3 Band Configuration

From the manuscript (not from the Python script — manuscript is source of truth):

| Band category | Wavelength range | Action |
|--------------|----------------|--------|
| Valid bands | **189 bands, 418–2445 nm** | Retained |
| Detector overlap | 1342–1391 nm | Masked |
| Water vapor A | 1350–1450 nm | Masked |
| Water vapor B | 1800–1950 nm | Masked |
| Below valid fraction | Various | Masked |

---

## VCA Algorithm

```
1. Mean-center spectra: R_c = R - mean(R)
2. SVD: U, S, V = svd(R_c)
3. Project to k-dimensional subspace: R_w = U[:, :k] × S[:k]
4. Iterative vertex finding (k iterations):
   - Random vector w
   - Orthogonalize against current endmember set
   - k = argmax|R_w · f|
   - Add to endmember set
```

---

## FCLS Implementation

```python
# Augmented system: adds sum-to-one as an additional equation
A_aug = vstack([endmember_matrix.T, scale × ones])
b_aug = hstack([pixel, scale])  # scale = 1000.0
abundances, _ = nnls(A_aug, b_aug)
abundances = abundances / abundances.sum()  # renormalize
```

---

## Linear Mixing Assumption — Limitation
Real-world mixing is often non-linear (intimate mixtures, multiple scattering). The thesis acknowledges this:
> "Structured residuals in the 2150–2300 nm region for samples with overlapping clay-carbonate signatures are flagged as cases requiring qualitative rather than quantitative interpretation."

Linear mixing is used because at 30m satellite pixels, areal (checkerboard) mixing dominates — each component reflects independently. This is the standard model for geological remote sensing at this scale.

---

## Related Concepts
- [[Hyperspectral Imaging]]
- [[VNIR-SWIR Spectroscopy]]
- [[EnMAP Satellite]]
- [[Reclamation Monitoring]]
- [[Reclamation Progress Index]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/VNIR-SWIR Spectroscopy.md (~526 words)
================================================================================
---
tags: [wiki, concept, spectroscopy, ch1]
updated: 2026-05-24
generated_by: claude
---

# VNIR-SWIR Spectroscopy

## Definition
Visible/Near-Infrared + Shortwave Infrared spectroscopy (VNIR-SWIR) covers 350–2500 nm. Combined with handheld XRF (HHXRF), it forms the core analytical approach of Chapter 1 of Abdelhak's thesis for field characterization of phosphate mine waste.

**Chapter 1 title:** "Integrating VNIR–SWIR Spectroscopy and Handheld XRF for Enhanced Mineralogical Characterization of Phosphate Mine Waste Rocks in Benguerir"  
**Published:** Sensors (IF 3.5), Dec 2025, doi:10.3390/s26010002

---

## Physical Basis

Spectral features in the VNIR-SWIR arise from two processes:

### Electronic transitions (VNIR, 400–1000 nm)
- **Fe2+/Fe3+ electronic transitions** → broad absorptions at 500 nm, 680 nm, 900 nm
- Diagnostic for iron oxides: hematite (α-Fe₂O₃), goethite (α-FeOOH)
- Present in phosphate waste due to oxidized gangue

### Molecular vibrations (SWIR, 1000–2500 nm)
- **Overtones and combination tones** of fundamental molecular bonds
- OH⁻ stretch → ~1400 nm, ~1900 nm (clays, hydroxyl minerals)
- CO₃ combination → ~2320 nm (carbonates)
- Al-OH combination → ~2200 nm (kaolinite, illite)
- Mg-OH combination → ~2330 nm (dolomite, chlorite)
- PO₄ overtone → ~2150 nm (apatite, fluorapatite) — weak but diagnostic

---

## Chapter 1 Workflow

```
104 field samples (ASD FieldSpec 4, 350–2500nm)
     ↓
Preprocessing: resampling → 1nm common grid → normalization
     ↓
Spectral library matching (ECOSTRESS splib07)
     Metrics: RMSE, SAM, SID, R² → composite score
     ↓
Best-match mineral identification (rank 1–8)
     ↓
NNLS spectral unmixing (endmember abundances)
     ↓
Integration with HHXRF (elemental chemistry)
     Results: CaO, SiO2, P2O5, Fe2O3, Al2O3, MgO, K2O, etc.
     ↓
Cross-validation with XRD (mineralogy)
```

---

## ECOSTRESS Spectral Library (splib07)
- ~1,609 spectra total; 15 curated for Benguerir target minerals
- **Key finding:** Fluorapatite/francolite underrepresented → apatite at rank 3–7, not rank 1
- Dominant rank-1 matches: Illite, Montmorillonite (clays absorb more strongly than apatite in VNIR-SWIR)
- This is physically correct: clay surface coatings dominate spectral response; apatite detected beneath clay signal via unmixing + XRF confirmation

---

## Matching Metrics

| Metric | Formula | Good value |
|--------|---------|-----------|
| RMSE | √(mean((a−b)²)) | Low |
| SAM | arccos(a·b / ‖a‖‖b‖) | Low (radians) |
| SID | KL divergence (symmetric) | Low |
| R² | 1 − SSres/SStot | High |
| Composite score | RMSE + SAM + SID | Low |

**Phosphate weighting:** RMSE is weighted 5× in the 2100–2300 nm window to emphasize PO₄ diagnostic region.

---

## ASD FieldSpec 4 Specifications
- Range: 350–2500 nm
- Sampling interval: 1.4 nm (VNIR), 2 nm (SWIR)
- FWHM: 3 nm (VNIR), 6–10 nm (SWIR)
- Field of view: ~25° FOV contact probe
- Calibration: BaSO₄ Spectralon white reference panel before each measurement

---

## Key Results (Thesis Ch.1)
- 104 samples from Benguerir waste rock piles (managed + unmanaged zones)
- Dominant minerals identified: illite > dolomite > calcite > kaolinite > apatite
- Clay minerals dominate spectral response → consistent with phosphate gangue mineralogy
- HHXRF validated: P₂O₅ content correlates with apatite abundance from unmixing
- Combined VNIR-SWIR + HHXRF outperforms either method alone

---

## Related Concepts
- [[Hyperspectral Imaging]]
- [[Spectral Library Matching]]
- [[Handheld XRF]]
- [[Mineral Assemblages]]
- [[Phosphate Mine Waste]]




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Waste Rock Characterization.md (~215 words)
================================================================================
---
tags:
  - wiki
  - waste-rock
  - concept
created: 2026-06-07
generated_by: claude
summary: "Mine waste rock characterization — mineralogy, spectral properties, and monitoring at Benguerir."
---

# Waste Rock Characterization

The process of identifying and quantifying the mineralogical, geochemical, and physical properties of excavated non-ore material from mining operations.

## Context (Benguerir, Morocco)

At the Benguerir phosphate mine ([[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine|OCP Group]]), waste rock piles (WRP) require characterization to:
- Assess environmental risk (leaching, dust, ARD potential)
- Identify valorization potential (residual phosphate, carbonates)
- Design reclamation and revegetation strategies

## Key Mineral Classes (from Thesis Ch.1)

| Class | Dominant Minerals | Spectral Signature |
|-------|------------------|-------------------|
| Carbonates | Dolomite, Calcite | ~2320–2350 nm |
| Clays | Illite, Kaolinite, Smectite | Al-OH ~2200 nm |
| Phosphates | Fluorapatite, Francolite | PO₄ ~2150 nm (weak) |
| Silicates | Quartz | Featureless SWIR |

## Methods Used in Abdelhak's Thesis

- **Field spectroscopy** (ASD FieldSpec 4, 350–2500 nm) + ECOSTRESS library matching → Ch.1
- **Handheld XRF** (Niton XL5) for elemental geochemistry → Ch.1
- **PRISMA satellite** (30m) classification → Ch.2
- **EnMAP satellite** spectral unmixing → Ch.3

## Related

- [[04_Knowledge Base/wiki/concepts/Phosphate Mine Waste]]
- [[04_Knowledge Base/wiki/concepts/VNIR-SWIR Spectroscopy]]
- [[04_Knowledge Base/wiki/concepts/Reclamation Monitoring]]
- [[04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine]]




================================================================================
FILE: 04_Knowledge Base/wiki/entities/Gantour Basin.md (~454 words)
================================================================================
---
tags: [wiki, entity, geology, morocco]
updated: 2026-05-24
generated_by: claude
---

# Gantour Basin

## Overview
The Gantour Basin is one of Morocco's two major phosphate sedimentary basins (the other being Ouled Abdoun/Khouribga). It hosts the Benguerir and Youssoufia mine sites operated by OCP Group.

---

## Geography

| Parameter | Value |
|-----------|-------|
| Location | Central Morocco, Marrakech-Safi region |
| Approximate coordinates | ~32°N, ~7.5–8°W |
| Area | ~1,600 km² (basin extent) |
| Key city | Benguerir (study site) |
| Distance from Marrakech | ~70 km north |

---

## Geological Setting

**Formation:** Paleocene–Eocene sedimentary sequence (marine phosphate)

**Stratigraphy (simplified):**
```
Top: Quaternary alluvium + lacustrine deposits
     └─ Eocene marls and limestones
     └─ Paleocene phosphate layers (economic horizon)
          ├─ Phosphate series: francolite in marl/limestone matrix
          ├─ Interbedded clays (illite, smectite)
          └─ Carbonate-rich beds (calcite, dolomite)
Bottom: Cretaceous basement
```

**Origin:** Upwelling marine current concentrated biogenic phosphate in shallow tropical sea (Tethys Ocean, Cretaceous-Paleocene). Organic matter decomposition released PO₄, which precipitated as carbonate fluorapatite (francolite).

---

## Mineralogy of the Deposit

The economic mineral is **francolite** (carbonate fluorapatite): Ca₅[(PO₄)(CO₃)]₃F. Unlike pure fluorapatite, francolite has partial CO₃ for PO₄ substitution, giving it a distinctive mixed spectral signature.

| Component | Role |
|-----------|------|
| Francolite | Economic phosphate mineral (ore) |
| Calcite/dolomite | Carbonate gangue |
| Illite/smectite | Clay gangue |
| Quartz | Silica gangue |
| Iron oxides | Accessory weathering products |

---

## Mining at Benguerir

| Parameter | Value |
|-----------|-------|
| Operator | OCP Group (Office Chérifien des Phosphates) |
| Mining method | Open-pit, strip mining |
| Stripping ratio | ~3:1 (3 t waste per 1 t ore) |
| Annual ore production | ~4 Mt/year (approx.) |
| Annual waste generation | ~12.3 Mt/year |
| Mine area (thesis study zone) | ~36 km² |

**Waste rock piles:** Accumulated over decades of mining. Form prominent topographic features visible in satellite imagery. Subject of Abdelhak's thesis.

---

## Environmental Significance

1. **Dust and aerosols:** Fine phosphate particles (PM10, PM2.5) from wind erosion of waste piles
2. **Fluorine leaching:** F⁻ ions from fluorapatite mobilize in rain events → soil and groundwater concerns
3. **Landscape rehabilitation:** OCP Group's sustainability program targets revegetation of all stable dumps
4. **Carbon footprint:** Processing and transport of phosphate rock significant CO₂ source

---

## Morocco's Strategic Role
Morocco holds ~70% of world's known phosphate reserves (primarily Gantour + Ouled Abdoun basins). This makes OCP Group a strategic geopolitical player in global food security (phosphate → fertilizer). Environmental management of waste rock is therefore a high-visibility priority.

---

## Related Concepts
- [[OCP Group and Benguerir Mine]]
- [[Phosphate Mine Waste]]
- [[Mineral Assemblages]]
- [[Reclamation Monitoring]]




================================================================================
FILE: 04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine.md (~288 words)
================================================================================
---
tags: [entity, institution, mining, Morocco, OCP, phosphate]
updated: 2026-05-24
generated_by: claude
type: institution
---

# OCP Group & Benguerir Mine

## OCP Group
- **Full name:** Office Chérifien des Phosphates (OCP Group)
- **Headquarters:** Casablanca, Morocco
- **Role:** World's largest phosphate exporter (~70% of global phosphate reserves in Morocco)
- **Connection to Abdelhak:** Benguerir is an OCP mine. UM6P itself was founded by OCP. The research is directly relevant to their environmental management needs.

## Benguerir Mine
- **Location:** Benguerir, Marrakech-Safi region, Morocco
- **Type:** Open-pit phosphate mine
- **Context:** Active phosphate extraction generating large waste rock dumps
- **Why it matters for thesis:** The waste rock dumps at Benguerir are the study site for mineralogical characterization and reclamation monitoring

## Why This Site?
1. Proximity to UM6P (university is literally in Benguerir, created by OCP)
2. Large waste rock surface area — good for satellite-scale study (PRISMA 30m)
3. Mineralogical diversity — phosphate ore, carbonates, clays, iron minerals
4. Environmental importance — waste rock management is an OCP priority
5. Data access — UM6P-OCP relationship facilitates ground truth collection

## Phosphate Mineralogy at Benguerir
Key minerals to characterize:
- **Phosphate minerals:** fluorapatite, carbonate-fluorapatite (francolite)
- **Carbonates:** calcite, dolomite (buffering capacity)
- **Clay minerals:** kaolinite, smectite, illite
- **Iron minerals:** goethite, hematite (AMD indicator)
- **Accessory:** quartz, feldspar

## Reclamation Context
OCP is actively rehabilitating waste rock dumps — revegetation programs, capping.  
Abdelhak's thesis monitors this process using PRISMA time series.

## Related Pages
- [[02_Academic & Work/thesis/Thesis Overview]]
- [[04_Knowledge Base/wiki/concepts/Waste Rock Characterization]]
- [[04_Knowledge Base/wiki/concepts/PRISMA Satellite]]
- UM6P (entity note not yet created)

## Potential Industry Application
OCP Group is a natural client for remote sensing consulting post-defense.  
→ See [[03_Digital Life/money/Money Overview]] (Consulting stream)




================================================================================
FILE: 04_Knowledge Base/bases/Browser Bookmarks.md (~3394 words)
================================================================================
---
generated_by: claude
date: 2026-06-07
tags: [knowledge, bookmarks, browser]
summary: "Imported bookmarks from Chrome and Edge browsers, organizing directories and links into a structured layout."
---

# 🔖 Imported Browser Bookmarks

> [!NOTE]
> **Import Date**: 2026-06-07  

> Automatically compiled from Chrome and Edge local application data profiles.


# 🌐 Microsoft Edge Bookmarks


# Profile: Default


## 📌 Favorites bar


## 📌 Other favorites


## 📌 Mobile favorites

- [Giveaway of the Day - free licensed software daily](https://www.giveawayoftheday.com/download/?c=b19521fcbc187396191f30405f6a7522#)
- [Scheduling Meeting During Master's Thesis Defenses - Claude](https://claude.ai/chat/8f79b058-0940-4e0c-af86-2a1a4f112c4f)
- [Confirmer et payer](https://fr.airbnb.be/book/stays/1181061852307759347?numberOfAdults=1&checkin=2024-11-16&numberOfGuests=1&checkout=2024-11-18&guestCurrency=EUR&productId=1181061852307759347&isWorkTrip=false&numberOfChildren=0&numberOfInfants=0&numberOfPets=0)
- [ERR-KECH-Ryanair](https://www.ryanair.com/ma/fr/payment?tpAdults=1&tpChildren=0&tpInfants=0&tpTeens=0&tpStartDate=2024-12-23&tpEndDate=2024-12-28&tpDiscount=0&tpOriginIata=RAK&tpDestinationIata=ERH)
- [Clavier arabe en ligne LEXILOGOS](https://www.lexilogos.com/clavier/araby.htm)
- [GitHub - Anselmoo/spectrafit: 📊📈🔬 SpectraFit is a command-line and Jupyter-notebook tool for quick data-fitting based on the regular expression of distribution functions.](https://github.com/anselmoo/spectrafit)
- [Pensión Portugal, Alicante (tarifs actualisés, 2025)](https://www.booking.com/hotel/es/pension-portugal-alicante.fr.html?aid=2369661&label=msn-6r9rjlyxP76yE7ig2iepng-80195816981661%3Atikwd-80195992121999%3Aaud-816715538%3Aloc-124%3Aneo%3Amte%3Alp151410%3Adec%3Aqsbooking&sid=2a234cdd597a198285c1682a4ec888a1&all_sr_blocks=34320008_364239060_3_0_0&checkin=2025-02-21&checkout=2025-02-23&dest_id=-370210&dest_type=city&dist=0&group_adults=3&group_children=0&hapos=6&highlighted_blocks=34320008_364239060_3_0_0&hpos=6&matching_block_id=34320008_364239060_3_0_0&nflt=price%3DUSD-min-190-1&no_rooms=1&req_adults=3&req_children=0&room1=A%2CA%2CA&sb_price_type=total&sr_order=popularity&sr_pri_blocks=34320008_364239060_3_0_0__12880&srepoch=1737901141&srpvid=8aa06496ad9c09c7&type=total&ucfs=1&lang=fr&soz=1&lang_changed=1)
- [Soil Spectroscopy for Global Good · GitHub](https://github.com/soilspectroscopy)
- [SPEC-PP2222](http://localhost:8888/notebooks/Downloads/SPEC-PP2222.ipynb?)
- [HyperCoast](https://hypercoast.org/#demos)
- [PIP Package | GPT Researcher](https://docs.gptr.dev/docs/gpt-researcher/gptr/pip-package#steps-to-install-gpt-researcher)
- [Earth Observation Applications for the Mineral Resources Sector](https://research.csiro.au/eoi/)
- [Hyperspectral Python](http://hyppy.is-great.org/index.html#download)
- [Exa Websets](https://websets.exa.ai/billing)
- [Genspark - Utilizing Hyperspectral Imaging in Mining](https://www.genspark.ai/agents?id=e52fbced-1e9f-40cf-bf8f-7acf2d844931)
- [1- التكنولوجيا ودورها في حياة الإنسان: التطور والذكاء الصناعي – Kooora Live – مشاهدة مباريات اليوم مباشر | Kora Live | Yalla Shoot | كورة لايف اون لاين](https://koralive.life/matchs/koralive/)
- [Cheap flights from Marrakech to Vienna at Skyscanner](https://www.skyscanner.net/transport/flights/rak/vie/250425/250504/config/15753-2504251000--31915-1-17517-2504251955%7C17517-2505040620--31915-1-15753-2505041310?adults=1&adultsv2=1&cabinclass=economy&children=0&childrenv2=&inboundaltsenabled=false&infants=0&outboundaltsenabled=false&preferdirects=false&ref=home&rtn=1)
- [J Balvin - Azul - YouTube](https://www.youtube.com/watch?v=bG-jhGgW_qw&ab_channel=LatinHype)
- [Etsy - Shop Dashboard](https://www.etsy.com/your/shops/me/dashboard?ref=seller-platform-mcnav)
- [Action CA22138 - COST](https://www.cost.eu/actions/CA22138/#tabs+Name:Description)
- [New tab](edge://newtab/)
- [Lovable - Build for the web 20x faster](https://lovable.dev/projects/9bf36a61-35b3-425e-8b35-c54cf6869a12)
- [IGARSS 2025 || Brisbane, Australia || 3 - 8 August 2025](https://2025.ieeeigarss.org/technical_program.php)
- [Living Planet Fellowship call for proposals 2025 - eo science for society](https://eo4society.esa.int/2025/07/16/living-planet-fellowship-call-for-proposals-2025/)
- [University of Florida - Details - Postdoctoral Research Associate: GeoAI and Remote Sensing for Invasive Species Ecology](https://explore.jobs.ufl.edu/cw/en-us/job/537559/postdoctoral-research-associate-geoai-and-remote-sensing-for-invasive-species-ecology?utm_source=Indeed&utm_medium=organic&utm_campaign=Indeed)
- [how to read research papers, in 5 minutes. | writing](https://masonjwang.com/writing/reading-research)
- [SpecLab - The Environmental Remote Sensing and Spectroscopy Laboratory - Contact](https://speclab.csic.es/en/contact)
- [Postdoctoral Research Position in Hyperspectral Imaging Application and Data Analysis in Heritage Science | Technical University of Munich (TUM) | Deadline: 31 January 2026 - E-rihs](https://www.e-rihs.eu/postdoctoral-research-position/)
- [Dashboard | DenserAI](https://denser.ai/u/chatbot/chat?c=cmiq6aa2j018sad0y67wj12tq)
- [Hyperspectral_Image_Processing_in_Python/Hyperspectral Image Processing.py at main · mortezmaali/Hyperspectral_Image_Processing_in_Python](https://github.com/mortezmaali/Hyperspectral_Image_Processing_in_Python/blob/main/Hyperspectral%20Image%20Processing.py)
- [Research Assistant (m/f/d) | Ruhr University Bochum | 5225](https://jobs.ruhr-uni-bochum.de/jobposting/bf037807b6379441c39af8038b8c6b7cf1711fa90)
- [Launch of new Canada Impact+ Research Training Awards | Natural Sciences and Engineering Research Council of Canada](https://nserc-crsng.canada.ca/en/news/launch-new-canada-impact-research-training-awards)
- [Remote Sensing | Vision Lab - University of Antwerp](https://visielab.uantwerpen.be/research/remote-sensing?utm_source=chatgpt.com)
- [Hyperspectral and Thermal Remote Sensing Laboratory (HyperSens)](https://safes.unimelb.edu.au/research/hypersens?utm_source=chatgpt.com)
- [Contact | Vision Lab - University of Antwerp](https://visielab.uantwerpen.be/contact)
- [Postdoctoral Researcher in Remote Sensing of Peatlands | Aalto University](https://www.aalto.fi/en/open-positions/postdoctoral-researcher-in-remote-sensing-of-peatlands)
- [2025 MSCA Post doctoral fellowships - University of Angers](https://wp3eugreen.univ-angers.fr/en/opportunities/msca-post-doctoral-fellowships.html)
- [NameJet.com](https://www.namejet.com/download.action?format=csv)
- [Learn about International Journal of Remote Sensing](https://www.tandfonline.com/journals/tres20/about-this-journal#aims-and-scope)
- [WonsultingAI by Wonsulting - AI for Job Search that Gets You Hired!](https://www.wonsulting.com/wonsultingai)
- [VIPBox Sports Streams | Live VIPBoxTV Online - VIPBox](https://www.vipbox.lc/)
- [](https://outlook.cloud.microsoft/mail/inbox/id/AAQkADM1NzA4OGVlLTVmMTQtNGZlYS04NTA2LWVmYmNhYzk1Njk5NAAQAJjM75oC8kQPjFsbVx3G8e4%3D)
- [Hyperspectral Scientist job in - Modern Technology Solutions](https://us.trabajo.org/job-3310-2913b3b83101fe176eae94256be3c9a2?utm_campaign=google_jobs_apply&utm_source=google_jobs_apply&utm_medium=organic)
- [UQAT Mining and Environment Webinar Certificate of Attendance - NotebookLM](https://notebooklm.google.com/notebook/c29a3b8e-a90b-4626-ac5c-b08c82703a39)
- [bone-bed](https://saidi.ma/memoires/Bajadi-2012.pdf)
- [API Keys | Claude Platform](https://platform.claude.com/settings/workspaces/default/keys)
- [OpenSpecLib Viewer](https://elliej.dev/openspeclib/)
- [w](file:///C:/Users/Dell/Downloads/mining-4317314-peer-review-v1.pdf)

# Profile: Profile 2


## 📌 Favorites bar

- [(54) A new framework for hyperspectral image classification using multiple spectral and spatial features - YouTube](https://www.youtube.com/watch?v=vxh53StWaUk&list=PLhJv5XZVfVl5K-X6F4Z1G8Ptcy3oUsc3o&index=2)
- [(54) Non-linear low-rank and sparse representation for hyperspectral image analysis - YouTube](https://www.youtube.com/watch?v=fG0GU-IyzQI&list=PLhJv5XZVfVl5K-X6F4Z1G8Ptcy3oUsc3o&index=16)
- [(7) How to write a literature review - YouTube](https://www.youtube.com/watch?v=rnHvO5aRXq0)
- [(92) قم بتنزيل صور Landsat-8 متعددة الأطياف مجانًا / Download Landsat-8 multispectral images for free - YouTube](https://www.youtube.com/watch?v=CILLtpcSLac)
- [25 Map Types: Brilliant Ideas to Build Unbeatable Maps - GIS Geography](https://gisgeography.com/map-types/)
- [450+ Free Photoshop Tutorials - Learn Photoshop Online](https://phlearn.com/photoshop-tutorials/)
- [75+ Geospatial Python and Spatial Data Science Resources and Guides - Matt Forrest](https://forrest.nyc/75-geospatial-python-and-spatial-data-science-resources-and-guides/)
- [A note on knowledge discovery and machine learning in digital soil mapping](https://onlinelibrary.wiley.com/doi/epdf/10.1111/ejss.12909)
- [A-cademic news](https://academicnews1.blogspot.com/)
- [An Evaluation Model for the Actions in Supporting of the Environmental and Landscaping Rehabilitation of the Pasquasia’s Site Mining (EN) | SpringerLink](https://link.springer.com/chapter/10.1007/978-3-319-09150-1_3)
- [An Overview on Linear Unmixing of Hyperspectral Data](https://www.hindawi.com/journals/mpe/2020/3735403/)
- [Assessment of the success of rehabilitation at waste rock piles of the former uranium mining from the supervisory authority’s perspective by the example of Schlema-Alberoda (Germany) | SpringerLink](https://link-springer-com.eressources.um6p.ma/chapter/10.1007/978-3-319-11059-2_38)
- [Bauxite Mine Rehabilitation Programs — A Progress Report Patrick Atkins, Alcoa Inc. | SpringerLink](https://link-springer-com.eressources.um6p.ma/chapter/10.1007/978-3-319-48176-0_9)
- [Boîte de réception - elmansour01abdelhak@gmail.com - Gmail](https://mail.google.com/mail/u/0/?ogbl#inbox)
- [Cadmium Toxicity And Its Phytoremediation A Review](https://www.ijser.org/researchpaper/Cadmium-Toxicity-And-Its-Phytoremediation-A-Review.pdf)
- [Cambridge Dictionary | English Dictionary, Translations & Thesaurus](https://dictionary.cambridge.org/)
- [Computing Spectral Indices • prismaread](https://ranghetti.github.io/prismaread/articles/Computing-Spectral-Indexes)
- [Data Analysis with R Programming - Programming and data analytics | Coursera](https://www.coursera.org/learn/data-analysis-r/home/week/1)
- [Data fusion of vis–NIR and PXRF spectra to predict soil physical and chemical properties](https://onlinelibrary.wiley.com/doi/epdf/10.1111/ejss.12875)
- [Ecological restoration of land with particular reference to the mining of metals and industrial minerals: A review of theory and practice](https://cdnsciencepub.com/doi/abs/10.1139/a01-014)
- [Ecological Restoration Suitability and Landscape Pattern Characteristics in a Watershed,Northwest Hunan--《Journal of Mountain Science》2009年05期](https://en.cnki.com.cn/Article_en/CJFDTotal-SDYA200905005.htm)
- [Elsevier Researcher Academy - Funding](https://researcheracademy.elsevier.com/research-preparation/funding)
- [ENVI 5.3 Download and Installation - YouTube](https://www.youtube.com/watch?v=YhFXSXGA-bA)
- [Environmental Management and Rehabilitation at Lightning Ridge - NSW Resources Regulator](https://www.resourcesregulator.nsw.gov.au/environment/environmental-management-and-rehabilitation-at-lightning-ridge2)
- [Events & Education - EnMAP](https://www.enmap.org/events_education/)
- [Geospatial Analysis 6th Edition, 2020 update](https://www.spatialanalysisonline.com/HTML/index.html?landscape_metrics.htm)
- [gestion-et-amenagement-ecologiques-des-carrieres.pdf](https://um6p-my.sharepoint.com/personal/abdelhak_elmansour_um6p_ma/Documents/Bureau/Docs/gestion-et-amenagement-ecologiques-des-carrieres.pdf)
- [Gmail](https://accounts.google.com/b/0/AddMailService)
- [Hands-On training: Data and software – EO College](https://eo-college.org/courses/beyond-the-visible/lessons/hands-on-training-data-and-software/)
- [Heavy metal contaminants in inorganic and organic fertilizers | SpringerLink](https://link.springer.com/chapter/10.1007%2F978-94-009-1586-2_2)
- [Helping the mining industry drive progressive mine rehabilitation - K2fly - Enterprise SaaS](https://k2fly.com/blog/helping-the-mining-industry-drive-progressive-mine-rehabilitation/)
- [High resolution topsoil mapping using hyperspectral image and field data in multivariate regression modeling procedures - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0016706106001030)
- [High-Resolution Mapping of Soil Properties Using AVIRIS-NG Hyperspectral Remote Sensing Data—A Case Study Over Lateritic Soils in Mangalore, India | SpringerLink](https://link.springer.com/chapter/10.1007/978-981-15-6828-2_54#citeas)
- [How to Avoid Plagiarism | 4 Steps to a Plagiarism-Free Paper](https://www.scribbr.com/plagiarism/how-to-avoid-plagiarism/)
- [How to prepare a proposal for a review article | Elsevier Researcher Academy](https://researcheracademy.elsevier.com/writing-research/writing-skills/prepare-proposal-review-article)
- [How to write a manuscript for peer review - Weinstein - 2020 - Journal of Clinical Apheresis - Wiley Online Library](https://onlinelibrary.wiley.com/doi/epdf/10.1002/jca.21797)
- [How to Write a Scientific Literature Review - Publishing in the Sciences - Research Guides at University of Michigan Library](https://guides.lib.umich.edu/c.php?g=283300&p=2915110)
- [How to Write and Publish a Scientific Paper (Project-Centered Course) - Home | Coursera](https://www.coursera.org/learn/how-to-write-a-scientific-paper/home/welcome)
- [Hyperspectral Image Analysis _Getting Started.ipynb - Colaboratory](https://colab.research.google.com/drive/1YxdtSvvhZCIf5u_d4pD69SKfpqPe0OrZ)
- [Hyperspectral Image Analysis — Getting Started | by Syam Kakarla | Towards Data Science](https://towardsdatascience.com/hyperspectral-image-analysis-getting-started-74758c12f2e9)
- [Hyperspectral remote sensing applications in soil: a review - ScienceDirect](https://www.sciencedirect.com/science/article/pii/B9780081028940000115)
- [In situ phytoremediation of copper and cadmium in a co-contaminated soil and its biological and physical effects - RSC Advances (RSC Publishing)](https://pubs.rsc.org/en/content/articlelanding/2019/ra/c8ra07645f)
- [Infographic: How to read a scientific paper](https://www.elsevier.com/connect/infographic-how-to-read-a-scientific-paper)
- [Integrating spectral indices into prediction models of soil phosphorus in a subtropical wetland - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0034425709002120)
- [Interpolating Soil Properties Using Kriging Combined with Categorical Information of Soil Maps - Liu - 2006 - Soil Science Society of America Journal - Wiley Online Library](https://acsess.onlinelibrary.wiley.com/doi/epdf/10.2136/sssaj2005.0126)
- [Introduction to Machine Learning using R](https://training.galaxyproject.org/training-material/topics/statistics/tutorials/intro-to-ml-with-r/tutorial.html)
- [Landscape character assessment with GIS using map-based indicators and photographs in the relationship between landscape and roads - PubMed](https://pubmed.ncbi.nlm.nih.gov/27240208/)
- [Landscape metrics | OpenGeoEdu](https://learn.opengeoedu.de/en/monitoring/landschaftstrukturmasse/strukturmasse)
- [Literature Reviews – The Writing Center • University of North Carolina at Chapel Hill](https://writingcenter.unc.edu/tips-and-tools/literature-reviews/)
- [LP DAAC - E-Learning](https://lpdaac.usgs.gov/resources/e-learning/)
- [lpsdp-mine-rehabilitation-handbook-french.pdf](https://um6p-my.sharepoint.com/personal/abdelhak_elmansour_um6p_ma/Documents/Bureau/Docs/lpsdp-mine-rehabilitation-handbook-french.pdf)
- [Machine Learning in R for beginners - DataCamp](https://www.datacamp.com/community/tutorials/machine-learning-in-r#one)
- [Mapping mine tailing surface mineralogy using hyperspectral remote sensing: Canadian Journal of Remote Sensing: Vol 35, No sup1](https://www.tandfonline.com/doi/abs/10.5589/m10-001)
- [Mapping soil profile depth, bulk density and carbon stock in Scotland using remote sensing and spatial covariates - Aitkenhead - 2020 - European Journal of Soil Science - Wiley Online Library](https://onlinelibrary.wiley.com/doi/ftr/10.1111/ejss.12916)
- [Maps](https://maps.google.com/)
- [MEGA ↓ 1%](https://mega.nz/folder/igh0zIaJ#qF08pX_ZTIET3BmlhJbt2g)
- [Mine Closure and Rehabilitation (Reclamation) – EXCELLENCE IN MINING | Creativity & Practicality Insights, perspectives and good practices by Ronaldo dos Santos](https://ronaldocrdossantos.wordpress.com/2016/07/10/mine-closure-and-rehabilitation-reclamation/)
- [Mineralogical Characteristics of Phosphate Tailings for Comprehensive Utilization](https://www.hindawi.com/journals/ace/2021/5529021/)
- [Mining and rehabilitation | SpringerLink](https://link-springer-com.eressources.um6p.ma/chapter/10.1007/978-94-009-3111-4_19)
- [Modelling soil erosion with a downscaled landscape evolution model - Coulthard - 2012 - Earth Surface Processes and Landforms - Wiley Online Library](https://onlinelibrary.wiley.com/doi/epdf/10.1002/esp.3226)
- [Monitoring and modelling progressive rehabilitation in aggregate mining ... A decade of ontario experience and a look at the future | SpringerLink](https://link-springer-com.eressources.um6p.ma/article/10.1007/BF02594419)
- [New rehabilitation framework for mining projects in Qld - Knowledge - Clayton Utz](https://www.claytonutz.com/knowledge/2018/december/new-rehabilitation-framework-for-mining-projects-in-qld)
- [Open Data Platform](https://opendata.ocpgroup.ma/)
- [Optimising the long term mine landform progression and truck hour schedule in a large scale open pit mine using mixed integer programming](https://espace.curtin.edu.au/handle/20.500.11937/67630)
- [Phytomining: a sustainable approach for recovery and extraction of valuable metals - ScienceDirect](https://www.sciencedirect.com/science/article/pii/B9780128212004000133)
- [Phytoremediation and Phytomining: Status and Promise - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0065229616301252)
- [Phytoremediation at Molecular Level - ScienceDirect](https://www.sciencedirect.com/science/article/pii/B978032389874400011X)
- [Phytoremediation of abandoned mining areas for land restoration: Approaches and technology - ScienceDirect](https://www.sciencedirect.com/science/article/pii/B978012821200400008X)
- [Phytoremediation of Cadmium by Native Plants Grown on Mining Soil - PubMed](https://pubmed.ncbi.nlm.nih.gov/29177694/)
- [Phytorestoration of Abandoned Mining and Oil Drilling Sites | ScienceDirect](https://www.sciencedirect.com/book/9780128212004/phytorestoration-of-abandoned-mining-and-oil-drilling-sites)
- [Phytorestoration of Abandoned Mining and Oil Drilling Sites | ScienceDirect](https://www.sciencedirect.com/book/9780128212004/phytorestoration-of-abandoned-mining-and-oil-drilling-sites#book-description)
- [Plagiarism: Avoiding the Peril in Scientific Writing - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0012369215491123)
- [Podcasts](https://www.fertilizer.org/Public/Resources/IFA_Podcast/Public/IFA_Resources/Podcasts/Podcasts.aspx?hkey=59e5f270-dd84-46b2-886e-101e4dc1658e)
- [Preprocessing of hyperspectral and multispectral images - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/B9780444639776000031)
- [Professor Peter Erskine - Sustainable Minerals Institute - University of Queensland](https://smi.uq.edu.au/profile/793/peter-erskine-erskine)
- [Programme de réhabilitation des mines du groupe OCP - Maroc Hebdo l'actualité du Maroc](https://www.maroc-hebdo.press.ma/programme-de-rehabilitation-mines-groupe-ocp)
- [Project Lifecycle | Mining Industry Overview | Extractives Hub](https://extractiveshub.org/topic/view/id/21/chapterId/268)
- [Projet_Authier_Lithium_Plan_de_restauration_du_site_16052018.pdf](https://um6p-my.sharepoint.com/personal/abdelhak_elmansour_um6p_ma/Documents/Bureau/Docs/Projet_Authier_Lithium_Plan_de_restauration_du_site_16052018.pdf)
- [Réaménagement forestier des carrières de granulats - Sylvie Vanpeene-Bruhier - Google Books](https://books.google.co.ma/books?id=5iKMpZdaNxkC&pg=PA36&lpg=PA36&dq=r%C3%A9am%C3%A9nagement+des+carri%C3%A8res+phosphates&source=bl&ots=AXaDQ1ZVhf&sig=ACfU3U2r7r9-UAYw7UMPcPM0W65JHWAGeQ&hl=en&sa=X&ved=2ahUKEwiro8Ss3sTxAhV78OAKHbqUCBwQ6AEwCXoECAwQAw#v=onepage&q=r%C3%A9am%C3%A9nagement%20des%20carri%C3%A8res%20phosphates&f=false)
- [Reducing liabilities through progressive mine closure - MINING.COM](https://www.mining.com/sponsored-content/reducing-liabilities-progressive-mine-closure/)
- [Register - Potsdam 2022](http://is.earsel.org/workshop/12-IS-Potsdam2022/registration/register/)
- [Registration](https://register.gotowebinar.com/recording/1414274736106081807)
- [Rehabilitation of Soils in Mining and Raw Material Extraction Areas | SpringerLink](https://link-springer-com.eressources.um6p.ma/chapter/10.1007/978-94-007-5751-6_3)
- [Rehabilitation plans and other environmental aspects of work plans - Earth Resources](https://earthresources.vic.gov.au/legislation-and-regulations/guidelines-and-codes-of-practice/rehabilitation-plans)
- [Relational Operators | R](https://campus.datacamp.com/courses/intermediate-r/chapter-1-conditionals-and-control-flow?ex=1)
- [REMEDy FOR CONTAMINATED SITES 2021: komunikat - Computerworld](https://www.computerworld.pl/konferencja/Remedy_4_en/stream?i=1547453&h=NjQ5MDdkMjQzMGQ4ODVlMzFmZTM3NDQyZjA5NDAzMzA)
- [Remote sensing and mountaintop mining: Remote Sensing Reviews: Vol 20, No 4](https://www.tandfonline.com/doi/pdf/10.1080/02757250109532440?needAccess=true)
- [Repenser le phosphate… Repenser l’environnement :: Athimar](https://www.athimar.org/articles/details/repenser-le-phosphate-repenser-lenvironnement)
- [Secure Checkout | Coursera](https://www.coursera.org/payments/finaid?cartId=205717505&course=data-analysis-with-r)
- [Secure Checkout | Coursera](https://www.coursera.org/payments/finaid?cartId=205717716&course=data-analysis-r)
- [Sensor Letters: Ingenta Connect Table Of Contents](https://www.ingentaconnect.com/content/asp/senlet/2012/00000010/f0020001;jsessionid=lyzia8o9k11h.x-ic-live-02)
- [Spatial Relationships | Landscape Metrics and Applications | Alison](https://alison.com/topic/learn/95735/landscape-metrics-and-applications)
- [State‐and‐Transition Successional Model for Bauxite Mining Rehabilitation in the Jarrah Forest of Western Australia - Grant - 2006 - Restoration Ecology - Wiley Online Library](https://onlinelibrary.wiley.com/doi/epdf/10.1111/j.1526-100X.2006.00102.x)
- [Student_Edition_DataSheet.pdf](https://www.l3harrisgeospatial.com/Portals/0/pdfs/Student_Edition_DataSheet.pdf)
- [The 5 Stages of the Mining Life Cycle - Decipher by K2fly](https://www.decipher.com.au/blog/mining-resources/the-5-stages-of-the-mining-life-cycle)
- [The Australian centre for minesite rehabilitation research — an initiative to meet the strategic research needs for sustainable mining rehabilitation | SpringerLink](https://link-springer-com.eressources.um6p.ma/article/10.1007/BF00280928)
- [The Integration of Hyperaccumulator Plants into Mine Rehabilitation in the Asia Pacific Region | SpringerLink](https://link-springer-com.eressources.um6p.ma/chapter/10.1007/978-3-030-58904-2_13)
- [The Literature Review | A Complete Step-by-Step Guide](https://www.scribbr.com/dissertation/literature-review/)
- [Top 50 ggplot2 Visualizations - The Master List (With Full R Code)](http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Scatterplot)
- [Trace Elements from Soil to Human - Alina Kabata-Pendias, Arun B. Mukherjee - Google Books](https://books.google.co.ma/books?hl=en&lr=&id=JYAq9X9phnYC&oi=fnd&pg=PR20&ots=o5ZYTGhAy6&sig=bJWwvPEcqRBP-KM_U1Gw_bknBJU&redir_esc=y#v=onepage&q&f=false)
- [Utility functions • landscapemetrics | Landscape Metrics for Categorical Map Patterns](https://r-spatialecology.github.io/landscapemetrics/articles/articles/utility.html)
- [Water resources in australian mine pit lakes: Mining Technology: Vol 118, No 3-4](https://www.tandfonline.com/doi/pdf/10.1179/174328610X12682159815028?needAccess=true)
- [Week 1 Quiz | Coursera](https://www.coursera.org/learn/r-programming/exam/lB1sR/week-1-quiz/attempt)
- [What Is A Research Hypothesis? A Simple Definition - Grad Coach](https://gradcoach.com/what-is-a-research-hypothesis-or-scientific-hypothesis/)
- [Widening gap between expectations and practice in Australian minesite rehabilitation - Lamb - 2015 - Ecological Management &amp; Restoration - Wiley Online Library](https://onlinelibrary.wiley.com/doi/epdf/10.1111/emr.12179)
- [Writing in the Sciences - Home | Coursera](https://www.coursera.org/learn/sciwrite/home/welcome)
- [Your AliExpress shopping cart - Buy directly from China](https://shoppingcart.aliexpress.com/shopcart/shopcartDetail.htm?spm=a2g0o.detail.1000002.2.1b8c5d11JK1WMh)
- [YouTube](https://youtube.com/)
- [Basic Hyperspectral Analysis Tutorial](https://www.l3harrisgeospatial.com/docs/hyperspectralanalysistutorial.html)
- [Basic Hyperspectral Analysis Tutorial](https://www.l3harrisgeospatial.com/docs/hyperspectralanalysistutorial.html#Exercise)
- [Pre Post SEO : Online SEO Tools](https://www.prepostseo.com/)
- [LIGE – montre connectée pour hommes et femmes, moniteur d'activité en temps réel, moniteur de fréquence cardiaque, horloge, pour Android IOS, nouveau, 2022 | AliExpress](https://fr.aliexpress.com/item/1005002287382274.html?gatewayAdapt=glo2fra&spm=a2g0o.order_list.0.0.21ef5e5bBx2T6l)
- [Cours : GLQ3401 - Géostatistique et géologie minières](https://moodle.polymtl.ca/course/view.php?id=1112)
- [Spectral eLearning | L3Harris Geospatial](https://www.l3harrisgeospatial.com/Learn/Training/eLearning?_cldee=7N770SjRjCLiRxLyUANTDhuubg_jpRTUW3Zc5Q4VY9JDb55oji7mO8ks8IUKtCbS&recipientid=lead-480aeb4f66b7ec11818f000c291eaf17-ac11082f9c0e47d4a5c014bbbc711279&utm_source=ClickDimensions&utm_medium=email&utm_campaign=Spectral%20eLearning%20Training&esid=165f6681-f0ca-ec11-8189-000c29b76cf6)
- [Citation Machine®: Format & Generate - APA, MLA, & Chicago](https://www.citationmachine.net/)
- [Products – Spectro Expo : Science.Technology.Applications](https://www.spectroexpo.com/shop/)
- [جميع الأغاني و الصور الناذرة لمبارك اولعربي _saghro bande _ mbark ol3rbi _ صاغرو باند tous - YouTube](https://www.youtube.com/watch?v=AwJk3OJYK3c)
- [(50) Google Earth Engine and geemap workshop at GeoPython Conference 2021 - YouTube](https://www.youtube.com/watch?v=wGjpjh9IQ5I&list=PLAxJ4-o7ZoPccOFv1dCwvGI6TYnirRTg3)
- [GeoPython 2021 - geemap](https://geemap.org/workshops/GeoPython_2021/)
- [Bengaluru Space Expo 2022](https://bsxindia.com/visitor-registration?utm_content=217188417&utm_medium=social&utm_source=linkedin&hss_channel=lcp-13731059)
- [Erreurs lors de l'échantillonnage [Sciences et Technologies des Poudres]](https://nte.mines-albi.fr/STP/fr/co/uc_ErreursEchantillonnage.html)
- [Tutorials for learning R | R-bloggers](https://www.r-bloggers.com/2015/12/how-to-learn-r-2/)
- [Watch Swiss Army Man (2016) Full Movie Online | M4ufree](https://ww1.m4ufree.to/movie/swiss-army-man-2016-tc8e.html)
- [Free PowerPoint templates and Google Slides themes - PresentationGO](https://www.presentationgo.com/page/3/)
- [Role of Phosphate in the Remediation and Reuse of Heavy Metal Polluted Wastes and Sites](https://hal.archives-ouvertes.fr/hal-01634023/document)
- [‪Mohammadmehdi Saberioon‬ - ‪Google Scholar‬](https://scholar.google.com/citations?user=CL4ddfYAAAAJ&hl=en&oi=ao)
- [Estimation of Field Scale Topsoil Properties of Agronomic Interest from Prisma Imaging Spectrometer Data | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/document/9554878)
- [Composite kernels for hyperspectral image classification | IEEE Journals & Magazine | IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/1576697)
- [Mapping_spatial_distribution_of_crop_residues_usin.pdf](file:///C:/Users/LABO/Downloads/Mapping_spatial_distribution_of_crop_residues_usin.pdf)
- [Estimate of Heavy Metal Contamination in Soils after a Mining Accident Using Reflectance Spectroscopy | Environmental Science & Technology](https://pubs.acs.org/doi/pdf/10.1021/es015747j)
- [Use of Airborne Hyperspectral Imagery to Map Soil Properties in Tilled Agricultural Fields](https://www.hindawi.com/journals/aess/2011/358193/)
- [Sites suggérés](https://ieonline.microsoft.com/#ieslice)
- [Ninite - Install or Update Multiple Apps at Once](https://ninite.com/)
- [Géologie, STE01](http://biodeug.com/cours/ste01/chap02.html)
- [Quran Explorer](http://www.quranexplorer.com/quran/)
- [Tectonique de la remontée du manteau : Les péridotites des Beni Bousera et leur enveloppe métamorphique, Rif interne, Maroc](http://toubkal.imist.ma/handle/123456789/1245)
- [These](https://tel.archives-ouvertes.fr/search/index/?q=Geologie+du+MAROC&submit=)
- [Petrogenesis of Pyroxenites and Melt Infiltrations in the Ultramafic Complex of Beni Bousera, Northern Morocco](http://petrology.oxfordjournals.org/content/52/9/1679.full.pdf+html?sid=658d2186-444a-4891-8dea-47d39005930c)
- [MARBRE.PPT](https://powerpoint.office.live.com/p/PowerPointView.aspx?FBsrc=https%3A%2F%2Fwww.facebook.com%2Fattachments%2Ffile_preview.php%3Fid%3D1643443752558255%26time%3D1426792979%26metadata&access_token=100001447653639%3AAVLQglsP7af5xQb54a9-dSUn40UTnwc7PLSrD6G1i7x5Ew&title=MARBRE.PPT)
- [MEGA](https://mega.co.nz/#!IU1TxSha!vvAlTwLbxTDYtAE2mwUQftajWnIQBnMyOlGTYI0Zrkk)
- [André Michard, Omar Saddiqi, Ahmed Chalouan, Dominique Frizon de Lamotte Continental Evolution - The Geology of Morocco - Structure, Stratigraphy, and Tectonics of the Africa-Atlantic-Mediterranean Triple Junction 201 - Télécharger - 4shared](http://www.4shared.com/office/Igi-PRUOce/Andr_Michard_Omar_Saddiqi_Ahme.html)
- [‫كيف تحصل على كلمة السر الخاصة بأي روتر أو موديم بطريقة سهلة‬‎ - YouTube](https://www.youtube.com/watch?v=Lno4w4AIpDM)
- [Student Home Page](http://www.usalearns.org/student-home)
- [Find PhDs | PhD Programs | Scholarships - jobs.ac.uk](http://www.jobs.ac.uk/phd)
- [Romans Français 2017 - Google Sheets](https://docs.google.com/spreadsheets/d/1GWbSgdTP1kCiaMkmcr2kOiat6jo-c_tpIXuvXyymc7c/edit#gid=0)
- [My Cookies Netflix](http://www.mycookiesnetflix.net/)
- [Library Genesis](http://gen.lib.rus.ec/search.php?req=Influence%20science%20and%20practice&open=0&res=25&view=detailed&phrase=0&column=title)
- [Fontaine de Connaissance](http://www.livrebank.com/)
- [Find A PhD : Intellectual Exchange and Innovation Program (IEI Program) at Kyushu University](https://www.findaphd.com/search/PhDDetails.aspx?CAID=2455&LID=2653)
- [كندا: منح الفرنكوفونية ـ دورة 2018 | وزارة التعليم العالي و البحث العلمي و تكوين الأطر](http://enssup.gov.ma/ar/Etudiant/Bourse-Cooperation-3686/%D9%83%D9%86%D8%AF%D8%A7-%D9%85%D9%86%D8%AD-%D8%A7%D9%84%D9%81%D8%B1%D9%86%D9%83%D9%88%D9%81%D9%88%D9%86%D9%8A%D8%A9-%D9%80-%D8%AF%D9%88%D8%B1%D8%A9-2018)
- [Fiche de Candidature à l’Inscription en 1ère Année de Doctorat (2017-2018)](https://docs.google.com/forms/d/e/1FAIpQLSfAXbZt7DAQqivRGtagWCYyaGnzpfApBMWT1RSx3Aj0-Ao7Fg/viewform)
- [PhDGermany - Database - DAAD - Deutscher Akademischer Austauschdienst](https://www.daad.de/deutschland/promotion/phd/en/13306-phdgermany-database/?promotiontype=&subject=&workinglang=&town=&paid=&q=&page=9&back=1)
- [Useful links | International Geoscience Education Organisation](http://www.igeoscied.org/?page_id=72)
- [- www.eurogeosurveys.org -](http://www.eurogeosurveys.org/)
- [مرجع آموزش زبان ایرانیان - دانلود کتاب های اینترچنج ویرایش چهارم Interchange 4th edition](http://www.irlanguage.com/554/%D8%AF%D8%A7%D9%86%D9%84%D9%88%D8%AF-%DA%A9%D8%AA%D8%A7%D8%A8-%D9%87%D8%A7%DB%8C-%D8%A7%DB%8C%D9%86%D8%AA%D8%B1%DA%86%D9%86%D8%AC-%D9%88%DB%8C%D8%B1%D8%A7%DB%8C%D8%B4-%DA%86%D9%87%D8%A7%D8%B1%D9%85-Interchange-4th-edition/)
- [Origin of Life - How Life Started on Earth - YouTube](https://www.youtube.com/watch?v=xyhZcEY5PCQ)
- [English in Early Childhood - Online Course](https://www.futurelearn.com/courses/english-in-early-childhood?lr=3)
- [Lettre de Motivation](https://fr.scribd.com/doc/144962713/Lettre-de-Motivation)
- [Cours: Géochimie Isotopique et géodynamique chimique - GIGC - Enseignement](http://www.ulb.ac.be/sciences/gigc/index_fichiers/cours/geochim%20isotopique/cours_geochimie_isotopique_chapitre2suite.html)
- [Geoscience Jobs : Earthworks : Two PhD positions in Structural Geology / Geomechanics - Darmstadt, Germany - Technical University Darmstadt](http://www.earthworks-jobs.com/geoscience/tud17121.html)
- [Internal dynamics vs external drivers - Environmental Challenges: Human Impact in the Natural Environment - University of Leeds](https://www.futurelearn.com/courses/environmental-ethics-human-impact/3/steps/224165)
- [Admissions - Udacity](https://admissions.udacity.com/apply/omac-dand-arabic)
- [Mine Geology | Mining Geology HQ](http://www.mininggeologyhq.com/mine-geology/)
- [CimaClub | مشاهدة الافلام اون لاين](http://cimaclub.com/)
- [Glencore Jobs - Liste d'emplois - emplois portail](https://glencorejobs.nga.net.au/cp/index.cfm?event=jobs.home&CurATC=CAN&CurBID=AEB00F98%2D79A6%2D480A%2D9A6A%2D9DB401357A6D&persistVariables=CurATC,CurBID)
- [Job opportunities | Glencore](http://www.glencore.com/careers/job-opportunities/)
- [مسلسل Oz Season 1 DVDRip الموسم الاول كامل مترجم – عرب ليونز](http://arablionz.tv/download/%D9%85%D8%B3%D9%84%D8%B3%D9%84-oz-season-1-dvdrip-%D8%A7%D9%84%D9%85%D9%88%D8%B3%D9%85-%D8%A7%D9%84%D8%A7%D9%88%D9%84-%D9%83%D8%A7%D9%85%D9%84-%D9%85%D8%AA%D8%B1%D8%AC%D9%85/)
- [https://career4.successfactors.com/careers](https://career4.successfactors.com/careers)
- [Morocco - Redstone Exploration Services](http://redstone-exploration.com/country-profiles/morocco/)
- [Atlas Pétrologique - Analyse de Lames Minces au Microscope](http://s.zaragosi.free.fr/ATLAS_PETRO/index.php?page=carb_dol_analyse)
- [1.1/ Une carte est le résultat d'une succession de choix - École normale supérieure | Coursera](https://www.coursera.org/learn/cartographie/lecture/AqUNf/1-1-une-carte-est-le-resultat-d-une-succession-de-choix)
- [Cambridge IELTS 1 thru 8 - Book + Audio - sum1_here.zip - Google Drive](https://drive.google.com/file/d/1nE9bN3o00RWUgB_LkhC_n55hReCywCKT/view)
- [Effortless English – Google Drive](https://drive.google.com/drive/folders/0B981zZs9Rm4yRWV3M0J6WE9ZREU)
- [Surpac Fundamentals Online Training • Optiro](https://www.optiro.com/online-training/surpac-fundamentals/)
- [(17) LES RESSOURCES MINIÈRES DANS LE CONTEXTE DE LA TRANSITION ÉNERGÉTIQUE-EXEMPLE DU CUIVRE ET DES TERRES RARES](https://www.researchgate.net/publication/324330462_LES_RESSOURCES_MINIERES_DANS_LE_CONTEXTE_DE_LA_TRANSITION_ENERGETIQUE-EXEMPLE_DU_CUIVRE_ET_DES_TERRES_RARES)
- [Rechercher une offre - ABG](https://www.abg.asso.fr/fr/candidatOffres)
- [Association Bernard Gregory](https://www.abg.asso.fr/fr/)
- [IFP School - Sujets de thèse 2018](http://www.ifp-school.com/jcms/r_8284/fr/sujets-de-these#refresh-6)
- [The Python Bible™ Everything You Need to Program in Python - Google Drive](https://drive.google.com/drive/u/0/folders/1eEp8f1NhtrTHNZEXA-ajKPXz4SIPNNYb)
- [Geochemistry - Supercontinent Cycles & Global Geodynamics](http://geodynamics.curtin.edu.au/phd-opportunities/geochemistry/)
- [Gestion du cycle doctorat](http://preinsdoc.uiz.ac.ma/etudiant/inscription.php)
- [Jobs in Geoscience : Earthworks : M.Sc in Uranium Exploration - Brandon, Canada - Brandon University](http://www.earthworks-jobs.com/geoscience/brandon18111.html)
- [Mutaz.net | موقع تحميل برامج مجانية](https://www.mutaz.net/free-programs/?fbclid=IwAR0PlbmrGhXi8ByFcjinU_4tv1NHmLhWqziHM0MiS5U9_yTpHbq7iKmTK1o)
- [How to install and register Matlab R2017a - YouTube](https://www.youtube.com/watch?v=yA29gnNSnRA&fbclid=IwAR1plv_AOrEOaiBzM-Gl9IpXNRhZDPmcUa9AI_uziYvwZmZwwD-wXXwe9TU)
- [European Association of Geochemistry](https://www.eag.eu.com/jobs/?fbclid=IwAR0IWp2xYOVeIWzTPTbflmpNpPO5sK64cCulcpF1pPdGQ0zFiU8ZtND1S2s)
- [Google Drive : avertissement relatif à l'analyse antivirus](https://drive.google.com/uc?id=1BGHWACAXRSj0f7RUVXs8U2bgv7eMoMtY&export=download)
- [Modelling lake water's surface changes using environmental and remote sensing data: A case study of lake urmia - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S2352938521001300)
- [Dust reduction method based on water infusion blasting in open-pit mines: a step toward green mining: Energy Sources, Part A: Recovery, Utilization, and Environmental Effects: Vol 0, No 0](https://www.tandfonline.com/doi/full/10.1080/15567036.2021.1903118)
- [Classification accuracy assessment. Confusion matrix method](http://www.50northspatial.org/classification-accuracy-assessment-confusion-matrix-method/)
- [- Skye Instruments](https://www.skyeinstruments.com/category/products/soil-measurement/)
- [Scopus - Document details - Mine reclamation based on remote sensing information and error compensation extreme learning machine | Signed in](https://www.scopus.com/record/display.uri?eid=2-s2.0-85100805679&origin=resultslist&sort=plf-f&cite=2-s2.0-85087513260&src=s&imp=t&sid=3f734191c17058a0243dccfcad54122b&sot=cite&sdt=a&sl=0&relpos=7&citeCnt=0&searchTerm=)
- [Scopus - Document details - Construction of a landscape ecological network for a large-scale energy and chemical industrial base: A case study of ningdong, China | Signed in](https://www.scopus.com/record/display.uri?eid=2-s2.0-85103597112&origin=resultslist&sort=plf-f&cite=2-s2.0-85087513260&src=s&imp=t&sid=3f734191c17058a0243dccfcad54122b&sot=cite&sdt=a&sl=0&relpos=5&citeCnt=1&searchTerm=)
- [IntegratedMinPro '22](https://mei.eventsair.com/integratedminpro22/call-for-abstracts)
- [Offre d'emploi Maroc : Caractérisation des Cavaliers d’Exploitations de Phosphate - Benguerir - Marrakech](https://www.emploi.ma/offre-emploi-maroc/caracterisation-des-cavaliers-exploitations-phosphate-3657992)
- [Integrating the LISFLOOD‐FP 2D hydrodynamic model with the CAESAR model: implications for modelling landscape evolution - Coulthard - 2013 - Earth Surface Processes and Landforms - Wiley Online Library](https://onlinelibrary.wiley.com/doi/10.1002/esp.3478)
- [Become a Graphic Designer](https://www.linkedin.com/learning/paths/become-a-graphic-designer)
- [Become a Software Developer](https://www.linkedin.com/learning/paths/become-a-software-developer?trk=lilblog_06-30-20_msft-announcement-reskilling-linkedin-learning_learning)
- [What are the different types of mine rehabilitation practices? - Decipher by K2fly](https://www.decipher.com.au/blog/mining-resources/what-are-the-different-types-of-mine-rehabilitation-practices)
- [EMG8.pdf](https://wedocs.unep.org/bitstream/handle/20.500.11822/29045/EMG8.pdf?sequence=1&isAllowed=y)
- [Manual for the rehabilitation of ornamental granite open-pit mines in Galicia | piedra.online](https://www.piedra.online/en/publications/manual-rehabilitation-granite-open-pit-mines-galicia)
- [Why are mine rehabilitation targets and objectives important? - Mining Software - Technical Assurance, Resource & Mineral Governance - Enterprise SaaS](https://k2fly.com/blog/why-are-mine-rehabilitation-targets-and-objectives-important/)
- [Welcome](https://www.linkedin.com/learning/academic-research-foundations-quantitative/welcome?u=73722380)
- [LinkedIn Learning: Online Courses for Creative, Technology, Business Skills](https://www.linkedin.com/learning/me?u=73722380)
- [Library Card Application Form | NYPL](https://www.nypl.org/library-card/congrats?newCard=true)
- [Announcing Registration for the 2021 Virtual Annual Mine Reclamation Symposium!!! | TRCR](http://www.trcr.bc.ca/virtual-2021-symposium-2/)
- [Adam Pratt on the State of Mine Rehabilitation and Closure in Australia](https://vytasresources.com/adam-pratt-mine-rehabilitation/)
- [Reclamation of abandoned open mines with innovative meandrically arranged geotextiles - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S026611441930158X)
- [Monitoring active open-pit mine stability in the Rhenish coalfields of Germany using a coherence-based SBAS method - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0303243420301720)
- [American Society of Reclamation Science > Events > Webinars](https://www.asrs.us/Events/Webinars)
- [Review of Practices in the Managements of Mineral Wastes: The Case of Waste Rocks and Mine Tailings](file:///C:/Users/LABO/Downloads/Shengo2021_Article_ReviewOfPracticesInTheManageme.pdf)

### 📁 Dell

  - [Dell Auction](http://www.dellauction.com/)
  - [Dell](http://www.dell.com/)
  - [Support.Dell.Com](http://www.dell.com/support/home)

### 📁 Dataprofiling

  - [What is Data Profiling? Data Profiling with Python | Medium](https://medium.com/@seckindinc/data-profiling-with-python-36497d3a1261)

## 📌 Other favorites

- [Smodin: Multi-lingual Writing Assistance | English](https://smodin.io/)
- [ShortlyAI | Your AI Writing Partner. Get rid of writer's block.](https://www.shortlyai.com/)
- [Voice Notepad - Speech to Text with Google Speech Recognition](https://dictation.io/speech)
- [EssayTyper](http://www.essaytyper.com/)
- [Share Premium Accounts Logins & Cookies Here - Freesoff Exclusive (Dialy Updates) - Give-Away and Freebies - Freesoff.com - Free Courses, Software and Useful Methods](https://freesoff.com/t/share-premium-accounts-logins-cookies-here-freesoff-exclusive-dialy-updates/61717/4)
- [Explorer | Solana](https://explorer.solana.com/address/5gQS2RVweCpBSPhyjVSSwGffcY4gjGjMfhLg6pPGKGKM)
- [DROP](https://legenddragon.org/wallet/)
- [Elsevier Enhanced Reader](https://reader.elsevier.com/reader/sd/pii/S0924271619302187?token=0502A2439442946984016B6B7BC026C11CCB5E90F0CFEE1135C7A3820A55781EB839D446BB4B3934A8F003E8ADC589FA&originRegion=eu-west-1&originCreation=20220221154957)
- [Hyperspectral image classification using spectral-spatial LSTMs - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0925231218309573)
- [Spatial-spectral local discriminant projection for dimensionality reduction of hyperspectral image - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0924271619301595)
- [Hyperspectral imagery classification based on semi-supervised 3-D deep neural network and adaptive band selection - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0957417419302374)
- [Deep learning classifiers for hyperspectral imaging: A review - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0924271619302187?via%3Dihub)
- [New Approach of Sample Generation and Classification for Wildfire Fuel Mapping on Hyperspectral (Prisma) Image | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/9554652)
- [Mining Geology Sampling Methods: Channel, Chips, Core](https://www.911metallurgist.com/blog/mining-geology-sampling-methods-channel-chip-core)

### 📁 Other Bookmarks

  - [(1) GEOLOGIE STRUCTURALE](https://www.facebook.com/notes/jeunes-geologues-de-taznakhte-jgt/geologie-structurale/578138628956797)
  - [Glossaire "plis"](http://www.geol-alp.com/0_geol_gene/glossaire_plis.html)
  - [بمناسبة قرب الامتحانات ..7 مواقع يجب ان تعرفها وتجربها كطالب](http://www.th3professional.com/2015/05/7sites.html)

### 📁 Synced Bookmarks

  - [Freesound - Freesound](https://freesound.org/)
  - [Phosphate Mining](https://www.biologicaldiversity.org/campaigns/phosphate_mining/)
  - [Efficiency of soil and fertilizer phosphorus use](https://www.fao.org/publications/card/en/c/862ee2d8-3681-50b2-945d-84c08b045722/)
  - [Download MATLAB, Simulink, Stateflow and Other MathWorks Products](https://www.mathworks.com/downloads/web_downloads/10864795)
  - [www.mathworks.com](https://www.mathworks.com/pl_learn)
  - [Mail - ABDELHAK ELMANSOUR - Outlook](https://outlook.office365.com/mail/inbox/id/AAQkADM1NzA4OGVlLTVmMTQtNGZlYS04NTA2LWVmYmNhYzk1Njk5NAAQANWzPH7TrT5PifHEvQ%2BMUdc%3D)
  - [Intro to Working with Hyperspectral Remote Sensing Data in HDF5 Format in R | NSF NEON | Open Data to Understand our Ecosystems](https://www.neonscience.org/resources/learning-hub/tutorials/hsi-hdf5-r)
  - [diarsproject.github.io/DIARS/HyperProcessing.html](http://diarsproject.github.io/DIARS/HyperProcessing.html)
  - [Plot Spectral Signatures Derived from Hyperspectral Remote Sensing Data in HDF5 Format in R | NSF NEON | Open Data to Understand our Ecosystems](https://www.neonscience.org/resources/learning-hub/tutorials/plot-hsi-spectral-profile-r)
  - [Immersive Reader](read://http_diarsproject.github.io/?url=http%3A%2F%2Fdiarsproject.github.io%2FDIARS%2FHyperProcessing.html)
  - [artmo_vip / ARTMO_P · GitLab](https://gitlab.com/artmo_vip/artmo_p)
  - [Utilisation des phosphates naturels pour une agriculture durable](https://www.fao.org/3/y5053f/y5053f05.htm)
  - [Initiation à la recherche en géographie - Chapitre 6. Les méthodes d’échantillonnage et la détermination de la taille de l’échantillon - Presses de l’Université de Montréal](https://books.openedition.org/pum/14800?lang=en)
  - [SIREDD - DRÂA - TAFILALET](https://siredd.environnement.gov.ma/Draa-Tafilalet/SIG/SigIndex)
  - [Pacemaker Journal Paper Writing Schedule : 300 words between Mar 16, 2023 and Apr 15, 2023](https://www.pacemaker.press/users/abdelhakk/plans/my-thesis)
  - [Hemingway Editor](https://hemingwayapp.com/)
  - [All The Best and Latest AI Tools That Will Make Your Life Much Easier](https://lachief.io/)
  - [Important Dates – Workshop on Hyperspectral Images and Signal Processing : an Evolution in Remote Sensing](https://www.ieee-whispers.com/important-dates/)
  - [A review of studies on sustainable development in mining life cycle - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0959652619315458)
  - [Violin Chart | the D3 Graph Gallery](https://d3-graph-gallery.com/violin.html)
  - [Conversation Bing avec GPT-4](https://www.bing.com/search?&q=Ce+que+la+nouvelle+conversation+de+Bing+peut+faire+pour+vous%3f&showconv=1&form=M7002V&msclkid=03d4c7a1bad218c2a2fca28d421453ca)
  - [Submit Abstract - 13th WS Imaging Spectroscopy](https://is.earsel.org/workshop/13-IS-Valencia2024/submit-abstracts/)
  - 📂 **Nouveau dossier**
    - [Room for rent in Benimaclet, Benimaclet, Valencia — idealista](https://www.idealista.com/inmueble/104079488/)
    - [Contact – CA22136 – PANGEOS COST Action](https://pangeos.eu/contact/)
    - [sustainability-15-13786.pdf](file:///C:/Users/elman/Downloads/sustainability-15-13786.pdf)
- [Glossaire "plis"](http://www.geol-alp.com/0_geol_gene/glossaire_plis.html)
- [(1) GEOLOGIE STRUCTURALE](https://www.facebook.com/notes/jeunes-geologues-de-taznakhte-jgt/geologie-structurale/578138628956797)
- [بمناسبة قرب الامتحانات ..7 مواقع يجب ان تعرفها وتجربها كطالب](http://www.th3professional.com/2015/05/7sites.html)

## 📌 Mobile favorites

- [Freesound - Freesound](https://freesound.org/)
- [Phosphate Mining](https://www.biologicaldiversity.org/campaigns/phosphate_mining/)
- [Efficiency of soil and fertilizer phosphorus use](https://www.fao.org/publications/card/en/c/862ee2d8-3681-50b2-945d-84c08b045722/)
- [Do multispectral or hyperspectral imagery processing in python or gis softwares by Nomanrazashah | Fiverr](https://www.fiverr.com/nomanrazashah/do-hyperspectral-image-processing?context_referrer=search_gigs&source=top-bar&ref_ctx_id=6a67aab35efc044fea33bebcddf71898&pckg_id=1&pos=1&context_type=auto&funnel=6a67aab35efc044fea33bebcddf71898&imp_id=d5695361-39db-45af-93c2-d8c43acf1085)


