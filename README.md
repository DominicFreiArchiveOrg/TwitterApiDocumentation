# Twitter API Documentation

## Base URL

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com```

## Endpoints

### Search

This returns the results for a search identical to ```https://twitter.com/search``` as a JSON.

Method: ```GET```

Path: ```/tweets/search/recent```

Path Parameters:

- None

Query Parameters:

- ```query```
  - The search query that is supposed to be sent. This is the same as you would use on ```https://twitter.com/search``` (parameter ```q```).
  - Mandatory
  - Type: string

- ```sorted_by```
    - The field to sort by. This can be any field that's part of the tweet, e.g. 'date', 'viewCount', etc.
    - Optional
    - Type: string
    - Default: 'date'

- ```max_results```
  - The maximum amount of results returned.
  - Optional
  - Type: int
  - Default: 10

Data / Body:

- None

Example:

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com/tweets/search/recent?query=%28from%3Adominicfrei%29%20-filter%3Areplies&sorted_by=viewCount&max_results=5```

This is the equivalent to searching ```(from:dominicfrei) -filter:replies``` on ```https://twitter.com/search```, specifically: ```https://twitter.com/search?q=(from%3Adominicfrei)%20-filter%3Areplies```

### Tweets

Method: ```GET```

Path: ```/users/:username/tweets```

Path Parameters:

- username:
  - The Twitter handle of the user you want to query, e.g. @dominicfrei

Query Parameters:

- ```sorted_by```
    - The field to sort by. This can be any field that's part of the tweet, e.g. 'date', 'viewCount', etc.
    - Optional
    - Type: string
    - Default: 'date'

- ```max_results```
    - The maximum amount of results returned.
    - Optional
    - Type: int
    - Default: 10

Data / Body:

- None

Example:

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com/users/dominicfrei/tweets?sorted_by=viewCount&max_results=3```

This returns the latest tweets for a specified user.

Note: This is basically just a shortcut to the ```GET /tweets/search/recent``` endpoint where the ```:username``` will be used to form a search query like this:
```(from:username) -filter:replies```.
