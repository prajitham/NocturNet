# NocturNet

**Multimodal polysomnography for respiratory-event classification with cross-signal fusion and overnight temporal context.**

NocturNet is a notebook-based research implementation of four-class sleep-related respiratory-event classification from polysomnography (PSG). The original research package includes a physiological-signal processing workflow, temporal multimodal model, internal and external evaluation studies, stored notebook outputs and **37 unaltered scientific figures**. This repository preserves the author's original research artifact and provides academic documentation for inspecting it.

> **Research materials.** This repository presents the final NocturNet implementation, study results and figures supplied for the project. The scientific notebook, configurations, outputs and figures are retained as provided.

![NocturNet model architecture](Code/figures/04_architecture.png)

*Original architecture figure supplied with the research package. [View the complete figure catalogue](docs/FIGURE_ATLAS.md).*

**Research navigation:** [Methodology](docs/METHODOLOGY.md) · [Results](docs/RESULTS.md) · [Dataset provenance](docs/DATASETS.md) · [Figure atlas](docs/FIGURE_ATLAS.md) · [Notebook cell guide](docs/NOTEBOOK_GUIDE.md) · [Setup and requirements](docs/SETUP_AND_REQUIREMENTS.md) · [Reviewer guide](docs/REVIEWER_GUIDE.md) · [Source integrity](docs/PROVENANCE.md) · [Citation](CITATION.md)

## Research question and contribution

Respiratory-event classification from PSG requires identifying physiologic patterns within each epoch while accounting for dynamics across an overnight recording. The supplied NocturNet implementation studies **native-processing-rate multimodal feature extraction, attention-based signal fusion, and temporal context modelling**. The principal classification task distinguishes **Normal, Hypopnea, Obstructive and Central** events. A supplementary variant, *NocturNet-S*, includes sleep-stage prediction. The archive further investigates cross-dataset evaluation, comparator models, robustness, event analysis and AHI-related measures.

| Implementation property | Recorded in source |
|---|---|
| Input channels | ECG, EEG, airflow, thoracic effort, abdominal effort, SpO₂ |
| Signal processing | ECG/EEG at 64 Hz; other channels at 16 Hz |
| Label interval | 30 s |
| Temporal window | 64 epochs (32 min); stride 32 |
| Core network | Modality-specific conv encoders; attention/Transformer fusion; temporal Transformer + BiGRU |
| Primary output | Four-class respiratory-event classification |
| Implementation | Original Python/PyTorch Jupyter notebook |
| Recorded seeds | 42, 43, 44 |

The notebook also explores the [OSF-Base foundation model](https://github.com/yang-ai-lab/OSF-Open-Sleep-FM) as separate model/probe context. The recorded main NocturNet instantiation uses `use_fm=False`; **the OSF backbone is not asserted to be pretrained weights for the primary classifier**. See [Methodology](docs/METHODOLOGY.md).

## Evaluation results

| Cohort | Role | Accuracy | Macro-F1 | Cohen's κ |
|---|---|---:|---:|---:|
| PhysioNet/CinC Challenge 2018 | Internal held-out evaluation | **0.8956** | **0.6984** | 0.6434 |
| UCDDB | External evaluation | 0.8396 | 0.5697 | 0.5121 |
| SLPDB | Further external evaluation | 0.6806 | 0.4717 | 0.3819 |

Values correspond to **NocturNet, seed 42**. Different cohorts, class distributions and comparator settings should not be treated as a unified benchmark. See [Results and interpretation](docs/RESULTS.md) for the multi-seed context and limitations.

| Main evaluation | Overnight agreement |
|---|---|
| ![Internal testing](Code/figures/06_eval_internal.png) | ![AHI agreement](Code/figures/10_ahi_agreement.png) |

The originally supplied package covers **200 selected Challenge-2018 records**, **25 UCDDB subjects**, and an SLPDB analysis with **18 recordings from 16 subjects**. Exact subject-split identifiers and raw PSG recordings are not included in the supplied materials. Obtain datasets from their authoritative sources: [Challenge 2018](https://physionet.org/content/challenge-2018/1.0.0/), [UCDDB](https://physionet.org/content/ucddb/1.0.0/), and [SLPDB](https://physionet.org/content/slpdb/1.0.0/). [Dataset access details](docs/DATASETS.md).

## Read the original implementation

The authoritative source is **`Code/NocturNet_FINAL.ipynb`** (29 code cells, including stored execution outputs). **The repository owner is uploading this exact notebook separately**; the other release materials are published independently. Once it appears, use [the original notebook](Code/NocturNet_FINAL.ipynb). Its expected SHA-256 is `25ee2044227e4334de7e73b963f560f381a87c8a8b1961fa27cbaaee1071f2d7`. The notebook includes setup, preprocessing, model definitions, training and evaluation routines, comparative analyses and scientific figures. Its [stage-by-stage map](docs/NOTEBOOK_GUIDE.md) is the recommended starting point.

No substitute, truncated, generated, or re-executed notebook is used. The notebook upload is the **only owner-managed source-file publication step**. See [repository completion and source integrity](docs/ARCHIVE_INTEGRITY.md).

### Getting the data and dependencies

The research notebook was developed around Google Colab and Drive-backed paths such as `MyDrive/QMLNet_v3` for a pre-existing PSG cache and `MyDrive/NocturNet` for results and model-related assets. The repository does **not** contain those caches, complete trained NocturNet checkpoints, original split files, or raw PSG data. The notebook installs certain packages dynamically and does not include a version-locked environment. The required data layout and software dependencies are described in [Setup and requirements](docs/SETUP_AND_REQUIREMENTS.md), and source-file availability is described under [Artifact access](docs/ARTIFACTS_AND_ACCESS.md).

## Research-file organization

```text
NocturNet/
├── README.md                          # Study overview and archive navigation
├── Code/
│   ├── NocturNet_FINAL.ipynb          # Exact supplied notebook
│   ├── config.json                    # Original settings and study metadata
│   ├── S1_configuration.json
│   ├── data_config.json
│   ├── training_config.json
│   ├── event_and_AHI_methods.json
│   ├── manifest.json / provenance.json
│   ├── figures/                     # 37 original scientific PNGs
│   └── fm/                           # OSF metadata (large binary artifacts external)
├── docs/
│   ├── METHODOLOGY.md
│   ├── RESULTS.md
│   ├── DATASETS.md
│   ├── SETUP_AND_REQUIREMENTS.md
│   ├── REVIEWER_GUIDE.md
│   ├── ARCHIVE_INTEGRITY.md
│   ├── FIGURE_ATLAS.md
│   ├── NOTEBOOK_GUIDE.md
│   └── PROVENANCE.md
├── CITATION.md / LICENSE_STATUS.md
└── .gitattributes
```

**Artifact distinction:** The supplied large `osf_backbone.pth` and `osf_tokens.npy` files are retained in the original private Drive ZIP, not in the ordinary GitHub tree. They are not model weights for the main NocturNet classifier. See [Artifact access](docs/ARTIFACTS_AND_ACCESS.md).

## Research scope and responsible interpretation

The reported findings concern biomedical machine-learning research, not a deployable clinical device. The respiratory-positive-epoch conversions used in some AHI analyses should not be interpreted as direct independently scored respiratory-event counts. Performance interpretation depends on cohort definition, model configuration, and the evaluation measures described in the notebook.

The supplied package does not specify an authorized project software license or complete final manuscript citation metadata. These are **not invented**: see [License status](LICENSE_STATUS.md) and [Citation guidance](CITATION.md). The repository should remain private until public distribution is authorized.

---

*NocturNet research code, study results and scientific figures are supplied as the final project materials.*

**Publication status:** All 37 original figures and the supplied text/JSON source assets are available in this repository. The unmodified notebook will be added by the owner. Two large OSF-related binary assets remain in the original privately controlled Drive archive, with [exact locations and sizes documented](docs/ARTIFACTS_AND_ACCESS.md). No Git LFS objects are claimed to have been uploaded.
