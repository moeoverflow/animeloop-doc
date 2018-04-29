## 通过 query 条件筛选获取一组 tags

**`GET /tag?[query=value, ...]`**

可用的 query 键值：

| KEY        | VALUE TYPE       | EXAMPLE                     | DESCRIPTION       |
| ---------- | ---------------- | --------------------------- | ----------------- |
| loopid     | MongoDB ObjectId | 592a63088e46ce684784a6b3    | tags 所在的 loopid   |
| type       | String           | general /  character / safe | tag 类型            |
| source     | Boolean          | true / false                | tag 的源出处          |
| confidence | Number           | 0.85,0.9 / 0.95,0.99        | tag 的可信度          |
| page       | Number           | 11                          | 获取第 N 页的 loops 数据 |
| limit      | Number           | 20                          | 每一页的数据量（默认为 30，最高不超过 1000）   |

示例请求

```bash
获取 loopid 为 59adf78ac4c0bc657943222d 的所有 character 类型 tags
curl https://animeloop.org/api/v2/tag?loopid=59adf78ac4c0bc657943222d&type=character
```

返回结果

```json
{
  "status": "success",
  "data": [
    {
      "type": "character",
      "loopid": "59af49e17a6bd32cad3ad52f",
      "source": "illustration2vec",
      "value": "nishikino maki",
      "confidence": 0.992725133895874,
      "id": "59e5b1f17321a02650a39516"
    },
    {
      "type": "character",
      "loopid": "59af49e17a6bd32cad3ad52f",
      "source": "illustration2vec",
      "value": "ayase eli",
      "confidence": 0.7277906537055969,
      "id": "59e5b1f17321a02650a39517"
    },
    {
      "type": "character",
      "loopid": "5992619ebca076360b842c7d",
      "source": "illustration2vec",
      "value": "kyon",
      "confidence": 0.8927875757217407,
      "id": "59e5b1fd7321a02650a39605"
    },
    {
      "type": "character",
      "loopid": "5992619ebca076360b842c7d",
      "source": "illustration2vec",
      "value": "kyonko",
      "confidence": 0.5385593771934509,
      "id": "59e5b1fd7321a02650a39606"
    },
    {
      "type": "character",
      "loopid": "59c8f3877b994e05711a368e",
      "source": "illustration2vec",
      "value": "fujiwara no mokou",
      "confidence": 0.5810472369194031,
      "id": "59e5b2007321a02650a39651"
    },
    {
      "type": "character",
      "loopid": "59c2a97d7b994e05711a2cda",
      "source": "illustration2vec",
      "value": "amami haruka",
      "confidence": 0.9253234267234802,
      "id": "59e5b2017321a02650a3965a"
    },
    {
      "type": "character",
      "loopid": "59c2a97d7b994e05711a2cda",
      "source": "illustration2vec",
      "value": "hagiwara yukiho",
      "confidence": 0.6046148538589478,
      "id": "59e5b2017321a02650a3965b"
    },
    {
      "type": "character",
      "loopid": "59a27a9f354a8f1df8c575f6",
      "source": "illustration2vec",
      "value": "sakura kyouko",
      "confidence": 0.564988374710083,
      "id": "59e5b2027321a02650a3967d"
    },
    {
      "type": "character",
      "loopid": "598d5288faa55762ad219b52",
      "source": "illustration2vec",
      "value": "tomoe mami",
      "confidence": 0.7448060512542725,
      "id": "59e5b2077321a02650a396ea"
    },
    {
      "type": "character",
      "loopid": "59991a6040b3de5d2126fc4d",
      "source": "illustration2vec",
      "value": "emiya kiritsugu",
      "confidence": 0.889092743396759,
      "id": "59e5b2087321a02650a396fb"
    },
    {
      "type": "character",
      "loopid": "598f4fb10e0dc5102456cf18",
      "source": "illustration2vec",
      "value": "uiharu kazari",
      "confidence": 0.6244797110557556,
      "id": "59e5b2097321a02650a39714"
    },
    {
      "type": "character",
      "loopid": "598f4fb10e0dc5102456cf18",
      "source": "illustration2vec",
      "value": "misaka mikoto",
      "confidence": 0.5438705682754517,
      "id": "59e5b2097321a02650a39715"
    },
    {
      "type": "character",
      "loopid": "59a0c7eb6c4805500909b22c",
      "source": "illustration2vec",
      "value": "kousaka kirino",
      "confidence": 0.9582517147064209,
      "id": "59e5b20b7321a02650a39750"
    },
    {
      "type": "character",
      "loopid": "59a0c7eb6c4805500909b22c",
      "source": "illustration2vec",
      "value": "kagamine rin",
      "confidence": 0.7113267183303833,
      "id": "59e5b20b7321a02650a39751"
    },
    {
      "type": "character",
      "loopid": "59b559b69be5ab05f52610f4",
      "source": "illustration2vec",
      "value": "hirasawa ui",
      "confidence": 0.54304039478302,
      "id": "59e5b2127321a02650a397c3"
    },
    {
      "type": "character",
      "loopid": "593b535e6e324b07195029fa",
      "source": "illustration2vec",
      "value": "ushiromiya battler",
      "confidence": 0.5971958637237549,
      "id": "59e5b2147321a02650a397ee"
    },
    {
      "type": "character",
      "loopid": "594cf05197d7cf18a418eb6c",
      "source": "illustration2vec",
      "value": "link",
      "confidence": 0.7175923585891724,
      "id": "59e5b2157321a02650a39808"
    },
    {
      "type": "character",
      "loopid": "599dcd1e988ffc732715522b",
      "source": "illustration2vec",
      "value": "tainaka ritsu",
      "confidence": 0.9126274585723877,
      "id": "59e5b2177321a02650a39826"
    },
    {
      "type": "character",
      "loopid": "59c2a97d7b994e05711a2cda",
      "source": "illustration2vec",
      "value": "kisaragi chihaya",
      "confidence": 0.5863552689552307,
      "id": "59e5b2367321a0267cfcd3ff"
    },
    {
      "type": "character",
      "loopid": "59b67b5a9be5ab05f5261a2f",
      "source": "illustration2vec",
      "value": "inaba tewi",
      "confidence": 0.7499340772628784,
      "id": "59e5b2547321a0267cfcd481"
    },
    {
      "type": "character",
      "loopid": "599dddab988ffc7327155334",
      "source": "illustration2vec",
      "value": "hirasawa yui",
      "confidence": 0.9034106135368347,
      "id": "59e5b25a7321a0267cfcd4e9"
    },
    {
      "type": "character",
      "loopid": "599dddab988ffc7327155334",
      "source": "illustration2vec",
      "value": "tainaka ritsu",
      "confidence": 0.6707159280776978,
      "id": "59e5b25a7321a0267cfcd4ea"
    },
    {
      "type": "character",
      "loopid": "5992641fbca076360b842e3b",
      "source": "illustration2vec",
      "value": "suzumiya haruhi",
      "confidence": 0.6030216813087463,
      "id": "59e5b25e7321a0267cfcd53f"
    },
    {
      "type": "character",
      "loopid": "59a9a4e9f0e315606a89ec3a",
      "source": "illustration2vec",
      "value": "nagato yuki",
      "confidence": 0.8905677795410156,
      "id": "59e5b2677321a0267cfcd5f5"
    },
    {
      "type": "character",
      "loopid": "599dd077988ffc732715523a",
      "source": "illustration2vec",
      "value": "hirasawa yui",
      "confidence": 0.9992274641990662,
      "id": "59e5b2697321a0267cfcd61a"
    },
    {
      "type": "character",
      "loopid": "599dd077988ffc732715523a",
      "source": "illustration2vec",
      "value": "tainaka ritsu",
      "confidence": 0.5392101407051086,
      "id": "59e5b2697321a0267cfcd61b"
    },
    {
      "type": "character",
      "loopid": "598c3af57de83a46a6dfb664",
      "source": "illustration2vec",
      "value": "hiiragi tsukasa",
      "confidence": 0.711155116558075,
      "id": "59e5b26e7321a0267cfcd681"
    },
    {
      "type": "character",
      "loopid": "59c2a97d7b994e05711a2cda",
      "source": "illustration2vec",
      "value": "akizuki ritsuko",
      "confidence": 0.768807053565979,
      "id": "59e5b2897321a026b1898c6a"
    },
    {
      "type": "character",
      "loopid": "599d8d7e988ffc7327154e3f",
      "source": "illustration2vec",
      "value": "tainaka ritsu",
      "confidence": 0.5375962853431702,
      "id": "59e5b2907321a026b1898c83"
    },
    {
      "type": "character",
      "loopid": "598506e521817348ba8a7f71",
      "source": "illustration2vec",
      "value": "emiya shirou",
      "confidence": 0.8103868961334229,
      "id": "59e5b3307321a02785eb5e20"
    }
  ]
}
```

