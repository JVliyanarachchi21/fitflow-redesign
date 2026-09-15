# FitFlow Architecture Overview

## System Architecture

The FitFlow application uses a hybrid microservice architecture with the following key components:

### Frontend – Flutter App (Android / iOS / Web)

The Flutter application provides all user interface screens including the Home Dashboard, AI Workout Planner, Progress Tracking, Community Feed and Nutrition Logger. It communicates with the NestJS backend through REST APIs and WebSockets. Firebase Authentication SDK handles user login directly in the app.

### Main Backend – NestJS (TypeScript)

The NestJS backend handles all core business logic including user management, workout plans, progress tracking, nutrition logging, community challenges and notifications. It verifies Firebase tokens on each request and communicates with PostgreSQL for data storage and FastAPI for AI features.

### AI Microservice – FastAPI (Python)

A separate Python-based microservice for AI/ML functionality. It generates personalised workout recommendations and processes food images for nutrition tracking. It is developed and scaled independently from the main backend.

### Database – PostgreSQL

Stores all structured relational data including users, workout plans, workout history, progress records, nutrition logs and community challenges.

### Caching – Redis

Caches frequently accessed data such as daily recommendations and leaderboard rankings to reduce database load.

### Push Notifications – Firebase Cloud Messaging

Delivers workout reminders, challenge invitations and social notifications to user devices.

### Real-Time – WebSockets (NestJS Gateway)

Provides live updates for the Community Feed, challenge progress and notification delivery.

## Data Flow – Personalised Workout Plan

```
User opens Workout Planner
    → Flutter sends request (user ID, goal, fitness level)
    → NestJS verifies token and fetches user data from PostgreSQL
    → NestJS sends user data to FastAPI AI Service
    → FastAPI generates personalised plan
    → NestJS saves plan and caches in Redis
    → Flutter displays personalised workout plan
```

## Data Flow – Community Challenge

```
User opens Community Feed
    → Flutter connects via WebSocket
    → NestJS fetches challenges from PostgreSQL
    → User joins challenge
    → NestJS creates participation record
    → NestJS sends FCM notification to members
    → NestJS broadcasts update via WebSocket
```

## Data Flow – Nutrition Tracking

```
User taps Scan Food
    → Flutter opens camera
    → User captures photo
    → Flutter uploads image to NestJS
    → NestJS forwards to FastAPI for food recognition
    → FastAPI returns detected food and nutrition
    → User confirms meal
    → NestJS saves nutrition log to PostgreSQL
```

## Security

- Firebase Authentication with token verification on all requests
- HTTPS/TLS encryption for all communication
- Role-based access control in NestJS
- Input validation using DTOs and validation pipes
- GDPR/CCPA compliant data handling
- API rate limiting

## Scalability

- Separate AI microservice for independent scaling
- PostgreSQL read replicas and connection pooling
- Redis caching to reduce database load
- Horizontal scaling with load balancing
- WebSocket scaling with Redis pub/sub
