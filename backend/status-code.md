### HTTP status code summary

200 - OK	Everything worked as expected.

400 - Bad Request	The request was unacceptable, often due to missing a required parameter.

401 - Unauthorized	No valid API key provided.

402 - Request Failed	The parameters were valid but the request failed.

404 - Not Found	The requested resource doesn't exist.

429 - Too Many Requests	Too many requests hit the API too quickly. We recommend an exponential backoff of your requests.

500, 502, 503, 504 - Server Errors	Something went wrong on Server
