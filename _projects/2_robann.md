---
layout: page
title: Robustness Analysis of Neural Networks 
description: Exploring techniques to analyze and robustify feature specific dissections of neural networks
img: assets/img/project_imgs/robust_analysis.png
importance: 2
category: Projects
related_publications: true
---

[Github repo🔗](https://github.com/kumar-selvakumaran/RobAn_veriml)

**What is this project about?**

 This project explores how **neural networks break under adversarial attacks** (tiny, carefully designed changes to images that trick AI models). Instead of looking at the model as a whole, it studies the problem from a **feature-by-feature perspective** — i.e., by examining the individual neurons that detect shapes, textures, or objects. This work was inspired by {% cite ilyas2019adversarial %} and {% cite bau2020understanding %}.

* **Goal**: Make models more robust by:

  1. Finding which features are **useful but fragile** under attack.
  2. Strengthening the model to rely on **robust, reliable features** instead.

---

### Problem Approach

* **Features = Neurons’ activations**: Each neuron (or filter) in a CNN responds to patterns like edges, colors, or objects.
* **Adversarial attacks** often target *brittle but useful* features — the ones that help with classification but flip easily when disturbed.
* By dissecting the network:

  * Assign **concepts** (e.g., “window,” “fur,” “wheel”) to neurons.
  * Check which concepts survive or collapse under noise.

---

### Methodology

1. **Identify Features**

   * Measure how strongly each neuron is activated by an image.
   * Pick the top activated ones = the most important features.

2. **Classify Features**

   * **Robust & Useful** → strong, reliable signals.
   * **Non-robust & Useful** → dangerous; fooled easily.
   * **Robust but Useless** → stable but unhelpful.
   * **Non-robust & Useless** → noise.

3. **Back-Perturbation**

   * Instead of letting adversarial noise trick the model, “push back” with corrective perturbations.
   * Create a **robust dataset** of images where the model learns to ignore brittle features.

---

### Deliverables

* **Layer selection strategy**: Prevent shallow/deep layers from dominating feature analysis.
* **Robustness classification**: Map adversarially fragile features back to real-world concepts (e.g., “grass” or “brick”).
* **Visual insights**: Show which concepts are brittle and how training shifts reliance toward robust ones.

---

### Impact & Implications

* **For AI safety**: Helps models resist adversarial attacks by teaching them to trust the “right” features.
* **For interpretability**: Bridges the gap between black-box AI and human-understandable concepts.
* **For research**: Introduces a **feature-first perspective** on robustness, not just loss-function tweaking.
* **For real-world AI**: Paves the way for more reliable vision systems in healthcare, autonomous driving, and security.

{% include figure.liquid loading="eager" path="assets/img/project_imgs/robust_analysis.png" title="robust_analysis" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    This figure visualizes regions that contributed the most to the neural network's prediction, and the concepts captured by the neurons that were activated the most.
</div>