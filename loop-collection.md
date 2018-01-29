## Get one collection

**`GET /collection?id=value`** get one collection by id

**`GET /collection?name=value`** get one collection by name

Example request

```bash
curl https://animeloop.org/api/v2/collection?id=1080
curl https://animeloop.org/api/v2/collection?name=nichijou123
```

Example response

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

## Get all collections from user

**`GET /collection?userid=value`**

Example request

```bash
curl -d https://animeloop.org/api/v2/collection?userid=1002
```

Example response

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

## Create new collection

**`POST /collection/new`**

Request body

| KEY         | EXAMPLE                           |
| ----------- | --------------------------------- |
| title       | Nichijou Collection               |
| description | animeloop collection for nichijou |
| name        | nichijou123                       |
| token       | TOKEN                             |

Example request

```bash
curl -d "title=Nichijou Collection&description=animeloop collection for nichijou&name=nichijou123&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/new"
```

Example response

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

## Delele collection

**`POST /collection/delete`**

请求体

| KEY   | EXAMPLE |
| ----- | ------- |
| id    | 1080    |
| token | TOKEN   |

Example request

```bash
curl -d "id=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/delete"
```

Example response

```json
{
  "status": "success",
  "code": 200,
  "message": "delete loop collection successfully.",
  "data": {}
}
```

## Add loops into or remove from collections

**`POST /collection/loop/add`** add loops

**`POST /collection/loop/delete`** remove loops

Request body

| KEY          | EXAMPLE                                  |
| ------------ | ---------------------------------------- |
| loopid       | 591446445f6e5e51d937e111 / [" 591446445f6e5e51d937e111", " 591446445f6e5e51d937e112"] |
| collectionid | 1080                                     |
| token        | TOKEN                                    |

!> The loopid here can be a single MongoDB ObjectId type string, or a JSON array of multiple.

Example request

```bash
curl -d "itemid=[\"591446445f6e5e51d937e111\",\"591446445f6e5e51d937e112\"]&collectionid=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/item/add"

curl -d "itemid=[\"591446445f6e5e51d937e111\",\"591446445f6e5e51d937e112\"]&collectionid=1080&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjQsInVzZXJuYW1lIjoic2hpbmN1cnJ5In0.qduQ3MKwUWMUbfZ5KVkij2DtDGQqagopA7ytHywvU8o" "https://animeloop.org/api/v2/collection/item/delete"
```

Example response

```json
{
  "status": "success",
  "code": 200,
  "message": "add item to collection successfully.",
  "data": {}
}
```

## Get loops from collection

**`GET /loop?collectionid=value&[key=value, ...]`**

Detailes at [Get a group of loops by querying](loop?id=get-a-group-of-loops-by-querying)