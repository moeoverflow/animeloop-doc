## 注册账户

**`POST /auth/register`**

请求体

| KEY      | EXAMPLE             |
| -------- | ------------------- |
| username | kyon777             |
| password | imjohnsmith777      |
| email    | johnsmith@haruhi.tv |

示例请求

```bash
curl -d "username=kyon777&password=imjohnsmith777&email=johnsmith@haruhi.tv" "https://animeloop.org/api/v2/auth/register"
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "register successfully.",
  "data": {}
}
```

## 发送激活验证邮件

**`POST /auth/verify/sendemail`**

请求体

| KEY      | eXAMPLE        |
| -------- | -------------- |
| username | kyon777        |
| password | imjohnsmith777 |

?> 当你注册账户的时候，系统会自动向你提供的邮箱地址发送一封邮件，所以一般情况下不需要在手动调用这个接口。

示例请求

```bash
curl -d "username=kyon777&password=imjohnsmith777" "https://animeloop.org/api/v2/auth/verify/sendemail"
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "send email successfully.",
  "data": {}
}
```

## 验证激活账户

**`GET /auth/verify?[code=value]`**

?> 在邮箱里查收激活邮件，邮件内附带有激活链接，一般情况下不需要手动调用这个接口。

示例请求

```bash
curl https://animeloop.org/api/v2/auth/verify?code=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY3Rpb24iOiJ2ZXJpZnkiLCJ1c2VybmFtZSI6InNxaW5jdXJyeTIiLCJkYXRlIjoiMjAxOC0wMS0yN1QwNToyMDozMC40NjhaIn0.JZ8xpCqusaAw_swnHT4bKXfjyxBxfHz0HyBkmVVoe-A
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "send email successfully.",
  "data": {}
}
```
