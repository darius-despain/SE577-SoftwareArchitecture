# ADR 2: Authentication System

## Status

Accepted

## Context

"Home Cook Collective" requires a secure, user-friendly, and standardized authentication method for its web and mobile users that supports rapid initial development.

## Decision

We will use OpenID Connect (OIDC) as the primary protocol for user authentication. Initially, Google Sign-In (Google SSO) will be implemented as the sole OIDC Identity Provider.

For authorization and secure communication between internal system components (e.g., client to API, service-to-service), OAuth 2.0 access tokens (obtained as part of the OIDC flow) will be utilized.

## Rationale

OIDC with Google SSO provides a secure, industry-standard solution that enhances user convenience (via familiar Google login) and accelerates initial development by offloading credential management. The use of OAuth 2.0 tokens ensures uniform, less complex security across system components.

### Rejected Alternatives

- **Building a Custom Username/Password System:** Rejected due to higher development effort, security risks, and maintenance burden.
- **SAML:** Rejected due to greater complexity for consumer-facing mobile/web apps compared to OIDC.
- **Other Social SSO Providers (e.g., Facebook, Apple):** Deferred to simplify MVP development; OIDC allows future integration.

## Consequences

### Positive

- Simplified sign-up/sign-in for users with Google accounts.
- Reduced development effort and security burden by offloading credential management to Google.
- Standardized, token-based security for APIs.

### Negative

- Initial dependency on Google's availability and policies.
- Users without Google accounts (or unwilling to use them) cannot sign up in the first version.
- Requires careful implementation of token handling on client and server.
