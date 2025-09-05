# Lab 16.2: API Flexibility Analysis

[Karl Johnson](https://github.com/hirekarl)  
2025-RTT-30  
<time datetime="2025-09-04">2025-09-04</time>  

## Assignment
### Scenario
Now that your team has a solid plan for connecting the client and server, the conversation has shifted to long-term API strategy. The default choice is a traditional REST API, but some team members have brought up GraphQL as a potential alternative. They argue it could solve common data-fetching problems and make the frontend development process faster.

Your tech lead has asked you to research the practical differences between REST and GraphQL. Your task is to prepare a document that compares the two, analyzes their respective trade-offs, and provides a recommendation on when to choose one over the other.

### Instructions
#### Task 1: Reading Assignment
Please read the following articles. They provide a detailed analysis of the strengths, weaknesses, and ideal use cases for both REST and GraphQL.

- **Article 1**: [GraphQL vs REST: A Comprehensive Comparison](https://hygraph.com/blog/graphql-vs-rest-apis)
- **Article 2**: [Is GraphQL Better Than REST? A Comparison](https://tailcall.run/graphql/graphql-vs-rest-api-comparison/)
- **Article 3**: [GraphQL vs REST: API Showdown](https://medium.com/@programordie/graphql-vs-rest-api-showdown-fcf11d9c4fe6)

Focus on how the design of each API style impacts both the backend (implementation, caching) and the frontend (data fetching, performance).

#### Task 2: Written Reflection
After reading the articles, answer the following questions in a clear and concise manner. Your total response should be between 300 and 500 words.

##### 1. The Over-fetching Problem
In your own words, explain the concepts of “over-fetching” and “under-fetching” in the context of a REST API. How does GraphQL’s query language inherently solve this problem?
> In a REST API, "under-fetching" has to do with the ways in which an HTTP request does not fetch all the required data. For instance, a social media application may require calls to a `users` endpoint, then a `posts` endpoint, then a `comments` endpoint, just to get the comments related to a specific user's specific post.
>
> "Over-fetching" has to do with the ways in which an API call to a REST API fetches *too much* data. For instance, in the social media application scenario described above, the call to the `users` endpoint will return more data than is necessary; e.g., the user's birthday, email address, and URL to a profile photo, which have nothing to do with the end goal of fetching comments.
>
> GraphQL solves this issue by giving clients the ability to grab only the components of each resource it needs, and allows them to lodge a request against multiple resources in one go. What might take three fetches in a REST API can be effectively done with one fetch in a GraphQL API.

##### 2. Endpoint and Schema Philosophy
Compare the endpoint structure of a typical REST API with that of a GraphQL API. How does GraphQL’s strongly-typed schema benefit frontend developers?
> A REST API contains endpoints for each separate resource (e.g., `/api/users` as an endpoint for user resources), whereas all GraphQL queries are lodged against a single endpoint, typically `/graphql`.
>
> Whereas in a REST API, where developers need to rely on human-generated API documentation that may become outdated, difficult to parse, or riddled with inaccuracies, GraphQL's strongly-typed schemas provide the infrastructure for self-documenting resources that are coupled to the data itself. This allows for type-checking and autocompletion in IDEs, documentation that is automatically synced to the shape of resources, and the ability to work with dynamic, flexible resources that can change without the explicit versioning between resource shapes that is characteristic of REST APIs.

##### 3. Caching and Complexity
Caching is often cited as a major advantage of REST. Explain why caching is simpler in REST compared to GraphQL. What is a use case where the flexibility of GraphQL might outweigh its caching complexity?
> REST leverages features already built into HTTP infrastructure to manage caching. Because REST resources are at fixed endpoints, HTTP headers like `Cache-Control` and `E-Tag` can be used to cache resources at those fixed endpoints. GraphQL, on the other hand, requires application-level caching behavior, since all queries are lodged against a singular endpoint; and all requests are `POST` requests, which are not cacheable by HTTP. This makes implementing cache behavior in GraphQL more complex than REST.
>
> In the case of a social media application, as mentioned above, a query for the comments on a specific user's specific post requires grabbing multiple resources over several API calls. Though REST's ability to work with HTTP headers to control caching makes it more efficient in some scenarios, the issue with retrieving those comments is that it still requires several calls to the API due to under-fetching. GraphQL's ability to grab all the necessary data in one call saves network resources and may ultimately result in better performance, above and beyond the performance savings that come from caching.
