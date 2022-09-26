## What is React Query?

React Query is a server state management library. It streamlines state fetching from the server.

Server state = any piece of data that is retrieved from server

React Query maintains a global cache for all the GET requests. The cache is like a dictionary which stores the fetched data against keys call `query keys`.
  - this makes it super easy to use the same `useQuery` hook in multiple components, and it will only fetch data once and return it from the cache
  - sort of like redux, where we fetch data from the server and make it available _everywhere_

Once data is fetched, React Query keeps track of aspects suchs as cache time. It manages the cache internally and also updates the cache so that the data is in sync with the server's state.

React query provides a [debugging tool](https://react-query.tanstack.com/devtools) to keep track of all the queries in the application.

