# API Doc Checklist

## Overview

Create human-readable API documentation for current feature branch.

## Steps

* [ ] Compare current feature branch and origin/main branch to extract the differences.
* [ ] Check `api/**/*route.go` for new API endpoints.
* [ ] Check `pkg/handler/model.go` for request and response struct changes.
* [ ] Review handler functions to understand business logic and validation rules.
* [ ] Check for path parameters, query parameters, and request headers.
* [ ] Identify authentication/authorization requirements.
* [ ] Document error responses and status codes.
* [ ] Write human-readable API documentation in Chinese.

## Details

* For IDs like `project_id`, `version_id`, check `constant/id.go` or similar places for ID prefix (like 'ap-111', 'agpv-222').
* Include all required and optional fields in request/response examples.
* Document field types, constraints, and validation rules when relevant.
* Note any breaking changes or deprecations.
* Include example values that reflect real-world usage.

## Format

##### 1.1.1.1 API名称/描述
* **path**: `/api/agent-manager/user/agent/xxx`
* **method**: `POST`
* **描述**: (Optional) Brief description of what this API does
* **请求 (Request)**
```json
{
    "project_id": "ap-xxx"
}
```
* **响应 (Response)**
  * **Status Code**: `200 OK`
```json
{
    "project_id": "ap-xxx",
    "name": "xxx",
    "is_deleted": 0
}
```

