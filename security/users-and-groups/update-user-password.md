---
description: A user's password can be updated with a call that includes the user's current password.
---

# Check a group has a user member

A user can update their password with a call that includes a new password and the user's current password. A member of the `System Administrator` group can update the password without the need to provide the existing password.

<span class="label label--post">POST</span> /api/management/security/users/**{userId}**/credentials/password

## Remarks

If the existing password is wrong then a 409 Conflict status is returned.

If the new password does not meet the password policy then a 422 Unprocessable Entity status is returned.

## Example request for user

```json
POST: /api/management/security/users/9bb89380-fd49-41a5-ab2f-fc25e482a251/credentials/password
{
    "existing": "m4rl451ng3r",
    "new": "pr0j3ctM4yh3m"
}
```

## Example request for a System Adminstrator member

```json
POST: /api/management/security/users/9bb89380-fd49-41a5-ab2f-fc25e482a251/credentials/password
{
    "new": "pr0j3ctM4yh3m"
}
```

## Response message

| HTTP status code | Reason                                      | Response model                   |
|:-----------------|:--------------------------------------------|:---------------------------------|
| 200              | OK - user in group                          |                                  |
| 403              | Forbidden                                   | [Error](/key-concepts/errors.md) |
| 404              | NotFound                                    | [Error](/key-concepts/errors.md) |
| 409              | Conflict - existing password invalid        | [Error](/key-concepts/errors.md) |
| 422              | Unprocessable Entity - new password invalid | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError                         | [Error](/key-concepts/errors.md) |