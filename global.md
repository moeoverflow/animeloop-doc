## BASEURL

**`https://animeloop.org/api/v2`**

## Global  query keys

| KEY  | VALUE TYPE | EXAMPLE      | DESCRIPTION                              |
| ---- | ---------- | ------------ | ---------------------------------------- |
| cdn  | Boolean    | true / false | Whether to return the CDN resource (default is true) |

?> Currently, the cdn resource url is HTTP, the origin resource url is HTTPS

## Status code

| CODE | MESSAGE               |
| ---- | --------------------- |
| 200  | request successfully  |
| 400  | request format error  |
| 500  | server internal error |

## Basic structure of Response JSON data

#### Success response

```json
{
  "status": "success",
  "code": 200,
  "data": {...DATA...}
}
```

#### Error response

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

?> seriesid and episodeid can be replaced by series and episode details respectively.