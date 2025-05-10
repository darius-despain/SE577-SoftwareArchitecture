# ADR 3: Data Persistence Layer - MySQL

## Status

Accepted

## Context

"Home Cook Collective" needs a reliable way to store its core data, which includes users, recipes, and ingredients. The system must ensure data integrity, handle relational queries effectively, and support rapid initial development.

## Decision

We will use MySQL as the primary database management system.

## Rationale

MySQL is a good fit because it offers a solid mix for our needs:

- Developers are generally familiar with SQL.
- It handles a relational data model and our data integrity requirements well.
- It's cost-effective, being open-source with managed options available.
- Its strong ecosystem will also help in developing the MVP quickly.

### Rejected Alternatives

- PostgreSQL: A strong Relational Database alternative; MySQL chosen due to perceived broader team/tooling familiarity for rapid initial setup.
- NoSQL (e.g. MongoDB): Rejected for primary data due to the highly relational nature of our core data and the need for strong consistency/joins provided by SQL.

## Consequences

### Positive

- Development should be faster since the team is familiar with SQL.
- Enforces data integrity for critical application data.
- It's a mature technology that performs well for typical web applications and has a good supporting ecosystem.

### Negative

- Requires upfront schema design, offering less flexibility for unstructured data than NoSQL.
- Potential for object-relational impedance mismatch if not carefully managed.
