# ✅ Quick Deployment Checklist

Use this checklist to track your deployment progress.

---

## 📋 Frontend (Vercel) - `https://hackathon-app-pearl.vercel.app`

- [ ] **Code Pushed to GitHub**
  - Command: `git push origin main`
  - Check: https://github.com/your-username/hackathon-app

- [ ] **Vercel Deployment Running**
  - Go to: https://vercel.com/dashboard
  - Look for: `hackathon-app-pearl` project
  - Status should show: "Ready" (green checkmark)
  - If building: Wait 3-5 minutes for deployment to complete

- [ ] **Frontend Environment Variables Set**
  - In Vercel Dashboard → Settings → Environment Variables
  - Add: `VITE_API_URL = https://hackathon-api-m4rm.onrender.com`
  - Redeploy after adding

- [ ] **Test Frontend**
  ```powershell
  curl https://hackathon-app-pearl.vercel.app
  ```
  - Expected: HTTP 200 status + HTML content

---

## 🔧 Backend (Render) - `https://hackathon-api-m4rm.onrender.com`

- [ ] **Database Created (PostgreSQL)**
  - Service: PostgreSQL on Render or Railway
  - Copy: `DATABASE_URL` connection string
  - Keep safe: You'll need this next

- [ ] **Render Backend Service Deployed**
  - Go to: https://render.com/dashboard
  - Look for: `hackathon-api` service
  - Status should show: "Live" (green)
  - If deploying: Check "Logs" tab for progress

- [ ] **Backend Environment Variables Set** (in Render)
  ```
  DATABASE_URL = postgresql://user:password@host/db
  JWT_SECRET = your-secret-key-here-minimum-32-characters
  CLOUDINARY_CLOUD_NAME = your-value
  CLOUDINARY_API_KEY = your-value
  CLOUDINARY_API_SECRET = your-value
  ALLOWED_ORIGINS = https://hackathon-app-pearl.vercel.app
  NODE_ENV = production
  ```

- [ ] **Test Backend API**
  ```powershell
  curl https://hackathon-api-m4rm.onrender.com/api/hackathons
  ```
  - Expected: JSON response with hackathons array (or empty array if no data)

---

## 🔗 Connect Frontend to Backend

- [ ] **Update Vercel Environment Variable**
  - In Vercel Dashboard → Settings → Environment Variables
  - Key: `VITE_API_URL`
  - Value: `https://hackathon-api-m4rm.onrender.com`
  - Click "Save"

- [ ] **Redeploy Frontend**
  - In Vercel Dashboard → Deployments tab
  - Click "..." on latest deployment
  - Select "Redeploy"
  - Wait for deployment to complete

---

## 🧪 Full End-to-End Testing

- [ ] **Open Frontend in Browser**
  - Go to: https://hackathon-app-pearl.vercel.app
  - Should load without errors
  - Check browser console (F12) for any errors

- [ ] **Test Login**
  - Try logging in with test credentials
  - Check network tab (F12) → should see API calls to backend

- [ ] **Test API Connection**
  - Go to: https://hackathon-api-m4rm.onrender.com/api/hackathons
  - Should return JSON data

- [ ] **Test Database Connection**
  - Create a hackathon in the app
  - Refresh page
  - Data should persist (proves database is connected)

- [ ] **Test File Uploads** (if applicable)
  - Upload an image/document
  - Should upload to Cloudinary successfully

---

## 🐛 If Something Doesn't Work

### Frontend shows "DEPLOYMENT_NOT_FOUND"
**Fix**: Wait 5 minutes for Vercel to finish building, then refresh

### Frontend shows "Failed to fetch" when logging in
**Fix**: 
1. Check `VITE_API_URL` is set correctly in Vercel env vars
2. Verify backend is running: https://hackathon-api-m4rm.onrender.com/api/hackathons
3. Check CORS: Backend's `ALLOWED_ORIGINS` includes your frontend URL

### Backend returns 503 error
**Fix**: 
1. Check Render service status in dashboard
2. View logs to see error messages
3. Verify DATABASE_URL is set and PostgreSQL is running

### Database connection error
**Fix**:
1. Verify DATABASE_URL is correct in Render env vars
2. Check PostgreSQL instance is running
3. Try connecting locally first to test DATABASE_URL

---

## 📞 Quick Links

- **Vercel Dashboard**: https://vercel.com/dashboard
- **Render Dashboard**: https://render.com/dashboard
- **Your Frontend**: https://hackathon-app-pearl.vercel.app
- **Your Backend**: https://hackathon-api-m4rm.onrender.com
- **GitHub Repo**: https://github.com/your-username/hackathon-app

---

## ✨ Success Criteria

All of these should be true when fully deployed:

✅ Frontend loads at https://hackathon-app-pearl.vercel.app  
✅ Backend responds at https://hackathon-api-m4rm.onrender.com/api/hackathons  
✅ Frontend can make API calls to backend without CORS errors  
✅ Database stores and retrieves data correctly  
✅ Users can login, create hackathons, and upload files  

**When all are checked, your app is LIVE! 🎉**

---

## 🔄 Next Steps After Deployment

1. **Monitor** - Check logs regularly for errors
2. **Backup** - Set up automatic database backups
3. **Custom Domain** - Point your own domain to Vercel/Render
4. **Analytics** - Set up error tracking (Sentry, LogRocket)
5. **Performance** - Monitor response times and optimize
6. **Updates** - Use Git + CD to deploy new features

---

**Status**: In Progress  
**Last Updated**: December 17, 2025
