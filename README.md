# Video Denoising Datasets Overview

This repository provides a curated, comparative overview of **publicly available video denoising datasets**, with emphasis on acquisition methodology, realism (real vs. synthetic), format (RAW/sRGB), and suitability for training modern deep models.

> *For a detailed discussion, gap analysis, and proposed beam-splitter-based acquisition strategy, see our [position paper for VISAPP 2026].*

---

## Summary Table

| Name | Type | Format | Acquisition Method | # Scenes / Videos | Frames | Resolution | Motion | GT Method | Public? | Links |
|------|------|--------|---------------------|-------------------|--------|------------|--------|-----------|---------|-------|
| **CRVD** (2020) | Real | RAW | Stop-and-motion + frame averaging | 11 | 385 | 1920×1080 | Artificial | Mean of 200–500 frames (BM3D at ISO 25600) | ✅ | [GitHub](https://github.com/cao-cong/RViDeNet) • [Paper](https://openaccess.thecvf.com/content_CVPR_2020/papers/Yue_Supervised_Raw_Video_Denoising_With_a_Benchmark_Dataset_on_Dynamic_CVPR_2020_paper.pdf) |
| **MOT16 (synthetic variant)** | Synthetic | sRGB→RAW (unprocessing) | Poisson+Gaussian noise on unprocessed MOT16 sRGB videos | 14 | ~11k | 1920×1080 | Realistic | Unprocessing (Brooks et al. 2019) | ✅ | [MOT16](https://motchallenge.net/data/MOT16/) • [Paper](https://arxiv.org/abs/1603.00831) |
| **DAVIS-2017** | Synthetic | sRGB | Additive Gaussian / Poisson-Gaussian on clean videos | 150 | ~10.5k | up to 4K | Realistic | Original clean video | ✅ | [DAVIS](https://davischallenge.org/) • [Paper](https://arxiv.org/abs/1704.00675) |
| **Set8** | Synthetic | sRGB | Gaussian noise on high-quality videos | 8 | 680 | 960×540 | Realistic | Original clean video | ✅ | [GitHub](https://github.com/m-tassano/dvdnet) • [Paper](https://arxiv.org/abs/1906.11890) |
| **ReCRVD** (2025) | Real | RAW | **Screen recapture** at low/high ISO | 120 | >12k | 1920×1080 (from 4K) | Realistic | Paired low-ISO (clean) / high-ISO (noisy) | ✅ | [GitHub](https://github.com/cao-cong/RViDeformer) • [Baidu](https://pan.baidu.com/s/1...) (key: `ogyw`) |
| **AIM 2025 RAW Video Challenge** | Real | RAW | Stop-motion on linear rail + burst averaging (200/500 frames) | 6 scenes × 14 sensors = 84 conditions | 7,560 | Sensor-dependent | Controlled | Frame averaging (high SNR reference) | ✅ (upon registration) | [Challenge](https://www.aim-2025.org) • [Paper (arXiv)](https://arxiv.org/abs/2508.16830) |
| **Real-LLRVD** (2023, unreleased) | Real | RAW | Screen recapture (calibrated) | 70 scenes | — | 9504×6336 (downscaled) | Realistic | Low-ISO ↔ high-ISO pairs | ❌ (contact authors) | *Private* • [Contact](mailto:bit-isp@bit.edu.cn) |
| **Vimeo-90K** | Synthetic | sRGB (H.264) | Gaussian + salt-and-pepper noise | 91,701 clips | 641,907 | 448×256 | Realistic | Original video | ✅ | [TOFlow](http://toflow.csail.mit.edu/) • [Paper](http://toflow.csail.mit.edu/toflow_ijcv.pdf) |
| **Learning to See in the Dark (Moving)** | Real | RAW | **Beam splitter**, coaxial optics | 179 | 35.8k | 1800×1000 | Realistic | Paired: with/without ND filter | ❌ (unreleased) | *Private* • [GitHub (code only)](https://github.com/MichaelHYJiang/Learning-to-See-Moving-Objects-in-the-Dark) • [Paper](https://openaccess.thecvf.com/content_ICCV_2019/papers/Jiang_Learning_to_See_Moving_Objects_in_the_Dark_ICCV_2019_paper.pdf) |

---

## 🔗 Key Resources

- **Codebases using these datasets**:  
  - [RViDeNet](https://github.com/cao-cong/RViDeNet) (CRVD, ReCRVD)  
  - [DVDnet](https://github.com/m-tassano/dvdnet) (Set8, DAVIS-test)  
  - [RViDeformer](https://github.com/cao-cong/RViDeformer) (ReCRVD)

- **Survey & Analysis Papers**:  
  - Yue et al., *Supervised Raw Video Denoising*, CVPR 2020  
  - Cao et al., *RViDeformer*, TCSVT 2025  
  - Jiang et al., *Learning to See Moving Objects in the Dark*, ICCV 2019  

---

## Notes

- ✅ **“Public”** means data can be downloaded *without explicit approval* (may require registration or Baidu links).  
- **RAW ≠ sRGB**: Simulating realistic sensor noise (e.g., shot/read noise) on sRGB data is **physically invalid** — see *Noise Flow (ICCV 2019)*.  
- **Screen recapture** (ReCRVD, Real-LLRVD) has been shown to preserve sensor noise statistics and avoid moiré (via aperture tuning) — see [arXiv:2305.00767](https://arxiv.org/abs/2305.00767).  
- **Beam splitter** setups enable *true simultaneous* capture but attenuate light — better suited for *low-light enhancement* than general denoising.

---

## Contact

For updates, corrections, or suggestions — feel free to open an issue or PR.  
Dataset access issues? Reach out to original authors (emails often in paper PDFs).

*Curated for reproducibility & research transparency — Sofia Dorogova, 2025.*
