* Create and manage APIs
* Endpoint/entry-point for applications
* Sits between applications & integrations (services)
* Highly available, scalable, handles authorization, throttling, caching, CORS, transformation, OpenAPI spec, direct integration and much more.
* Can connect to services/endpoints in AWS or on-premises
* HTTP APIs, REST APIs, and WebSocket APIs

Request phase

* Authorizes
* Transforms
* Validates

Response phase

* Transforms
* Prepares
* Returns

CloudWatch Logs can store and manage full stage request and response logs. CloudWatch can store metrics for client and integration sides.

Provides an API cache that can be used to reduce the number of calls made to backend integrations and improve client performance.

Authentication

* Client passes a token with request (what kind of token?)
* API gateway passes token to Cognito to verify token validity and authenticates with Cognito.

If there is a custom authentication (i.e. bearer token), API gateway will call a lambda function as the authorizer which will handle the authentication and return back an IAM policy and principal identifier.

Endpoint Types

* Edge Optimized
* Routed to nearest CloudFront POP
* Regional - Clients in the same region
* Private - Endpoint only accessible within a VPC via interface endpoint

Stages

* API Gateway deploys APIs to stages and each stage has one deployment that has its own unique URL and settings.
* Stages can be enabled for canary deployments. If done, deployments are made to the canary and not the stage.
* Stages enabled for canary deployments can be configured so a certain percentage of traffic is sent to the canary. This can be adjusted over time or the canary can be promoted to make it the new base 'stage'.

Errors (remember these!)

* 4XX - Client Error - Invalid request on the client side
* 5XX - Server Error - Valid request, backend issue
* 400 - Bad Request - Generic
* 403 - Access Denied - Authorizer denies.. WAF Filtered
* 429 - API Gateway can throttle - this means you've exceeded that amount.
* 502 - Bad Gateway Exception - bad output returns by lambda
* 503 - Service Unavailable - Backing endpoint offline? Major service issues
* 504 - Integration Failure/Timeout - 29s limit for any request to API gateway

Caching

* Configured per stage
* Without a cache, the backend services are called with every request.
* Cache TTL default is 300 seconds. Configurable min 0 and max 3600s. Can be encrypted. Cache size is 500 MB to 237 GB.
* Calls are only made to backend integrations if request is a cache miss.
