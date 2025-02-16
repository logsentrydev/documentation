---
title: "API documentation"
weight: 18
draft: false
description: "LogSentry API documentation."
slug: "api"
tags: ["API", "docs"]
series_order: 10
showAuthor: false
authors:
  - "audun"
showAuthorsBadges : false 
---

# API documentation

Base URL for all endpoints is `https://app.logsentry.dev/api/`

## Add a auditlog entry

{{< badge >}}
POST /auditlog
{{< /badge >}}

### Headers

| Header          | Value                           |
| --------------- | ------------------------------- |
| `Content-Type`  | `application/json` **required** |
| `Authorization` | `Bearer <token>` **required**   |

### Body

| Name | Type | Description |
| --------- | ------------ | ---------------------------------------------- |
| `project` | number       | Project id                                     |
| `level`   | number (0-7) | See [log levels](#log-levels)                  |
| `msg`     | string       | Log message                                    |
| `context` | json         | JSON encoded array with contextual information |
| `user`    | json         | JSON encoded array with user information       |
| `request` | json         | JSON encoded array with request information    |


### Response
```
{
  "status": "ok",
  "hash": "{logentry hash}"
}
```

## Log Levels


| Level | Value | Description |
| ----- | ----- | ------------|
| `Emergency` | `0` | System is unusable (e.g., kernel panic, total hardware failure). |
| `Alert` | `1` | Immediate action required (e.g., database corruption, security breach) |
| `Critical` | `2` | Critical conditions that could lead to failure (e.g., disk errors, power issues). |
| `Error` | `3` | Non-critical errors but issues that need fixing (e.g., failed service restart). |
| `Warning` | `4` | Something isn't right but not necessarily an error (e.g., high memory usage). |
| `Notice` | `5` | Normal but noteworthy events (e.g., service restart, configuration changes). |
| `Informational` | `6` | General system activity logs (e.g., user logins, service status updates). |
| `Debug` | `7` | Detailed information for troubleshooting (e.g., function calls, debug traces). |

