PRISM Anonymous Reproducibility Repository
This repository contains the implementation and supporting files for PRISM, a framework for preference-efficient personalized image aesthetic assessment with calibrated cohort mixtures. The package is organized for anonymous academic review and provides the source code, configuration files, data-processing utilities, evaluation components, documentation, and validation tools required to inspect and run the computational workflow.
Repository Contents
Path	Contents
prism/	Core Python package for the PRISM workflow
prism/models/	PRISM architecture, backbone interface, component modules, and monotonic mapping layers
prism/data/	Dataset schemas, input and output utilities, duplicate handling, episode construction, split management, and PyTorch dataset classes
prism/utils/	Reproducibility and utility functions
configs/	Model, dataset, baseline, ablation, concept, optimization, acquisition, calibration, and evaluation configurations
scripts/	Command-line programs for data preparation, split construction, feature extraction, training, calibration, inference, evaluation, ablation analysis, efficiency analysis, and artifact generation
schemas/	JSON schemas defining interaction and prediction file formats
splits/	Split protocol definitions and documentation for generated split manifests
tests/	Unit checks for acquisition, calibration, metrics, provenance, statistics, and data splits
docs/	Reviewer guidance, data-layout instructions, baseline protocols, anonymization checks, provenance notes, and workflow documentation
reference_outputs/	Reference files used by the table and figure generation utilities
logs/	Package-validation and workflow-check records


Core Package Modules
The prism package contains the following components:
- models/prism.py defines the main PRISM model.
- models/components.py contains reusable neural-network components.
- models/backbone.py provides the interface to the pretrained vision-language backbone.
- models/monotonic.py contains monotonic score-mapping utilities.
- acquisition.py implements support-item acquisition strategies.
- calibration.py provides calibration procedures for model outputs and predictive intervals.
- losses.py defines the training objectives used by the framework.
- metrics.py contains evaluation metrics for personalized aesthetic assessment.
- statistics.py provides statistical comparison and uncertainty-estimation utilities.
- baselines.py contains baseline-model interfaces and implementations.
- benchmark.py supports efficiency and runtime measurement.
- audit.py provides concept-level and package-level audit utilities.
- engine.py contains shared training and evaluation routines.
- config.py loads and validates experiment configurations.
- provenance.py records and checks artifact provenance metadata.
- cli.py provides the package command-line interface.
Configuration Files
The configs directory includes:
- base.yaml for shared model, training, acquisition, calibration, and evaluation settings.
- para.yaml, flickr_aes.yaml, and lapis.yaml for dataset-specific settings.
- baselines.yaml for baseline definitions.
- ablation.yaml for component-removal configurations.
- concepts.yaml for the prespecified aesthetic concept vocabulary and source-variable mappings.
- prism_bm.yaml for the capacity-matched PRISM configuration.
Workflow Scripts
The scripts directory includes programs for:
- validating and preparing dataset records;
- constructing duplicate-controlled and user-disjoint splits;
- creating episodic training shards;
- extracting backbone features;
- training ensemble members;
- fitting calibration parameters;
- running inference and computing evaluation summaries;
- executing baseline, ablation, fixed-query, concept-audit, and efficiency workflows;
- generating manuscript tables and figures from compatible run artifacts;
- checking target-file structure and release completeness;
- validating package integrity and anonymization;
- cleaning generated files.
The top-level run_reproduction.sh script coordinates the dataset-specific workflow, while validate_package.sh runs the package checks. The Makefile provides shortcuts for common validation tasks.
Data Interfaces
The package provides adapters and schemas for PARA, FLICKR-AES, and LAPIS. Prepared data are represented through image, user, interaction, attribute-mapping, manifest, and split files. The data utilities include identifier validation, score-range checks, missing-value handling, cryptographic hashes, perceptual hashes, duplicate-group constraints, and partition-integrity checks.

Public datasets, image files, personal variables, and pretrained model weights are not redistributed in this repository. They must be obtained from their original providers and arranged according to docs/DATA_LAYOUT.md.
Documentation
The docs directory contains:
- AI_EXECUTION_GUIDE.md for the end-to-end execution sequence;
- REVIEWER_GUIDE.md for package inspection and workflow verification;
- DATA_LAYOUT.md for dataset organization and prepared-file contracts;
- BASELINE_PROTOCOL.md for baseline implementation requirements;
- RESULT_PROVENANCE.md for artifact provenance conventions;
- ANONYMIZATION_CHECKLIST.md for anonymous-release checks.
Additional README files describe the split directory, validation logs, and reference-output organization.
Environment and Packaging
The repository includes:
- environment.yml for creating the Conda environment;
- requirements.txt for Python dependency installation;
- pyproject.toml for package metadata, dependencies, command-line registration, and test configuration;
- .gitignore for generated and local-only files;
- MANIFEST.sha256 for package file-integrity verification;
- LICENSE containing the BSD 3-Clause license.
The Python package is registered as prism-piaa and exposes the prism command-line entry point.
