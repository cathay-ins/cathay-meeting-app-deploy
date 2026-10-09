# Cathay Meeting distribution

This repository publishes the internal Cathay Meeting download page through
[GitHub Pages](https://cathay-ins.github.io/cathay-meeting-app-deploy/). It
provides installation links for iPhone/iPad and Android.

## Current distribution

- **iOS:** the download page opens the iOS installation manifest. The manifest
  points to `CathayMeeting.ipa`, which is currently small enough to remain in
  the repository.
- **Android:** the download page links to the
  [v2.0 GitHub Release](https://github.com/cathay-ins/cathay-meeting-app-deploy/releases/tag/v2.0).
  The APK is stored as a release asset, not in Git.

## Publish a new Android build

1. Create a GitHub Release with the app version as its tag.
2. Upload the APK as a release asset.
3. Update the Android download button to the asset's direct download URL:

   ```text
   https://github.com/cathay-ins/cathay-meeting-app-deploy/releases/download/<tag>/<apk-file>
   ```

4. Commit and push the page update to `main`.
5. Wait for GitHub Pages to finish rebuilding, then test the button on an
   Android device.

## Publish a new iOS build

1. Replace the IPA and update the iOS manifest metadata to match the new app
   version and bundle identifier.
2. Commit and push the manifest and download-page changes to `main`.
3. Open the download page on an iPhone or iPad and choose **Install on
   iPhone/iPad** to test the installation flow.

If an IPA exceeds GitHub's 100 MB file limit, upload it to the matching GitHub
Release instead of committing it. Then replace the manifest's
`software-package` URL with that release asset's direct download URL.

## Release checklist

- Use HTTPS for every manifest and release-asset URL.
- Keep the download-page version, GitHub Release tag, and app version aligned.
- Do not commit APK or IPA files larger than 100 MB.
- Confirm the GitHub Release asset has uploaded before publishing its link.
- Verify the GitHub Pages deployment and install path on the intended device.
