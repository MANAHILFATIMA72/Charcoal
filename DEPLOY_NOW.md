# CHARCOAL CLOTHING - DEPLOYMENT GUIDE

## ✅ ISSUES FIXED
- ❌ Removed incorrect environment variable syntax from vercel.json
- ✅ Added build script to package.json
- ✅ Server tested and working locally
- ✅ All dependencies installed (14 packages)

---

## 🚀 DEPLOYMENT STEPS (SIMPLE 5 STEPS)

### STEP 1: Make Sure You Have These Ready
```
1. MongoDB Atlas connection string (starts with mongodb+srv://)
2. Two random secret strings (for JWT and Session)
```

If you need to generate secrets, run:
```bash
openssl rand -base64 32
```

---

### STEP 2: Push Code to GitHub

```bash
git push origin main
```

---

### STEP 3: Go to Vercel Dashboard

1. Open https://vercel.com/dashboard
2. Click **"New Project"**
3. Select your GitHub repo: **MANAHILFATIMA72/Charcoal**
4. Click **"Import"**

---

### STEP 4: Add Environment Variables (IMPORTANT!)

In the Vercel import screen, scroll down to **"Environment Variables"** section.

Add these 3 variables:

| Variable | Value |
|----------|-------|
| `MONGODB_URI` | `mongodb+srv://Manahil:Manahil123@charcoal.12rulvd.mongodb.net/?appName=Charcoal` |
| `JWT_SECRET` | [Use generated secret from Step 1] |
| `SESSION_SECRET` | [Use generated secret from Step 1] |

Example:
```
MONGODB_URI = mongodb+srv://Manahil:Manahil123@charcoal.12rulvd.mongodb.net/?appName=Charcoal
JWT_SECRET = a7K9mP2xL5wQ8vN1bR4cD6eF9gH2jM5pS8tU1xY4zB7cE9fG2hJ5kM8nP1qR4sT7uV
SESSION_SECRET = xY7K2mP5wL9vN3bR8cD1eF4gH7jM2pS6tU9xY1zB4cE6fG9hJ1kM4nP7qR2sT5uV
```

---

### STEP 5: Deploy!

1. Click **"Deploy"** button
2. Wait 2-3 minutes for build
3. You should see a green checkmark when done
4. Click the preview URL to test your site

---

## ✅ VERIFICATION CHECKLIST

After deployment, check:

- [ ] Site loads without errors
- [ ] Can access homepage
- [ ] Can navigate between pages
- [ ] Database connection works
- [ ] Can sign up / login
- [ ] No red errors in browser console (F12 key)

---

## 🔧 TROUBLESHOOTING

### Build Failed?
1. Check build logs in Vercel dashboard
2. Common issues:
   - Wrong MONGODB_URI format
   - Missing environment variables
   - Typo in variable names

### Can't Connect to MongoDB?
1. Verify MONGODB_URI is correct
2. Check MongoDB Atlas whitelist: https://cloud.mongodb.com/
   - Go to Network Access
   - Whitelist IP: `0.0.0.0/0` (allows Vercel)
3. Verify password doesn't have special characters that need URL encoding

### Pages Not Loading?
1. Open browser console (F12)
2. Check for errors
3. Wait 1-2 minutes for Vercel to fully deploy
4. Refresh page (Ctrl+F5)

---

## 📊 PROJECT STATUS

```
Framework:     Express.js
Database:      MongoDB Atlas
Deployment:    Vercel (Node.js)
Status:        READY TO DEPLOY ✅
```

---

## 🎯 QUICK REFERENCE

| What | Where |
|------|-------|
| GitHub Repo | MANAHILFATIMA72/Charcoal |
| Vercel Dashboard | vercel.com/dashboard |
| MongoDB Atlas | cloud.mongodb.com |
| Entry Point | server.js |
| Build Tool | @vercel/node |

---

## ✨ NEXT STEPS AFTER DEPLOYMENT

1. **Test your site** - Visit the preview URL
2. **Custom domain** - (Optional) Add your domain in Vercel settings
3. **Monitor** - Check Vercel dashboard for errors

---

**You're ready to deploy! Start with Step 2 above.** 🎉
