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



{% tabs %}
{% tab title="React \(Design Patterns\)" %}
**Design Pattern:**

1. State-full or class-based components \(Smart Component\)
2. State-less or function-based components \(Dumb Component\)
3. State-full or function-based components \(using Hooks\) \(Smart Component\)
4. Presentational \(or high-order\) components
5. Container components

React Coding Pattern:

* [Container component](https://reactpatterns.com/#container-component)
* [Higher-order component](https://reactpatterns.com/#higher-order-component)
* [Controlled input](https://reactpatterns.com/#controlled-input)
* [Function as children](https://reactpatterns.com/#function-as-children)
* [Proxy component](https://reactpatterns.com/#proxy-component)
* [Layout component](https://reactpatterns.com/#layout-component)
* [State hoisting](https://reactpatterns.com/#state-hoisting)
* [JSX spread attributes](https://reactpatterns.com/#jsx-spread-attributes)
* [Props](https://reactpatterns.com/#props)
* [defaultProps](https://reactpatterns.com/#defaultprops)
* [Expressions](https://reactpatterns.com/#expressions)
* [Children pass-through](https://reactpatterns.com/#children-pass-through)
* [Children types](https://reactpatterns.com/#children-types)
* [Render prop](https://reactpatterns.com/#render-prop)
* [Style component](https://reactpatterns.com/#style-component)

**Problems:**

* [Prop Drilling](https://kentcdodds.com/blog/prop-drilling/)
* ..
{% endtab %}

{% tab title="React / Redux - Folder Structure" %}
* [Fractal Design Pattern](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af)
* [Redux Duck Pattern](https://www.freecodecamp.org/news/scaling-your-redux-app-with-ducks-6115955638be/)
* 
{% endtab %}

{% tab title="GraphQL Pattern" %}
* [Parameter Object Pattern \(Input: Object type\)](https://atheros.ai/blog/input-object-type-as-an-argument-for-graphql-mutations-and-queries)
  * [https://graphql.org/graphql-js/mutations-and-input-types/](https://graphql.org/graphql-js/mutations-and-input-types/)
* ...
{% endtab %}
{% endtabs %}



