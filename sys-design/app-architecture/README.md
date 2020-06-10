# App Architecture

{% tabs %}
{% tab title="Full Stack" %}
```csharp
# Approaches
1. JAM Stack
2. Serverless Architecture (FaaS)
3. Kubernetes & Dockers
4. OnPrem


# Patterns:
- Micro Services
- Micro Frontend


# Auth: (OAuth)
- UAA
- Auth0
- OpenID Auth [Ex: Github, Google,...]

```
{% endtab %}

{% tab title="UI" %}
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

{% tab title="BE" %}
```text
- Micro Services
- Micro Frontend

```
{% endtab %}

{% tab title="Key Features" %}
```csharp

# Key Features

- CRUD
- Pagination (offsetBased / cursorBased)
- Wildcard Search
- Sort
- Concurrent Transaction (Locks) (Consistency)
- Async Transaction (Pub/Sub)

- Live Data Updates (periodicPollingData / webSocket[Pub/Sub][GraphQLSubscription])  
- Send Email Notifications

# File (Features):
- Import/Export File (BlobStore[Ex:S3], CDN[Ex:CloudFront]?)
- Full Text search (fileTextSearch) (InvertedIndex) [Ex:ElasticSearch]
- CollbarativeEdit 
    - using 'Lock' (Pessimistic Concurrency Control)
    - using 'Versioning & Conflict Resolution' (Opttimistic Concurrency Control) 
    - Strategies: (Operational Transformation / Differential Syncing)

```
{% endtab %}
{% endtabs %}





