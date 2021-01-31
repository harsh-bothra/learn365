# GraphQL Series Part - 1

Index | Section
--- | ---
**1** | [About the attack](#About-the-attack)
**2** | [Introspection Queries](#Introspection-Queries)
**3** | [Some Attacks in GraphQL](#Some-Attacks-in-GraphQL)
**4** | [Practice](#Practice)
**5** | [References](#References)
___

### About the attack
```
- GraphQL is a query language for the underlying API. 
- A single endpoint can be used as a query API to perform all the actions including Create, Read, Update & Delete.
- GraphQL has its own type of system that’s used to define the schema of an API. The syntax for writing schemas is called Schema Definition Language (SDL).

A GraphQL operation can be of type:
1. query (a read-only fetch)
2. mutation (a write followed by fetch)
3. subscription (a long‐lived request that fetches data in response to source events.)
- A GraphQL document can contain one or more of these operations (i.e multiple queries/mutations/subscriptions).
- Mutations queries modify data in the data store and returns a value.
- Fields: describes a discrete piece of info. This info could be simple or complex with relationships between data.
- Directives are identifiers that add additional functionality wi/o affecting the value of the response but can affect what response comes back to the client.
```

### Introspection Queries
```
A GraphQL server supports introspection over its schema using the same GraphQL query language.
A server exposes the following introspection queries on the Query operation type.
__schema
__type
__typename
Note that introspection queries start with __
```


### Some Attacks in GraphQL 
```
1. Unauthenticated Access to GraphQL Endpoint 
2. Introspection Queries are Enabled
3. GraphQL in Debug Mode
4. Application Level DoS
5. SQL Injection
6. IDOR
7. Data Exposure through Error Messages
8. Misc. GraphQL Attacks

- Unauthenticated Access to the GraphQL Endpoint
1. Supposed your target runs GraphQL, now as an unauthenticated user hit the following URL: 
https://your_target/graphiql
2. If you are able to access the GraphQL Console, try running some schema extraction or other queries
3. Alternatively you can also try to query https://your_target_url/graphql?query={query_here} 
4. If you are able to extract information as an unauthenticated user, this is an issue.
```

### Practice
- https://owasp-skf.gitbook.io/asvs-write-ups/kbid-285-graphql-introspection

### References
- https://graphql.org/learn/
- https://hasura.io/learn/graphql/intro-graphql/introspection/
