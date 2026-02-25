# Install and Download APK

This repository includes a GitHub Actions workflow that builds a debug APK and uploads it as an artifact.

How to get the APK (artifact):

- Push changes to the `main` branch or run the workflow manually in the Actions tab.
- When the run completes, open the run and download the artifact named `app-debug-apk`.

Install the APK on an Android device:

1. Enable USB debugging on your device and connect it.
2. Download the artifact and extract the APK (the artifact contains `app-debug.apk`).
3. Run:

```bash
adb install -r app-debug.apk
```

Build locally (optional):

- Install JDK 17 and Android SDK (platform-tools, build-tools and platforms for API 33).
- Create `local.properties` in the repo root with:

```
sdk.dir=/path/to/android-sdk
```

- Build using the Gradle wrapper (or `gradle` if you have system Gradle):

```bash
./gradlew assembleDebug
# or
gradle assembleDebug
```

The debug APK will be at `app/build/outputs/apk/debug/app-debug.apk`.

Notes:
- The repository currently produces a debug APK (unsigned for release). For Play Store or release distribution, generate a keystore and sign the release APK.
- If you prefer, you can run the workflow manually via the Actions tab and download the artifact without running anything locally.
