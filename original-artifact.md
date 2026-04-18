---
title: Orignal Artifact
layout: page
---
[Home](index.md) |
[Original Artifact](original-artifact.md) |
[Enhancement One](enhancement-one.md) |
[Enhancement Two](enhancement-two.md) |
[Enhancement Three](enhancement-three.md) |
[Professional Self-Assessment](self-assessment.md)

## Repository Link
[View Original AAC Repository](https://github.com/byeagersnhu/CS-340/tree/main)

# Original Artifact: Animal Adoption Center (AAC)

The original AAC application was developed in CS-340: Client/Server Development. It served as the foundation for all three enhancements in this portfolio.

While functional, the original system had several limitations: 

- Filtering was limited to **three radio buttons** (Water, Mountain or Wilderness, Disaster or Tracking)
- No sorting, or ranking logic exsisted, and limited searching (breed only)
- The UI was static and lacked modern interaction patterns
- All filtering occured **client-side** using Pandas, limiting scalability
- No backend validation, schema enforcement, or security controls

---
This depicts the original interface exactly as it appeared before any enhancements
#### Starting View
This shows the dashboard immediately after launching the oringal JupyterDash application.

![Starting View](/ePortfolio/assets/images/Starting.png)

#### Disaster Rescue Filter
Selecting the **Disaster** radio button filtered the dataset to show only animal matching disaster rescue suitability.

![Disaster Rescue](/ePortfolio/assets/images/Disaster.png)

#### Mountain Rescue Filter
Selecting the **Mountain or Wilderness** radio button filtered the dataset to show only animal matching mountain or wilderness rescue suitability.

![Mountain View](/ePortfolio/assets/images/Mountain.png)

#### Reset View
The **Reset** radio returned the dashboard to its initial state. 

![Reset View](/ePortfolio/assets/images/Reset.png)

---

## Code Review Video

Before beginning the enhancement process, I conducted a structured code review of the orginal CS-340 artifact. This review evaluated the project using the CS-499 Code Review Checklist. Some key findings from the review are:

- The project lacked modularity and separation of concerns
- Filtering logic was tightly coupled to UI components
- All logic ran client-side, no backend layer exsisted
- No validation, schema enforcement, or security controls
- Minimal documentation and inconsistent naming
- Limited UI/UX functionality (Four radio buttons, No sorting, breed only search)

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


