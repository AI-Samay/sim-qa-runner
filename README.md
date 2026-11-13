# sim-qa-runner

Free iOS Simulator QA runner for Samay Vashsht's public Expo app repos.

- One manual workflow, **iOS Simulator QA** (`workflow_dispatch` only; pushing never starts it).
- Inputs: `repo` (a PUBLIC `owner/name`), `ref`, `flow_script`, `prepare_script`, `runner`.
- It checks out the target public repo, runs expo prebuild and pod install, builds a Release simulator app with ad-hoc signing, runs the app's own flow script, and uploads the screenshots and logs as an artifact.
- No secrets, no signing identity, no paid features. Private target repos are refused.

Contact: samayhuf@gmail.com
