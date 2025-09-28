# Image Denoising Efficiency

Benchmark and analysis of classical and deep-learning methods for color image denoising on the CBSD68 dataset.  
We compare **BM3D**, **Total Variation (Chambolle)**, **FFDNet**, and **DRUNet** in terms of both *denoising quality* (PSNR) and *computational cost* (operations per pixel).

---

## Project Overview
- **Goal**: Compare classical vs. deep learning denoising methods using a unified metric of efficiency (ops/pixel).
- **Dataset**: [CBSD68]([https://github.com/clausmichele/CBSD68](https://github.com/clausmichele/CBSD68-dataset/archive/refs/heads/master.zip)) (68 color natural images).
- **Noise model**: Gaussian, σ ∈ {5, 10, 25}.
- **Metrics**:
  - Peak Signal-to-Noise Ratio (PSNR)
  - Operations per pixel (ops/pixel), estimated analytically and via `ptflops`.

---

## Methods
| Method | Type | Avg. PSNR (σ=25) | Ops/pixel |
|--------|------|------------------|-----------|
| **TV (Chambolle)** | Classical | ~27 dB | ~10³ |
| **BM3D** | Classical | ~28 dB | ~8.5×10⁴ |
| **FFDNet** (IPOL) | CNN | ~30.6 dB | ~4.2×10⁵ |
| **DRUNet** (DeepInv) | CNN | ~31.0 dB | ~2.6×10⁶ |

Key trade-off: **DRUNet gives the best PSNR but at the highest computational cost.**

---

## Repository Structure
```
Image-Denoising-Efficiency/
│
├── notebooks/
│   ├── Denoisage.ipynb            # PSNR experiments
│   └── Operations_per_pixel_RN.ipynb  # Ops/pixel analysis (BM3D, TV, FFDNet, DRUNet)
│
├── report/
│   └── Rapport.pdf                # Full scientific report (in French)
│
└── README.md                      # This file
```

---

## Requirements
- Python 3.9+
- Main packages: `numpy`, `scikit-image`, `matplotlib`, `bm3d`, `ptflops`, `torch`, `deepinv`

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## Usage
1. **PSNR Experiments**
   ```bash
   jupyter notebook notebooks/Denoisage.ipynb
   ```
2. **Compute operations per pixel**
   ```bash
   jupyter notebook notebooks/Operations_per_pixel_RN.ipynb
   ```

---

## 📜 References
- [BM3D – Lebrun, 2012](https://doi.org/10.5201/ipol.2012.l-bm3d)  
- [Chambolle TV, 2013](https://doi.org/10.5201/ipol.2013.61)  
- [FFDNet – Zhang et al., 2018](https://arxiv.org/abs/1710.04026)  
- [DRUNet – DeepInverse, 2025](https://arxiv.org/abs/2505.20160)

---

## 👤 Author
Mohamed Mohamed El Bechir – [GitHub](https://github.com/medelbechir) · [LinkedIn](https://www.linkedin.com/in/mohamed-el-bechir-6958a5242/)
