# API Usage Examples

## 1. Overview
This document provides practical usage examples for the Conference Room Booking System API.
It demonstrates how a client application would authenticate, manage conference rooms,
create and cancel bookings, and check room availability. These examples are based on the
OpenAPI specification and are intended for documentation purposes only, as no backend
implementation exists.

---

## 2. Authentication
The API uses token-based authentication with a Bearer token. All endpoints require the
client to include an access token in the `Authorization` header.

Since this project focuses on API documentation, the authentication service is assumed
and not implemented.

**Authentication Header Example:**
```http
Authorization: Bearer <access-token>
3. Room Management
3.1 Retrieve All Conference Rooms
Retrieves a list of all conference rooms available in the system.
Example Request:
Copy code
Http
GET /rooms
Authorization: Bearer <access-token>
Example Response (200 OK):
Copy code
Json
[
  {
    "id": "room-101",
    "name": "Conference Room A",
    "capacity": 10,
    "equipment": ["Projector", "Whiteboard"]
  }
]
3.2 Retrieve a Single Conference Room
Retrieves details of a specific conference room.
Example Request:
Copy code
Http
GET /rooms/room-101
Authorization: Bearer <access-token>
Example Response (200 OK):
Copy code
Json
{
  "id": "room-101",
  "name": "Conference Room A",
  "capacity": 10,
  "equipment": ["Projector", "Whiteboard"]
}
3.3 Create a Conference Room
Creates a new conference room.
Example Request:
Copy code
Http
POST /rooms
Authorization: Bearer <access-token>
Content-Type: application/json
Example Request Body:
Copy code
Json
{
  "name": "Conference Room C",
  "capacity": 8,
  "equipment": ["TV Screen"]
}
Example Response (201 Created):
Copy code
Json
{
  "id": "room-103",
  "name": "Conference Room C",
  "capacity": 8,
  "equipment": ["TV Screen"]
}
3.4 Update a Conference Room
Updates details of an existing conference room.
Example Request:
Copy code
Http
PUT /rooms/room-101
Authorization: Bearer <access-token>
Content-Type: application/json
Example Response (200 OK):
Copy code
Json
{
  "id": "room-101",
  "name": "Conference Room A",
  "capacity": 12,
  "equipment": ["Projector", "Whiteboard"]
}
3.5 Delete a Conference Room
Deletes a conference room from the system.
Example Request:
Copy code
Http
DELETE /rooms/room-101
Authorization: Bearer <access-token>
Example Response (204 No Content)
4. Bookings
4.1 Retrieve All Bookings
Retrieves a list of all room bookings.
Example Request:
Copy code
Http
GET /bookings
Authorization: Bearer <access-token>
Example Response (200 OK):
Copy code
Json
[
  {
    "bookingId": "booking-5001",
    "roomId": "room-101",
    "date": "2026-02-01",
    "startTime": "10:00",
    "endTime": "11:00",
    "bookedBy": "user@example.com"
  }
]
4.2 Create a Booking
Creates a booking for a conference room.
Example Request:
Copy code
Http
POST /bookings
Authorization: Bearer <access-token>
Content-Type: application/json
Example Request Body:
Copy code
Json
{
  "roomId": "room-101",
  "date": "2026-02-01",
  "startTime": "10:00",
  "endTime": "11:00",
  "bookedBy": "user@example.com"
}
Example Response (201 Created):
Copy code
Json
{
  "bookingId": "booking-5002",
  "roomId": "room-101",
  "status": "confirmed"
}
4.3 Cancel a Room Booking
Cancels an existing booking for a conference room.
Example Request:
Copy code
Http
DELETE /bookings/booking-5002
Authorization: Bearer <access-token>
Example Response (204 No Content)
5. Availability
5.1 Check Room Availability
Checks whether a conference room is available for a given date and time range.
Example Request:
Copy code
Http
GET /rooms/availability?date=2026-02-01&startTime=10:00&endTime=11:00
Authorization: Bearer <access-token>
Example Response (200 OK):
Copy code
Json
{
  "roomId": "room-101",
  "available": false
}
6. Error Handling
The API uses standard HTTP status codes to indicate errors.
Room Not Found (404 Not Found):
Copy code
Json
{
  "error": "Room not found"
}
Booking Conflict (409 Conflict):
Copy code
Json
{
  "error": "Room is already booked for the selected time slot"
}
Unauthorized Access (401 Unauthorized):
Copy code
Json
{
  "error": "Authentication token is missing or invalid"
}
