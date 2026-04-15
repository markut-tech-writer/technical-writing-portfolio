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