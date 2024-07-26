# 26-07-2024

## *Working with GraphQL*

### WHAT IS GRAPHQL?

- `REST API, Stateless, client-independent API for exchanging data`
- `GraphQL API, Stateless, client-independent API for exchanging data with higher query flexibility`

#### REST API Limitations

- API endpoint `GET /post`, fetch posts, that returns the below json object, 
```javascript
{
  id: '1',
  title: 'First Post',
  content: '...',
  creator: {...}
}
```
- What if we only need the title & id?

#### Solution 1
- Create a new REST API endpoint (e.g. GET/post-slim)
- Problem: Lots and lots of endpoints and lots of updating

#### Solution 2
- Use query parameters (e.g. GET/post?data=slim)
- Problem: API becomes hard to understand

#### Solution 3
- Use GraphQL!
- Problem: None

#### How does GraphQL Work?
- Client can send request to only one kind of endpoint (POST/graphql), even for getting data
- This POST request contains Query Expression (to define the Data that should be returned)

#### A GraphQL Query
```javascript
{
  query {
    user {
      name
      age
    }
  }
}
// query => Operation type, other types: mutation, subscription
// user => Operation "endpoint"
// name, age => Requested fields
```

#### Operation Types
- Query, Retrieve Data ("GET")
- Mutation, Manipulate Data ("POST", "PUT", "PATCH", "DELETE")
- Subscription, Set up realtime connection via Websockets

#### GraphQL Big Picture
- Client sends request to the single GraphQL endpoint `POST/graphql` on the server
- We define `Type Definitions` on the server (Query Definitions, Mutation Definitions, Subscription Definitions) => Like Routes
- These Type Definitions are connected to the `Resolvers(contain your server-side logic) => Like Controllers`

#### How does GraphQL work?
- It's a normal Node (+ Express) Server!
- One Single Endpoint (typically /graphql)
- Uses POST because Request Body defines Data Structure of retrieved Data (POST for getting Data? Yep!)
- Server-side Resolver analyses Body, Fetches and Prepares and Returns Data

### UNDERSTANDING THE SETUP & WRITING OUR FIRST QUERY

- 