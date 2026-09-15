# ADR-001: FitFlow Technology Stack Selection

## Title
Selection of Technology Stack for FitFlow Redesign

## Status
Accepted

## Date
2026

## Context

FitFlow is a fitness tracking application that requires a redesign to address declining user retention. The application needs to support Android, iOS and web platforms from a shared codebase. Key features include AI-powered personalised workout plans, camera-based nutrition tracking, community challenges with real-time updates, progress visualisation and secure user authentication. The development team is mid-sized and needs a stack that balances development speed, maintainability and performance.

Previous research (Labs 1–4) identified the main user needs: better personalisation, easier meal logging, improved motivation through community features, and more detailed progress tracking. Usability testing confirmed that five core user flows need to work well: Home Dashboard, AI Workout Planner, Progress Tracking, Community Feed and Nutrition Logger.

## Decision

The following technology stack was selected based on weighted comparison matrices:

| Layer | Technology | Score |
|---|---|---|
| Frontend | Flutter + Dart | 4.75 / 5 |
| Main Backend | NestJS + TypeScript | 4.55 / 5 |
| AI Microservice | FastAPI + Python | 4.35 / 5 |
| Database | PostgreSQL | 4.65 / 5 |
| Authentication | Firebase Authentication | 4.90 / 5 |

Additional infrastructure includes Redis for caching, Firebase Cloud Messaging for push notifications and WebSockets for real-time features.

A hybrid architecture with a separate AI microservice was chosen instead of a single monolithic backend.

## Rationale

1. **Flutter** was selected because FitFlow requires a consistent cross-platform experience across Android, iOS and web. Flutter scored highest (4.75/5) due to strong code reusability, web compatibility, development speed and UI consistency.

2. **NestJS** was selected as the main backend because it provides a structured, modular architecture using TypeScript. It scored highest (4.55/5) for API development, real-time WebSocket support, scalability and maintainability.

3. **FastAPI** was retained as a separate AI microservice rather than integrating AI into NestJS. Python provides the best ecosystem for machine learning. Separating the AI service allows independent scaling and development.

4. **PostgreSQL** was selected because FitFlow contains strongly related data (users, workout plans, workouts, progress, meals, challenges). It scored highest (4.65/5) for query performance, data relationships, security and data integrity.

5. **Firebase Authentication** was selected because it provides easy Flutter integration, handles password security, supports social login and MFA. It scored highest (4.90/5) among authentication options.

## Consequences

- Developers need to learn Dart for Flutter development.
- Running two separate backend services increases deployment complexity.
- Firebase Authentication creates a dependency on Google's Firebase platform.
- The microservice architecture requires internal API contracts to be maintained.
- PostgreSQL requires structured schema planning.

## Alternatives Considered

- **React Native** – Closest frontend alternative but Flutter provided better UI consistency and web support.
- **Go** – Considered for backend but required more development effort for this project scope.
- **MongoDB** – Considered for database but PostgreSQL better handles FitFlow's relational data.
- **Supabase Auth** – Considered but Firebase Authentication offered stronger Flutter integration.
