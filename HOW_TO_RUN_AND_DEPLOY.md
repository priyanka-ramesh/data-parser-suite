# How to Run & Deploy - Advanced Data Parser Studio

Complete step-by-step guide for running locally and deploying to production.

---

## 📋 Table of Contents
1. [How to Run Locally](#how-to-run-locally)
2. [How to Deploy](#how-to-deploy)
3. [Troubleshooting](#troubleshooting)
4. [Environment Setup](#environment-setup)

---

## 🚀 How to Run Locally

### Step 1: Prerequisites Check

Before you start, make sure you have:

```bash
# Check Node.js version (should be 16 or higher)
node --version
# Output should be: v16.0.0 or higher

# Check npm version (should be 7 or higher)
npm --version
# Output should be: 7.0.0 or higher
```

**Don't have Node.js?**
- Download from: https://nodejs.org/ (LTS version recommended)
- Install it and restart your terminal

### Step 2: Download & Extract the Project

**Option A: From GitHub (Recommended)**
```bash
# Clone the repository
git clone https://github.com/yourusername/advanced-data-parser.git

# Navigate into the project
cd advanced-data-parser
```

**Option B: From ZIP file**
```bash
# Extract the ZIP file
unzip data-parser-studio.zip

# Navigate into the project
cd data-parser-studio
```

### Step 3: Install Dependencies

```bash
# Install all required packages
npm install

# This will take 2-3 minutes
# You'll see lots of packages being installed - this is normal!
```

**What's being installed?**
- React 19 - UI framework
- TypeScript - Type checking
- Vite - Build tool
- Lucide React - Icons
- Other development tools

### Step 4: Start Development Server

```bash
# Start the development server
npm run dev

# Output should show:
# ➜  Local:   http://localhost:3000/
# ➜  press h + enter to show help
```

### Step 5: Open in Browser

1. **Automatically opens** - The app should open in your default browser
2. **Manual open** - If not, go to: http://localhost:3000

### Step 6: Test the Features

✅ **Test URL Loading:**
1. Click "🔗 URL" tab
2. Paste: `https://api.github.com/users/github`
3. Click "Fetch"
4. See the tree view with expandable nodes
5. Type in search box to test search

✅ **Test File Upload:**
1. Click "📁 Upload" tab
2. Download a JSON file from https://sample-files.com/data/json/
3. Drag the file onto the upload zone
4. See it auto-load
5. Tree view appears instantly

✅ **Test Paste:**
1. Click "📋 Paste" tab
2. Copy this JSON:
```json
{
  "user": {
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30
  }
}
```
3. Paste it in the textarea
4. Click "Parse Data"
5. See tree view

✅ **Test Search:**
1. With any data parsed
2. In Tree view, find the search box
3. Type "name" or any value
4. Watch results filter in real-time

✅ **Test Export:**
1. Parse any JSON
2. Click "Table" view
3. Select "CSV" export
4. Click "Download CSV"
5. File downloads as `data-YYYYMMDD-HHMMSS.csv`

### Step 7: Stop the Development Server

```bash
# In your terminal, press:
Ctrl + C

# Or in PowerShell on Windows:
Ctrl + C
```

---

## 🌐 How to Deploy

Choose your preferred deployment platform:

### **OPTION 1: Vercel (EASIEST & RECOMMENDED) ⭐**

**Why Vercel?**
- ✅ Fastest to deploy (1 command)
- ✅ Free tier available
- ✅ Auto-deploys on GitHub push
- ✅ Custom domain support
- ✅ Best performance for React apps

#### Step 1: Create Vercel Account
```
1. Go to: https://vercel.com
2. Sign up with GitHub (recommended)
3. Authorize Vercel
```

#### Step 2: Deploy Your Project

**If you pushed to GitHub:**
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy to Vercel
vercel --prod

# Follow the prompts:
# - Select "y" for all questions
# - Link to GitHub repo (optional but recommended)
```

**Output:**
```
✓ Deployed to advanced-data-parser.vercel.app
✓ Your live site is ready
```

#### Step 3: Access Your App
- Your app is now live at: `https://advanced-data-parser.vercel.app`
- Share this link with anyone!

#### Optional: Custom Domain
1. Go to Vercel dashboard
2. Select your project
3. Go to Settings → Domains
4. Add your custom domain
5. Follow DNS setup instructions

---

### **OPTION 2: Netlify**

**Why Netlify?**
- ✅ Easy GitHub integration
- ✅ Free SSL/HTTPS
- ✅ Form handling
- ✅ Good performance

#### Step 1: Push to GitHub

```bash
# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: Advanced Data Parser"

# Create repository on GitHub
# Then push:
git remote add origin https://github.com/yourusername/advanced-data-parser.git
git branch -M main
git push -u origin main
```

#### Step 2: Connect to Netlify

1. Go to: https://app.netlify.com
2. Click "New site from Git"
3. Choose GitHub
4. Select your repository
5. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy"

#### Step 3: Done!
- Your site is live at: `https://your-site-name.netlify.app`
- Every push to GitHub auto-deploys

---

### **OPTION 3: GitHub Pages**

**Why GitHub Pages?**
- ✅ Free hosting
- ✅ Integrated with GitHub
- ✅ Simple setup
- ✅ Good for portfolios

#### Step 1: Build for Production

```bash
# Build the project
npm run build

# This creates a 'dist' folder with everything ready
```

#### Step 2: Push dist to gh-pages Branch

```bash
# Method 1: Using npm package (EASIEST)
npm install --save-dev gh-pages

# Add to package.json scripts:
# "deploy": "npm run build && gh-pages -d dist"

# Then run:
npm run deploy
```

**OR Method 2: Manual upload**
```bash
# Create gh-pages branch
git checkout --orphan gh-pages

# Copy dist files
cp -r dist/* .

# Commit and push
git add .
git commit -m "Deploy to GitHub Pages"
git push origin gh-pages
```

#### Step 3: Enable GitHub Pages

1. Go to your GitHub repository
2. Settings → Pages
3. Select "Deploy from a branch"
4. Choose "gh-pages" branch
5. Click Save

#### Step 4: Access Your Site
- Your site is live at: `https://yourusername.github.io/advanced-data-parser`

---

### **OPTION 4: Firebase Hosting**

**Why Firebase?**
- ✅ Google's platform
- ✅ Good for production
- ✅ Real-time database option
- ✅ Analytics included

#### Step 1: Install Firebase CLI

```bash
npm install -g firebase-tools

# Login to Firebase
firebase login
```

#### Step 2: Initialize Firebase

```bash
# In your project directory
firebase init hosting

# When asked:
# - Select a Firebase project (create new if needed)
# - Public directory: dist
# - Configure rewrite: y (for React routing)
# - Overwrite dist/index.html: n
```

#### Step 3: Build & Deploy

```bash
# Build
npm run build

# Deploy
firebase deploy

# Your site URL will be shown
```

---

### **OPTION 5: AWS S3 + CloudFront**

**Why AWS?**
- ✅ Enterprise-grade
- ✅ Highly scalable
- ✅ CDN included
- ✅ Custom domain easy

#### Step 1: Build

```bash
npm run build
```

#### Step 2: Create S3 Bucket

1. Go to AWS Console → S3
2. Create bucket (name: your-app-name)
3. Enable static website hosting
4. Upload contents of `dist/` folder

#### Step 3: Create CloudFront Distribution

1. Go to CloudFront
2. Create distribution
3. Select your S3 bucket
4. Configure settings
5. Deploy

#### Step 4: Access Your Site

- Your site is live at CloudFront URL

---

## 📋 Deployment Comparison

| Platform | Cost | Difficulty | Speed | Build Time | Custom Domain |
|----------|------|-----------|-------|-----------|----------------|
| **Vercel** | Free | ⭐ Easiest | ⭐⭐⭐ Fastest | 2-3 min | ✅ Yes |
| **Netlify** | Free | ⭐⭐ Easy | ⭐⭐⭐ Fast | 2-3 min | ✅ Yes |
| **GitHub Pages** | Free | ⭐⭐ Easy | ⭐⭐ Good | 2-3 min | ✅ Yes |
| **Firebase** | Free tier | ⭐⭐⭐ Medium | ⭐⭐⭐ Fast | 2-3 min | ✅ Yes |
| **AWS** | Paid | ⭐⭐⭐⭐ Hard | ⭐⭐⭐⭐ Best | 5-10 min | ✅ Yes |

**Recommendation:** Start with **Vercel** or **Netlify** - they're easiest and have free tiers!

---

## 🛠️ Environment Setup

### Complete Setup from Scratch

#### Windows Users:

```bash
# 1. Install Node.js (download from nodejs.org)
# 2. Open PowerShell and verify installation
node --version
npm --version

# 3. Clone project
git clone https://github.com/yourusername/advanced-data-parser.git
cd advanced-data-parser

# 4. Install dependencies
npm install

# 5. Run development server
npm run dev

# 6. Open http://localhost:3000 in browser
```

#### Mac Users:

```bash
# 1. Install Node.js via Homebrew (if not installed)
brew install node

# 2. Verify installation
node --version
npm --version

# 3. Clone project
git clone https://github.com/yourusername/advanced-data-parser.git
cd advanced-data-parser

# 4. Install dependencies
npm install

# 5. Run development server
npm run dev

# 6. Open http://localhost:3000 in browser
```

#### Linux Users:

```bash
# 1. Install Node.js
sudo apt-get update
sudo apt-get install nodejs npm

# 2. Verify installation
node --version
npm --version

# 3. Clone project
git clone https://github.com/yourusername/advanced-data-parser.git
cd advanced-data-parser

# 4. Install dependencies
npm install

# 5. Run development server
npm run dev

# 6. Open http://localhost:3000 in browser
```

---

## 🔧 Available Commands

```bash
# Development server (with hot reload)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Format code (if using Prettier)
npm run format

# Lint code (if using ESLint)
npm run lint

# Type check
npx tsc --noEmit
```

---

## 📊 Build Output Explanation

When you run `npm run build`, you'll see:

```
✓ 1234 modules transformed.
dist/index.html                    0.45 kB
dist/assets/index-abc123.js        125.43 kB
dist/assets/index-abc123.css       12.34 kB

✓ built in 3.21s
```

What this means:
- ✅ Build successful
- ✅ 3 files created
- ✅ Total size: ~138 KB (very optimized!)
- ✅ Ready to deploy

---

## 🚨 Troubleshooting

### Problem: "npm: command not found"

**Solution:** Install Node.js
```bash
# Download from https://nodejs.org/
# Install and restart terminal
node --version
```

### Problem: Port 3000 Already in Use

**Solution:**
```bash
# Use different port
npm run dev -- --port 3001

# Or kill process on port 3000
# Windows:
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# Mac/Linux:
lsof -ti:3000 | xargs kill -9
```

### Problem: "Module not found" Error

**Solution:**
```bash
# Clear node_modules and reinstall
rm -rf node_modules
npm install
npm run dev
```

### Problem: Build Fails

**Solution:**
```bash
# Check TypeScript errors
npx tsc --noEmit

# Check Node version
node --version

# Rebuild
rm -rf dist
npm run build
```

### Problem: CORS Error in Production

**Solution:**
- Check "Use CORS proxy" checkbox in URL tab
- Or use the provided CORS proxy service
- Contact server admin if self-hosted

### Problem: Large Files Not Loading

**Solution:**
- Max file size is 50MB
- For larger files, split them first
- Or use cloud storage + URL loading

---

## 📝 Deployment Checklist

Before deploying, verify:

- [ ] All features tested locally (`npm run dev`)
- [ ] No console errors (check browser DevTools)
- [ ] Builds successfully (`npm run build`)
- [ ] dist/ folder created and has files
- [ ] Git repository up to date
- [ ] GitHub account ready
- [ ] Vercel/Netlify/other account ready

---

## 🎯 Quick Deployment Commands

### Vercel (Fastest)
```bash
npm install -g vercel
vercel --prod
```

### Netlify (via Git)
```bash
git push origin main
# Auto-deploys to Netlify
```

### GitHub Pages
```bash
npm run build
npm run deploy
```

---

## 📱 Testing Deployed Site

After deployment, test:

1. ✅ **Load page** - Site loads at deployment URL
2. ✅ **URL tab** - Can fetch from https://api.github.com/users/github
3. ✅ **Upload tab** - Can upload JSON files
4. ✅ **Paste tab** - Can paste and parse data
5. ✅ **Tree view** - Nodes expand/collapse
6. ✅ **Search** - Search works instantly
7. ✅ **Export** - Can download CSV/JSON
8. ✅ **Mobile** - Works on mobile devices

---

## 🔗 Useful Links

**Deploy Platforms:**
- Vercel: https://vercel.com
- Netlify: https://netlify.com
- GitHub Pages: https://pages.github.com
- Firebase: https://firebase.google.com
- AWS: https://aws.amazon.com

**Node.js:**
- Download: https://nodejs.org/
- Documentation: https://nodejs.org/en/docs/

**Git:**
- Download: https://git-scm.com/
- Documentation: https://git-scm.com/doc

**Test Data:**
- Sample JSON: https://sample-files.com/data/json/
- Sample XML: https://sample-files.com/data/xml/
- GitHub API: https://api.github.com/

---

## 💡 Pro Tips

1. **Development** - Always use `npm run dev` for coding
2. **Testing** - Test with `npm run preview` before deploying
3. **Deployment** - Start with Vercel (easiest)
4. **Updates** - Push to GitHub, let CI/CD handle deployment
5. **Monitoring** - Each platform has logs/analytics dashboard
6. **Backups** - Keep git repository up to date

---

## ✅ You're Ready!

You now know how to:
- ✅ Run the app locally
- ✅ Deploy to Vercel
- ✅ Deploy to Netlify
- ✅ Deploy to GitHub Pages
- ✅ Deploy to Firebase
- ✅ Deploy to AWS
- ✅ Troubleshoot common issues

**Next Step:** Choose your platform and deploy! 🚀

---

## 📞 Need Help?

- Check the logs in your deployment platform
- Review browser console (F12) for errors
- Check repository issues
- Review documentation files

**Happy deploying!** 🎉

---

**Last Updated:** September 2026
**Status:** All deployment methods tested and verified ✅
