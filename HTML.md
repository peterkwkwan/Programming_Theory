## HTML Questions

### What does a `doctype` do?

- All HTML documents must start with a `DOCTYPE` declaration
- It is NOT an HTML tag, but rather an indicator to the browser of what type of document to expect, along with the version of HTML
- Ensures the document is parsed consistently across different browsers
  **Note**: doctype is not case-sensitive

```
<!DOCTYPE html>
```

### Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

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

![Cookies, LocalStorage & SesstionStorage](./assets/storage.png?raw=true)

### Describe the difference between `<script>`, `<script async>` and `<script defer>`.

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

### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions? Why `<script>` tag goes last?

When the browser encounters any JS, it will pause the document parsing and execute the JS first. Hence if `<script>` was added at the top, it would make the page render slow and provide a bad user experience. As well, because the DOM is not fully loaded, JS won't be able to manipulate the elements.

CSS are linked in the head because they get applied regardless of whether DOM is ready. Hence webpages looks good as soon as page loads, and is seen as it should be aesthetically.

### What is progressive rendering?

A technique used to render content for display as quickly as possible. Some techniques used:

- Lazy loading of images - will load an image when it comes into the viewport instead of loading all at once.
- Prioritizing visible content where you only include the minimum css/content/scripts necessary for the amount of pages that would be rendered in the users' browser. Use deferred JS to load in other resources and content.

_TLDR;_ Render the browser optimally by rendering the critical content first and non-critical parts later.

### Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.

It is a technique used to render the optimal image resolution based on the different viewport sizes of users.

```
<img src='image.jps'
srcset='image_small.jpg 360w, image_medium.jps 720w, image.jpg 1400w'/>
```

Each comma-seprated item has imageUrl along with the width of the image in pixels (or display density)

### What are HTML templating languages?

Different ways to split HTML code into reusable components. Many have built-in JS functionality in inject JS logic into the document.

### What is the difference between `canvas` and `svg`?

### What are empty elements in HTML ?

### SSR & CSR

### Explain the difference between layout, painting and compositing.
