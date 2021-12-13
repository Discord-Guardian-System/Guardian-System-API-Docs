## Introduction

The Discord Guardian System is a REST API created with the intention of providing further security and risk management for servers on the Discord platform. The API can be accessed by making requests to set endpoints, either via requests or aiohttp for JavaScript and Python or via the use of our in house packages; PyGuard (Python) & GuardianJS (JavaScript). If you are a developer using another language, you will be forced to create and send your own requests until either a package becomes available. Creating your own package is encouraged, and would earn special roles in our community [Discord Server](https://dsc.gg/dgsofficial) if you are the first to create a package for your preferred language. 

## Endpoints

Below are a list of all endpoints for `v1` of the API, their supported methods and path make-up. All requests should be made to the official API url: `https://api.guardiansystem.xyz/v1`.
    
| Endpoint | Methods | Paths | Description |
| --- | --- | --- | --- |
| Offenders | GET | `/offenders/{offender-id}` | Retrieves a user's offense, if present from API |
| Servers | GET | `/servers/{server-id}` | Retrieves a Discord Server, if present from API |
| Links | GET | `/links/{url-encoded-link}` | Retrieves a potential Scam Link from API if present | 
| Requests | GET, POST | GET: `/requests/{request-id}` POST: `/requests` | Retrieves or Creates a request| 
| Reports | GET, POST | GET: `/reports/{report-id}` POST: `/reports` | Retrieves or creates a report, submits addition to API. |

## Getting Started
 
 Getting started with the API. All applications that are accessing the API are required to have an `API_TOKEN`. Applications without tokens will not have their requests aknowledged by the web server. To apply for an API_TOKEN you will need to fill out a form on our website. Criteria for applications vary so make sure to pay attention to the criteria and whether or not your application meets it. 

## Submiting a Verification Request

Submitting a request for an `API Token` is fairly straight forward you can join [The Guardian System](https://discord.gg/eVUgfYEUaw), once there you can use our bot or login to our website to submit a request for verification. A Developer or Support Team member will reach out to you with questions regarding your bot, a link to the bot's listing page on Bot Lists, and other identifying information including a link to your bots support server to verify your identity as the lead developer. Once everything is received it may take up to 7-10 days for approval and a token to be sent to you. 

## Making Requests to The API

Making requests to the API are fairly simple. Depending on the request method how your request is formatted will change. POST requests are made straight to the endpoint, while GET requests require the use of request parameters either in the path or via the parameters field of the request header.


### Authorization 

Requests use basic authorization. Authorization tokens must be utf-8 and base64 encoded, then decoded utf-8. 

Python Example:
```py
clientId =  126483968473727964 # You Discord Application Id
api_token = brgnadhshdhsdghrhh.fdntndtsfsrbesvebrbsr 
authStr = str(clientId) + ":" + api_token
strencode = encode(bytes(authStr, "utf-8"), "base64")
auth = decode(strencode, "utf-8")

# Authorization Header
authorization = "Basic " + auth 
```

## Endpoint Make Up
View the supported fields and expected content for requests based on each endpoint.

### Offender Endpoint

| Field | Accepted Content | Example |
|  ---  |        ---       |   ---   |
| Method | GET | `method: GET` |
| Protocol | https/1.1 | `protocol: https/1.1` |
| Path | Route path / Endpoint | `path: /offenders` |
| Parameters | The ID of information requested | `parameters: "{id: offender-id}"` |
| Authorization | Basic Request Authorization | `authorization: Basic encoded-credentials`|
