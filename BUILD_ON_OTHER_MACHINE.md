# PolriBWC Build Repo

Repo ini adalah salinan bersih dari `Polri-BWC` yang difokuskan untuk build APK di mesin lain.

## Tujuan

- clone repo ini di mesin lain
- jalankan build APK `Flutter`
- hindari file runtime server lokal yang tidak relevan untuk Android build

## Yang sengaja dibersihkan

- `.git/`
- `build/`
- `.dart_tool/`
- `.flutter-plugins-dependencies`
- `server/server.pid`
- `server/server.log`
- `server/data/state.json`
- `out/`

## Build APK

### Opsi 1: Flutter host

```bash
git clone <repo-ini>
cd PolriBWC-build-repo

export ANDROID_HOME=/path/ke/android-sdk
export ANDROID_SDK_ROOT=/path/ke/android-sdk
export JAVA_HOME=/path/ke/jdk17
export PATH=/path/ke/flutter/bin:/path/ke/flutter/bin/cache/dart-sdk/bin:$ANDROID_SDK_ROOT/platform-tools:$PATH

flutter pub get
flutter build apk --debug
```

APK debug:

```bash
build/app/outputs/flutter-apk/app-debug.apk
```

### Opsi 2: GitHub Actions

Repo ini sudah membawa workflow:

```text
.github/workflows/build-apk.yml
```

Push ke GitHub, lalu unduh artifact `polri-bwc-debug-apk` dari tab `Actions`.

## File penting untuk build

- `pubspec.yaml`
- `pubspec.lock`
- `lib/`
- `android/`
- `.github/workflows/build-apk.yml`
- `scripts/build_apk_docker.sh`
- `docker/apk-builder.Dockerfile`

## Catatan

- Patch PTT diagnostik sudah termasuk.
- Build APK tidak membutuhkan server backend lokal untuk berhasil.
