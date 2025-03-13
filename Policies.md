1. Basic Authentication:
	we will generate username and password. The same user name and password will be distributed to all the consumers of that particular api. Then as part of the requests
	they will send the username and password and once we receive the request API will validate the username and password with the help of API Manager.
	If everything is fine the request will be processed and Response will be sent back.

2. Client Id Enforcement:
	We will generate different client ID and secret for each and every consumer of that particular API. They will send the reuquest with their client id and secret and 
	once we receive the request API will validate the client ID and secret. If everything is correct then then the request will be processed and response will be sent back.

3. Rate Limiting:
	The Rate Limiting policy enables you to control the incoming traffic to an API by limiting the number of requests that the API can receive within a given period of time. 
	After the limit is reached, the policy rejects all requests, thereby avoiding any additional load on the backend API.

4. Rate Limiting SLA:
	The Rate-Limiting Service Level Agreement (SLA) policy enables you to control incoming traffic to an API by limiting the number of requests that the API can receive within a given timespan. 
	When the limit is reached before the time expires, the policy rejects all requests, thereby avoiding any additional load on the backend API.

	To apply the Rate-Limiting SLA policy to an API, you must first create a contract between the API and a registered client application. 
	The number of requests that an API can receive within a given time is defined in the contracts section in API Manager.
	
5. Spike Control(Throttiling):
	The Spike Control policy regulates your API request traffic by limiting the number of messages processed by an API. 
	The policy ensures that the number of messages processed within a specified time does not exceed the limit that you configure. 
	If the number is exceeded, the request is queued for retry based on you have configured the policy.

RateLimiting Vs SpikeControl:
	Rate- Limiting will reject the request if it exceeds the number of requests specified in that time window.
	eg: If we configured 1000 requests per an hour then we received 1001 request then it will the reject that request.
	
	Spike COntrol policy will keep extra requests in a queue then it will process the request in queue in next window.
	eg: If we configured 1000 requests per an hour and 50 requests in queue then we received 1051 request it will the reject that request.
	It gives 429 Too many Requests
