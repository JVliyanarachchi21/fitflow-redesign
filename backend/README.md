# FitFlow Backend

## Technology
- **Framework:** NestJS
- **Language:** TypeScript
- **Database:** PostgreSQL (via TypeORM)
- **Caching:** Redis

## Description
The NestJS backend is the main application server for FitFlow. It handles all core business logic including user management, workout plans, progress tracking, nutrition logging, community challenges and real-time features.

## Core Modules (Planned)
- **Auth Module** – Firebase token verification and role-based access
- **Users Module** – User profiles and preferences
- **Workouts Module** – Workout plans, exercises and tracking
- **Progress Module** – Fitness statistics and goal tracking
- **Nutrition Module** – Meal logging and nutrition data
- **Community Module** – Challenges, posts and social features
- **Notifications Module** – FCM push notification triggers
- **AI Gateway Module** – Communication with FastAPI AI service

## Setup
```bash
npm install
npm run start:dev
```

## Environment Variables
```
DATABASE_URL=postgresql://user:password@localhost:5432/fitflow
REDIS_URL=redis://localhost:6379
FIREBASE_PROJECT_ID=your-firebase-project
AI_SERVICE_URL=http://localhost:8000
```
