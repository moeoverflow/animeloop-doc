## Get one episode by episodeid

**`GET /episode?[id=value]`**

Example Request

```bash
Get one episode which episodeid is 591b2b9268f9f00f82bf35ba
curl https://animeloop.org/api/v2/episode?id=591b2b9268f9f00f82bf35ba
```

Example Response

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

## Get a group of episodes by querying

**`GET /episode?[query=value, ...]`**

Avaliable query keys

| KEY      | VALUE TYPE       | EXAMPLE                  | DESCRIPTION                              |
| -------- | ---------------- | ------------------------ | ---------------------------------------- |
| seriesid | MongoDB ObjectId | 592a63088e46ce684784a6b3 | seriesid of episodes                     |
| no       | String           | 01 / OVA / Movie         | episode no                               |
| full     | Boolean          | true / false             | Whether to return complete episodes (including series) (default is false) |
| page     | Number           | 11                       | loops on page N (default: first page)    |
| limit    | Number           | 20                       | The number of bangumi per page(default 30, max 100) |

Example Request

```bash
Get a group of full episodes on first page (2 episodes per page) which seriesid is 592a63088e46ce684784a6b3
curl https://animeloop.org/api/v2/episode?series=592a63088e46ce684784a6b3&full=true&limit=2
```

Example Response

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

