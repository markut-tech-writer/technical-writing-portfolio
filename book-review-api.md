# Book Review Service API

## Overview

This document describes the API for a simple book review service.

The API allows clients to retrieve information about books and create reviews for them.

---

## Get Book by ID

### Endpoint

`GET /api/v1/books/{id}`

### Description

Returns detailed information about a book by its unique identifier.

This endpoint can be used to display book details in the application interface.

### Path Parameters

| Parameter | Type    | Required | Description            |
|-----------|---------|----------|------------------------|
| id        | integer | Yes      | Unique book identifier |

### Headers

| Header        | Required | Description                         |
|---------------|----------|-------------------------------------|
| Authorization | Yes      | Bearer token used for authentication |

### Request Example

```http
GET /api/v1/books/15 HTTP/1.1
Host: api.bookreviews.local
Authorization: Bearer <token>

### Successful Response

Status: 200 OK

{
  "id": 15,
  "title": "Clean Code",
  "author": "Robert C. Martin",
  "genre": "Programming",
  "rating": 4.8,
  "published_year": 2008
}

### Error Responses

401 Unauthorized

{
  "error": "unauthorized",
  "message": "Authentication is required"
}

