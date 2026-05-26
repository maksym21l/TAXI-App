# API Documentation — Taxi App

> This document describes the key REST API endpoints for the Taxi App platform.  
> The API is used by the passenger mobile app, driver mobile app, and admin web panel.

---

## Base URL

```
https://api.taxiapp.com/v1
```

---

## Authentication

All endpoints (except registration and login) require a Bearer token in the request header.

```
Authorization: Bearer <token>
```

Tokens are issued after successful login and expire after 24 hours.  
If a token is missing or expired, the server returns `401 Unauthorized`.

---

## Endpoints Overview

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | /auth/register | Register a new user (passenger or driver) | No |
| POST | /auth/login | Log in and receive access token | No |
| POST | /auth/logout | End current session | Yes |
| POST | /rides/request | Create a new ride request | Yes |
| GET | /rides/{id} | Get ride details by ID | Yes |
| PATCH | /rides/{id}/cancel | Cancel an active ride | Yes |
| PATCH | /rides/{id}/complete | Mark ride as completed (driver only) | Yes |
| GET | /drivers/nearby | Get list of nearby available drivers | Yes |
| POST | /payments | Process payment for a ride | Yes |
| POST | /ratings | Submit a rating after ride completion | Yes |
| GET | /rides/history | Get ride history for current user | Yes |

---

## Endpoint Details

---

### POST /auth/register

Register a new passenger or driver account.

**Request body:**
```json
{
  "role": "passenger",
  "first_name": "Anna",
  "last_name": "Kovalenko",
  "phone": "+380991234567",
  "password": "securepassword123"
}
```

> For drivers, additional fields are required: `vehicle_brand`, `vehicle_model`, `plate_number`, `vehicle_category`.

**Response `201 Created`:**
```json
{
  "id": "usr_001",
  "role": "passenger",
  "phone": "+380991234567",
  "status": "active"
}
```

**Possible errors:**

| Status | Reason |
|--------|--------|
| 400 | Missing required fields |
| 409 | Phone number already registered |

---

### POST /auth/login

Log in with phone number and password.

**Request body:**
```json
{
  "phone": "+380991234567",
  "password": "securepassword123"
}
```

**Response `200 OK`:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expires_at": "2025-06-01T12:00:00Z",
  "user_id": "usr_001",
  "role": "passenger"
}
```

**Possible errors:**

| Status | Reason |
|--------|--------|
| 400 | Missing phone or password |
| 401 | Invalid credentials |

---

### POST /rides/request

Create a new ride request. The system searches for a nearby available driver automatically.

**Request body:**
```json
{
  "pickup_location": "вул. Хрещатик, 1, Київ",
  "destination_location": "вул. Велика Васильківська, 100, Київ",
  "vehicle_category": "comfort",
  "payment_method": "card"
}
```

**Response `201 Created`:**
```json
{
  "ride_id": "ride_042",
  "status": "searching",
  "estimated_price": 95.00,
  "currency": "UAH",
  "vehicle_category": "comfort",
  "payment_method": "card"
}
```

**Possible errors:**

| Status | Reason |
|--------|--------|
| 400 | Invalid or unrecognized address |
| 404 | No available drivers nearby |
| 402 | Card payment declined |

---

### GET /rides/{id}

Get the current status and details of a specific ride.

**Response `200 OK`:**
```json
{
  "ride_id": "ride_042",
  "status": "in_progress",
  "pickup_location": "вул. Хрещатик, 1, Київ",
  "destination_location": "вул. Велика Васильківська, 100, Київ",
  "driver": {
    "name": "Олексій М.",
    "rating": 4.8,
    "vehicle": "Toyota Camry • АА1234ВВ"
  },
  "price": 95.00,
  "payment_method": "card"
}
```

**Ride status values:**

| Status | Meaning |
|--------|---------|
| `searching` | System is looking for a driver |
| `accepted` | Driver accepted the order |
| `in_progress` | Ride is active |
| `completed` | Ride finished successfully |
| `cancelled` | Ride was cancelled |

---

### POST /ratings

Submit a rating after a ride is completed. Both passengers and drivers can rate each other.

**Request body:**
```json
{
  "ride_id": "ride_042",
  "score": 5,
  "comment": "Дуже приємна поїздка, водій пунктуальний"
}
```

**Response `201 Created`:**
```json
{
  "rating_id": "rat_011",
  "ride_id": "ride_042",
  "score": 5,
  "saved": true
}
```

**Possible errors:**

| Status | Reason |
|--------|--------|
| 400 | Score out of range (must be 1–5) |
| 403 | Ride is not completed — rating not allowed |
| 409 | Rating already submitted for this ride |

---

## General Error Format

All errors follow the same response structure:

```json
{
  "error": {
    "code": "RIDE_NOT_FOUND",
    "message": "Ride with the specified ID does not exist.",
    "status": 404
  }
}
```

---

## Notes

- All timestamps are in **ISO 8601** format (`2025-05-22T10:00:00Z`)
- All monetary values are in **UAH** unless specified otherwise
- Driver accounts require administrator verification before they can go online (see FR-02, BR-08)
- Ratings can only be submitted for rides with `completed` status (see BR-07)
