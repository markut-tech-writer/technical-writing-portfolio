# Task Manager API

## Overview

This document describes the API for working with tasks in the Task Manager application.

The API allows clients to create tasks and retrieve task information.

---

## Get Task by ID

### Endpoint

`GET /api/v1/tasks/{id}`

### Description

Returns a list of tasks available to the user.

This endpoint can be used to display tasks in the dashboard or filter them by status.

### Query Parameters

| Parameter | Type   | Description              |
|----------|--------|--------------------------|
| status   | string | Filter tasks by status   |

### Path Parameters

| Parameter | Type    | Required | Description                |
|-----------|---------|----------|----------------------------|
| id        | integer | Yes      | Unique task identifier     |

### Headers

| Header        | Required | Description                         |
|---------------|----------|-------------------------------------|
| Authorization | Yes      | Bearer token used for authentication |

### Request Example

```http
GET /api/v1/tasks/42 HTTP/1.1
Host: api.taskmanager.local
Authorization: Bearer <token>

### Notes

- All responses are returned in JSON format  
- Authentication is required