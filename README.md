
<h1 align="center">Strips as Tokens: Artist Mesh Generation<br>with Native UV Segmentation</h1>

<p align="center"><b>ACM Transactions on Graphics (SIGGRAPH 2026)</b></p>

<p align="center">
  <a href="https://ruixu.me/">Rui Xu</a><sup>1,2*</sup>&nbsp;
  Dafei Qin<sup>1,2*</sup>&nbsp;
  Kaichun Qiao<sup>3,2</sup>&nbsp;
  <a href="https://qiujiedong.github.io/">Qiujie Dong</a><sup>4</sup>&nbsp;
  Huaijin Pi<sup>1</sup>&nbsp;
  Qixuan Zhang<sup>3,2</sup>&nbsp;
  Longwen Zhang<sup>3,2</sup><br>
  Lan Xu<sup>3†</sup>&nbsp;
  Jingyi Yu<sup>3</sup>&nbsp;
  <a href="https://engineering.tamu.edu/cse/profiles/Wang-Wenping.html">Wenping Wang</a><sup>5</sup>&nbsp;
  <a href="https://www.cs.hku.hk/index.php/people/academic-staff/taku">Taku Komura</a><sup>1†</sup>
</p>

<p align="center">
  <sup>1</sup>The University of Hong Kong&nbsp;&nbsp;
  <sup>2</sup>Deemos Technology Co., Ltd.&nbsp;&nbsp;
  <sup>3</sup>ShanghaiTech University&nbsp;&nbsp;
  <sup>4</sup>Shandong University&nbsp;&nbsp;
  <sup>5</sup>Texas A&M University<br>
  <sub>(* Equal contribution. † Corresponding authors.)</sub>
</p>

<p align="center">
  <a href="#">
    <img src="https://img.shields.io/badge/Paper-PDF-red?logo=adobeacrobatreader" alt="Paper">
  </a>&nbsp;
  <a href="#">
    <img src="https://img.shields.io/badge/Project-Page-blue?logo=googlechrome" alt="Project Page">
  </a>&nbsp;
  <a href="#">
    <img src="https://img.shields.io/badge/Code-GitHub-black?logo=github" alt="Code">
  </a>
</p>

<p align="center">
  <img src="https://xrvitd.github.io/images/video2.gif" width="100%" alt="SATO teaser">
</p>

**Strips as Tokens (SATO)** enables unified, high-quality artist mesh generation with native UV segmentation. Our strip-based tokenizer supports both triangle and quad meshes without retraining and automatically segments UV charts during autoregressive generation.

---

## Abstract

Recent advancements in autoregressive transformers have demonstrated remarkable potential for generating artist-quality meshes. However, the token ordering strategies employed by existing methods typically fail to meet professional artist standards, where coordinate-based sorting yields inefficiently long sequences, and patch-based heuristics disrupt the continuous edge flow and structural regularity essential for high-quality modeling. To address these limitations, we propose **Strips as Tokens (SATO)**, a novel framework with a token ordering strategy inspired by triangle strips. By constructing the sequence as a connected chain of faces that explicitly encodes UV boundaries, our method naturally preserves the organized edge flow and semantic layout characteristic of artist-created meshes. A key advantage of this formulation is its unified representation, enabling the same token sequence to be decoded into either a triangle or quadrilateral mesh. This flexibility facilitates joint training on both data types: large-scale triangle data provides fundamental structural priors, while high-quality quad data enhances the geometric regularity of the outputs. Extensive experiments demonstrate that SATO consistently outperforms prior methods in terms of geometric quality, structural coherence, and UV segmentation.

## Method

<p align="center">
  <img src="https://xrvitd.github.io/images/pipeline.gif" width="100%" alt="SATO pipeline">
</p>

**The Pipeline of SATO.** SATO uses a strip-based tokenizer to encode/decode both triangle and quad meshes as a unified discrete sequence. Conditioned on an input point cloud, a learnable point-cloud encoder cross-attends to the core Hourglass Transformer, which autoregressively generates token sequences that are decoded into triangle or quad meshes with native UV segmentation.

Given a set of 3D points as conditioning input, our goal is to generate an artist-style mesh with organized UV segmentation. Our core contribution includes a serialization scheme that embeds macro-structural semantic cues like UV island boundaries into the token stream, and a stride-aware decoding protocol that allows the same model to generate both triangle and quadrilateral meshes.

## Mesh Gallery

<p align="center">
  <img src="https://xrvitd.github.io/images/gallery111.gif" width="100%" alt="Mesh Gallery">
</p>

Generation results of SATO across diverse shapes, demonstrating strong generative diversity in both mesh geometry and UV segmentation. From bottom to top, it shows triangular mesh generation, shape generation with UV segmentation, and quadrilateral mesh generation. SATO supports all three tasks within a single framework and achieves compelling results on each of them.

## UV Segmentation Gallery

<p align="center">
  <img src="UVG1.jpg" width="100%" alt="UV Segmentation Gallery">
</p>

**Gallery of UV unwrapping results using our generated UV segmentation.** Artists can readily apply textures to the resulting UV layout: each component of the input shape is cleanly and consistently separated into well-defined islands, enabling targeted texture painting without inadvertently affecting other parts.

## BibTeX

```bibtex
@article{xu2026sato,
  title   = {Strips as Tokens: Artist Mesh Generation with Native UV Segmentation},
  author  = {Xu, Rui and Qin, Dafei and Qiao, Kaichun and Dong, Qiujie and Pi, Huaijin and Zhang, Qixuan and Zhang, Longwen and Xu, Lan and Yu, Jingyi and Wang, Wenping and Komura, Taku},
  journal = {ACM Transactions on Graphics (TOG)},
  year    = {2026}
}
```
