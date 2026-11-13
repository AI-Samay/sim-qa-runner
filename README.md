# sim-qa-runner

Free iOS Simulator QA runner for Samay Vashsht's public Expo app repos.

- One manual workflow, **iOS Simulator QA** (`workflow_dispatch` only; pushing never starts it).
- Inputs: `repo` (a PUBLIC `owner/name`), `ref`, `flow_script`, `prepare_script`, `runner`.
- It checks out the target public repo, runs expo prebuild and pod install, builds a Release simulator app with ad-hoc signing, runs the app's own flow script, and uploads the screenshots and logs as an artifact.
- No secrets, no signing identity, no paid features. Private target repos are refused.

Contact: samayhuf@gmail.com

## iOS Local Build (`.github/workflows/local-ios-build.yml`)

- Manual only. Runs `eas build --local` on a free hosted macOS runner, so no Expo Build credits are used (EAS only supplies the managed signing credentials and the remote build number).
- Inputs: `repo`, `ref`, `profile` (default `production`), `app_dir`, `build_number` (optional override), `upload` (true uploads the IPA to App Store Connect with `xcrun altool` and the ASC API key), `xcode_version`, `node_version`.
- Never runs a cloud `eas build` or `eas submit`.
- Secrets (repo secrets, never printed): `EXPO_TOKEN`, `ASC_KEY_ID`, `ASC_ISSUER_ID`, `ASC_KEY_P8`; optional `CHECKOUT_TOKEN` for private targets.
- The IPA and logs are kept as an artifact for 3 days.
