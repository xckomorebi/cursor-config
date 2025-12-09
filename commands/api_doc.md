# Api Doc Checklist

## Overview

create human readible api documentation for current feature branch.

## Steps

[ ] Compare current feature branch and origin/main branch to extract the differences.
[ ] Check api/**/*route.go for new APIs.
[ ] Check pkg/handler/model.go for request and response struct changes.
[ ] Write human readible api documentation in Chinese

## details
* for ids like `project_id`, `version_id`, check constant/id.go or similar places for id prefix (like 'ap-111', 'agpv-222')

## format

##### 1.1.1.1
* path: api/agent-manager/user/agent/xxx
* method: POST
* 请求
```json
{
    "project_id": "ap-xxx",
}

```
* 响应
```json
{
    "project_id": "ap-xxx",
    "name": "xxx",
    "is_deleted": 0
}
```

