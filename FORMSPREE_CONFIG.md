# Formspree Configuration Guide
## Co-Llab Group - Mini Site Tool

This guide helps you configure Formspree to deliver beautiful, branded email notifications.

---

## Step 1: Create Your Form

1. Log in to **https://formspree.io**
2. Click **"+ New Form"**
3. **Form Name:** `Co-Llab Mini Site`
4. **Notification Email:** Enter where you want submissions sent
5. Click **"Create Form"**
6. **Copy the Form ID** (e.g., `mwpkgdyz`)

---

## Step 2: Configure Email Settings

### Basic Settings

Navigate to your form dashboard → **Settings** tab:

| Setting | Recommended Value |
|---------|-------------------|
| **Form Name** | Co-Llab Mini Site |
| **Reply-To** | Use submitter's email (enables direct reply) |
| **Subject Line** | `New Site Analysis Request` |
| **Redirect** | Leave blank (using custom success state) |

### Email Template

**Default Template (Auto-Generated):**
```
You have a new submission from Co-Llab Mini Site:

Address: [submitted value]
Vision: [submitted value]
Email: [submitted value]

Submitted on: [timestamp]
Submitted from: [IP address]
```

**Custom Template (Optional):**

If you have Formspree's paid plan, you can customize the email HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background-color: #f0f4f8;
            padding: 20px;
        }
        .container {
            background: white;
            border-radius: 8px;
            padding: 30px;
            max-width: 600px;
            margin: 0 auto;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .header {
            border-bottom: 3px solid #0f2a4a;
            padding-bottom: 15px;
            margin-bottom: 20px;
        }
        .header h1 {
            color: #0f2a4a;
            margin: 0;
            font-size: 24px;
        }
        .field {
            margin: 15px 0;
            padding: 15px;
            background: #f8fafc;
            border-radius: 6px;
        }
        .field-label {
            font-weight: 700;
            color: #0f2a4a;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 5px;
        }
        .field-value {
            color: #1e293b;
            font-size: 16px;
            margin: 5px 0 0 0;
        }
        .action-button {
            display: inline-block;
            background: #3b82f6;
            color: white;
            padding: 12px 24px;
            border-radius: 6px;
            text-decoration: none;
            margin-top: 20px;
        }
        .footer {
            margin-top: 30px;
            padding-top: 15px;
            border-top: 1px solid #e2e8f0;
            font-size: 12px;
            color: #64748b;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏗️ New Site Analysis Request</h1>
        </div>

        <div class="field">
            <div class="field-label">Property Address</div>
            <div class="field-value">{{address}}</div>
        </div>

        <div class="field">
            <div class="field-label">Project Vision / Intent</div>
            <div class="field-value">{{vision}}</div>
        </div>

        <div class="field">
            <div class="field-label">Contact Email</div>
            <div class="field-value"><a href="mailto:{{email}}">{{email}}</a></div>
        </div>

        <a href="mailto:{{email}}?subject=Re:%20Your%20Site%20Analysis%20Request" class="action-button">
            Reply to Lead →
        </a>

        <div class="footer">
            <p>Submitted: {{_timestamp}}</p>
            <p>Source: Co-Llab Mini Site (QR Code)</p>
        </div>
    </div>
</body>
</html>
```

---

## Step 3: Advanced Settings

### Spam Protection

**reCAPTCHA (Optional):**
- ⚠️ **Pros:** Blocks spam submissions
- ⚠️ **Cons:** Adds friction, requires user interaction
- **Recommendation:** Only enable if spam becomes an issue

To enable:
1. Settings → **Spam Protection**
2. Toggle **"Enable reCAPTCHA"**
3. Choose reCAPTCHA version (v3 is invisible)

### Auto-Reply to Submitters

Send an automatic confirmation email to users:

**Subject:** `Your Site Analysis is Being Prepared`

**Body:**
```
Hi there,

Thank you for your interest in Co-Llab Group's Phase Zero analysis!

We've received your request for:
📍 {{address}}

Our team is now gathering zoning regulations, market data, and development
constraints for this property.

You'll receive your Executive Brief within 24-48 hours.

In the meantime, feel free to reply to this email with any questions.

Best regards,
The Co-Llab Group
---
AI-Powered Development Intelligence
```

To configure:
1. Settings → **Autoresponder**
2. Toggle **"Enable Autoresponder"**
3. Set **Subject** and **Message**
4. Use `{{address}}` and other field variables

### Webhooks (Advanced)

For integrating with other tools (Zapier, Slack, etc.):

**Example Slack Notification:**
1. Settings → **Integrations** → **Webhooks**
2. Add webhook URL: `https://hooks.slack.com/services/YOUR/WEBHOOK/URL`
3. Slack will receive instant notifications on submissions

**Example Zapier Automation:**
1. Create Zap: Formspree → Google Sheets
2. Auto-log submissions to spreadsheet
3. Track leads over time

---

## Step 4: Field Mapping

Formspree automatically detects these fields from your form:

| HTML Field Name | Type | In Email As |
|-----------------|------|-------------|
| `address` | text | "Address" |
| `vision` | text | "Vision" |
| `email` | email | "Email" |

**Hidden Fields (Auto-Captured):**
- `_timestamp` - Submission date/time
- `_ip` - Client IP address
- `_user_agent` - Browser info

---

## Step 5: Testing

### Send Test Submission

1. Open your local `index.html`
2. Fill out form with test data:
   ```
   Address: 123 Test Street, Austin, TX 78701
   Vision: Mixed-use residential
   Email: your-email@example.com
   ```
3. Submit form
4. Check inbox for email (allow 1-2 minutes)

### Verify Email Content

Check that email includes:
- ✅ All three fields (address, vision, email)
- ✅ Readable formatting
- ✅ Correct "From" address
- ✅ Correct "Subject" line
- ✅ Timestamp

### Test Edge Cases

**Empty Optional Field:**
- Leave "Vision" blank
- Ensure email still sends correctly

**Long Address:**
- Enter very long address (200+ characters)
- Verify it doesn't break email layout

**Special Characters:**
- Try address with apostrophes, commas
- Example: `O'Brien's Building, Suite 5, Austin, TX`

---

## Step 6: Quota Management

### Free Tier Limits

**Formspree Free Plan:**
- ✅ 50 submissions per month
- ✅ Unlimited forms
- ✅ Basic email notifications
- ✅ Spam filtering
- ❌ No custom templates
- ❌ No file uploads

**Monitoring Usage:**
1. Dashboard → **Your Form**
2. View submission count: `X / 50 this month`
3. Resets on 1st of each month

### If You Hit Limit

**Option 1:** Upgrade to paid plan ($10/month)
**Option 2:** Create secondary form (switch mid-month)
**Option 3:** Use alternative service (EmailJS, etc.)

---

## Step 7: Email Deliverability

### Avoid Spam Folder

**Tips:**
1. **Add Formspree to Contacts:** Whitelist `submissions@formspree.io`
2. **Check Spam Folder:** Initial emails may land there
3. **Mark as "Not Spam":** Trains your email filter
4. **Use Custom Domain:** Consider custom email domain for Formspree (paid feature)

### Gmail-Specific

If using Gmail, add filter:
1. Gmail Settings → **Filters and Blocked Addresses**
2. Create filter:
   - **From:** `submissions@formspree.io`
   - **Subject:** `New Site Analysis Request`
3. Apply label: `Co-Llab Leads`
4. **Never send to Spam**

---

## Sample Email Output

This is what you'll receive:

```
From: submissions@formspree.io
To: your-email@example.com
Subject: New Site Analysis Request
Date: Thu, Dec 12, 2025, 11:45 AM

You have a new submission from Co-Llab Mini Site:

Address: 1401 West 6th Street, Austin, TX 78703
Vision: Mixed-use with ground floor retail and 4 stories residential
Email: developer@realtypartners.com

---
Submitted on: Dec 12, 2025, 11:45:32 AM CST
Submitted from: 108.25.147.92
User Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 17_0 like Mac OS X)
```

---

## Troubleshooting

### "Form not submitting"

**Check:**
1. Formspree ID is correct in `index.html`
2. Form action URL is complete: `https://formspree.io/f/YOUR_ID`
3. Internet connection is active
4. Browser console for JavaScript errors

**Test:**
- Visit `https://formspree.io/f/YOUR_ID` directly
- Should see Formspree branding (confirms form exists)

### "No email received"

**Check:**
1. Spam folder
2. Formspree dashboard shows submission
3. Email address in settings is correct
4. Submission count under monthly limit (50 free tier)

**Fix:**
- Wait 5 minutes (can be delayed)
- Check Formspree "Submissions" tab
- Verify email notification settings enabled

### "Email formatting broken"

**Check:**
1. Field names match exactly: `address`, `vision`, `email`
2. No extra spaces in field names
3. HTML input `name` attribute is set correctly

**Example:**
```html
<!-- CORRECT -->
<input type="text" name="address" id="address">

<!-- WRONG -->
<input type="text" id="address">  <!-- Missing name attribute -->
```

---

## Security Best Practices

1. **Never Expose API Keys:** Formspree form ID is safe to expose publicly
2. **Rate Limiting:** Formspree automatically rate-limits to prevent abuse
3. **HTTPS Only:** Always use HTTPS (GitHub Pages enforces this)
4. **Validate Input:** HTML5 validation + Formspree server-side validation
5. **Monitor Submissions:** Check dashboard weekly for suspicious activity

---

## Upgrading to Paid Plan

**Formspree Gold ($10/month):**
- ✅ Unlimited submissions
- ✅ Custom email templates
- ✅ File uploads (up to 10MB)
- ✅ Remove Formspree branding
- ✅ Priority support

**When to Upgrade:**
- Exceeding 50 submissions/month
- Need custom email branding
- Want file upload capability
- Require faster support

---

## Alternative Services (If Needed)

| Service | Free Tier | Pricing | Notes |
|---------|-----------|---------|-------|
| **Formspree** | 50/month | $10/month unlimited | Recommended |
| **EmailJS** | 200/month | $9/month unlimited | More generous free tier |
| **Getform** | 50/month | $9.99/month unlimited | Similar to Formspree |
| **Basin** | 100/month | $5/month unlimited | Cheapest paid option |
| **FormSubmit** | Unlimited | Free | No dashboard, basic |

---

## Quick Reference

### Essential URLs

**Formspree Dashboard:**
https://formspree.io/forms

**Your Form URL:**
https://formspree.io/f/YOUR_FORM_ID

**Documentation:**
https://help.formspree.io

### Key Formspree Settings

```
Form Name: Co-Llab Mini Site
Notification Email: your-email@example.com
Subject: New Site Analysis Request
Reply-To: Use submitter's email
reCAPTCHA: Disabled (unless spam becomes issue)
Autoresponder: Enabled (optional)
```

### Form Fields

```
address (text, required)
vision (text, optional)
email (email, required)
```

---

## Support

**Formspree Help Center:**
https://help.formspree.io

**Formspree Community Forum:**
https://community.formspree.io

**Email Support (Paid Plans):**
support@formspree.io

---

**Configuration Status:** ⏳ Awaiting Setup

**Next Step:** Create Formspree account and copy Form ID to `index.html`
