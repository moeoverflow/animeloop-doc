## Get one series by seriesid

**`GET /series[?id=value]`**

Example Request

```bash
Get one series which seriesid is 592a63088e46ce684784a6b3
curl https://animeloop.org/api/v2/series?id=592a63088e46ce684784a6b3
```

Example Response

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

## Get a group of bangumi by querying

**`GET /series?[query=value, ...]`**

available query keys

| KEY    | VALUE TYPE | EXAMPLE          | DESCRIPTION                              |
| ------ | ---------- | ---------------- | ---------------------------------------- |
| type   | String     | OVA / TV / Movie | type of bangumi                          |
| season | String     | 2015-4 / 2018-1  | season of bangumi                        |
| page   | Number     | 11               | bangumi on page N                        |
| limit  | Number     | 20               | The number of bangumi per page(default 30) |

Example Request

```bash
Get a group of bangumi on page 1 on January 2015(3 bangumi per page）
curl https://animeloop.org/api/v2/series?season=2015-1
```

Example Response

```json
{
  "status": "success",
  "code": 200,
  "message": "success",
  "data": [
    {
      "id": "593f5b157cd4fa1d287e66c3",
      "title": "艦隊Collection",
      "title_romaji": "Kantai Collection: KanColle",
      "title_english": "KanColle",
      "title_japanese": "艦隊これくしょん -艦これ-",
      "description": "The base for the fleet arrayed against the \"deep sea fleet\" is Chinjufu. There, many various Kan-musume have gathered to live together and work hard everyday in training and other matters. One day, a Kan-musume arrives at Chinjufu, She is a special class of destroyer. Her name is Fubuki. \"I am Fubuki! Nice to meet you!\" Fubuki's story — as well as the Kan-musume's story — begins now.<br>\r\n<br>\r\n(Source: ANN)",
      "genres": [
        "Action",
        "Sci-Fi"
      ],
      "type": "TV",
      "total_episodes": 12,
      "anilist_id": 20553,
      "season": "2015-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20553/image_large.jpg"
    },
    {
      "id": "5948e63f0a87686840560ecf",
      "title": "心理测量者 劇場版",
      "title_romaji": "Psycho-Pass Movie",
      "title_english": "Psycho-Pass Movie",
      "title_japanese": "劇場版 Psycho-Pass サイコパス",
      "description": "Year 2116 – The Japanese government begins to export the Sibyl System unmanned drone robots to troubled countries, and the system spreads throughout the world. A state in the midst of a civil war, SEAUn (the South East Asia Union), brings in the Sibyl System as an experiment. Under the new system, the coastal town of Shambala Float achieves temporary peace and safety. But then SEAUn sends terrorists to Japan. They slip through the Sibyl System and then attack from within. The shadow of a certain man falls on this incident. In charge of the police, Tsunemori travels to Shambala Float to investigate. The truth of justice on this new ground will become clear.",
      "genres": [
        "Action",
        "Sci-Fi"
      ],
      "type": "Movie",
      "total_episodes": 1,
      "anilist_id": 20514,
      "season": "2015-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20514/image_large.jpg"
    },
    {
      "id": "5961383dbc2ef8075782ae36",
      "title": "純潔的瑪利亞",
      "title_romaji": "Junketsu no Maria",
      "title_english": "Maria the Virgin Witch",
      "title_japanese": "純潔のマリア",
      "description": "The story follows Maria, the most powerful witch who lives during the Hundred Years' War in France. She despises war, so she obstructs battles with her strong magical powers. Her meddling with her succubus Artemis and incubus Priapos has caught the attention of the heavens, and so the Archangel Michael issues an edict. When Maria loses her virginity, she will also lose her magical powers. A beautiful angel named Ezekiel is supposed to watch Maria and make sure the witch does not use magic in front of people, but Maria continues to use magic anyways.<br>\r\n<br>\r\n(Source: ANN)",
      "genres": [],
      "type": "TV",
      "total_episodes": 12,
      "anilist_id": 20840,
      "season": "2015-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20840/image_large.jpg"
    },
    {
      "id": "599054306fc77f5980d7dac8",
      "title": "不起眼女主角培育法",
      "title_romaji": "Saenai Heroine no Sodatekata",
      "title_english": "Saekano: How to Raise a Boring Girlfriend",
      "title_japanese": "冴えない彼女の育てかた",
      "description": "The life of Tomoyo Aki, a highschool otaku working part time to support his BD hording. With remarkable luck, he bumps head-first into, Megumi Kato, the most beautiful girl he has ever seen. Naturally, the meeting twists his life into a complicated torrent of relationships. Eriri Spencer Sawamura, his half-foreigner childhood friend who’s always valued her relationship with MC. Kasumigaoka Utaha, a cold, composed renowned literary genius who shoves everyone aside from our protagonist. What is this? An eroge introduction?\n<br><br>\nThe tale of a small not quite doujin circle, but not quite indie studio’s journey through the tough territory of comiket and beyond.<br>\n<br>\n<i>This includes \"Episode 0.\"</i>",
      "genres": [
        "Comedy",
        "Romance",
        "Slice of Life"
      ],
      "type": "TV",
      "total_episodes": 13,
      "anilist_id": 20657,
      "season": "2015-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20657/image_large.jpg"
    },
    {
      "id": "59c7ccff7b994e05711a32e6",
      "title": "死亡遊行",
      "title_romaji": "Death Parade",
      "title_english": "Death Parade",
      "title_japanese": "デス・パレード",
      "description": "\"Welcome to Quindecim\" What greets two unsuspecting guests is a strange bar, Quindecim, and the white-haired bartender, Decim. \"From here you two shall begin a battle where your lives hang in the balance,\" he says to introduce the Death Game. Before long the guests' true natures become apparent. As a matter of course, at the game's end Decim is revealed to be the \"arbiter.\" Decim's judgement on the two guests is...<br>\n<br>\n(Source: ANN)",
      "genres": [
        "Drama",
        "Mystery",
        "Psychological",
        "Supernatural"
      ],
      "type": "TV",
      "total_episodes": 12,
      "anilist_id": 20931,
      "season": "2015-1",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20931/image_large.jpg"
    }
  ]
}
```

## Get count of bangumi

**`GET /series/count?[query=value, ...]`**

The available query keys are the same as above except for the `page` and` limit` fields.

Example Request

```bash
curl https://animeloop.org/api/v2/series/count
```

Example Response

```json
{
  "status": "success",
  "code":200, 
  "message":"success", 
  "data": {
    "count": 495
  }
}
```

## Seach bangumi 

**`GET /search/series?[value=[keyword1, ...]`**

Example Request

```bash
curl https://animeloop.org/api/v2/search/series?value=Sakura
```

Example Response

```json
{
  "status": "success",
  "code": 200,
  "message": "success",
  "data": [
    {
      "id": "59357b0ca5c49d761ccff7c9",
      "title": "月刊少女野崎君",
      "title_romaji": "Gekkan Shoujo Nozaki-kun",
      "title_english": "Monthly Girls' Nozaki-kun",
      "title_japanese": "月刊少女野崎くん",
      "description": "The romantic comedy story begins when high school student Sakura Chiyo confesses her feelings to her classmate Nozaki. Due to a misunderstanding, Nozaki thinks Sakura is just a fan of his shoujo manga work. Sakura has to convey her true feelings while her relationship with Nozaki develops. \r\n<br><br>\r\n(Source: ANN)",
      "genres": [
        "Comedy",
        "Romance"
      ],
      "type": "TV",
      "total_episodes": 12,
      "anilist_id": 20668,
      "season": "2014-7",
      "image_url_large": "http://cdn.animeloop.org/files/anilist/20668/image_large.jpg"
    }
  ]
}
```

