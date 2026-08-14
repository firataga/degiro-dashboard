# DEGIRO Portfolio Dashboard - Complete Setup Guide

## 📦 Project Overview

**DEGIRO Portfolio Dashboard Online** — Een volledige online portfolio analyzer voor DEGIRO gebruikers met cloud sync.

### Features
- ✅ Firebase Authentication (login/register)
- ✅ Complete v4 Dashboard (risk analysis, watchlist, transactions, etc.)
- ✅ CSV Upload (Portfolio, Transactions, Account)
- ✅ Cloud Storage (Firebase Realtime Database)
- ✅ Auto Token Refresh (persistent sessions)
- ✅ Responsive Design (Desktop + Mobile)

---

## 🔧 Current Setup

### Files
- **DEGIRO_FINAL.html** — Main app (3300+ lines, all-in-one)
- **DEGIRO_v4_FINAL.html** — Offline version (backup)

### Firebase Project
- **Project ID:** degiro-portfolio-ff862
- **API Key:** AIzaSyCgVFnSKnqqqeXJWXEbcgvLW7ctNTYT_cc
- **Auth Domain:** degiro-portfolio-ff862.firebaseapp.com
- **Database URL:** https://degiro-portfolio-ff862-default-rtdb.europe-west1.firebasedatabase.app

### Current Deployment
- **Host:** Netlify
- **URL:** https://lovely-stardust-e80a04.netlify.app
- **User:** firataga@gmail.com

---

## 📋 How It Works

### User Flow
1. **Login Screen** → User logs in with email/password
2. **Auto Load** → Firebase token refreshes, cloud data loads
3. **Dashboard** → Shows portfolio if data exists
4. **Upload CSV** → Click "Nieuwe CSV uploaden" button
5. **Save** → Data synced to Firebase (persistent)
6. **Next Login** → Dashboard loads automatically

### Technical Flow
```
Login → Firebase Auth → Generate Token + Refresh Token
                ↓
         Store in localStorage
                ↓
         Load Cloud Data (if exists)
                ↓
         Build Dashboard with CSV data
                ↓
         Token Expires → Auto Refresh
                ↓
         Retry Cloud Load (seamless)
```

---

## 🚀 Deployment Instructions

### Option 1: Netlify (Current)
1. Go to netlify.com
2. Drag & drop **DEGIRO_FINAL.html**
3. Done! (instant deploy)

### Option 2: AntiGravity
1. Upload **DEGIRO_FINAL.html** to AntiGravity
2. No build process needed (it's a single HTML file)
3. Can be deployed as-is

### Option 3: Self-Hosted
1. Put DEGIRO_FINAL.html on any web server
2. Enable HTTPS (required for Firebase)
3. CORS should work (Firebase handles it)

---

## 🔐 Firebase Configuration

### Current Auth Rules
- Users can only read/write their own data
- Email/password authentication enabled
- No admin panel needed

### Database Structure
```
users/
  {uid}/
    portfolio.json
      - files: { portfolio, transactions, account }
      - timestamp: (ms since epoch)
```

### Important
- ⚠️ API Key is in HTML (acceptable for frontend)
- ✅ Database has security rules (data isolated per user)
- ✅ Token refreshes automatically

---

## 📝 User Guide

### First Time Setup
1. Go to app
2. Click "Geen account? Registreer"
3. Enter email + password
4. Click "Account maken"
5. Now logged in!

### Upload Data
1. Click "Nieuwe CSV uploaden" (sidebar)
2. Select 3 files (Portfolio.csv, Transactions.csv, Account.csv)
3. Click "Dashboard openen"
4. Data saved to cloud!

### Next Login
1. Open app
2. Login with same email/password
3. Dashboard loads automatically
4. Data is there! 

---

## 🐛 Troubleshooting

### "No cloud data"
- Normal on first login (no CSV uploaded yet)
- Upload CSV to fix

### "Token expired"
- Auto-refreshes in background
- If keeps failing, clear browser cache and re-login

### "401 Unauthorized"
- Token refresh issue
- Solution: Clear localStorage and login again

### CSV Upload Not Working
- Ensure file names contain "portfolio", "transaction", "account"
- Must be valid CSV format (comma-separated)

---

## 📊 Data That Gets Stored

### In Browser (localStorage)
```json
{
  "firebaseAuth": {
    "user": { "uid": "...", "email": "..." },
    "idToken": "...",
    "refreshToken": "...",
    "expiresIn": "3600"
  }
}
```

### In Firebase Cloud
```json
{
  "files": {
    "portfolio": "CSV content...",
    "transactions": "CSV content...",
    "account": "CSV content..."
  },
  "timestamp": 1234567890
}
```

---

## 🔄 Key Functions (DEGIRO_FINAL.html)

### Auth Functions
- `firebaseLogin()` — Login with email/password
- `firebaseRegister()` — Create account
- `refreshFirebaseToken()` — Auto-refresh token
- `firebaseLogout()` — Clear session

### Data Functions
- `loadCloudData()` — Load from Firebase
- `saveDataToCloud()` — Save CSV data
- `buildDashboard()` — Render UI (from v4)

### UI Functions
- `resetToUpload()` — Show upload screen
- `hideFirebaseAuth()` — Hide login overlay

---

## 📱 Browser Compatibility

- ✅ Chrome/Edge (latest)
- ✅ Safari (latest)
- ✅ Firefox (latest)
- ✅ Mobile browsers
- ⚠️ Requires HTTPS (for localStorage + Firebase)

---

## 🔗 Important Links

- Firebase Console: https://console.firebase.google.com
- Project: degiro-portfolio-ff862
- Netlify Deploy: https://lovely-stardust-e80a04.netlify.app
- GitHub (if needed): Can be pushed to repo

---

## 💡 Next Steps for AntiGravity

1. **Upload DEGIRO_FINAL.html** to your platform
2. **Test login/upload** with firataga@gmail.com
3. **Verify cloud sync** (check Firebase console)
4. **Optional:** Customize styling (modify CSS in HTML)
5. **Optional:** Add custom features (extend JavaScript)

---

## 📞 Support Notes

- No external dependencies (Chart.js from CDN)
- Single HTML file (no build process)
- Fully functional offline (except cloud sync)
- Token auto-refresh handles expiration

---

**Last Updated:** 25 June 2026
**Version:** DEGIRO Portfolio v202606231016 + Firebase
**Status:** Production Ready ✅
