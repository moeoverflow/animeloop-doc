## Get one loop by loopid

**`GET /loop?[id=value]`**

?> Get a single loop, it will acquiesce to get the complete data, equivalent to append the `&full=true` query parameter.

Example request

```bash
# Get one loop which loopid is 59adf78ac4c0bc657943222d
curl https://animeloop.org/api/v2/loop?id=59adf78ac4c0bc657943222d
```

Example response

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

## Get a group of loops by querying

**`GET /loop?[query=value, ...]`**

Avaliable query keys

| KEY          | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                              |
| ------------ | ---------------- | ------------------------ | ---------------------------------------- |
| seriesid     | MongoDB ObjectId | 592a63088e46ce684784a6b3 | seriesid of loops                        |
| episodeid    | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | episodeid of loops                       |
| collectionid | Number           | 1080 / 1111              | collectionid of loops                    |
| duration     | Number (Second)  | 0,1 / 1.5,2.0            | range of duration of loops               |
| source_from  | String           | automator / upload       | source of loops                          |
| full         | Boolean          | true / false             | Whether to return the full loops (including series and episode) (default is false) |
| page         | Number           | 11                       | loops on page N (default: first page)    |
| limit        | Number           | 20                       | The number of bangumi per page(default 30, max 100) |

!> It should be 
noted that if you need series and episode filter conditions here, you 
only need to provide one, if two key values are provided and the episode
 is not in the series, it will return empty data.

Example request

```bash
# Get loops on first page (3 loops per page) which seriesid is 592a63088e46ce684784a6b3 and range of duration is between 1.5s and 2.0s
https://animeloop.org/api/v1/loop?seriesid=592a63088e46ce684784a6b3&duration=1.5,2.0&limit=3
```

Example response

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

## Get count of loops

**`GET /loop/count?[query=value, ...]`**

The available query keys are the same as above except for the `page` and` limit` fields.

Example Request

```bash
curl https://animeloop.org/api/v2/loop/count?duration=3.0,4.0
```

Example Response

```json
{
  "status": "success",
  "code":200, 
  "message":"success", 
  "data": {
    "count": 3690
  }
}
```

## Get a group of random loops

**`GET /rand/loop?[query=value, ...]`**

Avaliable query keys

| KEY         | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                              |
| ----------- | ---------------- | ------------------------ | ---------------------------------------- |
| seriesid    | MongoDB ObjectId | 592a63088e46ce684784a6b3 | seriesid of loops                        |
| episodeid   | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | episodeid of loops                       |
| duration    | Number (Second)  | 0,1 / 1.5,2.0            | range of duration of loops               |
| source_from | String           | automator / upload       | source of loops                          |
| full        | Boolean          | true / false             | Whether to return the full loops (including series and episode) (default is false) |
| limit       | Number           | 20                       | The number of bangumi per page(default 30, max 100) |

!> Note that, when using the limit field, if the limit is 1, the result returned is still an array.

Example request

```bash
# Get three random loops which range of duration is between on 3s and 4s.
curl https://animeloop.org/api/v2/rand/loop?duration=3.0,4.0&limit=3
```

Example Response

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

## Get one random loop resource file

**`GET /rand/loop-{size}.{type}?[query=value, ...]`**

Avaliable size and type

| SIZE  | TYPE | FILE NAME      |
| ----- | ---- | -------------- |
| 360p  | gif  | loop-360p.gif  |
| 360p  | mp4  | loop-360p.mp4  |
| 360p  | jpg  | loop-360p.jpg  |
| 720p  | mp4  | loop-720p.mp4  |
| 720p  | jpg  | loop-720p.jpg  |
| 1080p | mp4  | loop-1080p.mp4 |
| 1080p | jpg  | loop-1080p.jpg |

Avaliable query keys

| KEY         | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                |
| ----------- | ---------------- | ------------------------ | -------------------------- |
| seriesid    | MongoDB ObjectId | 592a63088e46ce684784a6b3 | seriesid of loops          |
| episodeid   | MongoDB ObjectId | 591b2b9268f9f00f82bf35ba | episodeid of loops         |
| duration    | Number (Second)  | 0,1 / 1.5,2.0            | range of duration of loops |
| source_from | String           | automator / upload       | source of loops            |

?> This
 interface will randomly return a loop resource file for each request, 
suitable for calling directly within `<img>` or `<video>`.

Example request

```bash
# Get a random loop resource file which range of duration is between 0.5s and 1.5s.
curl https://animeloop.org/api/v2/rand/loop-720p.mp4?duration=0.5,1.5
```

Response header

```http 
HTTP/1.1 200 OK
Content-Type: video/mp4
Content-Length: 203883
```
