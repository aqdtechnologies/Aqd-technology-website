# AQD Technology Website - Deployment Guide

## Deployment Strategy

This repository uses a multi-environment deployment strategy to keep your original website safe while managing Facebook and other deployments independently.

### Environment Setup

| Environment | Branch | Purpose | URL | Status |
|---|---|---|---|---|
| **Production** | `main` | Live original website | yoursite.com | ✅ Active |
| **Staging** | `staging` | Testing environment | staging.yoursite.com | ✅ Created |
| **Facebook** | `facebook-deploy` | Facebook-optimized version | facebook.yoursite.com | ✅ Created |
| **Development** | `develop` | Local development | localhost | 📋 Create as needed |

---

## ✅ What's Been Set Up

### 1. **facebook-deploy Branch** ✅
- Created from `main` branch
- Ready for Facebook-specific customizations
- Completely independent from original website
- URL: https://github.com/aqdtechnologies/Aqd-technology-website/tree/facebook-deploy

### 2. **staging Branch** ✅
- Created from `main` branch
- Safe testing environment
- Test new features before going to production
- URL: https://github.com/aqdtechnologies/Aqd-technology-website/tree/staging

### 3. **Deployment Workflow Strategy**
```
main (Production - Original Website)
  ↓
staging (Testing & Review)
  ↓
facebook-deploy (Facebook-Optimized Version)
```

---

## 📋 How to Use Each Branch

### **main** - Original Website (Production)
```bash
# ❌ NEVER edit directly
# Always create feature branches and PRs
git checkout main
git pull origin main
git checkout -b fix/improve-homepage
# Make changes
git push origin fix/improve-homepage
# Create PR → Review → Merge to main
```

### **staging** - Testing & Review
```bash
# Test new features here first
git checkout staging
git pull origin staging
git checkout -b feature/new-feature-test
# Make and test changes
git push origin feature/new-feature-test
# Create PR to staging → Review → Merge
# When ready, create PR from staging to main
```

### **facebook-deploy** - Facebook Version
```bash
# Customized for Facebook platform
git checkout facebook-deploy
git pull origin facebook-deploy
git checkout -b feature/facebook-optimization
# Make Facebook-specific changes
# Examples:
#   - Optimize images for Facebook dimensions
#   - Add Facebook sharing buttons
#   - Adjust layout for mobile/social viewing
git push origin feature/facebook-optimization
# Create PR to facebook-deploy → Review → Merge
```

---

## 🔄 Syncing Between Branches

### Keep Facebook version updated with main
```bash
git checkout facebook-deploy
git pull origin main
git push origin facebook-deploy
```

### Promote staging changes to production
```bash
# After testing in staging and confirming everything works:
git checkout main
git pull origin staging
git push origin main
```

---

## 📁 Current Content

Your website contains:
- **index.html** (7.7 KB) - Main homepage
- **welcome.html** (18.5 KB) - Welcome/intro page
- **licensing.html** (29.5 KB) - Licensing page
- **AQD_Technology_Licensing_Deck.pdf** (7.2 KB) - Licensing deck

---

## 🚀 Next Steps

### 1. **Customize Facebook Version**
Go to the `facebook-deploy` branch and customize:
- Add Facebook-specific branding
- Optimize images for Facebook's recommended dimensions
- Add Facebook sharing/meta tags
- Test on facebook.com

### 2. **Set Up Hosting/Deployment**
Choose your hosting provider and set up auto-deployment:
- **Vercel** (Recommended for static sites) - Free tier available
- **Netlify** - Easy GitHub integration
- **GitHub Pages** - Free and built-in
- **Heroku**, **AWS**, etc.

### 3. **Enable Branch Protection on main**
Settings → Branches → Add Rule for `main`:
- ✅ Require pull request reviews
- ✅ Require status checks to pass
- ✅ Require branches to be up to date

### 4. **Test Each Environment**
- Test `main` at yoursite.com
- Test `staging` at staging.yoursite.com
- Test `facebook-deploy` at facebook.yoursite.com

---

## 📊 Branch Comparison

| Feature | main | staging | facebook-deploy |
|---------|------|---------|-----------------|
| Production Ready | ✅ Yes | ❌ No | ✅ Yes (Facebook) |
| Can be edited directly | ❌ No | ✅ Yes | ✅ Yes |
| Gets deployed | ✅ Main site | ✅ Test site | ✅ Facebook site |
| Should have PRs | ✅ Always | ✅ Recommended | ✅ Recommended |
| Can sync from main | ❌ No | ✅ Yes | ✅ Yes |

---

## 💡 Example Workflow

### Scenario: Add new feature to main
```
1. Create branch: feature/new-feature from main
2. Make changes and commit
3. Push to origin
4. Create PR to staging first
5. Test in staging
6. If all good, create PR to main
7. Review and merge to main
8. Optionally merge main to facebook-deploy
```

### Scenario: Customize for Facebook
```
1. Create branch: facebook/custom-layout from facebook-deploy
2. Customize HTML/styling for Facebook
3. Add Facebook meta tags and sharing buttons
4. Test locally and in staging
5. Push and create PR to facebook-deploy
6. Review and merge
```

---

## 🔗 Branch URLs

- **main**: https://github.com/aqdtechnologies/Aqd-technology-website
- **staging**: https://github.com/aqdtechnologies/Aqd-technology-website/tree/staging
- **facebook-deploy**: https://github.com/aqdtechnologies/Aqd-technology-website/tree/facebook-deploy

---

## ❓ FAQ

**Q: Can I edit main directly?**
A: ❌ No, always create a feature branch and PR for safety.

**Q: How do I keep facebook-deploy updated?**
A: Pull changes from main into facebook-deploy when needed.

**Q: What if I break something in staging?**
A: Just revert the branch to main's version with: `git reset --hard origin/main`

**Q: Can I deploy multiple environments?**
A: ✅ Yes! Each branch can have its own deployment URL (main, staging, facebook-deploy).

---

## 📞 Support

For GitHub documentation:
- [GitHub Branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
- [Pull Requests](https://docs.github.com/en/pull-requests)
- [GitHub Actions](https://docs.github.com/en/actions)
