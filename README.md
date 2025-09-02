# AdaPoinTr_UrbanTrees

Additional visuals illustrating urban tree point cloud reconstruction with **AdaPoinTr**.

*This work was conducted as part of a Master 2 internship (TELENVI: Remote Sensing and Environment).*

---

## Visual Companion

This repository provides **complementary visuals** for our study on 3D point cloud completion and denoising of urban trees using **AdaPoinTr**, a transformer-based deep learning model.  
It includes:
- A **diagram** of the model architecture  
- **3D GIFs** comparing:
  - TLS (LiDAR)  
  - SfM-MVS photogrammetry (noisy and incomplete)  
  - **AdaPoinTr completion of SfM-MVS clouds**

---

## About this Study

- **Data Acquisition:** Winter 2025 in Rennes, France (~60 urban trees, 6 species)
- **Goal:** Improve urban tree point clouds from smartphone photogrammetry to approach TLS standards (completion + denoising)
- **Methods:** AdaPoinTr completion model with two-stage fine-tuning (synthetic + TLS data)  
- **Evaluation:** Chamfer Distance, M3C2 metrics and metrics from AdQSM

---

## References

This work builds upon the following studies and codebases:  
- [PoinTr](https://github.com/yuxumin/PoinTr)  
- [TreePoinTr](https://github.com/alBrnd/treePoinTr)


---

## Architecture Overview

![Architecture](adapointr.png)

---

## Visual Results

### Example (Fraxinus excelsior): TLS vs SfM-MVS vs AdaPoinTr Completion

<div style="display: flex; align-items: flex-start; gap: 10px;">
  <div>
    <img src="gifs/TLS_FE_01.gif" width="400"/>
    <p style="text-align: center;">TLS (LiDAR)</p>
  </div>
  <div>
    <img src="gifs/Colmap_FE_01.gif" width="400"/>
    <p style="text-align: center;">SfM-MVS (Colmap)</p>
  </div>
  <div>
    <img src="gifs/Colmap_FE_01_completion.gif" width="400"/>
    <p style="text-align: center;">AdaPoinTr Completion of SfM-MVS</p>
  </div>
</div>

<div style="display: flex; align-items: flex-start; gap: 10px;">
  <div>
    <img src="gifs/GS_FE_01.gif" width="400"/>
    <p style="text-align: center;">3D Gaussian Splatting (3DGS)</p>
  </div>
  <div>
    <img src="gifs/GS_FE_01_completion.gif" width="400"/>
    <p style="text-align: center;">AdaPoinTr Completion of 3DGS</p>
  </div>
</div>

---

## Analysis
AdaPoinTr successfully reconstructs the trunks and main branches. However, fine branches at the extremities are often missing. This is because the tree is subdivided into smaller sub-point clouds during processing, and any sub-point cloud that does not contain enough points (less than 2048 in the partial input) is ignored, leading to missing details at the branch extremities.

Simpler species (e.g., European ash / Fraxinus excelsior) generally yield better results.

**Future work** could explore full-tree processing to improve structural coherence and better capture fine branches at the extremities.

> **Note:** Quantitative metrics such as Chamfer Distance, M3C2, and AdQSM (branch order and length) are not shown here, but were used to evaluate performance.

---

## About the Author

**Main Author:** Lola Bricout (CNRS - LETG Laboratory, Rennes, France)

**Contact:** lola.bricout@univ-rennes2.fr  

[![LinkedIn](https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://fr.linkedin.com/in/lola-bricout-4176ba187)
