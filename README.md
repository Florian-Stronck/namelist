# Guest check-in

Mobile page: search a guest list, tap a name to strike it out. Synced live between phones with Firebase Realtime Database. No sign-in needed for guests/co-hosts, just the link.

## Setup (about 10 minutes, free)

1. **Firebase project**: https://console.firebase.google.com -> Add project (disable Analytics).
2. **Web app config**: Project settings (gear) -> General -> "Your apps" -> `</>` Web -> register. Copy the `firebaseConfig` values into `config.js`.
3. **Database**: Build -> Realtime Database -> Create database (pick a region, "Start in test mode"). Copy its URL into `databaseURL` in `config.js` (looks like `https://xxx-default-rtdb.europe-west1.firebasedatabase.app`).
4. **Rules** (Realtime Database -> Rules), so only the guest list is open:
   ```json
   { "rules": { "guests": { ".read": true, ".write": true } } }
   ```
   Anyone with the link can edit the list. Delete the Firebase project after the party.
5. **Host**: GitHub repo -> Settings -> Pages -> deploy from branch, folder `/ (root)`. Open the Pages URL on every phone.
6. First open: tap **Load the saved guest list** (from `guests.js`), or paste names in Setup.

`claude-artifact.html` is the earlier version that syncs only for signed-in Claude users.
