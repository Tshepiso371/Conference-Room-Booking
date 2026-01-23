# Demo Script – API Documentation & Contract Validation

## Topic
Conference Room Booking System API
**Focus:** OpenAPI, Swagger UI, Postman  

---

## Demo Step 1: OpenAPI Specification

**Action:**
- Open the repository (https://github.com/Tshepiso371/Conference-Room-Booking)

- Navigate to `docs/api-documentation.yaml`

**What is shown:**
- API metadata (title, description, version)
- Server definitions (staging and production)
- Security scheme (Bearer token)
- Reusable schemas (Room, Booking, Error)

**Purpose:**
- Demonstrate that the API contract is clearly defined without backend code

---

## Demo Step 2: Swagger UI Rendering

**Action:**
- Open Swagger UI
- Load the OpenAPI specification

**What is shown:**
- Rendered API documentation
- Endpoints grouped by domain:
  - Rooms
  - Bookings
  - Availability
- Request parameters and response models

**Purpose:**
- Show how OpenAPI is transformed into interactive documentation

---

## Demo Step 3: Endpoint Inspection

**Action:**
- Select the `GET /rooms` endpoint

**What is shown:**
- Endpoint description
- Example response
- HTTP status codes

**Purpose:**
- Show how expected API behaviour is clearly documented

---

## Demo Step 4: Postman Contract Import

**Action:**
- Open Postman
- View the collection generated from the OpenAPI specification

**What is shown:**
- Automatically created requests
- Folder structure matching API endpoints

**Purpose:**
- Demonstrate reuse of the API contract across tools

---

## Demo Step 5: Contract Validation Test

**Action:**
- Open a request (e.g. `GET /rooms`)
- Run the request
- View the Tests tab

**What is shown:**
- Passing test result
- Status code validation (200 OK)

**Purpose:**
- Validate that the API behaves as defined in the contract


## Demo Conclusion

**Summary:**
- OpenAPI defines the API contract
- Swagger UI provides clear documentation
- Postman validates the contract through tests
- This approach reduces integration risk and improves collaboration

