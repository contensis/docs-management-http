---
description: Checks users membership within a group 
---

# Check a group has a user member

A group can be checked to see if it has a user member using the following HEAD request.

<span class="label label--head">HEAD</span> /api/management/security/groups/**{groupId}**/users/**{userId}**

## Remarks

Membership will be class as true if the user is a member of a child group of the specified group.

## Example request

```json
HEAD: /api/management/security/group/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f
```

## Response message

| HTTP status code | Reason                       | Response model                   |
|:-----------------|:-----------------------------|:---------------------------------|
| 200              | OK - user in group           |                                  |
| 403              | Forbidden                    | [Error](/key-concepts/errors.md) |
| 404              | NotFound - user not in group | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError          | [Error](/key-concepts/errors.md) |

---

# Check a user is a member of a group

A user can be checked to see if it is a member of a specific group using the following HEAD request.

<span class="label label--head">HEAD</span> /api/management/security/groups/**{groupId}**/users/**{userId}**

## Remarks

Membership will be class as true if the user is a member of a child group of the specified group.

## Example request

```json
HEAD: /api/management/security/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f/users/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

## Response message

| HTTP status code | Reason                       | Response model                   |
|:-----------------|:-----------------------------|:---------------------------------|
| 200              | OK - user in group           |                                  |
| 403              | Forbidden                    | [Error](/key-concepts/errors.md) |
| 404              | NotFound - user not in group | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError          | [Error](/key-concepts/errors.md) |

---