# Rhex releases

Official downloads and release notes for Rhex, a local-first Linux AI assistant
developed by Hex & Roach.

Rhex is alpha software intended for testing.

## Current release

**0.7.0-alpha.5 — Linux x86_64**

[Download Rhex alpha.5](https://github.com/HexandRoach/rhex-releases/releases/tag/v0.7.0-alpha.5)

Under Assets, download:

`rhex_0.7.0-alpha.5_amd64.AppImage`

Windows, macOS, and ARM builds are not provided here.

The automatically generated Source code archives are not application installers.
You do not need `latest.json` or the `.sig` file just to launch Rhex.

## First launch

If Rhex is already running, select Quit Rhex from its tray menu first.

Assuming the downloaded file is in your Downloads folder:

```bash
cd ~/Downloads &&
chmod +x rhex_0.7.0-alpha.5_amd64.AppImage &&
WEBKIT_DISABLE_DMABUF_RENDERER=1 \
  ./rhex_0.7.0-alpha.5_amd64.AppImage
```

Downloading the AppImage does not automatically create an application-menu entry.
A standalone launcher installer is planned.

Keep the AppImage in a writable location so the updater can replace it.
Keep a backup of important conversations through the export controls.

## Local chat setup

Local chat requires Ollama and the model requested by Rhex.

Follow the setup instructions inside the application if the local service or
model is unavailable. Initial installation and model downloads require internet
access and local storage.

## What is new in alpha.5

### Local Activity history

- Records application starts.
- Records successful conversation creation, rename, and deletion.
- Records model-download and update outcomes using fixed summaries.
- Does not record chat text, conversation titles, file paths, or raw error details.
- Displays the newest 200 events and retains at most 1,000.
- Removes events older than 30 days when Activity storage is accessed.
- Clearing Activity history does not delete conversations.

Activity is an operational history, not a tamper-proof audit log.

### Updater improvements

- Preserves update status when switching tabs.
- Blocks sidebar navigation, app shortcuts, and other Settings actions during
  update operations.
- Blocks tray Quit while alpha.5 performs an update installation.
- Requires confirmation before downloading and installing an update.

These controls do not prevent forced termination, system shutdown, or power loss.

## Updating Rhex

In an updater-enabled build:

1. Open Settings.
2. Select Check for updates.
3. Review the available version and release notes.
4. Select Download and install and approve the confirmation.
5. Wait for successful installation.
6. Select Quit Rhex from the tray menu.
7. Reopen the same AppImage or your installed launcher.

Closing the window only hides Rhex; it does not fully quit the application.

The AppImage filename may retain an older version number after updating.
Check Running version in Settings to identify the version actually running.

Builds that predate the updater, including alpha.2, require a manual download
of an updater-enabled release.

If an update check fails or offers no newer release unexpectedly, report the
exact message and your running version.

## Testing status

- The alpha.3 → alpha.4 update was tested successfully.
- Conversation preservation and local chat were confirmed after that upgrade.
- The alpha.4 → alpha.5 upgrade is still being verified.
- Alpha.5's installation guards require a later upgrade test from alpha.5.
- Model-download outcome logging needs a dedicated download test.
- Additional Linux-distribution testing is needed.

## Download security

Use the official Releases page linked above.

The in-app updater verifies signed update artifacts.
A manually downloaded AppImage is not automatically signature-verified merely
because a `.sig` file is attached to the release.

Never share passwords, signing keys, or private conversation content in reports.

## Reporting issues

Report issues through the Discord tester channel.

Include:

- Running Rhex version from Settings.
- Linux distribution and version.
- How you launched Rhex.
- Steps to reproduce the issue.
- Exact error text.
- Whether local chat works.
- Whether conversations remain after fully quitting and reopening.

## Development roadmap

## Arch Linux testing

The Linux x86_64 AppImage is available for Arch Linux users to test.

**Status: Arch compatibility has not yet been confirmed by a tester.**
A separate native Arch package is not currently provided.

### Download and launch

Download `rhex_0.7.0-alpha.5_amd64.AppImage` from the alpha.5 release Assets.

Assuming the file is in your Downloads folder:

```bash
cd ~/Downloads &&
chmod +x rhex_0.7.0-alpha.5_amd64.AppImage &&
WEBKIT_DISABLE_DMABUF_RENDERER=1 \
  ./rhex_0.7.0-alpha.5_amd64.AppImage
```

Run Rhex as your normal user, not with sudo.

### Missing FUSE dependency

Only if launching reports `libfuse.so.2` missing or an error requiring FUSE,
run this on the Arch computer:

```bash
sudo pacman -Syu --needed fuse2
```

This command also performs a system upgrade. Review the package transaction
before confirming, then try launching Rhex again.

If Rhex already launches, skip this step.

### Please report your results

Send feedback through the Discord tester channel, including:

- Arch Linux or derivative distribution name.
- Desktop environment and whether you use Wayland or X11.
- Running Rhex version shown in Settings.
- Whether the application opens and local chat works.
- Whether conversations remain after quitting and reopening.
- Whether Activity and tray controls work.
- Whether Check for updates completes.
- Exact terminal errors if anything fails.

Do not include private chats, passwords, or signing keys.
