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

- ```max_results```
  - The maximum amount of results returned.
  - Optional
  - Type: int
  - Default: 10

Data / Body:

- None

Example:

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com/tweets/search/recent?query=%28from%3Adominicfrei%29%20-filter%3Areplies&max_results=5```

This is the equivalent to searching ```(from:dominicfrei) -filter:replies``` on ```https://twitter.com/search```, specifically: ```https://twitter.com/search?q=(from%3Adominicfrei)%20-filter%3Areplies```

### Tweets

Method: ```GET```

Path: ```/users/:username/tweets```

Path Parameters:

- None

Query Parameters:

- ```max_results```
    - The maximum amount of results returned.
    - Optional
    - Type: int
    - Default: 10

Data / Body:

- None

Example:

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com/users/dominicfrei/tweets?max_results=1```

This returns the latest tweets for a specified user.

Note: This is basically just a shortcut to the ```GET /tweets/search/recent``` endpoint where the ```:username``` will be used to form a search query like this:
```(from:username) -filter:replies```.