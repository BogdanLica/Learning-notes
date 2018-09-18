## Web Sockets

#### IP Suite
  * Application layer(how the packages received should be processed)
    * HTTP
    * WebSockets
    * SSL
    * POP
  * Internet layer(where the data is sent to)
    
    * IPV4
    * IPV6
  * Transport layer(dictates how the packages are sent across)
    * TCP
    * UDP


#### HTTP
    * based on request/response
    * stateless
    * data is sent with headers
    * clients have to specify actions(GET/POST/PUT/DELETE)


#### Ajax Requests
    * same on request/response, but asnynchronously send data to server without refreshing

#### Web Sockets
    * upgrade from HTTP
    * only sends headers once
    * full duplex bi-directional communication
    * i.e: the server and the client can talk in real time without continuously making requests
    * downsides:
        * cannot communicate with REST
        * cannot be used with OAuth
        * does not provide automatic caching like HTTP
        * needs special configuration for load balancing

#### Alternatives to Web Sockets
* Polling
    * send AJAX requests every X amount of seconds for new data
* Long Polling
    * send request to server and keep connection open until new data
* Server Sent Events
    * uses EventSource API to send messages from server
    * not truly bi-directional

