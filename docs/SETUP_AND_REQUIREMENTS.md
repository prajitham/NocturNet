# Setup and material requirements

## Source notebook

The primary implementation is `Code/NocturNet_FINAL.ipynb`, a Jupyter notebook with 29 code cells and saved results. The repository owner is adding the **unaltered** notebook directly under `Code/`.

```text
Code/NocturNet_FINAL.ipynb
Size: 15,310,268 bytes
SHA-256: 25ee2044227e4334de7e73b963f560f381a87c8a8b1961fa27cbaaee1071f2d7
```

The digest is a source-file identification value; reading or checking it does not require executing the notebook.

## Software dependencies

The notebook was written for a Python environment with PyTorch, NumPy, pandas, SciPy, scikit-learn, Matplotlib, seaborn, WFDB, MNE, Einops and related utilities. Notebook cells 0–1 contain the actual imports and dynamic installation logic. No version-locked environment file was included in the supplied research materials; no guessed lockfile is provided.

## Data and workspace layout

The notebook expects Google Drive-linked paths for experiment inputs and outputs:

```text
MyDrive/
├── QMLNet_v3/      # PSG recording cache, processed samples and associated metadata
└── NocturNet/      # experiment figures, model-related assets and results
```

The raw physiological recordings and prepared data are not in this repository. Obtain the datasets through their cited sources and observe their respective access conditions; see [Datasets](DATASETS.md). The original study's exact subject-split file, primary classifier checkpoints and per-epoch prediction arrays are not included in the supplied ZIP, so they are not represented as downloadable repository files.

## Foundation-related artifacts

The supplied source ZIP also contains two large OSF-related files:

| File | Bytes | Availability |
|---|---:|---|
| `Code/fm/osf_backbone.pth` | 341,360,652 | Source ZIP in the owner's Drive |
| `Code/fm/osf_tokens.npy` | 1,262,745,728 | Source ZIP in the owner's Drive |

These are not primary NocturNet classifier checkpoints. They are not in ordinary GitHub storage or Git LFS at present. See [Artifact access](ARTIFACTS_AND_ACCESS.md).

## Notebook integrity

For a byte-identity check after manually adding the notebook:

```bash
sha256sum Code/NocturNet_FINAL.ipynb
```

For full research settings, use [Methodology](METHODOLOGY.md), the original notebook and the supplied JSON files under `Code/`.
