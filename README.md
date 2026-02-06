# Marine Whale Vision
## Evidence-Limited Whale Detection from Aerial Imagery

---

## Project Summary

This project studies the limitations of whale detection from single-frame aerial imagery under realistic marine conditions.  
Rather than optimizing for raw detection accuracy, the focus is on understanding visual evidence, uncertainty, and detectability limits in water-dominated environments.

The project analyzes whale detection across three spatial levels:
- Patch-level (local evidence)
- Bounding-box-level (spatial localization)
- Image-level (global context)

---

## Research Question

When does visual evidence genuinely support whale detection, and when does model confidence arise from background bias?

---

## Key Findings

- Local whale cues are weak and fragmented due to partial submergence and surface distortion.
- Bounding-box proposals are dominated by water surface structures such as foam, glare, and wave patterns.
- Full-frame CNN classifiers achieve high apparent detection rates despite limited localized evidence.
- Aggregation of weak signals improves reliability but substantially reduces recall.

---

## Experimental Components

### Patch-Level Evidence Analysis
- Grid-based patch extraction
- Edge-density–based candidate selection
- Lightweight CNN for whale vs background patches
- Image-level aggregation of patch evidence

Relevant notebooks:
- `patch_extraction.ipynb`
- `train_patch_cnn.ipynb`
- `evaluate_system.ipynb`

---

### Bounding-Box Proposal Analysis
- Edge-based connected component proposals
- Qualitative and quantitative analysis of candidate boxes
- Assessment of spatial fragmentation and background dominance

Relevant notebook:
- `bbox_analysis.ipynb`

---

### Full-Frame CNN Baseline
- Lightweight CNN operating on full images
- Comparison against evidence-driven approaches
- Analysis of confidence versus visual grounding

Relevant notebook:
- `image_level_detection.ipynb`

---


---

## Dataset

The experiments use a collection of aerial whale images.  
Due to size and licensing constraints, the dataset is not included in this repository.

All experiments assume access to a directory containing aerial whale imagery.

---

## Limitations

- Single-frame imagery only; no temporal aggregation
- No acoustic or thermal modalities
- No bounding-box annotations
- Emphasis on analysis rather than detector optimization

---

## Future Work

- Temporal aggregation across video sequences
- Uncertainty-aware detection strategies
- Multi-modal sensing for marine monitoring
- Weakly supervised localization methods

---

## Key Insight

High detection confidence does not imply strong visual evidence.  
In marine environments, background structures often dominate the visual signal, leading to overconfident predictions that are weakly grounded.


