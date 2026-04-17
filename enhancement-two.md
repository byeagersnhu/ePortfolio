---
title: Enhancement Two
layout: page
---

<div class="nav-links">
  [Home](index.md) |
  [Original Artifact](original-artifact.md) |
  [Enhancement One](enhancement-one.md) |
  [Enhancement Two](enhancement-two.md) |
  [Enhancement Three](enhancement-three.md) |
  [Professional Self-Assessment](self-assessment.md)
</div>

# Enhancement Two: Ranking Algorithm & Fuzzy Search

## Repository Link
[View Enhancement Two Repository](https://github.com/byeagersnhu/enhancement-two)

## Narrative

The artifact I selected for Enhancement Two is the backend search and filtering system from my Animal Adoption Center dashboard, originally created in CS-340 Client/Server Development. The initial version of this project used Python, JupyterDash, mock data, and included only basic filtering and display logic. It did not include any meaningful search algorithms, ranking systems, or data-driven decision logic. In Enhancement One, I rebuilt the JupyterDash project into a MEAN-stack application. For Enhancement Two, I expanded the backend significantly by implementing a custom multi-criteria ranking algorithm that evaluates animals for different rescue-type suitability categories (Water, Mountain, and Disaster), and by replacing the original filter with a capable fuzzy search system that can locate animals based on flexible, multi-field queries. 

I selected this artifact because it allowed me to demonstrate clear mastery of algorithmic reasoning and data-structure-driven problem solving. The enhancement transformed a simple data filter into a fully functional, production-style search engine. This includes a custom scoring algorithm, multi-criteria evaluation, weighted ranking, efficient lookups, a clean service-layer abstraction, integration with a database, and a polished UI that reflects algorithmic output. This enhancement shows my ability to design, implement, and optimize algorithms that operate on real data structures and to integrate those algorithms into a full-stack application. 
	
### Algorithmic Components
Several components demonstrate my algorithmic skill. rankAnimal() is a custom scoring algorithm that evaluates each animal against rescue-type criteria using weighted attributes. getApplicableRescueTypes() determines which rescue categories an animal qualifies for based on structured rules. and attachRescueTypes() enriches raw database documents with computed rescue classifications. I also implemented fuzzy search logic using regular expressions and multi-field matching, along with efficient data handling using arrays, maps and object transformations. 

Here is a simplified example of how the Water Rescue logic evaluates an animal:

Suppose an animal has the following attributes

	•	Breed: Labrador Retriever
	•	Age: 2 years (104 weeks)
	•	Sex: Neutered Male
	•	Animal Type: Dog
	The Water Rescue criteria might include: 
	Attribute	Condition	Score	Total
	Breed	Matches preferred water-rescue breeds	+150	150
	Age	Between 1-3 years (based on the difference from the midpoint)	+34 	184
	Sex	Neutered Male Preferred	+40	224
	Type	Must be a dog (receives negative if not dog)	+50	274

This example illustrates how the algorithm uses weighted, domain-specific logic to produce meaningful rankings. 
The fuzzy search evaluate multiple fields using case-insensitive partial matching; name, breed, and animal_type. For example, the query “Shephard” would match any breed that contains the word Shephard (German Shephard, Australian Shephard) or a name the contains Shephard. The fuzzy search uses a regular expression and checks each field, returning any animal where any field contains the substring. This makes the search flexible and intuitive for users. 

### Comparison to the Original System
The original System, built in Python using JupyterDash, offered only basic filtering and display capabilities. The backend consisted of a simple CRUD wrapper around MongoDB, where the read() method returned raw documents and the dashboard applied static filters through radio buttons and dropdowns. There was no search engine, no ranking logic, no weighted evaluation, and no service-layer abstraction. The JupyterDash interface simply loaded the entire dataset into a Pandas DataFrame and filtered it client-side, which limited scalability and prevented any meaningful algorithmic processing. In contrast, the enhancement MEAN-stack version introduces a fully realized backend search system with fuzzy matching, multi-field evaluation, and a custom multi-criteria rescue-ranking algorithm. Instead of static UI filters, the Angular frontend now communicates with a structured Express controller and service layer that performs server-side filtering, sorting, and scoring. The fuzzy search algorithm evaluates each animal record in linear time, O(n), by checking the query against multiple fields using case-insensitive regular expressions, while the rescue-ranking algorithm adds and O(n log n) sorting step to order animals by computed suitability score. Together, these improvements create a scalable search pipeline that remains efficient even as the dataset grows. Performance improved significantly: the original system reloaded the entire dataset and performed all filtering in the browser, while the enhanced version uses optimized server-side queries, structured evaluation logic, and a ranking pipeline that scales cleanly. The result is a faster, more flexible, and far more capable system than the original Python implementation. 

### Reflection and Outcomes
This enhancement demonstrates strong alignment with all five program outcomes while also reflecting significant personal learning and growth. By structuring the backend into modular services such as rankAnimals, searchAnimals, and attachRescueTypes, I created a codebase that supports collaborative development and is accessible to diverse audiences, fulfilling Outcome One. Through clear documentation, intentional naming, and a polished UI that visually communicates algorithmic output, such as rescue badges and ranked cards, I delivered professional-quality written and visual communication aligned with Outcome Two. The design of the ranking algorithm itself directly satisfies Outcome Three, I applied algorithmic principles, weighted scoring, fuzzy matching, and efficient sorting to solve a real problem while managing trade-offs between flexibility, interpretability, and performance. Implementing the enhancement using industry-standard tools such as Node.js, Express, MongoDB, and Angular demonstrates mastery of modern techniques and tools, fulfilling Outcome Four. Finally, although the enhancement was not primarily security-focused, I still applied a security mindset by sanitizing user input, avoiding direct string interpolation in queries, and ensuring the search endpoint exposed only necessary fields, practices that mitigate common vulnerabilities and align with Outcome Five. 

Throughout the process of designing and refining the search and ranking system, I learned how to break a complex problem into algorithmic components, structure a clean and maintainable service layer, and maintain schema consistency between the frontend and backend. I also gained experience debugging the interactions between Angular, Express, and MongoDB to ensure that UI behavior accurately reflected backend logic. These lessons emerged through several key challenges: resolving mismatched query parameters between the frontend and backend, preventing the UI from overwriting ranked results with alphabetical sorting, and ensuring that rescue ranking triggered correctly based on user input. Each challenge strengthened my understanding of full-stack architecture, algorithm integration, and the importance of intentional data flow. Ultimately, this enhancement demonstrates my ability to design and implement a real algorithm, integrate it into a full-stack application, and polish the UI to reflect algorithmic output. The result is a high-quality search and ranking system that significantly improves the original artifact and clearly aligns with the program outcomes.

## Screenshots
![Ranking Example](assets/images/enh2-ranking.png)

## Key Improvements
- Multi-criteria ranking
- Fuzzy search pipeline
- Improved user experience
