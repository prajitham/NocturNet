# Methodology and implementation

> This methodology follows the supplied `NocturNet_FINAL.ipynb` and its configuration files. Consult the notebook for complete algorithm definitions and computational details.

## Task definition

NocturNet maps polysomnographic recordings into 30-second analysis epochs and assigns one of four respiratory-event labels: **Normal, Hypopnea, Obstructive or Central**. The source maps event annotations to epoch labels and uses an overlap threshold defined by `min_overlap=5`. See notebook cells 1–4 (zero-based) for the exact data and annotation handling. The notebook also studies overnight severity proxies and an auxiliary sleep-stage prediction variant.

## Inputs and signal representation

| Modality | Processing rate | Model family |
|---|---:|---|
| ECG | 64 Hz | Fast-rate encoding |
| EEG | 64 Hz | Fast-rate encoding |
| Airflow | 16 Hz | Slow-rate encoding |
| Thoracic effort | 16 Hz | Slow-rate encoding |
| Abdominal effort | 16 Hz | Slow-rate encoding |
| SpO₂ | 16 Hz | Slow-rate encoding |

The notebook defines **64-epoch sequences** with **stride 32**—32 minutes of temporal context at 30 seconds per epoch. Note that these are *processing rates*, not claims about original clinical acquisition rates.

## Core network

![Original NocturNet architecture](../Code/figures/04_architecture.png)

The code in notebook cell 8 implements modality-specific convolutional feature encoders and attention-based multimodal aggregation, followed by a temporal model combining Transformer blocks and a bidirectional GRU. The network predicts four-class respiratory events; the auxiliary `NocturNet-S` adds sleep-stage outputs. For authoritative layer definitions, arguments and tensor behavior, inspect that unaltered source cell.

The foundation-model materials in cell 6 concern an **OSF-Base probe and optional model context**. The recorded primary NocturNet instantiation specifies `use_fm=False`; therefore the backbone/token cache must not be presented as weights for the primary four-class model.

## Training configuration captured in the archive

The supplied configuration files record a maximum 25 epochs, early-stopping patience of 6, learning rate `1e-3`, weight decay `1e-4`, focal-loss γ of 2, EMA factor 0.995, and seeds 42, 43 and 44. The primary notebook contains its own experiment dispatch and saved experiment outputs. See [Setup and requirements](SETUP_AND_REQUIREMENTS.md) for the associated data and software environment.

## Evaluation

The notebook contains internal Challenge-2018 analyses, independent UCDDB and SLPDB evaluations, model comparisons, ablations, repeat-seed analyses, channel/montage experiments, calibration, event-level examination, model interpretation, and overnight AHI-related analyses. See [Results](RESULTS.md), [Notebook guide](NOTEBOOK_GUIDE.md), and [Figure atlas](FIGURE_ATLAS.md).

## Distinction between event classification and AHI

Some notebook AHI computations convert respiratory-positive **30-second epochs** into a calibrated event-count proxy, divided by reference sleep time. These outputs should not be conflated with manually scored event onsets/durations, fully autonomous AHI measurement, or clinical diagnosis. The original definitions are preserved in `Code/event_and_AHI_methods.json` and notebook cells 16–17 and 22.
