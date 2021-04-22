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

{% tab title="App Design Patterns" %}
```csharp
# Application architecture patterns
- Monolithic architecture
- Microservice architecture



// ------------------------------------------------------------------------------

# Decomposition

- Decompose by business capability
- Decompose by subdomain
- Self-contained Service
- Service per team


# Strangler Application
- Anti-corruption layer


# Data management
- Database per Service
- Shared database
- Saga // distributed transactions
- API Composition
- CQRS
- Domain event
- Event sourcing


# Transactional messaging
- Transactional outbox
Transaction log tailing
Polling publisher


# Testing
- Service Component Test
- Consumer-driven contract test
- Consumer-side contract test


# Deployment patterns
- Multiple service instances per host
- Service instance per host
- Service instance per VM
- Service instance per Container
- Serverless deployment
- Service deployment platform


# Cross cutting concerns

Microservice chassis
Service Template
Externalized configuration


# Communication style

Remote Procedure Invocation
Messaging
Domain-specific protocol
Idempotent Consumer


# External API
- API gateway
- Backend for front-end


# Service discovery
- Client-side discovery
- Server-side discovery
Service registry
Self registration
3rd party registration


# Reliability
- Circuit Breaker


# Security
- Access Token


# Observability
- Log aggregation
- Application metrics
- Audit logging
- Distributed tracing
- Exception tracking
- Health check API
- Log deployments and changes


# UI patterns
- Server-side page fragment composition
- Client-side UI composition
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





## Design Patterns:

{% tabs %}
{% tab title="BE" %}
```javascript
1. Circuit Breaker
2. Command and Query Responsibility Segregation (CQRS)
3. Event Sourcing
4. Sidecar
5. Backend-for-Frontend
6. Strangler
```
{% endtab %}

{% tab title="Details" %}
* [https://betterprogramming.pub/modern-day-architecture-design-patterns-for-software-professionals-9056ee1ed977](https://betterprogramming.pub/modern-day-architecture-design-patterns-for-software-professionals-9056ee1ed977)
* [https://betterprogramming.pub/the-roles-of-service-mesh-and-api-gateways-in-microservice-architecture-f6e7dfd61043](https://betterprogramming.pub/the-roles-of-service-mesh-and-api-gateways-in-microservice-architecture-f6e7dfd61043)
{% endtab %}

{% tab title="" %}

{% endtab %}
{% endtabs %}





