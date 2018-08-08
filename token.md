## Token request

?> You should get tokens from [Dashboard API](https://animeloop.org/dashboard/profile/api).

**`GET /auth/token`** Get tokens

**`POST /auth/token/new`** Request a new token

**`POST /auth/token/revoke`** Revoke the existing token

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1320001 | get token success.                     |        |
| 1320002 | create a new token success.            |        |
| 1320003 | revoke the token success.              |        |
| 1940102 | cookie session validation failed.      | common |
| 1940103 | cookie session doesn't exist.          | common |
| 1950301 | internal server error, database error. | common |

Example request

```bash
# Get token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token"
```

Example response

```json
{
  "status":"success",
  "code":1320001,
  "message":"get token success.",
  "data": [{
    "_id": 1,
    "name": "animeloop_dev",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InNoaW5jdXJyeTIifQ.VMZHgDvyqeUHqN6Wg92CvlphdiwNynuOY5ELdFQTY3w"
  }]
}
```

----------------------------

Example request

```bash
# Request a new token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token/new"
```

Example response

```json
{
  "status": "success",
  "code": 1320002,
  "message": "create a new token success.",
  "data": {
    "_id": 1,
    "name": "animeloop_dev",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InNoaW5jdXJyeTIifQ.VMZHgDvyqeUHqN6Wg92CvlphdiwNynuOY5ELdFQTY3w"
  }
}
```

----------------------------

Example request

```bash
# Revoke the existing token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token/revoke"
```

Example response

```json
{
  "status":"success",
  "code":1320003,
  "message":"revoke the token success.",
  "data": {}
}
```
