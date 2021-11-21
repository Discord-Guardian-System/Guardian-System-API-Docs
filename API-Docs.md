# Guardian System API Introduction

Welcome, we are glad you have finally made it over to our repo, and are interested in possibly working with us. The Discord Guardian System in short is a way for moderation bots to all share data that then can be used to better protect end users on Discord.

## How It Works

The Guardian System is a REST API structure. Any data can be requested through the API's endpoints (You can find these in the `endpoints.json` file in the `server > config` folder of this repo).

 Bot programs will be able to request information through GET requests and can submit information using POST requests. There may be different API packages to download in the future making interaction with the API easier. 
 
 All requests are cached on our server in a `cache > call > return` system. What this means is that every request that comes in, the server will check the cache for the requested data before requesting it from the database. The goal here is to make the response as fast as possible for you and your applications, removing any need for response time handling on your end. 
 
 ## Getting Started
 
 To gain access to the server and obtain the ability to even have your requests acknowledged you will need an `API token`. Tokens are generated and given out on request/submission basis, to gain a token you will need to pass a verification. The verification process involves your application/bot being in at least 75 servers. You will need to submit a way to show your application/bots growth since initial release. Your application/bot must already be a verified Discord Bot. This may be limiting but for production and initial release we are limiting the amount of applications accepted for use.

## Submiting a Verification Request

Submitting a request for an `API Token` is fairly straight forward you can join [The Guardian System](https://discord.gg/eVUgfYEUaw), once there you can use our bot to submit a request for verification. A Developer or Support Team member will reach out to you with questions regarding your bot, a link to the bot's listing page on Bot Lists, and other identifying information including a link to your bots support server to verify your identity as the lead developer. Once everything is received it may take up to 7-10 days for approval and a token to be sent to you. 

## Making Requests to The API

Making requests to the API are very straight forward. We use the standard request format and will return requested content to you in `JSON` format. Request URLS are structured as such: 

`
https://guardiansystem.dev/api/v1/resources/resource-id?cached=Boolean
`

Looking at the URL above we can speak about a couple different identifiers that are important for making requests:

1. `base-URL` - The base-URL for all requests is `https://guardiansystem.dev/api/v1/`

2. `resources` - The resources endpoint portion of the above URL is pointing towards the information you are accessing. Accepted resource endpoints are: `[offenders, links, reports]`

3. `resource-id` - The resource-id portion of the above endpoint is referring to the unique identifier of a specific set of data in the previously defined resource. Identifiers can be a Discord User's ID Snowflake for `offenders` or `reports`. Likewise a link itself would be the unique identifier for the link data your are requesting. 

4. `?cached=Boolean` - The cached portion of the above endpoint is referring to whether you would like this specific request's return to be cached on the server. Although the server caches responses to requests by default they are removed after 5 minutes of inactivity. By requesting `?cached=true` the response data will be cached for 30-minutes to 1-hour depending on current traffic and amount of requests at the time of your request. 