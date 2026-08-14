# ECE1508-Deep-Generative-Models-Project

This project implements and evaluates StyleID-based image style transfer. It compares StyleID with an AdaIN baseline using quantitative metrics and qualitative visual examples.

## Setup

This project was developed and tested in Google Colab.

Install the required packages in the notebook:

```bash
pip install -r requirements.txt
```

## Usage

Run the notebook sections in order:

```text
1. Environment Setup
2. Data Preparation (MS-COCO content images + WikiArt style images)
3. Core Utility Functions (image loading, DDIM inversion, tensor-to-image conversion)
4. StyleID Core Mechanism (gamma, tau, AdaIN, selective layer injection)
5. StyleID Batch Generation (800 combos, default params)
6. AdaIN Baseline
7. Unified Evaluation (LPIPS, CFSD, FID, ArtFID)
8. StyleID vs AdaIN Final Comparison
9. Evaluation Framework and Additional Metrics
10. Qualitative Success/Failure Gallery
11. Gamma-Tau Joint Sweep
12. Layer Injection Ablation
13. Multi-Style Blending
```

The notebook prepares MS-COCO content images and WikiArt style images, generates stylized outputs, evaluates the generated images, and creates comparison tables and galleries.

## Project Structure

```text
.
├── requirements.txt
├── README.md
├── outputs/
│   ├── batch_default_params/
│   └── adain_baseline/
└── results/
    └── final_evaluation/
```

## Outputs

Generated images are saved in:

```text
outputs/
```

Evaluation results are saved in:

```text
results/
```

Important folders include:

```text
outputs/batch_default_params/
outputs/adain_baseline/
results/final_evaluation/
```

## Evaluation Metrics

The project reports the following metrics:

```text
LPIPS        Perceptual content similarity
CFSD         Structural preservation
FID          Style distribution similarity
ArtFID       Combined content and style quality
Histogram    Color transfer quality
LPIPS-Gray   Color-independent structure comparison
KID          Small-sample cross-check for FID
```

