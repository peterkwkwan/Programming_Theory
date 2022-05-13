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

## Traditionally, why has it been better to serve site assets from multiple domains?

## Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.

## What are the differences between Long-Polling, Websockets and Server-Sent Events?

## What are HTTP methods? List all HTTP methods that you know, and explain them.

## What is domain pre-fetching and how does it help with performance?

## What is a CDN and what is the benefit of using one?
