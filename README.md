# GTPBD-MM

This repository is the official code and resource repository for the paper **"GTPBD-MM: A Global Terraced Parcel and Boundary Dataset with Multi-Modality"**. We introduce the first **multimodal benchmark** for **complex terraced parcel extraction**, aiming to jointly model visual appearance, textual semantics, and terrain geometry to address two core challenges in terraced parcel delineation: **semantic confusion** and **boundary ambiguity**.

## 📁 Resources

### 1. Supplementary Materials

- The detailed supplementary materials for the paper are available in this repository under the file name: `supplementary materials(GTPBD-MM).pdf`.
- This document includes additional dataset samples, comparative visualizations with existing datasets, model details, complete definitions of evaluation metrics, and more extensive experimental results and qualitative visualizations.

### 2. GTPBD-MM Dataset

- The GTPBD-MM dataset is publicly available.
- It can be accessed and downloaded via the Hugging Face Datasets platform: [https://huggingface.co/datasets/wxqzzw/GTPBD-MM](https://huggingface.co/datasets/wxqzzw/GTPBD-MM)
- We strongly recommend visiting the official dataset page for the latest access instructions and terms of use.

## 🗂️ Dataset Overview (GTPBD-MM)

GTPBD-MM is the first multimodal benchmark dataset designed for global complex terraced parcel extraction. It is built upon the [GTPBD](https://github.com/Z-ZW-WXQ/GTPBD) dataset.

- **Core characteristic**: **multimodal alignment**. Each sample consists of spatially aligned **high-resolution optical imagery**, **digital elevation model (DEM)** data, **task-oriented textual descriptions**, and **three-level annotations** (mask, boundary, and parcel vector labels), providing a unified foundation for multimodal parsing and terraced parcel extraction.
- **Scale and coverage**: The dataset is collected from globally distributed terraced regions, covering **25 countries** worldwide, with a total area exceeding **900 km²** and more than **200,000 manually annotated parcel polygons**. In addition to covering the seven major geographical regions of China, the dataset further includes samples from 11 additional countries, such as Nepal, Indonesia, and Zimbabwe, offering rich diversity in morphology and regional styles.
- **Supported evaluation settings**: The dataset is designed to support systematic multimodal evaluation under the following input settings:
  - **Image only**
  - **Image + Text**
  - **Image + Text + DEM**
- **Text descriptions**: The textual descriptions are specifically designed for the terraced parcel extraction task. They characterize scene-level layout, local parcel morphology, and surrounding spatial relationships, providing task-relevant semantic information beyond generic captions. High-frequency terms include *terrace*, *irregular*, *curved*, *dense*, and *vegetation*.

## 🧠 Proposed Baseline Model: ETTerra

We further propose a multimodal baseline model, **ETTerra**, short for **Elevation- and Text-guided Terraced Parcel Network**.

- **Core idea**: ETTerra adopts a dual-branch design, where textual semantic priors are used to alleviate **semantic confusion**, and DEM-based geometric priors are exploited to address **boundary ambiguity**.
- **Architecture**:
  1. **Cross-modal semantic enhancement branch**: This branch leverages category-level and scene-level priors from textual descriptions to enhance visual features through multi-head cross-attention, thereby suppressing background interference.
  2. **Elevation-prior-guided boundary enhancement branch**: This branch independently encodes DEM data and employs a dedicated *elevation-feature fusion* module to inject terrain geometric structure into visual features, sharpening ambiguous terraced boundaries at the feature level.
- **Performance**: In the comprehensive benchmark on GTPBD-MM, ETTerra (Image+Text+DEM) achieves the best or highly competitive performance across pixel-level, edge-level, and object-level metrics, validating the effectiveness of joint multimodal modeling.

## 📊 Benchmark Results

We establish a comprehensive benchmark on GTPBD-MM covering multiple method families, including general semantic segmentation, parcel delineation, reasoning segmentation, and multimodal parcel delineation methods. Experimental results show that:

- Compared with image-only methods, introducing the **text modality** provides effective semantic priors and helps mitigate semantic confusion.
- Further incorporating the **DEM modality** offers critical geometric cues for recovering structurally consistent boundaries and effectively alleviates boundary ambiguity.
- By jointly modeling image appearance, textual semantics, and terrain geometry, ETTerra produces more accurate, coherent, and structurally consistent terraced parcel delineation results.

For detailed quantitative results and qualitative comparisons, please refer to the main paper and the supplementary materials.

---
