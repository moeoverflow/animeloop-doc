## 获取单个合集

**`GET /collection?id=value`** 通过合集 id 获取

**`GET /collection?name=value`** 通过合集名称获取

示例请求

```bash
curl https://animeloop.org/api/v2/collection?id=1080
curl https://animeloop.org/api/v2/collection?name=nichijou123
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "success",
  "data": [
    {
      "userid": 1002,
      "name": "nichijou123",
      "description": "animeloop collection for nichijou",
      "title": "Nichijou collection",
      "cid": 1080
    }
  ]
}
```

## 获取某个用户创建的所有合集

**`GET /collection?userid=value`**

示例请求

```bash
curl -d https://animeloop.org/api/v2/collection?userid=1002
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "success",
  "data": [
    {
      "userid": 1002,
      "name": "nichijou123",
      "description": "animeloop collection for nichijou",
      "title": "Nichijou Collection",
      "cid": 1080
    },
    {
      "userid": 1002,
      "name": "test_collection",
      "description": "test_collection_description",
      "title": "test_collection_title",
      "cid": 1081
    }
  ]
}
```

## 创建合集

**`POST /collection/new`**

请求体

| KEY         | EXAMPLE                           |
| ----------- | --------------------------------- |
| title       | Nichijou Collection               |
| description | animeloop collection for nichijou |
| name        | nichijou123                       |
| token       | TOKEN                             |

示例请求

```bash
curl -d "title=Nichijou Collection&description=animeloop collection for nichijou&name=nichijou123&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/new"
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "create loop collection successfully.",
  "data": {
    "id": "5a6eb42d3ace8f06b2880fc6",
    "cid": 1080,
    "title": "Nichijou Collection",
    "description": "animeloop collection for nichijou"
  }
}
```

## 删除合集

**`POST /collection/delete`**

请求体

| KEY   | EXAMPLE |
| ----- | ------- |
| id    | 1080    |
| token | TOKEN   |

示例请求

```bash
curl -d "id=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/delete"
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "delete loop collection successfully.",
  "data": {}
}
```

## 在合集中添加或删除 loops

**`POST /collection/loop/add`** 添加 loops

**`POST /collection/loop/delete`** 删除 loops

请求体

| KEY          | EXAMPLE                                  |
| ------------ | ---------------------------------------- |
| loopid       | 591446445f6e5e51d937e111 / [" 591446445f6e5e51d937e111", " 591446445f6e5e51d937e112"] |
| collectionid | 1080                                     |
| token        | TOKEN                                    |

!> 这里的 loopid 可以是单个 MongoDB ObjectId 类型字符串，或者多个值组合而成的 JSON 数组。

示例请求

```bash
curl -d "itemid=[\"591446445f6e5e51d937e111\",\"591446445f6e5e51d937e112\"]&collectionid=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/item/add"

curl -d "itemid=[\"591446445f6e5e51d937e111\",\"591446445f6e5e51d937e112\"]&collectionid=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/item/delete"
```

返回结果

```json
{
  "status": "success",
  "code": 200,
  "message": "add item to collection successfully.",
  "data": {}
}
```

## 获取某个合集中的 loops

**`GET /loop?collectionid=value&[key=value, ...]`**

详细参见 [通过 query 条件筛选获取一组 loops](zh-cn/loop?id=%e9%80%9a%e8%bf%87-query-%e6%9d%a1%e4%bb%b6%e7%ad%9b%e9%80%89%e8%8e%b7%e5%8f%96%e4%b8%80%e7%bb%84-loops)