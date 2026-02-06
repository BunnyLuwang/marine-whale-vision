Evidence-Limited Whale Detection from Aerial Imagery
Overview

This project investigates the limits of whale detection from single-frame aerial imagery.
Instead of optimizing for raw detection accuracy, the focus is on understanding detectability, uncertainty, and visual evidence in realistic marine environments.

Through a sequence of experiments, the project analyzes whale detection at three levels:

Patch-level evidence detection

Bounding-box proposal and localization analysis

Full-frame CNN baseline comparison

The results show that while whales may be visually present, they are often not visually dominant in the signal space that standard computer vision models rely on.

Motivation

Aerial imagery from drones and aircraft is widely used in:

marine wildlife monitoring

conservation and population surveys

ship-strike mitigation and marine safety

However, whales are frequently:

partially submerged

visually distorted by water surface effects

surrounded by high-frequency background patterns (foam, glare, waves)

This project asks a simple but important question:

When does visual evidence actually support whale detection, and when does model confidence arise from bias instead?

Key Findings

Local visual cues are weak
Patch-level whale features are fragmented and often indistinguishable from water textures.

Bounding-box localization is unreliable
Candidate boxes are dominated by water-induced edges rather than whale anatomy, even when whales are large and centered.

Full-frame CNNs are over-confident
Image-level classifiers detect whales in ~88% of images, despite limited localized evidence.

Aggregation improves reliability but reduces recall
Conservative, evidence-driven aggregation correctly abstains in many cases where confidence would be misleading.

Project Structure
├── explore_data.ipynb              # Initial dataset inspection
├── patch_extraction.ipynb          # Patch generation and analysis
├── train_patch_cnn.ipynb           # Lightweight patch-level CNN
├── evaluate_system.ipynb           # Patch aggregation and decisions
├── bbox_analysis.ipynb             # Bounding-box proposal analysis
├── image_level_detection.ipynb     # Full-frame CNN baseline
├── baseline_data_prep.py           # Data preparation utilities
├── baseline_fullframe_cnn.py       # Full-image CNN model
├── sample_whale.png                # Example aerial image
├── README.md
└── .gitignore


Note:
Large datasets, generated patches, and virtual environments are intentionally excluded from the repository.

Dataset

The experiments use a large collection of aerial whale images.
Due to size and licensing constraints, the dataset is not included in this repository.

The code assumes a directory of aerial images and can be adapted to other marine datasets with minimal changes.

Methodology Summary
Patch-Level Analysis

Grid-based patch extraction

Candidate selection via edge density

Lightweight CNN for whale vs background

Evidence aggregation at image level

Bounding-Box Analysis

Edge-based connected component proposals

Qualitative and quantitative analysis of box quality

Demonstration of spatial fragmentation and background dominance

Full-Frame Baseline

Lightweight CNN operating on full images

Comparison against evidence-driven methods

Analysis of confidence vs visual grounding

Key Insight

High detection confidence does not imply strong visual evidence.

In marine environments, background structures often dominate the visual signal, leading standard models to appear successful while relying on spurious correlations.

Limitations and Future Work

Single-frame imagery only (no temporal aggregation)

No acoustic or thermal modalities

No bounding-box annotations

Future directions include:

temporal evidence aggregation across video frames

uncertainty-aware detection

multi-modal marine sensing