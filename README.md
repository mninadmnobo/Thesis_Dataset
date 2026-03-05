# Thesis Dataset for Functional Web Testing

## Overview

This repository folder contains a curated benchmark dataset used in our thesis and empirical study on automated functional test generation for web applications.

The dataset is designed for reproducible experimentation across multiple real-world systems from different domains (banking, e-commerce, education, and travel). It combines:

- Runnable system environments (Docker-based where applicable)
- Structured functional specifications (`.json`)
- Human-readable functional references (`.md`)
- Ground-truth test artifacts for collaborative evaluation

This `Datasets` directory is part of a larger main repository. The instructions below are self-contained so reviewers and collaborators can work directly from this folder.

## Repository Structure

```text
Datasets/
  Ground_Truth_Reference_Tests/
  Mifos_Banking_System/
  Moodle_Learning_Management_System/
  Parabank_Demo_Banking/
  PHPTravels_Travel_Booking/
  SwagLab_Ecommerce_System/
```

## Included Systems

| System | Domain | Local Runtime | Functional Spec Files |
|---|---|---|---|
| Mifos Banking System | Core banking / microfinance | Docker Compose | `mifos.json`, `mifos.md` |
| Moodle LMS | Learning management | Docker Compose | `moodle_student.json`, `moodle_teacher.json` (+ markdown mirrors) |
| ParaBank Demo | Online banking demo | Public hosted website | `Parabank.json`, `Parabank.md` |
| PHPTravels | Travel booking | Public demo website | `PHPTravels.json`, `PHPTravels.md` |
| Swag Labs | E-commerce | Public hosted website | `SwagLab.json`, `SwagLab.md` |

## Data Format

Each system folder contains one or more structured functional description files.

- `*.json`: canonical machine-readable functional specification used by automation/multi-agent pipelines
- `*.md`: narrative functional reference for manual review, validation, and traceability

Typical JSON content includes:

- Navigation scope (reachable pages/views)
- Page-level actions and workflows
- Input validation expectations
- Success/failure behavior
- Business-flow coverage suitable for generating positive, negative, and edge test cases

## Quick Start

### 1. Clone

```bash
git clone https://github.com/mninadmnobo/Thesis_Dataset.git
cd Thesis_Dataset
```

### 2. Start runnable systems

There is no single root-level compose file. Start each system from its own folder.

Mifos:

```bash
cd Mifos_Banking_System
docker compose up -d
```

- App URL: `http://localhost:4200`
- Tenant: `default`
- Username: `mifos`
- Password: `password`

Moodle:

```bash
cd Moodle_Learning_Management_System
docker compose up -d
```

- App URL: `http://localhost:8080`
- Accounts: see `Moodle_Learning_Management_System/credentials.txt`
- Note: first build may take several minutes

### 3. Use hosted systems

- ParaBank: `https://parabank.parasoft.com/parabank/index.htm`
- PHPTravels: `https://phptravels.com/demo`
- Swag Labs: `https://www.saucedemo.com/`

## Ground Truth Collaboration Area

`Ground_Truth_Reference_Tests/` is reserved for collaborator-provided reference tests and adjudicated artifacts.

Recommended practice:

- Create one subfolder per collaborator or team
- Add one subfolder per system under test
- Include a short `notes.md` with assumptions and scope
- Keep artifacts versioned and date-stamped

Example:

```text
Ground_Truth_Reference_Tests/
  collaborator_a/
    Mifos_Banking_System/
      notes.md
      test_cases.json
      evidence/
```

## Reproducibility Notes

- Prefer Docker Desktop with current Compose plugin
- Run systems one at a time if host resources are limited
- Port conflicts may occur if multiple stacks are active simultaneously
- Moodle includes source code locally to improve offline reproducibility

## Intended Research Use

This dataset supports studies in:

- LLM/multi-agent web test generation
- Functional coverage benchmarking
- Cross-domain generalization analysis
- Error taxonomy and edge-case discovery
- Human-vs-automated test quality comparison

## Limitations

- Hosted demo systems may change over time (UI/content drift)
- Third-party availability can affect repeatability for public demos
- Credentials and seeded data may evolve between upstream releases

## Citation

If you use this dataset, please cite the corresponding thesis/paper artifact in your publication.

Suggested placeholder:

```text
Author(s). "Title." ASE Artifact / Thesis Dataset, Year.
Repository: https://github.com/mninadmnobo/Thesis_Dataset
```

## License and Upstream Components

This folder aggregates multiple systems and artifacts. Individual upstream components retain their original licenses and notices in their respective directories.
