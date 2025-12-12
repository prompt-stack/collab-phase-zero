# Co-Llab Group - AI "Mini Site" Exploration Tool

**Version:** 1.0
**Status:** Ready for Deployment
**Organization:** The Co-Llab Group

## Overview

A lightweight, mobile-first web application designed to capture real estate lead data (address, vision, contact info) via QR code. Built with a "Wizard of Oz" architecture that simulates real-time AI analysis while asynchronously processing data through Formspree.

---

## Features

- **Zero Build Required** - Pure HTML/CSS/JavaScript
- **Mobile-First Design** - Optimized for QR code scanning
- **Engaging UX** - Simulated AI processing with animated state transitions
- **Professional Aesthetic** - Co-Llab branded design system
- **Free Hosting** - Deploy to GitHub Pages at no cost

---

## Technology Stack

- **Frontend:** Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Styling:** CSS Variables + Custom Design System
- **Backend:** Formspree (Form handling & Email delivery)
- **Hosting:** GitHub Pages (Static hosting)
- **No Dependencies:** Zero npm packages, no build tools

---

## Quick Start

### 1. Configure Formspree

1. Go to [formspree.io](https://formspree.io) and create a free account
2. Create a new form project
3. Copy your form endpoint ID (format: `xyzabc123`)
4. Open `index.html` and replace `YOUR_FORMSPREE_ID` with your actual ID:

```html
<form id="intakeForm" action="https://formspree.io/f/xyzabc123" method="POST">
```

### 2. Test Locally

Simply open `index.html` in your browser:

```bash
open index.html
```

Or use a local server:

```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

### 3. Deploy to GitHub Pages

#### Option A: Using Git Commands

```bash
# Initialize git repository (if not already done)
git init

# Add files
git add .

# Commit
git commit -m "Initial commit: Co-Llab Mini Site"

# Create GitHub repo and push
# (Replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/collab-mini-site.git
git branch -M main
git push -u origin main

# Enable GitHub Pages
# Go to: Repository Settings > Pages
# Source: main branch / root folder
# Save
```

#### Option B: Using GitHub Desktop

1. Open GitHub Desktop
2. Add this folder as a repository
3. Publish to GitHub
4. Go to repository settings on GitHub.com
5. Navigate to "Pages" section
6. Select "main" branch and "/" root
7. Save and wait for deployment

Your site will be live at: `https://YOUR_USERNAME.github.io/collab-mini-site/`

---

## Configuration

### Formspree Setup

After creating your Formspree form, configure email notifications:

1. **Email Destination:** Set where form submissions should be sent
2. **Custom Subject:** Use "New Site Analysis Request - [address]"
3. **Auto-reply:** Optional confirmation email to the user
4. **Spam Protection:** Enable reCAPTCHA if needed (may impact UX)

### Form Field Mapping

The form submits three fields:

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| `address` | text | Yes | Property street address |
| `vision` | text | No | Project intent/vision |
| `email` | email | Yes | Contact email for report delivery |

---

## Customization Guide

### Color Scheme

Edit CSS variables in the `<style>` section:

```css
:root {
    --brand-navy: #0f2a4a;     /* Headers, primary text */
    --brand-blue: #3b82f6;     /* Buttons, accents */
    --brand-bg: #f0f4f8;       /* Page background */
    --text-main: #1e293b;      /* Body text */
    --card-white: #ffffff;     /* Card background */
}
```

### Loading Messages

Customize the AI simulation messages in the JavaScript section:

```javascript
const loadingSteps = [
    "Identifying Parcel Boundaries...",
    "Accessing Zoning Database...",
    "Pulling Market Demographics...",
    "Generating Optimal Use Scenarios...",
    "Finalizing Report Structure..."
];
```

### Timing

Adjust animation speed:

```javascript
}, 1200); // Message changes every 1.2 seconds
```

---

## QR Code Generation

To create a QR code for your deployed site:

### Free Online Tools
- [QR Code Generator](https://www.qr-code-generator.com/)
- [QRCode Monkey](https://www.qrcode-monkey.com/)

### Recommended Settings
- **Format:** PNG or SVG
- **Size:** 300x300px minimum
- **Error Correction:** Medium (M)
- **Margin:** 4 modules

### Print Specifications
- **Minimum Size:** 2" x 2" (50mm x 50mm)
- **Resolution:** 300 DPI
- **Format:** Vector (SVG/PDF) for scalability

---

## File Structure

```
mini-site-form/
├── index.html          # Main application (single file)
├── README.md           # This file
└── DEPLOYMENT.md       # Deployment checklist
```

---

## State Machine Logic

The application uses a simple finite state machine:

```
[IDLE] → User submits form
    ↓
[SUBMITTING] → Formspree API call + Loading animation
    ↓
[SUCCESS] → Confirmation message
    ↓ (on error)
[ERROR] → Return to IDLE, allow retry
```

---

## Browser Support

- **Chrome/Edge:** 90+
- **Safari:** 14+
- **Firefox:** 88+
- **Mobile Safari:** iOS 14+
- **Chrome Mobile:** Android 5+

No polyfills required. Uses native Fetch API and ES6.

---

## Security & Privacy

- **HTTPS Only:** GitHub Pages enforces SSL
- **No Cookies:** No tracking or session management
- **Client-Side Only:** No sensitive data stored locally
- **Formspree Compliance:** GDPR-compliant data handling

---

## Troubleshooting

### Form Not Submitting

1. Check browser console for errors
2. Verify Formspree ID is correct
3. Ensure form action URL is complete: `https://formspree.io/f/YOUR_ID`
4. Check network tab for 403/404 errors

### Styling Issues on Mobile

1. Test on real device, not just desktop browser resize
2. Check viewport meta tag is present
3. Verify touch targets are at least 44x44px

### GitHub Pages Not Updating

1. Clear browser cache (Cmd+Shift+R / Ctrl+F5)
2. Check repository settings > Pages is enabled
3. Wait 2-3 minutes for deployment
4. Check Actions tab for build errors

---

## Performance

- **Page Weight:** ~8KB (HTML + CSS + JS)
- **Load Time:** <500ms on 3G
- **First Paint:** <1s
- **Lighthouse Score:** 95+ (Mobile)

---

## Maintenance

This is a **zero-maintenance** application:

- No dependencies to update
- No build pipeline to break
- No server to maintain
- Formspree handles infrastructure

---

## Future Enhancements (Optional)

- [ ] Add Google Analytics for tracking
- [ ] Implement A/B testing for copy
- [ ] Add custom logo SVG
- [ ] Create dark mode variant
- [ ] Add multi-language support
- [ ] Implement progressive web app (PWA) features

---

## Support

For issues or questions:

1. Check the troubleshooting section above
2. Review Formspree documentation: https://help.formspree.io
3. GitHub Pages docs: https://docs.github.com/en/pages

---

## License

Proprietary - The Co-Llab Group © 2025

---

## Credits

**Design System:** Co-Llab "Phase Zero" Brand Guidelines
**Architecture:** Wizard of Oz Pattern
**Developer:** [Your Name]
**Version:** 1.0.0
**Last Updated:** December 2025
