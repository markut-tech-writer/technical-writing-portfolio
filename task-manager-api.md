Markdown
# Task Manager API

## Overview

This document describes the main API methods for working with tasks in the Task Manager application.

The API allows clients to retrieve task details and create new tasks.

---

# Get Task by ID

## Endpoint

`GET /api/v1/tasks/{id}`

## Description

Returns detailed information about a task by its unique identifier.

This endpoint can be used to display task details in the application interface or to retrieve task data for further processing.

## Path Parameters

| Parameter | Type | Required | Description |
|---|---|---:|---|
| `id` | integer | Yes | Unique task identifier |

## Headers

| Header | Required | Description |
|---|---:|---|
| `Authorization` | Yes | Bearer token used for authentication |

## Request Example

```http
GET /api/v1/tasks/42 HTTP/1.1
Host: api.taskmanager.local
Authorization: Bearer <token>
Successful Response
Status: 200 OK
JSON
{
  "id": 42,
  "title": "Prepare weekly report",
  "description": "Collect team updates and prepare a summary",
  "status": "In Progress",
  "priority": "High",
  "created_at": "2026-04-15T09:30:00Z"
}
Response Fields
Field
Type
Description
id
integer
Unique task identifier
title
string
Task title
description
string
Task description
status
string
Current task status
priority
string
Task priority level
created_at
string
Task creation date in ISO 8601 format
Error Responses
401 Unauthorized
Returned when the request does not contain a valid access token.
JSON
{
  "error": "unauthorized",
  "message": "Authentication is required"
}
404 Not Found
Returned when the specified task does not exist.