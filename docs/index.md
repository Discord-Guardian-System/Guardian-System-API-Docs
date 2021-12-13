# Guardian System API Introduction

Welcome, we are glad you have finally made it over to our repo, and are interested in possibly working with us. The Discord Guardian System in short is a way for moderation bots to all share data that then can be used to better protect end users on Discord.

## Introduction

The Discord Guardian System is a REST API created with the intention of providing further security and risk management for servers on the Discord platform. The API can be accessed by making requests to set endpoints, either via requests or aiohttp for JavaScript and Python or via the use of our in house packages; PyGuard (Python) & GuardianJS (JavaScript). If you are a developer using another language, you will be forced to create and send your own requests until either a package becomes available. Creating your own package is encouraged, and would earn special roles in our community [Discord Server](https://dsc.gg/dgsofficial) if you are the first to create a package for your preferred language. 

## Endpoints

Below are a list of all endpoints for `v1` of the API, their supported methods and path make-up. All requests should be made to the official API url: `https://api.guardiansystem.xyz/v1`.
    
| Endpoint | Methods | Path | Description |
| --- | --- | --- | --- |
| offenders | GET | `/offenders/{offender-id}` | Retrieves an offender, if present from API |
| servers | GET | `/servers/{server-id}` | Retrieves a Discord Server, if present from API |
| links | GET | `/links/{url-encoded-link}` | Retrieves a potential Scam Link from API if present | 
| Requests | GET, POST | GET: `/requests/{request-id}` POST: `/requests` | Retrieves or Creates a request| 
| Reports | GET, POST | GET: `/reports/{report-id}` POST: `/reports` | Retrieves or creates a report, submits addition to API. |

    1. `/offenders` - Retrieve information from the API about a member. Will return offense information or NONE FOUND response if user is not blacklisted. 
        - Methods: GET
        - Path: `/offenders/{offender-id}`
    
    2. `/servers` - Retrieve information from the API regarding a Discord Server. Will return server information or NONE FOUND response if server is not blacklisted.
        - Methods: GET
        - Path: `/servers/{server-id}`
    
    3. `/links` - Retrieve information about a potential scam link. Will return link information or NONE FOUND response if not in system.
        - Methods: GET
        - Path: `/links/{url-encoded-link}`
    
    4. `/requests` - Request or retreive a data requests status from the API. Guardian System allows its offenders or offending server owners/admins to request their stored data as an attempt to remain as transparent as possible. Only the server owner or user who owns the information can request access to it. 
        - Methods: POST, GET
        - Paths:
            - POST: `/requests` - include request creation data as JSON object in request payload
            - GET: `/requests/{request-id}` - gets a requests status via the provided ID.
    
    5. `/reports` - create or retrieve a report from the API. Reports are used to adding data to the API. Whether reporting a user, server, or simply a potential scam link. These reports are posted in an official channel in our discord server where auditors will investigate and ultimately decide upon its addition to the API or abandonment.
        - Methods: POST, GET
        - Paths:
            - POST: `/reports` - include report creation data as JSON object in request payload.
            - GET: `/reports/{report-id}` - Retrieves a report by ID and returns its current status. (Accepted, Abandoned, Pending) 


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
