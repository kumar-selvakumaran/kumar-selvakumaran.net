---
layout: page
title: Augmented Reality–Enhanced Textbooks
description: Exploring techniques to analyze and robustify feature specific dissections of neural networks
img: assets/img/project_gifs/ar_tb.gif
importance: 3
category: Publications
related_publications: False
---

[Github repo🔗](https://github.com/kumar-selvakumaran/RobAn_veriml)


**What is this project about?**

This project proposes a **scalable augmented reality (AR) pipeline** that integrates **interactive 3D experiences into textbooks** using affordable smartphones. By embedding AR markers into printed books, students from low-budget schools can access immersive visualizations of concepts — making learning more **engaging, interactive, and accessible** without expensive equipment.

👉 This work was **funded by the Tamil Nadu State Council for Science and Technology (TNSCST)**, highlighting its role in promoting **affordable, impactful educational technologies** for low-income schools.

* **Goal**: Create a low-cost, scalable AR system that:

  1. Enhances learning with **interactive 3D visualizations**.
  2. Runs on **affordable smartphones** with no extra hardware.
  3. Scales across entire curricula with reusable AR markers.

---

### Problem Approach

* Many schools, especially in low-income regions, rely almost entirely on **text-only education** with minimal learning tools.
* Meanwhile, smartphone penetration is relatively high, even in low-resource contexts.
* This project bridges that gap by combining **existing textbooks** with **AR visualizations**, triggered via printed QR-like markers.
* The pipeline emphasizes **scalability**, allowing entire subjects or curricula to be covered by systematically generating and managing AR experiences.

---

### Methodology

1. **Model Creation & Optimization**

   * Use **Blender** to design lightweight, mobile-ready 3D models.
   * Integrate existing **Sketchfab** assets where available (licensed under Creative Commons).

2. **Scene Integration**

   * Import models into **Unity 3D** and configure AR interactions (size, animations, sound, lighting).
   * Ensure low poly counts for smooth rendering on older smartphones.

3. **Marker Generation & Tracking**

   * Generate unique AR markers using an open-source marker generator.
   * Host them in **Vuforia’s database** for robust, real-time tracking.

4. **Deployment**

   * Build Android-compatible AR apps.
   * Students scan textbook markers with their smartphones → see interactive 3D experiences overlaid on the real world.

---

### Applications: Education

* **Science Learning** – Visualize magnetic fields, cell structures, or anatomy.
* **Literature** – Immerse students in stories by animating characters or scenes.
* **Practical Skills** – Simulate high-risk tasks (like surgery or lab experiments) safely and accessibly.

---

### Why This Approach is Better

* **Funded innovation**: Supported by **TNSCST** to democratize immersive education in Tamil Nadu.
* **Cost-effective**: Only requires textbooks + smartphones (no headsets or expensive equipment).
* **Scalable**: Automated marker generation and modular AR scenes allow rapid expansion across curricula.
* **Robust**: Works under challenging conditions (low light, partial occlusion, small marker size).
* **Accessible**: Democratizes immersive learning for low-budget schools, closing the gap with well-funded institutions.

---

### Findings

* Stable marker detection with as little as **20% visibility**.
* Robust tracking at recognition angles down to **22°** and marker sizes as small as **0.94 inches**.
* Operates reliably in **low-light conditions (≥ 32.6% of normal indoor lighting)**.
* Smooth performance achieved through Unity’s optimized rendering, GPU offloading, and lightweight 3D assets.

---

### Deliverables

* **Pipeline for AR model creation** (Blender + Sketchfab + Unity).
* **Marker generation system** with Vuforia integration.
* **Android AR learning app** with multiple subject-specific experiences.
* **Performance-tested AR modules** validated under occlusion, angle, resolution, and lighting constraints.

---

### Impact & Implications

* **For students**: Brings abstract or invisible concepts to life through interactive exploration.
* **For schools**: Provides affordable, scalable learning tools with no additional infrastructure costs.
* **For policy and research**: Demonstrates how targeted **funding from TNSCST** can create scalable, impactful educational technology for underserved communities.

{% include figure.liquid loading="eager" path="assets/img/project_gifs/ar_tb.gif" title="demo of the augmented reality app using dynamic (left) and static (right) 3d models" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    This figure visualizes regions that contributed the most to the neural network's prediction, and the concepts captured by the neurons that were activated the most.
</div>
