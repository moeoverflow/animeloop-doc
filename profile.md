## Get userinfo

**`GET /profile/get-userinfo`**

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520001 | fetch userinfo success.                |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

Example request

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/profile/get-userinfo"
```

Example response

```json
{
  "status": "success",
  "code": 1520001,
  "message": "fetch userinfo success.",
  "data": {}
}
```

## Update userinfo

**`POST /profile/update-userinfo`**

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520002 | update userinfo success                |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

Example request

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" "https://animeloop.org/api/v2/profile/update-userinfo"
```

Example response

```json
{
  "status": "success",
  "code": 1520002,
  "message": "update userinfo success.",
  "data": {}
}
```

## Upload avatar

**`POST /profile/upload-new-avatar`**

Request cookies

| KEY                | EXAMPLE                                                      |
| ------------------ | ------------------------------------------------------------ |
| animeloop.auth.sid | s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU |

!> These requests have an empty body, authentication works with session cookie from login api.

Request body

| KEY  | EXAMPLE       |
| ---- | ------------- |
| file | \<file data\> |

Possible response

| code    | message                                | note   |
| ------- | -------------------------------------- | ------ |
| 1520003 | upload new avatar success.             |        |
| 1940102 | cookie session doesn't exist.          | common |
| 1940103 | cookie session validation failed.      | common |
| 1950301 | internal server error, database error. | common |

Example request 

```bash
curl --cookie "animeloop.auth.sid=s%3A4VtJUXAabKIew3Wib8scACX1lDZK6Z3d.7Hqy%2F8Nk8d0rFr4ygSCoEnwg5GD%2BVMfghQieThqQ2dU" --file <filedata> "https://animeloop.org/api/v2/profile/upload-new-avatar"
```

Example response

```json
{
  "status": "success",
  "code": 1520003,
  "message": "upload new avatar success.",
  "data": {}
}
```

