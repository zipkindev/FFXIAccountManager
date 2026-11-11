# Release notes

## 1.0.64

- The manager checks this releases repository on startup and every six hours. Open **App updates** to check manually or install an available version.
- **Automatically install updates when idle** is off by default. Enable it if you want the protected Windows manager to install new releases after account operations and game updates finish.
- The updater verifies the download against the release’s SHA-256. The Windows installer checks that the replacement is ready and restores the prior manager if startup fails. A failed version won’t be retried automatically after rollback.
- Upgrade to **1.0.64 manually once** if you’re on 1.0.63 or older. Use the desktop shortcut created by **Enable unattended access** to install future updates from inside the app.

The Windows upgrade was tested with four connected clients. The manager restarted, all four game processes stayed open and reported fresh server traffic, and account settings and saved login validation remained unchanged. The test used a local release fixture containing the exact published EXE; the public download is verified separately.

## 1.0.63

- Recover from in-game **POL-2059** when a HaupBridge overlay covers part of the error message. The manager checks the exact error code, readable message fragments, and the visible **OK** button in two separate reads.
- Use FFXI's numeric Enter key to confirm the verified dialog. If the dialog fails to advance or the game loses focus after confirmation, pause automatic input for that process.
- Pause recovery while the Windower console is visible so pending text stays untouched.
- Live validation confirmed overlay recognition. A manual Enter press cleared the dialog and the manager completed the relogin. The automated Enter path was tested offline. Installing 1.0.63 preserved all three running sessions, account settings, and login validation.

This release was rebuilt from the cleaned source for the new downloads repository. Both Windows packages were verified before publication.
