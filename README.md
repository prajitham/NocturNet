# NocturNet

**Multimodal polysomnography for respiratory-event classification using cross-signal fusion and temporal context**

NocturNet is a PyTorch research implementation for classifying respiratory events in polysomnographic (PSG) recordings. The study represents six physiological channels at modality-specific processing rates, combines their features using attention-based fusion, and models the temporal context of respiratory events across consecutive 30-second epochs. The classification task comprises four classes: **Normal**, **Hypopnea**, **Obstructive**, and **Central**.

The supplied notebook contains the model and comparator implementations, training procedures, evaluation outputs, analyses of signal-montage configurations, overnight respiratory-event analyses, and visualisations of the experimental results.

![NocturNet architecture](Code/figures/04_architecture.png)

*Figure: NocturNet architecture (`Code/figures/04_architecture.png`).*

**Contents:** [Methodology](docs/METHODOLOGY.md) · [Results](docs/RESULTS.md) · [Datasets](docs/DATASETS.md) · [Figure catalogue](docs/FIGURE_ATLAS.md) · [Notebook guide](docs/NOTEBOOK_GUIDE.md) · [Environment and data paths](docs/SETUP_AND_REQUIREMENTS.md) · [Source files](docs/PROVENANCE.md)

## Experimental design

| Property | Specification |
|---|---|
| Physiological channels | ECG, EEG, airflow, thoracic effort, abdominal effort, SpO₂ |
| Processing rates | ECG and EEG: 64 Hz; airflow, effort signals and SpO₂: 16 Hz |
| Epoch duration | 30 seconds |
| Respiratory-event classes | Normal; Hypopnea; Obstructive; Central |
| Sequence length | 64 epochs (32 minutes) |
| Sequence stride | 32 epochs |
| Primary model | NocturNet |
| Auxiliary variant | NocturNet-S, with sleep-stage prediction |
| Random seeds recorded in the study | 42, 43, 44 |
| Study cohorts | PhysioNet/CinC Challenge 2018, UCDDB, SLPDB |

The network incorporates modality-specific convolutional encoders, attention-based signal fusion, and a temporal model with Transformer and bidirectional GRU components. The notebook additionally includes an OSF-Base representation analysis and an OSF linear-probe comparator; the primary NocturNet model is instantiated with `use_fm=False`.

The full definitions and training procedures are contained in `Code/NocturNet_FINAL.ipynb`. See [Methodology](docs/METHODOLOGY.md) for the experimental parameters specified in the notebook and configuration files.

## Results

### Respiratory-event classification

| Evaluation | Accuracy | Macro-F1 | Cohen's κ |
|---|---:|---:|---:|
| Challenge 2018 — held-out test | **0.8956** | **0.6984** | **0.6434** |
| UCDDB — external evaluation | **0.8396** | **0.5697** | **0.5121** |
| SLPDB — external evaluation | **0.6806** | **0.4717** | **0.3819** |

*NocturNet, seed 42. Values are taken from the evaluation outputs retained in the supplied notebook (Stages 11 and 18).* 

### Multi-seed analysis

| Evaluation | Mean macro-F1, seeds 42, 43 and 44 |
|---|---:|
| Challenge 2018 | 0.6880 |
| UCDDB | 0.5568 |
| SLPDB | 0.4607 |

The study includes comparator experiments, ablation studies, signal-montage evaluations, per-class analyses, and apnea–hypopnea index (AHI) agreement analyses. Their corresponding tables and figures are organised in the [Results](docs/RESULTS.md) and [Figure catalogue](docs/FIGURE_ATLAS.md).

| Internal evaluation | External evaluation |
|---|---|
| ![Held-out evaluation](Code/figures/06_eval_internal.png) | ![External evaluation](Code/figures/07_eval_external.png) |

| Model comparisons | Overnight AHI agreement |
|---|---|
| ![Model comparison](Code/figures/08_comparison.png) | ![AHI agreement](Code/figures/10_ahi_agreement.png) |

## Implementation and source materials

The principal implementation is the Jupyter notebook **`Code/NocturNet_FINAL.ipynb`**. The source archive contains 29 code cells with stored outputs. The [notebook guide](docs/NOTEBOOK_GUIDE.md) indexes the study stages, including preprocessing, architecture, model training, comparisons, and external evaluation.

The accompanying files comprise study settings (`config.json`, `data_config.json`, `training_config.json`), model context (`foundation_model_config.json`), event and AHI definitions (`event_and_AHI_methods.json`), supplementary-file metadata (`manifest.json`, `provenance.json`, `S1_configuration.json`), OSF token-record metadata, and **37 PNG figures**.

The notebook uses Drive-backed `QMLNet_v3` and `NocturNet` directories for processed PSG data and experiment outputs. The original stage code and package imports are recorded in the notebook; see [Environment and data paths](docs/SETUP_AND_REQUIREMENTS.md).

## Figures

The complete set of **37 figures** is available in [`Code/figures/`](Code/figures/) and indexed in the [Figure catalogue](docs/FIGURE_ATLAS.md). These include cohort and signal summaries, architecture, training and evaluation, comparator and ablation analyses, montage robustness, event and overnight views, embedding visualisation, saliency, and external-cohort analyses.

The figure files and original configuration files are retained without modification.
