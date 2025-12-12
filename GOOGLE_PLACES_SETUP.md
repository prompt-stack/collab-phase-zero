# Google Places Autocomplete Setup Guide

I've added Google Places Autocomplete to your address field! Now users will get professional address suggestions as they type.

---

## 🔑 Get Your Google API Key (Free)

### Step 1: Go to Google Cloud Console

1. Visit: **https://console.cloud.google.com/**
2. Sign in with your Google account

### Step 2: Create a Project

1. Click the project dropdown (top left)
2. Click **"New Project"**
3. Name it: "Co-Llab Phase Zero"
4. Click **"Create"**

### Step 3: Enable Places API

1. In the search bar, type: **"Places API"**
2. Click on **"Places API"**
3. Click **"Enable"**

### Step 4: Create API Key

1. Go to **"Credentials"** (left sidebar)
2. Click **"+ Create Credentials"** → **"API Key"**
3. Copy your API key (looks like: `AIzaSyB...`)

### Step 5: Restrict Your API Key (Important!)

1. Click on your new API key
2. Under **"Application restrictions"**:
   - Select **"HTTP referrers (websites)"**
   - Click **"Add an item"**
   - Add: `https://prompt-stack.github.io/collab-phase-zero/*`
   - Add: `http://localhost:*` (for local testing)
3. Under **"API restrictions"**:
   - Select **"Restrict key"**
   - Check **"Places API"**
4. Click **"Save"**

---

## 📝 Add API Key to Your Site

### Option 1: Update Local File

1. Open `index.html`
2. Find line 9:
   ```html
   <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
   ```
3. Replace `YOUR_API_KEY` with your actual key:
   ```html
   <script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyB...&libraries=places"></script>
   ```
4. Save the file

### Option 2: Quick Command

```bash
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"

# Replace YOUR_ACTUAL_KEY with the key you copied
sed -i '' 's/YOUR_API_KEY/YOUR_ACTUAL_KEY/g' index.html
```

---

## 🚀 Deploy the Update

```bash
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"

git add index.html
git commit -m "Add Google Places Autocomplete for address field"
git push

# Site updates in 1-2 minutes!
```

---

## ✅ How It Works

### User Experience:

1. User clicks on "Property Address" field
2. Starts typing: "123 Main..."
3. Google shows dropdown with matching addresses:
   ```
   📍 123 Main St, Austin, TX 78701
   📍 123 Main St, Houston, TX 77002
   📍 123 Main Street, Dallas, TX 75201
   ```
4. User clicks on their address
5. Full formatted address fills in automatically

### Features Included:

- ✅ **US addresses only** (configurable)
- ✅ **Autocomplete dropdown** styled to match your brand
- ✅ **Full address formatting** (street, city, state, ZIP)
- ✅ **Mobile-friendly** touch interactions
- ✅ **Keyboard navigation** (arrow keys + enter)

---

## 💰 Pricing (Free Tier Generous)

Google Places Autocomplete pricing:

- **Free tier:** $200/month credit
- **Cost per request:** $0.017 (Autocomplete Session)
- **Your free allowance:** ~11,700 address lookups/month

**Example:** Even with 500 form fills per month, you're well within the free tier.

---

## 🎨 Styling Customization

The autocomplete dropdown is styled to match your brand:

```css
.pac-container {
    /* Matches your card shadow */
    box-shadow: 0 10px 30px rgba(43, 92, 143, 0.15);
    border-radius: 8px;
}

.pac-item-selected {
    /* Teal highlight on hover */
    background-color: rgba(79, 179, 191, 0.1);
}

.pac-item-query {
    /* Navy text for main address */
    color: #2b5c8f;
    font-weight: 600;
}
```

---

## 🔧 Advanced Configuration

### Change to Worldwide Addresses

In `index.html`, find:
```javascript
componentRestrictions: { country: 'us' },
```

Remove this line to allow any country.

### Restrict to Specific States

```javascript
componentRestrictions: {
    country: 'us',
    administrativeArea: 'TX' // Texas only
},
```

### Change Address Types

```javascript
types: ['address'],        // Street addresses
types: ['geocode'],        // All locations
types: ['(cities)'],       // Cities only
types: ['establishment'],  // Businesses/landmarks
```

---

## 🐛 Troubleshooting

### Dropdown Doesn't Appear

**Check:**
1. Is your API key valid? (copy-paste error?)
2. Is Places API enabled in Google Cloud Console?
3. Check browser console for errors (F12)

### "This API project is not authorized to use this API"

**Solution:**
1. Make sure you enabled **Places API** (not just Maps API)
2. Wait 5 minutes for changes to propagate

### Autocomplete Works Locally But Not on GitHub Pages

**Solution:**
1. Add your GitHub Pages URL to API key restrictions:
   `https://prompt-stack.github.io/collab-phase-zero/*`

---

## 📊 Monitor Usage

Track your API usage:

1. Go to Google Cloud Console
2. Navigate to **"APIs & Services"** → **"Dashboard"**
3. Click on **"Places API"**
4. View request charts

---

## 🎯 Testing

### Local Test:
```bash
cd "/Users/hoff/Desktop/My Drive/workspace/client/CO-LLAB/mini-site-form"
open index.html
```

1. Click address field
2. Type "123 main st aus"
3. Should see Austin addresses appear

### Live Test:
1. Visit: https://prompt-stack.github.io/collab-phase-zero/
2. Click address field
3. Type any partial address
4. Verify dropdown appears

---

## 🔒 Security Best Practices

✅ **Restrict your API key** to your domain only
✅ **Limit to Places API** only (not all Google APIs)
✅ **Monitor usage** to catch abuse early
✅ **Set up billing alerts** (though free tier is generous)

---

## 🎉 Benefits

**For Users:**
- ✅ Faster form completion
- ✅ Fewer typos/errors
- ✅ Properly formatted addresses
- ✅ Professional experience

**For You:**
- ✅ Higher quality data
- ✅ Valid addresses only
- ✅ Standardized format
- ✅ Better lead information

---

## Alternative: No API Key Required

If you don't want to set up Google API:

**Option 1:** Keep the basic input field (works fine, just no autocomplete)

**Option 2:** Use browser's native autocomplete:
```html
<input
    type="text"
    name="address"
    autocomplete="street-address"
    list="address-history"
>
```

This uses the browser's saved addresses (free, no API needed).

---

## Quick Setup Summary

1. ✅ Go to console.cloud.google.com
2. ✅ Create project
3. ✅ Enable Places API
4. ✅ Create API key
5. ✅ Restrict to your domain
6. ✅ Copy key into index.html line 9
7. ✅ Push to GitHub
8. ✅ Test on live site

**Estimated time:** 10 minutes

---

**Ready to set up?** Follow the steps above and your users will have a professional address autocomplete experience! 🎯
