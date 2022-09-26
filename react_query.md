## What is React Query?

React Query is a server state management library. It streamlines state fetching from the server.

Server state = any piece of data that is retrieved from server

React Query maintains a global cache for all the GET requests. The cache is like a dictionary which stores the fetched data against keys call `query keys`.
  - this makes it super easy to use the same `useQuery` hook in multiple components, and it will only fetch data once and return it from the cache
  - sort of like redux, where we fetch data from the server and make it available _everywhere_

Once data is fetched, React Query keeps track of aspects suchs as cache time. It manages the cache internally and also updates the cache so that the data is in sync with the server's state.
  - _stale-while-revalidate_ caching strategy

React query provides a [debugging tool](https://react-query.tanstack.com/devtools) to keep track of all the queries in the application.

#### StaleTime vs CacheTime

StaleTime
- duration until a query transitions from fresh to stale. If fresh, the data will always be read from the cache - no network requests happen
- default 0 seconds

CacheTime
- duration until inactive queries will be removed from the cache. Queries are considered inactive as soon as there are no observers registered; so when all components which use that query have unmounted
- default 5 minutes

### Keep server and client state separate

- If you get data from useQuery, try not to put that data into local state. The main reason is that you implicitly opt out of all background updates that React Query does for you, because the state "copy" will not update with it.
- Read more here: [Practical React Query](https://tkdodo.eu/blog/practical-react-query)

#### Enabled option is very powerful

- 
