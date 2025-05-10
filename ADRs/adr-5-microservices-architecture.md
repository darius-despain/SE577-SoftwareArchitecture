# ADR 5: Microservices Architecture

## Status

Accepted

## Context

"Home Cook Collective" requires a backend architecture that supports modularity for its diverse features (recipes, users, nutrition, media), allows for independent scaling of components (complementing Kubernetes capabilities), and enables efficient, focused development, particularly with a desire to explore modern decoupled service patterns.

## Decision

We will adopt a microservices architecture for the backend of "Home Cook Collective." Initial candidate services include: Recipe Service, User Service, Ingredient Service (handling USDA integration and caching), and Media Service.

## Rationale

This architecture was chosen because:

- It promotes strong modularity, independent deployments, and better fault isolation.
- It aligns well with the strengths of Kubernetes and facilitates focused development efforts.
- It allows for future flexibility and the application of modern distributed system patterns.

### Rejected Alternatives

- **Modular Monolith:** Rejected due to a preference for the stronger decoupling, independent scalability, and lifecycle management benefits offered by microservices, despite their higher initial complexity.
- **Serverless Functions (e.g., AWS Lambda, Google Cloud Functions):** Rejected as Kubernetes is already chosen for orchestration, making containerized microservices a more direct fit for primary backend logic, though serverless may be used for specific event-driven tasks.

## Consequences

### Positive

- Clear separation of concerns across distinct service boundaries.
- Independent scalability and deployment of individual services.
- Potential for technology diversity per service in the long term.
- Improved fault isolation between services.

### Negative

- Increased operational complexity (inter-service communication, distributed tracing, service discovery).
- Potential for higher latency due to network calls between services.
- More complex local development and testing setup compared to a monolith.
- Challenges with managing eventual consistency and distributed transactions if required.
