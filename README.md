# Pyakha releases

Public Android release artifacts for Pyakha. Application source is maintained separately.

`Pyakhah-release.apk` and `update.json` are a matching pair. The manifest records the APK's
version, size and SHA-256 checksum. Always regenerate it after rebuilding the APK.

## Local repository

This repository lives in the application's `release/` folder. The parent source repository
ignores that folder; each repository has its own history and remote.

Build and prepare the artifacts from the parent project:

```sh
npm run android:release
npm run android:update -- --notes-file /path/to/release-notes.txt
```

Then commit and push the artifacts from this folder:

```sh
git add Pyakhah-release.apk update.json
git commit -m "Update release artifacts"
git push
```

## Publish an app update

A Git push saves these files but does not create a GitHub Release. In this repository's
Releases section, create a release tagged `v<versionName>` (initially `v2.0.52`), attach both
`Pyakhah-release.apk` and `update.json`, and publish it as the latest stable release.

The app checks:

https://github.com/saroj-mhrn/Pyakha-release/releases/latest/download/update.json

The APK download address in `update.json` must match the release tag and attached file name.
Users need to install the build configured for this channel once before receiving future
updates through the app.
