# Jigsaw Image Reconstruction

A deep learning model that reconstructs a complete **96×96 RGB image from nine unordered 28×28 RGB patches**.

This project was developed as the final project for the **Deep Learning course at the University of Bologna**.

---

## Overview

The model receives nine scrambled image patches extracted from an original 96×96 image and learns to reconstruct the complete image directly.

The architecture combines:

- Convolutional patch feature extraction
- Transformer-based patch interaction
- Differentiable Sinkhorn routing
- U-Net-style image reconstruction and inpainting

The complete model is implemented in **TensorFlow/Keras** and trained end-to-end using **Mean Absolute Error (MAE)**.

---

## Problem

Each input image is divided into a 3×3 grid of 32×32 cells.

From each cell, the central **28×28 region** is extracted, producing nine patches:

```text
Original image
96 × 96 × 3
       │
       ▼
┌──────┬──────┬──────┐
│      │      │      │
│ 32²  │ 32²  │ 32²  │
├──────┼──────┼──────┤
│      │      │      │
│ 32²  │ 32²  │ 32²  │
├──────┼──────┼──────┤
│      │      │      │
│ 32²  │ 32²  │ 32²  │
└──────┴──────┴──────┘
       │
       ▼
9 × 28 × 28 × 3 patches
       │
       ▼
Randomly shuffled
