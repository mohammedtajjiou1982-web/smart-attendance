# Smart Attendance QR — Android project

## Current implementation
- Arabic RTL interface
- Student add/edit/delete/search
- Daily attendance: one successful attendance record per student per date
- Duplicate and unknown-code warnings with audio tones
- Attendance history by date, CSV export, print view
- Student CSV import/export
- JSON backup and restore
- LocalStorage persistence (on the same app installation/device)

## Important build notes
This ZIP contains the complete web application source and Capacitor project configuration. The Android native wrapper must be generated and built on a computer with Node.js, Android Studio, Android SDK and JDK installed. An APK has **not** been built in this environment.

## Build on Windows
1. Install Node.js LTS and Android Studio.
2. Extract this folder.
3. Open PowerShell in this folder and run:
   ```powershell
   npm install
   npx cap add android
   npx cap sync android
   npx cap open android
   ```
4. In Android Studio, allow Gradle sync and install the Android SDK components it requests.
5. Connect an Android phone with USB debugging enabled, or use an emulator, then press Run.
6. To create an APK: Android Studio > Build > Build Bundle(s) / APK(s) > Build APK(s). The debug APK is usually under `android/app/build/outputs/apk/debug/app-debug.apk`.

## Camera / QR notes
- In a normal browser, QR camera scanning uses the browser's BarcodeDetector API and requires camera permission plus a secure origin (HTTPS or localhost).
- In the generated native Android wrapper, camera availability and permissions should be verified on the target phone. This starter includes Capacitor camera and community barcode scanner dependencies in package.json, but the current web scanner uses BarcodeDetector. Native plugin integration and device testing are required before production release.
- QR card rendering uses QRCode.js from a CDN. First-time QR generation therefore requires internet access. To make the entire application fully offline, vendor a QR generation library into `www/` and integrate native scanning plugin before release.

## Data warning
LocalStorage data belongs to this app installation on this device. Clearing app data or uninstalling the app may delete it. Use the JSON backup regularly and copy backups to a safe location.
