---
generated_by: claude
date: 2026-06-10
tags: [knowledge, compiled, notebooklm, wiki]
summary: "Compiled notes for Wiki theme: Wiki index, concepts, entities, and literature references."
---

# Abdelhak EL MANSOUR — Compiled Wiki

> This document is a consolidated export of Abdelhak EL MANSOUR's Wiki notes.
> Theme summary: Wiki index, concepts, entities, and literature references.


================================================================================
FILE: 04_Knowledge Base/wiki/Flashcards — Research Concepts.md (~1604 words)
================================================================================
---
tags:
  - flashcards
  - hyperspectral
  - remote-sensing
  - research
  - system
  - thesis
  - topic/system
generated_by: claude
date: 2026-06-07
type: system-note
status: active
created: '2026-06-08'
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


---

*Related: [[04_Knowledge Base/wiki/concepts/Hyperspectral Imaging|Hyperspectral Imaging]] · [[04_Knowledge Base/wiki/concepts/PRISMA Satellite|PRISMA]] · [[04_Knowledge Base/wiki/concepts/EnMAP Satellite|EnMAP]] · [[02_Academic & Work/thesis/Thesis MOC|Thesis MOC]] · [[02_Academic & Work/thesis/defense-prep/Flashcards — Defense|Flashcards — Defense]]*



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC - A-C.md (~357 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - range-a-c
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Sub-MOC for literature sources in alphabetical range A-C.
---

# 📚 Literature Index (A-C)

> Part 1 of the literature index, covering references from **abdolmalekiOreWasteDiscriminationUsing2022** to **clarkReflectanceSpectroscopyQuantitative1984b**.
> Back to [[Literature MOC|Master Literature MOC]].

## 📋 literature Notes

| Filename | Link |
| :--- | :--- |
| `abdolmalekiOreWasteDiscriminationUsing2022` | [[abdolmalekiOreWasteDiscriminationUsing2022]] |
| `achemrkTrackingQuarterCenturySpatioTemporal2026` | [[achemrkTrackingQuarterCenturySpatioTemporal2026]] |
| `acitoAtmosphericCompensationPRISMA2021` | [[acitoAtmosphericCompensationPRISMA2021]] |
| `acitoAtmosphericCompensationPRISMA2021a` | [[acitoAtmosphericCompensationPRISMA2021a]] |
| `agrawalEvaluatingPerformancePRISMA2023` | [[agrawalEvaluatingPerformancePRISMA2023]] |
| `allowayHeavyMetalsSoils2013` | [[allowayHeavyMetalsSoils2013]] |
| `alonsoDataProductsQuality2019` | [[alonsoDataProductsQuality2019]] |
| `alvesRevisitingRamanSpectra2023` | [[alvesRevisitingRamanSpectra2023]] |
| `amarMineWasteRock2023` | [[amarMineWasteRock2023]] |
| `amarWasteRockReprocessing2022` | [[amarWasteRockReprocessing2022]] |
| `amraniValorizationPhosphateMine2019` | [[amraniValorizationPhosphateMine2019]] |
| `anjjarPhosphateSeriesBenguerir` | [[anjjarPhosphateSeriesBenguerir]] |
| `araujoRecyclingReuseMine2022` | [[araujoRecyclingReuseMine2022]] |
| `aubineauHighlyVariableContent2022` | [[aubineauHighlyVariableContent2022]] |
| `aubineauPhosphateD13CorgChemostratigraphy2024` | [[aubineauPhosphateD13CorgChemostratigraphy2024]] |
| `audebertDeepLearningClassification2019` | [[audebertDeepLearningClassification2019]] |
| `bahhouUsePhosphateMine2021` | [[bahhouUsePhosphateMine2021]] |
| `barlowStatisticalInferenceOrder1972` | [[barlowStatisticalInferenceOrder1972]] |
| `barlowStatisticalInferenceOrder1980` | [[barlowStatisticalInferenceOrder1980]] |
| `bayoussefUseClaysByproducts2021` | [[bayoussefUseClaysByproducts2021]] |
| `bendorReflectanceMeasurementsSoils2015` | [[bendorReflectanceMeasurementsSoils2015]] |
| `bendorReflectanceMeasurementsSoils2015a` | [[bendorReflectanceMeasurementsSoils2015a]] |
| `benjaminiControllingFalseDiscovery1995` | [[benjaminiControllingFalseDiscovery1995]] |
| `benjaminiControllingFalseDiscovery1995a` | [[benjaminiControllingFalseDiscovery1995a]] |
| `bioucas-diasHyperspectralUnmixingOverview2012` | [[bioucas-diasHyperspectralUnmixingOverview2012]] |
| `bishopInfraredSpectroscopicAnalyses1994` | [[bishopInfraredSpectroscopicAnalyses1994]] |
| `bishopReflectanceEmissionSpectroscopy2008` | [[bishopReflectanceEmissionSpectroscopy2008]] |
| `boardmanjosephw.AUTOMATINGSPECTRALUNMIXING` | [[boardmanjosephw.AUTOMATINGSPECTRALUNMIXING]] |
| `BoardmanJWKruse` | [[BoardmanJWKruse]] |
| `boardmanMAPPINGTARGETSIGNATURES` | [[boardmanMAPPINGTARGETSIGNATURES]] |
| `boardmanMappingTargetSignatures1995` | [[boardmanMappingTargetSignatures1995]] |
| `bosseAssessmentPhosphateLimestone2013` | [[bosseAssessmentPhosphateLimestone2013]] |
| `boujoContributionLetudeGeologique1976` | [[boujoContributionLetudeGeologique1976]] |
| `bourazzaRestorationPhosphateMined2025` | [[bourazzaRestorationPhosphateMined2025]] |
| `bourazzaRestorationPhosphateMined2025a` | [[bourazzaRestorationPhosphateMined2025a]] |
| `bradshawRestorationMinedLands1997` | [[bradshawRestorationMinedLands1997]] |
| `breimanRandomForests2001` | [[breimanRandomForests2001]] |
| `bressanEvaluationMachineLearning2020` | [[bressanEvaluationMachineLearning2020]] |
| `buzziMappingChangesRecovering2014` | [[buzziMappingChangesRecovering2014]] |
| `c.heckerSpectralAbsorptionFeature2019` | [[c.heckerSpectralAbsorptionFeature2019]] |
| `chabrillatEnMAPSpaceborneImaging2024` | [[chabrillatEnMAPSpaceborneImaging2024]] |
| `chakrabortySpectralSpatialComparison2024` | [[chakrabortySpectralSpatialComparison2024]] |
| `charbaouiNewInsightsGeophysical2023` | [[charbaouiNewInsightsGeophysical2023]] |
| `charbaouiNewInsightsGeophysical2023a` | [[charbaouiNewInsightsGeophysical2023a]] |
| `chein-ichangSpectralInformationDivergence1999` | [[chein-ichangSpectralInformationDivergence1999]] |
| `chenIntegratingVisibleNearinfrared2010` | [[chenIntegratingVisibleNearinfrared2010]] |
| `chenXGBoostScalableTree2016` | [[chenXGBoostScalableTree2016]] |
| `chindongMultiSensorMachineLearning2025` | [[chindongMultiSensorMachineLearning2025]] |
| `chlahbiGeologicalGeomechanicalCharacterization2023` | [[chlahbiGeologicalGeomechanicalCharacterization2023]] |
| `choeMappingHeavyMetal2008` | [[choeMappingHeavyMetal2008]] |
| `clarkHighSpectralResolution1990` | [[clarkHighSpectralResolution1990]] |
| `clarkHighSpectralResolution1990a` | [[clarkHighSpectralResolution1990a]] |
| `clarkHighSpectralResolution1990b` | [[clarkHighSpectralResolution1990b]] |
| `clarkHighSpectralResolution1990c` | [[clarkHighSpectralResolution1990c]] |
| `clarkHighSpectralResolution1990d` | [[clarkHighSpectralResolution1990d]] |
| `clarkReflectanceSpectroscopyQuantitative1984` | [[clarkReflectanceSpectroscopyQuantitative1984]] |
| `clarkReflectanceSpectroscopyQuantitative1984a` | [[clarkReflectanceSpectroscopyQuantitative1984a]] |
| `clarkReflectanceSpectroscopyQuantitative1984b` | [[clarkReflectanceSpectroscopyQuantitative1984b]] |



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC - C-H.md (~357 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - range-c-h
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Sub-MOC for literature sources in alphabetical range C-H.
---

# 📚 Literature Index (C-H)

> Part 2 of the literature index, covering references from **clarkReflectanceSpectroscopyQuantitative1984c** to **hakkouValorizationPhosphateWaste2016**.
> Back to [[Literature MOC|Master Literature MOC]].

## 📋 literature Notes

| Filename | Link |
| :--- | :--- |
| `clarkReflectanceSpectroscopyQuantitative1984c` | [[clarkReflectanceSpectroscopyQuantitative1984c]] |
| `clarkSpectroscopyRocksMinerals1999` | [[clarkSpectroscopyRocksMinerals1999]] |
| `cogliatiPRISMAImagingSpectroscopy2021` | [[cogliatiPRISMAImagingSpectroscopy2021]] |
| `cogliatiPRISMAImagingSpectroscopy2021a` | [[cogliatiPRISMAImagingSpectroscopy2021a]] |
| `cogliatiPRISMAImagingSpectroscopy2021b` | [[cogliatiPRISMAImagingSpectroscopy2021b]] |
| `cogliatiPRISMAImagingSpectroscopy2021c` | [[cogliatiPRISMAImagingSpectroscopy2021c]] |
| `cohenStatisticalPowerAnalysis2013` | [[cohenStatisticalPowerAnalysis2013]] |
| `coppoLeonardoSpaceborneInfrared2020` | [[coppoLeonardoSpaceborneInfrared2020]] |
| `coppoLeonardoSpaceborneInfrared2020a` | [[coppoLeonardoSpaceborneInfrared2020a]] |
| `cordellStoryPhosphorusGlobal2009` | [[cordellStoryPhosphorusGlobal2009]] |
| `cordellStoryPhosphorusGlobal2009a` | [[cordellStoryPhosphorusGlobal2009a]] |
| `cortesSupportvectorNetworks1995` | [[cortesSupportvectorNetworks1995]] |
| `coverNearestNeighborPattern1967` | [[coverNearestNeighborPattern1967]] |
| `DataProductsQuality` | [[DataProductsQuality]] |
| `DataSeries2017` | [[DataSeries2017]] |
| `DataSeries2017a` | [[DataSeries2017a]] |
| `DataSeries2017b` | [[DataSeries2017b]] |
| `daviesMappingAcidicMine2017` | [[daviesMappingAcidicMine2017]] |
| `desanctisSpectroscopicCharacterizationMineralogy2012` | [[desanctisSpectroscopicCharacterizationMineralogy2012]] |
| `dobigeonNonlinearUnmixingHyperspectral2014` | [[dobigeonNonlinearUnmixingHyperspectral2014]] |
| `EditorialSpecialIssue` | [[EditorialSpecialIssue]] |
| `edwardsMineralResourceOre2001` | [[edwardsMineralResourceOre2001]] |
| `el-arafySuccessfulSpectralRemote2021` | [[el-arafySuccessfulSpectralRemote2021]] |
| `el-azhariEvaluatingGroundwaterSalinity2025` | [[el-azhariEvaluatingGroundwaterSalinity2025]] |
| `elazhariPollutionEcologicalRisk2017` | [[elazhariPollutionEcologicalRisk2017]] |
| `elbamikiPhosphateRocksReview2021` | [[elbamikiPhosphateRocksReview2021]] |
| `elberdaiValorizationPhosphateMine2024` | [[elberdaiValorizationPhosphateMine2024]] |
| `elberdaiValorizationPhosphateMine2024a` | [[elberdaiValorizationPhosphateMine2024a]] |
| `elmachiRecyclingMineWastes2024` | [[elmachiRecyclingMineWastes2024]] |
| `elmansourCuttingEdgeFrameworkSustainable2025` | [[elmansourCuttingEdgeFrameworkSustainable2025]] |
| `elmeknassiCircularEconomyStrategies2024` | [[elmeknassiCircularEconomyStrategies2024]] |
| `elserBrokenBiogeochemicalCycle2011` | [[elserBrokenBiogeochemicalCycle2011]] |
| `EnMAPSpaceborneImaging` | [[EnMAPSpaceborneImaging]] |
| `essingtonSoilWaterChemistry2004` | [[essingtonSoilWaterChemistry2004]] |
| `fauvelAdvancesSpectralSpatialClassification2013` | [[fauvelAdvancesSpectralSpatialClassification2013]] |
| `fieldingStatisticalInferenceOrder1974` | [[fieldingStatisticalInferenceOrder1974]] |
| `flogeacCharacterizationSoilParticles2005` | [[flogeacCharacterizationSoilParticles2005]] |
| `francosEstimationRelativeAbundance2021` | [[francosEstimationRelativeAbundance2021]] |
| `gaffeySpectralReflectanceCarbonate1986` | [[gaffeySpectralReflectanceCarbonate1986]] |
| `gaffeysSpectralReflectanceCarbonate1986` | [[gaffeysSpectralReflectanceCarbonate1986]] |
| `gaoGeneralizedUnsupervisedClustering2021` | [[gaoGeneralizedUnsupervisedClustering2021]] |
| `gasmiUsingPRISMAHyperspectral2022` | [[gasmiUsingPRISMAHyperspectral2022]] |
| `gazleyReviewReliabilityValidity2014` | [[gazleyReviewReliabilityValidity2014]] |
| `gazleyReviewReliabilityValidity2014a` | [[gazleyReviewReliabilityValidity2014a]] |
| `geladiPartialLeastsquaresRegression1986` | [[geladiPartialLeastsquaresRegression1986]] |
| `geladiPartialLeastsquaresRegression1986a` | [[geladiPartialLeastsquaresRegression1986a]] |
| `genesioUpdatesPRISMAScientific2022` | [[genesioUpdatesPRISMAScientific2022]] |
| `geurtsExtremelyRandomizedTrees2006` | [[geurtsExtremelyRandomizedTrees2006]] |
| `gewaliMachineLearningBased2019` | [[gewaliMachineLearningBased2019]] |
| `giardinoHyperspectralPrismaProducts2021` | [[giardinoHyperspectralPrismaProducts2021]] |
| `giardinoHyperspectralPrismaProducts2021a` | [[giardinoHyperspectralPrismaProducts2021a]] |
| `giglioActiveFireDetection2008` | [[giglioActiveFireDetection2008]] |
| `goetzImagingSpectrometryEarth1985` | [[goetzImagingSpectrometryEarth1985]] |
| `goetzImagingSpectrometryEarth1985a` | [[goetzImagingSpectrometryEarth1985a]] |
| `grewalMachineLearningDeep2023` | [[grewalMachineLearningDeep2023]] |
| `guanterSpectralCalibrationHyperspectral2006` | [[guanterSpectralCalibrationHyperspectral2006]] |
| `guhaReflectanceSpectroscopyASTER2019` | [[guhaReflectanceSpectroscopyASTER2019]] |
| `hakkouValorizationPhosphateWaste2016` | [[hakkouValorizationPhosphateWaste2016]] |



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC - H-M.md (~357 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - range-h-m
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Sub-MOC for literature sources in alphabetical range H-M.
---

# 📚 Literature Index (H-M)

> Part 3 of the literature index, covering references from **hallEvaluationPortableXray2014** to **maSituLeadImmobilization1993**.
> Back to [[Literature MOC|Master Literature MOC]].

## 📋 literature Notes

| Filename | Link |
| :--- | :--- |
| `hallEvaluationPortableXray2014` | [[hallEvaluationPortableXray2014]] |
| `HandheldXrayFluorescence2019` | [[HandheldXrayFluorescence2019]] |
| `HandheldXrayFluorescence2019a` | [[HandheldXrayFluorescence2019a]] |
| `hapkeBidirectionalReflectanceSpectroscopy1981` | [[hapkeBidirectionalReflectanceSpectroscopy1981]] |
| `hapkeTheoryReflectanceEmittance2012` | [[hapkeTheoryReflectanceEmittance2012]] |
| `heckerAssessingInfluenceReference2008` | [[heckerAssessingInfluenceReference2008]] |
| `heckerAssessingInfluenceReference2008a` | [[heckerAssessingInfluenceReference2008a]] |
| `heinzFullyConstrainedLeast2001` | [[heinzFullyConstrainedLeast2001]] |
| `heinzFullyConstrainedLeast2001a` | [[heinzFullyConstrainedLeast2001a]] |
| `heinzFullyConstrainedLeast2001b` | [[heinzFullyConstrainedLeast2001b]] |
| `hellerpearlshtienPRISMASensorEvaluation2021` | [[hellerpearlshtienPRISMASensorEvaluation2021]] |
| `hellerpearlshtienPRISMASensorEvaluation2021a` | [[hellerpearlshtienPRISMASensorEvaluation2021a]] |
| `hellerpearlshtienPRISMASensorEvaluation2021b` | [[hellerpearlshtienPRISMASensorEvaluation2021b]] |
| `heRecentAdvancesSpectral2018` | [[heRecentAdvancesSpectral2018]] |
| `hudson-edwardsTacklingMineWastes2016` | [[hudson-edwardsTacklingMineWastes2016]] |
| `huntSPECTRALSIGNATURESPARTICULATE1977` | [[huntSPECTRALSIGNATURESPARTICULATE1977]] |
| `huntVisibleNearinfraredSpectra1970` | [[huntVisibleNearinfraredSpectra1970]] |
| `huntVisibleNearinfraredSpectra1971` | [[huntVisibleNearinfraredSpectra1971]] |
| `HyperspectralRemoteSensing` | [[HyperspectralRemoteSensing]] |
| `ibrahimAssessmentMachineLearning2014` | [[ibrahimAssessmentMachineLearning2014]] |
| `idrissiSustainableUsePhosphate2021` | [[idrissiSustainableUsePhosphate2021]] |
| `ihbachGeophysicalProspectingGroundwater2020` | [[ihbachGeophysicalProspectingGroundwater2020]] |
| `ImagingSpectrometryEarth` | [[ImagingSpectrometryEarth]] |
| `inabiInvestigationInnovativeCombined2024` | [[inabiInvestigationInnovativeCombined2024]] |
| `inabiSustainableMiningRepurposing2025` | [[inabiSustainableMiningRepurposing2025]] |
| `InterlayersGeoenvironmentalAssessment` | [[InterlayersGeoenvironmentalAssessment]] |
| `jahodaMachineLearningRecognizing2021` | [[jahodaMachineLearningRecognizing2021]] |
| `jamiesonGeochemistryMineralogySolid2011` | [[jamiesonGeochemistryMineralogySolid2011]] |
| `jiangEvaluationPotentialRelease2015` | [[jiangEvaluationPotentialRelease2015]] |
| `kalnickyFieldPortableXRF2001` | [[kalnickyFieldPortableXRF2001]] |
| `karasiakSpatialDependenceTraining2022` | [[karasiakSpatialDependenceTraining2022]] |
| `kattenbornSpatiallyAutocorrelatedTraining2022` | [[kattenbornSpatiallyAutocorrelatedTraining2022]] |
| `kattenbornSpatiallyAutocorrelatedTraining2022a` | [[kattenbornSpatiallyAutocorrelatedTraining2022a]] |
| `keshavaSpectralUnmixing2002` | [[keshavaSpectralUnmixing2002]] |
| `keshavaSpectralUnmixing2002a` | [[keshavaSpectralUnmixing2002a]] |
| `khalilAssessmentSoilContamination2013` | [[khalilAssessmentSoilContamination2013]] |
| `kleinmannPredictionWaterQuality2000` | [[kleinmannPredictionWaterQuality2000]] |
| `koiralaRobustSupervisedMethod2021` | [[koiralaRobustSupervisedMethod2021]] |
| `koiralaRobustSupervisedMethod2021a` | [[koiralaRobustSupervisedMethod2021a]] |
| `kokalyUSGSSpectralLibrary2017` | [[kokalyUSGSSpectralLibrary2017]] |
| `kruseSpectralImageProcessing1993` | [[kruseSpectralImageProcessing1993]] |
| `kruseSpectralImageProcessing1993a` | [[kruseSpectralImageProcessing1993a]] |
| `laaksoAssessingAbilityCombine2018` | [[laaksoAssessingAbilityCombine2018]] |
| `lawsonSolvingLeastSquares1995` | [[lawsonSolvingLeastSquares1995]] |
| `lawsonSolvingLeastSquares1995a` | [[lawsonSolvingLeastSquares1995a]] |
| `liDeepLearningHyperspectral2019` | [[liDeepLearningHyperspectral2019]] |
| `liMineralProspectivityMapping2025` | [[liMineralProspectivityMapping2025]] |
| `loizzoPrismaItalianHyperspectral2018` | [[loizzoPrismaItalianHyperspectral2018]] |
| `loizzoPrismaMissionStatus2019` | [[loizzoPrismaMissionStatus2019]] |
| `loizzoPrismaMissionStatus2019a` | [[loizzoPrismaMissionStatus2019a]] |
| `lottermoserMineWastes2010` | [[lottermoserMineWastes2010]] |
| `loukiliMonitoringLandChanges2025` | [[loukiliMonitoringLandChanges2025]] |
| `malusisRestrictedSaltDiffusion2015` | [[malusisRestrictedSaltDiffusion2015]] |
| `mandendeHyperspectralCoreScanner2023` | [[mandendeHyperspectralCoreScanner2023]] |
| `mansourIntegratingVNIRSWIR2025` | [[mansourIntegratingVNIRSWIR2025]] |
| `MappingHyperspectralAVIRIS` | [[MappingHyperspectralAVIRIS]] |
| `marshallFieldlevelCropYield2022` | [[marshallFieldlevelCropYield2022]] |
| `maSituLeadImmobilization1993` | [[maSituLeadImmobilization1993]] |



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC - M-R.md (~357 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - range-m-r
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Sub-MOC for literature sources in alphabetical range M-R.
---

# 📚 Literature Index (M-R)

> Part 4 of the literature index, covering references from **mcclellanMineralogyCarbonateFluorapatites1980** to **ruffinCombinedDerivativeSpectroscopy2008**.
> Back to [[Literature MOC|Master Literature MOC]].

## 📋 literature Notes

| Filename | Link |
| :--- | :--- |
| `mcclellanMineralogyCarbonateFluorapatites1980` | [[mcclellanMineralogyCarbonateFluorapatites1980]] |
| `meerdinkECOSTRESSSpectralLibrary2019` | [[meerdinkECOSTRESSSpectralLibrary2019]] |
| `melganiClassificationHyperspectralRemote2004` | [[melganiClassificationHyperspectralRemote2004]] |
| `melganiSupportVectorMachines2002` | [[melganiSupportVectorMachines2002]] |
| `meyerImportanceSpatialPredictor2019` | [[meyerImportanceSpatialPredictor2019]] |
| `meznedPerspectiveChapterOptical2023` | [[meznedPerspectiveChapterOptical2023]] |
| `mghazliDescriptionMicrobialCommunities2021` | [[mghazliDescriptionMicrobialCommunities2021]] |
| `mielkeEnGeoMAP20AutomatedHyperspectral2016` | [[mielkeEnGeoMAP20AutomatedHyperspectral2016]] |
| `MineralCommoditySummaries` | [[MineralCommoditySummaries]] |
| `MineralCommoditySummaries2021` | [[MineralCommoditySummaries2021]] |
| `MineralCommoditySummaries2023` | [[MineralCommoditySummaries2023]] |
| `MineralCommoditySummaries2023a` | [[MineralCommoditySummaries2023a]] |
| `MineralCommoditySummaries2025` | [[MineralCommoditySummaries2025]] |
| `MineralCommoditySummaries2025a` | [[MineralCommoditySummaries2025a]] |
| `MineralCommoditySummaries2025b` | [[MineralCommoditySummaries2025b]] |
| `MineralCommoditySummaries2025c` | [[MineralCommoditySummaries2025c]] |
| `MineralCommoditySummaries2025d` | [[MineralCommoditySummaries2025d]] |
| `MineralCommoditySummaries2025e` | [[MineralCommoditySummaries2025e]] |
| `MineWastesCharacterization` | [[MineWastesCharacterization]] |
| `mitchellFundamentalsSoilBehavior2005` | [[mitchellFundamentalsSoilBehavior2005]] |
| `MitigatingSoilContamination2018` | [[MitigatingSoilContamination2018]] |
| `mostafaReleasePotentiallyToxic2025` | [[mostafaReleasePotentiallyToxic2025]] |
| `mulderQuantifyingMineralAbundances2013` | [[mulderQuantifyingMineralAbundances2013]] |
| `nascimentoVertexComponentAnalysis2005` | [[nascimentoVertexComponentAnalysis2005]] |
| `nascimentoVertexComponentAnalysis2005a` | [[nascimentoVertexComponentAnalysis2005a]] |
| `nationalmineralsinformationcenterUSGeologicalSurvey2024` | [[nationalmineralsinformationcenterUSGeologicalSurvey2024]] |
| `nordstromMineWatersAcidic2011` | [[nordstromMineWatersAcidic2011]] |
| `norouziInformationDepthNIR2021` | [[norouziInformationDepthNIR2021]] |
| `notescoApplicationHyperspectralRemote2020` | [[notescoApplicationHyperspectralRemote2020]] |
| `OCPSustainabilityIntegrated2021` | [[OCPSustainabilityIntegrated2021]] |
| `ongPredictingAcidDrainage2003` | [[ongPredictingAcidDrainage2003]] |
| `OpenFileReport2002` | [[OpenFileReport2002]] |
| `OpenFileReport2002a` | [[OpenFileReport2002a]] |
| `ouzemouIntegratingPostrainfallMultispectral2026` | [[ouzemouIntegratingPostrainfallMultispectral2026]] |
| `ouzemouPredictingSoilSalinity2025` | [[ouzemouPredictingSoilSalinity2025]] |
| `percivalCustomizedSpectralLibraries2018` | [[percivalCustomizedSpectralLibraries2018]] |
| `pereiraMultiTemporalMineralMapping2025` | [[pereiraMultiTemporalMineralMapping2025]] |
| `pignattiEvaluationPRISMAHyperspectral2021` | [[pignattiEvaluationPRISMAHyperspectral2021]] |
| `plantePredictingGeochemicalBehaviour2011` | [[plantePredictingGeochemicalBehaviour2011]] |
| `plazaForewordSpecialIssue2012` | [[plazaForewordSpecialIssue2012]] |
| `plazaForewordSpecialIssue2012a` | [[plazaForewordSpecialIssue2012a]] |
| `plazaRecentDevelopmentsEndmember2011` | [[plazaRecentDevelopmentsEndmember2011]] |
| `plotonSpatialValidationReveals2020` | [[plotonSpatialValidationReveals2020]] |
| `pottsHandbookSilicateRock1987` | [[pottsHandbookSilicateRock1987]] |
| `pourEditorialSpecialIssue2021` | [[pourEditorialSpecialIssue2021]] |
| `prevotCorrespondanceEntreContenu1979` | [[prevotCorrespondanceEntreContenu1979]] |
| `ProgressGeoenvironmentalModels2002` | [[ProgressGeoenvironmentalModels2002]] |
| `qianGEOTECHNICALASPECTSLANDFILL` | [[qianGEOTECHNICALASPECTSLANDFILL]] |
| `r.desikanExploringRockPhosphates2018` | [[r.desikanExploringRockPhosphates2018]] |
| `ramakrishnanHyperspectralRemoteSensing2015` | [[ramakrishnanHyperspectralRemoteSensing2015]] |
| `ramseyCanSituGeochemical2012` | [[ramseyCanSituGeochemical2012]] |
| `rastiNoiseReductionHyperspectral2018` | [[rastiNoiseReductionHyperspectral2018]] |
| `rastiNoiseReductionHyperspectral2018a` | [[rastiNoiseReductionHyperspectral2018a]] |
| `robertsCrossvalidationStrategiesData2017` | [[robertsCrossvalidationStrategiesData2017]] |
| `roggeIntegrationSpatialSpectral2007` | [[roggeIntegrationSpatialSpectral2007]] |
| `romanoAppropriateStatisticsOrdinal2006` | [[romanoAppropriateStatisticsOrdinal2006]] |
| `rousseauCorrectionsMatrixEffects2006` | [[rousseauCorrectionsMatrixEffects2006]] |
| `ruffinCombinedDerivativeSpectroscopy2008` | [[ruffinCombinedDerivativeSpectroscopy2008]] |



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC - R-Z.md (~367 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - range-r-z
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Sub-MOC for literature sources in alphabetical range R-Z.
---

# 📚 Literature Index (R-Z)

> Part 5 of the literature index, covering references from **ryskinVibrationsProtonsMinerals1974** to **zouhriCretaceousTertiaryPlateaus2008**.
> Back to [[Literature MOC|Master Literature MOC]].

## 📋 literature Notes

| Filename | Link |
| :--- | :--- |
| `ryskinVibrationsProtonsMinerals1974` | [[ryskinVibrationsProtonsMinerals1974]] |
| `safhiCharacterizationsPotentialRecovery2022` | [[safhiCharacterizationsPotentialRecovery2022]] |
| `safhiCharacterizationsPotentialRecovery2022a` | [[safhiCharacterizationsPotentialRecovery2022a]] |
| `sahooModellingSpectralUnmixing2023` | [[sahooModellingSpectralUnmixing2023]] |
| `savitzkySmoothingDifferentiationData1964` | [[savitzkySmoothingDifferentiationData1964]] |
| `savitzkySmoothingDifferentiationData1964a` | [[savitzkySmoothingDifferentiationData1964a]] |
| `savitzkySmoothingDifferentiationData1964b` | [[savitzkySmoothingDifferentiationData1964b]] |
| `savitzkySmoothingDifferentiationData1964c` | [[savitzkySmoothingDifferentiationData1964c]] |
| `schaepmanEarthSystemScience2009` | [[schaepmanEarthSystemScience2009]] |
| `scholzSustainableUsePhosphorus2013` | [[scholzSustainableUsePhosphorus2013]] |
| `sealProgressGeoenvironmentalModels2002` | [[sealProgressGeoenvironmentalModels2002]] |
| `shadmanroodposhtiUncertaintyAssessmentHyperspectral2019` | [[shadmanroodposhtiUncertaintyAssessmentHyperspectral2019]] |
| `sheblPRISMAHyperspectralData2023` | [[sheblPRISMAHyperspectralData2023]] |
| `shirmardComparativeStudyConvolutional2022` | [[shirmardComparativeStudyConvolutional2022]] |
| `shirmardReviewMachineLearning2022` | [[shirmardReviewMachineLearning2022]] |
| `simapeyghambariHyperspectralRemoteSensing2021` | [[simapeyghambariHyperspectralRemoteSensing2021]] |
| `slanskyGeologySedimentaryPhosphates1986` | [[slanskyGeologySedimentaryPhosphates1986]] |
| `smilPhosphorusEnvironmentNatural2000` | [[smilPhosphorusEnvironmentNatural2000]] |
| `SpectralReflectanceCarbonate` | [[SpectralReflectanceCarbonate]] |
| `stonerCharacteristicVariationsReflectance1981` | [[stonerCharacteristicVariationsReflectance1981]] |
| `storchEnMAPImagingSpectroscopy2023` | [[storchEnMAPImagingSpectroscopy2023]] |
| `sudharsanMachineLearningdrivenMineral2025` | [[sudharsanMachineLearningdrivenMineral2025]] |
| `swayzeUsingImagingSpectroscopy2000` | [[swayzeUsingImagingSpectroscopy2000]] |
| `TacklingMineWastes` | [[TacklingMineWastes]] |
| `tahaZeroSolidWaste2021` | [[tahaZeroSolidWaste2021]] |
| `tahaZeroSolidWaste2021a` | [[tahaZeroSolidWaste2021a]] |
| `tahaZeroSolidWaste2021b` | [[tahaZeroSolidWaste2021b]] |
| `testaBACKFILLINGOPENPITMETALLIC2007` | [[testaBACKFILLINGOPENPITMETALLIC2007]] |
| `testaBACKFILLINGOPENPITMETALLIC2007a` | [[testaBACKFILLINGOPENPITMETALLIC2007a]] |
| `tsaiDerivativeAnalysisHyperspectral` | [[tsaiDerivativeAnalysisHyperspectral]] |
| `tsaiDerivativeAnalysisHyperspectrala` | [[tsaiDerivativeAnalysisHyperspectrala]] |
| `turnerVisibleShortwaveInfrared2016` | [[turnerVisibleShortwaveInfrared2016]] |
| `tusaDrillCoreMineralAbundance2020` | [[tusaDrillCoreMineralAbundance2020]] |
| `UsingPRISMAHyperspectral` | [[UsingPRISMAHyperspectral]] |
| `valaviBlockCVPackageGenerating2019` | [[valaviBlockCVPackageGenerating2019]] |
| `vandermeerAnalysisSpectralAbsorption2004` | [[vandermeerAnalysisSpectralAbsorption2004]] |
| `vandermeerMultiHyperspectralGeologic2012` | [[vandermeerMultiHyperspectralGeologic2012]] |
| `vandermeerMultiHyperspectralGeologic2012a` | [[vandermeerMultiHyperspectralGeologic2012a]] |
| `vandijkPhosphorusFlowsBalances2016` | [[vandijkPhosphorusFlowsBalances2016]] |
| `vangenuchtenClosedformEquationPredicting1980` | [[vangenuchtenClosedformEquationPredicting1980]] |
| `vangiNewHyperspectralSatellite2021` | [[vangiNewHyperspectralSatellite2021]] |
| `vankauwenberghWorldPhosphateRock2010` | [[vankauwenberghWorldPhosphateRock2010]] |
| `wangSpectralSpatialMultifeaturebased2017` | [[wangSpectralSpatialMultifeaturebased2017]] |
| `wangUncertaintyQuantificationDeep2025` | [[wangUncertaintyQuantificationDeep2025]] |
| `waskeMappingHyperspectralAVIRIS2009` | [[waskeMappingHyperspectralAVIRIS2009]] |
| `withersStewardshipTackleGlobal2015` | [[withersStewardshipTackleGlobal2015]] |
| `woldPLSregressionBasicTool2001` | [[woldPLSregressionBasicTool2001]] |
| `WorldFertilizerTrends` | [[WorldFertilizerTrends]] |
| `WorldFertilizerTrends2019` | [[WorldFertilizerTrends2019]] |
| `yangEnvironmentalImpactsCaused2014` | [[yangEnvironmentalImpactsCaused2014]] |
| `yekutieliResamplingbasedFalseDiscovery1999` | [[yekutieliResamplingbasedFalseDiscovery1999]] |
| `yueSpectralSpatialClassification2015` | [[yueSpectralSpatialClassification2015]] |
| `zainiDeterminationCarbonateRock2014` | [[zainiDeterminationCarbonateRock2014]] |
| `zhangCHARACTERIZATIONQUANTITATIVEANALYSIS2001` | [[zhangCHARACTERIZATIONQUANTITATIVEANALYSIS2001]] |
| `zhangPredictionRecyclePhosphate2024` | [[zhangPredictionRecyclePhosphate2024]] |
| `zineAdvancementsMineClosure2023` | [[zineAdvancementsMineClosure2023]] |
| `zineNativePlantDiversity2023` | [[zineNativePlantDiversity2023]] |
| `zineNativePlantDiversity2023a` | [[zineNativePlantDiversity2023a]] |
| `zineNativePlantDiversity2023b` | [[zineNativePlantDiversity2023b]] |
| `zouhriCretaceousTertiaryPlateaus2008` | [[zouhriCretaceousTertiaryPlateaus2008]] |



================================================================================
FILE: 04_Knowledge Base/wiki/Literature MOC.md (~135 words)
================================================================================
---
generated_by: claude
date: '2026-06-10'
tags:
  - moc
  - topic/wiki-concept
type: concept-note
status: active
created: '2026-06-10'
summary: Master Literature Map of Content (MOC) linking to alphabetical sub-MOCs for
  a clean, clustered graph layout.
---

# 📚 Literature Map of Content (MOC)

> Master directory of all 292 literature notes and bibliography sources ingested in the Second Brain.
> Split into 5 alphabetical sub-MOCs to maintain a clean and clustered graph view.

## 📂 Alphabetical Sub-MOCs

- [[Literature MOC - A-C|Literature MOC — Range A-C]] (58 references)
- [[Literature MOC - C-H|Literature MOC — Range C-H]] (58 references)
- [[Literature MOC - H-M|Literature MOC — Range H-M]] (58 references)
- [[Literature MOC - M-R|Literature MOC — Range M-R]] (58 references)
- [[Literature MOC - R-Z|Literature MOC — Range R-Z]] (60 references)

---

*Back to [[index|Wiki Index]]*



================================================================================
FILE: 04_Knowledge Base/wiki/hot.md (~717 words)
================================================================================
---
tags:
  - hot-cache
  - system
  - topic/system
  - wiki
updated: 2026-06-08
generated_by: claude
type: system-note
status: active
created: '2026-06-08'
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
FILE: 04_Knowledge Base/wiki/index.md (~696 words)
================================================================================
---
tags:
  - index
  - system
  - topic/system
  - wiki
updated: 2026-05-24
generated_by: claude
type: system-note
status: active
created: '2026-05-24'
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

> 📂 **Master Catalog**: [[Literature MOC|View all 292 literature notes]]


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
- [[01_System/graphify-out/GRAPH_REPORT|Graph Report]] — Network analysis of the vault structure




================================================================================
FILE: 04_Knowledge Base/wiki/sources/BoardmanJWKruse.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: BoardmanJWKruse
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Boardman, J

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@BoardmanJWKruse)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/DataProductsQuality.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: DataProductsQuality
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Data Products

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@DataProductsQuality)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/DataSeries2017.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: DataSeries2017
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Data Series

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@DataSeries2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/DataSeries2017a.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: DataSeries2017a
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Data Series

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@DataSeries2017a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/DataSeries2017b.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: DataSeries2017b
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Data Series

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@DataSeries2017b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/EditorialSpecialIssue.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: EditorialSpecialIssue
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Editorial for the Special Issue

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@EditorialSpecialIssue)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/EnMAPSpaceborneImaging.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: EnMAPSpaceborneImaging
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The EnMAP Spaceborne Imaging Spectroscopy Mission

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@EnMAPSpaceborneImaging)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/HandheldXrayFluorescence2019.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: HandheldXrayFluorescence2019
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hand-Held X-ray

* **Authors:** Unknown Authors
* **Published in:** *Analytical Methods* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@HandheldXrayFluorescence2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/HandheldXrayFluorescence2019a.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: HandheldXrayFluorescence2019a
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hand-Held X-ray

* **Authors:** Unknown Authors
* **Published in:** *Analytical Methods* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@HandheldXrayFluorescence2019a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/HyperspectralRemoteSensing.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: HyperspectralRemoteSensing
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Remote Sensing and Geological Applications

* **Authors:** Unknown Authors
* **Published in:** *HYPERSPECTRAL REMOTE SENSING* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@HyperspectralRemoteSensing)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ImagingSpectrometryEarth.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: ImagingSpectrometryEarth
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Imaging Spectrometry

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ImagingSpectrometryEarth)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/InterlayersGeoenvironmentalAssessment.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: InterlayersGeoenvironmentalAssessment
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Interlayers Geo-Environmental Assessment of Phosphate Waste Rock for Sustainable Management Practices \textbar

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@InterlayersGeoenvironmentalAssessment)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MappingHyperspectralAVIRIS.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: MappingHyperspectralAVIRIS
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping of Hyperspectral AVIRIS

* **Authors:** Unknown Authors
* **Published in:** *Canadian Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MappingHyperspectralAVIRIS)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineWastesCharacterization.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineWastesCharacterization
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mine Wastes

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineWastesCharacterization)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2021.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2021
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2023.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2023
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2023a.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2023a
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2023

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2023a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025a.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025a
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025b.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025b
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025c.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025c
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025c)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025d.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025d
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025d)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MineralCommoditySummaries2025e.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: MineralCommoditySummaries2025e
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Commodity Summaries 2025

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MineralCommoditySummaries2025e)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/MitigatingSoilContamination2018.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: MitigatingSoilContamination2018
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mitigating Soil Contamination at Abandoned Moroccan

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@MitigatingSoilContamination2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/OCPSustainabilityIntegrated2021.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: OCPSustainabilityIntegrated2021
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 OCP Sustainability Integrated Report

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@OCPSustainabilityIntegrated2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/OpenFileReport2002.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: OpenFileReport2002
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Open-File Report

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@OpenFileReport2002)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/OpenFileReport2002a.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: OpenFileReport2002a
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Open-File Report

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@OpenFileReport2002a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ProgressGeoenvironmentalModels2002.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: ProgressGeoenvironmentalModels2002
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Progress on Geoenvironmental Models for Selected Mineral Deposit Types

* **Authors:** Unknown Authors
* **Published in:** *Open-File Report* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ProgressGeoenvironmentalModels2002)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/SpectralReflectanceCarbonate.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: SpectralReflectanceCarbonate
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Reflectance of Carbonate Minerals in the Visible and near Infrared (0.35--2.55 Um): Anhydrous

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@SpectralReflectanceCarbonate)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/TacklingMineWastes.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: TacklingMineWastes
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Tackling Mine Wastes \textbar

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@TacklingMineWastes)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/UsingPRISMAHyperspectral.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: UsingPRISMAHyperspectral
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Using PRISMA Hyperspectral Satellite Imagery

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@UsingPRISMAHyperspectral)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/WorldFertilizerTrends.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: WorldFertilizerTrends
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 World Fertilizer Trends and Outlook to 2022

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@WorldFertilizerTrends)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/WorldFertilizerTrends2019.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: WorldFertilizerTrends2019
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 World Fertilizer Trends and Outlook to 2022

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@WorldFertilizerTrends2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/abdolmalekiOreWasteDiscriminationUsing2022.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: abdolmalekiOreWasteDiscriminationUsing2022
year: Unknown Year
authors: Abdolmaleki, Mehdi and Consens, Mariano and Esmaeili, Kamran
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Ore-Waste Discrimination Using Supervised

* **Authors:** Abdolmaleki, Mehdi and Consens, Mariano and Esmaeili, Kamran
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@abdolmalekiOreWasteDiscriminationUsing2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/achemrkTrackingQuarterCenturySpatioTemporal2026.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: achemrkTrackingQuarterCenturySpatioTemporal2026
year: Unknown Year
authors: Achemrk, Aiman and Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay,
  Ali and Hajaj, Soufiane and Oussaoui, Sabir and Chehbouni, Abdelghani
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Tracking Quarter-Century Spatio-Temporal Soil Salinization Dynamics

* **Authors:** Achemrk, Aiman and Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Hajaj, Soufiane and Oussaoui, Sabir and Chehbouni, Abdelghani
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@achemrkTrackingQuarterCenturySpatioTemporal2026)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/acitoAtmosphericCompensationPRISMA2021.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: acitoAtmosphericCompensationPRISMA2021
year: Unknown Year
authors: Acito, Nicola and Diani, Marco and Procissi, Gregorio and Corsini, Giovanni
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Atmospheric Compensation

* **Authors:** Acito, Nicola and Diani, Marco and Procissi, Gregorio and Corsini, Giovanni
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@acitoAtmosphericCompensationPRISMA2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/acitoAtmosphericCompensationPRISMA2021a.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: acitoAtmosphericCompensationPRISMA2021a
year: Unknown Year
authors: Acito, Nicola and Diani, Marco and Procissi, Gregorio and Corsini, Giovanni
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Atmospheric Compensation

* **Authors:** Acito, Nicola and Diani, Marco and Procissi, Gregorio and Corsini, Giovanni
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@acitoAtmosphericCompensationPRISMA2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/agrawalEvaluatingPerformancePRISMA2023.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: agrawalEvaluatingPerformancePRISMA2023
year: Unknown Year
authors: Agrawal, Neelam and Govil, Himanshu and Mishra, Gaurav and Gupta, Manika
  and Srivastava, Prashant K.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluating the Performance

* **Authors:** Agrawal, Neelam and Govil, Himanshu and Mishra, Gaurav and Gupta, Manika and Srivastava, Prashant K.
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@agrawalEvaluatingPerformancePRISMA2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/allowayHeavyMetalsSoils2013.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: allowayHeavyMetalsSoils2013
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Heavy Metals

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@allowayHeavyMetalsSoils2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/alonsoDataProductsQuality2019.md (~115 words)
================================================================================
---
tags:
  - topic/literature
citekey: alonsoDataProductsQuality2019
year: Unknown Year
authors: Alonso, Kevin and Bachmann, Martin and Burch, Kara and Carmona, Emiliano
  and Cerra, Daniele and De Los Reyes, Raquel and Dietrich, Daniele and Heiden, Uta
  and H\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Data Products

* **Authors:** Alonso, Kevin and Bachmann, Martin and Burch, Kara and Carmona, Emiliano and Cerra, Daniele and De Los Reyes, Raquel and Dietrich, Daniele and Heiden, Uta and H\
* **Published in:** *Sensors* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@alonsoDataProductsQuality2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/alvesRevisitingRamanSpectra2023.md (~97 words)
================================================================================
---
tags:
  - topic/literature
citekey: alvesRevisitingRamanSpectra2023
year: Unknown Year
authors: Alves, Julliana F. and Edwards, Howell G. M. and Korsakov, Andrey and De
  Oliveira, Luiz Fernando C.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Revisiting the Raman Spectra

* **Authors:** Alves, Julliana F. and Edwards, Howell G. M. and Korsakov, Andrey and De Oliveira, Luiz Fernando C.
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@alvesRevisitingRamanSpectra2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/amarMineWasteRock2023.md (~110 words)
================================================================================
---
tags:
  - topic/literature
citekey: amarMineWasteRock2023
year: Unknown Year
authors: Amar, Hicham and Benzaazoua, Mostafa and Elghali, Abdellatif and Taha, Yassine
  and El Ghorfi, Mustapha and Krause, Anna and Hakkou, Rachid
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mine Waste Rock Reprocessing Using Sensor-Based Sorting (SBS

* **Authors:** Amar, Hicham and Benzaazoua, Mostafa and Elghali, Abdellatif and Taha, Yassine and El Ghorfi, Mustapha and Krause, Anna and Hakkou, Rachid
* **Published in:** *Minerals Engineering* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@amarMineWasteRock2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/amarWasteRockReprocessing2022.md (~101 words)
================================================================================
---
tags:
  - topic/literature
citekey: amarWasteRockReprocessing2022
year: Unknown Year
authors: Amar, Hicham and Benzaazoua, Mostafa and Elghali, Abdellatif and Hakkou,
  Rachid and Taha, Yassine
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Waste Rock Reprocessing to Enhance the Sustainability of Phosphate Reserves: A

* **Authors:** Amar, Hicham and Benzaazoua, Mostafa and Elghali, Abdellatif and Hakkou, Rachid and Taha, Yassine
* **Published in:** *Journal of Cleaner Production* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@amarWasteRockReprocessing2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/amraniValorizationPhosphateMine2019.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: amraniValorizationPhosphateMine2019
year: Unknown Year
authors: Amrani, Mustapha and Taha, Yassine and Kchikach, Azzouz and Benzaazoua, Mostafa
  and Hakkou, Rachid
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Valorization of Phosphate Mine Waste Rocks

* **Authors:** Amrani, Mustapha and Taha, Yassine and Kchikach, Azzouz and Benzaazoua, Mostafa and Hakkou, Rachid
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@amraniValorizationPhosphateMine2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/anjjarPhosphateSeriesBenguerir.md (~97 words)
================================================================================
---
tags:
  - topic/literature
citekey: anjjarPhosphateSeriesBenguerir
year: Unknown Year
authors: Anjjar, A and Driouch, Y and Benjelloun, F and Hmeid, H Ait and Alami, A
  El
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Phosphate Series of Benguerir

* **Authors:** Anjjar, A and Driouch, Y and Benjelloun, F and Hmeid, H Ait and Alami, A El
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@anjjarPhosphateSeriesBenguerir)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/araujoRecyclingReuseMine2022.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: araujoRecyclingReuseMine2022
year: Unknown Year
authors: Araujo, Francisco and Taborda-Llano
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Recycling and Reuse

* **Authors:** Araujo, Francisco and Taborda-Llano
* **Published in:** *Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@araujoRecyclingReuseMine2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/aubineauHighlyVariableContent2022.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: aubineauHighlyVariableContent2022
year: Unknown Year
authors: Aubineau, J\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Highly Variable Content of Fluorapatite-Hosted CO32

* **Authors:** Aubineau, J\
* **Published in:** *Chemical Geology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@aubineauHighlyVariableContent2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/aubineauPhosphateD13CorgChemostratigraphy2024.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: aubineauPhosphateD13CorgChemostratigraphy2024
year: Unknown Year
authors: Aubineau, J\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Phosphate $\delta$13Corg

* **Authors:** Aubineau, J\
* **Published in:** *Chemical Geology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@aubineauPhosphateD13CorgChemostratigraphy2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/audebertDeepLearningClassification2019.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: audebertDeepLearningClassification2019
year: Unknown Year
authors: Audebert, Nicolas and Le Saux, Bertrand and Lefevre, Sebastien
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Deep Learning

* **Authors:** Audebert, Nicolas and Le Saux, Bertrand and Lefevre, Sebastien
* **Published in:** *IEEE Geoscience and Remote Sensing Magazine* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@audebertDeepLearningClassification2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bahhouUsePhosphateMine2021.md (~112 words)
================================================================================
---
tags:
  - topic/literature
citekey: bahhouUsePhosphateMine2021
year: Unknown Year
authors: Bahhou, Abdelmoujib and Taha, Yassine and El Khessaimi, Yassine and Idrissi,
  Hicham and Hakkou, Rachid and Amalik, Jamal and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Use of Phosphate Mine By-Products as Supplementary Cementitious Materials

* **Authors:** Bahhou, Abdelmoujib and Taha, Yassine and El Khessaimi, Yassine and Idrissi, Hicham and Hakkou, Rachid and Amalik, Jamal and Benzaazoua, Mostafa
* **Published in:** *Materials Today: Proceedings* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bahhouUsePhosphateMine2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/barlowStatisticalInferenceOrder1972.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: barlowStatisticalInferenceOrder1972
year: Unknown Year
authors: Barlow, R. E.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Statistical Inference Under Order Restrictions

* **Authors:** Barlow, R. E.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@barlowStatisticalInferenceOrder1972)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/barlowStatisticalInferenceOrder1980.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: barlowStatisticalInferenceOrder1980
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Statistical Inference under Order Restrictions: The Theory and Application of Isotonic Regression

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@barlowStatisticalInferenceOrder1980)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bayoussefUseClaysByproducts2021.md (~116 words)
================================================================================
---
tags:
  - topic/literature
citekey: bayoussefUseClaysByproducts2021
year: Unknown Year
authors: Bayoussef, A. and Loutou, M. and Taha, Y. and Mansori, M. and Benzaazoua,
  M. and Manoun, B. and Hakkou, R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Use of Clays By-Products from Phosphate Mines for the Manufacture of Sustainable Lightweight Aggregates

* **Authors:** Bayoussef, A. and Loutou, M. and Taha, Y. and Mansori, M. and Benzaazoua, M. and Manoun, B. and Hakkou, R.
* **Published in:** *Journal of Cleaner Production* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bayoussefUseClaysByproducts2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bendorReflectanceMeasurementsSoils2015.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: bendorReflectanceMeasurementsSoils2015
year: Unknown Year
authors: Ben Dor, Eyal and Ong, Cindy and Lau, Ian C.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Measurements of Soils in the Laboratory: Standards

* **Authors:** Ben Dor, Eyal and Ong, Cindy and Lau, Ian C.
* **Published in:** *Geoderma* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bendorReflectanceMeasurementsSoils2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bendorReflectanceMeasurementsSoils2015a.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: bendorReflectanceMeasurementsSoils2015a
year: Unknown Year
authors: Ben Dor, Eyal and Ong, Cindy and Lau, Ian C.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Measurements of Soils in the Laboratory: Standards

* **Authors:** Ben Dor, Eyal and Ong, Cindy and Lau, Ian C.
* **Published in:** *Geoderma* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bendorReflectanceMeasurementsSoils2015a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/benjaminiControllingFalseDiscovery1995.md (~82 words)
================================================================================
---
tags:
  - topic/literature
citekey: benjaminiControllingFalseDiscovery1995
year: Unknown Year
authors: Benjamini, Yoav and Hochberg, Yosef
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Controlling the False Discovery Rate

* **Authors:** Benjamini, Yoav and Hochberg, Yosef
* **Published in:** *Journal of the Royal Statistical Society: Series B (Methodological)* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@benjaminiControllingFalseDiscovery1995)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/benjaminiControllingFalseDiscovery1995a.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: benjaminiControllingFalseDiscovery1995a
year: Unknown Year
authors: Benjamini, Yoav and Hochberg, Yosef
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Controlling the False Discovery Rate

* **Authors:** Benjamini, Yoav and Hochberg, Yosef
* **Published in:** *Journal of the Royal Statistical Society Series B: Statistical Methodology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@benjaminiControllingFalseDiscovery1995a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bioucas-diasHyperspectralUnmixingOverview2012.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: bioucas-diasHyperspectralUnmixingOverview2012
year: Unknown Year
authors: Bioucas-Dias
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Unmixing Overview

* **Authors:** Bioucas-Dias
* **Published in:** *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bioucas-diasHyperspectralUnmixingOverview2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bishopInfraredSpectroscopicAnalyses1994.md (~77 words)
================================================================================
---
tags:
  - topic/literature
citekey: bishopInfraredSpectroscopicAnalyses1994
year: Unknown Year
authors: Bishop, Janice L. and Pieters, Carl\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Infrared Spectroscopic Analyses

* **Authors:** Bishop, Janice L. and Pieters, Carl\
* **Published in:** *Clays and Clay Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bishopInfraredSpectroscopicAnalyses1994)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bishopReflectanceEmissionSpectroscopy2008.md (~105 words)
================================================================================
---
tags:
  - topic/literature
citekey: bishopReflectanceEmissionSpectroscopy2008
year: Unknown Year
authors: Bishop, J. L. and Lane, M. D. and Dyar, M. D. and Brown, A. J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance and Emission Spectroscopy Study of Four Groups of Phyllosilicates: Smectites, Kaolinite-Serpentines, Chlorites and Micas

* **Authors:** Bishop, J. L. and Lane, M. D. and Dyar, M. D. and Brown, A. J.
* **Published in:** *Clay Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bishopReflectanceEmissionSpectroscopy2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/boardmanMAPPINGTARGETSIGNATURES.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: boardmanMAPPINGTARGETSIGNATURES
year: Unknown Year
authors: Boardman, Joseph and Kruse, F.A. and Green, Robert, O.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 MAPPING TARGET SIGNATURES VIA PARTIAL UNMIXING OF AVIRIS DATA

* **Authors:** Boardman, Joseph and Kruse, F.A. and Green, Robert, O.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@boardmanMAPPINGTARGETSIGNATURES)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/boardmanMappingTargetSignatures1995.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: boardmanMappingTargetSignatures1995
year: Unknown Year
authors: Boardman, Joseph W. and Kruse, Fred A. and Green, Robert O.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping Target Signatures via Partial Unmixing of AVIRIS

* **Authors:** Boardman, Joseph W. and Kruse, Fred A. and Green, Robert O.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@boardmanMappingTargetSignatures1995)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/boardmanjosephw.AUTOMATINGSPECTRALUNMIXING.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: boardmanjosephw.AUTOMATINGSPECTRALUNMIXING
year: Unknown Year
authors: Boardman, Joseph W.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 AUTOMATING SPECTRAL UNMIXING OF AVIRIS DATA USING CONVEX GEOMETRY CONCEPTS

* **Authors:** Boardman, Joseph W.
* **Published in:** *1993* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@boardmanjosephw.AUTOMATINGSPECTRALUNMIXING)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bosseAssessmentPhosphateLimestone2013.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: bosseAssessmentPhosphateLimestone2013
year: Unknown Year
authors: Boss\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Assessment of Phosphate Limestone Wastes

* **Authors:** Boss\
* **Published in:** *Mine Water and the Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bosseAssessmentPhosphateLimestone2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/boujoContributionLetudeGeologique1976.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: boujoContributionLetudeGeologique1976
year: Unknown Year
authors: Boujo, Armand
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Contribution \`a l

* **Authors:** Boujo, Armand
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@boujoContributionLetudeGeologique1976)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bourazzaRestorationPhosphateMined2025.md (~101 words)
================================================================================
---
tags:
  - topic/literature
citekey: bourazzaRestorationPhosphateMined2025
year: Unknown Year
authors: Bourazza, Anass and Hassane Sidikou, Abdel Aziz and Fenta, Berhanu Amsalu
  and Hirich, Abdelaziz
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Restoration of Phosphate Mined Lands: Literature Review with Insights from Morocco

* **Authors:** Bourazza, Anass and Hassane Sidikou, Abdel Aziz and Fenta, Berhanu Amsalu and Hirich, Abdelaziz
* **Published in:** *Frontiers in Environmental Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bourazzaRestorationPhosphateMined2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bourazzaRestorationPhosphateMined2025a.md (~101 words)
================================================================================
---
tags:
  - topic/literature
citekey: bourazzaRestorationPhosphateMined2025a
year: Unknown Year
authors: Bourazza, Anass and Hassane Sidikou, Abdel Aziz and Fenta, Berhanu Amsalu
  and Hirich, Abdelaziz
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Restoration of Phosphate Mined Lands: Literature Review with Insights from Morocco

* **Authors:** Bourazza, Anass and Hassane Sidikou, Abdel Aziz and Fenta, Berhanu Amsalu and Hirich, Abdelaziz
* **Published in:** *Frontiers in Environmental Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bourazzaRestorationPhosphateMined2025a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bradshawRestorationMinedLands1997.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: bradshawRestorationMinedLands1997
year: Unknown Year
authors: Bradshaw, Anthony
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Restoration of Mined Lands---Using Natural Processes

* **Authors:** Bradshaw, Anthony
* **Published in:** *Ecological Engineering* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bradshawRestorationMinedLands1997)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/breimanRandomForests2001.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: breimanRandomForests2001
year: Unknown Year
authors: Breiman, Leo
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Random Forests

* **Authors:** Breiman, Leo
* **Published in:** *Machine Learning* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@breimanRandomForests2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/bressanEvaluationMachineLearning2020.md (~104 words)
================================================================================
---
tags:
  - topic/literature
citekey: bressanEvaluationMachineLearning2020
year: Unknown Year
authors: Bressan, Thiago Santi and Kehl De Souza, Marcelo and Girelli, Tiago J. and
  Junior, Farid Chemale
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluation of Machine Learning Methods for Lithology Classification Using Geophysical Data

* **Authors:** Bressan, Thiago Santi and Kehl De Souza, Marcelo and Girelli, Tiago J. and Junior, Farid Chemale
* **Published in:** *Computers \& Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@bressanEvaluationMachineLearning2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/buzziMappingChangesRecovering2014.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: buzziMappingChangesRecovering2014
year: Unknown Year
authors: Buzzi, Jorge and Riaza, Asunci\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping Changes

* **Authors:** Buzzi, Jorge and Riaza, Asunci\
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@buzziMappingChangesRecovering2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/c.heckerSpectralAbsorptionFeature2019.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: c.heckerSpectralAbsorptionFeature2019
year: Unknown Year
authors: C. Hecker
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Absorption Feature Analysis

* **Authors:** C. Hecker
* **Published in:** *IEEE Geoscience and Remote Sensing Magazine* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@c.heckerSpectralAbsorptionFeature2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chabrillatEnMAPSpaceborneImaging2024.md (~210 words)
================================================================================
---
tags:
  - topic/literature
citekey: chabrillatEnMAPSpaceborneImaging2024
year: Unknown Year
authors: Chabrillat, Sabine and Foerster, Saskia and Segl, Karl and Beamish, Alison
  and Brell, Maximilian and Asadzadeh, Saeid and Milewski, Robert and Ward, Kathrin
  J. and Brosinsky, Arlena and Koch, Katrin and Scheffler, Daniel and Guillaso, Stephane
  and Kokhanovsky, Alexander and Roessner, Sigrid and Guanter, Luis and Kaufmann,
  Hermann and Pinnel, Nicole and Carmona, Emiliano and Storch, Tobias and Hank, Tobias
  and Berger, Katja and Wocher, Mathias and Hostert, Patrick and van der Linden
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The EnMAP

* **Authors:** Chabrillat, Sabine and Foerster, Saskia and Segl, Karl and Beamish, Alison and Brell, Maximilian and Asadzadeh, Saeid and Milewski, Robert and Ward, Kathrin J. and Brosinsky, Arlena and Koch, Katrin and Scheffler, Daniel and Guillaso, Stephane and Kokhanovsky, Alexander and Roessner, Sigrid and Guanter, Luis and Kaufmann, Hermann and Pinnel, Nicole and Carmona, Emiliano and Storch, Tobias and Hank, Tobias and Berger, Katja and Wocher, Mathias and Hostert, Patrick and van der Linden
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chabrillatEnMAPSpaceborneImaging2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chakrabortySpectralSpatialComparison2024.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: chakrabortySpectralSpatialComparison2024
year: Unknown Year
authors: Chakraborty, Rupsa and Rachdi, Imane and Thiele, Samuel and Booysen, Ren\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Spectral

* **Authors:** Chakraborty, Rupsa and Rachdi, Imane and Thiele, Samuel and Booysen, Ren\
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chakrabortySpectralSpatialComparison2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/charbaouiNewInsightsGeophysical2023.md (~115 words)
================================================================================
---
tags:
  - topic/literature
citekey: charbaouiNewInsightsGeophysical2023
year: Unknown Year
authors: Charbaoui, Anas and Kchikach, Azzouz and Jaffal, Mohammed and Khadiri, Oussama
  Yazami and Guernouche, Mourad and Amar, Mounir and Bikarnaf, Ahmed and Jourani,
  Es-Said and Khelifi, Nabil
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 New Insights

* **Authors:** Charbaoui, Anas and Kchikach, Azzouz and Jaffal, Mohammed and Khadiri, Oussama Yazami and Guernouche, Mourad and Amar, Mounir and Bikarnaf, Ahmed and Jourani, Es-Said and Khelifi, Nabil
* **Published in:** *Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@charbaouiNewInsightsGeophysical2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/charbaouiNewInsightsGeophysical2023a.md (~115 words)
================================================================================
---
tags:
  - topic/literature
citekey: charbaouiNewInsightsGeophysical2023a
year: Unknown Year
authors: Charbaoui, Anas and Kchikach, Azzouz and Jaffal, Mohammed and Khadiri, Oussama
  Yazami and Guernouche, Mourad and Amar, Mounir and Bikarnaf, Ahmed and Jourani,
  Es-Said and Khelifi, Nabil
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 New Insights

* **Authors:** Charbaoui, Anas and Kchikach, Azzouz and Jaffal, Mohammed and Khadiri, Oussama Yazami and Guernouche, Mourad and Amar, Mounir and Bikarnaf, Ahmed and Jourani, Es-Said and Khelifi, Nabil
* **Published in:** *Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@charbaouiNewInsightsGeophysical2023a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chein-ichangSpectralInformationDivergence1999.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: chein-ichangSpectralInformationDivergence1999
year: Unknown Year
authors: Chein-I Chang
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Information Divergence for Hyperspectral Image Analysis

* **Authors:** Chein-I Chang
* **Published in:** *IEEE* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chein-ichangSpectralInformationDivergence1999)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chenIntegratingVisibleNearinfrared2010.md (~99 words)
================================================================================
---
tags:
  - topic/literature
citekey: chenIntegratingVisibleNearinfrared2010
year: Unknown Year
authors: Chen, Xianfeng and Warner, Timothy A. and Campagna, David J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Integrating Visible, near-Infrared and Short-Wave Infrared Hyperspectral and Multispectral Thermal Imagery for Geological Mapping at Cuprite

* **Authors:** Chen, Xianfeng and Warner, Timothy A. and Campagna, David J.
* **Published in:** *International Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chenIntegratingVisibleNearinfrared2010)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chenXGBoostScalableTree2016.md (~77 words)
================================================================================
---
tags:
  - topic/literature
citekey: chenXGBoostScalableTree2016
year: Unknown Year
authors: Chen, Tianqi and Guestrin, Carlos
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 XGBoost

* **Authors:** Chen, Tianqi and Guestrin, Carlos
* **Published in:** *Proceedings of the 22nd ACM SIGKDD International Conference* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chenXGBoostScalableTree2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chindongMultiSensorMachineLearning2025.md (~109 words)
================================================================================
---
tags:
  - topic/literature
citekey: chindongMultiSensorMachineLearning2025
year: Unknown Year
authors: Chindong, Joyce Mongai and Ouzemou, Jamal-Eddine and Laamrani, Ahmed and
  El Battay, Ali and Hajaj, Soufiane and Rhinane, Hassan and Chehbouni, Abdelghani
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Multi-Sensor Machine Learning Framework

* **Authors:** Chindong, Joyce Mongai and Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Hajaj, Soufiane and Rhinane, Hassan and Chehbouni, Abdelghani
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chindongMultiSensorMachineLearning2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/chlahbiGeologicalGeomechanicalCharacterization2023.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: chlahbiGeologicalGeomechanicalCharacterization2023
year: Unknown Year
authors: Chlahbi, Safa and Belem, Tikou and Elghali, Abdellatif and Rochdane, Samia
  and Zerouali, Essaid and Inabi, Omar and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Geological and Geomechanical Characterization

* **Authors:** Chlahbi, Safa and Belem, Tikou and Elghali, Abdellatif and Rochdane, Samia and Zerouali, Essaid and Inabi, Omar and Benzaazoua, Mostafa
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@chlahbiGeologicalGeomechanicalCharacterization2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/choeMappingHeavyMetal2008.md (~92 words)
================================================================================
---
tags:
  - topic/literature
citekey: choeMappingHeavyMetal2008
year: Unknown Year
authors: Choe, Eunyoung and van der Meer
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping of Heavy Metal Pollution in Stream Sediments Using Combined Geochemistry, Field Spectroscopy, and Hyperspectral Remote Sensing: A

* **Authors:** Choe, Eunyoung and van der Meer
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@choeMappingHeavyMetal2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkHighSpectralResolution1990.md (~107 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkHighSpectralResolution1990
year: Unknown Year
authors: Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg
  A. and Vergo, Norma
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 High Spectral Resolution Reflectance Spectroscopy of Minerals

* **Authors:** Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg A. and Vergo, Norma
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkHighSpectralResolution1990)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkHighSpectralResolution1990a.md (~107 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkHighSpectralResolution1990a
year: Unknown Year
authors: Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg
  A. and Vergo, Norma
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 High Spectral Resolution Reflectance Spectroscopy of Minerals

* **Authors:** Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg A. and Vergo, Norma
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkHighSpectralResolution1990a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkHighSpectralResolution1990b.md (~107 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkHighSpectralResolution1990b
year: Unknown Year
authors: Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg
  A. and Vergo, Norma
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 High Spectral Resolution Reflectance Spectroscopy of Minerals

* **Authors:** Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg A. and Vergo, Norma
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkHighSpectralResolution1990b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkHighSpectralResolution1990c.md (~107 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkHighSpectralResolution1990c
year: Unknown Year
authors: Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg
  A. and Vergo, Norma
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 High Spectral Resolution Reflectance Spectroscopy of Minerals

* **Authors:** Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg A. and Vergo, Norma
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkHighSpectralResolution1990c)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkHighSpectralResolution1990d.md (~107 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkHighSpectralResolution1990d
year: Unknown Year
authors: Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg
  A. and Vergo, Norma
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 High Spectral Resolution Reflectance Spectroscopy of Minerals

* **Authors:** Clark, Roger N. and King, Trude V. V. and Klejwa, Matthew and Swayze, Gregg A. and Vergo, Norma
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkHighSpectralResolution1990d)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkReflectanceSpectroscopyQuantitative1984.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkReflectanceSpectroscopyQuantitative1984
year: Unknown Year
authors: Clark, Roger N. and Roush, Ted L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Spectroscopy: Quantitative

* **Authors:** Clark, Roger N. and Roush, Ted L.
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkReflectanceSpectroscopyQuantitative1984)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkReflectanceSpectroscopyQuantitative1984a.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkReflectanceSpectroscopyQuantitative1984a
year: Unknown Year
authors: Clark, Roger N. and Roush, Ted L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Spectroscopy: Quantitative

* **Authors:** Clark, Roger N. and Roush, Ted L.
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkReflectanceSpectroscopyQuantitative1984a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkReflectanceSpectroscopyQuantitative1984b.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkReflectanceSpectroscopyQuantitative1984b
year: Unknown Year
authors: Clark, Roger N. and Roush, Ted L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Spectroscopy: Quantitative

* **Authors:** Clark, Roger N. and Roush, Ted L.
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkReflectanceSpectroscopyQuantitative1984b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkReflectanceSpectroscopyQuantitative1984c.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkReflectanceSpectroscopyQuantitative1984c
year: Unknown Year
authors: Clark, Roger N. and Roush, Ted L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Spectroscopy: Quantitative

* **Authors:** Clark, Roger N. and Roush, Ted L.
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkReflectanceSpectroscopyQuantitative1984c)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/clarkSpectroscopyRocksMinerals1999.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: clarkSpectroscopyRocksMinerals1999
year: Unknown Year
authors: Clark, Roger
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectroscopy of Rocks and Minerals and Principles of Spectroscopy

* **Authors:** Clark, Roger
* **Published in:** *Manual of Remote Sensing, Volume* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@clarkSpectroscopyRocksMinerals1999)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cogliatiPRISMAImagingSpectroscopy2021.md (~126 words)
================================================================================
---
tags:
  - topic/literature
citekey: cogliatiPRISMAImagingSpectroscopy2021
year: Unknown Year
authors: Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso,
  R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A.
  and P\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The PRISMA

* **Authors:** Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso, R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A. and P\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cogliatiPRISMAImagingSpectroscopy2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cogliatiPRISMAImagingSpectroscopy2021a.md (~126 words)
================================================================================
---
tags:
  - topic/literature
citekey: cogliatiPRISMAImagingSpectroscopy2021a
year: Unknown Year
authors: Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso,
  R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A.
  and P\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The PRISMA

* **Authors:** Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso, R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A. and P\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cogliatiPRISMAImagingSpectroscopy2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cogliatiPRISMAImagingSpectroscopy2021b.md (~126 words)
================================================================================
---
tags:
  - topic/literature
citekey: cogliatiPRISMAImagingSpectroscopy2021b
year: Unknown Year
authors: Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso,
  R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A.
  and P\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The PRISMA

* **Authors:** Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso, R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A. and P\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cogliatiPRISMAImagingSpectroscopy2021b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cogliatiPRISMAImagingSpectroscopy2021c.md (~126 words)
================================================================================
---
tags:
  - topic/literature
citekey: cogliatiPRISMAImagingSpectroscopy2021c
year: Unknown Year
authors: Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso,
  R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A.
  and P\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The PRISMA

* **Authors:** Cogliati, S. and Sarti, F. and Chiarantini, L. and Cosi, M. and Lorusso, R. and Lopinto, E. and Miglietta, F. and Genesio, L. and Guanter, L. and Damm, A. and P\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cogliatiPRISMAImagingSpectroscopy2021c)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cohenStatisticalPowerAnalysis2013.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: cohenStatisticalPowerAnalysis2013
year: Unknown Year
authors: Cohen, Jacob
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Statistical Power Analysis

* **Authors:** Cohen, Jacob
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cohenStatisticalPowerAnalysis2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/coppoLeonardoSpaceborneInfrared2020.md (~124 words)
================================================================================
---
tags:
  - topic/literature
citekey: coppoLeonardoSpaceborneInfrared2020
year: Unknown Year
authors: Coppo, Peter and Brandani, Fabio and Faraci, Marco and Sarti, Francesco and
  Dami, Michele and Chiarantini, Leandro and Ponticelli, Beatrice and Giunti, Lorenzo
  and Fossati, Enrico and Cosi, Massimo
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Leonardo Spaceborne Infrared Payloads for Earth

* **Authors:** Coppo, Peter and Brandani, Fabio and Faraci, Marco and Sarti, Francesco and Dami, Michele and Chiarantini, Leandro and Ponticelli, Beatrice and Giunti, Lorenzo and Fossati, Enrico and Cosi, Massimo
* **Published in:** *Appl. Opt.* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@coppoLeonardoSpaceborneInfrared2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/coppoLeonardoSpaceborneInfrared2020a.md (~124 words)
================================================================================
---
tags:
  - topic/literature
citekey: coppoLeonardoSpaceborneInfrared2020a
year: Unknown Year
authors: Coppo, Peter and Brandani, Fabio and Faraci, Marco and Sarti, Francesco and
  Dami, Michele and Chiarantini, Leandro and Ponticelli, Beatrice and Giunti, Lorenzo
  and Fossati, Enrico and Cosi, Massimo
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Leonardo Spaceborne Infrared Payloads for Earth

* **Authors:** Coppo, Peter and Brandani, Fabio and Faraci, Marco and Sarti, Francesco and Dami, Michele and Chiarantini, Leandro and Ponticelli, Beatrice and Giunti, Lorenzo and Fossati, Enrico and Cosi, Massimo
* **Published in:** *Appl. Opt.* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@coppoLeonardoSpaceborneInfrared2020a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cordellStoryPhosphorusGlobal2009.md (~82 words)
================================================================================
---
tags:
  - topic/literature
citekey: cordellStoryPhosphorusGlobal2009
year: Unknown Year
authors: Cordell, Dana and Drangert, Jan-Olof and White, Stuart
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Story of Phosphorus: Global

* **Authors:** Cordell, Dana and Drangert, Jan-Olof and White, Stuart
* **Published in:** *Global Environmental Change* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cordellStoryPhosphorusGlobal2009)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cordellStoryPhosphorusGlobal2009a.md (~82 words)
================================================================================
---
tags:
  - topic/literature
citekey: cordellStoryPhosphorusGlobal2009a
year: Unknown Year
authors: Cordell, Dana and Drangert, Jan-Olof and White, Stuart
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Story of Phosphorus: Global

* **Authors:** Cordell, Dana and Drangert, Jan-Olof and White, Stuart
* **Published in:** *Global Environmental Change* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cordellStoryPhosphorusGlobal2009a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/cortesSupportvectorNetworks1995.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: cortesSupportvectorNetworks1995
year: Unknown Year
authors: Cortes, Corinna and Vapnik, Vladimir
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Support-Vector Networks

* **Authors:** Cortes, Corinna and Vapnik, Vladimir
* **Published in:** *Machine Learning* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@cortesSupportvectorNetworks1995)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/coverNearestNeighborPattern1967.md (~77 words)
================================================================================
---
tags:
  - topic/literature
citekey: coverNearestNeighborPattern1967
year: Unknown Year
authors: Cover, T. and Hart, P.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Nearest Neighbor Pattern Classification

* **Authors:** Cover, T. and Hart, P.
* **Published in:** *IEEE Transactions on Information Theory* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@coverNearestNeighborPattern1967)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/daviesMappingAcidicMine2017.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: daviesMappingAcidicMine2017
year: Unknown Year
authors: Davies, Gwendolyn E. and Calvin, Wendy M.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping Acidic Mine Waste with Seasonal Airborne Hyperspectral Imagery at Varying Spatial Scales

* **Authors:** Davies, Gwendolyn E. and Calvin, Wendy M.
* **Published in:** *Environmental Earth Sciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@daviesMappingAcidicMine2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/desanctisSpectroscopicCharacterizationMineralogy2012.md (~219 words)
================================================================================
---
tags:
  - topic/literature
citekey: desanctisSpectroscopicCharacterizationMineralogy2012
year: Unknown Year
authors: De Sanctis, M. C. and Ammannito, E. and Capria, M. T. and Tosi, F. and Capaccioni,
  F. and Zambon, F. and Carraro, F. and Fonte, S. and Frigeri, A. and Jaumann, R.
  and Magni, G. and Marchi, S. and McCord, T. B. and McFadden, L. A. and McSween,
  H. Y. and Mittlefehldt, D. W. and Nathues, A. and Palomba, E. and Pieters, C. M.
  and Raymond, C. A. and Russell, C. T. and Toplis, M. J. and Turrini, D.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectroscopic Characterization

* **Authors:** De Sanctis, M. C. and Ammannito, E. and Capria, M. T. and Tosi, F. and Capaccioni, F. and Zambon, F. and Carraro, F. and Fonte, S. and Frigeri, A. and Jaumann, R. and Magni, G. and Marchi, S. and McCord, T. B. and McFadden, L. A. and McSween, H. Y. and Mittlefehldt, D. W. and Nathues, A. and Palomba, E. and Pieters, C. M. and Raymond, C. A. and Russell, C. T. and Toplis, M. J. and Turrini, D.
* **Published in:** *Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@desanctisSpectroscopicCharacterizationMineralogy2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/dobigeonNonlinearUnmixingHyperspectral2014.md (~104 words)
================================================================================
---
tags:
  - topic/literature
citekey: dobigeonNonlinearUnmixingHyperspectral2014
year: Unknown Year
authors: Dobigeon, Nicolas and Tourneret, Jean-Yves and Richard, Cedric and Bermudez,
  Jose Carlos M. and McLaughlin, Stephen and Hero, Alfred O.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Nonlinear Unmixing

* **Authors:** Dobigeon, Nicolas and Tourneret, Jean-Yves and Richard, Cedric and Bermudez, Jose Carlos M. and McLaughlin, Stephen and Hero, Alfred O.
* **Published in:** *IEEE Signal Processing Magazine* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@dobigeonNonlinearUnmixingHyperspectral2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/edwardsMineralResourceOre2001.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: edwardsMineralResourceOre2001
year: Unknown Year
authors: Edwards, A.C. and of Mining, Australasian Institute and Metallurgy
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Resource

* **Authors:** Edwards, A.C. and of Mining, Australasian Institute and Metallurgy
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@edwardsMineralResourceOre2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/el-arafySuccessfulSpectralRemote2021.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: el-arafySuccessfulSpectralRemote2021
year: Unknown Year
authors: El-Arafy
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Successful Spectral Remote Sensing Techniques for Mapping Apatite Mineral of Phosphatic Rocks at Eastern Side of Abu Tartur Plateau

* **Authors:** El-Arafy
* **Published in:** *Arabian Journal of Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@el-arafySuccessfulSpectralRemote2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/el-azhariEvaluatingGroundwaterSalinity2025.md (~77 words)
================================================================================
---
tags:
  - topic/literature
citekey: el-azhariEvaluatingGroundwaterSalinity2025
year: Unknown Year
authors: El-Azhari
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluating Groundwater Salinity Patterns and Spatiotemporal Dynamics in Complex Endorheic Aquifer Systems

* **Authors:** El-Azhari
* **Published in:** *Science of The Total Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@el-azhariEvaluatingGroundwaterSalinity2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elazhariPollutionEcologicalRisk2017.md (~104 words)
================================================================================
---
tags:
  - topic/literature
citekey: elazhariPollutionEcologicalRisk2017
year: Unknown Year
authors: El Azhari, Abdellah and Rhoujjati, Ali and El Hachimi, Moulay La\^a
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Pollution and Ecological Risk Assessment of Heavy Metals in the Soil-Plant System and the Sediment-Water Column around a Former Pb

* **Authors:** El Azhari, Abdellah and Rhoujjati, Ali and El Hachimi, Moulay La\^a
* **Published in:** *Ecotoxicology and Environmental Safety* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elazhariPollutionEcologicalRisk2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elbamikiPhosphateRocksReview2021.md (~99 words)
================================================================================
---
tags:
  - topic/literature
citekey: elbamikiPhosphateRocksReview2021
year: Unknown Year
authors: El Bamiki, Radouan and Raji, Otmane and Ouabid, Muhammad and Elghali, Abdellatif
  and Khadiri Yazami, Oussama and Bodinier, Jean-Louis
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Phosphate Rocks

* **Authors:** El Bamiki, Radouan and Raji, Otmane and Ouabid, Muhammad and Elghali, Abdellatif and Khadiri Yazami, Oussama and Bodinier, Jean-Louis
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elbamikiPhosphateRocksReview2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elberdaiValorizationPhosphateMine2024.md (~121 words)
================================================================================
---
tags:
  - topic/literature
citekey: elberdaiValorizationPhosphateMine2024
year: Unknown Year
authors: El Berdai, Yahya and Taha, Yassine and Trauchessec, Romain and Rhaouti, Yasmine
  and Safhi, Amine El Mahdi and Hakkou, Rachid and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Valorization of Phosphate Mine Waste Rock as Alternative Aggregates for High-Performance Concrete

* **Authors:** El Berdai, Yahya and Taha, Yassine and Trauchessec, Romain and Rhaouti, Yasmine and Safhi, Amine El Mahdi and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Case Studies in Construction Materials* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elberdaiValorizationPhosphateMine2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elberdaiValorizationPhosphateMine2024a.md (~121 words)
================================================================================
---
tags:
  - topic/literature
citekey: elberdaiValorizationPhosphateMine2024a
year: Unknown Year
authors: El Berdai, Yahya and Taha, Yassine and Trauchessec, Romain and Rhaouti, Yasmine
  and Safhi, Amine el Mahdi and Hakkou, Rachid and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Valorization of Phosphate Mine Waste Rock as Alternative Aggregates for High-Performance Concrete

* **Authors:** El Berdai, Yahya and Taha, Yassine and Trauchessec, Romain and Rhaouti, Yasmine and Safhi, Amine el Mahdi and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Case Studies in Construction Materials* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elberdaiValorizationPhosphateMine2024a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elmachiRecyclingMineWastes2024.md (~111 words)
================================================================================
---
tags:
  - topic/literature
citekey: elmachiRecyclingMineWastes2024
year: Unknown Year
authors: El Machi, Aiman and El Berdai, Yahya and Mabroum, Safaa and Safhi, Amine
  El Mahdi and Taha, Yassine and Benzaazoua, Mostafa and Hakkou, Rachid
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Recycling of Mine Wastes

* **Authors:** El Machi, Aiman and El Berdai, Yahya and Mabroum, Safaa and Safhi, Amine El Mahdi and Taha, Yassine and Benzaazoua, Mostafa and Hakkou, Rachid
* **Published in:** *Buildings* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elmachiRecyclingMineWastes2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elmansourCuttingEdgeFrameworkSustainable2025.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: elmansourCuttingEdgeFrameworkSustainable2025
year: Unknown Year
authors: El Mansour, Abdelhak and Laamrani, Ahmed and Elghali, Abdellatif and Hakkou,
  Rachid and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Cutting-Edge Framework

* **Authors:** El Mansour, Abdelhak and Laamrani, Ahmed and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elmansourCuttingEdgeFrameworkSustainable2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elmeknassiCircularEconomyStrategies2024.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: elmeknassiCircularEconomyStrategies2024
year: Unknown Year
authors: Elmeknassi, Malak and Elghali, Abdellatif and Laamrani, Ahmed and Benzaazoua,
  Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Circular Economy Strategies in Sedimentary Phosphate Mine Reclamation: Development

* **Authors:** Elmeknassi, Malak and Elghali, Abdellatif and Laamrani, Ahmed and Benzaazoua, Mostafa
* **Published in:** *Journal of Environmental Management* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elmeknassiCircularEconomyStrategies2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/elserBrokenBiogeochemicalCycle2011.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: elserBrokenBiogeochemicalCycle2011
year: Unknown Year
authors: Elser, James and Bennett, Elena
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Broken Biogeochemical Cycle

* **Authors:** Elser, James and Bennett, Elena
* **Published in:** *Nature* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@elserBrokenBiogeochemicalCycle2011)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/essingtonSoilWaterChemistry2004.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: essingtonSoilWaterChemistry2004
year: Unknown Year
authors: Essington, Michael E.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Soil and Water Chemistry: An Integrative Approach

* **Authors:** Essington, Michael E.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@essingtonSoilWaterChemistry2004)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/fauvelAdvancesSpectralSpatialClassification2013.md (~98 words)
================================================================================
---
tags:
  - topic/literature
citekey: fauvelAdvancesSpectralSpatialClassification2013
year: Unknown Year
authors: Fauvel, M. and Tarabalka, Y. and Benediktsson, J. A. and Chanussot, J. and
  Tilton, J. C.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Advances in Spectral-Spatial Classification

* **Authors:** Fauvel, M. and Tarabalka, Y. and Benediktsson, J. A. and Chanussot, J. and Tilton, J. C.
* **Published in:** *Proceedings of the IEEE* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@fauvelAdvancesSpectralSpatialClassification2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/fieldingStatisticalInferenceOrder1974.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: fieldingStatisticalInferenceOrder1974
year: Unknown Year
authors: Fielding, A. and Barlow, R. E. and Bartholomew, D. J. and Bremner, J. M.
  and Brunk, H. D.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Statistical Inference Under Order Restrictions

* **Authors:** Fielding, A. and Barlow, R. E. and Bartholomew, D. J. and Bremner, J. M. and Brunk, H. D.
* **Published in:** *Journal of the Royal Statistical Society. Series A (General)* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@fieldingStatisticalInferenceOrder1974)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/flogeacCharacterizationSoilParticles2005.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: flogeacCharacterizationSoilParticles2005
year: Unknown Year
authors: Flogeac, Karine and Guillon, Emmanuel and Aplincourt, Michel and Marceau,
  Eric and Stievano, Lorenzo and Beaunier, Patricia and Frapart, Yves-Michel
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Characterization of Soil Particles by X-ray

* **Authors:** Flogeac, Karine and Guillon, Emmanuel and Aplincourt, Michel and Marceau, Eric and Stievano, Lorenzo and Beaunier, Patricia and Frapart, Yves-Michel
* **Published in:** *Agronomy for Sustainable Development* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@flogeacCharacterizationSoilParticles2005)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/francosEstimationRelativeAbundance2021.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: francosEstimationRelativeAbundance2021
year: Unknown Year
authors: Francos, Nicolas and Notesco, Gila and Ben-Dor
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Estimation of the Relative Abundance

* **Authors:** Francos, Nicolas and Notesco, Gila and Ben-Dor
* **Published in:** *Applied Spectroscopy* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@francosEstimationRelativeAbundance2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gaffeySpectralReflectanceCarbonate1986.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: gaffeySpectralReflectanceCarbonate1986
year: Unknown Year
authors: Gaffey, Susan J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Reflectance of Carbonate Minerals in the Visible and near Infrared (0.35-2.55 Microns); Calcite, Aragonite, and Dolomite

* **Authors:** Gaffey, Susan J.
* **Published in:** *American Mineralogist* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gaffeySpectralReflectanceCarbonate1986)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gaffeysSpectralReflectanceCarbonate1986.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: gaffeysSpectralReflectanceCarbonate1986
year: Unknown Year
authors: Gaffey, S, J
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Reflectance of Carbonate Minerals in the Visible and near Infrared (0.35--2.55 \textmu m): Calcite, Aragonite, and Dolomite

* **Authors:** Gaffey, S, J
* **Published in:** *American mineralogist* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gaffeysSpectralReflectanceCarbonate1986)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gaoGeneralizedUnsupervisedClustering2021.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: gaoGeneralizedUnsupervisedClustering2021
year: Unknown Year
authors: Gao, Angela F. and Rasmussen, Brandon and Kulits, Peter and Scheller, Eva
  L. and Greenberger, Rebecca and Ehlmann, Bethany L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Generalized Unsupervised Clustering

* **Authors:** Gao, Angela F. and Rasmussen, Brandon and Kulits, Peter and Scheller, Eva L. and Greenberger, Rebecca and Ehlmann, Bethany L.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gaoGeneralizedUnsupervisedClustering2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gasmiUsingPRISMAHyperspectral2022.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: gasmiUsingPRISMAHyperspectral2022
year: Unknown Year
authors: Gasmi, Anis and Gomez, C\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Using PRISMA Hyperspectral Satellite Imagery

* **Authors:** Gasmi, Anis and Gomez, C\
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gasmiUsingPRISMAHyperspectral2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gazleyReviewReliabilityValidity2014.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: gazleyReviewReliabilityValidity2014
year: Unknown Year
authors: Gazley, M. F. and Fisher, L. A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Review of the Reliability and Validity of Portable X-ray

* **Authors:** Gazley, M. F. and Fisher, L. A.
* **Published in:** *Mineral resource and ore reserve estimation--The AusIMM guide to good practice* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gazleyReviewReliabilityValidity2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gazleyReviewReliabilityValidity2014a.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: gazleyReviewReliabilityValidity2014a
year: Unknown Year
authors: Gazley, Michael and Fisher, Louise
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Review of the Reliability and Validity of Portable X-ray

* **Authors:** Gazley, Michael and Fisher, Louise
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gazleyReviewReliabilityValidity2014a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/geladiPartialLeastsquaresRegression1986.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: geladiPartialLeastsquaresRegression1986
year: Unknown Year
authors: Geladi, Paul and Kowalski, Bruce R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Partial Least-Squares Regression: A Tutorial

* **Authors:** Geladi, Paul and Kowalski, Bruce R.
* **Published in:** *Analytica Chimica Acta* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@geladiPartialLeastsquaresRegression1986)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/geladiPartialLeastsquaresRegression1986a.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: geladiPartialLeastsquaresRegression1986a
year: Unknown Year
authors: Geladi, Paul and Kowalski, Bruce R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Partial Least-Squares Regression: A Tutorial

* **Authors:** Geladi, Paul and Kowalski, Bruce R.
* **Published in:** *Analytica Chimica Acta* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@geladiPartialLeastsquaresRegression1986a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/genesioUpdatesPRISMAScientific2022.md (~174 words)
================================================================================
---
tags:
  - topic/literature
citekey: genesioUpdatesPRISMAScientific2022
year: Unknown Year
authors: Genesio, Lorenzo and Braga, Federica and Bresciani, Mariano and Boschetti,
  Mirco and Carotenuto, Federico and Cogliati, Sergio and Colella, Simone and Colombo,
  Roberto and Giardino, Claudia and Gioli, Beniamino and Lopinto, Ettore and Meloni,
  Daniela and Pepe, Monica and Pascucci, Simone and Pignatti, Stefano and Pompilio,
  Loredana and Sacco, Patrizia and Satalino, Giuseppe and Miglietta, Franco
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Updates On PRISMA

* **Authors:** Genesio, Lorenzo and Braga, Federica and Bresciani, Mariano and Boschetti, Mirco and Carotenuto, Federico and Cogliati, Sergio and Colella, Simone and Colombo, Roberto and Giardino, Claudia and Gioli, Beniamino and Lopinto, Ettore and Meloni, Daniela and Pepe, Monica and Pascucci, Simone and Pignatti, Stefano and Pompilio, Loredana and Sacco, Patrizia and Satalino, Giuseppe and Miglietta, Franco
* **Published in:** *IGARSS* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@genesioUpdatesPRISMAScientific2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/geurtsExtremelyRandomizedTrees2006.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: geurtsExtremelyRandomizedTrees2006
year: Unknown Year
authors: Geurts, Pierre and Ernst, Damien and Wehenkel, Louis
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Extremely Randomized Trees

* **Authors:** Geurts, Pierre and Ernst, Damien and Wehenkel, Louis
* **Published in:** *Machine Learning* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@geurtsExtremelyRandomizedTrees2006)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/gewaliMachineLearningBased2019.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: gewaliMachineLearningBased2019
year: Unknown Year
authors: Gewali, Utsav B. and Monteiro, Sildomar T. and Saber, Eli
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Machine Learning Based Hyperspectral Image Analysis: A

* **Authors:** Gewali, Utsav B. and Monteiro, Sildomar T. and Saber, Eli
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@gewaliMachineLearningBased2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/giardinoHyperspectralPrismaProducts2021.md (~131 words)
================================================================================
---
tags:
  - topic/literature
citekey: giardinoHyperspectralPrismaProducts2021
year: Unknown Year
authors: Giardino, Claudia and Bresciani, Mariano and Fabbretto, Alice and Ghirardi,
  Nicola and Mangano, Salvatore and Pellegrino, Andrea and Vaiciute, Diana and Braga,
  Federica and Brando, Vittorio E. and Laanen, Marnix and Tzimas, Apostolos
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Prisma Products

* **Authors:** Giardino, Claudia and Bresciani, Mariano and Fabbretto, Alice and Ghirardi, Nicola and Mangano, Salvatore and Pellegrino, Andrea and Vaiciute, Diana and Braga, Federica and Brando, Vittorio E. and Laanen, Marnix and Tzimas, Apostolos
* **Published in:** *2021 IEEE International Geoscience* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@giardinoHyperspectralPrismaProducts2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/giardinoHyperspectralPrismaProducts2021a.md (~131 words)
================================================================================
---
tags:
  - topic/literature
citekey: giardinoHyperspectralPrismaProducts2021a
year: Unknown Year
authors: Giardino, Claudia and Bresciani, Mariano and Fabbretto, Alice and Ghirardi,
  Nicola and Mangano, Salvatore and Pellegrino, Andrea and Vaiciute, Diana and Braga,
  Federica and Brando, Vittorio E. and Laanen, Marnix and Tzimas, Apostolos
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Prisma Products

* **Authors:** Giardino, Claudia and Bresciani, Mariano and Fabbretto, Alice and Ghirardi, Nicola and Mangano, Salvatore and Pellegrino, Andrea and Vaiciute, Diana and Braga, Federica and Brando, Vittorio E. and Laanen, Marnix and Tzimas, Apostolos
* **Published in:** *2021 IEEE International Geoscience* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@giardinoHyperspectralPrismaProducts2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/giglioActiveFireDetection2008.md (~91 words)
================================================================================
---
tags:
  - topic/literature
citekey: giglioActiveFireDetection2008
year: Unknown Year
authors: Giglio, Louis and Csiszar, Ivan and Rest\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Active Fire Detection and Characterization with the Advanced Spaceborne Thermal Emission and Reflection Radiometer (ASTER

* **Authors:** Giglio, Louis and Csiszar, Ivan and Rest\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@giglioActiveFireDetection2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/goetzImagingSpectrometryEarth1985.md (~91 words)
================================================================================
---
tags:
  - topic/literature
citekey: goetzImagingSpectrometryEarth1985
year: Unknown Year
authors: Goetz, Alexander F. H. and Vane, Gregg and Solomon, Jerry E. and Rock, Barrett
  N.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Imaging Spectrometry

* **Authors:** Goetz, Alexander F. H. and Vane, Gregg and Solomon, Jerry E. and Rock, Barrett N.
* **Published in:** *Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@goetzImagingSpectrometryEarth1985)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/goetzImagingSpectrometryEarth1985a.md (~91 words)
================================================================================
---
tags:
  - topic/literature
citekey: goetzImagingSpectrometryEarth1985a
year: Unknown Year
authors: Goetz, Alexander F. H. and Vane, Gregg and Solomon, Jerry E. and Rock, Barrett
  N.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Imaging Spectrometry

* **Authors:** Goetz, Alexander F. H. and Vane, Gregg and Solomon, Jerry E. and Rock, Barrett N.
* **Published in:** *Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@goetzImagingSpectrometryEarth1985a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/grewalMachineLearningDeep2023.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: grewalMachineLearningDeep2023
year: Unknown Year
authors: Grewal, Reaya and Singh Kasana, Singara and Kasana, Geeta
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Machine Learning

* **Authors:** Grewal, Reaya and Singh Kasana, Singara and Kasana, Geeta
* **Published in:** *Electronics* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@grewalMachineLearningDeep2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/guanterSpectralCalibrationHyperspectral2006.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: guanterSpectralCalibrationHyperspectral2006
year: Unknown Year
authors: Guanter, Luis and Richter, Rudolf and Moreno, Jos\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Calibration of Hyperspectral Imagery Using Atmospheric Absorption Features

* **Authors:** Guanter, Luis and Richter, Rudolf and Moreno, Jos\
* **Published in:** *Applied Optics* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@guanterSpectralCalibrationHyperspectral2006)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/guhaReflectanceSpectroscopyASTER2019.md (~133 words)
================================================================================
---
tags:
  - topic/literature
citekey: guhaReflectanceSpectroscopyASTER2019
year: Unknown Year
authors: Guha, Arindam and Vinod Kumar, K. and Porwal, Alok and Rani, Komal and Sahoo,
  K.C. and Aneesh Kumar, S.R. and Singaraju, V. and Singh, R.P. and Khandelwal, M.K.
  and Raju, P.V. and Diwakar, P.G.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Reflectance Spectroscopy and ASTER

* **Authors:** Guha, Arindam and Vinod Kumar, K. and Porwal, Alok and Rani, Komal and Sahoo, K.C. and Aneesh Kumar, S.R. and Singaraju, V. and Singh, R.P. and Khandelwal, M.K. and Raju, P.V. and Diwakar, P.G.
* **Published in:** *Ore Geology Reviews* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@guhaReflectanceSpectroscopyASTER2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hakkouValorizationPhosphateWaste2016.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: hakkouValorizationPhosphateWaste2016
year: Unknown Year
authors: Hakkou, Rachid and Benzaazoua, Mostafa and Bussi\`e
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Valorization of Phosphate Waste Rocks

* **Authors:** Hakkou, Rachid and Benzaazoua, Mostafa and Bussi\`e
* **Published in:** *Procedia Engineering* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hakkouValorizationPhosphateWaste2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hallEvaluationPortableXray2014.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: hallEvaluationPortableXray2014
year: Unknown Year
authors: Hall, Gwendy E.M. and Bonham-Carter
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluation of Portable X-ray

* **Authors:** Hall, Gwendy E.M. and Bonham-Carter
* **Published in:** *Geochemistry: Exploration, Environment, Analysis* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hallEvaluationPortableXray2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hapkeBidirectionalReflectanceSpectroscopy1981.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: hapkeBidirectionalReflectanceSpectroscopy1981
year: Unknown Year
authors: Hapke, Bruce
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Bidirectional Reflectance Spectroscopy: 1. Theory

* **Authors:** Hapke, Bruce
* **Published in:** *Journal of Geophysical Research: Solid Earth* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hapkeBidirectionalReflectanceSpectroscopy1981)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hapkeTheoryReflectanceEmittance2012.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: hapkeTheoryReflectanceEmittance2012
year: Unknown Year
authors: Hapke, Bruce
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Theory of Reflectance

* **Authors:** Hapke, Bruce
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hapkeTheoryReflectanceEmittance2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heRecentAdvancesSpectral2018.md (~89 words)
================================================================================
---
tags:
  - topic/literature
citekey: heRecentAdvancesSpectral2018
year: Unknown Year
authors: He, Lin and Li, Jun and Liu, Chenying and Li, Shutao
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Recent Advances

* **Authors:** He, Lin and Li, Jun and Liu, Chenying and Li, Shutao
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heRecentAdvancesSpectral2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heckerAssessingInfluenceReference2008.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: heckerAssessingInfluenceReference2008
year: Unknown Year
authors: Hecker, Christoph and van der Meijde
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Assessing the Influence

* **Authors:** Hecker, Christoph and van der Meijde
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heckerAssessingInfluenceReference2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heckerAssessingInfluenceReference2008a.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: heckerAssessingInfluenceReference2008a
year: Unknown Year
authors: Hecker, Christoph and van der Meijde
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Assessing the Influence

* **Authors:** Hecker, Christoph and van der Meijde
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heckerAssessingInfluenceReference2008a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heinzFullyConstrainedLeast2001.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: heinzFullyConstrainedLeast2001
year: Unknown Year
authors: Heinz, D.C. and Chein-I-Chang
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Fully Constrained Least Squares Linear Spectral Mixture Analysis Method for Material Quantification in Hyperspectral Imagery

* **Authors:** Heinz, D.C. and Chein-I-Chang
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heinzFullyConstrainedLeast2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heinzFullyConstrainedLeast2001a.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: heinzFullyConstrainedLeast2001a
year: Unknown Year
authors: Heinz, D.C. and Chein-I-Chang
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Fully Constrained Least Squares Linear Spectral Mixture Analysis Method for Material Quantification in Hyperspectral Imagery

* **Authors:** Heinz, D.C. and Chein-I-Chang
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heinzFullyConstrainedLeast2001a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/heinzFullyConstrainedLeast2001b.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: heinzFullyConstrainedLeast2001b
year: Unknown Year
authors: Heinz, D.C. and Chein-I-Chang
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Fully Constrained Least Squares Linear Spectral Mixture Analysis Method for Material Quantification in Hyperspectral Imagery

* **Authors:** Heinz, D.C. and Chein-I-Chang
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@heinzFullyConstrainedLeast2001b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hellerpearlshtienPRISMASensorEvaluation2021.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: hellerpearlshtienPRISMASensorEvaluation2021
year: Unknown Year
authors: Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 PRISMA

* **Authors:** Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
* **Published in:** *International Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hellerpearlshtienPRISMASensorEvaluation2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hellerpearlshtienPRISMASensorEvaluation2021a.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: hellerpearlshtienPRISMASensorEvaluation2021a
year: Unknown Year
authors: Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 PRISMA

* **Authors:** Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
* **Published in:** *International Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hellerpearlshtienPRISMASensorEvaluation2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hellerpearlshtienPRISMASensorEvaluation2021b.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: hellerpearlshtienPRISMASensorEvaluation2021b
year: Unknown Year
authors: Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 PRISMA

* **Authors:** Heller Pearlshtien, Daniela and Pignatti, Stefano and Greisman-Ran
* **Published in:** *International Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hellerpearlshtienPRISMASensorEvaluation2021b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/hudson-edwardsTacklingMineWastes2016.md (~64 words)
================================================================================
---
tags:
  - topic/literature
citekey: hudson-edwardsTacklingMineWastes2016
year: Unknown Year
authors: Hudson-Edwards
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Tackling Mine Wastes

* **Authors:** Hudson-Edwards
* **Published in:** *Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@hudson-edwardsTacklingMineWastes2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/huntSPECTRALSIGNATURESPARTICULATE1977.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: huntSPECTRALSIGNATURESPARTICULATE1977
year: Unknown Year
authors: Hunt, Graham R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 SPECTRAL SIGNATURES OF PARTICULATE MINERALS IN THE VISIBLE AND NEAR INFRARED

* **Authors:** Hunt, Graham R.
* **Published in:** *GEOPHYSICS* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@huntSPECTRALSIGNATURESPARTICULATE1977)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/huntVisibleNearinfraredSpectra1970.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: huntVisibleNearinfraredSpectra1970
year: Unknown Year
authors: Hunt, Graham R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Visible and Near-Infrared Spectra of Minerals and Rocks: I

* **Authors:** Hunt, Graham R.
* **Published in:** *Modern geology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@huntVisibleNearinfraredSpectra1970)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/huntVisibleNearinfraredSpectra1971.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: huntVisibleNearinfraredSpectra1971
year: Unknown Year
authors: Hunt, Graham R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Visible and Near-Infrared Spectra of Minerals and Rocks: II

* **Authors:** Hunt, Graham R.
* **Published in:** *Modern Geology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@huntVisibleNearinfraredSpectra1971)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ibrahimAssessmentMachineLearning2014.md (~75 words)
================================================================================
---
tags:
  - topic/literature
citekey: ibrahimAssessmentMachineLearning2014
year: Unknown Year
authors: Ibrahim, Adamu M. and Bennett, Brandon
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Assessment

* **Authors:** Ibrahim, Adamu M. and Bennett, Brandon
* **Published in:** *Procedia Computer Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ibrahimAssessmentMachineLearning2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/idrissiSustainableUsePhosphate2021.md (~117 words)
================================================================================
---
tags:
  - topic/literature
citekey: idrissiSustainableUsePhosphate2021
year: Unknown Year
authors: Idrissi, Hicham and Taha, Yassine and Elghali, Abdellatif and El Khessaimi,
  Yassine and Aboulayt, Abdelilah and Amalik, Jamal and Hakkou, Rachid and Benzaazoua,
  Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Sustainable Use of Phosphate Waste Rocks: From

* **Authors:** Idrissi, Hicham and Taha, Yassine and Elghali, Abdellatif and El Khessaimi, Yassine and Aboulayt, Abdelilah and Amalik, Jamal and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Materials Chemistry and Physics* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@idrissiSustainableUsePhosphate2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ihbachGeophysicalProspectingGroundwater2020.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: ihbachGeophysicalProspectingGroundwater2020
year: Unknown Year
authors: Ihbach, Fatim-Zahra and Kchikach, Azzouz and Jaffal, Mohammed and El Azzab,
  Driss and Khadiri Yazami, Oussama and Jourani, Es-Said and Pe\~n
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Geophysical Prospecting

* **Authors:** Ihbach, Fatim-Zahra and Kchikach, Azzouz and Jaffal, Mohammed and El Azzab, Driss and Khadiri Yazami, Oussama and Jourani, Es-Said and Pe\~n
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ihbachGeophysicalProspectingGroundwater2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/inabiInvestigationInnovativeCombined2024.md (~99 words)
================================================================================
---
tags:
  - topic/literature
citekey: inabiInvestigationInnovativeCombined2024
year: Unknown Year
authors: Inabi, Omar and Khalil, Abdessamad and Zouine, Abir and Hakkou, Rachid and
  Benzaazoua, Mostafa and Taha, Yassine
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Investigation of the Innovative Combined Reuse

* **Authors:** Inabi, Omar and Khalil, Abdessamad and Zouine, Abir and Hakkou, Rachid and Benzaazoua, Mostafa and Taha, Yassine
* **Published in:** *Buildings* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@inabiInvestigationInnovativeCombined2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/inabiSustainableMiningRepurposing2025.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: inabiSustainableMiningRepurposing2025
year: Unknown Year
authors: Inabi, Omar and Khalil, Abdessamad and Benzaazoua, Mostafa and Taha, Yassine
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Toward Sustainable Mining

* **Authors:** Inabi, Omar and Khalil, Abdessamad and Benzaazoua, Mostafa and Taha, Yassine
* **Published in:** *E3S Web of Conferences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@inabiSustainableMiningRepurposing2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/jahodaMachineLearningRecognizing2021.md (~104 words)
================================================================================
---
tags:
  - topic/literature
citekey: jahodaMachineLearningRecognizing2021
year: Unknown Year
authors: Jahoda, Pavel and Drozdovskiy, Igor and Payler, Samuel J. and Turchi, Leonardo
  and Bessone, Loredana and Sauro, Francesco
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Machine Learning for Recognizing Minerals from Multispectral Data

* **Authors:** Jahoda, Pavel and Drozdovskiy, Igor and Payler, Samuel J. and Turchi, Leonardo and Bessone, Loredana and Sauro, Francesco
* **Published in:** *The Analyst* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@jahodaMachineLearningRecognizing2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/jamiesonGeochemistryMineralogySolid2011.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: jamiesonGeochemistryMineralogySolid2011
year: Unknown Year
authors: Jamieson, H. E.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Geochemistry and Mineralogy

* **Authors:** Jamieson, H. E.
* **Published in:** *Elements* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@jamiesonGeochemistryMineralogySolid2011)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/jiangEvaluationPotentialRelease2015.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: jiangEvaluationPotentialRelease2015
year: Unknown Year
authors: Jiang, Liguo and Xue, Qiang and Liu, Lei
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluation of the Potential Release of Phosphorus from Phosphate Waste Rock Piles in Different Environmental Scenarios

* **Authors:** Jiang, Liguo and Xue, Qiang and Liu, Lei
* **Published in:** *Environmental Earth Sciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@jiangEvaluationPotentialRelease2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kalnickyFieldPortableXRF2001.md (~77 words)
================================================================================
---
tags:
  - topic/literature
citekey: kalnickyFieldPortableXRF2001
year: Unknown Year
authors: Kalnicky, Dennis J and Singhvi, Raj
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Field Portable XRF

* **Authors:** Kalnicky, Dennis J and Singhvi, Raj
* **Published in:** *Journal of Hazardous Materials* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kalnickyFieldPortableXRF2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/karasiakSpatialDependenceTraining2022.md (~98 words)
================================================================================
---
tags:
  - topic/literature
citekey: karasiakSpatialDependenceTraining2022
year: Unknown Year
authors: Karasiak, N. and Dejoux, J.-F. and Monteil, C. and Sheeren, D.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spatial Dependence between Training and Test Sets: Another Pitfall of Classification Accuracy Assessment in Remote Sensing

* **Authors:** Karasiak, N. and Dejoux, J.-F. and Monteil, C. and Sheeren, D.
* **Published in:** *Machine Learning* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@karasiakSpatialDependenceTraining2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kattenbornSpatiallyAutocorrelatedTraining2022.md (~117 words)
================================================================================
---
tags:
  - topic/literature
citekey: kattenbornSpatiallyAutocorrelatedTraining2022
year: Unknown Year
authors: Kattenborn, Teja and Schiefer, Felix and Frey, Julian and Feilhauer, Hannes
  and Mahecha, Miguel D. and Dormann, Carsten F.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spatially Autocorrelated Training and Validation Samples Inflate Performance Assessment of Convolutional Neural Networks

* **Authors:** Kattenborn, Teja and Schiefer, Felix and Frey, Julian and Feilhauer, Hannes and Mahecha, Miguel D. and Dormann, Carsten F.
* **Published in:** *ISPRS Open Journal of Photogrammetry and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kattenbornSpatiallyAutocorrelatedTraining2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kattenbornSpatiallyAutocorrelatedTraining2022a.md (~117 words)
================================================================================
---
tags:
  - topic/literature
citekey: kattenbornSpatiallyAutocorrelatedTraining2022a
year: Unknown Year
authors: Kattenborn, Teja and Schiefer, Felix and Frey, Julian and Feilhauer, Hannes
  and Mahecha, Miguel D. and Dormann, Carsten F.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spatially Autocorrelated Training and Validation Samples Inflate Performance Assessment of Convolutional Neural Networks

* **Authors:** Kattenborn, Teja and Schiefer, Felix and Frey, Julian and Feilhauer, Hannes and Mahecha, Miguel D. and Dormann, Carsten F.
* **Published in:** *ISPRS Open Journal of Photogrammetry and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kattenbornSpatiallyAutocorrelatedTraining2022a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/keshavaSpectralUnmixing2002.md (~74 words)
================================================================================
---
tags:
  - topic/literature
citekey: keshavaSpectralUnmixing2002
year: Unknown Year
authors: Keshava, N. and Mustard, J.F.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Unmixing

* **Authors:** Keshava, N. and Mustard, J.F.
* **Published in:** *IEEE Signal Processing Magazine* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@keshavaSpectralUnmixing2002)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/keshavaSpectralUnmixing2002a.md (~74 words)
================================================================================
---
tags:
  - topic/literature
citekey: keshavaSpectralUnmixing2002a
year: Unknown Year
authors: Keshava, N. and Mustard, J.F.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral Unmixing

* **Authors:** Keshava, N. and Mustard, J.F.
* **Published in:** *IEEE Signal Processing Magazine* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@keshavaSpectralUnmixing2002a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/khalilAssessmentSoilContamination2013.md (~113 words)
================================================================================
---
tags:
  - topic/literature
citekey: khalilAssessmentSoilContamination2013
year: Unknown Year
authors: Khalil, A. and Hanich, L. and Bannari, A. and Zouhri, L. and Pourret, O.
  and Hakkou, R.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Assessment of Soil Contamination around an Abandoned Mine in a Semi-Arid Environment Using Geochemistry and Geostatistics: Pre-work

* **Authors:** Khalil, A. and Hanich, L. and Bannari, A. and Zouhri, L. and Pourret, O. and Hakkou, R.
* **Published in:** *Journal of Geochemical Exploration* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@khalilAssessmentSoilContamination2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kleinmannPredictionWaterQuality2000.md (~82 words)
================================================================================
---
tags:
  - topic/literature
citekey: kleinmannPredictionWaterQuality2000
year: Unknown Year
authors: Kleinmann, R.L.P. and Acid Drainage Technology Initiative. Prediction Workgroup
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Prediction of Water Quality

* **Authors:** Kleinmann, R.L.P. and Acid Drainage Technology Initiative. Prediction Workgroup
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kleinmannPredictionWaterQuality2000)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/koiralaRobustSupervisedMethod2021.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: koiralaRobustSupervisedMethod2021
year: Unknown Year
authors: Koirala, Bikram and Zahiri, Zohreh and Lamberti, Alfredo and Scheunders,
  Paul
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Robust Supervised Method

* **Authors:** Koirala, Bikram and Zahiri, Zohreh and Lamberti, Alfredo and Scheunders, Paul
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@koiralaRobustSupervisedMethod2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/koiralaRobustSupervisedMethod2021a.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: koiralaRobustSupervisedMethod2021a
year: Unknown Year
authors: Koirala, Bikram and Zahiri, Zohreh and Lamberti, Alfredo and Scheunders,
  Paul
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Robust Supervised Method

* **Authors:** Koirala, Bikram and Zahiri, Zohreh and Lamberti, Alfredo and Scheunders, Paul
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@koiralaRobustSupervisedMethod2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kokalyUSGSSpectralLibrary2017.md (~134 words)
================================================================================
---
tags:
  - topic/literature
citekey: kokalyUSGSSpectralLibrary2017
year: Unknown Year
authors: Kokaly, Raymond F. and Clark, Roger and Swayze, Gregg and Livo, K. Eric and
  Hoefen, Todd and Pearson, Neil and Wise, Richard and Benzel, William and Lowers,
  Heather A. and Driscoll, Rhonda and Klein, Anna
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 USGS Spectral Library Version

* **Authors:** Kokaly, Raymond F. and Clark, Roger and Swayze, Gregg and Livo, K. Eric and Hoefen, Todd and Pearson, Neil and Wise, Richard and Benzel, William and Lowers, Heather A. and Driscoll, Rhonda and Klein, Anna
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kokalyUSGSSpectralLibrary2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kruseSpectralImageProcessing1993.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: kruseSpectralImageProcessing1993
year: Unknown Year
authors: Kruse, F.A. and Lefkoff, A.B. and Boardman, J.W. and Heidebrecht, K.B. and
  Shapiro, A.T. and Barloon, P.J. and Goetz, A.F.H.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Spectral Image Processing System (SIPS

* **Authors:** Kruse, F.A. and Lefkoff, A.B. and Boardman, J.W. and Heidebrecht, K.B. and Shapiro, A.T. and Barloon, P.J. and Goetz, A.F.H.
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kruseSpectralImageProcessing1993)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/kruseSpectralImageProcessing1993a.md (~124 words)
================================================================================
---
tags:
  - topic/literature
citekey: kruseSpectralImageProcessing1993a
year: Unknown Year
authors: Kruse, F. A. and Lefkoff, A. B. and Boardman, J. W. and Heidebrecht, K. B.
  and Shapiro, A. T. and Barloon, P. J. and Goetz, A. F. H.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Spectral Image Processing System (SIPS

* **Authors:** Kruse, F. A. and Lefkoff, A. B. and Boardman, J. W. and Heidebrecht, K. B. and Shapiro, A. T. and Barloon, P. J. and Goetz, A. F. H.
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@kruseSpectralImageProcessing1993a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/laaksoAssessingAbilityCombine2018.md (~94 words)
================================================================================
---
tags:
  - topic/literature
citekey: laaksoAssessingAbilityCombine2018
year: Unknown Year
authors: Laakso, K. and Middleton, M. and Heinig, T. and B\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Assessing the Ability to Combine Hyperspectral Imaging (HSI

* **Authors:** Laakso, K. and Middleton, M. and Heinig, T. and B\
* **Published in:** *International Journal of Applied Earth Observation and Geoinformation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@laaksoAssessingAbilityCombine2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/lawsonSolvingLeastSquares1995.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: lawsonSolvingLeastSquares1995
year: Unknown Year
authors: Lawson, Charles L. and Hanson, Richard J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Solving Least Squares Problems

* **Authors:** Lawson, Charles L. and Hanson, Richard J.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@lawsonSolvingLeastSquares1995)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/lawsonSolvingLeastSquares1995a.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: lawsonSolvingLeastSquares1995a
year: Unknown Year
authors: Lawson, Charles L. and Hanson, Richard J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Solving Least Squares Problems

* **Authors:** Lawson, Charles L. and Hanson, Richard J.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@lawsonSolvingLeastSquares1995a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/liDeepLearningHyperspectral2019.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: liDeepLearningHyperspectral2019
year: Unknown Year
authors: Li, Shutao and Song, Weiwei and Fang, Leyuan and Chen, Yushi and Ghamisi,
  Pedram and Benediktsson, Jon Atli
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Deep Learning

* **Authors:** Li, Shutao and Song, Weiwei and Fang, Leyuan and Chen, Yushi and Ghamisi, Pedram and Benediktsson, Jon Atli
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@liDeepLearningHyperspectral2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/liMineralProspectivityMapping2025.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: liMineralProspectivityMapping2025
year: Unknown Year
authors: Li, Quanke and Chen, Guoxiong and Wang, Detao
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineral Prospectivity Mapping Using Semi-supervised Machine Learning

* **Authors:** Li, Quanke and Chen, Guoxiong and Wang, Detao
* **Published in:** *Mathematical Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@liMineralProspectivityMapping2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/loizzoPrismaItalianHyperspectral2018.md (~104 words)
================================================================================
---
tags:
  - topic/literature
citekey: loizzoPrismaItalianHyperspectral2018
year: Unknown Year
authors: Loizzo, R. and Guarini, R. and Longo, F. and Scopa, T. and Formaro, R. and
  Facchinetti, C. and Varacalli, G.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Prisma: The Italian Hyperspectral Mission

* **Authors:** Loizzo, R. and Guarini, R. and Longo, F. and Scopa, T. and Formaro, R. and Facchinetti, C. and Varacalli, G.
* **Published in:** *IGARSS* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@loizzoPrismaItalianHyperspectral2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/loizzoPrismaMissionStatus2019.md (~102 words)
================================================================================
---
tags:
  - topic/literature
citekey: loizzoPrismaMissionStatus2019
year: Unknown Year
authors: Loizzo, R. and Daraio, M. and Guarini, R. and Longo, F. and Lorusso, R. and
  Dini, L. and Lopinto, E.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Prisma Mission Status

* **Authors:** Loizzo, R. and Daraio, M. and Guarini, R. and Longo, F. and Lorusso, R. and Dini, L. and Lopinto, E.
* **Published in:** *IGARSS* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@loizzoPrismaMissionStatus2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/loizzoPrismaMissionStatus2019a.md (~102 words)
================================================================================
---
tags:
  - topic/literature
citekey: loizzoPrismaMissionStatus2019a
year: Unknown Year
authors: Loizzo, R. and Daraio, M. and Guarini, R. and Longo, F. and Lorusso, R. and
  Dini, L. and Lopinto, E.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Prisma Mission Status

* **Authors:** Loizzo, R. and Daraio, M. and Guarini, R. and Longo, F. and Lorusso, R. and Dini, L. and Lopinto, E.
* **Published in:** *IGARSS* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@loizzoPrismaMissionStatus2019a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/lottermoserMineWastes2010.md (~66 words)
================================================================================
---
tags:
  - topic/literature
citekey: lottermoserMineWastes2010
year: Unknown Year
authors: Lottermoser, Bernd
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mine Wastes

* **Authors:** Lottermoser, Bernd
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@lottermoserMineWastes2010)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/loukiliMonitoringLandChanges2025.md (~105 words)
================================================================================
---
tags:
  - topic/literature
citekey: loukiliMonitoringLandChanges2025
year: Unknown Year
authors: Loukili, Ikram and Laamrani, Ahmed and El Ghorfi, Mustapha and El Moutak,
  Saida and Ghafiri, Abdessamad
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Monitoring Land Changes at an Open Mine Site Using Remote Sensing and Multi-Spectral Indices

* **Authors:** Loukili, Ikram and Laamrani, Ahmed and El Ghorfi, Mustapha and El Moutak, Saida and Ghafiri, Abdessamad
* **Published in:** *Heliyon* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@loukiliMonitoringLandChanges2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/maSituLeadImmobilization1993.md (~98 words)
================================================================================
---
tags:
  - topic/literature
citekey: maSituLeadImmobilization1993
year: Unknown Year
authors: Ma, Qi Ying and Traina, Samuel J. and Logan, Terry J. and Ryan, James A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 In Situ Lead Immobilization by Apatite

* **Authors:** Ma, Qi Ying and Traina, Samuel J. and Logan, Terry J. and Ryan, James A.
* **Published in:** *Environmental Science \& Technology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@maSituLeadImmobilization1993)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/malusisRestrictedSaltDiffusion2015.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: malusisRestrictedSaltDiffusion2015
year: Unknown Year
authors: Malusis, Michael A. and Kang, Jong-Beom and Shackelford, Charles D.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Restricted Salt Diffusion in a Geosynthetic Clay Liner

* **Authors:** Malusis, Michael A. and Kang, Jong-Beom and Shackelford, Charles D.
* **Published in:** *Environmental Geotechnics* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@malusisRestrictedSaltDiffusion2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mandendeHyperspectralCoreScanner2023.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: mandendeHyperspectralCoreScanner2023
year: Unknown Year
authors: Mandende, H. and Ndou, C. and Mothupi, T.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Core Scanner: An

* **Authors:** Mandende, H. and Ndou, C. and Mothupi, T.
* **Published in:** *Journal of the Southern African Institute of Mining and Metallurgy* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mandendeHyperspectralCoreScanner2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mansourIntegratingVNIRSWIR2025.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: mansourIntegratingVNIRSWIR2025
year: Unknown Year
authors: Mansour, Abdelhak El and Najih, Ahmed and Ouzemou, Jamal-Eddine and Laamrani,
  Ahmed and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Integrating VNIR

* **Authors:** Mansour, Abdelhak El and Najih, Ahmed and Ouzemou, Jamal-Eddine and Laamrani, Ahmed and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Sensors* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mansourIntegratingVNIRSWIR2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/marshallFieldlevelCropYield2022.md (~105 words)
================================================================================
---
tags:
  - topic/literature
citekey: marshallFieldlevelCropYield2022
year: Unknown Year
authors: Marshall, Michael and Belgiu, Mariana and Boschetti, Mirco and Pepe, Monica
  and Stein, Alfred and Nelson, Andy
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Field-Level Crop Yield Estimation with PRISMA

* **Authors:** Marshall, Michael and Belgiu, Mariana and Boschetti, Mirco and Pepe, Monica and Stein, Alfred and Nelson, Andy
* **Published in:** *ISPRS Journal of Photogrammetry and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@marshallFieldlevelCropYield2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mcclellanMineralogyCarbonateFluorapatites1980.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: mcclellanMineralogyCarbonateFluorapatites1980
year: Unknown Year
authors: McClellan, Guerry H.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mineralogy of Carbonate Fluorapatites

* **Authors:** McClellan, Guerry H.
* **Published in:** *Journal of the Geological Society* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mcclellanMineralogyCarbonateFluorapatites1980)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/meerdinkECOSTRESSSpectralLibrary2019.md (~94 words)
================================================================================
---
tags:
  - topic/literature
citekey: meerdinkECOSTRESSSpectralLibrary2019
year: Unknown Year
authors: Meerdink, Susan K. and Hook, Simon J. and Roberts, Dar A. and Abbott, Elsa
  A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The ECOSTRESS

* **Authors:** Meerdink, Susan K. and Hook, Simon J. and Roberts, Dar A. and Abbott, Elsa A.
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@meerdinkECOSTRESSSpectralLibrary2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/melganiClassificationHyperspectralRemote2004.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: melganiClassificationHyperspectralRemote2004
year: Unknown Year
authors: Melgani, F. and Bruzzone, L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Classification of Hyperspectral Remote Sensing Images with Support Vector Machines

* **Authors:** Melgani, F. and Bruzzone, L.
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@melganiClassificationHyperspectralRemote2004)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/melganiSupportVectorMachines2002.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: melganiSupportVectorMachines2002
year: Unknown Year
authors: Melgani, F. and Bruzzone, L.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Support Vector Machines for Classification of Hyperspectral Remote-Sensing Images

* **Authors:** Melgani, F. and Bruzzone, L.
* **Published in:** *IEEE International Geoscience* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@melganiSupportVectorMachines2002)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/meyerImportanceSpatialPredictor2019.md (~86 words)
================================================================================
---
tags:
  - topic/literature
citekey: meyerImportanceSpatialPredictor2019
year: Unknown Year
authors: Meyer, Hanna and Reudenbach, Christoph and W\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Importance of Spatial Predictor Variable Selection in Machine Learning Applications -- Moving

* **Authors:** Meyer, Hanna and Reudenbach, Christoph and W\
* **Published in:** *Ecological Modelling* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@meyerImportanceSpatialPredictor2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/meznedPerspectiveChapterOptical2023.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: meznedPerspectiveChapterOptical2023
year: Unknown Year
authors: Mezned, Nouha
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Perspective Chapter

* **Authors:** Mezned, Nouha
* **Published in:** *Functional Phosphate Materials* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@meznedPerspectiveChapterOptical2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mghazliDescriptionMicrobialCommunities2021.md (~101 words)
================================================================================
---
tags:
  - topic/literature
citekey: mghazliDescriptionMicrobialCommunities2021
year: Unknown Year
authors: Mghazli, Najoua and Sbabou, Laila and Hakkou, Rachid and Ouhammou, Ahmed
  and El Adnani, Mariam and Bruneel, Odile
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Description of Microbial Communities

* **Authors:** Mghazli, Najoua and Sbabou, Laila and Hakkou, Rachid and Ouhammou, Ahmed and El Adnani, Mariam and Bruneel, Odile
* **Published in:** *Frontiers in Microbiology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mghazliDescriptionMicrobialCommunities2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mielkeEnGeoMAP20AutomatedHyperspectral2016.md (~89 words)
================================================================================
---
tags:
  - topic/literature
citekey: mielkeEnGeoMAP20AutomatedHyperspectral2016
year: Unknown Year
authors: Mielke, Christian and Rogass, Christian and Boesche, Nina and Segl, Karl
  and Altenberger, Uwe
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 EnGeoMAP

* **Authors:** Mielke, Christian and Rogass, Christian and Boesche, Nina and Segl, Karl and Altenberger, Uwe
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mielkeEnGeoMAP20AutomatedHyperspectral2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mitchellFundamentalsSoilBehavior2005.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: mitchellFundamentalsSoilBehavior2005
year: Unknown Year
authors: Mitchell, James Kenneth and Soga, Ken
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Fundamentals of Soil Behavior

* **Authors:** Mitchell, James Kenneth and Soga, Ken
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mitchellFundamentalsSoilBehavior2005)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mostafaReleasePotentiallyToxic2025.md (~92 words)
================================================================================
---
tags:
  - topic/literature
citekey: mostafaReleasePotentiallyToxic2025
year: Unknown Year
authors: Mostafa, Mouataz T. and Farhat, Hassan I. and Abd El-Bakey
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Release of Potentially Toxic Elements from an Operational Phosphate Mine (Sebaiya

* **Authors:** Mostafa, Mouataz T. and Farhat, Hassan I. and Abd El-Bakey
* **Published in:** *Environmental Earth Sciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mostafaReleasePotentiallyToxic2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/mulderQuantifyingMineralAbundances2013.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: mulderQuantifyingMineralAbundances2013
year: Unknown Year
authors: Mulder, V.L. and Pl\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Quantifying Mineral Abundances of Complex Mixtures by Coupling Spectral Deconvolution of SWIR

* **Authors:** Mulder, V.L. and Pl\
* **Published in:** *Geoderma* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@mulderQuantifyingMineralAbundances2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/nascimentoVertexComponentAnalysis2005.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: nascimentoVertexComponentAnalysis2005
year: Unknown Year
authors: Nascimento, J.M.P. and Dias, J.M.B.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Vertex Component Analysis: A Fast Algorithm to Unmix Hyperspectral Data

* **Authors:** Nascimento, J.M.P. and Dias, J.M.B.
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@nascimentoVertexComponentAnalysis2005)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/nascimentoVertexComponentAnalysis2005a.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: nascimentoVertexComponentAnalysis2005a
year: Unknown Year
authors: Nascimento, J.M.P. and Dias, J.M.B.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Vertex Component Analysis: A Fast Algorithm to Unmix Hyperspectral Data

* **Authors:** Nascimento, J.M.P. and Dias, J.M.B.
* **Published in:** *IEEE Transactions on Geoscience and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@nascimentoVertexComponentAnalysis2005a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/nationalmineralsinformationcenterUSGeologicalSurvey2024.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: nationalmineralsinformationcenterUSGeologicalSurvey2024
year: Unknown Year
authors: National Minerals Information Center
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 U.S

* **Authors:** National Minerals Information Center
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@nationalmineralsinformationcenterUSGeologicalSurvey2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/nordstromMineWatersAcidic2011.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: nordstromMineWatersAcidic2011
year: Unknown Year
authors: Nordstrom, D. K.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mine Waters

* **Authors:** Nordstrom, D. K.
* **Published in:** *Elements* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@nordstromMineWatersAcidic2011)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/norouziInformationDepthNIR2021.md (~102 words)
================================================================================
---
tags:
  - topic/literature
citekey: norouziInformationDepthNIR2021
year: Unknown Year
authors: Norouzi, Sarem and Sadeghi, Morteza and Liaghat, Abdolmajid and Tuller, Markus
  and Jones, Scott B. and Ebrahimian, Hamed
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Information Depth of NIR

* **Authors:** Norouzi, Sarem and Sadeghi, Morteza and Liaghat, Abdolmajid and Tuller, Markus and Jones, Scott B. and Ebrahimian, Hamed
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@norouziInformationDepthNIR2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/notescoApplicationHyperspectralRemote2020.md (~79 words)
================================================================================
---
tags:
  - topic/literature
citekey: notescoApplicationHyperspectralRemote2020
year: Unknown Year
authors: Notesco, Gila and Weksler, Shahar and Ben-Dor
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Application of Hyperspectral Remote Sensing

* **Authors:** Notesco, Gila and Weksler, Shahar and Ben-Dor
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@notescoApplicationHyperspectralRemote2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ongPredictingAcidDrainage2003.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: ongPredictingAcidDrainage2003
year: Unknown Year
authors: Ong, Cindy and Cudahy, Thomas and Swayze, Gregg
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Predicting Acid Drainage Related Physicochemical Measurements Using Hyperspectral Data

* **Authors:** Ong, Cindy and Cudahy, Thomas and Swayze, Gregg
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ongPredictingAcidDrainage2003)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ouzemouIntegratingPostrainfallMultispectral2026.md (~110 words)
================================================================================
---
tags:
  - topic/literature
citekey: ouzemouIntegratingPostrainfallMultispectral2026
year: Unknown Year
authors: Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Whalen,
  Joann K. and Chehbouni, Abdelghani
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Integrating Post-Rainfall Multispectral Satellite-Derived Features and Multi-Source Datasets to Enhance Soil Salinity Mapping Accuracy

* **Authors:** Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Whalen, Joann K. and Chehbouni, Abdelghani
* **Published in:** *Remote Sensing Applications: Society and Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ouzemouIntegratingPostrainfallMultispectral2026)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ouzemouPredictingSoilSalinity2025.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: ouzemouPredictingSoilSalinity2025
year: Unknown Year
authors: Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Whalen,
  Joann K.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Predicting Soil Salinity Based

* **Authors:** Ouzemou, Jamal-Eddine and Laamrani, Ahmed and El Battay, Ali and Whalen, Joann K.
* **Published in:** *Soil Systems* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ouzemouPredictingSoilSalinity2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/percivalCustomizedSpectralLibraries2018.md (~125 words)
================================================================================
---
tags:
  - topic/literature
citekey: percivalCustomizedSpectralLibraries2018
year: Unknown Year
authors: Percival, Jeanne B. and Bosman, Sean A. and Potter, Eric G. and Peter, Jan
  M. and Laudadio, Alexandra B. and Abraham, Ashley C. and Shiley, Daniel A. and Sherry,
  Chris
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Customized Spectral Libraries

* **Authors:** Percival, Jeanne B. and Bosman, Sean A. and Potter, Eric G. and Peter, Jan M. and Laudadio, Alexandra B. and Abraham, Ashley C. and Shiley, Daniel A. and Sherry, Chris
* **Published in:** *Clays and Clay Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@percivalCustomizedSpectralLibraries2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/pereiraMultiTemporalMineralMapping2025.md (~67 words)
================================================================================
---
tags:
  - topic/literature
citekey: pereiraMultiTemporalMineralMapping2025
year: Unknown Year
authors: Pereira, In\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Multi-Temporal Mineral Mapping

* **Authors:** Pereira, In\
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@pereiraMultiTemporalMineralMapping2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/pignattiEvaluationPRISMAHyperspectral2021.md (~121 words)
================================================================================
---
tags:
  - topic/literature
citekey: pignattiEvaluationPRISMAHyperspectral2021
year: Unknown Year
authors: Pignatti, S. and Amodeo, A. and Mona, L. and Palombo, A. and Pascucci, S.
  and Rosoldi, M. and Santini, F. and Casa, R. and Laneve, G.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Evaluation of the PRISMA Hyperspectral Radiance Data

* **Authors:** Pignatti, S. and Amodeo, A. and Mona, L. and Palombo, A. and Pascucci, S. and Rosoldi, M. and Santini, F. and Casa, R. and Laneve, G.
* **Published in:** *2021 IEEE International Geoscience* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@pignattiEvaluationPRISMAHyperspectral2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/plantePredictingGeochemicalBehaviour2011.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: plantePredictingGeochemicalBehaviour2011
year: Unknown Year
authors: Plante, B. and Benzaazoua, M. and Bussi\`e
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Predicting Geochemical Behaviour

* **Authors:** Plante, B. and Benzaazoua, M. and Bussi\`e
* **Published in:** *Mine Water and the Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@plantePredictingGeochemicalBehaviour2011)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/plazaForewordSpecialIssue2012.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: plazaForewordSpecialIssue2012
year: Unknown Year
authors: Plaza, Antonio and Bioucas-Dias
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Foreword to the Special Issue

* **Authors:** Plaza, Antonio and Bioucas-Dias
* **Published in:** *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@plazaForewordSpecialIssue2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/plazaForewordSpecialIssue2012a.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: plazaForewordSpecialIssue2012a
year: Unknown Year
authors: Plaza, Antonio and Bioucas-Dias
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Foreword to the Special Issue

* **Authors:** Plaza, Antonio and Bioucas-Dias
* **Published in:** *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@plazaForewordSpecialIssue2012a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/plazaRecentDevelopmentsEndmember2011.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: plazaRecentDevelopmentsEndmember2011
year: Unknown Year
authors: Plaza, Antonio and Mart\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Recent Developments

* **Authors:** Plaza, Antonio and Mart\
* **Published in:** *Optical Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@plazaRecentDevelopmentsEndmember2011)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/plotonSpatialValidationReveals2020.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: plotonSpatialValidationReveals2020
year: Unknown Year
authors: Ploton, Pierre and Mortier, Fr\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spatial Validation Reveals Poor Predictive Performance of Large-Scale Ecological Mapping Models

* **Authors:** Ploton, Pierre and Mortier, Fr\
* **Published in:** *Nature Communications* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@plotonSpatialValidationReveals2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/pottsHandbookSilicateRock1987.md (~68 words)
================================================================================
---
tags:
  - topic/literature
citekey: pottsHandbookSilicateRock1987
year: Unknown Year
authors: Potts, P. J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Handbook

* **Authors:** Potts, P. J.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@pottsHandbookSilicateRock1987)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/pourEditorialSpecialIssue2021.md (~89 words)
================================================================================
---
tags:
  - topic/literature
citekey: pourEditorialSpecialIssue2021
year: Unknown Year
authors: Pour, Amin Beiranvand and Zoheir, Basem and Pradhan, Biswajeet and Hashim,
  Mazlan
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Editorial for the Special Issue

* **Authors:** Pour, Amin Beiranvand and Zoheir, Basem and Pradhan, Biswajeet and Hashim, Mazlan
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@pourEditorialSpecialIssue2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/prevotCorrespondanceEntreContenu1979.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: prevotCorrespondanceEntreContenu1979
year: Unknown Year
authors: Pr\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Une correspondance entre le contenu palynologique et la composition min\

* **Authors:** Pr\
* **Published in:** *Sciences G\* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@prevotCorrespondanceEntreContenu1979)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/qianGEOTECHNICALASPECTSLANDFILL.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: qianGEOTECHNICALASPECTSLANDFILL
year: Unknown Year
authors: Qian, Xuede
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 GEOTECHNICAL ASPECTS OF LANDFILL DESIGN AND CONSTRUCTION

* **Authors:** Qian, Xuede
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@qianGEOTECHNICALASPECTSLANDFILL)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/r.desikanExploringRockPhosphates2018.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: r.desikanExploringRockPhosphates2018
year: Unknown Year
authors: R. Desikan
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Exploring Rock Phosphates Using Hyperspectral Remote Sensing

* **Authors:** R. Desikan
* **Published in:** *2018 9th Workshop* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@r.desikanExploringRockPhosphates2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ramakrishnanHyperspectralRemoteSensing2015.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: ramakrishnanHyperspectralRemoteSensing2015
year: Unknown Year
authors: Ramakrishnan, D. and Bharti, Rishikesh
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Remote Sensing and Geological Applications

* **Authors:** Ramakrishnan, D. and Bharti, Rishikesh
* **Published in:** *Current Science* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ramakrishnanHyperspectralRemoteSensing2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ramseyCanSituGeochemical2012.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: ramseyCanSituGeochemical2012
year: Unknown Year
authors: Ramsey, Michael H. and Boon, Katy A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Can in Situ Geochemical Measurements Be More Fit-for-Purpose than Those Made Ex Situ?

* **Authors:** Ramsey, Michael H. and Boon, Katy A.
* **Published in:** *Applied Geochemistry* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ramseyCanSituGeochemical2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/rastiNoiseReductionHyperspectral2018.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: rastiNoiseReductionHyperspectral2018
year: Unknown Year
authors: Rasti, Behnood and Scheunders, Paul and Ghamisi, Pedram and Licciardi, Giorgio
  and Chanussot, Jocelyn
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Noise Reduction

* **Authors:** Rasti, Behnood and Scheunders, Paul and Ghamisi, Pedram and Licciardi, Giorgio and Chanussot, Jocelyn
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@rastiNoiseReductionHyperspectral2018)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/rastiNoiseReductionHyperspectral2018a.md (~90 words)
================================================================================
---
tags:
  - topic/literature
citekey: rastiNoiseReductionHyperspectral2018a
year: Unknown Year
authors: Rasti, Behnood and Scheunders, Paul and Ghamisi, Pedram and Licciardi, Giorgio
  and Chanussot, Jocelyn
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Noise Reduction

* **Authors:** Rasti, Behnood and Scheunders, Paul and Ghamisi, Pedram and Licciardi, Giorgio and Chanussot, Jocelyn
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@rastiNoiseReductionHyperspectral2018a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/robertsCrossvalidationStrategiesData2017.md (~120 words)
================================================================================
---
tags:
  - topic/literature
citekey: robertsCrossvalidationStrategiesData2017
year: Unknown Year
authors: Roberts, David R. and Bahn, Volker and Ciuti, Simone and Boyce, Mark S. and
  Elith, Jane and Guillera-Arroita, Gurutzeta and Hauenstein, Severin and Lahoz-Monfort,
  Jos\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Cross-validation Strategies for Data with Temporal, Spatial, Hierarchical, or Phylogenetic Structure

* **Authors:** Roberts, David R. and Bahn, Volker and Ciuti, Simone and Boyce, Mark S. and Elith, Jane and Guillera-Arroita, Gurutzeta and Hauenstein, Severin and Lahoz-Monfort, Jos\
* **Published in:** *Ecography* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@robertsCrossvalidationStrategiesData2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/roggeIntegrationSpatialSpectral2007.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: roggeIntegrationSpatialSpectral2007
year: Unknown Year
authors: Rogge, D. M. and Rivard, B. and Zhang, J. and Sanchez, A. and Harris, J.
  and Feng, J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Integration of Spatial--Spectral Information for the Improved Extraction of Endmembers

* **Authors:** Rogge, D. M. and Rivard, B. and Zhang, J. and Sanchez, A. and Harris, J. and Feng, J.
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@roggeIntegrationSpatialSpectral2007)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/romanoAppropriateStatisticsOrdinal2006.md (~95 words)
================================================================================
---
tags:
  - topic/literature
citekey: romanoAppropriateStatisticsOrdinal2006
year: Unknown Year
authors: Romano, Jeanine and Kromrey, Jeffrey D. and Coraggio, Jesse and Skowronek,
  Jeff
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Appropriate Statistics for Ordinal Level Data: Should

* **Authors:** Romano, Jeanine and Kromrey, Jeffrey D. and Coraggio, Jesse and Skowronek, Jeff
* **Published in:** *Annual Meeting of the Florida Association* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@romanoAppropriateStatisticsOrdinal2006)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/rousseauCorrectionsMatrixEffects2006.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: rousseauCorrectionsMatrixEffects2006
year: Unknown Year
authors: Rousseau, Richard M.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Corrections for Matrix Effects in X-ray

* **Authors:** Rousseau, Richard M.
* **Published in:** *Spectrochimica Acta Part B: Atomic Spectroscopy* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@rousseauCorrectionsMatrixEffects2006)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ruffinCombinedDerivativeSpectroscopy2008.md (~86 words)
================================================================================
---
tags:
  - topic/literature
citekey: ruffinCombinedDerivativeSpectroscopy2008
year: Unknown Year
authors: Ruffin, Chris and King, Roger L. and Younan, Nicolas H.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Combined Derivative Spectroscopy

* **Authors:** Ruffin, Chris and King, Roger L. and Younan, Nicolas H.
* **Published in:** *GIScience \& Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ruffinCombinedDerivativeSpectroscopy2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/ryskinVibrationsProtonsMinerals1974.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: ryskinVibrationsProtonsMinerals1974
year: Unknown Year
authors: Ryskin, \relax Ya
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Vibrations

* **Authors:** Ryskin, \relax Ya
* **Published in:** *The Infrared Spectra* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@ryskinVibrationsProtonsMinerals1974)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/safhiCharacterizationsPotentialRecovery2022.md (~118 words)
================================================================================
---
tags:
  - topic/literature
citekey: safhiCharacterizationsPotentialRecovery2022
year: Unknown Year
authors: Safhi, Amine El Mahdi and Amar, Hicham and El Berdai, Yahya and El Ghorfi,
  Mustapha and Taha, Yassine and Hakkou, Rachid and Al-Dahhan
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Characterizations and Potential Recovery Pathways of Phosphate Mines Waste Rocks

* **Authors:** Safhi, Amine El Mahdi and Amar, Hicham and El Berdai, Yahya and El Ghorfi, Mustapha and Taha, Yassine and Hakkou, Rachid and Al-Dahhan
* **Published in:** *Journal of Cleaner Production* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@safhiCharacterizationsPotentialRecovery2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/safhiCharacterizationsPotentialRecovery2022a.md (~118 words)
================================================================================
---
tags:
  - topic/literature
citekey: safhiCharacterizationsPotentialRecovery2022a
year: Unknown Year
authors: Safhi, Amine el Mahdi and Amar, Hicham and El Berdai, Yahya and El Ghorfi,
  Mustapha and Taha, Yassine and Hakkou, Rachid and Al-Dahhan
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Characterizations and Potential Recovery Pathways of Phosphate Mines Waste Rocks

* **Authors:** Safhi, Amine el Mahdi and Amar, Hicham and El Berdai, Yahya and El Ghorfi, Mustapha and Taha, Yassine and Hakkou, Rachid and Al-Dahhan
* **Published in:** *Journal of Cleaner Production* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@safhiCharacterizationsPotentialRecovery2022a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/sahooModellingSpectralUnmixing2023.md (~95 words)
================================================================================
---
tags:
  - topic/literature
citekey: sahooModellingSpectralUnmixing2023
year: Unknown Year
authors: Sahoo, Maitreya Mohan and Kalimuthu, R. and Pv, Arun and Porwal, Alok and
  Mathew, Shibu K.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Modelling Spectral Unmixing

* **Authors:** Sahoo, Maitreya Mohan and Kalimuthu, R. and Pv, Arun and Porwal, Alok and Mathew, Shibu K.
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@sahooModellingSpectralUnmixing2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/savitzkySmoothingDifferentiationData1964.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: savitzkySmoothingDifferentiationData1964
year: Unknown Year
authors: Savitzky, \relax Abraham
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Smoothing and Differentiation

* **Authors:** Savitzky, \relax Abraham
* **Published in:** *Analytical Chemistry* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@savitzkySmoothingDifferentiationData1964)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/savitzkySmoothingDifferentiationData1964a.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: savitzkySmoothingDifferentiationData1964a
year: Unknown Year
authors: Savitzky, \relax Abraham
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Smoothing and Differentiation

* **Authors:** Savitzky, \relax Abraham
* **Published in:** *Analytical Chemistry* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@savitzkySmoothingDifferentiationData1964a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/savitzkySmoothingDifferentiationData1964b.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: savitzkySmoothingDifferentiationData1964b
year: Unknown Year
authors: Savitzky, \relax Abraham
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Smoothing and Differentiation

* **Authors:** Savitzky, \relax Abraham
* **Published in:** *Analytical Chemistry* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@savitzkySmoothingDifferentiationData1964b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/savitzkySmoothingDifferentiationData1964c.md (~69 words)
================================================================================
---
tags:
  - topic/literature
citekey: savitzkySmoothingDifferentiationData1964c
year: Unknown Year
authors: Savitzky, \relax Abraham
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Smoothing and Differentiation

* **Authors:** Savitzky, \relax Abraham
* **Published in:** *Analytical Chemistry* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@savitzkySmoothingDifferentiationData1964c)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/schaepmanEarthSystemScience2009.md (~110 words)
================================================================================
---
tags:
  - topic/literature
citekey: schaepmanEarthSystemScience2009
year: Unknown Year
authors: Schaepman, Michael E. and Ustin, Susan L. and Plaza, Antonio J. and Painter,
  Thomas H. and Verrelst, Jochem and Liang, Shunlin
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Earth System Science Related Imaging Spectroscopy---An

* **Authors:** Schaepman, Michael E. and Ustin, Susan L. and Plaza, Antonio J. and Painter, Thomas H. and Verrelst, Jochem and Liang, Shunlin
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@schaepmanEarthSystemScience2009)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/scholzSustainableUsePhosphorus2013.md (~86 words)
================================================================================
---
tags:
  - topic/literature
citekey: scholzSustainableUsePhosphorus2013
year: Unknown Year
authors: Scholz, Roland W. and Ulrich, Andrea E. and Eilitt\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Sustainable Use of Phosphorus: A

* **Authors:** Scholz, Roland W. and Ulrich, Andrea E. and Eilitt\
* **Published in:** *Science of The Total Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@scholzSustainableUsePhosphorus2013)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/sealProgressGeoenvironmentalModels2002.md (~73 words)
================================================================================
---
tags:
  - topic/literature
citekey: sealProgressGeoenvironmentalModels2002
year: Unknown Year
authors: Unknown Authors
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Progress on Geoenvironmental Models for Selected Mineral Deposit Types

* **Authors:** Unknown Authors
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@sealProgressGeoenvironmentalModels2002)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/shadmanroodposhtiUncertaintyAssessmentHyperspectral2019.md (~87 words)
================================================================================
---
tags:
  - topic/literature
citekey: shadmanroodposhtiUncertaintyAssessmentHyperspectral2019
year: Unknown Year
authors: Shadman Roodposhti, Majid and Aryal, Jagannath and Lucieer, Arko and Bryan,
  Brett A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Uncertainty Assessment

* **Authors:** Shadman Roodposhti, Majid and Aryal, Jagannath and Lucieer, Arko and Bryan, Brett A.
* **Published in:** *Entropy* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@shadmanroodposhtiUncertaintyAssessmentHyperspectral2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/sheblPRISMAHyperspectralData2023.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: sheblPRISMAHyperspectralData2023
year: Unknown Year
authors: Shebl, Ali and Abriha, D\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 PRISMA

* **Authors:** Shebl, Ali and Abriha, D\
* **Published in:** *Ore Geology Reviews* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@sheblPRISMAHyperspectralData2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/shirmardComparativeStudyConvolutional2022.md (~97 words)
================================================================================
---
tags:
  - topic/literature
citekey: shirmardComparativeStudyConvolutional2022
year: Unknown Year
authors: Shirmard, Hojat and Farahbakhsh, Ehsan and Heidari, Elnaz and Beiranvand
  Pour, Amin and Pradhan, Biswajeet and M\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Comparative Study

* **Authors:** Shirmard, Hojat and Farahbakhsh, Ehsan and Heidari, Elnaz and Beiranvand Pour, Amin and Pradhan, Biswajeet and M\
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@shirmardComparativeStudyConvolutional2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/shirmardReviewMachineLearning2022.md (~99 words)
================================================================================
---
tags:
  - topic/literature
citekey: shirmardReviewMachineLearning2022
year: Unknown Year
authors: Shirmard, Hojat and Farahbakhsh, Ehsan and Muller, R. Dietmar and Chandra,
  Rohitash
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Review of Machine Learning in Processing Remote Sensing Data for Mineral Exploration

* **Authors:** Shirmard, Hojat and Farahbakhsh, Ehsan and Muller, R. Dietmar and Chandra, Rohitash
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@shirmardReviewMachineLearning2022)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/simapeyghambariHyperspectralRemoteSensing2021.md (~81 words)
================================================================================
---
tags:
  - topic/literature
citekey: simapeyghambariHyperspectralRemoteSensing2021
year: Unknown Year
authors: Sima Peyghambari
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Hyperspectral Remote Sensing in Lithological Mapping, Mineral Exploration, and Environmental Geology: An Updated Review

* **Authors:** Sima Peyghambari
* **Published in:** *Journal of Applied Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@simapeyghambariHyperspectralRemoteSensing2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/slanskyGeologySedimentaryPhosphates1986.md (~74 words)
================================================================================
---
tags:
  - topic/literature
citekey: slanskyGeologySedimentaryPhosphates1986
year: Unknown Year
authors: Slansky, Maurice and Slansky, Maurice
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Geology of Sedimentary Phosphates

* **Authors:** Slansky, Maurice and Slansky, Maurice
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@slanskyGeologySedimentaryPhosphates1986)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/smilPhosphorusEnvironmentNatural2000.md (~74 words)
================================================================================
---
tags:
  - topic/literature
citekey: smilPhosphorusEnvironmentNatural2000
year: Unknown Year
authors: Smil, Vaclav
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Phosphorus in the Environment: Natural

* **Authors:** Smil, Vaclav
* **Published in:** *Annual Review of Energy and the Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@smilPhosphorusEnvironmentNatural2000)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/stonerCharacteristicVariationsReflectance1981.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: stonerCharacteristicVariationsReflectance1981
year: Unknown Year
authors: Stoner, E. R. and Baumgardner, M. F.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Characteristic Variations

* **Authors:** Stoner, E. R. and Baumgardner, M. F.
* **Published in:** *Soil Science Society of America Journal* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@stonerCharacteristicVariationsReflectance1981)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/storchEnMAPImagingSpectroscopy2023.md (~126 words)
================================================================================
---
tags:
  - topic/literature
citekey: storchEnMAPImagingSpectroscopy2023
year: Unknown Year
authors: Storch, Tobias and Honold, Hans-Peter and Chabrillat, Sabine and Habermeyer,
  Martin and Tucker, Paul and Brell, Maximilian and Ohndorf, Andreas and Wirth, Katrin
  and Betz, Matthias and Kuchler, Michael and M\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The EnMAP

* **Authors:** Storch, Tobias and Honold, Hans-Peter and Chabrillat, Sabine and Habermeyer, Martin and Tucker, Paul and Brell, Maximilian and Ohndorf, Andreas and Wirth, Katrin and Betz, Matthias and Kuchler, Michael and M\
* **Published in:** *Remote Sensing of Environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@storchEnMAPImagingSpectroscopy2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/sudharsanMachineLearningdrivenMineral2025.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: sudharsanMachineLearningdrivenMineral2025
year: Unknown Year
authors: Sudharsan, S. and Hemalatha, R. and V., Tejas N. and Sivakumar, Krisha Aarunee
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Machine Learning-Driven Mineral Identification Using PRISMA

* **Authors:** Sudharsan, S. and Hemalatha, R. and V., Tejas N. and Sivakumar, Krisha Aarunee
* **Published in:** *Earth Science Informatics* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@sudharsanMachineLearningdrivenMineral2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/swayzeUsingImagingSpectroscopy2000.md (~154 words)
================================================================================
---
tags:
  - topic/literature
citekey: swayzeUsingImagingSpectroscopy2000
year: Unknown Year
authors: Swayze, G. A. and Smith, K. S. and Clark, R. N. and Sutley, S. J. and Pearson,
  R. M. and Vance, J. S. and Hageman, P. L. and Briggs, Paul H. and Meier, A. L. and
  Singleton, M. J. and Roth, S.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Using Imaging Spectroscopy to Map Acidic Mine Waste

* **Authors:** Swayze, G. A. and Smith, K. S. and Clark, R. N. and Sutley, S. J. and Pearson, R. M. and Vance, J. S. and Hageman, P. L. and Briggs, Paul H. and Meier, A. L. and Singleton, M. J. and Roth, S.
* **Published in:** *Environmental Science \& Technology* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@swayzeUsingImagingSpectroscopy2000)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tahaZeroSolidWaste2021.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: tahaZeroSolidWaste2021
year: Unknown Year
authors: Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua,
  Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Towards Zero Solid Waste

* **Authors:** Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tahaZeroSolidWaste2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tahaZeroSolidWaste2021a.md (~85 words)
================================================================================
---
tags:
  - topic/literature
citekey: tahaZeroSolidWaste2021a
year: Unknown Year
authors: Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua,
  Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Towards Zero Solid Waste

* **Authors:** Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tahaZeroSolidWaste2021a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tahaZeroSolidWaste2021b.md (~91 words)
================================================================================
---
tags:
  - topic/literature
citekey: tahaZeroSolidWaste2021b
year: Unknown Year
authors: Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua,
  Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Towards Zero Solid Waste in the Sedimentary Phosphate Industry: Challenges

* **Authors:** Taha, Yassine and Elghali, Abdellatif and Hakkou, Rachid and Benzaazoua, Mostafa
* **Published in:** *Minerals* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tahaZeroSolidWaste2021b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/testaBACKFILLINGOPENPITMETALLIC2007.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: testaBACKFILLINGOPENPITMETALLIC2007
year: Unknown Year
authors: Testa, Stephen M. and Pompy, James S.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 BACKFILLING OF OPEN-PIT METALLIC MINES

* **Authors:** Testa, Stephen M. and Pompy, James S.
* **Published in:** *Journal American Society of Mining and Reclamation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@testaBACKFILLINGOPENPITMETALLIC2007)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/testaBACKFILLINGOPENPITMETALLIC2007a.md (~84 words)
================================================================================
---
tags:
  - topic/literature
citekey: testaBACKFILLINGOPENPITMETALLIC2007a
year: Unknown Year
authors: Testa, Stephen M. and Pompy, James S.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 BACKFILLING OF OPEN-PIT METALLIC MINES

* **Authors:** Testa, Stephen M. and Pompy, James S.
* **Published in:** *Journal American Society of Mining and Reclamation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@testaBACKFILLINGOPENPITMETALLIC2007a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tsaiDerivativeAnalysisHyperspectral.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: tsaiDerivativeAnalysisHyperspectral
year: Unknown Year
authors: Tsai, Fuan and Philpot, William
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Derivative Analysis

* **Authors:** Tsai, Fuan and Philpot, William
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tsaiDerivativeAnalysisHyperspectral)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tsaiDerivativeAnalysisHyperspectrala.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: tsaiDerivativeAnalysisHyperspectrala
year: Unknown Year
authors: Tsai, Fuan and Philpot, William
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Derivative Analysis

* **Authors:** Tsai, Fuan and Philpot, William
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tsaiDerivativeAnalysisHyperspectrala)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/turnerVisibleShortwaveInfrared2016.md (~88 words)
================================================================================
---
tags:
  - topic/literature
citekey: turnerVisibleShortwaveInfrared2016
year: Unknown Year
authors: Turner, David J. and Rivard, Benoit and Groat, Lee A.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Visible and Short-Wave Infrared Reflectance Spectroscopy of REE

* **Authors:** Turner, David J. and Rivard, Benoit and Groat, Lee A.
* **Published in:** *American Mineralogist* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@turnerVisibleShortwaveInfrared2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/tusaDrillCoreMineralAbundance2020.md (~70 words)
================================================================================
---
tags:
  - topic/literature
citekey: tusaDrillCoreMineralAbundance2020
year: Unknown Year
authors: Tu\c s
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Drill-Core Mineral Abundance Estimation Using Hyperspectral

* **Authors:** Tu\c s
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@tusaDrillCoreMineralAbundance2020)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/valaviBlockCVPackageGenerating2019.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: valaviBlockCVPackageGenerating2019
year: Unknown Year
authors: Valavi, Roozbeh and Elith, Jane and Lahoz-Monfort
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 blockCV

* **Authors:** Valavi, Roozbeh and Elith, Jane and Lahoz-Monfort
* **Published in:** *Methods in Ecology and Evolution* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@valaviBlockCVPackageGenerating2019)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vandermeerAnalysisSpectralAbsorption2004.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: vandermeerAnalysisSpectralAbsorption2004
year: Unknown Year
authors: van der Meer
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Analysis of Spectral Absorption Features in Hyperspectral Imagery

* **Authors:** van der Meer
* **Published in:** *International Journal of Applied Earth Observation and Geoinformation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vandermeerAnalysisSpectralAbsorption2004)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vandermeerMultiHyperspectralGeologic2012.md (~165 words)
================================================================================
---
tags:
  - topic/literature
citekey: vandermeerMultiHyperspectralGeologic2012
year: Unknown Year
authors: Van Der Meer, Freek D. and Van Der Werff, Harald M.A. and Van Ruitenbeek,
  Frank J.A. and Hecker, Chris A. and Bakker, Wim H. and Noomen, Marleen F. and Van
  Der Meijde, Mark and Carranza, E. John M. and Smeth, J. Boudewijn De and Woldai,
  Tsehaie
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Multi- and Hyperspectral Geologic Remote Sensing: A

* **Authors:** Van Der Meer, Freek D. and Van Der Werff, Harald M.A. and Van Ruitenbeek, Frank J.A. and Hecker, Chris A. and Bakker, Wim H. and Noomen, Marleen F. and Van Der Meijde, Mark and Carranza, E. John M. and Smeth, J. Boudewijn De and Woldai, Tsehaie
* **Published in:** *International Journal of Applied Earth Observation and Geoinformation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vandermeerMultiHyperspectralGeologic2012)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vandermeerMultiHyperspectralGeologic2012a.md (~165 words)
================================================================================
---
tags:
  - topic/literature
citekey: vandermeerMultiHyperspectralGeologic2012a
year: Unknown Year
authors: Van Der Meer, Freek D. and Van Der Werff, Harald M.A. and Van Ruitenbeek,
  Frank J.A. and Hecker, Chris A. and Bakker, Wim H. and Noomen, Marleen F. and Van
  Der Meijde, Mark and Carranza, E. John M. and Smeth, J. Boudewijn De and Woldai,
  Tsehaie
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Multi- and Hyperspectral Geologic Remote Sensing: A

* **Authors:** Van Der Meer, Freek D. and Van Der Werff, Harald M.A. and Van Ruitenbeek, Frank J.A. and Hecker, Chris A. and Bakker, Wim H. and Noomen, Marleen F. and Van Der Meijde, Mark and Carranza, E. John M. and Smeth, J. Boudewijn De and Woldai, Tsehaie
* **Published in:** *International Journal of Applied Earth Observation and Geoinformation* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vandermeerMultiHyperspectralGeologic2012a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vandijkPhosphorusFlowsBalances2016.md (~78 words)
================================================================================
---
tags:
  - topic/literature
citekey: vandijkPhosphorusFlowsBalances2016
year: Unknown Year
authors: van Dijk
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Phosphorus Flows and Balances of the European Union Member States

* **Authors:** van Dijk
* **Published in:** *The Science of the total environment* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vandijkPhosphorusFlowsBalances2016)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vangenuchtenClosedformEquationPredicting1980.md (~76 words)
================================================================================
---
tags:
  - topic/literature
citekey: vangenuchtenClosedformEquationPredicting1980
year: Unknown Year
authors: Van Genuchten, M. \relax Th
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 A Closed

* **Authors:** Van Genuchten, M. \relax Th
* **Published in:** *Soil Science Society of America Journal* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vangenuchtenClosedformEquationPredicting1980)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vangiNewHyperspectralSatellite2021.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: vangiNewHyperspectralSatellite2021
year: Unknown Year
authors: Vangi, Elia and D
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The New Hyperspectral Satellite PRISMA

* **Authors:** Vangi, Elia and D
* **Published in:** *Sensors* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vangiNewHyperspectralSatellite2021)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/vankauwenberghWorldPhosphateRock2010.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: vankauwenberghWorldPhosphateRock2010
year: Unknown Year
authors: Van Kauwenbergh, S. J.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 World Phosphate Rock Reserves

* **Authors:** Van Kauwenbergh, S. J.
* **Published in:** *Unknown Source* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@vankauwenberghWorldPhosphateRock2010)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/wangSpectralSpatialMultifeaturebased2017.md (~100 words)
================================================================================
---
tags:
  - topic/literature
citekey: wangSpectralSpatialMultifeaturebased2017
year: Unknown Year
authors: Wang, Lizhe and Zhang, Jiabin and Liu, Peng and Choo, Kim-Kwang Raymond and
  Huang, Fang
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral--Spatial Multi-Feature-Based Deep Learning for Hyperspectral Remote Sensing Image Classification

* **Authors:** Wang, Lizhe and Zhang, Jiabin and Liu, Peng and Choo, Kim-Kwang Raymond and Huang, Fang
* **Published in:** *Soft Computing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@wangSpectralSpatialMultifeaturebased2017)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/wangUncertaintyQuantificationDeep2025.md (~80 words)
================================================================================
---
tags:
  - topic/literature
citekey: wangUncertaintyQuantificationDeep2025
year: Unknown Year
authors: Wang, Ziye and Zuo, Renguang and Kreuzer, Oliver P.
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Uncertainty Quantification

* **Authors:** Wang, Ziye and Zuo, Renguang and Kreuzer, Oliver P.
* **Published in:** *Mathematical Geosciences* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@wangUncertaintyQuantificationDeep2025)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/waskeMappingHyperspectralAVIRIS2009.md (~71 words)
================================================================================
---
tags:
  - topic/literature
citekey: waskeMappingHyperspectralAVIRIS2009
year: Unknown Year
authors: Waske, Bj\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Mapping of Hyperspectral AVIRIS

* **Authors:** Waske, Bj\
* **Published in:** *Canadian Journal of Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@waskeMappingHyperspectralAVIRIS2009)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/withersStewardshipTackleGlobal2015.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: withersStewardshipTackleGlobal2015
year: Unknown Year
authors: Withers, Paul J. A. and Van Dijk, Kimo C. and Neset, Tina-Simone S. and Nesme,
  Thomas and Oenema, Oene and Rub\ae
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Stewardship to Tackle Global Phosphorus Inefficiency: The

* **Authors:** Withers, Paul J. A. and Van Dijk, Kimo C. and Neset, Tina-Simone S. and Nesme, Thomas and Oenema, Oene and Rub\ae
* **Published in:** *AMBIO* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@withersStewardshipTackleGlobal2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/woldPLSregressionBasicTool2001.md (~72 words)
================================================================================
---
tags:
  - topic/literature
citekey: woldPLSregressionBasicTool2001
year: Unknown Year
authors: Wold, Svante and Sj\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 PLS-regression

* **Authors:** Wold, Svante and Sj\
* **Published in:** *Chemometrics and Intelligent Laboratory Systems* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@woldPLSregressionBasicTool2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/yangEnvironmentalImpactsCaused2014.md (~108 words)
================================================================================
---
tags:
  - topic/literature
citekey: yangEnvironmentalImpactsCaused2014
year: Unknown Year
authors: Yang, Yu-You and Wu, Huai-Na and Shen, Shui-Long and Horpibulsuk, Suksun
  and Xu, Ye-Shuang and Zhou, Qing-Hong
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Environmental Impacts Caused by Phosphate Mining and Ecological Restoration: A Case History in Kunming

* **Authors:** Yang, Yu-You and Wu, Huai-Na and Shen, Shui-Long and Horpibulsuk, Suksun and Xu, Ye-Shuang and Zhou, Qing-Hong
* **Published in:** *Natural Hazards* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@yangEnvironmentalImpactsCaused2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/yekutieliResamplingbasedFalseDiscovery1999.md (~86 words)
================================================================================
---
tags:
  - topic/literature
citekey: yekutieliResamplingbasedFalseDiscovery1999
year: Unknown Year
authors: Yekutieli, Daniel and Benjamini, Yoav
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Resampling-Based False Discovery Rate Controlling Multiple Test Procedures for Correlated Test Statistics

* **Authors:** Yekutieli, Daniel and Benjamini, Yoav
* **Published in:** *Journal of Statistical Planning and Inference* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@yekutieliResamplingbasedFalseDiscovery1999)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/yueSpectralSpatialClassification2015.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: yueSpectralSpatialClassification2015
year: Unknown Year
authors: Yue, Jun and Zhao, Wenzhi and Mao, Shanjun and Liu, Hui
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Spectral--Spatial Classification of Hyperspectral Images Using Deep Convolutional Neural Networks

* **Authors:** Yue, Jun and Zhao, Wenzhi and Mao, Shanjun and Liu, Hui
* **Published in:** *Remote Sensing Letters* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@yueSpectralSpatialClassification2015)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zainiDeterminationCarbonateRock2014.md (~93 words)
================================================================================
---
tags:
  - topic/literature
citekey: zainiDeterminationCarbonateRock2014
year: Unknown Year
authors: Zaini, Nasrullah and Van Der Meer, Freek and Van Der Werff, Harald
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Determination of Carbonate Rock Chemistry Using Laboratory-Based Hyperspectral Imagery

* **Authors:** Zaini, Nasrullah and Van Der Meer, Freek and Van Der Werff, Harald
* **Published in:** *Remote Sensing* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zainiDeterminationCarbonateRock2014)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zhangCHARACTERIZATIONQUANTITATIVEANALYSIS2001.md (~89 words)
================================================================================
---
tags:
  - topic/literature
citekey: zhangCHARACTERIZATIONQUANTITATIVEANALYSIS2001
year: Unknown Year
authors: Zhang, Guangyu and Wasyliuk, Ken and Pan, Yuanming
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 THE CHARACTERIZATION AND QUANTITATIVE ANALYSIS OF CLAY MINERALS IN THE ATHABASCA BASIN

* **Authors:** Zhang, Guangyu and Wasyliuk, Ken and Pan, Yuanming
* **Published in:** *The Canadian Mineralogist* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zhangCHARACTERIZATIONQUANTITATIVEANALYSIS2001)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zhangPredictionRecyclePhosphate2024.md (~106 words)
================================================================================
---
tags:
  - topic/literature
citekey: zhangPredictionRecyclePhosphate2024
year: Unknown Year
authors: Zhang, Ling and Hou, Haochun and Yang, Lu and Zhang, Zeliang and Zhao, Yan
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Prediction for the Recycle of Phosphate Tailings in Enhanced Gravity Field Based on Machine Learning and Interpretable Analysis

* **Authors:** Zhang, Ling and Hou, Haochun and Yang, Lu and Zhang, Zeliang and Zhao, Yan
* **Published in:** *Waste Management* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zhangPredictionRecyclePhosphate2024)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zineAdvancementsMineClosure2023.md (~95 words)
================================================================================
---
tags:
  - topic/literature
citekey: zineAdvancementsMineClosure2023
year: Unknown Year
authors: Zine, Hamza and El Mansour, Abdelhak and Hakkou, Rachid and Papazoglou, Eleni
  G. and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Advancements in Mine Closure

* **Authors:** Zine, Hamza and El Mansour, Abdelhak and Hakkou, Rachid and Papazoglou, Eleni G. and Benzaazoua, Mostafa
* **Published in:** *Mining* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zineAdvancementsMineClosure2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zineNativePlantDiversity2023.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: zineNativePlantDiversity2023
year: Unknown Year
authors: Zine, Hamza and Hakkou, Rachid and Elmansour, Abdelhak and Elgadi, Sara and
  Ouhammou, Ahmed and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Native Plant Diversity for Ecological Reclamation in Moroccan

* **Authors:** Zine, Hamza and Hakkou, Rachid and Elmansour, Abdelhak and Elgadi, Sara and Ouhammou, Ahmed and Benzaazoua, Mostafa
* **Published in:** *Biodiversity Data Journal* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zineNativePlantDiversity2023)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zineNativePlantDiversity2023a.md (~105 words)
================================================================================
---
tags:
  - topic/literature
citekey: zineNativePlantDiversity2023a
year: Unknown Year
authors: Zine, Hamza and Hakkou, Rachid and El Mansour, Abdelhak and Elgadi, Sara
  and Ouhammou, Ahmed and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Native Plant Diversity for Ecological Reclamation in Moroccan

* **Authors:** Zine, Hamza and Hakkou, Rachid and El Mansour, Abdelhak and Elgadi, Sara and Ouhammou, Ahmed and Benzaazoua, Mostafa
* **Published in:** *Biodiversity Data Journal* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zineNativePlantDiversity2023a)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zineNativePlantDiversity2023b.md (~103 words)
================================================================================
---
tags:
  - topic/literature
citekey: zineNativePlantDiversity2023b
year: Unknown Year
authors: Zine, Hamza and Hakkou, Rachid and Elmansour, Abdelhak and Elgadi, Sara and
  Ouhammou, Ahmed and Benzaazoua, Mostafa
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 Native Plant Diversity for Ecological Reclamation in Moroccan

* **Authors:** Zine, Hamza and Hakkou, Rachid and Elmansour, Abdelhak and Elgadi, Sara and Ouhammou, Ahmed and Benzaazoua, Mostafa
* **Published in:** *Biodiversity Data Journal* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zineNativePlantDiversity2023b)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/sources/zouhriCretaceousTertiaryPlateaus2008.md (~83 words)
================================================================================
---
tags:
  - topic/literature
citekey: zouhriCretaceousTertiaryPlateaus2008
year: Unknown Year
authors: Zouhri, S. and Kchikach, A. and Saddiqi, O. and Ha\
generated_by: claude
type: literature-note
status: reference
created: '2026-06-09'
---

# 📄 The Cretaceous-Tertiary Plateaus

* **Authors:** Zouhri, S. and Kchikach, A. and Saddiqi, O. and Ha\
* **Published in:** *Continental Evolution* (Unknown Year)
* **Zotero Link:** [Open in Zotero](zotero://select/items/@zouhriCretaceousTertiaryPlateaus2008)

---

## 💡 Key Takeaways
* *Summary of findings...*

## 🛠️ Methodology & Relevance
* *How this relates to multi-scale remote sensing / unmixing...*




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/EnMAP Satellite.md (~554 words)
================================================================================
---
tags:
  - ch3
  - remote-sensing
  - satellite
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Handheld XRF.md (~524 words)
================================================================================
---
tags:
  - ch1
  - geochemistry
  - instrument
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Hyperspectral Imaging.md (~517 words)
================================================================================
---
tags:
  - remote-sensing
  - spectroscopy
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Machine Learning for Hyperspectral.md (~683 words)
================================================================================
---
tags:
  - ch2
  - machine-learning
  - method
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-06-05'
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
FILE: 04_Knowledge Base/wiki/concepts/Mineral Assemblages.md (~535 words)
================================================================================
---
tags:
  - benguerir
  - mineralogy
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-06-08'
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
FILE: 04_Knowledge Base/wiki/concepts/PRISMA Satellite.md (~403 words)
================================================================================
---
tags:
  - PRISMA
  - core
  - remote-sensing
  - satellite
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
domain: Remote Sensing
type: concept-note
status: seed
created: '2026-06-08'
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
FILE: 04_Knowledge Base/wiki/concepts/Phosphate Mine Waste.md (~506 words)
================================================================================
---
tags:
  - benguerir
  - geology
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-06-08'
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
FILE: 04_Knowledge Base/wiki/concepts/Reclamation Monitoring.md (~686 words)
================================================================================
---
tags:
  - ch3
  - environmental
  - reclamation
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Reclamation Progress Index.md (~569 words)
================================================================================
---
tags:
  - ch3
  - novel-contribution
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Shannon Entropy Uncertainty.md (~444 words)
================================================================================
---
tags:
  - ch2
  - method
  - statistics
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Spatially Constrained Cross-Validation.md (~581 words)
================================================================================
---
tags:
  - ch2
  - method
  - statistics
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Spectral Analysis.md (~270 words)
================================================================================
---
tags:
  - spectral-analysis
  - topic/wiki-concept
created: '2026-06-07'
generated_by: claude
summary: "Spectral analysis methods used in hyperspectral remote sensing \u2014 library\
  \ matching, unmixing, classification."
type: concept-note
status: seed
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
FILE: 04_Knowledge Base/wiki/concepts/Spectral Library Matching.md (~519 words)
================================================================================
---
tags:
  - method
  - spectroscopy
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-05-24'
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

---

*Related: [[04_Knowledge Base/AI-Generated/thesis-ingestion/Spectroscopy Notebook Ingestion|Spectroscopy Notebook Ingestion]]*




================================================================================
FILE: 04_Knowledge Base/wiki/concepts/Spectral Unmixing VCA-FCLS.md (~582 words)
================================================================================
---
tags:
  - ch1
  - ch3
  - method
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
source-of-truth: Thesis Manuscript-Abdelhak EL MANSOUR 2026.docx
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/VNIR-SWIR Spectroscopy.md (~534 words)
================================================================================
---
tags:
  - ch1
  - spectroscopy
  - topic/wiki-concept
updated: 2026-05-24
generated_by: claude
type: concept-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/concepts/Waste Rock Characterization.md (~218 words)
================================================================================
---
tags:
  - topic/wiki-concept
  - waste-rock
created: '2026-06-07'
generated_by: claude
summary: "Mine waste rock characterization \u2014 mineralogy, spectral properties,\
  \ and monitoring at Benguerir."
type: concept-note
status: seed
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
FILE: 04_Knowledge Base/wiki/entities/Gantour Basin.md (~462 words)
================================================================================
---
tags:
  - geology
  - morocco
  - topic/wiki-entity
updated: 2026-05-24
generated_by: claude
type: entity-note
status: seed
created: '2026-05-24'
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
FILE: 04_Knowledge Base/wiki/entities/OCP Group and Benguerir Mine.md (~298 words)
================================================================================
---
tags:
  - Morocco
  - OCP
  - institution
  - mining
  - phosphate
  - topic/wiki-entity
updated: 2026-05-24
generated_by: claude
type: institution
status: seed
created: '2026-06-08'
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



