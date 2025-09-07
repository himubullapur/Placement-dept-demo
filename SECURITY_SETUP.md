# 🔒 Security Setup for GitHub Hosting

## Current Setup
Your Firebase API keys are now in a separate `config.js` file that should be added to `.gitignore`.

## Steps to Secure Your API Keys

### 1. Add config.js to .gitignore
Make sure `config.js` is in your `.gitignore` file (already created).

### 2. For GitHub Pages Deployment

#### Option A: Use GitHub Secrets (Recommended)
1. Go to your GitHub repository
2. Click on **Settings** → **Secrets and variables** → **Actions**
3. Add these repository secrets:
   - `FIREBASE_API_KEY`
   - `FIREBASE_AUTH_DOMAIN`
   - `FIREBASE_DATABASE_URL`
   - `FIREBASE_PROJECT_ID`
   - `FIREBASE_STORAGE_BUCKET`
   - `FIREBASE_MESSAGING_SENDER_ID`
   - `FIREBASE_APP_ID`
   - `FIREBASE_MEASUREMENT_ID`

#### Option B: Use Environment Variables in GitHub Pages
1. Create a GitHub Action workflow file (`.github/workflows/deploy.yml`)
2. Use the secrets in your deployment process

### 3. For Local Development
1. Copy `config.js` to `config.local.js`
2. Update your local `config.local.js` with your actual API keys
3. Add `config.local.js` to `.gitignore`
4. Update `index.html` to use `config.local.js` for local development

### 4. Firebase Security Rules
Make sure your Firebase Realtime Database has proper security rules:

```json
{
  "rules": {
    "placementPortalData": {
      ".read": true,
      ".write": true
    }
  }
}
```

### 5. Alternative: Use Firebase Hosting
Consider using Firebase Hosting instead of GitHub Pages for better integration with Firebase services.

## Important Notes
- ⚠️ **Never commit API keys to version control**
- ✅ **Always use environment variables for production**
- 🔄 **Rotate API keys regularly**
- 📝 **Monitor Firebase usage for unusual activity**

## Current Files
- `config.js` - Contains your Firebase configuration (add to .gitignore)
- `.gitignore` - Prevents sensitive files from being committed
- `SECURITY_SETUP.md` - This security guide
