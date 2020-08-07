---
description: Checks users membership within a group
---

# Check a group has a user member

A group can be checked to see if it has a user member using the following HEAD request. A 204 HTTP status response confirms membership, whereas a 404 HTTP status marks no membership.

If an invalid value for userIdentifier or any groupIdentifier is passed then a 400 HTTP status response will be returned.

<span class="label label--head">HEAD</span> /api/management/security/groups/**{groupIdentifier}**/users/**{userIdentifier}**

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |
| userIdentifier  | path           | [UserIdentifier](/security/identifiers.md)  | One of the user identifiers  |

## Remarks

Membership will be classed as true if the user is a member of a child group of the specified group.

## Example requests

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f
```

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/tdurden
```

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/tdurden@fightclub.com
```

```http
HEAD: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

## Response message

| HTTP status code | Reason                       | Response model                   |
| :--------------- | :--------------------------- | :------------------------------- |
| 204              | OK - user in group           |                                  |
| 403              | Forbidden                    | [Error](/key-concepts/errors.md) |
| 404              | NotFound - user not in group | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError          | [Error](/key-concepts/errors.md) |

---

# Check a user is a member of a group

A user can be checked to see if it is a member of a specific group, or groups, using the following HEAD request. A 204 HTTP status response confirms membership, whereas a 404 HTTP status marks no membership.

Multiple groups can be specified using a CSV of [GroupIdentifiers](/security/identifiers.md).

If an invalid value for userIdentifier or any groupIdentifier is passed then a 400 HTTP status response will be returned.

<span class="label label--head">HEAD</span> /api/management/security/users/**{userIdentifier}**/groups/**{groupIdentifier}**[ ,...n ]

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |
| userIdentifier  | path           | [UserIdentifier](/security/identifiers.md)  | One of the user identifiers  |

## Remarks

Membership will be classed as true if the user is a member of a child group of the specified group.

Multiple groupId values can be passed in the path as comma-separated-value (CSV). If a CSV is passed then an OR evaluation will be performed.

## Example requests

#### Single groupId

```http
HEAD: /api/management/security/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

```http
HEAD: /api/management/security/users/tdurden/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

```http
HEAD: /api/management/security/users/t.durden@fightclub.com/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

```http
HEAD: /api/management/security/users/t.durden@fightclub.com/groups/Paper%20Street%20Soap%20Company
```

#### Csv of groupId values

```http
HEAD: /api/management/security/users/653aca45-d768-48d4-9af0-435e138b063f/groups/0ccf6d37-56a2-4a0d-bda1-efc377369232,eee2ca1a-8736-48b7-a274-da6f35499e56,504f21d0-361c-4c56-a87c-25e24ea81dfc
```

```http
HEAD: /api/management/security/users/tdurden/groups/0ccf6d37-56a2-4a0d-bda1-efc377369232,eee2ca1a-8736-48b7-a274-da6f35499e56,504f21d0-361c-4c56-a87c-25e24ea81dfc
```

```http
HEAD: /api/management/security/users/tdurden/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251
```

```http
HEAD: /api/management/security/users/t.durden@fightclub.com/groups/Paper%20Street%20Soap%20Company,Liposuction%20Technicians
```

```http
HEAD: /api/management/security/users/t.durden@fightclub.com/groups/0ccf6d37-56a2-4a0d-bda1-efc377369232,Liposuction%20Technicians
```

## Response message

| HTTP status code | Reason                       | Response model                   |
| :--------------- | :--------------------------- | :------------------------------- |
| 204              | OK - user in group           |                                  |
| 403              | Forbidden                    | [Error](/key-concepts/errors.md) |
| 404              | NotFound - user not in group | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError          | [Error](/key-concepts/errors.md) |
