---
layout: page
title: Classification on Imbalanced Browse Node data using Transformers
description:  Customized DeBERTa with Focal Loss for large-scale e-commerce browse node classification, improving convergence, confidence, and performance on imbalanced product data.
img: assets/img/project_imgs/cises_deberta.png
importance: 2
category: Publications
related_publications: False
---

#### Published in the 2023 International Conference on Computational Intelligence and Sustainable Engineering Solutions (CISES): [link🔗](https://ieeexplore.ieee.org/document/10183484)

[Github repo🔗](https://github.com/kumar-selvakumaran/AR_enabled_textbooks)


**What is this project about?**

This project develops a **customized DeBERTa-based transformer** for **browse node classification in e-commerce product catalogs**, tackling the twin challenges of **massive scale** and **class imbalance**. By integrating **Focal Loss** (originally designed for object detection) into DeBERTa, the model makes **more confident predictions** on underrepresented product categories while maintaining scalability for millions of records.

* **Goal**: Build an efficient, scalable NLP pipeline that:

  1. Classifies products into fine-grained browse nodes.
  2. Addresses **imbalanced product distributions**.
  3. Encourages **confident predictions** across all classes.

---

### Problem Approach

* **E-commerce product classification** is difficult because:

  * Data is **massive** (millions of products, 250+ classes).
  * Classes are **highly imbalanced** (many rare product categories).
  * Standard **cross-entropy loss** leads to underconfident predictions on minority classes.

* This project uses:

  * **DeBERTa** (Decoding-enhanced BERT with disentangled attention) for contextual understanding of product titles + descriptions.
  * **Focal Loss** to down-weight easy, overrepresented samples and focus on harder, underrepresented classes.
  * **Inter-batch validation** to efficiently monitor convergence on large datasets.

---

### Methodology

1. **Data Preparation**

   * Dataset: 1,004,773 product records across 250 browse node classes.
   * Text features: product title, bullet points, and description concatenated.
   * Missing values handled by simple concatenation → ensures no data loss.

2. **Modeling with DeBERTa**

   * Uses **disentangled attention** (separates word, segment, and position information).
   * Uses **enhanced decoding** (absolute + relative positional embeddings).

3. **Customization with Focal Loss**

   * Replaces cross-entropy with Focal Loss.
   * Down-weights **underconfident predictions**.
   * Helps the model **fit minority classes** better.

4. **Training & Validation**

   * Batch size constrained by computational limits (\~7850 batches/epoch).
   * **Inter-batch validation every 300 batches** to track unbiased performance.

---

### Applications: E-Commerce

* **Product Cataloguing** – Assign browse node IDs for millions of products automatically.
* **Product Discovery** – Improve search and recommendation by ensuring products are classified into the right categories.
* **Inventory Management** – Group and manage products at scale with consistent labels.

---

### Why This Approach is Better

* **Handles Imbalance**: Focal Loss improves predictions on minority classes, where cross-entropy underfits.
* **Confident Predictions**: Encourages the model to converge toward **high-confidence outputs**, reducing underconfident classifications.
* **Scalable**: DeBERTa + efficient tokenization + inter-batch validation enables training on million-scale datasets.
* **Faster Convergence**: Custom DeBERTa converges faster than vanilla versions, reducing compute costs.

---

### Findings

* **Default DeBERTa vs. Custom DeBERTa (Focal Loss)**:

  * Custom version converged **quicker** and performed better on minority classes.
  * Validation accuracy improved by \~2%.
  * Training + validation curves showed **slower slope decay**, indicating stable convergence.

* **Comparison with Other Transformers**:

  * Outperformed BERT, RoBERTa, Electra, and DistilBERT in both accuracy and loss.
  * Achieved **0.839 validation accuracy** (vs. 0.805–0.827 for others).

---

### Deliverables

* **Customized DeBERTa model** with Focal Loss integration.
* **Resource-efficient tokenization pipeline** (Rust-based, parallelized).
* **Performance logs + visualizations** (accuracy, loss, convergence trends).

---

### Impact & Implications

* **For businesses**: Faster, more accurate classification at scale → better cataloguing, search, and recommendation.
* **For research**: Demonstrates how **loss functions from computer vision (Focal Loss)** can successfully extend to NLP tasks.
* **For industry adoption**: Shows a practical tradeoff between accuracy, confidence, and scalability in large-scale product data.

{% include figure.liquid loading="eager" path="assets/img/project_imgs/cises_deberta.jpg" title="model benchmark and proposed method evaluation" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    Finetuning results for product browse node classification. DeBERTa outperforms other transformers, and integrating Focal Loss yields faster, more confident convergence.
</div>