# Research-source integrity and completion

## Immutable origin

The owner supplied `Code (1).zip` as the final research package. This ZIP contains **54 members**. A **48-file source review package** excluded the two large OSF-related binary artifacts and four Hugging Face cache metadata/lock files, while retaining the original notebook, all 37 scientific figures, and the source JSON/text files.

The repository follows a **document-and-preserve** policy: scientific code, figures and metadata are not edited or rerun. Repository documents under `docs/` are newly authored navigation and scientific communication, not results from new experiments.

## Manual notebook upload — the only remaining owner action

Upload the original `Code/NocturNet_FINAL.ipynb` to **exactly** this path (inside `Code/`), using the original unedited notebook from `Code (1).zip` or `NocturNet_review_pack.zip`.

| Integrity property | Expected value |
|---|---|
| File | `Code/NocturNet_FINAL.ipynb` |
| Size | **15,310,268 bytes** |
| SHA-256 | `25ee2044227e4334de7e73b963f560f381a87c8a8b1961fa27cbaaee1071f2d7` |
| Original cells | 29 |
| Stored outputs | Preserved as-is |

**Do not** convert it to `.py`, clear outputs, re-save it through a different Jupyter environment, or run it for GitHub presentation. Such actions can change the source-file bytes or results.

The file hashes can be checked on any trusted machine without running the notebook:

```bash
sha256sum Code/NocturNet_FINAL.ipynb
```

For the review package's complete 48-member checksum ledger, see [SOURCE_SHA256SUMS.txt](SOURCE_SHA256SUMS.txt). That ledger includes the owner-uploaded notebook and must not be represented as an inventory of files already present on GitHub.

## Source archive versus repository

| Type | Original ZIP | GitHub disposition |
|---|---|---|
| Scientific PNG figures | 37 | All 37 published unchanged |
| Original supplementary JSON files | 9 | Published unchanged |
| Original `README.txt` | 1 | Published unchanged |
| Original notebook | 1 | Reserved for owner's manual upload |
| `osf_backbone.pth` | 1 | In original privately held Drive archive; not in GitHub tree |
| `osf_tokens.npy` | 1 | In original privately held Drive archive; not in GitHub tree |
| Hugging Face cache entries | 4 | Retained in ZIP, omitted from source-oriented GitHub archive |

These counts total 54 source members. The published documentation, such as `README.md` and files in `docs/`, is added separately and does not replace original research content.

## Referenced but not supplied

The original `Code/manifest.json` declares `S2`–`S12` supplementary JSONs and 18 structured table files that are **not** in the provided ZIP; there is no legitimate basis for fabricating their contents. Raw recordings, exact split identities, NocturNet classifier checkpoints, and prediction arrays also are not bundled. See [Setup and requirements](SETUP_AND_REQUIREMENTS.md) and [Provenance](PROVENANCE.md).

## Release integrity policy

The final project materials are presented without altering the scientific code, figures, configurations or results. Manuscript acceptance, software licensing permissions and clinical deployment status are not inferred from the supplied files.
