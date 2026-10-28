# Kernel Spectral Matched Filter (KSMF) for Oil Spill Detection

Python implementation of the linear matched filter detector (MFD) and the kernel spectral matched filter (KSMF) for detecting oil in hyperspectral imagery.

Part of the PhD research of **Ali Abutaleb, PhD** (George Mason University, 2023):
*Integrating Nonlinear Kernel-Based Detector Algorithms and Minimum Noise Fraction for Advanced Oil-Spill Detection with Hyperspectral Imagery.*

Portfolio: [abutaleb012.github.io](https://abutaleb012.github.io/) · Write-up: [How I found oil spills in hyperspectral imagery](https://abutaleb012.github.io/oil-spill/)

## Method

1. **Data.** A hyperspectral flight line of 26,159 × 796 pixels with 224 bands (ENVI format, read with `spectral`). A 285 × 76 pixel region of interest with a labeled oil ground truth is used for testing.
2. **Background model.** K-means clustering of the background pixels gives representative samples for the background statistics and the kernel matrix (200 centroids).
3. **Detectors.** Linear MFD (equation 7 of the reference), then KSMF (equation 27) with three kernels: Gaussian RBF, polynomial, and spectral angle.
4. **Evaluation.** Detection maps and ROC curves against the ground truth.

## Results

The notebook compares the detection maps of all four detectors side by side and plots their ROC curves. In the ROC plot, KSMF with the Gaussian RBF and polynomial kernels reaches near-complete detection at very low false-alarm rates, well above the linear matched filter. The spectral angle kernel performs worst. See the plots at the end of the notebook.

## Files

- `KSMF2_OilspillGGS998.ipynb`: the full notebook.

## Running it

The hyperspectral data is not included. Place the ENVI files in `./data/` and run the notebook top to bottom. Written for Python 3.7 with:

```
numpy  scikit-learn  spectral  matplotlib  pillow
```

## Related repositories

- [KOSP](https://github.com/Abutaleb012/KOSP): kernel orthogonal subspace projection
- [KMSD](https://github.com/Abutaleb012/KMSD): kernel matched subspace detector
- [KASD](https://github.com/Abutaleb012/KASD): kernel adaptive subspace detector
- [KSMF_2021](https://github.com/Abutaleb012/KSMF_2021): later version of this notebook

## Reference

H. Kwon and N. M. Nasrabadi, "Kernel spectral matched filter for hyperspectral imagery," *International Journal of Computer Vision*, 2007. [Link](https://link.springer.com/article/10.1007/s11263-006-6689-3)
