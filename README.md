# Waterfall1

Android project with pre-installed CI tooling.

## Status

This repository currently contains **only the automated build infrastructure**.  
Drop your Android Studio project files into the root and the GitHub Actions pipeline will pick them up and build a debug APK on every push / PR to `main`.

## What the CI does

- Sets up JDK 17 + Android SDK
- Caches Gradle dependencies aggressively
- Runs `./gradlew assembleDebug`
- Uploads the resulting debug APK as a workflow artifact (available for 14 days)

## How to use

1. Create a new project in Android Studio (or open an existing one).
2. Make sure the project root contains:
   - `gradlew` / `gradlew.bat`
   - `settings.gradle.kts` (or `.gradle`)
   - `app/` module
3. Push everything to this repository.
4. The workflow will automatically build and produce an APK artifact.

## Notes

- The workflow is intentionally tolerant: if no `gradlew` is present yet, it exits cleanly instead of failing.
- Once you add real source code, subsequent builds will be significantly faster thanks to Gradle caching.
