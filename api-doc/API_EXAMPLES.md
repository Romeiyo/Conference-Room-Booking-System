# API Usage Examples: Conference Room Booking System
This guide provides realistic usage examples for the Conference Room Booking API.

## 1. Authentication

**Request:**
`POST /auth/login`

**Body (JSON):**
```json
{
  "email": "user@example.com",
  "password": "SecurePass123!"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1Ni...",
  "tokenType": "Bearer",
  "expiresIn": 3600
}
```

## 2. Room Management

**Request:**
`GET /rooms?capacity=10`

**Response:**
```json
[
  {
    "id": 12,
    "name": "Boardroom A",
    "capacity": 10,
    "available": true
  }
]
```

## 3. Availability

**Request:**
`GET /availability?date=2026-01-22`

**Response:**
```json
[
  {
    "id": 12,
    "name": "Boardroom A",
    "capacity": 10
  }
]
```

## 4. Bookings

**Request:**
`POST /bookings`

**Response:**
```json
{
  "roomId": 12,
  "userId": 101,
  "startTime": "2026-01-22T14:00:00Z",
  "endTime": "2026-01-22T15:00:00Z"
}
```