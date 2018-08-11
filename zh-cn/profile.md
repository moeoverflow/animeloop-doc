## 获取用户信息

**`GET /profile/get-userinfo`**

请求 Cookie

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

?> 这些请求的请求体为空，只通过 session cookie 来进行鉴权。

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520001 | fetch userinfo success.                |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/profile/get-userinfo"
```

返回结果

```json
{
  "status": "success",
  "code": 1520001,
  "message": "fetch userinfo success.",
  "data": {}
}
```

## 更新用户信息

**`POST /profile/update-userinfo`**

请求 Cookie

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

?> 这些请求的请求体为空，只通过 session cookie 来进行鉴权。

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520002 | update userinfo success                |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/profile/update-userinfo"
```

返回结果

```json
{
  "status": "success",
  "code": 1520002,
  "message": "update userinfo success.",
  "data": {}
}
```
## 上传头像

**`POST /profile/upload-new-avatar`**

请求 Cookie

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

?> 这些请求的请求体为空，只通过 session cookie 来进行鉴权。

请求体

| KEY  | EXAMPLE       |
| ---- | ------------- |
| file | \<file data\> |

可能的响应结果

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520003 | upload new avatar success.             |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

示例请求

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" --file <filedata> "https://animeloop.org/api/v2/profile/upload-new-avatar"
```

返回结果

```json
{
  "status": "success",
  "code": 1520003,
  "message": "upload new avatar success.",
  "data": {}
}
```

