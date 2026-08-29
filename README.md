# SciMaster — Physics & Chemistry Study App (Android, Kotlin + Jetpack Compose)

An offline-first study companion for Intermediate Physics and Chemistry students —
formula bank, short tricks, lab calculators, study games, motivation content, and
bookmarks, built entirely with modern Android tooling.

## Features
- **Physics & Chemistry formula bank** with organized topic browsing
- **Lab Calculators** for common physics/chemistry computations
- **Study Games & Quizzes** to reinforce learning
- **Bookmarks** — save any topic for later, persisted locally with Room
- **Motivation screen** — short study tips and encouragement
- Clean bottom-navigation structure across Home, Physics, Chemistry, Games,
  Lab Calculators, and Bookmarks
- 100% offline — no backend or network dependency required to run
- Built entirely with **Jetpack Compose** and **Material 3**

## Tech Stack
- Kotlin
- Jetpack Compose (Material 3)
- Navigation Compose
- Room (local persistence for bookmarks)
- ViewModel + StateFlow (MVVM architecture)
- Kotlin Coroutines

## Requirements
- Android Studio (latest stable — Ladybug or newer recommended)
- JDK 11+
- Android SDK 36 (compileSdk / targetSdk), minSdk 24
- Gradle Wrapper included — no local Gradle install required

## Getting Started
1. Extract the project archive.
2. Open the project root folder in Android Studio (`File > Open`).
3. Let Gradle sync (the Gradle Wrapper will download Gradle 9.3.1 automatically).
4. Run on an emulator or physical device (`Run > Run 'app'`).

To build from the command line instead:
```
./gradlew assembleDebug      # macOS/Linux
gradlew.bat assembleDebug    # Windows
```

## Project Structure
```
app/src/main/java/com/mazbahstudios/scimaster/
├── data/            Room database, DAO, entities (bookmarks persistence)
├── model/           Static repository data (Physics, Chemistry, Quiz, Motivation)
├── ui/
│   ├── components/  Shared reusable Compose components
│   ├── screens/     Home, Physics, Chemistry, Games, Lab Calculators,
│   │                Bookmarks, Motivation screens
│   └── theme/       Color, typography, and Material 3 theme definitions
├── viewmodel/       MainViewModel, GameViewModel, LabCalculatorViewModel
└── MainActivity.kt  App entry point + bottom navigation
```

## Customization
- **App name**: update `app_name` in `app/src/main/res/values/strings.xml`
- **Package name / Application ID**: update `namespace` and `applicationId`
  in `app/build.gradle.kts`
- **App icon**: replace the images in `app/src/main/res/mipmap-*`
- **Colors & theme**: edit `app/src/main/java/.../ui/theme/Color.kt` and `Theme.kt`
- **Content**: all formulas, quizzes, and motivational content live in
  `app/src/main/java/.../model/` as plain Kotlin data — easy to extend or replace
  for a different subject.

## Notes
- The project ships with a release signing config that reads
  `KEYSTORE_PATH` / `STORE_PASSWORD` / `KEY_PASSWORD` environment variables
  (falls back to a local `my-upload-key.jks` if present). Generate your own
  keystore before producing a signed release build.
- No API keys, secrets, or backend services are required to build or run the app.
- Legacy (pre-Android 8.0) launcher icons were regenerated from the app's
  actual adaptive-icon art — the originally shipped `mipmap-*/ic_launcher.webp`
  files were corrupted placeholders and have been replaced with valid PNGs.

## Marketplace Upload Assets
`codester-assets/` contains images sized for the Codester item listing form
(not part of the installable app):
* `codester-icon.png`           -> Item icon field          (200 x 200 px)
* `codester-preview-image.png`  -> Item preview image field  (1600 x 800 px, 2x for retina)

## Building a Demo APK (no Android Studio required)
This project includes a GitHub Actions workflow
(`.github/workflows/build-apk.yml`) that builds a debug APK in the cloud —
useful if your machine doesn't have room for Android Studio locally.

1. Push this project to a GitHub repository.
2. Go to the repo's **Actions** tab. If prompted, click "I understand my
   workflows, go ahead and enable them".
3. Select **Build Debug APK** in the left sidebar, then click
   **Run workflow** (top right) to trigger it manually. It also runs
   automatically on every push to `main`.
4. Wait for the run to finish (a few minutes).
5. Open the completed run, scroll to **Artifacts**, and download
   `scimaster-debug-apk` — this is a zip containing `app-debug.apk`.
6. Upload that APK to Google Drive (or any file host), set sharing to
   "Anyone with the link", and use that link as your Codester demo APK link.
