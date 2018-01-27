## Register account

**`POST /auth/register`**

Request body

| KEY      | EXAMPLE             |
| -------- | ------------------- |
| username | kyon777             |
| password | imjohnsmith777      |
| email    | johnsmith@haruhi.tv |

Example request 

```bash
curl -d "username=kyon777&password=imjohnsmith777&email=johnsmith@haruhi.tv" "https://animeloop.org/api/v2/auth/register"
```

Example response

```json
{
  "status": "success",
  "code": 200,
  "message": "register successfully.",
  "data": {}
}
```

## Send verification email

**`POST /auth/verify/sendemail`**

Request body

| KEY      | eXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

?> When you sign up for an account, the system will automatically send an email to the email address you provided, so you do not need to call this interface manually.

Example request 

```bash
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/verify/sendemail"
```

Example response

```json
{
  "status": "success",
  "code": 200,
  "message": "send email successfully.",
  "data": {}
}
```

## Verify account

**`GET /auth/verify?[code=value]`**

?> In the mailbox check the verification email with a verify url, You do not need to manually call this interface.

Example request 

```bash
curl https://animeloop.org/api/v2/auth/verify?code=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY3Rpb24iOiJ2ZXJpZnkiLCJ1c2VybmFtZSI6InNxaW5jdXJyeTIiLCJkYXRlIjoiMjAxOC0wMS0yN1QwNToyMDozMC40NjhaIn0.JZ8xpCqusaAw_swnHT4bKXfjyxBxfHz0HyBkmVVoe-A
```

Example response

```json
{
  "status": "success",
  "code": 200,
  "message": "send email successfully.",
  "data": {}
}
```
