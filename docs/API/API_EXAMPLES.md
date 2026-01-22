# API Usage Examples

## 1. Overview
This document provides usage examples for the Conference Room Booking  API.
It demonstrates how a client would  retrieve conference rooms,
create bookings, and check room availability. The examples are based on the OpenAPI


## 2. Authentication
The API assumes token-based authentication using a Bearer token. All protected endpoints
require the client to include an access token in the `Authorization` header.

Since this project focuses on API documentation, the authentication service is assumed
and not implemented.

**Authentication Details:**
- Authentication type: Bearer Token
- Token location: `Authorization` header
- Token format: `Bearer <access-token>`


 ## 3. Retrieve All Conference Rooms
This endpoint allows a client application to retrieve a list of all conference rooms
available in the system, including room capacity and available equipment.

Example Request:

GET /rooms
Authorization: Bearer <access-token>
Example Response (200 OK):

[
  {
    "id": "room-101",
    "name": "Conference Room A",
    "capacity": 10,
    "equipment": ["Projector", "Whiteboard"]
  },
  {
    "id": "room-102",
    "name": "Conference Room B",
    "capacity": 6,
    "equipment": ["TV Screen"]
  }
]


## 4. Create a Booking
This endpoint allows a client to create a new booking for a conference room at a specified
date and time.

Example Request:

POST /bookings
Authorization: Bearer <access-token>
Content-Type: application/json
Example Request Body:

{
  "roomId": "room-101",
  "date": "2026-02-01",
  "startTime": "10:00",
  "endTime": "11:00",
  "bookedBy": "user@example.com"
}
Example Response (201 Created):

{
  "bookingId": "booking-5001",
  "roomId": "room-101",
  "status": "confirmed"
}


## 5 Check Room Availability
This endpoint allows a client to check whether a specific conference room is available
for a given date and time range before making a booking.

Example Request:

GET /rooms/availability?date=2026-02-01&startTime=10:00&endTime=11:00
Authorization: Bearer <access-token>
Example Response (200 OK):

{
  "roomId": "room-101",
  "available": false
}
## 6. Error Handling
The API uses standard HTTP status codes to indicate errors when a request cannot be
processed successfully.

Room Already Booked (409 Conflict):

{
  "error": "Room is already booked for the selected time slot"
}
Invalid Request (400 Bad Request):

{
  "error": "Invalid request data"
}
Unauthorized Access (401 Unauthorized):

{
  "error": "Authentication token is missing or invalid"
}