## Token 申请

**`POST /auth/token`** 获取 token

**`POST /auth/token/new`** 申请新的 token

**`POST /auth/token/revoke`** 注销原有的 token

请求体

| KEY      | EXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

示例请求

```bash
# 获取 token
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token"
```

返回结果

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

示例请求

```bash
# 获取 token
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token/new"
```

返回结果

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

示例请求

```bash
# 注销原有的 token
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/token/revoke"
```

返回结果

```json
{
  "status":"success",
  "code":200,
  "message":"revoke the token successfully.",
  "data": {}
}
```
