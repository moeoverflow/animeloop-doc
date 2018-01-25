## 通过 episodeid 来获取单个 episode 的数据

**`GET /episode?[id=value]`**

示例请求

```bash
获取 episodeid 为 591b2b9268f9f00f82bf35ba 的 episode 数据
curl https://animeloop.org/api/v2/episode?id=591b2b9268f9f00f82bf35ba
```

返回结果

```json
{
  "status": "success",
  "data": {
    "id": "591b2b9268f9f00f82bf35ba",
    "no": "01",
    "series": {
      "id": "592a63088e46ce684784a6b3",
      "title": "小魔女學院",
      "title_romaji": "Little Witch Academia (TV)",
      "title_english": "Little Witch Academia (TV)",
      "title_japanese": "リトルウィッチアカデミア (TV)",
      "description": "TV series of Little Witch Academia.",
      "genres": [
        "Adventure",
        "Comedy",
        "Fantasy"
      ],
      "type": "TV",
      "total_episodes": 25,
      "anilist_id": 21858,
      "season": "2017-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/21858/image_large.jpg"
    }
  }
}
```

## 通过 query 筛选获取一组 episodes

**`GET /episode?[query=value, ...]`**

可用的 query 键值：

| KEY      | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                    |
| -------- | ---------------- | ------------------------ | ------------------------------ |
| seriesid | MongoDB ObjectId | 592a63088e46ce684784a6b3 | episodes 所在的 seriesid          |
| no       | String           | 01 / OVA / Movie         | episode 序号                     |
| full     | Boolean          | true / false             | 是否返回完整的 episodes 数据（包括 series） |
| page     | Number           | 11                       | 获取第 N 页的 loops 数据              |
| limit    | Number           | 20                       | 每一页的数据量（默认为 30）                |

示例请求

```bash
获取 seriesid 为 592a63088e46ce684784a6b3 且完整的第一页 episodes（每页 2 个 episodes）
curl https://animeloop.org/api/v2/episode?series=592a63088e46ce684784a6b3&full=true&limit=2
```

返回结果

```json
{
  "status": "success",
  "data": [
    {
      "id": "591b2b9268f9f00f82bf35ba",
      "no": "01",
      "series": {
        "id": "592a63088e46ce684784a6b3",
        "title": "小魔女學院",
        "title_romaji": "Little Witch Academia (TV)",
        "title_english": "Little Witch Academia (TV)",
        "title_japanese": "リトルウィッチアカデミア (TV)",
        "description": "TV series of Little Witch Academia.",
        "genres": [
          "Adventure",
          "Comedy",
          "Fantasy"
        ],
        "type": "TV",
        "total_episodes": 25,
        "anilist_id": 21858,
        "season": "2017-1",
        "image_url_large": "http://cdn.animeloop.org/files/anilist/21858/image_large.jpg"
      }
    },
    {
      "id": "591b2b9268f9f00f82bf35bb",
      "no": "02",
      "series": {
        "id": "592a63088e46ce684784a6b3",
        "title": "小魔女學院",
        "title_romaji": "Little Witch Academia (TV)",
        "title_english": "Little Witch Academia (TV)",
        "title_japanese": "リトルウィッチアカデミア (TV)",
        "description": "TV series of Little Witch Academia.",
        "genres": [
          "Adventure",
          "Comedy",
          "Fantasy"
        ],
        "type": "TV",
        "total_episodes": 25,
        "anilist_id": 21858,
        "season": "2017-1",
        "image_url_large": "http://cdn.animeloop.org/files/anilist/21858/image_large.jpg"
      }
    }
  ]
}
```

