---
description: Checks users membership within a group
---

# Check a group has a user member

A group can be checked to see if it has a user member using the following HEAD request. A 200 HTTP status response confirms membership, whereas a 404 HTTP status marks no membership.

<span class="label label--head">HEAD</span> /api/management/security/groups/**{groupId}**/users/**{userId}**

## Remarks

Membership will be classed as true if the user is a member of a child group of the specified group.

## Example request

```json
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f
```

## Response message

| HTTP status code | Reason                       | Response model |
| :--------------- | :--------------------------- | :------------- |
| 204              | OK - user in group           |                |
| 403              | Forbidden                    |                |
| 404              | NotFound - user not in group |                |
| 500              | InternalServerError          |                |

---

# Check a user is a member of a group

A user can be checked to see if it is a member of a specific group using the following HEAD request. A 200 HTTP status response confirms membership, whereas a 404 HTTP status marks no membership.

<span class="label label--head">HEAD</span> /api/management/security/users/**{userId}**/groups/**{groupId}**

## Remarks

Membership will be classed as true if the user is a member of a child group of the specified group.

## Example request

```json
HEAD: /api/management/security/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

## Response message

| HTTP status code | Reason                       | Response model |
| :--------------- | :--------------------------- | :------------- |
| 204              | OK - user in group           |                |
| 403              | Forbidden                    |                |
| 404              | NotFound - user not in group |                |
| 500              | InternalServerError          |                |

---

# Check a user is a member of a list of groups

A user can be checked to see if it is a member of any specific group in a given list of groups using the following HEAD request. A 204 HTTP status response confirms membership, whereas a 404 HTTP status marks no membership.

If an invalid value for userId or any groupId in groupIdCsv is passed then a 400 HTTP status response will be returned.

<span class="label label--head">HEAD</span> /api/management/security/users/**{userId}**/groups?groupIdCsv=**{groupIdCsv}**

## Remarks

Membership will be classed as true if the user is a member of any child-groups of the groups specified in groupIdCsv.

## Example request

```json
HEAD: /api/management/security/users/653aca45-d768-48d4-9af0-435e138b063f/groups?groupIdCsv=0ccf6d37-56a2-4a0d-bda1-efc377369232,eee2ca1a-8736-48b7-a274-da6f35499e56,504f21d0-361c-4c56-a87c-25e24ea81dfc
```

## Response message

| HTTP status code | Reason                                 | Response model |
| :--------------- | :------------------------------------- | :------------- |
| 204              | OK - user is in at least one of groups |                |
| 400              | Invalid userId or groupId passed       |                |
| 403              | Forbidden                              |                |
| 404              | NotFound - user not in any of groups   |                |
| 500              | InternalServerError                    |                |
