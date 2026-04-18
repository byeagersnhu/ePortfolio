---
title: Enhancement Three
layout: page
---

[Home](index.md) |
[Original Artifact](original-artifact.md) |
[Enhancement One](enhancement-one.md) |
[Enhancement Two](enhancement-two.md) |
[Enhancement Three](enhancement-three.md) |
[Professional Self-Assessment](self-assessment.md)

---

# Enhancement Three: Security & Data Integrity

## Repository Link
[View Enhancement Three Repository](https://github.com/byeagersnhu/enhancement-three)

---

## Narrative
The artifact I selected for this enhancement is the database and backend layer of the Animal Adoption Center Dashboard, a full‑stack application originally created in CS‑340. The system uses a Node.js and Express backend connected to a MongoDB database, with an Angular frontend for interacting with animal records. While the original version was functional, it relied on minimal validation, accepted loosely structured data, and lacked safeguards against malformed or excessive requests.

For this enhancement, I focused on strengthening the database model, enforcing strict validation rules, and improving backend security to ensure the system behaves predictably and safely under real‑world conditions.

I selected this artifact because it represents the core of the application’s integrity: the schema, validation logic, and request‑handling pipeline. Enhancing this layer allowed me to demonstrate my ability to design intentional data models, enforce business rules through Mongoose validation, and apply security‑first thinking through rate limiting and unknown‑field rejection. These improvements elevate the project from a classroom prototype to a more professional, production‑ready application.

---

## Backend and Database Enhancements

The most significant improvements centered on the database model and request validation. I strengthened the Mongoose schema by adding required fields, enums, trimming rules, and type constraints. These changes ensure that only valid, intentional data enters the database and that every record adheres to a predictable structure.

	animal_type: { 
   		type: String, 
   		required: true, 
   		unique: false, 
   		trim: false, 
   		enum: [‘Dog’, ‘Cat’, ‘Bird’, ‘Other’] 
	}, 

I also enabled unknown‑field rejection, preventing extra or unexpected fields from being processed or stored. This reduces schema drift, improves data integrity, and mitigates the risk of malicious payloads.

To protect the API from excessive or automated requests, I implemented rate limiting on sensitive routes such as the Create Animal endpoint:

	const createAnimalLimiter = rateLimit({ 
   		windowMs: 60 * 1000, 
   		max: 10,  
	   message: { 
    	  error: “Too many create attempts. Please slow down.” 
   	} 
	}); 
 
This ensures that even under high request volume or automated misuse, the system remains stable, predictable, and secure.
---

## Validated Request Data Flow

#### Create Animal Modal (Frontend Validation + Rate Limiting)
This screenshot shows the Create Animal modal, which now enforces strict validation rules before a request is sent.

![Create Modal](/ePortfolio/assets/images/enh3-create-modal.png)

When a user submits the Create Animal form, the request moves through a structured validation pipeline:

1. Angular frontend validation ensures required fields are present and correctly formatted.  
2. Rate limiting prevents excessive create attempts within a short time window.  
3. Unknown‑field stripping removes any fields not defined in the schema.  
4. Schema validation enforces required fields, enums, type checks, and trimming rules.

Only when the request satisfies every rule does the system allow the document to be inserted. Invalid requests—such as missing fields, incorrect types, or disallowed values—are rejected with clear error messages.

This layered approach ensures that every record entering the database is intentional, consistent, and aligned with the application’s defined data model.

---

## Testing Validation and Rate Limiting

To verify that the enhanced validation rules and rate‑limiting protections worked correctly, I conducted structured backend tests using two custom Node.js scripts: validateSchema.js and cleanupTestData.js.

- The validation script attempts to insert a series of controlled test documents—some valid, others intentionally malformed—to confirm that the schema enforces all rules.  
- The cleanup script removes temporary records created during testing, ensuring the database remains clean.

#### Schema Validation Test
This screenshot shows the output of the validation test script, which attempts to insert one valid and several intentionally malformed documents.

![Validation Test](/ePortfolio/assets/images/enh3-validation-test.png)

#### Test Cleanup Script
After each test cycle, the cleanup script removes temporary documents to keep the database clean.

![Cleanup](/ePortfolio/assets/images/enh3-test-cleanup.png)

I also tested the rate limiter by submitting rapid, repeated POST requests to confirm that excessive create attempts were blocked with the appropriate error message. Together, these tests provided a reliable, repeatable way to validate the integrity of the schema and the effectiveness of the security enhancements.

---

## Reflection and Outcomes

This enhancement strengthened my understanding of how critical strong validation, schema design, and secure request handling are in real‑world applications. By restructuring the Mongoose model, enforcing strict validation rules, and adding rate limiting and unknown‑field rejection, I gained deeper insight into how backend systems maintain data integrity and protect themselves from misuse.

- **Outcome One:** Modular scripts and clear backend structure support collaborative development.  
- **Outcome Two:** The validation scripts and error messages demonstrate clear, professional communication.  
- **Outcome Three:** Designing a rule‑driven data pipeline required algorithmic reasoning and structured problem‑solving.  
- **Outcome Four:** Implementing modern tools such as Node.js, Express, MongoDB, and Mongoose demonstrates mastery of industry‑standard techniques.  
- **Outcome Five:** Rate limiting, input sanitization, and unknown‑field rejection reflect a strong security mindset.  

Throughout this enhancement, I learned how to maintain schema consistency, debug backend‑to‑frontend interactions, and design predictable data flows. These improvements significantly increased the reliability and safety of the application and strengthened my confidence as a backend engineer.

---

## Key Improvements
- Strict schema validation  
- Unknown‑field rejection  
- Rate limiting  
- Backend testing scripts  

---

[<-Enhancement Three](enhancement-three.md) | [Profession Self-Assessment ->](self-assessment.md)
