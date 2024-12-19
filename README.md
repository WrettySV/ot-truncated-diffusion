# **Optimal Transport-Based Truncation for Diffusion Models**

This repository introduces an **Optimal Transport (OT)**-based truncation procedure to accelerate **Denoising Diffusion Probabilistic Models (DDPMs)**. Truncation methods, commonly used in generative models like GANs and VAEs, balance sample quality and diversity. This project applies OT tools to control the DDPM sampling process and evaluates its effectiveness against traditional truncation approaches.

---

## **Key Features**

1. **OT-Based Truncation**:
   - Implements a novel OT-based approach to truncate the sampling process in DDPMs.
   - Uses Neural Optimal Transport (Neural OT) to map and truncate latent distributions efficiently.

2. **Comparison with GANs and VAEs**:
   - Evaluates truncation techniques used in GANs and VAEs and compares their performance with OT-based truncation in diffusion models.

3. **Performance Evaluation**:
   - Benchmarks the results using metrics such as:
     - **FID (Fréchet Inception Distance)** for image quality.
     - **SSIM (Structural Similarity Index)** for perceptual quality.
     - **PSNR (Peak Signal-to-Noise Ratio)** for reconstruction fidelity.

4. **Acceleration of DDPMs**:
   - Introduces truncation guided by **Signal-to-Noise Ratio (SNR)** for optimal stopping, improving computational efficiency.

---

## **Installation**

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/ot-ddpm-truncation.git
   cd ot-ddpm-truncation
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Download the CIFAR-10 dataset (done automatically during training).

---

## **Usage**

### **Train the Models**
Train the Neural OT and Diffusion models:
```bash
python train.py --epochs 10 --batch_size 32
```

### **Apply OT-Based Truncation**
Run the OT-based truncation procedure:
```bash
python truncate.py --method ot --samples 100
```

### **Visualize Results**
Visualize generated samples and truncation effects:
```bash
python visualize.py --output_dir results/
```

---

## **Methodology**

1. **Truncation via Optimal Transport**:
   - Neural OT aligns latent distributions during sampling, ensuring high-quality and diverse outputs.

2. **Signal-to-Noise Ratio (SNR) for Optimal Stopping**:
   - Sampling is truncated at the timestep \(t^*\) when SNR meets a predefined threshold:
     \[
     \text{SNR}(t) = \frac{\alpha_t}{1 - \alpha_t}
     \]

3. **Comparison with GANs and VAEs**:
   - Benchmarks the OT-based truncation against GANs' truncation via latent clipping and VAEs' sampling control.

---

## **Results**

- OT-based truncation significantly improves DDPM sampling efficiency while maintaining high image quality.
- Comparative evaluation shows OT outperforms traditional methods in balancing sample diversity and fidelity.
- Example visualization:
  ![Generated Samples](path_to_sample_image.png)

---

## **Repository Structure**

```
├── data/                  # Dataset storage
├── models/                # Neural OT and Diffusion model architectures
├── results/               # Generated samples and evaluation metrics
├── train.py               # Training script
├── truncate.py            # Truncation and sampling script
├── visualize.py           # Visualization tools
└── README.md              # Project description
```

---

## **Future Work**
- Extend OT-based truncation to other datasets (e.g., ImageNet).
- Explore adaptive thresholds for SNR-based stopping.
- Integrate advanced diffusion models (e.g., DDIM, Latent Diffusion).