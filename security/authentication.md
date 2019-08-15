# Authentication

To access any resource from the Management API, a client needs to authenticate with the Zengenti OAuth 2.0 Identity Provider, which is hosted with the Contensis application.

Websites and applications are authenticated using the [OAuth 2.0 client credential flow](https://tools.ietf.org/html/rfc6749#section-4.4), which is used to grant access to resources such as entries, content types and projects.

The client needs to provide a *clientId*, a *shared secret* and a list of [scopes](/security/scopes.md). The *clientId* and *shared secret* can be created in [API Management](https://zenhub.zengenti.com/Contensis/9/kb/content-types-and-entries/api-keys/api-key-overview.aspx) screen in Contensis. These credentials are used to request an *access token* from the identity provider, which is cached locally and passed along with each request as a HTTP Authorization header to the Delivery API services. If the authentication request fails then a 401 HTTP status code response is returned.

## Example request

```http
POST: https://cms-yourcontensis.com/authenticate/connect/token
Content-Type: application/x-www-form-urlencoded
Accept: application/json

grant_type=client_credentials&
client_id=bda30e56-4faf-412c-b460-6fce9342b162&
client_secret=1e2759cee76b4ae7947722be71cc33e1-56a63ae1361241fdab7c9ee90cc8a6b3-6dc4c02b8eda43d49de499ad5eef1160&
scope=Entry_Read ContentType_Read Project_Read
```

## Successful response

`200 - OK`

```json
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6IjlmcEhwSnMxZkdnUG5NRURHdmNNbnhxUmZNMCIsImtpZCI6IjlmcEhwSnMxZkdnUG5NRURHdmNNbnhxUmZNMCJ9.eyJpc3MiOiJodHRwOi8vY21zLWRldmVsb3AuY2xvdWQuY29udGVuc2lzLmNvbS9hdXRoZW50aWNhdGUiLCJhdWQiOiJodHRwOi8vY21zLWRldmVsb3AuY2xvdWQuY29udGVuc2lzLmNvbS9hdXRoZW50aWNhdGUvcmVzb3VyY2VzIiwiZXhwIjoxNDg4Mzc5MzU4LCJuYmYiOjE0ODgzNzU3NTgsImNsaWVudF9pZCI6ImJkYTMwZTU2LTRmYWYtNDEyYy1iNDYwLTZmY2U5MzQyYjE2MiIsImNsaWVudF9zdWIiOiJiZGEzMGU1Ni00ZmFmLSQxMmMtYjQ2MC02ZmNlOTM0MmIxNjIiLCJjbGllbnRfdXNlcm5hbWUiOiJTaW1vbidzIGtleSIsInNjb3BlIjoiRW50cnlfUmVhZCJ9.g1krcmM_2Qe5ZIB_2c8LDmBVP8tc2V2j01PqvlHk8swVLTonF_x-5Iob0Tql8dJN_jDyJyJNx0dzZGAd-w1Gn8qS_6KQR9e4Uk4z1OAd6s1soo6WhXMqgbGJ8Hq9WXgOehZz_Vz2efdGFZ2JJLr7mRRNj-4XL21XhkVYXWnxXfugSZ0tJdBa2rMTxDgz8uVF9Tdrcduy7l85lOjTZL13CwMbrPQebCdTQCty7LKGfF_U3KaWyRtTXwZhUvhq-7wCtEuHymcEAa_8jokL8pT0vhPkvMKZ_SiVCkdnBbwQ6GNFMU_mfjt4b-xgxjUFsHDhQPczosxmn8I7__hRpcsZCQ",
  "expires_in": 3600,
  "token_type": "Bearer"
}
```

> **Note** The *expires_in* value is in seconds.

## Unsuccessful response
s
`400 - BadRequest`

```json
{
  "error": "invalid_client"
}
```
