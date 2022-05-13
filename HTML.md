# html

## What does a `doctype` do?

- All HTML documents must start with a `DOCTYPE` declaration
- It is NOT an HTML tag, but rather an indicator to the browser of what type of document to expect, along with the version of HTML
- Ensures the document is parsed consistently across different browsers
  **Note**: doctype is not case-sensitive

```
<!DOCTYPE html>
```

## Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

- Similarities:
  -- All store data on user's browser
  -- Meant for storing information specific to a user

- Differences:
  -- Cookies store only 4kb, vs 5mb (storage) & 10mb (local)
  -- Cookies & localStorage are available in all tabs
  -- SessionStorage is only available for that tab/session (lost upon closing tab)
  -- Cookies need to be set when they are to expire
  -- LocalStorage never expires

- Notes:
  -- Should always try to use local or sessionStorage as cookies are sent to the server along with ANY requests
  -- If too many cookies, this will slow down the requests and create overhead

![Cookies, LocalStorage & SessionStorage](./assets/storage.png?raw=true)

## Describe the difference between `<script>`, `<script async>` and `<script defer>`.

When a browser parses a script tag declaration, it will perform the following steps:

1. Pause the document parser
2. Download script
3. Execute script
4. Resume document parsing

This is bad for the user experience because the user cannot interact with the page during the script download.
HTML5 provides a solution to this problem with `async` and `defer`. These attributes inform the browser that the script can be downloaded _in parallel_ with the document parsing process.

- `Async`
  -- After `async` script is downloaded the browser will pause the document parsing, and execute the script, then resume parsing the document

- `Defer`
  -- `defer` script will only be executed when the parser has completed its job
  -- Ensures that entire document is parsed before executing --### useful for when scripts depend on each other

## Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions? Why `<script>` tag goes last?

When the browser encounters any JS, it will pause the document parsing and execute the JS first. Hence if `<script>` was added at the top, it would make the page render slow and provide a bad user experience. As well, because the DOM is not fully loaded, JS won't be able to manipulate the elements.

CSS are linked in the head because they get applied regardless of whether DOM is ready. Hence webpages looks good as soon as page loads, and is seen as it should be aesthetically.

## What is progressive rendering?

A technique used to render content for display as quickly as possible. Some techniques used:

- Lazy loading of images - will load an image when it comes into the viewport instead of loading all at once.
- Prioritizing visible content where you only include the minimum css/content/scripts necessary for the amount of pages that would be rendered in the users' browser. Use deferred JS to load in other resources and content.

_TLDR;_ Render the browser optimally by rendering the critical content first and non-critical parts later.

## Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.

It is a technique used to render the optimal image resolution based on the different viewport sizes of users.

```
<img src='image.jps'
srcset='image_small.jpg 360w, image_medium.jps 720w, image.jpg 1400w'/>
```

Each comma-seprated item has imageUrl along with the width of the image in pixels (or display density)

## What are HTML templating languages?

Solves some of the fundamental limitations of HTML as a markup language. Some limitations include:

- Difficult to add dynamic data into the document
- No programming logic (loops, conditionals)
- Verbose and takes long to write

Many have built-in JS functionality in inject JS logic into the document.

Some different templating languages:

- EJS
- Handlebars
- Mustache
- JSX

## What is the difference between `canvas` and `svg`?

`<svg>`

- Vector based (composed of shapes)
- Better scalability
- Multiple graphical elements, which become the part of the page’s DOM tree.

`<canvas>`

- Raster based (composed of pixels)
- Poor scalability, not suitable for printing on high resolutions
- Single element similar to `<img>` in behavior. Canvas diagram can be saved to PNG or JPG format.

_Note:_ HTML5 specifications recommends to avoid canvas if there are other alternatives

## What are empty elements in HTML ?

An element that _cannot_ have any child nodes
Using a closing tag on an empty element is usually invalid. (E.g. `<input type="text"></input>`)
A few examples of empty elements

- `<area>`
- `<br>`
- `<hr>`
- `<link>`
- `<source>`

## SSR & CSR

Server-side Rendering

- user makes request to webpage, the server sends the required HTML and data from the database and sends it to the user's machine
- page is rendered and prepared on the server
- page is fully rendered when it arrives to the user
- when navigating to a different route, the server needs to do all the work again, hence the full page refresh

  **Advantages**:

  - SEO is a priority - this is because the webpage is more friendly to search engine bots that can effectively crawl the page
  - website has a faster initial load - eliminates blank page problem of CSR
  - better experience for users that have poor internet connection
  - ideal for static sites (not much user interaction)

Client-side Rendering

- user makes request to webpage, the server will send a single page skeleton instead, along with the javascript file.
- page is rendered on the client browser
- when navigating to a different route, the server will not send another page, instead, the client will re-render the page according to the specified route
- SPA = no refresh needed

  **Advantages**:

  - SEO is not a priority
  - site has lots of user interaction or site re-routes (better seamless user experience)
  - better performance after initial load
  - ideal for web apps

## Dynamic vs SPA vs Static sites

3 main ways to render websites

1. Dynamic pages

- generated dynamically on the server, with help of server-side language (e.g. Node.js) and templating engine
- old methodology that was widely used 10+ years ago

  **Advantages**:

  - client receives the finished website along with all the data
  - important if the client is not a user but a web crawler (good for SEO)
  - logic happens on the server, not performance intensive for client browser

  **Disadvantages**:

  - EVERY page needs to be generated on the server, even if just one detail/data changes on the page, a new page has to be requested and sent back to client

2. SPA

- server generates a single, pre-generated HTML page which contains JS code. The bundled JS code changes the page dynamically WITHIN the browser (Client-side rendering)

  **Advantages**:

  - Amazing performance and responsive for UX

  **Disadvantages**:

  - Slow initial load, esp with poor internet connection
  - not great for SEO (but there are solutions to this, such as SSR SPA tools)

3. Static pages

- HTML pages are pre-generated on the server using a static site generation tool. The pre-generated pages are then stored on the server
- oldest technique used
- if we want to create a static page using dynamically changing content, we can do so by using static site generating tools like Gatsby.js
- Gatsby uses a React app that builds locally and then it 'visits' every page that would exist on the SPA. Snapshots would get stored as HTML files, which is then sent to the server.

  **Advantages**:

  - No initial JS load, fast start time
  - By using static site generators, we essentially get the benefits of SPA (fast updates, instant changes)

  **Disadvantages**:

  - Not great for sites that have lots of user interactivity, as each update would require the site to be re-generated and re-deployed

## What is Hydration?

Hydration is the process of using client-side JS to add app-like state and interaction to the server-rendered HTML.
Tools like Gatsby use hydration to transform the static HTMl created at build time into a React app.

In typical React app, the app relies on CSR. Instead of parsing HTMl to create the DOM, CSR uses JS to create it. Typical navigation links builds the requested page on the client instead of requesting it from the server. Because they make fewer network requests, CSR is extremely fast.

SSR makes HTML available to the client BEFORE the JS loads. Users can view and read content before it is fully interactive. SSR eliminates the blank page problem. However, SSR makes more network requests - every URL request needs a round trip to the server.

Hydration takes a hybrid approach.

Gatsby build process uses Node.js and ReactDOMServer to create 2 different versions of your site. Each URL is available both as a static HTML page and as a JS component.

When visitor first enters your site, the response contains static HTML along with JS and assets. React takes over and then _hydrates_ the HTML (add event listeners to DOM). Subsequent page requests are DOM updates managed by React.

Essentially you get "best" of both worlds - better SEO due to SSR static HTML on initial load, and better UX/performance.
