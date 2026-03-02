## ECG-Image-Distortion-Removal
Performance-driven ECG image restoration framework analyzing classical processing, adversarial U-Net models, and Mixture-of-Experts architecture for generalized multi-distortion correction.

<p align="center">
  <img src="MOE_datflow_diagram.png" width="800">
</p>
![MOE_datflow diagram](https://github.com/user-attachments/assets/f8389773-f744-41af-90e5-370e72bcb5aa)

## Dataset

Full dataset is not included due to size constraints.
Sample distorted and ground-truth images are provided for demonstration purposes.


## Problem Statement

ECG paper images are commonly affected by real-world distortions:

Wrinkles (non-linear geometric deformation)

Rotation (global affine transformation)

Text artifacts (structured occlusions)

Salt & Pepper noise (impulse corruption)

These distortions degrade segmentation fidelity and structural waveform recovery.

This project benchmarks multiple restoration strategies under identical evaluation metrics.

## Approaches Implemented

# Classical Image Processing

The classical approach is based on a deterministic morphological preprocessing pipeline designed to restore structured ECG distortions without requiring any learning-based training. The method begins with RGB to HSV color space transformation, followed by extraction of the value channel to emphasize intensity information. Multi-Otsu thresholding is applied for segmentation, enabling separation of waveform structures from the background. Morphological opening and closing operations are then performed to remove noise artifacts and refine structural continuity, followed by binary inversion to obtain the final segmentation mask. This approach is particularly effective for structured distortions such as wrinkles, offering low computational cost and straightforward implementation. However, due to its rule-based nature, it demonstrates limited generalization across heterogeneous distortion types.

# GAN-Enhanced U-Net

The GAN-enhanced U-Net model leverages a deep encoder–decoder segmentation architecture augmented with adversarial training to improve structural realism and segmentation fidelity. The U-Net backbone consists of a convolutional encoder that captures hierarchical spatial features and a decoder that reconstructs high-resolution segmentation maps using skip connections to preserve fine-grained waveform details. An adversarial discriminator is incorporated to enforce structural consistency and encourage realistic waveform reconstruction. This architecture is particularly suited for correcting global geometric distortions such as rotation, as it learns spatial invariance and distortion-aware feature representations. While the model achieves high segmentation precision and structural recovery, it requires distortion-specific training and increased computational resources compared to classical methods.

# Mixture-of-Experts (MoE) Model

The Mixture-of-Experts (MoE) model is a unified deep learning framework designed to handle multiple distortion types within a single architecture. In this approach, each expert network is trained independently on a specific distortion class, allowing specialization in learning distortion-specific feature representations. The learned parameters of each expert are stored separately after training. During inference, a distortion-aware weighting mechanism leverages the expertise of the most relevant networks to generate the final segmentation output. This modular design enables robust generalization across heterogeneous distortion conditions while preserving structural waveform fidelity. Although the architecture introduces higher complexity and computational overhead, it provides strong cross-distortion adaptability and improved structural consistency compared to single-model approaches.
