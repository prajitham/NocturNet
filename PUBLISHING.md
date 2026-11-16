# Publishing the unchanged NocturNet source to GitHub

This procedure starts from **the complete original `Code (1).zip`** and adds only the presentation overlay. It does not use the separate `NocturNet-Research-Release-v0.1` development project, run the research notebook, retrain models, rewrite notebooks, or regenerate figures.

## Before you start

- Have the complete original archive `Code (1).zip` on your computer (or download it from your Drive).
- Have `NocturNet-GitHub-Presentation-Overlay.zip` from this response.
- Install [Git](https://git-scm.com/downloads) and [Git LFS](https://git-lfs.com/).
- On GitHub, create an **empty** repository named `NocturNet`. Do **not** initialize it with README, `.gitignore` or a license; those are supplied here.
- Confirm the paper owners have authorized public code/assets redistribution. Until that is confirmed, use a **private** repository.

## Recommended: one-command PowerShell publication

The overlay includes `publish_nocturnet.ps1`. Open PowerShell in a folder containing the script, and supply your actual file paths and GitHub repository URL:

```powershell
.\publish_nocturnet.ps1 `
  -OriginalZip "C:\Users\YOU\Downloads\Code (1).zip" `
  -OverlayZip "C:\Users\YOU\Downloads\NocturNet-GitHub-Presentation-Overlay.zip" `
  -RepositoryUrl "https://github.com/YOUR-USERNAME/NocturNet.git" `
  -Workspace "C:\Users\YOU\Documents\NocturNet-GitHub"
```

The script refuses to reuse an existing nonempty workspace. It extracts both ZIP files into a **new publication directory**; your original ZIP is never changed. It then initializes Git, enables Git LFS, adds exactly the original source tree and presentation files, and pushes the initial commit.

GitHub authentication is handled through your locally configured Git credential manager. **Never put a personal access token inside the script or send one in chat.**

## Manual alternative

1. Extract **the entire original** `Code (1).zip` into an empty local folder. The resulting folder should contain `Code/NocturNet_FINAL.ipynb` and `Code/fm/osf_tokens.npy`.
2. Extract `NocturNet-GitHub-Presentation-Overlay.zip` into that *same* folder (so `README.md` and `Code/` sit at the same level).
3. Open a terminal in this folder and run:

```bash
git init -b main
git lfs install
git remote add origin https://github.com/YOUR-USERNAME/NocturNet.git
git add .
git commit -m "Publish original NocturNet research artifacts"
git push -u origin main
```

The two large files are tracked through the supplied `.gitattributes` rules:

```gitattributes
Code/fm/osf_backbone.pth filter=lfs diff=lfs merge=lfs -text
Code/fm/osf_tokens.npy filter=lfs diff=lfs merge=lfs -text
```

This is a **publishing requirement**, not a scientific change. GitHub rejects individual standard Git objects larger than 100 MiB; LFS stores their bytes separately and places Git pointers in the repository history. Note that Git LFS storage/bandwidth allowances depend on your account.

## After upload

Open the repository's root `README.md`. It links to the original notebook, original figures, data sources, and supporting documentation. The next optional documentation-only edit is to replace `CITATION.md` with the real authors, paper title and DOI once those details are available.

## What this process deliberately does not do

- No Python notebook execution, tests, training, or evaluation.
- No editing, splitting, renaming, or reformatting of supplied code.
- No regenerated diagrams, tables, or accuracy claims.
- No deletion or modification of `Code (1).zip`.
- No use of the previously proposed parallel development implementation.
