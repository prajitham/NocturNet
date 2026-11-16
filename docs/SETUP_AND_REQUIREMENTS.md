# Environment and data paths

The computational workflow is contained in `Code/NocturNet_FINAL.ipynb`. The following information is recorded in notebook Stages 0–3 and the supplied configuration files.

## Python packages

Notebook cells 0–1 import Python and scientific-computing packages including:

- PyTorch; NumPy; pandas; SciPy; scikit-learn;
- Matplotlib; seaborn; MNE; WFDB; Einops;
- Hugging Face Hub utilities.

The opening notebook cell attempts installation of `wfdb`, `mne`, `seaborn`, `einops` and `huggingface_hub` when an import is unavailable. The exact imports and installation statements are retained in the notebook source.

## Runtime directories

Notebook Stage 0 assigns:

```python
DATA_BASE = os.path.join(ROOT, "QMLNet_v3")
BASE = os.path.join(ROOT, "NocturNet")
```

In Google Colab, `ROOT` is defined as `/content/drive/MyDrive`. The notebook identifies `QMLNet_v3` as the data-cache location and `NocturNet` as the location for figures, checkpoints, results and stage flags. It also defines a temporary raw-data directory.

## Configuration files

| File | Recorded content |
|---|---|
| [`config.json`](../Code/config.json) | Shared study configuration |
| [`data_config.json`](../Code/data_config.json) | Challenge-2018 sampling and split settings |
| [`training_config.json`](../Code/training_config.json) | Training parameters |
| [`foundation_model_config.json`](../Code/foundation_model_config.json) | OSF-Base repository and model settings |
| [`event_and_AHI_methods.json`](../Code/event_and_AHI_methods.json) | Extracted event and AHI method definitions |

The notebook source contains the download, preprocessing, training and evaluation implementations. It also references intermediate data, checkpoint and prediction files produced or accessed in its runtime directories; those filenames and paths are specified by the corresponding notebook stages.
