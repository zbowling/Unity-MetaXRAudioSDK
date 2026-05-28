# Agent Instructions — Unity Meta XR Audio SDK Samples

Unity project demonstrating Meta's Presence Platform Audio SDK (spatialization, room acoustics, ambisonics, directivity) for Meta Quest.

## Source-of-truth files (read these first, do not duplicate their contents in this file)

For setup, build steps, SDK versions, and project layout, read:

- `README.md` — official setup, build, and run instructions
- `MetaXRAudioSDK/ProjectSettings/ProjectVersion.txt` — Unity editor version
- `MetaXRAudioSDK/Packages/manifest.json` — Unity package versions (Meta XR Audio SDK via UPM)
- `LICENSE` (Oculus SDK License) and `THIRD_PARTY_NOTICES.txt` / `third-party/` — third-party audio sample attributions

## Quest / Horizon-specific notes

- The actual Unity project lives under `MetaXRAudioSDK/`, not the repo root — open that subdirectory in the Unity Editor.
- Each scene's audio behavior is best evaluated in playmode over Oculus Link (per README) so headset audio output mirrors what end users will hear; speakers / desktop output will not reproduce spatialization correctly.
- Look in the **Main** scene of the `MetaXRAudioSDK/` project for the entry-point used to cycle through the feature demonstrations.
- After installing the APK via `adb install`, the app appears under the Quest's **Unknown Sources** section in the App Library.
- Repository is under the **Oculus SDK License**, not MIT — preserve license headers when refactoring.

## Meta Quest tooling

This repository is part of the Meta Quest / Horizon OS ecosystem (a sample, library, template, or related project — the bespoke intro above describes which). Use that intro and the source-of-truth files it references for project-specific decisions; don't restate or invent facts from memory.

When the user asks anything about Quest device behavior, build / deploy / debug / capture flows, on-device performance, or Horizon OS APIs, reach for these tools instead of generic Unity answers:

- **`hzdb`** — Quest-aware ADB wrapper (device list, install / launch / stop, logs, screenshots, Perfetto traces, on-device docs search). Already wired up as an MCP server via `.mcp.json`, `.vscode/mcp.json`, and `.cursor/mcp.json`. Also runnable directly: `npx -y @meta-quest/hzdb <subcommand>`.
- **Meta Quest Agentic Tools** — the full skill set, including Unity-specific skills: [github.com/meta-quest/agentic-tools](https://github.com/meta-quest/agentic-tools). Install per your client (Claude Code: `/plugin install meta-vr@meta-quest`; Gemini CLI: `gemini extensions install https://github.com/meta-quest/agentic-tools`; Cursor / VS Code: install the **Meta Horizon** extension from the Marketplace).

A few behavior expectations:

- **Read this repo's files first.** Before answering anything project-specific, read `README.md` and whichever source-of-truth files the intro above points at. Don't restate their contents in chat — quote or link instead.
- **Use `hzdb` for device-side work.** Anything that touches an attached Quest (install, launch, logs, screenshot, capture, manifest inspection) goes through `hzdb`, not raw `adb`.
- **Check live Horizon OS docs before answering API questions.** `hzdb docs search "..."` queries the live docs; training data on Horizon OS APIs goes stale fast.
- **Don't fabricate SDK / engine versions.** If a version isn't visible in this repo's files, say so rather than guessing.
