# Artifacts and access

## Original research files

The authoritative source is the supplied `Code (1).zip`. Keep the internal `Code/` directory and all original filenames. This publishing overlay adds new root-level GitHub documentation; it does **not** change any file inside `Code/`.

| Artifact | Original location | GitHub handling |
|---|---|---|
| Full notebook with saved outputs | `Code/NocturNet_FINAL.ipynb` | Ordinary Git |
| Research figures (37 PNGs) | `Code/figures/` | Ordinary Git |
| Configuration and provenance JSON | `Code/*.json` | Ordinary Git |
| Foundation-model backbone | `Code/fm/osf_backbone.pth` | **Git LFS**, original bytes |
| Foundation-associated NumPy tokens | `Code/fm/osf_tokens.npy` | **Git LFS**, original bytes |
| Foundation token-record list | `Code/fm/osf_tokens_records.json` | Ordinary Git |
| Hugging Face cache metadata | `Code/fm/.cache/` | Preserve as supplied; ordinary Git |
| Existing supplementary text | `Code/README.txt` | Ordinary Git |

The 325.55 MiB `.pth` and 1.18 GiB `.npy` files exceed GitHub's standard 100 MiB single-object limit. Root-level `.gitattributes` instructs Git LFS to manage these original paths. No converted or recomputed versions are created by this overlay.

## External datasets and referenced runtime artifacts

The notebook refers to external PhysioNet datasets and historical runtime directories, including `QMLNet_v3` and `NocturNet`. Raw recordings, processed epoch stores, certain subject-split files, and training/inference runtime artifacts are not part of the supplied `Code (1).zip`. Their absence from the archive does not alter what the archived notebook reports; it determines what a new user must obtain to rerun the full workflow in the original environment.

The archive's `manifest.json` is preserved exactly, including its descriptions of supplementary exports. Its lists should be read as original metadata, not as a guarantee that every named supplementary JSON is included in this specific ZIP.

### Official dataset pages

- [PhysioNet / CinC Challenge 2018](https://physionet.org/content/challenge-2018/1.0.0/)
- [UCDDB](https://physionet.org/content/ucddb/1.0.0/)
- [MIT-BIH SLPDB](https://physionet.org/content/slpdb/1.0.0/)

## Foundation-model attribution

The notebook references the [OSF-Open-Sleep-FM repository](https://github.com/yang-ai-lab/OSF-Open-Sleep-FM) and `yang-ai-lab/OSF-Base` as recorded in its configuration. A third-party model's license and redistribution terms should be followed for the included binary weights. The main NocturNet prediction model should not be described as pretrained on OSF solely because those assets are present.

## Scope of this packaging step

No scientific code is executed, changed, corrected, reformatted, or regenerated. The packaging process only adds the README, figure links, technical guide, citation/rights notices, and Git publishing metadata.
