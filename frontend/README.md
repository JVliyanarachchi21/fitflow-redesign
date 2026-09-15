# FitFlow Frontend

## Technology
- **Framework:** Flutter
- **Language:** Dart

## Description
The Flutter application provides the cross-platform client for FitFlow, targeting Android, iOS and web from a single codebase.

## Core Screens
- Home Dashboard (AI Daily Flow recommendation)
- AI Workout Planner (goal-based personalised plans)
- Progress Tracking (statistics and charts)
- Community Feed (challenges and social features)
- Nutrition Logger (camera-based food scanning)

## Setup
```bash
flutter pub get
flutter run
```

## Dependencies (Planned)
- `firebase_auth` – Firebase Authentication
- `http` / `dio` – API communication
- `web_socket_channel` – WebSocket connections
- `fl_chart` – Progress charts and visualisations
- `camera` – Device camera for nutrition scanning
- `firebase_messaging` – Push notifications
- `provider` / `riverpod` – State management
