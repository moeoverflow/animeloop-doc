## Register account

**`POST /auth/register`**

Request body

| KEY                  | EXAMPLE                                                      |
| -------------------- | ------------------------------------------------------------ |
| username             | kyon777                                                      |
| password             | imjohnsmith777                                               |
| email                | johnsmith@haruhi.tv                                          |
| g-recaptcha-response | 03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJh... |

!> Password stored in the database was encrypted by [bcryptjs](https://github.com/dcodeIO/bcrypt.js), not the original password, feel free to use it.

Possible response

| code    | message                                                      | note   |
| ------- | ------------------------------------------------------------ | ------ |
| 1120001 | register successfully.                                       |        |
| 1140001 | [username] is empty, please provide a correct one.           |        |
| 1140002 | [username] must be at least 5 at most 15 characters long, please try another. |        |
| 1140003 | [password] is empty, please provide a correct one.           |        |
| 1140004 | [password] must be at least 6 at most 17 characters long, please try another. |        |
| 1140005 | [email] is empty, please provide a correct one.              |        |
| 1140006 | [email] is not in correct format, please try another.        |        |
| 1940101 | Google reCAPTCHA verification failed.                        | common |
| 1140901 | This username has been registered.                           |        |
| 1950301 | internal server error, database error.                       | common |

Example request 

```bash
curl -d "username=kyon777&password=imjohnsmith777&email=johnsmith@haruhi.tv&g-recaptcha-response=03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJhEnbecV7PwAgCSF1JKUC3Gr5AQILxBuSrKKZrvkHQlm2pZfnTFWuyq0rYID2oUhlsKxVA4FY03GEJV-BCaciZphPDZpvid9t9ompoh8HS0_iKP9EgD9ju7ksqSiy9XcVkHfOy7BQJ2qEeaR2qHxrG2wFLC6w0D4bG8dySX9VgKeMW_pvXnni9ZMLXIVcTz4WpDtaELvRaIc02wWjgmvZZ8DXJ0on2B7T1IACOFYu5dvDVRJz3DsRvs8nYIbz1MwRfzQGVycQz5p5Z8b1lwhkVotYlaetMS3A79ECfJPXOJs4_Hrd5q9TofiYOIbqFPk" "https://animeloop.org/api/v2/auth/register"
```

Example response

```json
{
  "status": "success",
  "code": 1120001,
  "message": "register successfully.",
  "data": {}
}
```

## Send verification email

**`POST /auth/verify/sendemail`**

Request body

| KEY      | EXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

?> When you sign up for an account, the system will automatically send an email to the email address you provided, so you do not need to call this interface manually.

Possible response

| code    | message                                 | note   |
| ------- | --------------------------------------- | ------ |
| 1420002 | send verification email successfully.   |        |
| 1420003 | this account has already been verified. |        |
| 1940104 | username is empty.                      | common |
| 1940105 | password is empty.                      | common |
| 1940106 | incorrect username or password.         | common |
| 1950301 | internal server error, database error.  | common |

Example request 

```bash
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/verify/sendemail"
```

Example response

```json
{
  "status": "success",
  "code": 1420002,
  "message": "send verification email successfully.",
  "data": {}
}
```

## Verify account

**`GET /auth/verify?[code=value]`**

?> In the mailbox check the verification email with a verify url, You do not need to manually call this interface.

| code    | message                                          | note   |
| ------- | ------------------------------------------------ | ------ |
| 1420001 | verify account successfully.                     |        |
| 1440001 | [code] is empty, please provide a correct one.   |        |
| 1440002 | [code] is invalid, please provide a correct one. |        |
| 1950301 | internal server error, database error.           | common |

Example request

```bash
curl https://animeloop.org/api/v2/auth/verify?code=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY3Rpb24iOiJ2ZXJpZnkiLCJ1c2VybmFtZSI6InNxaW5jdXJyeTIiLCJkYXRlIjoiMjAxOC0wMS0yN1QwNToyMDozMC40NjhaIn0.JZ8xpCqusaAw_swnHT4bKXfjyxBxfHz0HyBkmVVoe-A
```

Example response

```json
{
  "status": "success",
  "code": 1420001,
  "message": "verify account successfully.",
  "data": {}
}
```

## login

**`POST /auth/login`**

Request body

| KEY                  | eXAMPLE                                                      |
| -------------------- | ------------------------------------------------------------ |
| username             | kyon777                                                      |
| password             | imjohnsmith777                                               |
| g-recaptcha-response | 03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJh... |

!> The response of this request contains a session cookie.

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1220001 | login successfully.                    |        |
| 1940101 | Google reCAPTCHA verification failed.  | common |
| 1940104 | username is empty.                     | common |
| 1940105 | password is empty.                     | common |
| 1940106 | incorrect username or password.        | common |
| 1950301 | internal server error, database error. | common |

Example request 

```bash
curl -d "username=kyon777&password=imjohnsmith777&g-recaptcha-response=03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJhEnbecV7PwAgCSF1JKUC3Gr5AQILxBuSrKKZrvkHQlm2pZfnTFWuyq0rYID2oUhlsKxVA4FY03GEJV-BCaciZphPDZpvid9t9ompoh8HS0_iKP9EgD9ju7ksqSiy9XcVkHfOy7BQJ2qEeaR2qHxrG2wFLC6w0D4bG8dySX9VgKeMW_pvXnni9ZMLXIVcTz4WpDtaELvRaIc02wWjgmvZZ8DXJ0on2B7T1IACOFYu5dvDVRJz3DsRvs8nYIbz1MwRfzQGVycQz5p5Z8b1lwhkVotYlaetMS3A79ECfJPXOJs4_Hrd5q9TofiYOIbqFPk" "https://animeloop.org/api/v2/auth/login"
```

Example response

```json
// response contains auth session cookie [animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU]

{
  "status": "success",
  "code": 1220001,
  "message": "login successfully.",
  "data": {}
}
```

## Logout

**`POST /auth/logout`**

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1220002 | logout successfully.                   |        |
| 1940102 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

Example request 

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/logout"
```

Example response

```json
// response contains auth session cookie [animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU]

{
  "status": "success",
  "code": 1220002,
  "message": "logout successfully.",
  "data": {}
}
```

