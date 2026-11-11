# Daily Notes — mobile-build starter

## Build an APK using only an Android phone
1. Download and extract this ZIP using a file manager.
2. In a browser, sign in to GitHub and create a new **private** repository named `daily-notes-android`.
3. Upload the extracted project files and folders to the repository root (including the hidden `.github` folder). Commit to `main`.
4. Open the repository's **Actions** tab. If prompted, enable GitHub Actions.
5. Open **Build Daily Notes APK** and wait for the workflow to finish successfully.
6. Open the completed workflow run, download the `Daily-Notes-debug-APK` artifact, extract it, then tap `app-debug.apk` to install.

## What this build contains
- Initial Android app screen and 4-digit PIN gate.
- A Daily Notes button placeholder.
- Firebase Messaging receiver source code, ready for later backend integration.

## Important limitations
- This APK is only a UI/prototype. The remote pairing, authenticated signal sending, and real partner-to-partner vibration are NOT connected yet.
- A real, consent-based Firebase backend and Firebase app configuration must be added before remote vibration can work.
- Android background delivery is best-effort; battery restrictions and force-stop can prevent delivery.
- Do not share this APK publicly yet. Test privately with both users' knowledge and consent.
- The starter PIN is a prototype and should be upgraded to secure storage before release.


## Chat features added in this prototype
- Chat screen with text composer.
- Photo picker using Android document picker.
- Voice recording with runtime microphone permission.
- Clear demo labels: text/photo/voice are local-only in this version.

## Still required for real partner-to-partner chat
- Firebase Authentication and Firestore for paired chat messages.
- Firebase Storage (or another secure media store) for photo and audio uploads.
- Cloud security rules restricting access to the two paired, consenting accounts.
- Push notifications are optional and must be user-configurable.
- End-to-end encryption is not implemented in this starter; do not use it for sensitive conversations until security review is completed.


## Remote Delete prototype added
- The home screen now includes a Remote Delete / Privacy entry.
- The new screen includes an explicit local consent switch and a delete-request UI.
- This is currently a **UI prototype only**. It does not send a request to the partner phone and does not delete remote data.
- To activate real remote deletion safely, configure Firebase Authentication for both people, mutually verified pairing, Firestore security rules that restrict requests to the paired accounts, and partner-side request handling that checks the partner's prior opt-in before deleting only app-owned data.
- The partner's phone must eventually connect to receive a pending request. Do not claim deletion succeeded until that phone confirms completion.
- This cannot remove Android system logs, screenshots, screen recordings, externally saved copies, or data held by third parties.
