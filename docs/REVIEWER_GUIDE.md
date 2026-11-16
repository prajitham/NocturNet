# Reviewer guide

This guide provides an efficient path through the NocturNet study and its supporting materials.

## Reading sequence

1. **Research problem and model:** [Methodology](METHODOLOGY.md) describes the four respiratory classes, six PSG channels, data representation, cross-modal fusion, and temporal context. See the [architecture figure](../Code/figures/04_architecture.png).
2. **Study cohorts:** [Datasets](DATASETS.md) identifies Challenge 2018, UCDDB and SLPDB, including study sample counts and dataset citations.
3. **Classification and overnight results:** [Results](RESULTS.md) presents the principal cohort-specific metrics, seed aggregation, and AHI-related analyses.
4. **Visual evidence:** [Figure atlas](FIGURE_ATLAS.md) indexes all 37 supplied scientific figures.
5. **Implementation:** [Notebook guide](NOTEBOOK_GUIDE.md) maps the 29 code cells to data preparation, model architecture, training, and evaluation.
6. **Environment and material requirements:** [Setup and requirements](SETUP_AND_REQUIREMENTS.md) documents the supplied files, associated dataset access requirements, and runtime paths.
7. **Scientific-file provenance:** [Provenance](PROVENANCE.md), [Source integrity](ARCHIVE_INTEGRITY.md) and the [SHA-256 ledger](SOURCE_SHA256SUMS.txt) identify source materials.

## Study interpretation

- **Prediction target:** four-class 30-second respiratory-event classification—Normal, Hypopnea, Obstructive, Central.
- **PSG channels:** ECG, EEG, airflow, thoracic effort, abdominal effort and SpO₂.
- **Model:** modality-specific feature encoding, attention-based fusion, and temporal modelling with Transformer and BiGRU components.
- **Evaluation:** held-out Challenge-2018 testing and UCDDB/SLPDB external evaluations; figures additionally address robustness, calibration, error patterns and overnight analyses.
- **Foundation-model context:** the OSF-Base exploration is separate from the primary NocturNet classifier configuration (`use_fm=False`).

## Use and attribution

The study concerns research-oriented biomedical signal analysis; it is not presented as an approved clinical diagnostic product. Data use and redistribution are subject to dataset and third-party licences. The source archive does not contain a complete manuscript citation, DOI, or explicit software licence; see [Citation](../CITATION.md) and [License status](../LICENSE_STATUS.md).
