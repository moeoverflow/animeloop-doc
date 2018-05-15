## Token request

**`POST /auth/token`** Get token

**`POST /auth/token/new`** Request a new token

**`POST /auth/token/revoke`** Revoke the existing token

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Possible response

| code    | message                                    | note   |
| ------- | ------------------------------------------ | ------ |
| 1320001 | request token successfully.                |        |
| 1320002 | request a new token successfully.          |        |
| 1320003 | revoke the token successfully.             |        |
| 1340401 | request token failed. token doesn't exist. |        |
| 1940102 | cookie session validation failed.          | common |
| 1940103 | cookie session doesn't exist.              | common |
| 1950301 | internal server error, database error.     | common |

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
  "message":"request the token successfully.",
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InNoaW5jdXJyeTIifQ.VMZHgDvyqeUHqN6Wg92CvlphdiwNynuOY5ELdFQTY3w"
  }
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
  "message": "request a new token successfully.",
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InNoaW5jdXJyeTIifQ.VMZHxDvyqeUHaN6Wg92CvlphvicNynuOY5ELdFQTY3w"
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
  "message":"revoke the token successfully.",
  "data": {}
}
```
