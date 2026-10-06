# Rhex releases

Official downloads and release notes for Rhex, a local-first Linux AI assistant.

Rhex is currently alpha software. These builds are intended for testing.

## Download

Current tester release: **0.7.0-alpha.4**

[Open the alpha.4 release](https://github.com/HexandRoach/rhex-releases/releases/tag/v0.7.0-alpha.4)

Under Assets, download:

`rhex_0.7.0-alpha.4_amd64.AppImage`

This build targets Linux x86_64. Windows, macOS, and ARM builds are not provided here.

Do not select the automatically generated Source code archives to install Rhex.

## First launch

If Rhex is already running, select Quit Rhex from its tray menu first.

Assuming the AppImage is in your Downloads folder, run:

```bash
cd ~/Downloads &&
chmod +x rhex_0.7.0-alpha.4_amd64.AppImage &&
WEBKIT_DISABLE_DMABUF_RENDERER=1 \
  ./rhex_0.7.0-alpha.4_amd64.AppImage
```

Keep the AppImage in a location where your user can write to it so the updater can replace it.

Downloading the AppImage does not automatically create an application-menu entry.
A standalone launcher installer is planned.

## Local AI setup

Local chat requires Ollama and the model requested by Rhex.

If the local service or model is unavailable, follow the setup instructions inside
the application. Initial engine and model downloads require internet access.

## Application updates

In Settings:

1. Select Check for updates.
2. Review the available version and release notes.
3. Select Download and install and approve the confirmation.
4. Wait for successful installation.
5. Select Quit Rhex from the tray menu.
6. Reopen the same AppImage.

Closing the window only hides Rhex; it does not fully quit the application.

The AppImage filename may keep an older version number after updating.
Check Running version in Settings to identify the version actually running.

Builds that predate the updater, including alpha.2, require a manual download
of an updater-enabled build.

## Security

Use downloads from this repository's official Releases page.

The in-app updater verifies signed update artifacts.
A manually downloaded AppImage is not automatically signature-verified merely
because a .sig file is attached to the release.

Never share signing keys, passwords, or private conversation data in bug reports.

## Tester reports

Please include:

- Rhex running version from Settings.
- Linux distribution and version.
- How you launched the application.
- Steps to reproduce the issue.
- Exact error text.
- Whether local chat works.
- Whether conversations remain after fully quitting and reopening.

Share reports through the project's Discord tester channel.
