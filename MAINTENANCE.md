# 🛠️ Website Maintenance & Customization Guide

## Quick Links
- **Edit Colors**: `style.css` lines 1-12 (CSS Variables)
- **Edit Content**: `index.html` - edit text in sections
- **Edit Forms**: `index.html` - lines ~270 (Contact) and ~310 (Newsletter)
- **Edit Footer**: `index.html` - bottom of file

## Common Tasks

### 1. Update Email Address
**File**: `index.html`

Find and replace all instances of:
```html
dieamselcollective@gmail.com
```
With your new email address.

### 2. Change Brand Colors

**File**: `style.css` (Top of file)

Update these variables:
```css
:root {
  --accent: #d97ab2;           /* Primary pink - main buttons, headings */
  --accent-dark: #c25a93;      /* Darker pink - on hover */
  --accent-light: #dfa1c2;     /* Lighter pink - light backgrounds */
  --bg: #f5ebe0;               /* Page background */
  --text: #3d2b1f;             /* Body text color */
}
```

**Example**: Change to purple theme:
```css
--accent: #8b5cf6;           /* Purple */
--accent-dark: #7c3aed;      /* Dark purple */
--accent-light: #a78bfa;     /* Light purple */
```

### 3. Update Text Content

#### Hero Section (Lines 45-55)
```html
<h1>Welcome to dieAmsel Collective</h1>
<p>We provide a safe platform...</p>
```

#### About Section (Lines 75-85)
```html
<h2>About Us - dieAmsel Collective</h2>
<p>dieAmsel Collective consists of...</p>
```

#### Help Section (Lines 125-155)
Each card has:
```html
<h3>Card Title</h3>
<p>Card description text</p>
```

### 4. Update Form Field Labels

**Contact Form** (Line ~270):
```html
<label for="contact-name">Your Label*</label>
```

**Newsletter Form** (Line ~310):
```html
<label for="newsletter-email">Your Label*</label>
```

### 5. Change Formspree Form IDs

After creating forms in Formspree:

**Contact Form** (Line ~273):
```html
action="https://formspree.io/f/YOUR_FORM_ID"
```

**Newsletter Form** (Line ~313):
```html
action="https://formspree.io/f/YOUR_FORM_ID"
```

### 6. Customize Cookie Banner

**File**: `index.html` (Lines 14-25)

```html
<h3>Your Privacy Matters</h3>          <!-- Change title -->
<p>We use cookies to improve...</p>    <!-- Change message -->
```

### 7. Update Navigation Links

**File**: `index.html` (Lines 37-42)

```html
<nav class="nav">
  <a href="index.html" class="active">Home</a>
  <a href="#about">About us</a>
  <a href="#contact">Contact us</a>
  <a href="#newsletter">Newsletter</a>
</nav>
```

## CSS Customization

### Change Button Style
**File**: `style.css` (Line ~120)

Current:
```css
.btn-pink {
  background: linear-gradient(135deg, var(--accent-light) 0%, var(--accent) 100%);
  color: var(--white);
}
```

Options:
- Remove gradient: `background: var(--accent);`
- Change direction: `linear-gradient(90deg, ...)` (left-to-right)
- Add border: `border: 2px solid var(--accent);`

### Adjust Spacing
**File**: `style.css`

- Section padding: `padding: 80px 48px;` (change 80 for height)
- Gaps between cards: `gap: 40px 32px;` (first = vertical, second = horizontal)
- Margins: `margin: 20px;` (adjust as needed)

### Change Font
**File**: `style.css` (Line 33)

Current:
```css
font-family: Georgia, 'Times New Roman', serif;
```

Options:
```css
/* Sans-serif (modern) */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;

/* Playful */
font-family: 'Trebuchet MS', sans-serif;

/* Professional */
font-family: 'Courier New', monospace;

/* Or use Google Fonts - add to <head> first */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');
font-family: 'Inter', sans-serif;
```

### Adjust Animation Speed
**File**: `style.css` (Lines with `0.3s ease`)

Change `0.3s` to:
- `0.15s` - very fast
- `0.3s` - current (default)
- `0.5s` - slower
- `0.8s` - very slow

## Testing

### Before Going Live
1. **Test Forms**
   - Fill out contact form → check email
   - Subscribe to newsletter → check email
   - Try with missing fields → should show error

2. **Test Cookie Banner**
   - Clear browser cookies
   - Refresh page → banner should appear
   - Click Accept → banner disappears, cookie saved
   - Refresh page → banner should NOT appear
   - Clear cookies again → repeat

3. **Test Mobile**
   - Resize to 375px wide → should stack vertically
   - Test on actual phone if possible
   - Test landscape orientation

4. **Test Accessibility**
   - Use keyboard Tab to navigate → all buttons should be focusable
   - Check color contrast with contrast checker
   - Test with screen reader (optional)

### Browser Testing
- Chrome/Edge
- Firefox
- Safari
- Mobile Safari (iOS)
- Chrome Mobile (Android)

## Deployment

### Upload Files
Upload these files to your web host:
```
index.html
style.css
gdpr.html
SETUP_GUIDE.md
IMPROVEMENTS.md
assets/
```

### Verify After Upload
1. Visit your domain
2. Test all forms
3. Test cookie banner
4. Check mobile view
5. Test all navigation links

### Production Checklist
- [ ] Email forms are working
- [ ] Form emails are received
- [ ] Cookie consent works
- [ ] All links are working
- [ ] Mobile view is responsive
- [ ] Images are loading
- [ ] No console errors (F12 to check)
- [ ] Lighthouse score > 90 (optional)

## Troubleshooting

### Forms Not Working
- ✅ Check Formspree form IDs are correct
- ✅ Verify form action URL is complete
- ✅ Check browser console for errors (F12)
- ✅ Try in incognito window
- ✅ Test email address works

### Cookie Banner Not Appearing
- ✅ Check js-cookie library is loaded (line 8)
- ✅ Clear browser cookies and refresh
- ✅ Check browser console for errors
- ✅ Verify cookie-consent div has `display: none` initially

### Styling Issues
- ✅ Hard refresh (Ctrl+F5 or Cmd+Shift+R)
- ✅ Clear browser cache
- ✅ Check CSS file is linked correctly
- ✅ No typos in CSS variable names

### Mobile Issues
- ✅ Check viewport meta tag exists
- ✅ Verify media queries in CSS
- ✅ Test with DevTools mobile emulation
- ✅ Test on actual device

## Performance Tips

### Optimize Images
- Use appropriate image sizes
- Compress images before upload
- Consider WebP format for new images

### Improve Speed
- Minimize CSS (optional)
- Lazy load images (optional)
- Enable gzip compression on server

### SEO Optimization
1. Add meta description in `<head>`:
```html
<meta name="description" content="Your site description">
```

2. Update page title:
```html
<title>dieAmsel Collective - Safe Sexual Health Platform</title>
```

3. Add Schema markup (optional):
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "dieAmsel Collective"
}
</script>
```

## Support Resources
- Formspree Help: https://formspree.io/docs
- CSS Documentation: https://developer.mozilla.org/en-US/docs/Web/CSS
- HTML Guide: https://developer.mozilla.org/en-US/docs/Web/HTML
- Browser DevTools: Press F12 to debug

---

**Need help? Check the error message in the browser console (F12)** 🔍
