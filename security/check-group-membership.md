---
description: Creating a user can be done by POST'ing user profile details resource to the users resource collection. 
---

# Check a user in a member of a group

<span class="label label--head">HEAD</span> /api/management/security/groups/**{groupId}**/

## Example request

```json
HEAD: /api/management/security/group/

```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Created             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |