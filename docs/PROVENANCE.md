# Source files and supplementary materials

The original research archive is organised under `Code/`. Its principal implementation is `NocturNet_FINAL.ipynb`. The study package also includes configuration exports, recorded notebook provenance, supplementary metadata and 37 PNG figures.

## Computational source

- `NocturNet_FINAL.ipynb` — source cells, execution outputs and study figures.
- `config.json`, `data_config.json` and `training_config.json` — configuration values.
- `foundation_model_config.json`, `fm/osf_tokens_records.json` — OSF-Base configuration and token-record information.
- `event_and_AHI_methods.json` — extracted AHI method definitions.
- `S1_configuration.json` — initial notebook source and stored outputs.
- `manifest.json`, `provenance.json`, `README.txt` — supplementary-file descriptions and source provenance.

The source `manifest.json` identifies the notebook by SHA-256:

`25ee2044227e4334de7e73b963f560f381a87c8a8b1961fa27cbaaee1071f2d7`

## Figures

The archive contains **37 PNG figures**. Their original filenames and corresponding topics are listed in [Figure catalogue](FIGURE_ATLAS.md).

## Foundation-model-related files

The source archive also contains `fm/osf_backbone.pth` and `fm/osf_tokens.npy`. The main NocturNet model configuration in notebook Stage 7 sets `use_fm=False`, while the notebook separately includes OSF-Base and an OSF linear-probe comparator.
