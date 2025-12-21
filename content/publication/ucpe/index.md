---
title: "Unified Camera Positional Encoding for Controlled Video Generation"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Boying Li
- Meng Wei
- Yan-Pei Cao
- Camilo Cruz Gambardella
- Dinh Phung
- Jianfei Cai

# # Author notes (optional)
# author_notes:
# - "Equal contribution"
# - "Equal contribution"
# - "Equal contribution"

date: "2025-12-22T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2017-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: arXiv preprint

abstract: ""

# Summary. An optional shortened abstract.
summary: "Camera-controlled text-to-video generation, now with intrinsics, distortion and orientation control!"

tags:
- Deep Learning
- Video Generation
- Camera Control
- Camera Positional Encoding

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
links:
- name: arXiv
  url: 'https://arxiv.org/abs/2512.07237'

url_pdf: ''
url_code: 'https://github.com/chengzhag/UCPE'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: 'https://youtu.be/DogzWyoVBEs'

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Camera-controlled video generation with UCPE'
  focal_point: Center
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []
# - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: "" # example
---

<!-- {{% callout note %}}
Click the *Cite* button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /callout %}}

{{% callout note %}}
Create your slides in Markdown - click the *Slides* button to check out the example.
{{% /callout %}}

Supplementary notes can be added here, including [code, math, and images](https://wowchemy.com/docs/writing-markdown-latex/). -->

## <div class="publication-header">arXiv 2026</div>

<div class="publication-header">
  <a href="https://chengzhag.github.io/" target="_blank">Cheng Zhang</a>
  <sup>1,2</sup>
  &nbsp; &nbsp;
  <a href="https://leeby68.github.io" target="_blank">Boying Li</a>
  <sup>1</sup>
  &nbsp; &nbsp;
  <a href="https://github.com/Meng-Wei" target="_blank">Meng Wei</a>
  <sup>1</sup>
  <!-- &nbsp; &nbsp; -->
  <br />
  <a href="https://yanpei.me" target="_blank">Yan-Pei Cao</a>
  <sup>3</sup>
  &nbsp; &nbsp;
  <a href="https://www.researchgate.net/profile/Camilo-Cruz-Gambardella" target="_blank">Camilo Cruz Gambardella</a>
  <sup>1,2</sup>
  &nbsp; &nbsp;
  <a href="https://dinhphung.ml" target="_blank">Dinh Phung</a>
  <sup>1</sup>
  &nbsp; &nbsp;
  <a href="https://jianfei-cai.github.io" target="_blank">Jianfei Cai</a>
  <sup>1</sup>
</div>

<div class="publication-header">
  <sup>1</sup>
  <a href="https://www.monash.edu" target="_blank">Monash University</a> 
  &nbsp; &nbsp;
  <!-- <br /> -->
  <sup>2</sup>
  <a href="https://building4pointzero.org" target="_blank">Building 4.0 CRC</a>
  &nbsp; &nbsp;
  <sup>3</sup>
  <a href="https://github.com/VAST-AI-Research" target="_blank">VAST</a> 
  <!-- <br /> -->
</div>

<center>
  <!-- <a href="#" class="btn btn-outline-primary js-cite-modal" data-filename="cite.bib">
  Cite
  </a> -->
  <a href="https://github.com/chengzhag/UCPE" class="btn btn-outline-primary" target="_blank">
  Code
  </a>
  <a href="https://www.youtube.com/watch?v=DogzWyoVBEs" class="btn btn-outline-primary" target="_blank">
  Video
  </a>
  <!-- <a href="https://www.bilibili.com/video/BV1By4y1g7c5/" class="btn btn-outline-primary" target="_blank">
  bilibili
  </a> -->
  <a href="https://arxiv.org/abs/2512.07237" class="btn btn-outline-primary">
  arXiv
  </a> 
  <a href="https://arxiv.org/pdf/2512.07237" class="btn btn-outline-primary">
  Paper
  </a>
</center>


---
## Video

{{< youtube DogzWyoVBEs >}}

Our UCPE introduces a geometry-consistent alternative to Plücker rays as one of the core contributions, enabling better generalization in Transformers. We hope to inspire future research on camera-aware architectures.

---

## TLDR

🔥 Camera-controlled text-to-video generation, now with intrinsics, distortion and orientation control!

<p align="center">
  <img src="cameras.png"
       height="120"
       style="display:inline-block; margin-right:48px;">
  <img src="orientation.png"
       height="140"
       style="display:inline-block;">
</p>

📷 UCPE integrates Relative Ray Encoding—which delivers significantly better generalization than Plücker across diverse camera motion, intrinsics and lens distortions—with Absolute Orientation Encoding for controllable pitch and roll, enabling a unified camera representation for Transformers and state-of-the-art camera-controlled video generation with just 0.5% extra parameters (35.5M over the 7.3B parameters of the base model)

<p align="center">
  <img src="video-ucpe.gif"
       alt="UCPE"
       style="max-height:480px; width:auto;">
</p>

---

## Highlights

Our **Relative Ray Encoding** not only generalizes to but also enables controllability over a wide range of camera intrinsics and lens distortions.

<p align="center">
  <img src="video-lens.gif"
       alt="Lens control"
       style="max-height:480px; width:auto;">
</p>

Its geometry-consistent design further allows strong generalization and controllability over diverse camera motions.

<p align="center">
  <img src="video-pose.gif"
       alt="Pose control"
       style="max-height:480px; width:auto;">
</p>

We also introduce **Absolute Orientation Encoding** to eliminate the ambiguity in pitch and roll in previous T2V methods.

<p align="center">
  <img src="video-orientation.gif"
       alt="Orientation control"
       style="max-height:480px; width:auto;">
</p>

---

## Abstract

Transformers have emerged as a universal backbone across 3D perception, video generation, and world models for autonomous driving and embodied AI, where understanding camera geometry is essential for grounding visual observations in three-dimensional space. However, existing camera encoding methods often rely on simplified pinhole assumptions, restricting generalization across the diverse intrinsics and lens distortions in real-world cameras. We introduce **Relative Ray Encoding**, a geometry-consistent representation that unifies complete camera information, including 6-DoF poses, intrinsics, and lens distortions. To evaluate its capability under diverse controllability demands, we adopt camera-controlled text-to-video generation as a testbed task. Within this setting, we further identify pitch and roll as two components effective for **Absolute Orientation Encoding**, enabling full control over the initial camera orientation. Together, these designs form **UCPE (Unified Camera Positional Encoding)**, which integrates into a pretrained video Diffusion Transformer through a lightweight spatial attention adapter, adding **less than 1% trainable parameters** while achieving state-of-the-art camera controllability and visual fidelity. To facilitate systematic training and evaluation, we construct a large video dataset covering a wide range of camera motions and lens types. Extensive experiments validate the effectiveness of UCPE in camera-controllable video generation and highlight its potential as a general camera representation for Transformers across future multi-view, video, and 3D tasks.

---
## Method

{{< figure width="600" src="rays.png" caption="**Spherical Camera Optical Flow.** The optical flow from a panoramic video (left) can be interpreted as a spherical camera optical flow (right). For complex motion **f**, the camera rotation yields an analytic rotation flow **fr** on the sphere. By decomposing **f** into **fr** and its residual, we obtain a derotated flow **fd** that more clearly captures camera translation and object dynamics." >}}

{{< figure width="600" src="pipeline.png" caption="**Overview of Spatial Attention Adapter.** The adapter injects UCPE into pretrained Transformers through a lightweight branch that preserves pretrained priors. It constructs hybrid encoding from the world-to-ray transform **T**^rw and an optional Lat-Up map, applies them within attention, and fuses the resulting camera-aware tokens back through a zero-initialized linear layer." >}}
