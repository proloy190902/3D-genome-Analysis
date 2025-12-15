# 3D-genome-Analysis
# HiC-MAFormer: Multi-Modal Transformer Framework for Cross-Cell Hi-C Resolution Enhancement
# 📌 Overview

HiC-MAFormer is a novel multi-modal transformer-based architecture designed for Hi-C contact map super-resolution. The model takes low-resolution Hi-C matrices (40×40) as input and predicts corresponding high-resolution contact maps, effectively enhancing genomic interaction patterns while preserving biological structure.

This repository currently contains Proposal / Implementation – Phase 1.

# 🧬 Key Contributions

Hybrid local + global attention tailored for Hi-C data

Adaptive dilation mechanism to capture multi-scale genomic interactions

Transformer-style feed-forward blocks with CNN-level efficiency

Robust skip connections for stable training

Designed specifically for Hi-C super-resolution tasks

# Architecture Pipeline
![Result Image](https://github.com/proloy190902/3D-genome-Analysis/blob/74e7010bea169ea275bae196d7a9ad700194359e/HiC-MAFormer.png)


# 📂 Dataset

This work uses data from the DiCARN-DNase project.

Source: OluwadareLab / DiCARN_DNase (Zenodo)

Format: Pre-processed .npz files

Task: 10 kb (LR) → 40 kb (HR) Hi-C resolution enhancement

Matrix Size: 40 × 40

Channels: Single-channel Hi-C matrices

# Data Fields

data → Low-resolution Hi-C matrices

target → High-resolution Hi-C matrices

inds → Sample indices & metadata

# 🏋️ Training Details

# Training Data

File: hicarn_10kb40kb_c40_s40_b201_nonpool_train.npz

Total samples: 42,832

Used samples: 20,000 (random subset)

Input shape: (40, 40, 1)

Batch size: 4

Training batches per epoch: 5000

# Validation Data

File: hicarn_10kb40kb_c40_s40_b201_nonpool_valid.npz

Total samples: 18,063

Used samples: 5,000 (random subset)

Validation batches: 1250

# Note: Subset sampling (20K/5K instead of full data) was used to reduce GPU memory usage and speed up training while maintaining representative data distribution.

# 🏗️ Architecture Highlights

Transformer-based global dependency modeling

CNN-based local pattern extraction

Multi-scale receptive fields via adaptive dilation

Skip connections for information preservation

# Training Progress
| Metric          | Epoch 1 | Epoch 24 | Improvement |
| --------------- | ------- | -------- | ----------- |
| Training Loss   | 0.1370  | 0.1166   | ↓ 14.9%     |
| Validation Loss | 0.1224  | 0.1146   | ↓ 6.4%      |
| Training MAE    | 0.0380  | 0.0108   | ↓ 71.6%     |
| Validation MAE  | 0.0306  | 0.0109   | ↓ 64.4%     |


# Best Performance Metrics
| Metric | Value    |
| ------ | -------- |
| PCC    | 0.6268   |
| SSIM   | 0.9308   |
| PSNR   | 21.82 dB |
| MSE    | 0.000412 |
| MAE    | 0.011257 |

