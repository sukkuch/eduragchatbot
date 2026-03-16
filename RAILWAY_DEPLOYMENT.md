# Railway Deployment Guide

## Prerequisites
1. Create a [Railway.app](https://railway.app) account
2. Your project should be pushed to GitHub (✅ Already done)

## Deployment Steps

### Option 1: Deploy via Railway Web Dashboard (Recommended)

1. **Go to Railway.app** and sign in
2. **Create a new project**
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Authorize Railway to access your GitHub account
   - Select the `eduragchatbot` repository

3. **Configure Services**
   - Railway will auto-detect the project structure
   - Add environment variables for the backend:
     - Go to Variables tab
     - Add:
       ```
       DEV_USERNAME=admin
       DEV_PASSWORD=your_password
       FRONTEND_URL=https://your-frontend-railway-url.railway.app
       ```

4. **Deploy Backend and Frontend**
   - Railway will automatically build and deploy both services
   - Check the deployment logs in the dashboard

### Option 2: Deploy via CLI (If tools are installed)

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login to Railway
railway login

# Initialize the project
railroad link

# Deploy
railway up
```

## Environment Variables to Set

Set these in the Railway dashboard under your backend service's Variables:

```
DEV_USERNAME=admin
DEV_PASSWORD=your_secure_password
FRONTEND_URL=<your_frontend_railway_url>
PORT=8000
```

For frontend, set:
```
VITE_API_URL=<your_backend_railway_url>
```

## Useful Railway Commands

- View logs: `railway logs`
- View status: `railway status`
- Open dashboard: `railway open`
- View environment: `railway variables`

## Troubleshooting

### Backend deployment fails
- Check if all dependencies in `backend/requirements.txt` are installed correctly
- Verify environment variables are set
- Check Railway build logs in the dashboard

### Frontend not connecting to backend
- Ensure `FRONTEND_URL` is set correctly in backend environment
- Update `VITE_API_URL` in frontend environment variables
- Check CORS settings in `backend/main.py`

### Port issues
- Railway automatically assigns ports
- Your services will be available at `https://your-service-name-<random>.railway.app`

## Verify Deployment

Once deployed:
1. Visit your backend at `https://your-backend-service.railway.app`
2. Visit your frontend at `https://your-frontend-service.railway.app`
3. Test the API with: `/docs` endpoint (FastAPI Swagger UI)

## Next Steps

- Monitor your applications in the Railway dashboard
- Set up custom domains if needed
- Configure auto-redeployment on GitHub push
- Set up monitoring and alerts
