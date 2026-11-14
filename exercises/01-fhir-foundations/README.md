# Module 1 — FHIR Foundations

## Learning Objectives
- Understand FHIR resources and JSON structure.
- Identify resourceType, id, and identifier.
- Understand resource references and basic datatypes.
- Create a fictional Patient resource.

## Planned Hands-On Exercise
Create a synthetic FHIR R4 Patient resource, inspect its JSON structure, and validate it against the FHIR specification.

## Status
Not yet completed.

## Evidence and Lessons Learned
### FHIR Validation Exercise

**Resource:** Synthetic FHIR R4 Patient (`patient-001.json`)

**Environment:** HAPI FHIR R4 public test server

**Actions performed:**
1. Retrieved the server CapabilityStatement using `GET /metadata`.
2. Searched Patient resources using `GET /Patient?_count=5`.
3. Read an individual Patient resource using `GET /Patient/{id}`.
4. Validated my synthetic Patient JSON using `$validate`.
5. Investigated a `dom-6` warning about a missing human-readable narrative.
6. Added a `text` element with XHTML narrative and validated again.

**Final result:** The server returned an `OperationOutcome` stating "No issues detected during validation."

**Lessons learned:** FHIR search returns a Bundle, while a read returns an individual resource. The logical `id` differs from a business `identifier`. Validation feedback can identify problems that should be corrected and retested.

**Note:** All data are fictional. This exercise does not establish conformance to every implementation guide.
### FHIR Create and Read Exercise

**Test environment:** HAPI FHIR R4 public server

**Create:** Submitted a fictional Patient resource using `POST /Patient`, without specifying a logical ID.

**Create result:** `HTTP 201 Created`. The server assigned Patient ID `737787` and resource version `1`.

**Read:** Retrieved the same resource using `GET /Patient/737787`.

**Read result:** `HTTP 200 OK`. Confirmed that the response contained the fictional patient's information, including business identifier `SYN-1001` and the human-readable narrative.

**Lessons learned:** A FHIR server can assign the logical `id` during creation. The server-assigned `id` differs from the Patient's business `identifier`. A successful read retrieves the stored resource by its logical ID.

**Note:** HAPI is a public demonstration server and may periodically remove test records. All patient details in this exercise are fictional.
