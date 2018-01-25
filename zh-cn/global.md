## BASEURL

**`https://animeloop.org/api/v2`**

## 全局  query 键值

| KEY  | VALUE TYPE | EXAMPLE      | DESCRIPTION             |
| ---- | ---------- | ------------ | ----------------------- |
| cdn  | Boolean    | true / false | 是否返回 CDN 资源链接（默认为 true） |

?> 目前 cdn 的资源链接为 HTTP，源站资源链接为 HTTPS

## 错误状态码

| CODE | MESSAGE   |
| ---- | --------- |
| 200  | 请求成功      |
| 400  | 请求格式错误    |
| 500  | 服务器内部未知错误 |

## 请求响应 JSON 数据的基本结构

#### 成功响应

```json
{
  "status": "success",
  "code": 200,
  "data": {...DATA...}
}
```

#### 错误响应

```json
{
  "status": "error",
  "code": ERROR_CODE,
  "message": "...MESSAGE..."
}
```

#### Loop

```json
{
  "id": MongoDB ObjectId,
  "duration": Number,
  "period": {
  "begin": Time String,
  "end": Time String
  },
  "frame": {
    "begin": Number,
    "end": Number
  },
  "sourceFrom": String,
  "uploadDate": Date String,
  "files": {
    "jpg_360p": URL,
    "mp4_360p": URL,
    "gif_360p": URL,
    "jpg_720p": URL,
    "mp4_720p": URL,
    "mp4_1080p": URL,
    "jpg_1080p": URL
  },
  "episodeid": MongoDB ObjectId,
  "seriesid": MongoDB ObjectId
}
```

#### Episode

```json
{
  "id": MongoDB ObjectId,
  "no": String,
  "seriesid": MongoDB ObjectId
}
```

#### Series

```json
{
  "id": MongoDB ObjectId,
  "title": String,
  "title_romaji": String,
  "title_english": String,
  "title_japanese": String,
  "description": String,
  "genres": [String],
  "type": String,
  "total_episodes": 12,
  "anilist_id": 10012,
  "season": String,
  "image_url_large": URL,
  "image_url_banner": URL
}
```

?> seriesid 和 episodeid 可分别被替换为 series 和 episode 详细内容。