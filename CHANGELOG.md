# Release notes

## 1.0.68

- **Reliable member selection:** improve PlayOnline member-list recognition at high DPI and resume eligible maintained accounts in the existing session, while still requiring the exact Square Enix ID.
- **Faster, accurate connectivity checks:** a healthy internet check permits login immediately. Only an actual failed check starts stabilization: three successful checks five seconds apart, with bounded backoff during repeated failures. Accounts share checks; POL-0019 resumes its bounded Retry workflow after connectivity returns.
- **Complete recovery tracking:** allow confirmed character entry to finish loading and verify the matching character/world with fresh traffic. Record delayed successful recovery without repeating login input, and display its recovery time.
- **Clear update scheduling:** show the last and next app-update checks. Check shortly after startup and every 12 hours, with manual checks available anytime. Explain when automatic installation is idle; running games remain open.
- Preserve manual stops, credential rejection, other-terminal protection, shared game-update queues, saved settings, and previously validated logins.

Validation: 716 core checks plus dashboard/safety smoke checks passed. Native Windows OCR fixtures covered four resolutions. A live maintained-account login completed in the existing POL process, and 1.0.68 verified the delayed world entry and recovery timestamp without replaying input. Installation preserved all four game processes, settings and saved login validations; all four reported fresh connection evidence. Internet-outage and backoff cases were tested with simulated probes, without disrupting live networking.

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
