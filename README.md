<div align="center">
  <h1>PDEO: Plug-and-Play PDE Optimization for 3D Gaussian Splatting</h1>
  <h3>Toward High-Quality Rendering and Reconstruction</h3>
  
  <p>
    <b>Anonymous CVPR 2026 Submission</b><br>
    (Paper ID #38873)
  </p>
  
  <p>
    <a href="#abstract"><strong>Abstract</strong></a> |
    <a href="#method"><strong>Method</strong></a> |
    <a href="#results"><strong>Results</strong></a> |
    <a href="#citation"><strong>Citation</strong></a>
  </p>
</div>

---

### Abstract

3D Gaussian Splatting (3DGS) has revolutionized radiance field reconstruction but encounters blurring and floaters in complex scenes due to unstable optimization of small Gaussians. We attribute this to the imbalance in gradient magnitudes during optimization. 

To address this, we present **PDEO**, a novel, plug-and-play optimization framework. We theoretically derive that 3DGS optimization can be modeled as a Partial Differential Equation (PDE) and introduce a **viscous term** inspired by fluid simulation to ensure stable optimization. By employing the **Material Point Method (MPM)**, we obtain a stable numerical solution that enhances both global and local constraints. Extensive experiments confirm that PDEO achieves state-of-the-art rendering and reconstruction quality across various datasets.

---

### Teaser & Overview

<div align="center">
  <img src="fig/teaser.pdf" alt="Teaser Image" width="90%">
  <br>
  <i>Figure 1: PDEO enables stable optimization of 3D Gaussians, significantly reducing artifacts and floaters while enhancing details in both rendering and surface reconstruction.</i>
</div>

<br>

<div align="center">
  <img src="fig/pipeline.pdf" alt="Method Overview" width="80%">
  <br>
  <i>Figure 3: Overview of the proposed PDEO framework. We model 3DGS optimization as a PDE and solve it using MPM (Particle-to-Grid and Grid-to-Particle) with a viscous term.</i>
</div>

---

### Method

Our core insight is that the instability in 3DGS optimization arises because positional gradients dominate other attribute gradients when Gaussian scales are small. 

**Key Contributions:**
1.  **PDE Formulation**: We model the 3DGS optimization procedure as the discretization of a Partial Differential Equation (PDE).
2.  **Viscous Term**: Inspired by fluid dynamics, we introduce a viscous term into the PDE to suppress abrupt motion changes and stabilize the optimization process.
3.  **MPM Solver**: We employ the Material Point Method (MPM) to efficiently solve the PDE, utilizing Particle-to-Grid (P2G) and Grid-to-Particle (G2P) strategies to enforce local and global constraints.
4.  **Plug-and-Play**: PDEO can be easily integrated into existing 3DGS-based methods (e.g., MipGS, 2DGS, RaDeGS) to boost performance.

---

### Results

#### Novel View Synthesis
PDEO consistently improves PSNR, SSIM, and LPIPS across Mip-NeRF360, Tanks&Temples, and ScanNet++ datasets.

<div align="center">
  <img src="fig/nvs_comparison.pdf" alt="Novel View Synthesis Results" width="90%">
  <br>
  <i>Figure 4: Qualitative comparisons on Mip-NeRF360. PDEO significantly reduces artifacts and floaters compared to baseline methods.</i>
</div>

#### Surface Reconstruction
PDEO also excels in surface reconstruction tasks, achieving lower Chamfer Distance errors on the DTU dataset and higher F1-scores on Tanks&Temples.

<div align="center">
  <img src="fig/recon_comparison.pdf" alt="Surface Reconstruction Results" width="90%">
  <br>
  <i>Figure 5: Qualitative comparisons on Tanks&Temples for surface reconstruction. PDEO produces smoother and more accurate geometry.</i>
</div>

#### Quantitative Tables
*   **Novel View Synthesis**: Outperforms SOTA methods like SpecGS, MipGS, and 2DGS across all metrics (See Table 1 in paper).
*   **Surface Reconstruction**: RaDeGS+PDEO achieves the best F1-score on Tanks&Temples (See Table 3 in paper).

---

### Paper & Code

*   **Paper**: [Download PDF](PDEO.pdf) (CVPR 2026 Submission #38873)
*   **Code**: [GitHub Repository](https://github.com/MoYfan/PDEO) (Coming Soon)
*   **Video**: [Supplementary Video](#) (Coming Soon)

*(Note: Please upload your actual paper PDF to the repository root and name it `PDEO.pdf` so the link above works.)*

---

### Citation

If you find our work useful, please consider citing:

```bibtex
@inproceedings{anonymous2026pdeo,
  title={Plug-and-Play PDE Optimization for 3D Gaussian Splatting: Toward High-Quality Rendering and Reconstruction},
  author={Anonymous},
  booktitle={IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2026}
}
