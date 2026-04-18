---
title: Original Artifact
layout: page
---
[Home](index.md) |
[Original Artifact](original-artifact.md) |
[Enhancement One](enhancement-one.md) |
[Enhancement Two](enhancement-two.md) |
[Enhancement Three](enhancement-three.md) |
[Professional Self-Assessment](self-assessment.md)

---

## Repository Link
[View Original AAC Repository](https://github.com/byeagersnhu/CS-340/tree/main)

--- 

# Original Artifact: Animal Adoption Center (AAC)

The original AAC application was developed in **CS‑340: Client/Server Development** and served as the foundation for all three enhancements in this portfolio. While functional, the system had several limitations that restricted scalability, usability, and maintainability.

### Key Limitations of the Original System
- Filtering was limited to **three radio buttons** (Water, Mountain/Wilderness, Disaster/Tracking)  
- No sorting or ranking logic existed, and searching was limited to **breed only**  
- The UI was static and lacked modern interaction patterns  
- All filtering occurred **client‑side** using Pandas, limiting scalability  
- No backend validation, schema enforcement, or security controls  

---

This section depicts the original interface exactly as it appeared before any enhancements.

### Starting View
This screenshot shows the dashboard immediately after launching the original JupyterDash application.

![Starting View](/ePortfolio/assets/images/Starting.png)

### Disaster Rescue Filter
Selecting the **Disaster** radio button filtered the dataset to show only animals matching disaster rescue suitability.

![Disaster Rescue](/ePortfolio/assets/images/Disaster.png)

### Mountain/Wilderness Rescue Filter
Selecting the **Mountain or Wilderness** radio button filtered the dataset to show only animals matching mountain or wilderness rescue suitability.

![Mountain View](/ePortfolio/assets/images/Mountain.png)

### Reset View
The **Reset** option returned the dashboard to its initial state.

![Reset View](/ePortfolio/assets/images/Reset.png)

---

## Code Review Video

Before beginning the enhancement process, I conducted a structured code review of the original CS‑340 artifact using the **CS‑499 Code Review Checklist**. This review helped identify weaknesses in the original implementation and guided the direction of each enhancement.

### Key Findings from the Review
- The project lacked modularity and separation of concerns  
- Filtering logic was tightly coupled to UI components  
- All logic ran client‑side; **no backend layer existed**  
- No validation, schema enforcement, or security controls  
- Minimal documentation and inconsistent naming  
- Limited UI/UX functionality (four radio buttons, no sorting, breed‑only search)

A full walkthrough of the review is provided in the video below.

<div style="text-align:center;">
  <iframe width="560" height="315"
    src="https://www.youtube.com/embed/mFLUWp8lkbQ?si=lBmScg-f2lGVazTA"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen>
  </iframe>
</div>

---


[<- Home](index.md) | [Enhancement One ->](enhancement-one.md)

