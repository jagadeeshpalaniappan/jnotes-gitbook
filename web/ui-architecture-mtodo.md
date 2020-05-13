# UI Architecture \[MTODO\]

{% tabs %}
{% tab title="Tech Stack" %}
```csharp


# Web Components
- React (Virtual DOM)
- Angular
- Svelte


# State Management:
- Redux
- React Hooks (useContext, useReducer)

# Build Pack:
- Web Pack


# API :
- REST-API
    - fetch
    - axios
- GRAPHQL-API
    - graphql-request
    - apollo-boost
    

```
{% endtab %}

{% tab title="Concepts" %}
```csharp


# Pagination :
---------------
 - 'Offset' based pagination (also called 'Numbered' pagination)
     -- // getUsers({offset: 0, limit: 10}) // getUsers({offset: 10, limit: 10}) // getUsers({offset: 20, limit: 10}) // getUsers({offset: 30, limit: 10})
     -- One major downside of this approach is 'item can be skipped' or 'returned twice' when items are inserted into or removed from the list at the same time. 
     -- That can be avoided with cursor-based pagination.
 - 'Cursor' based pagination
 
 https://www.apollographql.com/docs/react/data/pagination/
 https://www.apollographql.com/blog/understanding-pagination-rest-graphql-and-relay-b10f835549e7
     

# Live Data :
-------------
- Periodic Polling Data (req/resp are send/received more than expected)
- Live Queries (Pub/Sub) // WebScoket / (GraphQL Subscription)



# Design Patterns :
---------------------
- BFF (Backend for Frontend Design Pattern) // E.g. GraphQL
    -- GraphQL schema should be driven by the 'UI Requirements'
- Higher Order Components
- Higher Order Functions
- Pure Functions (noSideEffects)


```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

