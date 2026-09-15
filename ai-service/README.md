# FitFlow AI Service

## Technology
- **Framework:** FastAPI
- **Language:** Python

## Description
The FastAPI AI microservice handles all AI and machine learning functionality for FitFlow. It runs as a separate service from the main NestJS backend and communicates through internal REST APIs.

## Core Features (Planned)
- **Workout Recommendation Engine** – Generates personalised workout plans based on user goals, fitness level, workout history and progress data.
- **Plan Adaptation** – Adjusts recommendations based on user performance and feedback.
- **Food Image Recognition** – Processes meal photos to identify food items and estimate nutritional information.
- **Future ML Models** – Framework for adding new ML capabilities as FitFlow evolves.

## Setup
```bash
pip install -r requirements.txt
uvicorn main:app --reload
```

## API Endpoints (Planned)
```
POST /api/v1/recommend-workout    – Generate personalised workout plan
POST /api/v1/adapt-plan           – Adapt existing plan based on progress
POST /api/v1/scan-food            – Analyse food image and return nutrition data
GET  /api/v1/health               – Health check
```

## Environment Variables
```
DATABASE_URL=postgresql://user:password@localhost:5432/fitflow
MODEL_PATH=./models
```
