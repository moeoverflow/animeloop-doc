## 请求响应状态码

### Account - 11 xxx xx

| code    | message                                                      | note |
| ------- | ------------------------------------------------------------ | ---- |
| 1120001 | register successfully.                                       |      |
| 1140001 | [username] is empty, please provide a correct one.           |      |
| 1140002 | [username] must be at least 5 at most 15 characters long, please try another. |      |
| 1140003 | [password] is empty, please provide a correct one.           |      |
| 1140004 | [password] must be at least 6 at most 17 characters long, please try another. |      |
| 1140005 | [email] is empty, please provide a correct one.              |      |
| 1140006 | [email] is not in correct format, please try another.        |      |
| 1140901 | This username has been registered.                           |      |



### Token - 13 xxx xx

| code    | message                     | note |
| ------- | --------------------------- | ---- |
| 1320001 | get token success.          |      |
| 1320002 | create a new token success. |      |
| 1320003 | revoke the token success.   |      |
|         |                             |      |
|         |                             |      |
|         |                             |      |



### Profile - 15 xxx xx

| code    | message                    | note |
| ------- | -------------------------- | ---- |
| 1520001 | fetch userinfo success.    |      |
| 1520002 | update userinfo success    |      |
| 1520003 | upload new avatar success. |      |
|         |                            |      |

### Common - 19 xxx xx

| code    | message                                    | note |
| ------- | ------------------------------------------ | ---- |
| 1940101 | Google reCAPTCHA verification failed.      |      |
| 1940102 | cookie session doesn't exist.              |      |
| 1940103 | cookie session validation failed.          |      |
| 1940104 | token doesn't exist.                       |      |
| 1940105 | token validation failed.                   |      |
| 1940106 | cookie session or token validation failed. |      |
| 1950301 | internal server error, database error.     |      |
|         |                                            |      |