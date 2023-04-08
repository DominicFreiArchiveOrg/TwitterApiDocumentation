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

Example Response:

```
{
  "conversationId": 1644397705605656576,
  "date": "2023-04-07 17:52:19",
  "id": 1644397705605656576,
  "inReplyToTweetId": null,
  "inReplyToUser": null,
  "likeCount": 11,
  "quoteCount": 0,
  "rawContent": "As a human, what is your favorite breakfast?",
  "renderedContent": "As a human, what is your favorite breakfast?",
  "replyCount": 12,
  "retweetCount": 1,
  "user": {
    "created": "2011-04-16 11:16:10",
    "displayName": "Dominic Frei \ud83d\ude80 www.grittr.app",
    "followerCount": 834,
    "followingCount": 158,
    "id": 283004207,
    "profileBannerUrl": "https://pbs.twimg.com/profile_banners/283004207/1679880618",
    "profileImageUrl": "https://pbs.twimg.com/profile_images/1321489002759946240/J2aAULS-_normal.jpg",
    "rawDescription": "!!! https://t.co/sgY6fVDKq6 !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
    "renderedDescription": "!!! GrittR.app !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
    "tweetCount": 10528,
    "username": "dominicfrei"
  },
  "viewCount": 565
}
```

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

Example Response:

```
{
  "conversationId": 1644397705605656576,
  "date": "2023-04-07 17:52:19",
  "id": 1644397705605656576,
  "inReplyToTweetId": null,
  "inReplyToUser": null,
  "likeCount": 11,
  "quoteCount": 0,
  "rawContent": "As a human, what is your favorite breakfast?",
  "renderedContent": "As a human, what is your favorite breakfast?",
  "replyCount": 12,
  "retweetCount": 1,
  "user": {
    "created": "2011-04-16 11:16:10",
    "displayName": "Dominic Frei \ud83d\ude80 www.grittr.app",
    "followerCount": 834,
    "followingCount": 158,
    "id": 283004207,
    "profileBannerUrl": "https://pbs.twimg.com/profile_banners/283004207/1679880618",
    "profileImageUrl": "https://pbs.twimg.com/profile_images/1321489002759946240/J2aAULS-_normal.jpg",
    "rawDescription": "!!! https://t.co/sgY6fVDKq6 !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
    "renderedDescription": "!!! GrittR.app !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
    "tweetCount": 10528,
    "username": "dominicfrei"
  },
  "viewCount": 565
}
```

### Users

Method: ```GET```

Path: ```/users/:username```

Path Parameters:

- username:
  - The Twitter handle of the user you want to query, e.g. @dominicfrei

Query Parameters:

- None

Data / Body:

- None

Example:

```http://twitterapi-env.eba-tmjmxmmh.ap-northeast-1.elasticbeanstalk.com/users/dominicfrei```

Example Response:

```
{
  "created": "2011-04-16 11:16:10",
  "displayName": "Dominic Frei \ud83d\ude80 www.grittr.app",
  "followerCount": 834,
  "followingCount": 158,
  "id": 283004207,
  "profileBannerUrl": "https://pbs.twimg.com/profile_banners/283004207/1679880618",
  "profileImageUrl": "https://pbs.twimg.com/profile_images/1321489002759946240/J2aAULS-_normal.jpg",
  "rawDescription": "!!! https://t.co/sgY6fVDKq6 !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
  "renderedDescription": "!!! GrittR.app !!! 20+ years Software Engineer & Developer Advocate @MongoDB Ask me about coding, programming, AI, Twitter, entrepreneurship.",
  "tweetCount": 10529,
  "username": "dominicfrei"
}
```
