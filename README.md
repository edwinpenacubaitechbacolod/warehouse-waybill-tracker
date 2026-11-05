# Warehouse Waybill Tracker

GitHub Pages-ready static website for Bacolod Warehouse waybill monitoring.

## Routes
- DFC: Cebu → Bacolod (Incoming), Bacolod → Cebu (Outgoing)
- CAPEX: Manila → Bacolod (Incoming only)
- RADEX: Manila → Bacolod (Incoming only)

## Publish
1. Create a GitHub repository called `warehouse-waybill-tracker`.
2. Upload `index.html` to its root.
3. Under Settings → Pages, select Deploy from a branch, main, root.

## IMPORTANT: Enable real shared records and secure admin editing
The default app is **DEMO MODE ONLY**. Records are saved in the local browser and demo editor is not secure. Do not use it for real shared warehouse records.

1. Create a Firebase project, register a Web app and copy the `firebaseConfig` object.
2. Enable Firestore Database.
3. Enable Google sign-in in Firebase Authentication.
4. Sign in once with your designated admin Google account and copy its UID from Firebase Authentication → Users.
5. In `index.html`, replace `const firebaseConfig=null` with the web app config object and replace `ADMIN_UID` placeholder with that UID.
6. In `firestore.rules`, replace the UID placeholder with the SAME UID, and publish these rules under Firebase Console → Firestore Database → Rules.
7. Add your GitHub Pages domain to Firebase Authentication authorized domains if required.
8. Commit and push your updated index.html. Test as admin and in an incognito window as a viewer. Verify viewer cannot modify Firestore data.

Firebase web app config is public; security is enforced by Firestore rules, not by hiding frontend code. The site intentionally uses no shared hardcoded admin password.

## Notes
- The app supports manual pickup/receipt confirmation, **not** live courier API tracking.
- Export is CSV (opens in Excel), not styled XLSX.
- Records are grouped per waybill; no DR number is required.
- Read access is public once Firebase is enabled. Avoid personal/sensitive shipment information in remarks.
