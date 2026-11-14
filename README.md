# Birthday Wishlists: deploy on Firebase (free)

Friends sign in with Google, then each person can edit only their own list. Everyone signed in can see all the lists.

## 1. Create the Firebase project (about 3 minutes)
1. Go to https://console.firebase.google.com → **Add project**. Analytics isn't needed.
2. **Build → Authentication → Get started → Sign-in method → Google → Enable → Save**
3. **Build → Firestore Database → Create database**. Pick a location near you (e.g. `europe-west`) and start in **production mode**.
4. **Project settings (gear icon) → Your apps → Web (</>)**. Register an app; you don't need Firebase Hosting ticked here.
   Copy the `firebaseConfig` values into `public/index.html` (search for `FIREBASE_CONFIG`).
   You only need `apiKey`, `authDomain`, `projectId` and `appId`.
   The config is safe to put in the page. The Firestore rules are what protect the data.

## 2. Deploy
```bash
npm install -g firebase-tools
firebase login
cd wishlist-site
firebase deploy --project YOUR_PROJECT_ID
```
This uploads the site and the security rules in `firestore.rules`.
You'll get a link like `https://YOUR_PROJECT_ID.web.app`. Send that to your friends.

## Updating later
Edit `public/index.html` and run `firebase deploy --project YOUR_PROJECT_ID` again.

## Hosting somewhere else (Netlify, Vercel, GitHub Pages)
You can upload just `public/index.html` there instead. Then add that site's domain under
**Authentication → Settings → Authorized domains**, or Google sign-in will fail.
Deploy the rules once with: `firebase deploy --only firestore:rules --project YOUR_PROJECT_ID`
