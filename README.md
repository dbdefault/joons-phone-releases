# JOONS Phone Releases

Update channel for **JOONS Phone**, the Android companion app of the [JOONS](https://github.com/dbdefault/joons-ecosystem) agent system.

This repository contains **no source code, keys or connection settings** – only signed release builds. The app checks this repository for updates and installs them in place.

## How the update check works

1. The app reads `manifest.json` from the [latest release](https://github.com/dbdefault/joons-phone-releases/releases/latest).
2. If `version_code` is higher than the installed one, it downloads `JOONS_Phone.apk` from the same release.
3. The manifest also carries the file size and SHA-256, so any download can be checked against it. Android itself refuses an in-place update signed with a different certificate.

## Release contents

Every release has exactly two assets:

| File | Purpose |
|---|---|
| `JOONS_Phone.apk` | The signed app build |
| `manifest.json` | Version and integrity data for the update check |

Example `manifest.json`:

```json
{
  "package_name": "com.joons.agent",
  "version_code": 66,
  "version_name": "0.6.10",
  "size": 1495635,
  "sha256": "957a6f516adeb5be98315289468ad6fae1ec03a08633fe74b01664aa535deda2"
}
```

## Verify a download yourself

```sh
# Linux / macOS
sha256sum JOONS_Phone.apk

# Windows PowerShell
Get-FileHash JOONS_Phone.apk -Algorithm SHA256
```

The hash must match `sha256` in the `manifest.json` of the same release.

## Scope and limits

- The app is a personal tool built for one specific multi-PC setup; it is published here only so devices can update themselves.
- There is no support for other environments, and issues or pull requests are not expected.
- Older releases are kept for rollback; only `releases/latest` is used by the app.

---

## 한국어 요약

쥰스 폰 앱의 온라인 업데이트 전용 공개 저장소입니다. 앱은 최신 릴리스의 `manifest.json`과 `JOONS_Phone.apk`만 읽습니다. manifest에는 파일 크기와 SHA-256 값이 들어 있어 내려받은 파일을 대조할 수 있습니다. 이 저장소에는 소스, 키, 연결 정보를 두지 않습니다.
