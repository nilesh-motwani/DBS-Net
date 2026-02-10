# DBS-Net: A Pareto-Efficient Framework for Volumetric Segmentation

### *Spectrally Disentangled Subspace Learning for Resource-Constrained Clinical Environments*

---

## 🏥 Clinical Value Proposition

Volumetric segmentation in medical imaging (CT/MRI) faces a rigid **Pareto trade-off** between the necessity for global topological consistency and the prohibitive computational cost of 3D kernels. Native three-dimensional convolutions scale with **cubic complexity (O(N³))**, often forcing aggressive downsampling regimes that degrade high-frequency boundary transients.

**DBS-Net** resolves this ill-posed inverse problem by approximating the 3D manifold through **spectrally disentangled subspace learning**. It achieves state-of-the-art volumetric accuracy within a real-time inference envelope, making it uniquely suitable for intraoperative assistants and resource-constrained clinical workstations.

---

## 🔬 Core Innovations

### 1. Spectrally Disentangled Axial Attention

Standard Multi-Head Self-Attention (MHSA) incurs **quadratic complexity (O(N²))**. Our **Axial Attention Bridge** factorizes the dense correlation matrix into statistically orthogonal one-dimensional subspaces.

- **Complexity Reduction**: Reduces computational overhead to **linear complexity (O(N))**.
- **Volumetric Approximation**: Recovers z-axis continuity and eliminates *staircase artifacts* without native 3D operations.

---

### 2. Decoupled Boundary Supervision (DBS)

Traditional networks treat segmentation as a monolithic manifold. DBS-Net bifurcates the learning objective into parallel streams using morphological operators:

- **Body Stream**: Functions as a learned **low-pass filter**, prioritizing regional homogeneity and structural solidity.
- **Edge Stream**: Acts as a **high-pass filter**, explicitly attending to high-frequency boundary gradients.

---

### 3. Mathematical Orthogonality

FFT analysis and Pearson Correlation Coefficient (PCC) empirically validate that the architecture factorizes the semantic manifold into two independent subspaces:

**ρ(𝓕_body, 𝓕_edge) ≈ 0**

This confirms the theoretical orthogonality enforced by DBS-Net.

---

## 📊 Performance & Benchmarks

DBS-Net was rigorously validated on volumetric (KiTS19, BraTS2020) and 2D geometric (retinal) benchmarks.

| Metric | KiTS19 (Kidney CT) | BraTS2020 (Tumor MRI) | DRIVE (Retinal) |
|------|-------------------|----------------------|----------------|
| **Dice Similarity (DSC)** | 0.942 | 0.880 | 0.860 |
| **HD95 (mm)** | 3.85 | 5.20 | 3.15 |
| **Inference Speed** | 63.56 FPS | 51.01 FPS | 54.97 FPS |

---

### Efficiency Highlights

- **FLOPs Reduction**: 78% reduction compared to transformer-heavy architectures such as TransUNet.
- **Data Efficiency**: Surpasses fully supervised baselines using only **25% of training data**, confirming a superior inductive bias.

---

## 🩺 Clinical Reliability & Robustness

- **Volumetric Agreement**: Bland–Altman analysis demonstrates a negligible systematic bias of **−4.95 voxels**, confirming neutrality across anatomical scales.
- **Noise Resilience**: Maintains stability under Gaussian noise injection (simulating low-dose CT), consistently outperforming standard U-Net baselines.

---

## 📝 Citation

If you utilize this framework in your research, please cite the preprint:

```bibtex
@article{motwani2026dbsnet,
  title={DBS-Net: A Pareto-Efficient Framework for Volumetric Segmentation via Spectrally Disentangled Axial Attention},
  author={Motwani, Nilesh and Pradhan, Debasish},
  journal={SSRN 6106613},
  year={2026}
}
