# WorldChat: setup (about 15 minutes)

You need a free Google account. No coding required.

## 1. Create the Firebase project
1. Go to https://console.firebase.google.com and click **Add project**. Name it anything.
2. In the left menu, open **Build → Authentication → Get started → Sign-in method**. Enable **Anonymous**.
3. Open **Build → Firestore Database → Create database**. Choose **production mode** and a region close to your users.
4. In Firestore, open the **Rules** tab. Replace everything with the contents of `firestore.rules` and click **Publish**.

## 2. Get your config
1. Project settings (gear icon) → **Your apps** → click the web icon `</>` → register an app.
2. Copy the `firebaseConfig` values (apiKey, authDomain, projectId, appId).
3. Paste them into the `firebaseConfig` block near the top of the script in `index.html`.

(The apiKey is not a secret. The security rules protect your data.)

## 3. Put it online
Easiest options, all free to start:
- **Firebase Hosting:** install the Firebase CLI, run `firebase init hosting` in this folder, then `firebase deploy`.
- **Netlify Drop:** drag this folder onto https://app.netlify.com/drop.
- **Cloudflare Pages / Vercel / GitHub Pages** also work.

In Firebase **Authentication → Settings → Authorized domains**, add your site's domain.

## 4. Before you share it widely
- **Moderation:** reported messages appear in Firestore under `reports`. Delete bad messages in the Firebase console (Firestore → rooms → messages). Check this regularly.
- **Spam and abuse:** turn on **Firebase App Check** (Build → App Check) to block bots. The page has a 2-second cooldown, but that can be bypassed, so App Check matters.
- **Costs:** the free tier has daily read and write limits. A viral site can exceed them. Set a **budget alert** in Google Cloud and consider limits on how many messages each room loads.
- **Safety and law:** public chat with strangers can attract abuse and minors. Add Terms and a Privacy Policy, and check the rules where you operate (for example GDPR in the EU, which includes Denmark).
- **Content filtering:** this version has no word filter or translation. Both can be added later.
