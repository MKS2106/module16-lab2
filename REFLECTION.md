# REFLECTION

## 1. Over-fetching happens when a REST API returns more data than needed, often because endpoints send full objects or large datasets even if the client only needs a few fields.
Example: 
- Users call /users/:id1  to get a user's name and profile picture.
- The server responds with the entire user object—address, phone number, preferences, etc.
Your app only uses two fields, but the rest still travels over the network.


Under-fetching is when an endpoint returns too little data, requiring multiple additional requests to gather everything the client needs.
Example :
- You call /posts/:id to get a blog post.
- But the author info is stored separately, so you now need to call /users/:id to get the author’s name.
- You end up making multiple round trips to assemble the full picture.

GraphQL solves both by allowing clients to specify exactly what data they want in a single query. This avoids extra or missing data, making data transfer more efficient and precise.

## 2. 
- REST can over/under-fetch but GraphQL fetches just what’s needed.This results in more efficient and faster communication between client and server.
- REST often needs versioning GraphQL evolves its schema.
- GraphQL has a strongly-typed schema for clear contracts.
- Frontend devs get autocompletion, early error detection.
- Schema is self-documenting—no waiting on backend docs.

## 3.
Caching is simpler in REST because each resource has a unique URL (e.g., GET /products/:id), allowing standard HTTP caches to store responses based on method and URL. This makes it easy to cache data at the browser or CDN level without extra configuration.
In GraphQL, all queries use the same endpoint (/graphql), and data is requested in the body of the request. Since the URL doesn't change, traditional caching strategies don't work well, and caching must rely on custom logic or in-memory cache.
A good use case where GraphQL’s flexibility is worth the caching complexity is a social media feed where users see personalized content—like a mix of posts, comments, and user info—all fetched in one flexible query tailored to the UI. This reduces the number of API calls and simplifies frontend logic, even if caching is more complex.