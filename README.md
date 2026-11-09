# My Outfit

A responsive virtual fashion platform combining a personal 3D avatar, AI garment understanding and hybrid virtual try-on.

## Phase 1 starter scope

This scaffold includes:
- Next.js + TypeScript + Tailwind frontend
- Premium editorial-style responsive homepage
- Interactive Three.js / React Three Fiber placeholder avatar (drag to orbit)
- FastAPI backend with health and v1 status endpoints
- Local PostgreSQL and Redis services through Docker Compose
- Initial monorepo structure and environment template

The avatar in this starter is deliberately a **temporary geometric placeholder**, not the final body model. AI body scanning, authentication, uploads, garment recognition, and try-on are not implemented yet.

## Requirements

- Node.js 20.9+ (Node 22 LTS recommended)
- npm 10+
- Python 3.11+ (3.12 recommended)
- Docker Desktop (optional, for local PostgreSQL and Redis)

## 1. Install frontend dependencies

From the repository root:

```bash
npm install
```

## 2. Start the website

```bash
npm run dev
```

Open http://localhost:3000.

## 3. Start the API

In a second terminal:

```bash
cd apps/api
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell: .venv\\Scripts\\Activate.ps1
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

API health: http://localhost:8000/health  
API docs: http://localhost:8000/docs

## 4. Start local infrastructure (optional in this first UI sprint)

From the repository root:

```bash
docker compose up -d
```

PostgreSQL: localhost:5432  
Redis: localhost:6379

The Compose database password is for local development only. Change it before any shared or deployed environment.

## 5. Environment variables

Copy `.env.example` to `.env.local` for the frontend and configure backend environment variables separately when persistence is implemented. Never commit secrets.

## 6. GitHub setup

Create a new private repository named `my-outfit` on GitHub. Then, from this folder:

```bash
git init
git add .
git commit -m "chore: initialize My Outfit Phase 1"
git branch -M main
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/my-outfit.git
git push -u origin main
```

Replace `YOUR_GITHUB_USERNAME` with your GitHub username. Do not put access tokens in the remote URL.

## Suggested next implementation milestones

1. Replace the geometric placeholder with a licensed, rigged, inclusive base avatar (GLB).
2. Add Supabase Auth and user profile persistence.
3. Add avatar measurement schema and manual customization controls.
4. Add secure image upload with private storage and consent/retention controls.
5. Add asynchronous AI processing jobs and garment-analysis pipeline.

## Product and privacy principles

- Keep source photographs separate from generated avatar assets.
- Make photo-based scanning optional and provide manual measurement correction.
- Require explicit consent before processing body images.
- Store private uploads in non-public storage and authorize every access.
- Do not use user photos for model training without separate explicit consent.
- Review commercial licenses for every avatar base model, AI model, checkpoint and asset before production use.
# my-outfit
