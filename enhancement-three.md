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


# Enhancement Three: Security & Data Integrity

## Repository Link
[View Enhancement Three Repository](https://github.com/byeagersnhu/enhancement-three)

## Narrative
The artifact I selected for this enhancement is the database and backend layer of the Animal Adoption Center Dashboard, a full-stack application originally created in CS-340. The system uses a Node.js and Express backend connected to a MongoDB database, with an Angular frontend for interacting with animal records. While the original version of the artifact was functional, it relied on minimal validation, accepted loosely structured data, and lacked safeguards against malformed or excessive requests. For this enhancement, I focused on strengthening the database model, enforcing strict validation rules, and improving backend security to ensure the system behaves predictably and safely under real-world conditions. 

I selected this artifact because it represents the core of the application’s integrity: the database schema, validation logic, and request-handling pipeline. These backend components determine how reliably the system stores information, how safely it processes user input, and how resilient it is to misuse. Enhancing this layer allowed me to demonstrate my ability to design intentional data models, enforce business rules through Mongoose validation, and apply security-first thinking through rate limiting and unknown-field rejection. These improvements elevate the project from a classroom prototype to a more professional, production-ready application. 

### Backend and Database Enhancements

The most significant improvements in this enhancement cycle centered on the database model and request validation. I updated the Mongoose schema to enforce a stricter and more meaningful document structure by adding required fields, enums, trimming rules, and type constraints. For example, the animal_type field now accepts only specific values: 

	animal_type: { 
   		type: String, 
   		required: true, 
   		unique: false, 
   		trim: false, 
   		enum: [‘Dog’, ‘Cat’, ‘Bird’, ‘Other’] 
	}, 

This ensures that only valid, intentional data enters the database. I also enabled unknown-field rejection so that any extra or unexpected fields in a request are discarded before reaching MongoDB, preventing schema drift and reducing the risk of malicious payloads. 

To protect the API from excessive or automated requests, I implemented rate limiting on sensitive routes such as the Create Animal endpoint:
	
	const createAnimalLimiter = rateLimit({ 
   		windowMs: 60 * 1000, 
   		max: 10,  
	   message: { 
    	  error: “Too many create attempts. Please slow down.” 
   	} 
	}); 

This ensures that even under high request volume or automated misuse, the system remains stable and responsive. 
Validated Request Dataflow

When a user submits the Create Animal form, the request moves through a structured validation pipeline before any data is written to MongoDB. The process begins in the Angular frontend, where the form collects user input and sends it to the Express backend through a POST request. As soon as the request reaches the server, it is first evaluated by the rate limiting middleware, which ensures the user has not exceeded the allowed number of create attempts within the current time window. If the request is permitted, it then passes through middleware that strips out any fields not defined in the Mongoose schema, preventing accidental or malicious data from entering the system. After this cleanup step, the sanitized request is handed to the Mongoose model, which enforces all schema rules, including required fields, enum constraints, type checks, and trimming behavior. Only when the request satisfies every validation rule does Mongoose allow the document to be inserted into the database. For example, a well-formed request containing a valid animal_type, a recognized breed, and a properly formatted age value is accepted and stored, while any request containing invalid types, missing fields, or disallowed values, is rejected with a clear error message. This layered approach ensures that every record entering the database is intentional, consistent, and aligned with the application’s data model. 

### Testing Validation and Rate Limiting
	
To verify that the enhanced validation rules and rate limiting protections were functioning correctly, I conducted structured backend tests using two custom Node.js scripts: validateSchema.js and cleanupTestData.js. The validateSchema script connects directly to MongoDB and attempts to insert a series of controlled test documents, some valid and others intentionally malformed documents, to confirm that the Mongoose model enforces all schema rules as expected. These tests included invalid enum values, negative numeric ranges, missing required fields, duplicate IDs, incorrect data types, and even a custom validator that rejects empty breed values. Each case produced clear success or failure logs, allowing me to confirm that the schema correctly accepted valid documents and rejected invalid ones. After each test run, the cleanupTestData script removed all temporary records created during validation, ensuring that the database remained clean and consistent for repeated testing cycles. 

I also tested the rate limiter by submitting rapid, repeated POST requests to confirm that excessive create attempts were blocked with the appropriate error message. Together, these scripts provided a reliable, repeatable way to validate the integrity of the schema and the effectiveness of the security enhancements, demonstrating that the backend now behaves predictably and safely under both normal and edge-case conditions. 

### Reflection and Outcomes

This enhancement strengthened my understanding of how critical strong validation, schema design, and secure request handling are in real-world applications. By restructuring the Mongoose model, enforcing strict validation rules, and adding rate limiting and unknown-field rejection, I gained deeper insight into how backend systems maintain data integrity and protect themselves from misuse. These improvements directly support Outcome Three, as they required me to apply algorithmic reasoning and structured problem-solving to design a predictable, rule-driven data pipeline. 

The process also reinforced the importance of clear communication and maintainable design, aligning with Outcome Two. Writing the validateSchema and cleanupTestData scripts required me to document test cases, produce meaningful console output, and structure the scripts so that another developer could easily understand and reuse them. These scripts also support Outcome One, because they create a collaborative environment where backend behavior is transparent, testable, and easy for teammates to verify.

Implementing rate limiting, rejecting unknown fields, and delaying the delete feature until proper authentication is available reflects a strong security mindset, directly supporting Outcome Five. These decisions demonstrate responsible engineering practices and an understanding that secure design often involves preventing unsafe actions rather than simply enabling features. 
	
Finally, the use of modern tools such as Node.js, Express, MongoDB, and Mongoose aligns with Outcome Four, as I applied industry-standard techniques to build a more reliable and professional backend. Working through the challenges of schema enforcement, validation failures, and repeated test cycles strengthened my confidence in full-stack development and deepened my understanding of how backend logic interacts with database constraints. 

Overall, this enhancement not only improved the quality and safety of the application but also reinforced the skills and mindset I will carry into future professional work. This artifact now serves as a strong representation of my backend engineering abilities within my ePortfolio and supports my long-term goal of building secure, maintainable, and professional-quality full-stack applications. The lessons learned in this enhancement will directly inform my future work as a software engineer. 

## Screenshots
![Schema Validation](assets/images/enh3-schema.png)

## Key Improvements
- Strict schema validation
- Unknown-field rejection
- Rate Limiting
- Backend testing scripts
