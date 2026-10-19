# Smart White Cane Android app (GitHub Actions build)

This is a starter Android source project for the Smart White Cane HC-05 Bluetooth app.

## Features
- Connect to a paired HC-05 device
- Receive and display Bluetooth terminal text
- Night Mode ON sends `N`
- Night Mode OFF sends `n`
- Lock System sends `L`
- Clear terminal
- SOS button sends `S` (optional; remove if your Arduino does not implement it)

## Important hardware notes
- Pair HC-05 in Android Bluetooth settings first (common PINs are 1234 or 0000, depending on module).
- This app uses Bluetooth Classic SPP, suitable for HC-05.
- Your Arduino sketch must read single-character commands from the HC-05 serial connection.
- If HC-05 is wired to Arduino UNO pins D0/D1, disconnect the module while uploading the Arduino sketch. Avoid using Serial Monitor while the module occupies the hardware serial pins.
- SOS only sends `S`; it does NOT automatically call emergency services or share GPS location.
- A smart cane is an assistive prototype, not a replacement for a conventional mobility aid. Test with supervision before relying on it.

## Build APK using GitHub Actions (no Android Studio on your Windows 7 PC)
1. Create a new GitHub repository, e.g. `SmartWhiteCane`.
2. Upload all files/folders in this project to the repository (keep folder structure).
3. Open the repository's **Actions** tab and enable Actions if asked.
4. Select workflow **Build Smart White Cane APK** and click **Run workflow**.
5. Wait for the run to finish successfully.
6. Open that run and download the `SmartWhiteCane-debug-apk` artifact.
7. Extract the ZIP to get `app-debug.apk`.

The workflow builds with Java 17 and Android SDK on GitHub-hosted Ubuntu runners. No Google Drive upload is performed.

## Compatibility
- Minimum Android version: Android 6.0 (API 23).
- Bluetooth connection requires location/Bluetooth permissions appropriate to the Android version.
- This is an unsigned debug APK for testing, not a Play Store release.
