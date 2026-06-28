# MAKSEA: Makkoran Coast Vessel Segmentation Dataset

**Paper:** [MVSegNet: A Multi-Scale Attention-Based Segmentation Algorithm for Small and Overlapping Maritime Vessels](https://www.mdpi.com/1999-4893/19/1/23)
*Algorithms, MDPI, 2026 — Vol. 19, Issue 1, Article 23*

**Authors:** Zobeir Raisi, Valimohammad Nazarzehi Had, Rasoul Damani, Esmaeil Sarani

---

## Overview

MAKSEA is a satellite imagery dataset collected from the **Makkoran Coast** for the segmentation of small and densely distributed maritime vessels. Existing benchmark datasets do not adequately represent the challenges of overlapping and small-scale ships in real-world maritime traffic scenarios. MAKSEA was created to address this gap and serve as a challenging benchmark for instance segmentation research.

## Dataset

| Split | Images | Labels | Annotations (VOC XML) |
|-------|--------|--------|----------------------|
| All   | 8,438  | 8,438  | 2,034                |

- **Image size:** 512 × 512 pixels, 3-band GeoTIFF
- **Projection:** EPSG:3857 (WGS 84 / Pseudo-Mercator)
- **Label format:** Binary mask GeoTIFF (per-pixel segmentation)
- **Annotation format:** Pascal VOC XML with georeferenced bounding boxes

## File Structure

```
ship_manual_all/
├── images/          # GeoTIFF satellite image tiles
├── labels/          # Binary segmentation mask tiles (GeoTIFF)
└── annotations/     # Pascal VOC bounding box annotations (XML)
```

## Download

The full dataset (~5.9 GB) is available on Zenodo:

> **[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21002461.svg)](https://doi.org/10.5281/zenodo.21002461)**

## MVSegNet

We propose **MVSegNet**, a UNet++-based segmentation architecture augmented with three modules:

1. **Multi-Scale Context Aggregation** — Atrous Spatial Pyramid Pooling (ASPP) to handle vessels at varying scales
2. **Attention-Guided Skip Connections** — focuses features on ship-relevant regions
3. **Multi-Head Self-Attention Block** — models long-range spatial dependencies before the final prediction layer

### Results

| Dataset     | Metric   | Score  |
|-------------|----------|--------|
| LEVIR_SHIP  | F1-Score | 0.9028 |
| DIOR_SHIP   | F1-Score | 0.9607 |
| MAKSEA      | IoU      | 0.826  |

MVSegNet improves the UNet++ baseline by **~7.0% IoU** on MAKSEA.

## Citation

If you use MAKSEA or MVSegNet in your research, please cite:

```bibtex
@article{raisi2026mvsegnet,
  title     = {MVSegNet: A Multi-Scale Attention-Based Segmentation Algorithm for Small and Overlapping Maritime Vessels},
  author    = {Raisi, Zobeir and Nazarzehi Had, Valimohammad and Damani, Rasoul and Sarani, Esmaeil},
  journal   = {Algorithms},
  volume    = {19},
  number    = {1},
  pages     = {23},
  year      = {2026},
  publisher = {MDPI},
  doi       = {10.3390/a19010023}
}
```

## License

Please refer to the paper for dataset usage terms.
