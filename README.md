# ECG-Image-Distortion-Removal
Performance-driven ECG image restoration framework analyzing classical processing, adversarial U-Net models, and Mixture-of-Experts architecture for generalized multi-distortion correction.

<p align="center">
  <img src="MOE_datflow_diagram.png" width="800">
</p>
![MOE_datflow diagram](https://github.com/user-attachments/assets/f8389773-f744-41af-90e5-370e72bcb5aa)

## Dataset

Full dataset is not included due to size constraints.
Sample distorted and ground-truth images are provided for demonstration purposes.


# Problem Statement

ECG paper images are commonly affected by real-world distortions:

Wrinkles (non-linear geometric deformation)

Rotation (global affine transformation)

Text artifacts (structured occlusions)

Salt & Pepper noise (impulse corruption)

These distortions degrade segmentation fidelity and structural waveform recovery.

This project benchmarks multiple restoration strategies under identical evaluation metrics.

# Approaches Implemented
1️⃣ Classical Image Processing

A deterministic morphological preprocessing pipeline:

RGB → HSV transformation

Value channel extraction

Multi-Otsu threshold segmentation

Morphological opening and closing

Binary inversion

Designed primarily for structured wrinkle distortions.

Performance (Wrinkled Images)

Dice Coefficient: 0.9699

SSIM: 0.8860

Characteristics

No training required

Low computational cost

Limited generalization capability

2️⃣ GAN-Enhanced U-Net

An encoder–decoder segmentation architecture augmented with adversarial training.

Architecture Components

Convolutional encoder–decoder backbone

Skip connections for spatial preservation

Adversarial discriminator for structural refinement

Optimized for rotation-based distortions and structural consistency recovery.

Performance (Rotated Images)

Dice Coefficient: 0.9972

SSIM: 0.9308

Characteristics

Learns spatial invariance

High segmentation precision

Requires distortion-specific training

3️⃣ Mixture-of-Experts (MoE) Model

A unified multi-expert deep learning architecture where:

Each expert network is trained on a specific distortion class

Learned expert parameters are stored independently

During inference, distortion-aware weighting enables robust segmentation

This enables a single model to generalize across heterogeneous distortion types.

Performance (Multi-Distortion Dataset)

Dice Coefficient: 0.9972

SSIM: 0.9608

Characteristics

Strong cross-distortion generalization

Higher structural similarity preservation

Increased architectural complexity
