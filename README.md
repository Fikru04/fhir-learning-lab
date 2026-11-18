# HL7 FHIR R4 Learning Lab

## About This Repository

This repository documents my independent study and hands-on practice in
HL7 FHIR R4, healthcare interoperability, REST APIs, clinical terminology,
and FHIR validation.

My professional background includes HL7 v2.5.1 immunization messaging,
immunization information systems (IIS), and public health data standards.
I have also completed FHIR training through the CDC Public Health
Informatics Fellowship bootcamp.

This learning project builds on that training through structured study,
specification navigation, synthetic resource examples, practical API
exercises, and knowledge checks.

My current certification goal is the
**HL7 FHIR Foundational Implementer certification**.

> This repository documents learning and practice. It does not represent
> certification attainment or a production-ready implementation.

## Learning Objectives

- Understand FHIR resources, elements, cardinality, datatypes, and references.
- Distinguish FHIR datatypes from their JSON and XML representations.
- Create and inspect synthetic Patient, Observation, and Immunization resources.
- Practice FHIR REST API interactions using HAPI FHIR test environments.
- Interpret HTTP responses, resource versions, and OperationOutcome information.
- Explore search, Bundles, profiles, and implementation guides.
- Study terminology concepts including SNOMED CT, LOINC, RxNorm, CVX, and UCUM.
- Practice validation against applicable FHIR requirements.
- Explore FHIR use cases relevant to IIS and public health.

## Current Learning Progress

Learning progresses in curriculum module order. Completion means that the
module's instructional material and learning assessments have been completed;
it does not imply production implementation experience.

| Module | Topic | Status |
|---|---|---|
| 1 | What FHIR Is and Why It Exists | Completed |
| 2 | How to Read the FHIR Specification | Completed |
| 3 | JSON, XML, Datatypes and References | Completed |
| 4 | RESTful FHIR API Behavior | In progress — practical lab underway |

Later modules will be documented as they are reached.

## Completed Learning: Modules 1–3

### Module 1 — FHIR Foundations

Topics studied:

- FHIR as an HL7 interoperability standard
- Resource types versus resource instances
- Common clinical and administrative resources
- Logical resource IDs versus business identifiers
- FHIR in the context of existing HL7 v2 experience

### Module 2 — Reading the FHIR Specification

Topics practiced:

- Resource Content tables
- Cardinality and datatype interpretation
- Choice elements such as `value[x]` and `effective[x]`
- Resource scope and boundaries
- Search Parameters sections
- Resource-specific operations
- Must Support versus minimum cardinality

### Module 3 — JSON, XML, Datatypes and References

Topics studied and practiced:

- Primitive and complex datatype representation
- JSON objects, arrays, strings, numbers, and booleans
- Repeating elements in JSON and XML
- FHIR XML primitive value attributes and element ordering
- Identifier, Coding, CodeableConcept, and Reference
- HumanName, Address, Quantity, Period, and Attachment
- Relative, absolute, contained, and identifier-based references
- References resolved through Bundle entry `fullUrl` values
## Learning Assessments

These are educational knowledge checks and remediation exercises completed
during independent study. They are not official HL7 certification exams
or validated predictors of certification performance.

| Module / Checkpoint | Result | Outcome |
|---|---|---|
| Module 1 — Foundations | Knowledge checks and targeted remediation completed | Completed |
| Module 2 — Reading the FHIR Specification | 9/10 — 90% | Passed |
| Module 3 — JSON/XML representation checkpoint | 8/10 — 80% | Passed |
| Module 3 — Final closeout assessment | 8/10 — 80% | Passed; targeted remediation followed |
| Module 3 — Targeted remediation | 9/10 — 90% | Completed; module closed |
| Module 4 — RESTful FHIR API Behavior | Ongoing knowledge checks and practical exercises | Final assessment pending |

### Assessment Approach

- Complete knowledge checks during each module.
- Review incorrect answers and explain the underlying distinction.
- Use fresh remediation questions to reinforce missed concepts.
- Combine assessment results with hands-on exercises before closing a module.
- Carry recurring learning gaps into later practice.

The study target for module closeout is at least 80%, with targeted
remediation for important foundational gaps.
### Key Distinctions Reinforced

| Concept | Distinction |
|---|---|
| Logical ID vs Identifier | Resource identity on a FHIR server vs business identification |
| FHIR datatype vs JSON representation | For example, Quantity vs JSON object |
| Coding vs CodeableConcept | One code-system/code structure vs a concept containing codings and/or text |
| Reference vs reference form | The linking datatype vs how its target is expressed |
| Cardinality vs instance count | A repeating element uses a JSON array even when only one item is present |

## Current Module: RESTful FHIR API Behavior

Topics covered so far:

- HTTP method versus FHIR interaction
- CREATE, READ, UPDATE, and DELETE
- READ versus VREAD
- Logical IDs versus version IDs
- Instance, type, and system history
- READ versus SEARCH
- Search responses as `searchset` Bundles
- Capabilities interaction and CapabilityStatement
- System-, type-, and instance-level operations
- HTTP status families and selected status codes
- Conditional create using `If-None-Exist`
- Conditional update using search criteria
- Troubleshooting using HTTP status, headers, and OperationOutcome

These concepts are being reinforced through a practical HAPI FHIR R4 lab.

## Practical Lab: Synthetic Patient Lifecycle

**Environment:** HAPI FHIR R4 public test server  
**Data:** Fictional educational Patient record only

| Step | Request Pattern | Observed Result | Status |
|---|---|---|---|
| CREATE | `POST [base]/Patient` | `201 Created`; server assigned a logical ID; version `1` | Completed |
| READ | `GET [base]/Patient/{id}` | `200 OK`; retrieved the current Patient representation | Completed |
| UPDATE | `PUT [base]/Patient/{id}` | `200 OK`; logical ID unchanged; version changed to `2` | Completed |
| VREAD | `GET [base]/Patient/{id}/_history/1` | Retrieve and inspect the original version | Pending |
| Instance History | `GET [base]/Patient/{id}/_history` | Inspect the resource's history Bundle | Pending |

The completed UPDATE changed the fictional Patient's `gender` from
`unknown` to `female`.

### Lessons Demonstrated

- A normal CREATE lets the server assign the logical ID.
- READ retrieves the current resource representation.
- In this lab, UPDATE preserved the logical ID and produced a new version.
- Response headers and resource metadata help identify resource versions.
- VREAD retrieves a specified version rather than the current version.
- Instance History and VREAD are different interactions.

> Public test-server data may change or be removed. Recorded results describe
> what was observed during the exercise, not a guarantee of current server state.

## Planned Portfolio Exercises

The following are portfolio themes, not replacements for the curriculum's
module sequence:

1. FHIR foundations and JSON/XML
2. Core clinical resources
3. REST APIs and search
4. Bundles and transactions
5. Clinical terminology
6. Profiles and validation
7. Public health interoperability
8. Independent capstone project

## Evidence and Documentation

As artifacts are prepared and reviewed, this repository will include:

- Original learning notes and concept summaries
- Synthetic FHIR JSON examples
- Request and response examples
- Selected screenshots with explanatory captions
- Troubleshooting notes
- Reflections on mistakes and corrections
- Links to authoritative specifications and implementation guides

Only work actually completed will be labeled as completed.
Planned exercises will remain clearly identified as planned.

## Tools and References

- HL7 FHIR R4 Specification
- HAPI FHIR Public Test Server
- Visual Studio Code
- US Core Implementation Guide, when relevant to an exercise

FHIR release and implementation-guide versions will be recorded for
exercises that depend on them.

## Data Safety and Source Materials

- Examples use fictional data only.
- No patient information, credentials, access tokens, or confidential
  organizational information will be published.
- Trainer slides and other third-party training materials will not be
  redistributed without permission or an applicable license.
- Learning notes and examples will be written independently, with references
  to source specifications where appropriate.

## Disclaimer

This is an independent educational portfolio, not an official CDC or HL7
project.

No patient information, confidential government materials, or internal
project documents are included.
