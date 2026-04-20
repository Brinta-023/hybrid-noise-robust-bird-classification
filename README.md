# Hybrid Gaussian-Diffusion Augmentation for Noise-Robust Bird Sound Classification

## Overview

Real-world bird sound classification systems fail under noisy environmental conditions (wind, rain, traffic, etc.).
This project proposes a **hybrid augmentation strategy** combining Gaussian noise and diffusion-generated noise to improve robustness.

The model is built using the **Audio Spectrogram Transformer (AST)** and evaluated under real environmental noise conditions using the **ESC-50 dataset**.

---

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
