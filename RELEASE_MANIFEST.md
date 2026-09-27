# Release manifest

## Included

- user-authored Python notebook and validation utilities;
- kernel metadata and data-mount smoke tests;
- compact run/provenance receipts that contain no competition samples;
- links and checks for obtaining the original data from Kaggle.

## Excluded

- `raw/`, `processed/`, `submissions/`, `runs/`, and `logs/`;
- archive files, model weights, and generated prediction artifacts;
- virtual environments, bytecode, credentials, and machine-local settings.

## Reproducibility contract

After gaining access through the official competition page, acquire data into a
private local directory, set the paths expected by the notebook, and run the
included validation commands. Never use this public repository as evidence
that a reader is permitted to obtain, redistribute, or train on the original
competition data.
