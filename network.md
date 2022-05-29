# network

## How are TCP, DNS and IP address related?

- Transmission Control Protocol (TCP)

  - connection-oriented protocol between client and server, used to send data

- Domain Name System (DNS)
  - essentially the 'phonebook' of the internet
  - translates the domain names to IP Address (from human readable URL to machine alphanumeric address)
  - converts the hostname to a computer-friendly IP Address

## Difference between http & https

HyperText Transfer Protocol (Secure)

- https is an extension of http
  - transmits encrypted data using TLS (Transport Layer Security)

1. Client (browser) and server establish a TCP connection
2. Client says 'hello' to server. Message also contains cryptography and latest TLS version it can support
3. Server says 'hello' to client. Responds by saying whether it can support the algorithm and TLS version
4. Server sends the SSL certificate (contains public key, host name, expiry)
5. Client validates SSL cert
6. Client then generates a session key and encrypts it using public key
7. Server receives encrypted session key and decrypts it with private key
8. Client and Server now hold same session key --> secure connection established --> data can now pass bilaterally

## What is CORS?

- Cross-Origin Resource Sharing
- Allows us to relax SOP

- Browsers have a security policy known as Same-Origin Policy (SOP)

  - essentially a way for browsers to prevent any requests or perform operations outside its origin
  - origin is the source of the request (who is making the request?)
  - origin is a combination of the:
    - http/https
    - domain
    - port
  - if any of the above are diff, we are not on the same origin

- one way to relax CORS is for our BE APIs to allow external entities diff from its origin to make requests
- this is achieved through http headers in the response
  - **Access-Control-Allow-Origin** header
  - configured to specify which origins are allowed to talk to your api
  - Can use \* asterisk to allow anyone to talk to your api

## What is Cross-Site Request Forgery (CSRF / XSRF)?

- Method by which malicious scripts try to impersonate a user by exploiting a browser's trusted connection with a site

## Describe the process from the time you type in a website's URL to it finishing loading on your screen.

1. your browser performs IP Address lookup - tries to find site in sequence below

- Browser cache
- Operating system
- DNS lookup request to ISP

2. depends if http or https

- if https, then client/server need to establish a secure connection first using SSL certificate

3. Resource is requested from the domain's server

- depends if SSR or CSR
- site is loaded

## What are the differences between Polling, WebSockets and Server-Sent Events?

Various ways to enable real-time web application. Two general approaches: client pull or server push

![Polling, WebSockets & SSE](./assets/client-pull-server-push.png?raw=true)

<ins>Polling (client pull)</ins>

1. Short polling

- asks server at regular intervals using an AJAX-based timer
- - does not block server side resources, as a response is sent back immediately
- - downside is that it creates a lot of traffic/requests

```
00:00:00 C-> Is the cake ready?
 00:00:01 S-> No, wait.
 00:00:01 C-> Is the cake ready?
 00:00:02 S-> No, wait.
 00:00:02 C-> Is the cake ready?
 00:00:03 S-> Yes. Have some lad.
 00:00:03 C-> Is the other cake ready?
```

2. Long polling

- client will be notified by server when the resource is ready
- - less traffic
- - server resource is blocked until response is sent back
- however, with Node, you can save a lot more resources as it will not spawn an instance for each request

```
00:00:00 C-> Is the cake ready?
00:00:03 S-> Yes.Have some lad.
00:00:03 C-> Is the cake ready?
```

Pros of Polling: 
- implemented using XMLHttpRequest which is widely supported

Cons of Polling: 
- more server intensive
- possible for multiple HTTP requests from the same client to be in flight simultaneously (two browser tabs open); creates problem of duplicate data

<ins>WebSockets (server push)</ins>
Websockets are best for instantaneous data without the browser refresh
- does your app involve multiple users communicating with each other?
- does your server-side data constantly change?
If yes to either question, websockets would be an ideal choice.

- persistent connection between client & server, 2-way communication channel, using a single TCP connection
- send messages to server and receive event-driven responses without having to poll

Use cases:
- social feeds
- multiplayer games
- collaborative editing
- financial tickers (websockets can stream the latest prices)

Pros of WebSockets: 
- WebSockets keeps a unique connection open
- do not use XMLHttpRequest, as such, headers are not sent each time we need info from server. This reduces expensive data loads being sent to the server

Cons of WebSockets: 
- WebSockets don’t automatically recover when connections are terminated. Need to implement yourself. There are many client-side libraries in existence to solve this.
- Browsers older than 2011 aren’t able to support WebSocket connections

<ins>Server-Sent Events (server push)</ins>

- unlike WebSockets (bilateral), Server-Sent Events are unilateral
- client receives data from server
- uses one long-lived HTTP connection
 
 Pros of SSE: 
- SSEs come with automatic reconnection
- simpler and faster solution than WebSockets

Cons of SSE: 
- More browsers support WebSockets as opposed to SSE
- Suffer from a limitation to the maximum number of open connections, which can be especially painful when opening various tabs, as the limit is per browser is six.

Use cases:
- apps that do not require data being sent from client
- push notifications
- newsletters & feeds
## What is AJAX?

Asynchronous Javascript And XML

- uses browser built-in XMLHttpRequest: used to request data from server
- Javascript and HTML DOM: to display or use the data

- allows web pages to be updated asynchronously by exchanging data with a server behind the scenes
  - means we are able to update parts of the page without reloading the whole page

![AJAX](./assets/AJAX.png?raw=true)

## Traditionally, why has it been better to serve site assets from multiple domains?

Because browsers usually have limits on the number of concurrent downloads from a domain at a moment. So, serving assets from multiple domains can increase the concurrent level.

## What are HTTP methods? List all HTTP methods that you know, and explain them.

GET

- read / retrieve resource

POST

- add / create

PUT

- updates the entire resource
- can create a new resource if it does not exist
- need to send all the resource attributes
- e.g. if updating an object, need to send all properties

PATCH

- only partial update
- only required to send the data you want to update
- e.g. if updating an object, only send the property you want to update

DELETE

## What is RESTful api?

Representational State Transfer

- A set of architectural constraints when building APIs

STATELESS

- a client request should contain all the information necessary to respond to the request
- no client information is stored between requests
- each request is separate and unconnected
- i.e. should be possible to make 2 or more http requests in any order and same response should be received

LAYERED

- the client does not need to know whether its communicating with the server, proxy or intermediary

HTTP

- requests managed through HTTP

CACHE

- data should be cache-able to streamline client/server interaction

## What is domain pre-fetching and how does it help with performance?

DNS Prefetch is a resource hint to make a DNS lookup for a domain the browser has not yet determined needs to be made. This can improve performance because when the browser does need to make a request for a resource, the DNS lookup for that domain has already occurred.

We can optimize this by adding a DNS prefetch resource hint in the <head> of the HTML file, as shown below:

`<link rel="dns-prefetch" href="https://stats.example.com/">`

## What is a CDN and what is the benefit of using one?

Content Delivery Network (CDN)

- a group of servers spread out over a region that work together to speed up content delivery
- CDN temporarily stores or cache content like HTML, images, JS and video
  - these are then ready to be sent to end users / client
    Benefits of CDN

1. Better Performance

- client requests data from CDN --> uses the closest server to speed up delivery

2. Increased Reliability

- uninterrupted service; even if one server goes down there are alternatives
- load balancing in case one server is overwhelmed with requests; can spread out workload

3. Cost Savings

- less bandwidth cost because of the temporary storage/cache

4. Better Security

- defend against DoS or DDoS
- attackers cannot send high volume of junk requests to overwhelm a single server
- since there are many servers, CDNs are better adapted to handle such events/traffic


## What are PWA (Progessive Web Apps)?

- PWAs are web apps that use service workers along with progressive enhancement to give users an experience on par with native apps

Advantages:
- network independent
  - can work offline
- progressively enhanced
  - still usable on older browsers, but enhanced with more features on modern browsers
- installable
  - available on the device's home screen or app launcher
- decreased loading times
  - uses caching with service workers to save time and bandwidth on 2nd+ visit