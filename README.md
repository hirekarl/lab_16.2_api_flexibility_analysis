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
>

##### 2. Endpoint and Schema Philosophy
Compare the endpoint structure of a typical REST API with that of a GraphQL API. How does GraphQL’s strongly-typed schema benefit frontend developers?
>

##### 3. Caching and Complexity
Caching is often cited as a major advantage of REST. Explain why caching is simpler in REST compared to GraphQL. What is a use case where the flexibility of GraphQL might outweigh its caching complexity?
>