---
layout: page
title: Single-Shot Localized Retrieval using YOLOv3
description:  A retrieval system that takes object selections as bounding box prompts from the user, given an image and retrievs similar objects from an image database.
img: assets/img/project_imgs/semantic_project_catalogue_searcher.png
importance: 3
category: Projects
related_publications: true
---

[Github repo🔗](https://github.com/kumar-selvakumaran/RobAn_veriml)

**What is this project about?**

This project explores how **neural networks can be used for content-based image retrieval (CBIR)** — finding visually similar objects based on features learned by an object detection network. Instead of classifying images into rigid categories (dog vs. cat), this system extracts object-specific embeddings and uses them for **similarity search and recommendations**.

* **Goal**: Enable search, grouping, and recommendation of objects by visual features such as **size, texture, color, and style** — especially in **product cataloguing contexts** where users look for items that “look like this one.”

---

### Problem Approach

* **Traditional retrieval methods** often rely on multi-step processes: first isolating an object manually, then extracting features in a separate step, and finally performing similarity search.
* This project makes retrieval more **efficient and scalable** by using a **single forward pass of the detection network** to:

  * Detect objects,
  * Extract embeddings,
  * And slice features for the chosen object.

This means **location-specific retrieval happens in one step**, avoiding the inefficiency of multi-stage pipelines.

---

### Methodology

1. **Detect Objects**

   * Run the image through an object detector to get bounding boxes.

2. **Extract Features (Embeddings)**

   * Collect feature maps from the detection backbone (e.g., ResNet, YOLO).

3. **Object-Specific Slicing**

   * Slice embeddings according to object location to isolate **features for the chosen object**.

4. **Similarity Search**

   * Compare the chosen object’s features against a pre-computed dataset using KNN.

5. **Retrieve Matches**

   * Return images ranked by similarity — highlighting visual attributes like **color, texture, and lighting**.

---

### Applications: Product Cataloguing

* **Furniture Catalogs** – A customer highlights a couch in a cluttered image; the system retrieves **visually similar couches** from the database.
* **E-commerce Product Discovery** – Group or recommend products by shared visual features (color, texture, style).
* **Automated Curation** – Streamline catalog management by automatically clustering products with similar aesthetics.

This workflow enables **fast, accurate, and context-aware cataloguing**, reducing the manual effort usually required for tagging or categorization.

---

### Why This Approach is Better

* **Single-Shot Retrieval**: The object detection network simultaneously handles object localization and feature extraction.
* **Efficiency**: Unlike multi-step methods that require separate processes for detection and embedding, this workflow performs **location-specific retrieval directly** from the detection backbone.
* **Scalability**: The system is well-suited for large product catalogues, where speed and automation are critical.

---

### Findings

Experiments show that the network captures rich object features:

* **Color and Texture** (e.g., fabric, material)
* **Shape and Size**
* **Appearance under lighting**

These embeddings make similarity search and recommendation **practical and accurate**, even in visually diverse datasets.

---

### Deliverables

* **Feature extraction pipeline** (ResNet / YOLO embeddings).
* **KNN-based similarity search** on pre-computed object embeddings.
* **Visualization experiments** of targets vs. retrieved matches.

---

### Impact & Implications

* **For product cataloguing**: Simplifies grouping, tagging, and discovery of items with shared features.
* **For users**: Enables intuitive “find me more like this” search.
* **For research**: Extends CBIR from classification-based to **object-detection–based retrieval** with efficiency gains.

---

### Development Setup

* **OS**: Windows 11 with Docker (WSL2, Ubuntu 22.04)
* **Docker desktop**: v4.22.1
* **Docker version**: 24.0.5
* **Compiler**: Python 3.7

---

### Run Instructions

Go through the following notebooks to reproduce the workflow:

1. [init_setup.ipynb](https://github.com/kumar-selvakumaran/semantic_product_catalogue_assistant/blob/main/src/init_setup.ipynb)
2. [Resnet_embedding_collector.ipynb](https://github.com/kumar-selvakumaran/semantic_product_catalogue_assistant/blob/main/src/Resnet_embedding_collector.ipynb)
3. [embedding_KNN_analyzer.ipynb](https://github.com/kumar-selvakumaran/semantic_product_catalogue_assistant/blob/main/src/embedding_KNN_analyzer.ipynb)
4. [Yolo_embedding_collector.ipynb](https://github.com/kumar-selvakumaran/semantic_product_catalogue_assistant/blob/main/src/Yolo_embedding_collector.ipynb)
5. [Location_information_analysis.ipynb](https://github.com/kumar-selvakumaran/semantic_product_catalogue_assistant/blob/main/src/Location_information_analysis.ipynb)

{% include figure.liquid loading="eager" path="assets/img/project_imgs/prodseek_workflow.jpg" title="prodseek_workflow" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    This figure visualizes the workflow of the retrieval pipeline.
</div>

{% include figure.liquid loading="eager" path="assets/img/project_imgs/local_retrieval_masking.jpg" title="local_retrieval_masking" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    This figure visualizes how localized retrieval is done in the latent space of the yolov3 model. each channel selection in the spatial embedding grid corresponds to a crop in the input image, as shown in the figure. The yellow grid surrounded (surrounded by the blue) is the spatial
    embedding selection, and the corresponding crop is indicated using the black bounding box.
</div>
