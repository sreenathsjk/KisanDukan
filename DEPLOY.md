 # Kisan Dukan — deploy checklist

Files: `index.html` (site), `firestore.rules`, `vercel.json` (optional security headers).

## 1. Firebase (5 min)
1. Firebase Console → create project → add a **Web app** → copy the config.
2. Open `index.html`, find `const firebaseConfig = {` (near the bottom) and replace every `YOUR_…` value.
3. Authentication → Sign-in method → enable **Email/Password** and **Anonymous**.
4. Authentication → Users → add your admin email + password → copy the **UID**.
5. Firestore → create database (production mode) → collection `admins` → document ID = that UID → field `role` = `admin`.
6. Firestore → Rules → paste `firestore.rules` → Publish.

## 2. Contact details
In `index.html` find `const SITE_CONTACT=` and fill `whatsapp` / `phone` / `email`
(digits with country code, e.g. `919876543210`). Leave blank and the Contact link scrolls to the Join section.

## 3. Host
- **Vercel:** put the 3 files in one folder → `vercel --prod` (or drag the folder into a new Vercel project).
- **Firebase Hosting / Netlify** also work. Must be HTTPS.

## 4. After you have the live URL (often missed)
Firebase Console → Authentication → Settings → **Authorized domains** → add your domain
(e.g. `yoursite.vercel.app`). Without this, registrations and admin login fail.

## 5. Test on a phone
Submit a farmer + buyer form → check they appear in Firestore `registrations` → open footer **Admin Panel**,
sign in, approve the farmer → open **Produce** and confirm the farmer shows publicly.

## 6. Recommended soon
- Firebase **App Check** (reCAPTCHA) to limit spam registrations.
- Anonymous sign-ins are not verified identities — add phone OTP before relying on registrations.
