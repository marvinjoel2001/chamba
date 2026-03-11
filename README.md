# Chamba Fullstack Scaffold

This workspace contains:

- `backend/`: NestJS API (TypeORM + PostgreSQL/PostGIS, Redis, Socket.io, Cloudflare R2-ready)
- `mobile/`: Flutter app (clean architecture-style folders, Riverpod, login/home starter screens)

## Backend quick start

0. (Optional) start local infra:

```bash
docker compose up -d
```

1. Copy env file:

```bash
cd backend
cp .env.example .env
```

2. Update `.env` with your real credentials.

3. Run backend:

```bash
pnpm install
pnpm start:dev
```

API base URL: `http://localhost:3000/api`

## Mobile quick start

```bash
cd mobile
flutter pub get
flutter run \
  --dart-define=API_BASE_URL=http://localhost:3000/api \
  --dart-define=SOCKET_BASE_URL=http://localhost:3000
```

Optional Firebase mobile push defines:

```bash
--dart-define=FIREBASE_API_KEY=... \
--dart-define=FIREBASE_APP_ID=... \
--dart-define=FIREBASE_MESSAGING_SENDER_ID=... \
--dart-define=FIREBASE_PROJECT_ID=... \
--dart-define=FIREBASE_STORAGE_BUCKET=...
```

## What is pre-wired

- Users module (`controller`, `service`, `entity`, `DTOs`)
- Redis session middleware and Redis cache service
- Socket.io gateway at `/realtime` namespace
- Cloudflare R2 storage service using S3-compatible SDK
- Firebase FCM push wiring (`/api/notifications/status`, `/api/notifications/test-push`)
- Dependency health probe (`/api/health`: Postgres + PostGIS + Redis)
- Placeholder API module for future business domains
