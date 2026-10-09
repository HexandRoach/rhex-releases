# Rhex releases

Official downloads and release notes for Rhex, a local-first Linux AI assistant developed by Hex & Roach.

Rhex is alpha software intended for testing.

## Current release

0.7.0-alpha.9 — Linux x86_64

[Download Rhex alpha.9](https://github.com/HexandRoach/rhex-releases/releases/tag/v0.7.0-alpha.9)

Under Assets, download `rhex_0.7.0-alpha.9_amd64.AppImage`.

Windows, macOS, and ARM builds are not provided here. Automatically generated Source code archives are not application installers. You do not need `latest.json` or the `.sig` file just to launch Rhex.

## First launch

If Rhex is already running, select Quit Rhex from its tray menu first.

Assuming the downloaded file is in your Downloads folder:

```bash
cd ~/Downloads &&
chmod +x rhex_0.7.0-alpha.9_amd64.AppImage &&
WEBKIT_DISABLE_DMABUF_RENDERER=1 \
  ./rhex_0.7.0-alpha.9_amd64.AppImage
```

Downloading the AppImage does not automatically create an application-menu entry. A standalone launcher installer is planned.

Keep the AppImage in a writable location so the updater can replace it. Keep a backup of important conversations through the export controls.

## Local chat setup

Local chat and workflows require Ollama and the model requested by Rhex. Follow the setup instructions inside the application if the local service or model is unavailable.

Rhex does not automatically install or start Ollama. Initial installation and model downloads require internet access and local storage. The endpoint and configured model remain fixed; no selector is provided. Local inference does not by itself prove network isolation.

## Release history — newest first

### 0.7.0-alpha.9 — Pasted-text workflows

- Adds a Workflows page for summarization and explicit-task extraction using the same configured Ollama endpoint and model as local chat.
- Requests structured results and validates them before display.
- Requires supporting quotations to match the submitted text.
- Requires task owners and deadlines to appear in their supporting quotation, or remain unspecified.
- Keeps workflow input and results separate from saved conversations.
- Adds source preview, manual result copying, and a review warning.
- Adds a 12,000-byte UTF-8 input limit, loading states, and readable errors.
- Clears stale results when the source changes and preserves workflow state across navigation.
- Blocks update installation while a workflow request or result copy is busy.

Matching quotations show that quoted text exists in the source, not that the model interpreted it correctly. Results may omit information and require review. Workflows accept pasted text; there is no file import or workflow PDF export. Extracted tasks are not executed.

### 0.7.0-alpha.8 — Local-model status and diagnostic summaries

- Displays the fixed Ollama endpoint, configured model, and app version.
- Adds a previewable diagnostic summary and manual clipboard copying.
- Summaries exclude conversation text, credentials, local file paths, and raw error messages.
- Distinguishes a failed model-list check from a confirmed missing model.
- Offers retry after model-list failure and blocks model downloads until a successful check.
- Matches the exact configured model name.

Status results are snapshots, not continuous monitoring. Model listing does not test generation or prove network isolation. Diagnostic summaries are not desktop scans or protection tools.

### 0.7.0-alpha.7 — Setup wording and assistant grounding

- Corrected local Ollama setup documentation and unavailable-service wording.
- Improved assistant instructions about unverified commands, product capabilities, public distribution, and network-isolation claims.
- Added a manual grounding-test record documenting improvements and failures.

Assistant replies can still contain unsupported claims or contradictory corrections, especially after misleading conversation history. Review answers before acting on them.

### 0.7.0-alpha.6 — Update restart and operation guards

- Added a confirmed Restart now action after successful update installation.
- Kept the update panel mounted when switching pages.
- Added update-busy protections for navigation, shortcuts, and conflicting Settings actions.
- Added a tray Quit guard during update installation.

The published alpha.5 does not have Restart now. After updating from alpha.5, fully quit through the tray menu and reopen manually. The restart action is available for subsequent updates installed while running alpha.6 or later.

### 0.7.0-alpha.5 — Local Activity history and updater improvements

- Records application starts and successful conversation creation, rename, and deletion.
- Records model-download and update outcomes using fixed summaries.
- Does not record chat text, conversation titles, file paths, or raw error details.
- Displays the newest 200 events and retains at most 1,000.
- Removes events older than 30 days when Activity storage is accessed.
- Clearing Activity history does not delete conversations.
- Preserves update status when switching tabs.
- Blocks sidebar navigation, app shortcuts, and other Settings actions during update operations.
- Blocks tray Quit while alpha.5 performs an update installation.
- Requires confirmation before downloading and installing an update.

Activity is an operational history, not a tamper-proof audit log. Update guards do not prevent forced termination, system shutdown, or power loss.

## Updating Rhex

In an updater-enabled build:

1. Open Settings.
2. Select Check for updates.
3. Review the available version and release notes.
4. Select Download and install and approve the confirmation.
5. Wait for successful installation.
6. Use Restart now if offered and approve its confirmation.
7. If no restart action is available, select Quit Rhex from the tray menu and reopen the same AppImage or your installed launcher.

Closing the window only hides Rhex; it does not fully quit the application.

The AppImage filename may retain an older version number after updating. Check Running version in Settings to identify the version actually running.

Builds that predate the updater, including alpha.2, require a manual download of an updater-enabled release.

If an update check fails or offers no newer release unexpectedly, report the exact message and your running version.

## Testing status

Completed on the release builder's Linux machine:

- Alpha.8 → alpha.9 in-app update and restart, with conversations preserved.
- Fresh local chat and workflow execution with copying after the alpha.9 updater restart.
- Alpha.9 packaged launch, fresh local chat, summarization, task extraction, manual copying, and conversation preservation after reopening.
- Alpha.9 downloaded-artifact checksum and independent Minisign signature verification.
- Unauthenticated downloads of the published alpha.9 AppImage and signature, matching their expected SHA-256 values.
- Alpha.7 → alpha.8 in-app update and restart, with conversations preserved and diagnostic copying working.

Alpha.9 development validation also passed all eight Rust unit tests, TypeScript compilation, the Vite production build, and live workflow checks.

The alpha.6 restart test used a patched test build to install the signed alpha.6 AppImage; it is not confirmation of the unmodified published alpha.5 upgrade path.

Still pending or not confirmed by the available records:

- Workflow failure-state and clipboard-failure handling.
- Input-size boundaries and additional malformed-result validation tests.
- Separate-machine and additional Linux-distribution testing, including Arch.
- Packaged Ollama-unavailable setup/clipboard behavior.
- Dedicated model-download outcome logging tests.
- Earlier alpha.4 → alpha.5 upgrade and published alpha.5 guard validation.

Builder-machine results do not establish compatibility with every Linux distribution.

## Download security

Use the official Releases page linked above.

The in-app updater verifies signed update artifacts. A manually downloaded AppImage is not automatically signature-verified merely because a `.sig` file is attached to the release.

Alpha.9 AppImage SHA-256:

```text
0552c4dbee2db132e745a2a4c1c59891d9ca6f52ce1efd1089d6a4e582440e5d
```

A checksum comparison is not a substitute for independent signature verification. Never share passwords, signing keys, or private conversation content in reports.

## Reporting issues

Report issues through the Discord tester channel. Include:

- Running Rhex version from Settings.
- Linux distribution and version.
- How you launched Rhex.
- Steps to reproduce the issue.
- Exact error text.
- Whether local chat and workflows work.
- Whether conversations remain after fully quitting and reopening.

Review diagnostic summaries before copying or sharing them. Do not include private workflow source text, chats, passwords, or signing keys.

## Arch Linux testing

The Linux x86_64 AppImage is available for Arch Linux users to test. Arch compatibility has not yet been confirmed by a tester. A separate native Arch package is not currently provided.

### Download and launch

Download `rhex_0.7.0-alpha.9_amd64.AppImage` from the alpha.9 release Assets. Use the First launch commands above and run Rhex as your normal user, not with sudo.

### Missing FUSE dependency

Only if launching reports `libfuse.so.2` missing or an error requiring FUSE, run this on the Arch computer:

```bash
sudo pacman -Syu --needed fuse2
```

This command also performs a system upgrade. Review the package transaction before confirming, then try launching Rhex again. If Rhex already launches, skip this step.

### Please report your results

Send feedback through the Discord tester channel, including:

- Arch Linux or derivative distribution name.
- Desktop environment and whether you use Wayland or X11.
- Running Rhex version shown in Settings.
- Whether the application opens and local chat and workflows work.
- Whether conversations remain after quitting and reopening.
- Whether Activity and tray controls work.
- Whether Check for updates completes.
- Exact terminal errors if anything fails.

Do not include private chats, workflow source text, passwords, or signing keys.
