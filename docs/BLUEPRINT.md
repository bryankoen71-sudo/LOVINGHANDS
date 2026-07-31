
# LOVING HANDS - Blueprint & Build Guide
Version: Final Secret Admin v1
Date: 2026-07-31

## 1. Overview
This package contains the full Loving Hands site with:
- Splash screen: Giving Love logo, 380px, intense pink (#E6086B) + blue (#4F46E5) neon double glow, 5 sec duration
- Gallery: 9 people images looping every 1 second (replaces original caregiver image)
- Top Nav Logo: 60px rotating conic-gradient glow (top->left->bottom->right) continuous, 2s loop, blur 18px
- Secret Admin: bottom logo 7 clicks -> password love1234 -> unlimited editing

## 2. Folder Structure
- index.html - FINAL production file (upload this)
- assets/gallery/ - 9 webp images used in loop
- assets/logos/ - giving-love-logo.webp (splash)
- docs/ - design and instructions with images
- scripts/ - previous builds for reference

## 3. Step-by-Step Build Process
### Step 1: Base Site
Started from file8709768987288915149.html (React build). Located splash timer (hold 500ms, out 3000ms, hide 4000ms) and caregiver image.

### Step 2: Gallery Injection
- Converted 9 user images to base64 data URLs to embed
- Created #lh-gallery-wrap with absolute positioned imgs, opacity transition 0.6s
- JS MutationObserver waits for React to render caregiver img, then replaces its card with gallery
- setInterval 1000ms cycles active class

Code:
```
let cur=0;
setInterval(()=>{ els[cur].classList.remove('active'); cur=(cur+1)%els.length; els[cur].classList.add('active'); },1000);
```

### Step 3: Splash Override
- Created #custom-splash fixed z-index 9999999 covering viewport
- Inner: .splash-logo-outer 380px with ::before and ::after conic gradients blurred 22px and 38px, animation outerGlow scale pulse
- Inner card: white background, padding 28px, border-radius 40px, box-shadow pink/blue
- Timer: 5000ms then add .hide class (opacity 0 scale 0.97) and remove

### Step 4: Top Logo Rotating Glow
- Wrapped top logo img in .nav-logo-glow-wrap 60px
- ::before: conic-gradient(E6086B 0deg, #4F46E5 90deg...) inset -5px, animation rotateGlow 2s linear infinite
- ::after: same gradient blurred 18px inset -16px reverse
- JS finds img[alt*="Loving Hands Logo"] and wraps

### Step 5: Secret Admin
- Click counter on bottom logo (footer img): 7 clicks within 2s opens #admin-login-modal
- Password check love1234 -> shows #admin-panel
- Admin features:
  - Gallery: bulk upload via FileReader to dataURL, save to localStorage LH_ADMIN_CONFIG
  - Logos: upload top/splash/footer
  - Content: scrape h1-h4,p,button (80 items) allow inline edit, save to textOverrides
  - Style: glowSize, glowBlur, colors
  - Sections: hide/show sections
  - Data: export JSON, import, rebuild HTML (replace window.__LH_GALLERY_IMAGES array and download blob)
  - Apply saved: on load, override src and text

## 4. How to Deploy
1. Upload index.html to your host (Netlify, GitHub Pages, cPanel) as index.html
2. Test splash (5s), gallery (1s), top glow, bottom 7-click admin
3. For edits: open admin, make changes, click Rebuild & Download Site, re-upload

## 5. Design System
- Primary Pink: #E6086B
- Primary Blue: #4F46E5
- Glow: double layer - sharp 5px + blurred 18px
- Font: Inter, letter-spacing 4px for brand
- Border radius: 40-44px for logo cards
- Animations: outerGlow scale 0.92->1.08, rotateGlow 0->360deg linear

## 6. Security Note
Admin is client-side, password is obfuscated in JS. For true security, move check to server, but for secret editing it's sufficient. Trigger is invisible.

## 7. Future Upgrades
- Add server-side auth
- Image compression on upload
- Drag to reorder gallery
- Direct S3 upload

