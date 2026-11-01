# MY JARVIS Android starter

## Backend configuration

This Android app is configured to use the Render OpenJarvis service:

`https://openjarvis-server-w8pi.onrender.com`

The Brain chat uses the OpenAI-compatible OpenJarvis endpoint:

`POST /v1/chat/completions`

It sends `Authorization: Bearer <OPENJARVIS_API_KEY>` and requests the configured `gemini-2.5-flash` model.

After installing the APK:

1. Open **Settings** in MY JARVIS.
2. In Render Dashboard, open the `openjarvis-server` service → **Environment**.
3. Reveal and copy the value of `OPENJARVIS_API_KEY` on your own device. Do not paste it into chat, GitHub, screenshots, or public messages.
4. Paste it into **Render OPENJARVIS_API_KEY** in the app and tap **Save backend key**.
5. Open **Brain** and send a simple test message.

The key is saved in the app's private DataStore on this device. Do not publish it or commit it to source control. If it is exposed, rotate it in Render and update the app.

## Build

The GitHub Actions workflow `.github/workflows/android-build.yml` builds a debug APK with JDK 17 and Gradle 8.9. Upload this project ZIP to the MY-JARVIS repository (replace the existing starter ZIP if using the ZIP-based workflow), then run the Android build workflow. Download the `JARVIS-app-debug` artifact and install `app-debug.apk`.

## Current limitations

- Alexa OAuth / Smart Home Skill is not implemented in this starter and will need a separate integration.
- Voice HUD and automation screens need their own functional integration and device testing.
- Render free services can sleep when idle, so the first request may take longer while the service wakes.
