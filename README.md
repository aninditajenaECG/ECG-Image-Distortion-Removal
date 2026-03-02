# ECG-Image-Distortion-Removal
Performance-driven ECG image restoration framework analyzing classical processing, adversarial U-Net models, and Mixture-of-Experts architecture for generalized multi-distortion correction.

#Supported Distortions

Wrinkles

Rotation

Text artifacts

Salt & Pepper noise

#Approaches Implemented
1. Classical Image Processing

Applies morphological and threshold-based preprocessing:

HSV value channel extraction

Multi-Otsu thresholding

Morphological opening & closing

Binary inversion

Best suited for structured distortions such as wrinkles.

Performance:

Dice: 0.9699

SSIM: 0.8860

2. GAN + U-Net Model

Encoder–decoder segmentation model enhanced with adversarial training.

Designed for rotation-based distortions and structured recovery.

Performance:

Dice: 0.9972

SSIM: 0.9308

3. Mixture-of-Experts (MoE) Model

Unified deep learning model trained across all distortion types.

Enables distortion-aware restoration within a single architecture.

Performance:

Dice: 0.9972

SSIM: 0.9608

#ECG-Image-Distortion-Removal/
│
├── notebooks/
│   ├── classical_processing.ipynb
│   ├── gan_unet_model.ipynb
│   ├── moe_model.ipynb
│
├── sample_images/
│   ├── distorted_examples/
│   ├── ground_truth_examples/
│
├── results/
│   ├── classical_results.png
│   ├── gan_unet_results.png
│   ├── moe_results.png
│
├── architecture/
│   ├── moe_architecture.png
│
├── requirements.txt
└── README.md

## Dataset

Full dataset is not included due to size constraints.
Sample distorted and ground-truth images are provided for demonstration purposes.
