## Token 申请

?> 你应该通过 [Dashboard API](https://animeloop.org/dashboard/profile/api) 来获取 token。

**`GET /auth/token`** 获取 token

**`POST /auth/token/new`** 申请新的 token

**`POST /auth/token/revoke`** 注销原有的 token

请求 Cookie

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

?> 这些请求的请求体为空，只通过 session cookie 来进行鉴权。

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1320001 | get token success.                     |        |
| 1320002 | create a new token success.            |        |
| 1320003 | revoke the token success.              |        |
| 1940102 | cookie session validation failed.      | common |
| 1940103 | cookie session doesn't exist.          | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
# 获取 token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token"
```

返回结果

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

示例请求

```bash
# 生成新的 token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token/new"
```

返回结果

```json
{
  "status": "success",
  "code": 1320002,
  "message": "create a new token success.",
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InNoaW5jdXJyeTIifQ.VMZHxDvyqeUHaN6Wg92CvlphvicNynuOY5ELdFQTY3w"
  }
}
```

----------------------------

示例请求

```bash
# 注销原有的 token
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/auth/token/revoke"
```

返回结果

```json
{
  "status":"success",
  "code":1320003,
  "message":"revoke the token success.",
  "data": {}
}
```
