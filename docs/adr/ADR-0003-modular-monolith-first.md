# ADR-0003: Start with a Modular Monolith

## Status

Accepted

## Context

Starting directly with many microservices creates distributed-system complexity before the business domain is understood.

## Decision

Build the first MVP as a modular monolith with clear internal boundaries.

Initial modules:

- Authentication/User
- Problem
- Submission

## Rationale

This allows the team to:

- Understand business rules.
- Establish API contracts.
- Define transaction boundaries.
- Build tests.
- Validate the data model.
- Learn the domain before introducing network failures and distributed consistency.

## Consequences

Positive:

- Faster initial development.
- Easier debugging.
- Easier transactions.
- Lower infrastructure overhead.

Later work:

- Extract services based on proven boundaries.
- Introduce asynchronous messaging where it solves a real problem.
