# Book Review Service API

## Overview

This document describes the API for a simple book review service.

The API allows clients to retrieve information about books and create reviews for them.

This API is used in the Book Review application described in the User Guide.

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
```

### Successful Response

**Status:** `200 OK`

Returns a book object.

```json
{
  "id": 15,
  "title": "Clean Code",
  "author": "Robert C. Martin",
  "genre": "Programming",
  "rating": 4.8,
  "published_year": 2008
}
```

### Response Fields

| Field          | Type    | Description            |
|----------------|---------|------------------------|
| id             | integer | Unique book identifier |
| title          | string  | Book title             |
| author         | string  | Book author            |
| genre          | string  | Book genre             |
| rating         | number  | Average book rating    |
| published_year | integer | Year of publication    |

### Error Responses

#### 401 Unauthorized

```json
{
  "error": "unauthorized",
  "message": "Authentication is required"
}
```

#### 404 Not Found

```json
{
  "error": "not_found",
  "message": "Book not found"
}
```

---

## Get Books

### Endpoint

`GET /api/v1/books`

### Description

Returns a list of books.

This endpoint can be used to display books in the catalog and filter them by genre or author.

### Headers

| Header        | Required | Description                         |
|---------------|----------|-------------------------------------|
| Authorization | Yes      | Bearer token used for authentication |

### Query Parameters

| Parameter | Type   | Description            |
|-----------|--------|------------------------|
| genre     | string | Filter books by genre  |
| author    | string | Filter books by author |

### Request Example

```http
GET /api/v1/books?genre=Programming HTTP/1.1
Host: api.bookreviews.local
Authorization: Bearer <token>
```

### Successful Response

**Status:** `200 OK`

Returns a list of book objects.

```json
[
  {
    "id": 15,
    "title": "Clean Code",
    "author": "Robert C. Martin",
    "genre": "Programming"
  },
  {
    "id": 22,
    "title": "The Pragmatic Programmer",
    "author": "Andrew Hunt",
    "genre": "Programming"
  }
]
```

### Error Responses

#### 401 Unauthorized

```json
{
  "error": "unauthorized",
  "message": "Authentication is required"
}
```

---

## Create Review

### Endpoint

`POST /api/v1/reviews`

### Description

Creates a new review for a book.

Use this endpoint when a user submits feedback and rating for a book.

### Headers

| Header        | Required | Description                         |
|---------------|----------|-------------------------------------|
| Authorization | Yes      | Bearer token used for authentication |
| Content-Type  | Yes      | application/json                    |

### Request Body

| Field    | Type    | Required | Description            |
|----------|---------|----------|------------------------|
| book_id  | integer | Yes      | Identifier of the book |
| reviewer | string  | Yes      | Reviewer name          |
| rating   | integer | Yes      | Rating from 1 to 5     |
| comment  | string  | No       | Review text            |

### Request Example

```http
POST /api/v1/reviews HTTP/1.1
Host: api.bookreviews.local
Authorization: Bearer <token>
Content-Type: application/json
```

```json
{
  "book_id": 15,
  "reviewer": "Maria",
  "rating": 5,
  "comment": "Clear and practical book for developers."
}
```

### Successful Response

**Status:** `201 Created`

```json
{
  "id": 101,
  "book_id": 15,
  "reviewer": "Maria",
  "rating": 5,
  "comment": "Clear and practical book for developers.",
  "created_at": "2026-04-17T12:30:00Z"
}
```

### Error Responses

#### 400 Bad Request

```json
{
  "error": "invalid_request",
  "message": "Rating must be between 1 and 5"
}
```

#### 404 Not Found

```json
{
  "error": "not_found",
  "message": "Book not found"
}
```

---

## Notes

- All responses are returned in JSON format
- Authentication is required for all endpoints
- The API follows REST principles
- Date and time values use UTC and ISO 8601 format
