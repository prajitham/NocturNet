# Notebook guide

## Source of truth

[`Code/NocturNet_FINAL.ipynb`](../Code/NocturNet_FINAL.ipynb) is the unchanged computational notebook supplied for publication. This guide is a reading map—not an alternative training or execution workflow.

| Notebook code cell (zero-based) | Original notebook heading / content |
|---|---|
| 0–1 | Stage 0; environment setup, imports and central configuration |
| 2 | Stage 1; event mapping, channels and epoch preparation |
| 3 | Stage 2; dataset acquisition / preprocessing |
| 4 | Stage 3; dataset assembly and subject splitting |
| 5 | Stage 4; cohort and signal exploratory figures |
| 6 | Stage 5; OSF-Base loading and feature/token context |
| 7 | Stage 6; foundation-model representation analysis |
| 8 | Stage 7; NocturNet architecture and baseline definitions |
| 9 | Stage 8; training / evaluation utilities |
| 10 | Stage 9; primary NocturNet experiment |
| 11 | Stage 10; comparison models |
| 12 | Stage 11; internal/external evaluation |
| 13 | Stage 12; model comparisons / ablation tables |
| 14 | Stage 12b; multi-seed analyses |
| 15 | Stage 12c; montage-robustness experiments |
| 16–17 | Stage 13; event and AHI analyses |
| 18 | Stage 13b; waveform, event and overnight visualizations |
| 19–20 | Stage 14; interpretability and representations |
| 21 | Stage 15; research summary and efficiency context |
| 22 | Stage 16; automatic AHI with NocturNet-S |
| 23 | Stage 17; literature context |
| 24 | Stage 18; SLPDB external evaluation |
| 25 | Stage 18b; SLPDB secondary analyses |
| 26 | Stage 19; external visualization |
| 27 | Stage 19b; external evaluation audit |
| 28 | Final results / figure archive creation |

## Original configuration and provenance files

| File | Scope |
|---|---|
| [`config.json`](../Code/config.json) | Consolidated configuration recorded from notebook |
| [`data_config.json`](../Code/data_config.json) | Dataset and split settings |
| [`training_config.json`](../Code/training_config.json) | Training parameters |
| [`foundation_model_config.json`](../Code/foundation_model_config.json) | Foundation-model metadata |
| [`S1_configuration.json`](../Code/S1_configuration.json) | Extracted source and outputs for initial cells |
| [`event_and_AHI_methods.json`](../Code/event_and_AHI_methods.json) | Extracted AHI/event method definitions |
| [`manifest.json`](../Code/manifest.json) | Original supplementary-file inventory and declared scope |
| [`provenance.json`](../Code/provenance.json) | Original export provenance |

The GitHub documentation does not modify the original configurations or regenerate their values. The notebook retains the research execution's saved outputs.
