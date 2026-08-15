# Style Injection in Diffusion Models: A Training-Free Attention-Based Approach

ECE1508G Deep Generative Models — Course Project (Summer 2026)

---

## Overview

This project implements and evaluates StyleID, a training-free diffusion-based image style transfer method. StyleID injects style information into the self-attention layers of a pretrained Stable Diffusion model while preserving the spatial structure of a content image.

We compare StyleID with an Adaptive Instance Normalization (AdaIN) baseline across twelve WikiArt style categories using quantitative metrics and qualitative examples. Additional experiments examine attention parameters, layer injection configurations, and multi-style blending.

## Setup

This project was developed and tested in Google Colab. A CUDA-enabled GPU is recommended.

Install the required packages with:

```bash
pip install -r requirements.txt
```

The notebook uses Google Drive to store datasets, checkpoints, generated images, and evaluation results. Update `PROJECT_ROOT` in the notebook if a different Google Drive directory is used.

## Usage

Run the sections in `ECE1508G.ipynb` in order:

```text
1. Environment Setup
2. Data Preparation (MS-COCO content images and WikiArt style images)
3. Core Utility Functions (image loading, DDIM inversion, and tensor-to-image conversion)
4. StyleID Core Mechanism (gamma, tau, AdaIN, and selective layer injection)
5. StyleID Batch Generation (800 content-style pairs per run)
6. AdaIN Baseline
7. Unified Evaluation (LPIPS, CFSD, FID, and ArtFID)
8. StyleID vs. AdaIN Final Comparison
9. Evaluation Framework and Additional Metrics
10. Qualitative Success/Failure Gallery
11. Gamma-Tau Joint Sensitivity Sweep
12. Layer Injection Ablation
13. Multi-Style Blending
```

The notebook prepares the content and style images, generates stylized outputs, evaluates the results, and produces the comparison tables and visualizations used in the report.

Each experimental round evaluates 800 content-style pairs. The main comparison combines three rounds, producing 2,400 outputs per method across twelve style categories.

## Project Structure

```text
ECE1508-Deep-Generative-Models-Project/
├── ECE1508G.ipynb
├── README.md
├── requirements.txt
└── seeds/
    ├── ECE1508G1.html
    ├── ECE1508G2.html
    └── ECE1508G3.html
```

`ECE1508G.ipynb` contains the complete implementation and evaluation pipeline. The files in `seeds/` are exported execution logs for the three experimental rounds used to obtain the reported results.

## Generated Outputs

The notebook creates the following directories in Google Drive during execution. They are not included in the repository because they contain generated images, checkpoints, and evaluation artifacts.

```text
outputs/
├── batch_default_params/
└── adain_baseline/

results/
└── final_evaluation/
```

Generated images are stored under `outputs/`, while metric summaries, tables, figures, and other evaluation artifacts are stored under `results/`.

## Evaluation Metrics

The project reports the following metrics:

```text
LPIPS        Perceptual content similarity
CFSD         Content-structure preservation
FID          Distributional style similarity
ArtFID       Combined content and style evaluation
Histogram    Color-distribution similarity
LPIPS-Gray   Color-independent structural similarity
KID          Small-sample distributional comparison
```

Lower values indicate better performance for all reported metrics.

Because the number of samples available for each style category is limited, the absolute FID and ArtFID values should not be compared directly with large-scale published benchmarks. These measurements are reported as supplementary results, while KID is emphasized in the main distributional comparison.

## Additional Experiments

The project includes a joint sensitivity sweep over the query-preservation weight `gamma` and attention temperature `tau`. It also evaluates different self-attention layer injection configurations and demonstrates training-free blending of multiple style references.

## Reference

> Chung, J., Hyun, S., & Heo, J.-P. (2024). Style Injection in Diffusion: A Training-free Approach for Adapting Large-scale Diffusion Models for Style Transfer. *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, 8795–8805. [arXiv:2312.09008](https://arxiv.org/abs/2312.09008)
