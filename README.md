# Optimal Transport and Truncated Diffusion Experiments

This repository contains research notebooks with experiments on diffusion reconstruction, truncation, and evaluation metrics (including FID/SNR) on CIFAR-10.

## What is in this repo

The project is notebook-based (no standalone `train.py` / `truncate.py` scripts in this repository).

### Notebooks

- `optimal_transport.ipynb` - core OT/diffusion experiment notebook.
- `optimal_transport_and_metrics.ipynb` - diffusion reconstruction notebook with metric tracking.
- `truncated_ddpm_with_vae.ipynb` - truncated DDPM + VAE experiments and visualization utilities.

## Run

Start Jupyter and open any notebook from the list above:

```bash
jupyter notebook
```

Most notebooks download CIFAR-10 automatically to `./data` on first run.

## Methodology

The experiments in this repository follow a common workflow:

1. Prepare and normalize CIFAR-10 images.
2. Train/use diffusion components for forward noising and reverse reconstruction.
3. Apply truncation of the reverse process (reduced number of denoising steps).
4. In selected experiments, combine diffusion reconstruction with a VAE module.
5. Evaluate reconstruction/generation quality with metrics such as FID and SNR, and compare behavior across truncation settings.

The exact architecture and hyperparameters vary by notebook, but the core goal is the same: study the quality/speed trade-off introduced by truncated diffusion and OT-related reconstruction ideas.

### Early stopping vs Truncated Diffusion Model

`DDPM/DDIM with early stopping` and a `Truncated Diffusion Model (TDM)` are related but not identical ideas.

- Early stopping typically means cutting the reverse trajectory at an earlier step in an existing sampler.
- TDM usually implies a model/procedure explicitly designed or adapted to operate with a shortened trajectory (for example, with dedicated training/reconstruction setup for truncation).

In this repository, truncation is treated as an experimental design choice that is evaluated directly (quality vs speed), rather than only a generic inference-time early stop.

## Repository structure

```text
.
├── optimal_transport.ipynb
├── optimal_transport_and_metrics.ipynb
├── truncated_ddpm_with_vae.ipynb
└── README.md
```