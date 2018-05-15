## 注册账户

**`POST /auth/register`**

请求体

| KEY                  | EXAMPLE                                                      |
| -------------------- | ------------------------------------------------------------ |
| username             | kyon777                                                      |
| password             | imjohnsmith777                                               |
| email                | [johnsmith@haruhi.tv](mailto:johnsmith@haruhi.tv)            |
| g-recaptcha-response | 03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJh... |

!> 密码通过 [bcryptjs](https://github.com/dcodeIO/bcrypt.js) 加密存储于数据库，并非密码原文存储，请各位用户放心。

可能的响应结果

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

示例请求

```bash
curl -d "username=kyon777&password=imjohnsmith777&email=johnsmith@haruhi.tv&g-recaptcha-response=03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJhEnbecV7PwAgCSF1JKUC3Gr5AQILxBuSrKKZrvkHQlm2pZfnTFWuyq0rYID2oUhlsKxVA4FY03GEJV-BCaciZphPDZpvid9t9ompoh8HS0_iKP9EgD9ju7ksqSiy9XcVkHfOy7BQJ2qEeaR2qHxrG2wFLC6w0D4bG8dySX9VgKeMW_pvXnni9ZMLXIVcTz4WpDtaELvRaIc02wWjgmvZZ8DXJ0on2B7T1IACOFYu5dvDVRJz3DsRvs8nYIbz1MwRfzQGVycQz5p5Z8b1lwhkVotYlaetMS3A79ECfJPXOJs4_Hrd5q9TofiYOIbqFPk" "https://animeloop.org/api/v2/auth/register"
```

返回结果

```json
{
  "status": "success",
  "code": 1120001,
  "message": "register successfully.",
  "data": {}
}
```

## 发送激活验证邮件

**`POST /auth/verify/sendemail`**

请求体

| KEY      | EXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

?> 当你注册账户的时候，系统会自动向你提供的邮箱地址发送一封邮件，所以一般情况下不需要在手动调用这个接口。

可能的响应结果

| code    | message                                 | note   |
| ------- | --------------------------------------- | ------ |
| 1420002 | send verification email successfully.   |        |
| 1420003 | this account has already been verified. |        |
| 1440003 | empty username or password.             |        |
| 1440004 | incorrect username or password.         |        |
| 1950301 | internal server error, database error.  | common |

示例请求

```bash
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/verify/sendemail"
```

返回结果

```json
{
  "status": "success",
  "code": 1420002,
  "message": "send verification email successfully.",
  "data": {}
}
```

## 验证激活账户

**`GET /auth/verify?[code=value]`**

?> 在邮箱里查收激活邮件，邮件内附带有激活链接，一般情况下不需要手动调用这个接口。

可能的响应结果

| code    | message                                          | note   |
| ------- | ------------------------------------------------ | ------ |
| 1420001 | verify account successfully.                     |        |
| 1440001 | [code] is empty, please provide a correct one.   |        |
| 1440002 | [code] is invalid, please provide a correct one. |        |
| 1950301 | internal server error, database error.           | common |

示例请求

```bash
curl https://animeloop.org/api/v2/auth/verify?code=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY3Rpb24iOiJ2ZXJpZnkiLCJ1c2VybmFtZSI6InNxaW5jdXJyeTIiLCJkYXRlIjoiMjAxOC0wMS0yN1QwNToyMDozMC40NjhaIn0.JZ8xpCqusaAw_swnHT4bKXfjyxBxfHz0HyBkmVVoe-A
```

返回结果

```json
{
  "status": "success",
  "code": 1420001,
  "message": "verify account successfully.",
  "data": {}
}
```

## 登录

**`POST /auth/login`**

请求体

| KEY                  | EXAMPLE                                                      |
| -------------------- | ------------------------------------------------------------ |
| username             | kyon777                                                      |
| password             | imjohnsmith777                                               |
| g-recaptcha-response | 03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJh... |

?> 这个请求的响应结果包含有 session cookie。

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1220001 | login successfully.                    |        |
| 1240101 | incorrect username or password.        |        |
| 1240102 | this account has not yet verified.     |        |
| 1940101 | Google reCAPTCHA verification failed.  | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
curl -d "username=kyon777&password=imjohnsmith777&g-recaptcha-response=03AJpayVF6YpF1BGU-kZqEwN6G2k7cOv16_Q-SvK8zOUHrtkqdlVrIf9BJhEnbecV7PwAgCSF1JKUC3Gr5AQILxBuSrKKZrvkHQlm2pZfnTFWuyq0rYID2oUhlsKxVA4FY03GEJV-BCaciZphPDZpvid9t9ompoh8HS0_iKP9EgD9ju7ksqSiy9XcVkHfOy7BQJ2qEeaR2qHxrG2wFLC6w0D4bG8dySX9VgKeMW_pvXnni9ZMLXIVcTz4WpDtaELvRaIc02wWjgmvZZ8DXJ0on2B7T1IACOFYu5dvDVRJz3DsRvs8nYIbz1MwRfzQGVycQz5p5Z8b1lwhkVotYlaetMS3A79ECfJPXOJs4_Hrd5q9TofiYOIbqFPk" "https://animeloop.org/api/v2/auth/login"
```

返回结果

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

请求 Cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

?> 这些请求的请求体为空，只通过 session cookie 来进行鉴权。

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1220002 | logout successfully.                   |        |
| 1940102 | cookie session validation failed.      | common |
| 1940103 | cookie session doesn't exist.          | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/logout"
```

返回结果

```json
// 响应结果包含 session cookie [animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU]

{
  "status": "success",
  "code": 1220002,
  "message": "logout successfully.",
  "data": {}
}
```

