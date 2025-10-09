# NCMH Platform - REST API Specification

> **Status:** 🚧 Future Implementation - This API is planned for future backend integration

## Table of Contents

- [Overview](#overview)
- [Authentication](#authentication)
- [Endpoints](#endpoints)
  - [User Management](#user-management)
  - [Sentiment Analysis](#sentiment-analysis)
  - [Chat Services](#chat-services)
  - [Appointments](#appointments)
  - [Facilities](#facilities)
  - [Emergency Services](#emergency-services)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)
- [Webhooks](#webhooks)
- [SDKs](#sdks)

---

## Overview

### Base URL
```
Production: https://api.ncmh-platform.sa/v1
Staging: https://staging-api.ncmh-platform.sa/v1
Development: http://localhost:3000/v1
```

### API Version
- **Current Version:** v1
- **API Versioning:** URI-based (`/v1`, `/v2`)
- **Deprecation Notice:** 6 months advance notice for breaking changes

### Content Type
All requests and responses use JSON:
```
Content-Type: application/json
```

### Date Format
ISO 8601 format:
```
2025-10-08T14:30:00Z
```

---

## Authentication

### Overview
The API uses JWT (JSON Web Tokens) for authentication.

### Authentication Flow

```
1. User Login → POST /auth/login
2. Receive JWT Token
3. Include token in subsequent requests
4. Token expires after 24 hours
5. Refresh token before expiry
```

### Obtaining a Token

**Endpoint:** `POST /auth/login`

**Request:**
```json
{
  "username": "user@example.com",
  "password": "SecurePassword123!",
  "language": "english"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expiresIn": 86400,
    "user": {
      "id": "usr_123456",
      "username": "user@example.com",
      "preferredLanguage": "english",
      "createdAt": "2025-10-08T14:30:00Z"
    }
  }
}
```

### Using the Token

Include the JWT token in the Authorization header:

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### Refreshing Tokens

**Endpoint:** `POST /auth/refresh`

**Request:**
```json
{
  "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expiresIn": 86400
  }
}
```

### Anonymous Access

Some endpoints support anonymous access:
- `GET /facilities` - Public facility information
- `POST /emergency/call` - Emergency services (no auth required)
- `GET /resources` - Public wellness resources

---

## Endpoints

### User Management

#### Register New User

**Endpoint:** `POST /users/register`

**Authentication:** None required

**Request:**
```json
{
  "firstName": "Ahmed",
  "lastName": "Al-Saud",
  "email": "ahmed@example.com",
  "username": "ahmed123",
  "password": "SecurePass123!",
  "preferredLanguage": "arabic",
  "acceptedTerms": true
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "userId": "usr_789012",
    "email": "ahmed@example.com",
    "verificationSent": true,
    "message": "Please check your email to verify your account"
  }
}
```

**Status Codes:**
- `201` - Created
- `400` - Bad Request (validation errors)
- `409` - Conflict (email/username already exists)

---

#### Verify Email

**Endpoint:** `POST /users/verify`

**Authentication:** None required

**Request:**
```json
{
  "email": "ahmed@example.com",
  "verificationCode": "123456"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "verified": true,
    "message": "Email verified successfully"
  }
}
```

---

#### Get User Profile

**Endpoint:** `GET /users/me`

**Authentication:** Required

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "usr_123456",
    "username": "ahmed123",
    "email": "ahmed@example.com",
    "firstName": "Ahmed",
    "lastName": "Al-Saud",
    "preferredLanguage": "arabic",
    "createdAt": "2025-10-08T14:30:00Z",
    "lastLogin": "2025-10-08T16:45:00Z",
    "settings": {
      "notifications": true,
      "emergencyContact": "+966501234567"
    }
  }
}
```

---

#### Update User Profile

**Endpoint:** `PATCH /users/me`

**Authentication:** Required

**Request:**
```json
{
  "firstName": "Ahmed",
  "preferredLanguage": "english",
  "settings": {
    "notifications": false
  }
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "usr_123456",
    "updated": true,
    "message": "Profile updated successfully"
  }
}
```

---

### Sentiment Analysis

#### Analyze Sentiment

**Endpoint:** `POST /sentiment/analyze`

**Authentication:** Optional (enhanced results with auth)

**Request:**
```json
{
  "feeling": "anxiety",
  "details": "I've been feeling overwhelmed with work stress and can't sleep well",
  "voiceRecording": null,
  "anonymous": false
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "analysisId": "sa_345678",
    "sentiment": "negative",
    "score": -5,
    "urgencyLevel": "moderate",
    "recommendations": [
      {
        "type": "tier2",
        "title": "Connect with a Therapist",
        "description": "Your symptoms suggest you could benefit from professional support",
        "action": "schedule_appointment"
      }
    ],
    "keywords": ["anxiety", "overwhelmed", "stress", "sleep"],
    "timestamp": "2025-10-08T17:00:00Z"
  }
}
```

**Status Codes:**
- `200` - Success
- `400` - Invalid input
- `429` - Rate limit exceeded

---

#### Get Sentiment History

**Endpoint:** `GET /sentiment/history`

**Authentication:** Required

**Query Parameters:**
- `limit` (optional): Number of records (default: 10, max: 100)
- `offset` (optional): Pagination offset
- `startDate` (optional): Filter from date
- `endDate` (optional): Filter to date

**Response:**
```json
{
  "success": true,
  "data": {
    "analyses": [
      {
        "id": "sa_345678",
        "sentiment": "negative",
        "score": -5,
        "feeling": "anxiety",
        "timestamp": "2025-10-08T17:00:00Z"
      }
    ],
    "pagination": {
      "total": 25,
      "limit": 10,
      "offset": 0,
      "hasMore": true
    }
  }
}
```

---

### Chat Services

#### Start Chat Session

**Endpoint:** `POST /chat/sessions`

**Authentication:** Optional

**Request:**
```json
{
  "initialMessage": "I need help with anxiety",
  "language": "english",
  "anonymous": true
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "chat_567890",
    "botResponse": "Hello! I'm here to help you with anxiety...",
    "suggestedActions": [
      "breathing_exercise",
      "connect_therapist",
      "view_resources"
    ],
    "createdAt": "2025-10-08T17:05:00Z"
  }
}
```

---

#### Send Chat Message

**Endpoint:** `POST /chat/sessions/:sessionId/messages`

**Authentication:** Optional

**Request:**
```json
{
  "message": "I've been having panic attacks",
  "timestamp": "2025-10-08T17:06:00Z"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "messageId": "msg_123456",
    "botResponse": {
      "text": "I understand you're experiencing panic attacks. That must be very difficult...",
      "sentiment": "crisis_detected",
      "suggestedActions": [
        {
          "type": "emergency",
          "label": "Call Crisis Hotline",
          "action": "tel:920033360"
        },
        {
          "type": "resource",
          "label": "Breathing Exercise",
          "action": "view_breathing_guide"
        }
      ]
    },
    "timestamp": "2025-10-08T17:06:05Z"
  }
}
```

---

#### Get Chat History

**Endpoint:** `GET /chat/sessions/:sessionId/messages`

**Authentication:** Required (owner only)

**Response:**
```json
{
  "success": true,
  "data": {
    "sessionId": "chat_567890",
    "messages": [
      {
        "id": "msg_123456",
        "role": "user",
        "content": "I need help with anxiety",
        "timestamp": "2025-10-08T17:05:00Z"
      },
      {
        "id": "msg_123457",
        "role": "bot",
        "content": "Hello! I'm here to help you...",
        "timestamp": "2025-10-08T17:05:02Z"
      }
    ]
  }
}
```

---

### Appointments

#### Get Available Slots

**Endpoint:** `GET /appointments/availability`

**Authentication:** Required

**Query Parameters:**
- `specialization` (optional): therapist, psychiatrist, counselor
- `date` (optional): YYYY-MM-DD
- `city` (optional): riyadh, jeddah, dammam

**Response:**
```json
{
  "success": true,
  "data": {
    "availableSlots": [
      {
        "slotId": "slot_111111",
        "therapist": {
          "id": "ther_222222",
          "name": "Dr. Sarah Al-Ahmad",
          "specialization": "Anxiety Disorders",
          "rating": 4.8,
          "languages": ["arabic", "english"]
        },
        "dateTime": "2025-10-10T10:00:00Z",
        "duration": 60,
        "type": "video",
        "cost": 0
      }
    ]
  }
}
```

---

#### Book Appointment

**Endpoint:** `POST /appointments`

**Authentication:** Required

**Request:**
```json
{
  "slotId": "slot_111111",
  "reason": "Anxiety management",
  "preferredLanguage": "english",
  "notes": "First time seeking therapy"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "appointmentId": "apt_333333",
    "status": "confirmed",
    "therapist": {
      "name": "Dr. Sarah Al-Ahmad",
      "specialization": "Anxiety Disorders"
    },
    "dateTime": "2025-10-10T10:00:00Z",
    "duration": 60,
    "type": "video",
    "meetingLink": "https://meet.ncmh-platform.sa/room/apt_333333",
    "confirmationSent": true
  }
}
```

---

#### Cancel Appointment

**Endpoint:** `DELETE /appointments/:appointmentId`

**Authentication:** Required

**Request:**
```json
{
  "reason": "Schedule conflict",
  "requestReschedule": true
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "appointmentId": "apt_333333",
    "status": "cancelled",
    "refund": "full",
    "message": "Appointment cancelled successfully"
  }
}
```

---

### Facilities

#### Get All Facilities

**Endpoint:** `GET /facilities`

**Authentication:** None required

**Query Parameters:**
- `city` (optional): Filter by city
- `type` (optional): hospital, clinic, center
- `services` (optional): Comma-separated services

**Response:**
```json
{
  "success": true,
  "data": {
    "facilities": [
      {
        "id": "fac_444444",
        "name": "Al-Amal Hospital - Riyadh",
        "type": "hospital",
        "city": "riyadh",
        "location": {
          "lat": 24.7136,
          "lng": 46.6753,
          "address": "King Fahd Road, Riyadh"
        },
        "services": [
          "psychiatric_care",
          "addiction_treatment",
          "emergency_services"
        ],
        "contact": {
          "phone": "+966112345678",
          "email": "info@alamal-riyadh.sa",
          "website": "https://www.moh.gov.sa"
        },
        "hours": {
          "emergency": "24/7",
          "clinic": "08:00-16:00"
        },
        "languages": ["arabic", "english"]
      }
    ],
    "total": 8
  }
}
```

---

#### Search Facilities by Location

**Endpoint:** `POST /facilities/search`

**Authentication:** None required

**Request:**
```json
{
  "latitude": 24.7136,
  "longitude": 46.6753,
  "radius": 50,
  "services": ["emergency_services"]
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "facilities": [
      {
        "id": "fac_444444",
        "name": "Al-Amal Hospital - Riyadh",
        "distance": 2.3,
        "estimatedTime": "8 minutes",
        "location": {
          "lat": 24.7136,
          "lng": 46.6753
        }
      }
    ],
    "searchCenter": {
      "lat": 24.7136,
      "lng": 46.6753
    },
    "radius": 50
  }
}
```

---

### Emergency Services

#### Trigger Emergency Protocol

**Endpoint:** `POST /emergency/alert`

**Authentication:** None required (for accessibility)

**Request:**
```json
{
  "type": "suicide_risk",
  "location": {
    "lat": 24.7136,
    "lng": 46.6753
  },
  "contactNumber": "+966501234567",
  "message": "Need immediate help"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "alertId": "emg_555555",
    "status": "dispatched",
    "hotlines": [
      {
        "name": "Saudi Mental Health Hotline",
        "number": "920033360",
        "available": "24/7"
      },
      {
        "name": "Emergency Services",
        "number": "997",
        "available": "24/7"
      }
    ],
    "nearestFacilities": [
      {
        "name": "Al-Amal Hospital - Riyadh",
        "distance": 2.3,
        "phone": "+966112345678",
        "emergency": true
      }
    ],
    "timestamp": "2025-10-08T17:30:00Z"
  }
}
```

**Status Codes:**
- `200` - Alert created
- `202` - Alert queued for processing
- `503` - Service temporarily unavailable

---

## Error Handling

### Error Response Format

All errors follow this structure:

```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "details": {
      "field": "Additional context"
    },
    "timestamp": "2025-10-08T17:00:00Z",
    "requestId": "req_123456"
  }
}
```

### Common Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `INVALID_REQUEST` | 400 | Malformed request |
| `UNAUTHORIZED` | 401 | Missing or invalid token |
| `FORBIDDEN` | 403 | Insufficient permissions |
| `NOT_FOUND` | 404 | Resource not found |
| `CONFLICT` | 409 | Resource already exists |
| `RATE_LIMIT_EXCEEDED` | 429 | Too many requests |
| `INTERNAL_ERROR` | 500 | Server error |
| `SERVICE_UNAVAILABLE` | 503 | Temporary outage |

### Error Examples

**Validation Error:**
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": {
      "email": "Invalid email format",
      "password": "Password must be at least 8 characters"
    }
  }
}
```

**Authentication Error:**
```json
{
  "success": false,
  "error": {
    "code": "UNAUTHORIZED",
    "message": "Invalid or expired token",
    "details": {
      "expiredAt": "2025-10-08T16:00:00Z"
    }
  }
}
```

---

## Rate Limiting
