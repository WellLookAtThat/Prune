# Getting Prune live — step by step

Two things to do: (1) connect real login, (2) put the site on a real URL. About 10-12 minutes total, no coding — just copy-pasting values into one file.

---

## Step 1 — Create a free Firebase project (5 min)

Firebase is Google's backend-as-a-service. It gives you real user accounts and a real database without you running a server.

1. Go to **console.firebase.google.com** → sign in with any Google account → **Add project**.
2. Name it (e.g. "prune-app") → skip Google Analytics if asked → **Create project**.
3. In the left sidebar: **Build → Authentication → Get started**.
   - Click **Email/Password** → enable it → Save.
   - Click **Google** → enable it → pick a support email → Save.
4. In the left sidebar: **Build → Firestore Database → Create database** → choose **Start in test mode** → pick any location → **Enable**.
   *(Test mode is open access — fine while you're validating. Before a real public launch, tighten the rules under Firestore → Rules. Ask me when you're there.)*
5. Click the **gear icon** (top left, next to "Project Overview") → **Project settings**.
6. Scroll to **"Your apps"** → click the **`</>`** (web) icon → nickname it anything → **Register app**.
7. You'll see a code block with a `firebaseConfig` object — six lines like `apiKey: "AIza..."`. Copy the whole object.

## Step 2 — Paste it into the site (1 min)

1. Open `index.html` in any text editor.
2. Find `const firebaseConfig = {` (search for `PASTE_YOUR`).
3. Replace the placeholder object with the real one you copied, e.g.:
   ```js
   const firebaseConfig = {
     apiKey: "AIzaSyD...",
     authDomain: "prune-app-xxxx.firebaseapp.com",
     projectId: "prune-app-xxxx",
     storageBucket: "prune-app-xxxx.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:abc123"
   };
   ```
4. Save.

That's it — "Join the waitlist" now opens a real signup/login modal, creates real accounts, and stores each signup in Firestore under **Build → Firestore Database → users**, viewable any time in your Firebase console.

## Step 3 — Put it on GitHub Pages (5 min)

1. Go to **github.com** → sign in (free account if needed).
2. **+** (top right) → **New repository** → name it `prune-site` → keep **Public** → **Create repository**.
3. Click **uploading an existing file** → drag in `index.html` → **Commit changes**.
4. Repo → **Settings** tab → **Pages** (left sidebar).
5. **Source: Deploy from a branch** → branch **main** → folder **/ (root)** → **Save**.
6. Wait ~1 minute, refresh that page — your live URL appears:
   ```
   https://yourusername.github.io/prune-site/
   ```

**One extra Firebase step once it's live:** Firebase blocks logins from domains it doesn't recognize. In the Firebase console → **Authentication → Settings → Authorized domains → Add domain**, paste in `yourusername.github.io`.

---

## What's real right now

- Actual user accounts (email/password or Google sign-in) — this is a genuine, working login system.
- Signups are saved to a real database you own and can see.
- The particle field, glitch text, and laser-cut demo — all self-contained, work anywhere.

## What's still not built

There's no product behind the login yet — once someone signs in, there's nowhere further to go. That's next: a real dashboard is the natural following step once you've got people actually creating accounts. Payments are still deliberately out of scope, as agreed.
