# Data

### Training data
General info:

You are provided with:
* A training set of ~500 annotated articles, each annotated article includes:
  - **`original_doc`**: The content the article in which body and the headline are provided. However, titles of articles ARE NOT PROVIDED.
  - **`html_annotation`**: The annotation important events in the match.
  - **`match_summary`**: The expected output.
* Teams can use `html_annotation` and `match_summary` for training the systems, however, but these annotations DO NOT AVAILABLE IN THE TEST SET.

Detail training data format:
- **`original_doc`**: represents the content of original article which `description` and `body` are provided.
Properties such as `published_date`, `url` are for references purposes, they may not appear in the test.
- **`html_annotation`**: contains annotation of events in the match.  

All paragraphs in the body are annotated, each event found in the paragraph is marked by `tag` in the span. There are several main event types:
- `goal_info`: describes a goal
- `match_info`: describes two participating teams of the match
- `match_result`: describes the result of the match
- `card_info`: describes a foul card situation 
- `substitution`: describes a substitution

You can get list of events by follow the instruction.

```
python
    from bs4 import BeautifulSoup
    for html in doc["html_annotation"]:
        soup = BeautifulSoup(html)
        events = soup.find_all("span", {"class": "tag"})
        for e in events:
            print("event_type:" e["data"])
            print("event_id:", e["event_id"])
            print("text:", e.text)
```

- **`match_summary`**: is the match summary which contains:
    - `players`: two teams of the match
    - `score_board`: the score of each team, they should follow the order of player
    - `score_list`: list of goals of the matches that found in the article
    - `card_list`: list of foul situations
    - Notes: The values of `ref_event_ids` in the match summary refers to events in the event list.
- `html_annotation` and `match_summary` do not available in the test set.

### Training data file
Train documents are organized in a \*.jsonl format.

### Test data
Each test case is a json document contains only `original_doc`.
Participants should find the `match_summary` of each test_case if possible.

Test cases are organized in a \*.jsonl format.

### Sample submission

The submission follow the `*.jsonl` format in which each line of the file is a json string object. 

Below is the sample submission file:

```
{"test_id": "test1001", "match_summary": { .... }},
{"test_id": "test1002", "match_summary": { .... }},
...
...
...
```

Each line is the result of each test case which contains test_id and match_summary found:

```json
{
 "test_id":"test1001",
 "match_summary": {
  "players": { "team1":"Man United", "team2":"Middlesbrough" },
  "score_board": { "score1":"2", "score2":"1" },
  "score_list": [
   { "player_name":"Anthony Martia", "time":"85", "team":"M.U" },
   { "player_name":"Pogba", "time":"1 phút sau", "team":"M.U" }
  ],
  "card_list": [],
  "substitution_list": []
 }
}
```

### Additional Notes

`*.jsonl` format is the file in which each line is a json document.

---

### Traing data
* [ZaloAI Public Data](https://dl.challenge.zalo.ai/news-summarization/data/train.zip)
* [Backup Data](./data/train.zip)

### Publish test
* [ZaloAI Public Data](https://dl.challenge.zalo.ai/news-summarization/data/public_test.zip )
* [Backup Data](./data/private_test.zip)

### Sample submission (public test)
* [ZaloAI Public Data](https://dl.challenge.zalo.ai/news-summarization/data/public_test_sample_submit.zip)
* [Backup Data](./data/public_test_sample_submit.zip)

### Private test
* [ZaloAI Public Data](https://dl.challenge.zalo.ai/news-summarization/data/private_test.zip)
* [Backup Data](./data/private_test.zip)

### Sample submission (private test)
* [ZaloAI Public Data](https://dl.challenge.zalo.ai/news-summarization/data/private_test_sample_submit.zip)
* [Backup Data](./data/private_test_sample_submit.zip)
