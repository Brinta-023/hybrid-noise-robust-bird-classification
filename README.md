# Hybrid Gaussian-Diffusion Augmentation for Noise-Robust Bird Sound Classification

## Overview

Bird sound classification systems degrade significantly under real-world noise (wind, rain, traffic), making them unreliable for ecological monitoring.

This project introduces a **hybrid augmentation pipeline** combining Gaussian noise (diversity) and diffusion-generated noise (realism) to improve robustness across varying noise levels.

Built on the **Audio Spectrogram Transformer (AST)**, the proposed method significantly improves performance under extreme noise conditions (up to +64% absolute gain at 0 dB over baseline).

## Key Contributions

* Proposed a **hybrid augmentation pipeline** combining stochastic (Gaussian) and generative (diffusion) noise
* Demonstrated improved robustness across multiple noise levels (10 dB, 5 dB, 0 dB)
* Showed that hybrid augmentation outperforms individual methods
* Analyzed the **diversity vs realism trade-off** in augmentation strategies

---

## Methodology

### Model

* Audio Spectrogram Transformer (AST)
* Fine-tuned on bird sound dataset

### Augmentation Strategies

* Baseline (no augmentation)
* Gaussian noise
* Diffusion-generated environmental noise
* Hybrid (Gaussian + Diffusion)


---
## Pipeline

Audio → Spectrogram → Augmentation (Gaussian / Diffusion / Hybrid) → AST → Classification

- Feature extraction: Log-mel spectrograms  
- Augmentation applied during training  
- Evaluation across controlled noise levels (10 dB, 5 dB, 0 dB)
---
## Implementation Details

- Modular training and evaluation pipelines  
- SLURM-based training for large-scale experiments  
- Controlled experiments across multiple noise regimes  
- Debugged normalization and training instability issues
---
## Reproducibility

- Fixed random seeds for experiments  
- Consistent preprocessing across all models  
- Same evaluation protocol for fair comparison
---
## Results

| Model     | Clean     | 10 dB     | 5 dB      | 0 dB      |
| --------- | --------- | --------- | --------- | --------- |
| Baseline  | 73.61     | 51.64     | 17.29     | 3.13      |
| Gaussian  | 75.25     | 70.22     | 68.08     | 57.52     |
| Diffusion | 73.00     | 67.70     | 67.38     | 61.59     |
| Hybrid    | **75.86** | **72.85** | **71.71** | **67.12** |

Hybrid model achieves the best performance across all noise conditions.

---

## Dataset

* Bird sound dataset (60 classes)
* ESC-50 dataset for environmental noise

---

## Project Structure

```
project-root/
│── models/
│── augmentation/
│── utils/
│── train.py
│── evaluate.py
│── requirements.txt
```

---

## How to Run

```
pip install -r requirements.txt
python train.py
python evaluate.py
```

---
