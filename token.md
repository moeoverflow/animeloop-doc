## Token request

**`POST /auth/token`** Get token

**`POST /auth/token/new`** Request a new token

**`POST /auth/token/revoke`** Revoke the existing token

Request body

| KEY      | EXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

Example request

```bash
# Get token
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token"
```

Example response

```json
{
  "status":"success",
  "code":200,
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
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token/new"
```

Example response

```json
{
  "status": "success",
  "code": 200,
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
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token/revoke"
```

Example response

```json
{
  "status":"success",
  "code":200,
  "message":"revoke the token successfully.",
  "data": {}
}
```
