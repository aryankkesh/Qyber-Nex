# QYBERNEX

QYBERNEX is an AI-driven adaptive cyber deception and quantum-safe threat intelligence platform. This repository contains a working starter implementation with a FastAPI backend and a React + TypeScript + Tailwind frontend for a security operations experience.

## Cross-platform compatibility status

This implementation includes the shared architecture required for multi-device delivery:

- Responsive web application for Windows, macOS, Linux, Android, iPhone, and tablet browsers
- Progressive Web App capabilities with manifest and service worker registration
- Capacitor project shells for Android and iOS packaging
- Standardized production API configuration through environment variables
- Network-aware UI that degrades gracefully offline and shows live-status messaging

Important: the project is prepared for Android/iOS packaging, but no signed APK or IPA is claimed to have been generated in this environment. A signed Android release and any iOS IPA still require platform-specific signing workflows on Android Studio / Xcode with valid developer credentials.

## Included capabilities

- Role-based authentication and JWT session handling
- Protected dashboard APIs with secure headers and CORS controls
- AI-style threat intelligence and incident summaries
- Honeypot monitoring and security event views
- Admin user list and access control
- SQLite-first local development with PostgreSQL-ready Docker configuration
- PWA manifest and offline shell support
- Cross-platform download page and install guidance

## Project structure

- `backend/` — FastAPI API, JWT auth, SQLAlchemy models, demo data, and tests
- `frontend/` — React + Vite dashboard UI, PWA assets, Capacitor config, and download page
- `docker-compose.yml` — local PostgreSQL, backend, and frontend environment
- `android/` and `ios/` — generated Capacitor native project shells

## Quick start

### 1) Backend

```bash
cd backend
python -m venv .venv
. .venv/Scripts/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### 2) Frontend

```bash
cd frontend
npm install
cp .env.example .env
npm run dev -- --host 0.0.0.0 --port 5173
```

### 3) Run the full stack with Docker Compose

```bash
docker compose up --build
```

### 4) Android / iOS packaging preparation

```bash
cd frontend
npm run build
npx cap sync
npm run android:open
npm run ios:open
```

## Default demo credentials

The demo mode seeds a default administrator account:

- Email: `admin@qybernex.local`
- Password: `Admin123!`

## Environment variables

Copy the sample files and adjust values if needed:

```bash
cp .env.example .env
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

Use production API URLs through environment configuration only. Do not hardcode localhost endpoints into production builds.

## Compatibility test matrix

| Platform | Browser / environment | Status |
|---|---|---|
| Windows 10/11 | Chrome / Edge | Prepared for responsive browser testing |
| macOS | Safari / Chrome | Prepared for responsive browser testing |
| Linux | Firefox / Chrome | Prepared for responsive browser testing |
| Android | Chrome mobile | Prepared for PWA and Capacitor packaging |
| iPhone / iPad | Safari | Prepared for PWA and iOS packaging workflow |

This project does not claim device-specific verification beyond what was actually executed in this environment. The PWA install and native platform packaging steps are configured, but full signed release generation requires a matching platform signing environment.

## Validation

The backend test suite is in `backend/tests/test_api.py` and was validated locally with pytest.
The frontend production build was validated with `npm run build`.
The QYBERNEX PWA and Capacitor project shells were created and configured for cross-platform packaging.
