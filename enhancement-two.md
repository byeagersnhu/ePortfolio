---
title: Enhancement Two
layout: page
---

[Home](index.md) |
[Original Artifact](original-artifact.md) |
[Enhancement One](enhancement-one.md) |
[Enhancement Two](enhancement-two.md) |
[Enhancement Three](enhancement-three.md) |
[Professional Self-Assessment](self-assessment.md)

---

# Enhancement Two: Ranking Algorithm & Fuzzy Search

## Repository Link
[View Enhancement Two Repository](https://github.com/byeagersnhu/enhancement-two)

---

## Narrative
The artifact I selected for Enhancement Two is the backend search and filtering system from my Animal Adoption Center dashboard, originally created in **CS‑340: Client/Server Development**. The initial version used Python, JupyterDash, and basic filtering logic. It did not include meaningful search algorithms, ranking systems, or data‑driven decision logic.

In Enhancement One, I rebuilt the JupyterDash project into a MEAN‑stack application. For Enhancement Two, I expanded the backend significantly by implementing:

- a **custom multi‑criteria ranking algorithm** that evaluates animals for Water, Mountain, and Disaster rescue suitability  
- a **fuzzy search system** capable of flexible, multi‑field, case‑insensitive matching  

I selected this artifact because it allowed me to demonstrate mastery of algorithmic reasoning, data‑structure‑driven problem solving, and backend architecture. The enhancement shows my ability to design, implement, and optimize algorithms that operate on real data structures and integrate them into a full‑stack application.

---

## Algorithmic Components
Several components demonstrate my algorithmic skill:

- **rankAnimal()** — a custom scoring algorithm that evaluates each animal using weighted attributes  
- **getApplicableRescueTypes()** — determines which rescue categories an animal qualifies for  
- **attachRescueTypes()** — enriches raw database documents with computed rescue classifications  
- **Fuzzy search logic** — uses regular expressions and multi‑field matching  
- **Efficient data handling** — uses arrays, maps, and object transformations  

### Example: Water Rescue Scoring
Suppose an animal has the following attributes:

- Breed: Labrador Retriever  
- Age: 2 years (104 weeks)  
- Sex: Neutered Male  
- Type: Dog  

A simplified scoring breakdown might look like:

| Attribute | Condition | Score | Total |
|----------|-----------|-------|-------|
| Breed | Matches preferred water‑rescue breeds | +150 | 150 |
| Age | Between 1–3 years | +34 | 184 |
| Sex | Neutered male preferred | +40 | 224 |
| Type | Must be a dog | +50 | 274 |

This example illustrates how weighted, domain‑specific logic produces meaningful rankings.

---

#### Fuzzy Search Example
The fuzzy search evaluates multiple fields using case‑insensitive partial matching.

![Fuzzy Search](/ePortfolio/assets/images/enh2-fuzzy.png)

#### Rescue‑Type Badges
Each animal card now displays badges showing which rescue categories it qualifies for.

![Rescue Badges](/ePortfolio/assets/images/enh2-badges.png)

#### Rescue‑Type Ranking
Each animal can be ranked by rescue‑type suitability. Ranking is also case‑insensitive.

![Water Rescue Ranking](/ePortfolio/assets/images/enh2-water-rescue.png)
![Mountain Rescue Ranking](/ePortfolio/assets/images/enh2-mountain-rescue.png)
![Disaster Rescue Ranking](/ePortfolio/assets/images/enh2-disaster-rescue.png)

---

## Comparison to the Original System
The original system, built in Python using JupyterDash, offered only basic filtering and display capabilities. The backend consisted of a simple CRUD wrapper around MongoDB, where the `read()` method returned raw documents and the dashboard applied static filters through radio buttons and dropdowns.

Key limitations included:

- no search engine  
- no ranking logic  
- no weighted evaluation  
- no service‑layer abstraction  
- all filtering performed client‑side in Pandas  
- limited scalability  

In contrast, the enhanced MEAN‑stack version introduces a fully realized backend search system with:

- fuzzy matching  
- multi‑field evaluation  
- a custom multi‑criteria rescue‑ranking algorithm  
- server‑side filtering, sorting, and scoring  
- structured controllers and services  

The fuzzy search evaluates each animal in **O(n)** time using case‑insensitive regular expressions. The ranking algorithm adds an **O(n log n)** sorting step to order animals by suitability score.

Performance improved significantly. The original system reloaded the entire dataset and filtered it in the browser, while the enhanced version uses optimized server‑side queries, structured evaluation logic, and a ranking pipeline that scales cleanly.

The result is a faster, more flexible, and far more capable system than the original Python implementation.

---

## Reflection and Outcomes
This enhancement demonstrates strong alignment with all five program outcomes and reflects significant personal learning and growth.

- **Outcome One:** Modular services (`rankAnimals`, `searchAnimals`, `attachRescueTypes`) support collaborative development and clear communication.  
- **Outcome Two:** Clear documentation, intentional naming, and UI elements such as rescue badges communicate algorithmic output effectively.  
- **Outcome Three:** The ranking algorithm applies weighted scoring, fuzzy matching, and efficient sorting to solve a real problem using algorithmic principles.  
- **Outcome Four:** Implementing the enhancement using Node.js, Express, MongoDB, and Angular demonstrates mastery of modern tools and techniques.  
- **Outcome Five:** Although not primarily security‑focused, the enhancement applies a security mindset through sanitized input, safe query construction, and minimal data exposure.  

Throughout this process, I learned how to break a complex problem into algorithmic components, structure a maintainable service layer, and maintain schema consistency between the frontend and backend. I also gained experience debugging interactions between Angular, Express, and MongoDB to ensure UI behavior accurately reflected backend logic.

These lessons emerged through challenges such as resolving mismatched query parameters, preventing UI sorting from overwriting ranked results, and ensuring rescue ranking triggered correctly based on user input. Ultimately, this enhancement demonstrates my ability to design and implement a real algorithm, integrate it into a full‑stack application, and polish the UI to reflect algorithmic output.

---

## Key Improvements
- Multi‑criteria ranking  
- Fuzzy search pipeline  
- Improved user experience  

---


[<- Enhancement One](enhancement-one.md) | [Enhancement Three ->](enhancement-three.md)

