---
title: "Holistic 3D Scene Understanding from a Single Image with Implicit Representation"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Zhaopeng Cui
- Yinda Zhang
- Bing Zeng
- Marc Pollefeys
- Shuaicheng Liu

# Author notes (optional)
author_notes:
- "Equal contribution"
- "Equal contribution"
- "Equal contribution"

date: "2021-03-11T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2017-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: IEEE Conference on Computer Vision and Pattern Recognition, 2021
publication_short: CVPR 2021

abstract: We present a new pipeline for holistic 3D scene understanding from a single image, which could predict object shape, object pose, and scene layout. As it is a highly ill-posed problem, existing methods usually suffer from inaccurate estimation of both shapes and layout especially for the cluttered scene due to the heavy occlusion between objects. We propose to utilize the latest deep implicit representation to solve this challenge. We not only propose an image-based local structured implicit network to improve the object shape estimation, but also refine 3D object pose and scene layout via a novel implicit scene graph neural network that exploits the implicit local object features. A novel physical violation loss is also proposed to avoid incorrect context between objects. Extensive experiments demonstrate that our method outperforms the state-of-the-art methods in terms of object shape, scene layout estimation, and 3D object detection.

# Summary. An optional shortened abstract.
summary: We present a new pipeline which takes a single image as input, estimates layout and object poses, then reconstructs the scene with Signed Distance Function (SDF) representation.

tags:
- Deep Learning
- 3D Reconstruction
- 3D Detection
- 3D Scene Understanding

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: 'https://arxiv.org/pdf/2103.06422'
url_code: 'https://github.com/pidan1231239/Implicit3DUnderstanding'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Scene reconstruction comparison'
  focal_point: ""
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


## 3D Scene Understanding 
Given a single color image,
- Estimate the room layout, including object categories and poses in 3D space
- Reconstruct mesh of individual object

## Motivations
- Implicit representation like Signed Distance Function (SDF) can be used to detect collision and propagate gradients
- And together with structured representation (LDIF), the shapes can be learned better and more shape priors can be provided for relationship understanding
- Graph Convolutional Network (GCN) is proven to be good at resolving context information in the task of scene graph generation

## Pipeline
![pipeline](pipeline.png)

The proposed system consists of two stages, i.e., the initial estimation stage, and the refinement stage. 
In the initial estimation stage, a 2D detector is first adopted to extract the 2D bounding box from the input image, followed by an Object Detection Network (ODN) to recover the object poses as 3D bounding boxes and a new Local Implicit Embedding Network (LIEN) to extract the implicit local shape information from the image directly, which can further be decoded to infer 3D geometry.
The input image is also fed into a Layout Estimation Network (LEN) to produce a 3D layout bounding box and relative camera pose.
In the refinement stage, a novel Scene Graph Convolutional Network (SGCN) is designed to refine the initial predictions via the scene context information.

## Results
![results](results.png)

*Qualitative comparison on object detection and scene reconstruction.* We compare object detection results with Total3D and ground truth in both oblique view and camera view. The results show that our method gives more accurate bounding box estimation and with less intersection. We compare scene reconstruction results with Total3D in camera view and observe more reasonable object poses.
