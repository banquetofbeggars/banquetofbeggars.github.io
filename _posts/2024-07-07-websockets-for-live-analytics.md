### Websockets for Live Analytics

Websockets are a superior option versus polling HTTP requests for applications running real-time live analytics.
These may be unfamiliar to developers however are the only performant choice for ultra-frequent data updates.
Examples of these could be financial ticker data, profit/loss measures, or other real-time telemetry data.

Websockets are an ideal choice as messages may be initiated by the server, instead of the server waiting for a periodic request for data and responding at the time of receipt.

A naive attempt at real-time analytics may be as follows:
- A server that receives updates in an ad-hoc manner (that is, not with a predictable frequency).
- A front end that polls on a timer, we will use 1s for this example.

In the worst case, the update may not be received for the entire length of the polling cycle (1s) plus the send/response time:

A request for an update may be processed by the server just prior to an update being made. The (now out of date) response is sent back, and the front-end now waits another period of one second before sending an update request.
At this point, the front end will also be delayed by the entire request round trip before receiving the update.

### A websocket solution

A connection is opened between the front-end and server.
As and when the server receives an update on the relevant data, it is sent directly to the subscribed front end.
In this case the delay is only the time taken to transfer the data between server and front end one-way.


### An example using kdb

kdb+ tickerplants can execute callback functions either on a timer, or on every update they receive.
Passing this data downstream to consumers can be done via a websocket connection.
As mentioned, the websocket is far superior from a performance standpoint to periodic polling via HTTP requests from a client.
The server notifies the front-end consumer immediately upon the meeting of update criteria.
In this scenario, the main performance concern is the need to not overwhelm the client with updates - tickerplants can process updates with incredible speed.
Examples are shown below:

```q
.z.ts:{1 .z.t;}
```