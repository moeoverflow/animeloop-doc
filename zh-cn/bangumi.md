## 通过 seriesid 来获取单个 series 的数据

**`GET /series[?id=value]`**

示例请求

```bash
获取 seriesid 为 592a63088e46ce684784a6b3 的 series 数据
curl https://animeloop.org/api/v2/series?id=592a63088e46ce684784a6b3
```

返回结果

```json
{
  "status": "success",
  "data": {
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
```

## 通过 query 筛选获取一组 series

**`GET /series?[query=value, ...]`**

可用的 query 键值：

| KEY    | VALUE TYPE | EXAMPLE          | DESCRIPTION        |
| ------ | ---------- | ---------------- | ------------------ |
| type   | String     | OVA / TV / Movie | series 类型          |
| season | String     | 2015-4 / 2018-1  | 番剧播放季度             |
| page   | Number     | 11               | 获取第 N 页的 series 数据 |
| limit  | Number     | 20               | 每一页的数量（默认为 30）     |

示例请求

```bash
获取2015年1月番剧第一页的 series（每页 3 个 series）
curl https://animeloop.org/api/v1/series?season=2015-1
```

返回结果

```json
{
  "status": "success",
  "data": [
    {
      "id": "591b2b9868f9f00f82bf3640",
      "title": "幻想嘉年华",
      "title_romaji": "Carnival Phantasm",
      "title_english": "Carnival Phantasm",
      "title_japanese": "カーニバル・ファンタズム",
      "description": "Carnival Phantasm is an adaption of the manga \"Take Moon\" by Type-Moon's Eri Takenashi, to celebrate Type-Moon's 10th Anniversary.<br><br>\nCarnival Phantasm shows parodies and new stories loosely based on Type-Moon's original works like Melty Blood, Fate/Stay Night, Tsukihime, and more.",
      "genres": [
        "Comedy",
        "Supernatural"
      ],
      "type": "OVA",
      "total_episodes": 12,
      "anilist_id": 10012,
      "season": "2011-8",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/10012/image_large.jpg"
    },
    {
      "id": "592553f935b31b2fc80e7b67",
      "title": "真实之泪",
      "title_romaji": "True Tears",
      "title_english": "True Tears",
      "title_japanese": "True Tears",
      "description": "Shinichiro is a student living in what would be a dream come true for most high school boys, but for him is mostly a frustration. A well liked girl in school named Hiromi has lived in his house for a year along with his family. Her father was a close friend of the family, and when he died they immediately took her in. She is popular and well liked, always smiles, is talented in sports- but Shinichiro knows there must be tears inside her. Having an artistic tendency, he makes watercolours of her and thinks about wishing to ease her tears. Yet he cannot bring up the nerve to talk to her even in his own home. She, too, is quiet and withdrawn in their house, quite unlike at school. Shinichiro is also distracted by teasing from his friend Nobuse for watching Hiromi from afar, a curse of bad luck from a strange girl named Noe, and being forced to perform Muhiga dancing. By helping Noe he hopes to ease his own problems, yet he seems to have difficulty helping himself.<br><br>\n(Source: ANN)",
      "genres": [
        "Drama",
        "Romance"
      ],
      "type": "TV",
      "total_episodes": 13,
      "anilist_id": 2129,
      "season": "2008-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/2129/image_large.jpg"
    },
    {
      "id": "5925c2232ab64839a477b768",
      "title": "聲之形",
      "title_romaji": "Koe no Katachi",
      "title_english": "A Silent Voice",
      "title_japanese": "聲の形",
      "description": "I wish we had never met. I wish we could meet once again. A boy who can hear, Shoya Ishida, and a transfer student who can't, Shoko Nishimiya. One fateful day, the two meet, and Shoya leads the class in bullying Shoko. But before long, the class shifts its target from Shoko to Shoya. Years later, Shoya feels strongly that he must see Shoko once again.<br>\r\n<br>\r\n(Source: Crunchyroll)",
      "genres": [
        "Drama",
        "Romance"
      ],
      "type": "Movie",
      "total_episodes": 1,
      "anilist_id": 20954,
      "season": "2016-9",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20954/image_large.jpg"
    }
  ]
}
```
