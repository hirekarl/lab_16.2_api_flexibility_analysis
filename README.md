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
> In a REST API, "over-fetching" and "under-fetching" refer to the ways in which resources are fixed by endpoints. In a social media app, getting the comments related to a user's post may involve first querying a `users` endpoint, then a `posts` endpoint, then a `comments` endpoint. "Over-fetching" refers to the ways in which the queries to each of these endpoints will return more data than is necessary to complete the initial request (e.g., a user resource may return the user's email address, birthday, and other data unrelated to the user's posts, let alone the comments related to a specific post); "under-fetching" refers to the ways in which three separate requests need to be made against the API to complete the request (i.e., a request first against `users`, then `posts`, then `comments`).
>
> GraphQL, by virtue of having a single endpoint and serving as a query language in and of itself, is able to grab only the necessary details related to the user's post's comments in a single query. Clients are able to specify exactly which fields are necessary to complete the request, and network usage is significantly cheaper by virtue of consolidating the request logic in a single query.

##### 2. Endpoint and Schema Philosophy
Compare the endpoint structure of a typical REST API with that of a GraphQL API. How does GraphQL’s strongly-typed schema benefit frontend developers?
> A REST API contains endpoints for each separate resource (e.g., `/api/users` as an endpoint for user resources), whereas all GraphQL queries are lodged against a single endpoint, typically `/graphql`. GraphQL's strongly-typed schema makes it easy for front-end developers to create complex queries without having to account for versioning, as in a REST API; and the strongly-typed nature of GraphQL means schemas are self-documenting and produce their own consistently formatted error messages. When running requests against a REST API, developers must rely on documentation to understand the structure of endpoints and expected responses, whereas GraphQL provides a much more streamlined experience.

##### 3. Caching and Complexity
Caching is often cited as a major advantage of REST. Explain why caching is simpler in REST compared to GraphQL. What is a use case where the flexibility of GraphQL might outweigh its caching complexity?
>