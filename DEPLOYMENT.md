# Charcoal Clothing - Vercel Deployment Guide

## Overview
This is an Express.js + MongoDB application configured for deployment on Vercel.

## Project Structure
- `server.js` - Main server entry point
- `routes/` - API and page routes
- `models/` - Mongoose database schemas
- `middleware/` - Express middleware functions
- `controllers/` - Route controllers
- `views/` - EJS template files
- `public/` - Static assets

## Prerequisites
- Node.js 18+ 
- MongoDB Atlas account (or any MongoDB instance)
- Vercel account

## Local Development

### 1. Setup Environment Variables
```bash
cp .env.example .env
```

Edit `.env` with your configuration:
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/?appName=Charcoal
JWT_SECRET=your_jwt_secret_key_here
SESSION_SECRET=your_session_secret_key_here
PORT=3000
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Run Development Server
```bash
npm run dev
```

The application will run on `http://localhost:3000`

## Deployment to Vercel

### 1. Push Code to GitHub
```bash
git add .
git commit -m "Prepare for Vercel deployment"
git push origin main
```

### 2. Connect to Vercel
- Go to [vercel.com](https://vercel.com)
- Click "New Project"
- Select your GitHub repository
- Click "Import"

### 3. Configure Environment Variables in Vercel
In Vercel Project Settings → Environment Variables, add:

```
MONGODB_URI = mongodb+srv://username:password@cluster.mongodb.net/?appName=Charcoal
JWT_SECRET = your_jwt_secret_key_here
SESSION_SECRET = your_session_secret_key_here
```

**Important:** Never commit `.env` file to GitHub. These values must be set in Vercel's dashboard only.

### 4. Deploy
- Vercel will automatically deploy when you push to `main`
- Or click "Deploy" in the Vercel dashboard

### 5. Monitor Deployment
- Check deployment logs in Vercel dashboard
- Verify all routes are working
- Monitor database connections

## Vercel Configuration

The `vercel.json` file handles:
- Build process using `@vercel/node`
- Server routes to `server.js`
- Environment variable mapping

## Troubleshooting

### MongoDB Connection Issues
- Verify MONGODB_URI is correct in Vercel Environment Variables
- Add Vercel IP to MongoDB Atlas whitelist (0.0.0.0/0 for development)

### Port Issues
- Vercel automatically assigns PORT via environment variable
- Server is configured to listen on `0.0.0.0:PORT`

### Static Files Not Loading
- Ensure `public/` directory is included in deployment
- Check that static routes are properly configured

## Production Best Practices

1. **Security**
   - Use strong JWT_SECRET and SESSION_SECRET
   - Enable MongoDB Atlas IP whitelist
   - Use HTTPS only (Vercel provides this automatically)

2. **Monitoring**
   - Set up error logging (Sentry, etc.)
   - Monitor database performance
   - Track API response times

3. **Scalability**
   - Consider MongoDB Atlas connection pooling
   - Implement caching strategies
   - Optimize database queries

## Additional Resources
- [Vercel Node.js Deployment](https://vercel.com/docs/concepts/nodejs)
- [Express.js Documentation](https://expressjs.com/)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
