# Deployment Guide

## Railway Deployment

This project is configured to deploy on Railway. Follow these steps:

### 1. Prerequisites
- GitHub repository (already set up ✓)
- Railway account (sign up at https://railway.app)

### 2. Deploy to Railway

#### Option A: Via Railway Dashboard
1. Go to https://railway.app/new
2. Click "Deploy from GitHub repo"
3. Select your `cyberchris.github.io` repository
4. Railway will automatically detect the configuration from `railway.json` and `nixpacks.toml`
5. Add environment variables if needed (e.g., database URLs, API keys)
6. Click "Deploy"

#### Option B: Via Railway CLI
```bash
# Install Railway CLI
npm i -g @railway/cli

# Login to Railway
railway login

# Link to your project (or create new)
railway link

# Deploy
railway up
```

### 3. Environment Variables

Make sure to set these in Railway:
- `NODE_ENV=production`
- Any database connection strings
- API keys and secrets
- `PORT` (Railway sets this automatically)

### 4. Database Setup

If using a database, add it in Railway:
1. In your Railway project, click "+ New"
2. Select "Database" → Choose your database type
3. Railway will automatically set environment variables
4. Run migrations: `railway run pnpm run db:push`

## Build Configuration

The project uses:
- **Build command**: `pnpm run build` (builds both frontend and backend)
- **Start command**: `pnpm run start` (runs production server)
- **Node version**: 20.x
- **Package manager**: pnpm

## Troubleshooting

### Build fails
- Check that all dependencies are in `package.json`
- Verify build script works locally: `pnpm run build`

### Server won't start
- Check environment variables are set correctly
- View Railway logs for error messages
- Ensure `PORT` environment variable is used (Railway auto-assigns)

### Database connection issues
- Verify database environment variables
- Check if migrations ran successfully
- Ensure database is in the same Railway project
