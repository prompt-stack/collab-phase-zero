# Quick Start Guide
## Co-Llab Group - Mini Site Tool

**Get up and running in 10 minutes.**

---

## Step 1: Get Your Formspree ID (3 minutes)

1. Go to **https://formspree.io**
2. Click **"Get Started"** (or **"Sign Up"**)
3. Create a free account (email + password)
4. Click **"+ New Form"**
5. Name it: `"Co-Llab Mini Site"`
6. Copy the **Form ID** (looks like `xyzabc123`)

---

## Step 2: Configure the App (1 minute)

1. Open `index.html` in a text editor
2. Find line 158:
   ```html
   <form id="intakeForm" action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">
   ```
3. Replace `YOUR_FORMSPREE_ID` with your actual ID
4. Save the file

**Example:**
```html
<!-- BEFORE -->
action="https://formspree.io/f/YOUR_FORMSPREE_ID"

<!-- AFTER -->
action="https://formspree.io/f/mwpkgdyz"
```

---

## Step 3: Test Locally (2 minutes)

**Option A: Double-Click**
- Double-click `index.html`
- Opens in your default browser

**Option B: Command Line**
```bash
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"
open index.html
```

**Test the form:**
1. Enter a test address
2. Enter your email
3. Click **"GENERATE ANALYSIS"**
4. Wait for loading animation
5. Check for success message
6. Check your email inbox

---

## Step 4: Deploy to GitHub (4 minutes)

### If you DON'T have a GitHub account:

1. Go to **https://github.com**
2. Click **"Sign Up"**
3. Create account (free)

### Deploy Steps:

```bash
# Navigate to project folder
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"

# Initialize git
git init

# Add files
git add .

# Create commit
git commit -m "Initial deployment"

# Go to GitHub.com and create a new repository named: collab-mini-site
# (Make it PUBLIC for free hosting)

# Connect your local folder to GitHub (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/collab-mini-site.git

# Push code
git branch -M main
git push -u origin main
```

### Enable GitHub Pages:

1. Go to your repository on GitHub.com
2. Click **Settings** (top right)
3. Click **Pages** (left sidebar)
4. Under **Source**:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**

**Wait 2-3 minutes.** Your site will be live at:
```
https://YOUR_USERNAME.github.io/collab-mini-site/
```

---

## Step 5: Create QR Code (2 minutes)

1. Copy your live URL (from GitHub Pages)
2. Go to **https://www.qr-code-generator.com/**
3. Paste your URL
4. Click **"Create QR Code"**
5. Download as:
   - **SVG** (for print/design)
   - **PNG** (for digital use)

**Test it:**
- Open your phone camera
- Point at the QR code
- Tap the notification
- Should open your live site

---

## You're Done!

Your Co-Llab Mini Site is now:
- ✅ Live on the internet
- ✅ Accessible via QR code
- ✅ Collecting submissions via Formspree
- ✅ Sending emails to your inbox

---

## Next Steps

### Customize the Form

**Change colors:**
Open `index.html`, find the `:root` section, edit:
```css
--brand-navy: #0f2a4a;
--brand-blue: #3b82f6;
```

**Change loading messages:**
Find the `loadingSteps` array:
```javascript
const loadingSteps = [
    "Your custom message...",
    "Another message...",
];
```

**Add your logo:**
Replace the text header with an image:
```html
<img src="logo.svg" alt="The Co-Llab Group" style="width: 200px;">
```

### Monitor Submissions

**Formspree Dashboard:**
1. Log in to formspree.io
2. Click your form name
3. View all submissions in real-time

**Email Notifications:**
- Formspree automatically sends emails
- Check your spam folder if not receiving
- Configure custom email template in Formspree settings

### Update the Site

Make changes:
```bash
# 1. Edit index.html
# 2. Test locally (open index.html)
# 3. Commit and push
git add index.html
git commit -m "Update: [what you changed]"
git push

# 4. Wait 2-3 minutes for GitHub Pages to update
```

---

## Troubleshooting

### "Form doesn't submit"
- ✅ Check Formspree ID is correct
- ✅ Check internet connection
- ✅ Open browser console (F12) for errors

### "No email received"
- ✅ Check Formspree dashboard for submission
- ✅ Check spam folder
- ✅ Verify email in Formspree settings
- ✅ Free tier limit: 50/month

### "QR code doesn't work"
- ✅ Check URL is correct
- ✅ Test on multiple phones
- ✅ Ensure QR code is at least 2"x2" if printed
- ✅ Verify high contrast (black on white)

### "GitHub Pages not loading"
- ✅ Wait 5 minutes (can take time)
- ✅ Check repository is PUBLIC
- ✅ Verify Pages is enabled in Settings
- ✅ Clear browser cache

---

## Getting Help

**For this project:**
- Read `README.md` for detailed docs
- Read `TECHNICAL_DOCS.md` for code details
- Read `DEPLOYMENT.md` for step-by-step checklist

**For Formspree:**
- https://help.formspree.io

**For GitHub Pages:**
- https://docs.github.com/en/pages

**For HTML/CSS/JS:**
- https://developer.mozilla.org (MDN)

---

## Checklist

- [ ] Formspree account created
- [ ] Form ID copied
- [ ] `index.html` updated with Form ID
- [ ] Local test completed successfully
- [ ] Test email received
- [ ] GitHub account created (if needed)
- [ ] Repository created on GitHub
- [ ] Code pushed to GitHub
- [ ] GitHub Pages enabled
- [ ] Live site tested
- [ ] QR code generated
- [ ] QR code tested with phone

---

**Total Time:** 10-15 minutes

**You're ready to go live!**
