# Video Denoising Datasets: Real vs. Synthetic Benchmarks

A curated and comparative overview of public (and notable private) video denoising datasets, structured by acquisition realism.  
This repository supports our position paper for **VISAPP 2026** on the need for high-fidelity RAW video benchmarks with realistic motion and cross-device diversity.

> 🔗 *Full analysis, methodology critique, and a proposal for an enhanced beam-splitter acquisition pipeline are given in the paper.*

---

## Dataset Summary

| Type | Dataset (Year) | Task | Format | Resolution | # Samples | # Frames | Open Access | Links |
|------|----------------|------|--------|------------|-----------|----------|-------------|-------|
| **REAL** | **LSMOD** (2019) | Low-Light Video Enhancement | RAW | 1800×1000 | 179 | ~36k | ❌ | [Paper (ICCV)](https://openaccess.thecvf.com/content_ICCV_2019/papers/Jiang_Learning_to_See_Moving_Objects_in_the_Dark_ICCV_2019_paper.pdf) • [Code Only (GitHub)](https://github.com/MichaelHYJiang/Learning-to-See-Moving-Objects-in-the-Dark) |
|  | **CRVD** (2020) | RAW Video Denoising | RAW | 1920×1080 | 55 (11 scenes × 5 ISO) | 385 | ✅ | [GitHub](https://github.com/cao-cong/RViDeNet) • [Paper (CVPR)](https://openaccess.thecvf.com/content_CVPR_2020/papers/Yue_Supervised_Raw_Video_Denoising_With_a_Benchmark_Dataset_on_Dynamic_CVPR_2020_paper.pdf) |
|  | **Real-LLRVD** (2022) | Low-Light Enhancement | RAW | 3840×2160 (downscaled) | 210 | — | ❌ | [Paper (IEEE)](https://ieeexplore.ieee.org/document/10003653) |
|  | **ReCRVD** (2025) | RAW Video Denoising | RAW | 1920×1080 | 120 | ~1,200 | ✅ | [GitHub (RViDeformer)](https://github.com/cao-cong/RViDeformer) • [Paper (arXiv:2305.00767)](https://arxiv.org/abs/2305.00767) |
|  | **AIM 2025 Challenge** (2025) | Mobile RAW Denoising | RAW | 14 sensors (2592×1940 to 4080×3072) | 756 sequences | 7,560 | ⚠️ (registration) |  • [Paper (arXiv:2508.16830)](https://arxiv.org/abs/2508.16830) |
| **SYNTHETIC** | **MOT16** (2016) | Video Denoising (via unprocessing) | sRGB → RAW | 1920×1080 | 14 | ~11k | ✅ | [Official](https://motchallenge.net/data/MOT16/) • [Paper (arXiv:1603.00831)](https://arxiv.org/abs/1603.00831) |
|  | **DAVIS-2017** | Video Denoising (post-hoc noise) | sRGB | 720–4K | 150 sequences | ~11k | ✅ | [Official](https://davischallenge.org/) • [Paper (arXiv:1704.00675)](https://arxiv.org/abs/1704.00675) |
|  | **Vimeo-90K** (2019) | General Video Restoration | sRGB (H.264) | 448×256 | 91,701 | ~642k | ✅ | [TOFlow](http://toflow.csail.mit.edu/) • [Paper (IJCV)](http://toflow.csail.mit.edu/toflow_ijcv.pdf) |
|  | **Set8** (2019) | Video Denoising | sRGB | 960×540 | 8 | 680 | ✅ | [GitHub (DVDnet)](https://github.com/m-tassano/dvdnet) • [Paper (arXiv:1906.11890)](https://arxiv.org/abs/1906.11890) |

> ✅ — freely downloadable  
> ⚠️ — requires registration / approval  
> ❌ — not publicly released (contact authors or use via cited code)

---

## Notes on Synthetic RAW

- **RAW from sRGB?** Datasets like MOT16, DAVIS, YouTube/Vimeo are *originally sRGB*. To simulate RAW, works use *unprocessing* (e.g., Brooks et al., *Unprocessing Images for Learned Raw Denoising*, CVPR 2019). This is convenient but **does not reproduce real sensor noise statistics** (e.g., shot/read noise correlation, ISP nonlinearity). See *Noise Flow (ICCV 2019)* for discussion
- **Set8 & DAVIS** are commonly used for *evaluation only* (e.g., in VRT, DVDnet), not for training RAW models.

---

## Key Citations

```bibtex
@inproceedings{Yue2020CRVD,
  title={Supervised Raw Video Denoising with a Benchmark Dataset on Dynamic Scenes},
  author={Yue, Huanjing and Cao, Cong and Yang, Jingyu},
  booktitle={CVPR},
  year={2020}
}

@inproceedings{Jiang2019LSMOD,
  title={Learning to See Moving Objects in the Dark},
  author={Jiang, Haoyu and Liu, Chen and Wu, Boxin and Wang, Ruiqin and Yang, Jingyu and Huang, Jia-Bin},
  booktitle={ICCV},
  year={2019}
}

@article{Cao2025ReCRVD,
  title={RViDeformer: Efficient Raw Video Denoising Transformer with a Larger Benchmark Dataset},
  author={Cao, Cong and Yue, Huanjing and Liao, Lei and Yang, Jingyu},
  journal={IEEE TCSVT},
  year={2025}
}

@article{MOT16,
  title={MOT16: A Benchmark for Multi-Object Tracking},
  author={Milan, A. and Leal-Taix{\'e}, L. and Reid, I. and Roth, S. and Schindler, K.},
  journal={arXiv:1603.00831},
  year={2016}
}

@inproceedings{Perazzi2016DAVIS,
  title={A Benchmark Dataset and Evaluation Methodology for Video Object Segmentation},
  author={Perazzi, Federico and Pont-Tuset, Jordi and McWilliams, Brian and Van Gool, Luc and Gross, Markus and Sorkine-Hornung, Alexander},
  booktitle={CVPR},
  year={2016}
}

@article{Tassano2019DVDnet,
  title={DVDnet: A Fast Network for Deep Video Denoising},
  author={Tassano, Matias and Delon, Julie and Veit, Thomas},
  journal={arXiv:1906.11890},
  year={2019}
}
