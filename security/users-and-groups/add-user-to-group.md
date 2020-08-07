---
description: A user can be added to a group by sending a PUT request specifying the group and user identifiers.
---

# Add user to a group

A user can be added to a group by sending a PUT request specifying the [group and user identifiers](/security/identifiers.md).

<span class="label label--put">PUT</span> /api/management/security/groups/**{groupIdentifier}**/users/**{userIdentifier}**

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| userIdentifier  | path           | [UserIdentifier](/security/identifiers.md)  | One of the user identifiers  |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |

## Example requests

```http
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
PUT: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/tdurden
```

```http
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/t.durden@fightclub.com
```

```http
PUT: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/t.durden@fightclub.com
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

---

# Add many users to a group

Multiple users can be added to a group in bulk by sending a POST request to the group's users collection with the user ids as an array in the body.

<span class="label label--post">POST</span> /api/management/security/groups/**{groupIdentifier}**/users/

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |
| userIds         | body           | Array\<GUID>                                | An array of user ids         |

## Example request

```http
POST: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/
[
    "75490b0f-56f7-4690-a20a-6f2a822f1d3f",
    "20b5e923-beb8-44ab-8bb4-34467582230f",
    "13f8cd48-7765-47b7-9fa3-2ad9c935a4be",
    "3c3d98a1-c80a-49d1-b602-f38ad2b01af8",
    "11f5ce76-ca86-45d8-9928-d7fd56863ec7"
]
```

```http
POST: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/
[
    "75490b0f-56f7-4690-a20a-6f2a822f1d3f",
    "20b5e923-beb8-44ab-8bb4-34467582230f",
    "13f8cd48-7765-47b7-9fa3-2ad9c935a4be",
    "3c3d98a1-c80a-49d1-b602-f38ad2b01af8",
    "11f5ce76-ca86-45d8-9928-d7fd56863ec7"
]
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
