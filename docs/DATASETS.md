# Datasets and access

No raw PSG recordings are bundled in this GitHub repository. The code references publicly hosted biomedical datasets; users must obtain data from the original maintainers and comply with the applicable access/licence terms. **Do not treat the included figure PNGs as distributable raw patient recordings.**

| Cohort | Role recorded in notebook | Recorded scope | Primary source |
|---|---|---:|---|
| PhysioNet/CinC Challenge 2018 | Internal train/validation/test experiment | 200 records; configuration 70% / 10% / 20% | [Challenge 2018 v1.0.0](https://physionet.org/content/challenge-2018/1.0.0/) |
| UCD Sleep Apnea Database (UCDDB) | External evaluation | 25 subjects | [UCDDB v1.0.0](https://physionet.org/content/ucddb/1.0.0/) |
| MIT-BIH Polysomnographic Database (SLPDB) | Additional external evaluation | 18 records / 16 subjects in saved evaluation | [SLPDB v1.0.0](https://physionet.org/content/slpdb/1.0.0/) |

**Scope caveat:** The original Challenge source is broader than the 200-record subset selected in this study. The original split-identity file is not contained in the supplied ZIP. A split ratio/seed is not a substitute for the subject assignments.

## External dataset references

- **Challenge 2018 v1.0.0** — [PhysioNet landing page](https://physionet.org/content/challenge-2018/1.0.0/) · DOI [10.13026/6phb-r450](https://doi.org/10.13026/6phb-r450).
- **UCDDB v1.0.0** — [PhysioNet landing page](https://physionet.org/content/ucddb/1.0.0/) · DOI [10.13026/C26C7D](https://doi.org/10.13026/C26C7D).
- **SLPDB v1.0.0** — [PhysioNet landing page](https://physionet.org/content/slpdb/1.0.0/) · DOI [10.13026/C23K5S](https://doi.org/10.13026/C23K5S).

Citation and licensing requirements should be verified on the source pages when reusing the data. The cited dataset records and versions reflect the recorded notebook context and linked dataset landing pages; dataset-level DOIs do not establish the software project's own publication DOI.

## Expected input layout

The notebook refers to Drive-backed storage paths resembling:

```text
MyDrive/
  QMLNet_v3/    # pre-existing raw/processed recordings and subject-split cache
  NocturNet/    # experiment figures, outputs and checkpoints
```

These are runtime paths **referenced in the original notebook**; they are not dependencies made available automatically by cloning this repository. See [Setup and requirements](SETUP_AND_REQUIREMENTS.md).
