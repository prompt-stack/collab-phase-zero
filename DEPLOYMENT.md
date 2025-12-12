# Deployment Checklist
## Co-Llab Group - Mini Site Tool

Use this checklist to ensure a smooth deployment process.

---

## Pre-Deployment

### 1. Formspree Configuration ✓

- [ ] Create Formspree account at https://formspree.io
- [ ] Create new form project
- [ ] Copy form endpoint ID
- [ ] Update `index.html` line 158 with your Formspree ID
- [ ] Configure email notification settings
- [ ] Set up custom email template (optional)
- [ ] Test form submission in Formspree dashboard

**Example Configuration:**
```html
<!-- BEFORE -->
<form id="intakeForm" action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">

<!-- AFTER -->
<form id="intakeForm" action="https://formspree.io/f/mwpkgdyz" method="POST">
```

### 2. Local Testing ✓

- [ ] Open `index.html` in Chrome
- [ ] Open `index.html` in Safari
- [ ] Test on mobile device (scan test QR)
- [ ] Verify form submission works
- [ ] Check loading animation displays correctly
- [ ] Confirm success message appears
- [ ] Test error handling (disconnect wifi during submit)
- [ ] Validate responsive design at different screen sizes

**Test Data:**
```
Address: 123 Test Street, Austin, TX 78701
Vision: Mixed-use residential
Email: test@example.com
```

### 3. Code Review ✓

- [ ] Verify all placeholder text is correct
- [ ] Check brand colors match specifications
- [ ] Confirm loading messages are appropriate
- [ ] Review success message copy
- [ ] Validate HTML for accessibility (ARIA labels)
- [ ] Test keyboard navigation (Tab through form)

---

## GitHub Setup

### 4. Repository Creation ✓

- [ ] Log in to GitHub account
- [ ] Create new repository named `collab-mini-site`
- [ ] Set repository to Public (required for free GitHub Pages)
- [ ] Do NOT initialize with README (we have one)
- [ ] Copy repository URL

### 5. Git Initialization ✓

```bash
# Navigate to project folder
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"

# Initialize repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial deployment: Co-Llab Mini Site v1.0"

# Add remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/collab-mini-site.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**Checklist:**
- [ ] Repository initialized locally
- [ ] Files committed
- [ ] Remote added
- [ ] Pushed to GitHub
- [ ] Verify files visible on GitHub.com

### 6. GitHub Pages Activation ✓

1. Go to repository on GitHub.com
2. Click **Settings** tab
3. Scroll to **Pages** section (left sidebar)
4. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**
6. Wait 2-3 minutes for deployment

**Checklist:**
- [ ] Pages section found
- [ ] Main branch selected
- [ ] Root folder selected
- [ ] Green success banner appears
- [ ] Site URL displayed: `https://YOUR_USERNAME.github.io/collab-mini-site/`

---

## Post-Deployment

### 7. Live Site Testing ✓

- [ ] Visit deployed URL
- [ ] Test form submission with real data
- [ ] Check email arrives at configured address
- [ ] Verify mobile responsiveness on actual device
- [ ] Test on multiple browsers (Chrome, Safari, Firefox)
- [ ] Validate HTTPS certificate (green lock icon)

### 8. QR Code Generation ✓

- [ ] Go to https://www.qr-code-generator.com/
- [ ] Enter your deployed URL
- [ ] Select **High** error correction
- [ ] Download as SVG (vector format)
- [ ] Download as PNG (300x300px minimum)
- [ ] Test QR code with phone camera
- [ ] Confirm it opens correct URL

**QR Code Specs:**
- **Format:** SVG + PNG
- **Size:** 300x300px (PNG), Vector (SVG)
- **Error Correction:** High (H)
- **Quiet Zone:** 4 modules minimum

### 9. Print Materials ✓

- [ ] Create test print at 2"x2" size
- [ ] Verify QR code scans from paper
- [ ] Test from 12-18 inches distance
- [ ] Check on different phone models (iOS & Android)
- [ ] Prepare high-res version for professional printing

**Print Checklist:**
- [ ] QR code embedded in branded flyer
- [ ] Call-to-action text included
- [ ] URL printed below QR (backup)
- [ ] Co-Llab branding consistent

---

## Monitoring & Analytics (Optional)

### 10. Performance Tracking ✓

- [ ] Add Google Analytics (optional)
- [ ] Set up Formspree email notifications
- [ ] Create submission tracking spreadsheet
- [ ] Test email delivery speed
- [ ] Verify data reaches correct inbox

### 11. Error Monitoring ✓

- [ ] Check Formspree dashboard weekly
- [ ] Monitor GitHub Pages status
- [ ] Test live site monthly
- [ ] Review submission data quality

---

## Launch Day Checklist

### Pre-Launch (1 hour before)

- [ ] Final test of live site
- [ ] Verify email notifications working
- [ ] Check mobile experience
- [ ] Confirm QR codes printed correctly
- [ ] Test QR codes with multiple devices

### During Launch

- [ ] Monitor Formspree dashboard
- [ ] Watch for error emails
- [ ] Have backup contact method ready
- [ ] Keep laptop accessible for quick fixes

### Post-Launch (24 hours)

- [ ] Review first submissions
- [ ] Check for common errors in data
- [ ] Verify email delivery times
- [ ] Collect user feedback
- [ ] Document any issues

---

## Rollback Plan

If critical issues occur:

1. **Quick Fix** (5 minutes):
   ```bash
   # Make changes to index.html
   git add index.html
   git commit -m "Hotfix: [describe issue]"
   git push
   # Wait 2-3 minutes for Pages to update
   ```

2. **Emergency Rollback** (if site is broken):
   ```bash
   git revert HEAD
   git push
   ```

3. **Alternative:** Disable form temporarily:
   - Change form action to `#`
   - Add alert: "Temporarily unavailable"
   - Push update

---

## Custom Domain Setup (Optional)

If using a custom domain (e.g., `minisite.collabgroup.com`):

### DNS Configuration

1. Add CNAME record in your DNS provider:
   ```
   Type: CNAME
   Name: minisite
   Value: YOUR_USERNAME.github.io
   ```

2. Update GitHub Pages settings:
   - Go to Settings > Pages
   - Enter custom domain: `minisite.collabgroup.com`
   - Enable "Enforce HTTPS" (after DNS propagates)

3. Wait 24-48 hours for DNS propagation

**Checklist:**
- [ ] CNAME record added
- [ ] Custom domain configured in GitHub
- [ ] HTTPS enabled
- [ ] Test custom URL

---

## Maintenance Schedule

### Weekly
- [ ] Check Formspree submission count
- [ ] Review email delivery logs
- [ ] Test live site functionality

### Monthly
- [ ] Audit submission data quality
- [ ] Review loading messages for relevance
- [ ] Check mobile experience on new devices
- [ ] Update QR codes if URL changed

### Quarterly
- [ ] Review analytics (if implemented)
- [ ] Consider UX improvements
- [ ] Update copy based on feedback
- [ ] Test on latest browser versions

---

## Contact Information

**Primary Contact:** [Your Name]
**Email:** [Your Email]
**GitHub:** [Your GitHub Username]

**Formspree Account:** [Account Email]
**Repository:** https://github.com/YOUR_USERNAME/collab-mini-site

---

## Version History

| Version | Date | Changes | Deployed By |
|---------|------|---------|-------------|
| 1.0.0 | Dec 2025 | Initial release | [Your Name] |

---

## Success Criteria

Deployment is successful when:

- ✅ Live site loads without errors
- ✅ Form submissions reach designated email
- ✅ QR code successfully opens site on mobile
- ✅ All three UI states function correctly (form → loading → success)
- ✅ No console errors in browser developer tools
- ✅ Mobile responsive design works on iPhone and Android
- ✅ HTTPS enabled with valid certificate
- ✅ Page loads in under 2 seconds on 3G

---

**Deployment Status:** ⏳ Ready for Configuration

**Next Step:** Complete Section 1 - Formspree Configuration
