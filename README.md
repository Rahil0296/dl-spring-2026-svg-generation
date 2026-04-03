# DL Spring 2026 — Text-to-SVG Generation
**NYU Tandon | CS-GY 9223 / ECE-GY 7123 | Team: Rahil Shaikh & Shubham**

## Overview
Fine-tuned Qwen2.5-Coder-1.5B-Instruct with QLoRA to generate SVG code from natural language text prompts.

## Competition
Kaggle: DL Spring 2026 – SVG Generation from Text Prompts (Extended Deadline)  
Best public leaderboard score: **12.58802**

## Notebooks
- `colab_tfidf_baseline.ipynb` — Colab run, TF-IDF retrieval baseline, score 12.58802
- `rtx5060_qlora_training.ipynb` — Local RTX 5060 run, QLoRA fine-tune on 10k samples, score 11.76595

## Approach
- Model: Qwen/Qwen2.5-Coder-1.5B-Instruct
- Method: QLoRA fine-tuning (4-bit NF4 quantization)
- LoRA rank: 32, alpha: 64
- Training data: 50,000 (prompt, SVG) pairs from competition dataset

## Ablations
| Run | Samples | Epochs | Hardware | Score |
|-----|---------|--------|----------|-------|
| Run 1 | 5,000 | 2 | Colab A100 80GB | Model output invalid — right-padding bug |
| Run 2 (TF-IDF) | N/A | N/A | CPU | **12.58802** — best score |
| Run 3 | 10,000 | 2 | RTX 5060 8GB | 11.76595 |
| Run 4 | 20,000 | 2 | A100 40GB | Inference dtype error (BF16 vs FP16) |

## Reproducibility
Fixed random seed: 42 across all runs.

## AI Tooling Disclosure
Claude (Anthropic) was used for code scaffolding and debugging assistance.