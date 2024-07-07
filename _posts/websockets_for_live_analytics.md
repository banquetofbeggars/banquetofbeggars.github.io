kdb+ tickerplants can execute callback functions either on a timer, or on every update they receive.
Passing this data downstream to consumers can be done via a websocket connection.
This is far superior from a performance standpoint to periodic polling via http requests from a frontend.
The server notifies the front-end consumer code immediately upon the criteria.
This can significantly reduce the latency of real-time analytics.
The main performance concern in this situation is the need to not overwhelm an updating front-end with information as a tickerplant can process updates with incredible speed.
Examples are shown below:

```q
.z.ts:{1 .z.t;}
```