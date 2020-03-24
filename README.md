# node-botometer-rapid-api

`node-botometer` evaluates Twitter accounts using [Botometer](https://botometer.iuni.iu.edu/#!/), a project by the [Indiana University Network Science Institute](https://iuni.iu.edu/), that "checks the activity of a Twitter account and gives it a score based on how likely the account is to be a bot. Higher scores are more bot-like."

It uses [Twit](https://github.com/ttezel/twit) and Botometer's [mashape API](https://market.mashape.com/OSoMe/botometer). Twitter application and Botometer mashape API keys are required.

## Install

`npm install node-botometer-rapid-api`

## Use

### Setup
`consumer_key` (string): Twitter API Key

`consumer_secret` (string): Twitter Secret Key

`x_rapid_api_host` (string): X-RapidAPI-Host value, more info: https://rapidapi.com/OSoMe/api/botometer/endpoints

`x_rapid_api_key` (string): X-RapidAPI-Key value, more info: https://rapidapi.com/OSoMe/api/botometer/endpoints

`rate_limit` (integer): In milliseconds. Will apply to any calls to the Twitter or mashape APIs. Default: 0.

`log_progress` (boolean): Set to `true` to console log progress on score collection for each name. Default: true.

`include_user` (boolean): Include user data from Twitter in output object. Default: true.

`include_timeline` (boolean): Include the 200 most recent tweets from this user in output object. Default: false.

`include_mentions` (boolean): Include the 100 most recent mentions of this user in output object. Default: false.

```js
const botometer = require('node-botometer');

const B = new botometer({
  consumer_key: '',
  consumer_secret: '',
  x_rapid_api_host: '',
  x_rapid_api_key: '',
  app_only_auth: true,
  rate_limit: 0,
  log_progress: true,
  include_user: true,
  include_timeline: false,
  include_mentions: false
});
```

### Get Botometer scores

You can get scores for one account or for many. It takes about six seconds per account and I'm looking for ideas to make it faster!

```js
// array can be one screen name or many
const names = ["collinskeith","usinjuries","actual_ransom"];

B.getBatchBotScores(names,data => {
  console.log(data);
});
```
