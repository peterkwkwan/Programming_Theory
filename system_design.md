# system design

## Basic server-client flow

1. Users access websites through domain names, such as www.example.com. Usually, the Domain Name System (DNS) is a paid service provided by 3rd parties and not hosted by our servers.
2. Internet Protocol (IP) address is returned to the browser or mobile app. In the example, IP address 15.125.23.214 is returned.
3. Once the IP address is obtained, Hypertext Transfer Protocol (HTTP) requests are sent directly to your web server.
4. The web server returns HTML pages or JSON response for rendering.

## Scaling with multiple servers and database

With the growth of the user base, one server is not enough, and we need multiple servers: one for web/mobile traffic, the other for the database. Separating web/mobile traffic (web tier) and database (data tier) servers allows them to be scaled independently.

## Which database to use? NoSQL vs SQL?
