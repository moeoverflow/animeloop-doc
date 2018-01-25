## 通过 loopid 来获取单个 loop 的数据

**`GET /loop?[id=value]`**

?> 在获取单个 loop 的时候，会默认获取完整的数据，相当于附加上 `&full=true` 参数。

示例请求

```bash
# 获取 loopid 为 59adf78ac4c0bc657943222d 的 loop 数据
curl https://animeloop.org/api/v2/loop?id=59adf78ac4c0bc657943222d
```

返回结果

```json
{
  "status": "success",
  "data": {
    "id": "59adf78ac4c0bc657943222d",
    "duration": 0.7507499999999999,
    "period": {
      "begin": "00:22:47.783000",
      "end": "00:22:48.533000"
    },
    "frame": {
      "begin": 32794,
      "end": 32812
    },
    "sourceFrom": "automator",
    "uploadDate": "2017-09-05T01:00:26.913Z",
    "files": {
      "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/59adf78ac4c0bc657943222d.jpg",
      "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/59adf78ac4c0bc657943222d.mp4",
      "gif_360p": "http://cdn.animeloop.org/files/gif_360p/59adf78ac4c0bc657943222d.gif",
      "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/59adf78ac4c0bc657943222d.jpg",
      "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/59adf78ac4c0bc657943222d.mp4",
      "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/59adf78ac4c0bc657943222d.mp4",
      "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/59adf78ac4c0bc657943222d.jpg"
    },
    "episode": {
      "id": "59adf789c4c0bc65794321fb",
      "no": "13",
      "seriesid": "59adb3f8c4c0bc6579431f49"
    },
    "series": {
      "id": "59adb3f8c4c0bc6579431f49",
      "title": "LoveLive! 2期",
      "title_romaji": "Love Live! School Idol Project 2nd Season",
      "title_english": "Love Live! School Idol Project 2nd Season",
      "title_japanese": "ラブライブ! School idol project 2期",
      "description": "The girls of μ's are back! A second Love Live! contest is happening. This is the last time all nine girls can try to win together.",
      "genres": [
        "Music",
        "Slice of Life"
      ],
      "type": "TV",
      "total_episodes": 13,
      "anilist_id": 19111,
      "season": "2014-4",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/19111/image_large.jpg"
    }
  }
}
```

## 通过 query 条件筛选获取一组 loops

**`GET /loop?[query=value, ...]`**

可用的 query 键值：

| KEY         | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                              |
| ----------- | ---------------- | ------------------------ | ---------------------------------------- |
| seriesid    | MongoDB ObjectId | 592a63088e46ce684784a6b3 | loops 所在的 seriesid                       |
| episodeid   | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | loops 所在的 episodeid                      |
| duration    | Number (Second)  | 0,1 / 1.5,2.0            | loops 的时间长度                              |
| source_from | String           | automator / upload       | loop 的来源                                 |
| full        | Boolean          | true / false             | 是否返回完整的 loop 数据（包括 series 和 episode 数据）（默认为 false） |
| page        | Number           | 11                       | 获取第 N 页的 loops 数据（默认为 1）                 |
| limit       | Number           | 20                       | 每一页的数量（默认为 30，最高不超过 100）                 |

!> 需要注意的是，如果这里需要 series 和 episode 做筛选条件的话，只需要提供其中一个，如果两个键值都提供而 episode 不在 series 里面，那么将返回空数据。



示例请求

```bash
获取 seriesid 为 592a63088e46ce684784a6b3 且 duration 大于 1.5s 小于 2.0s 的第一页 loops（每页 3 个 loops）
https://animeloop.org/api/v1/loop?seriesid=592a63088e46ce684784a6b3&duration=1.5,2.0&limit=3
```

返回结果

```json
{
  "status": "success",
  "data": [
    {
      "id": "591446445f6e5e51d937e118",
      "duration": 1.6683333333333332,
      "period": {
        "begin": "00:06:13",
        "end": "00:06:14"
      },
      "frame": {
        "begin": 8935,
        "end": 8975
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-05-20T10:30:45.801Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/591446445f6e5e51d937e118.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/591446445f6e5e51d937e118.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/591446445f6e5e51d937e118.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/591446445f6e5e51d937e118.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/591446445f6e5e51d937e118.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/591446445f6e5e51d937e118.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/591446445f6e5e51d937e118.jpg"
      },
      "episodeid": "591b2b9868f9f00f82bf3641",
      "seriesid": "591b2b9868f9f00f82bf3640"
    },
    {
      "id": "591446445f6e5e51d937e153",
      "duration": 1.5014999999999998,
      "period": {
        "begin": "00:08:27",
        "end": "00:08:29"
      },
      "frame": {
        "begin": 12158,
        "end": 12194
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-05-20T10:30:45.801Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/591446445f6e5e51d937e153.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/591446445f6e5e51d937e153.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/591446445f6e5e51d937e153.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/591446445f6e5e51d937e153.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/591446445f6e5e51d937e153.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/591446445f6e5e51d937e153.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/591446445f6e5e51d937e153.jpg"
      },
      "episodeid": "591b2b9968f9f00f82bf3644",
      "seriesid": "591b2b9868f9f00f82bf3640"
    },
    {
      "id": "591446445f6e5e51d937e168",
      "duration": 1.5972696245733788,
      "period": {
        "begin": "00:13:28",
        "end": "00:13:30"
      },
      "frame": {
        "begin": 19727,
        "end": 19766
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-05-20T10:30:45.801Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/591446445f6e5e51d937e168.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/591446445f6e5e51d937e168.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/591446445f6e5e51d937e168.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/591446445f6e5e51d937e168.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/591446445f6e5e51d937e168.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/591446445f6e5e51d937e168.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/591446445f6e5e51d937e168.jpg"
      },
      "episodeid": "591b2b9968f9f00f82bf3645",
      "seriesid": "591b2b9868f9f00f82bf3640"
    }
  ]
}
```

## 随机获取一组 loops

**`GET /rand/loop?[query=value, ...]`**

可用的 query 键值：

| KEY         | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                              |
| ----------- | ---------------- | ------------------------ | ---------------------------------------- |
| seriesid    | MongoDB ObjectId | 592a63088e46ce684784a6b3 | loops 所在的 seriesid                       |
| episodeid   | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | loops 所在的 episodeid                      |
| duration    | Number (Second)  | 0,1 / 1.5,2.0            | loops 的时间长度                              |
| source_from | String           | automator / upload       | loop 的来源                                 |
| full        | Boolean          | true / false             | 是否返回完整的 loop 数据（包括 series 和 episode 数据）（默认为 false） |
| limit       | Number           | 20                       | 随机获取 loops 的数量（默认为 30，最高不超过 100）         |

!> 需要注意的是，使用 limit 字段的时候，如果 limit 为 1，返回的结果仍然是一个数组。

示例请求

```bash
# 随机获取时长在 3s 到 4s 之间的三个 loops
curl https://animeloop.org/api/v2/rand/loop?duration=3.0,4.0&limit=3
```

返回结果

```json
{
  "status": "success",
  "data": [
    {
      "id": "59a02ed56c4805500909ab5c",
      "duration": 3.128125,
      "period": {
        "begin": "00:00:40.331000",
        "end": "00:00:43.460000"
      },
      "frame": {
        "begin": 967,
        "end": 1042
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-08-25T14:05:10.369Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/59a02ed56c4805500909ab5c.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/59a02ed56c4805500909ab5c.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/59a02ed56c4805500909ab5c.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/59a02ed56c4805500909ab5c.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/59a02ed56c4805500909ab5c.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/59a02ed56c4805500909ab5c.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/59a02ed56c4805500909ab5c.jpg"
      },
      "episodeid": "593e24cba793aa30a98f128f",
      "seriesid": "593dffbda793aa30a98f1247"
    },
    {
      "id": "59835a19ed0b995c09a26793",
      "duration": 3.2115416666666663,
      "period": {
        "begin": "00:13:46.825000",
        "end": "00:13:50.037000"
      },
      "frame": {
        "begin": 19824,
        "end": 19901
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-08-03T17:14:08.223Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/59835a19ed0b995c09a26793.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/59835a19ed0b995c09a26793.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/59835a19ed0b995c09a26793.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/59835a19ed0b995c09a26793.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/59835a19ed0b995c09a26793.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/59835a19ed0b995c09a26793.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/59835a19ed0b995c09a26793.jpg"
      },
      "episodeid": "59835a18ed0b995c09a26779",
      "seriesid": "59833f73ed0b995c09a266af"
    },
    {
      "id": "5953236797d7cf18a418ff85",
      "duration": 3.3366666666666664,
      "period": {
        "begin": "00:10:07.690000",
        "end": "00:10:11.027000"
      },
      "frame": {
        "begin": 14570,
        "end": 14650
      },
      "sourceFrom": "automator",
      "uploadDate": "2017-06-28T03:31:03.441Z",
      "files": {
        "jpg_360p": "http://cdn.animeloop.org/files/jpg_360p/5953236797d7cf18a418ff85.jpg",
        "mp4_360p": "http://cdn.animeloop.org/files/mp4_360p/5953236797d7cf18a418ff85.mp4",
        "gif_360p": "http://cdn.animeloop.org/files/gif_360p/5953236797d7cf18a418ff85.gif",
        "jpg_720p": "http://cdn.animeloop.org/files/jpg_720p/5953236797d7cf18a418ff85.jpg",
        "mp4_720p": "http://cdn.animeloop.org/files/mp4_720p/5953236797d7cf18a418ff85.mp4",
        "mp4_1080p": "http://cdn.animeloop.org/files/mp4_1080p/5953236797d7cf18a418ff85.mp4",
        "jpg_1080p": "http://cdn.animeloop.org/files/jpg_1080p/5953236797d7cf18a418ff85.jpg"
      },
      "episodeid": "5953236197d7cf18a418ff6c",
      "seriesid": "59531b3097d7cf18a418ff51"
    }
  ]
}
```

## 随机获取一个 loop 资源文件

**`GET /rand/loop-{size}.{type}?[query=value, ...]`**

可用的尺寸和类型

| SIZE  | TYPE | FILE NAME      |
| ----- | ---- | -------------- |
| 360p  | gif  | loop-360p.gif  |
| 360p  | mp4  | loop-360p.mp4  |
| 360p  | jpg  | loop-360p.jpg  |
| 720p  | mp4  | loop-720p.mp4  |
| 720p  | jpg  | loop-720p.jpg  |
| 1080p | mp4  | loop-1080p.mp4 |
| 1080p | jpg  | loop-1080p.jpg |

可用的 query 键值：

| KEY         | VALUE TYPE       | EXAMPLE                  | DESCRIPTION         |
| ----------- | ---------------- | ------------------------ | ------------------- |
| seriesid    | MongoDB ObjectId | 592a63088e46ce684784a6b3 | loops 所在的 seriesid  |
| episodeid   | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | loops 所在的 episodeid |
| duration    | Number (Second)  | 0,1 / 1.5,2.0            | loops 的时间长度         |
| source_from | String           | automator / upload       | loop 的来源            |

?> 这个接口每次请求都会随机返回一个 loop 资源文件，适合于直接在 `<img>` 或者 `<video>` 内调用。

示例请求

```bash
# 随机获取一个时长在 0.5s-1.5s 之间的 loop 资源文件
curl https://animeloop.org/api/v2/rand/loop-720p.mp4?duration=0.5,1.5
```

返回响应头

```http 
HTTP/1.1 200 OK
Content-Type: video/mp4
Content-Length: 203883
```
