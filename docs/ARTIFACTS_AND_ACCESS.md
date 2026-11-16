# Research artifacts and access

## Supplied research package

The Drive file `Code (1).zip` is the supplied project package. Its 54 members include the research notebook, 37 PNG figures, recorded configuration/metadata exports, two large foundation-related binary assets and small Hugging Face cache entries. Its contents are retained without scientific changes.

## GitHub inclusion and exclusions

| File category | GitHub availability | Notes |
|---|---|---|
| `Code/NocturNet_FINAL.ipynb` | **Owner will upload separately** | Expected SHA-256 in [integrity note](ARCHIVE_INTEGRITY.md) |
| `Code/figures/*.png` | 37 original files | Original image bytes, unchanged |
| Original JSON and `Code/README.txt` | Included | Original metadata and supplementary-file declarations unchanged |
| `Code/fm/osf_tokens_records.json` | Included | Token record mapping only; not the token tensor |
| `Code/fm/osf_backbone.pth` | **Not in GitHub repository** | 341,360,652 bytes; remains in owner's original private Drive ZIP |
| `Code/fm/osf_tokens.npy` | **Not in GitHub repository** | 1,262,745,728 bytes; remains in owner's original private Drive ZIP |
| Hugging Face `.cache/` metadata | Not in GitHub repository | Download/cache support files, not research implementation |
| Trained primary NocturNet checkpoints, exact subject split, raw PSG arrays, prediction arrays | Not in source ZIP | These were referenced in the notebook but not included in the supplied artifact |

The `.gitattributes` file documents intended Git LFS tracking if the rights-holders later authorize the two large files' transfer. **Git LFS tracking patterns do not mean LFS objects have been uploaded.** We do not commit nonfunctional placeholder LFS pointer files.

**Drive archive reference (access is controlled by the owner's Drive sharing settings):** [Code (1).zip](https://drive.google.com/file/d/1zFHIELjF0NXtF0Xxe8OsGoN6HrIsZbxD/view). This link is not a guarantee of access for third-party readers or a licence to redistribute the binary contents.

## Methodological distinction

The backbone and token array support the notebook's OSF-Base foundation-model exploration. The primary NocturNet model is instantiated with `use_fm=False`; those assets are **not claimed to be a trained checkpoint for the primary classifier**. See [Methodology](METHODOLOGY.md).

## Source manifest note

The original `Code/manifest.json` lists stage files (`S2`–`S12`) and structured table exports which are not in the 54-member supplied ZIP. The original metadata is preserved unmodified; see [Provenance](PROVENANCE.md).

## Public reuse

The repository is intentionally **private** pending confirmation of the project licence, authorship/publication metadata and applicable rights to redistribute original work and third-party assets. Source datasets remain subject to their own access terms: [Datasets](DATASETS.md). No clinical diagnostic claim is made.
