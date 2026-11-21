# Release notes

## 1.0.70

- Show true job/master progression separately from effective level-sync levels. Resolve the Exemplar target from its authoritative requirement instead of adding one to the synced master level. Display remaining EXP/Exemplar Points and the level-99 EXP cap.
- Estimate EXP, Limit Points, Capacity Points and Exemplar rewards per hour from up to ten minutes of consecutive passive reward samples, including idle time. Show merit/JP reward equivalents without mistaking spending, caps or level transitions for gains.
- Companion 0.5.0 reports unlocked job levels, sync state and cumulative observed rewards at the existing reporting cadence. Missing data, reconnects, stale reports and job changes reset rate estimates. Existing login and recovery behavior is unchanged.

After upgrading, deploy companion **0.5.0** and reload **FFXIManager** in already-running sessions to enable the new sync fields and reward counters. Games do not need to be logged out. Rates start after at least one minute of consecutive samples and use up to ten minutes of history; merit/JP rates are reward equivalents, not changes in the stored balance.

Validation: 848 core checks, desktop/dashboard safety smoke checks and all six Lua regression modes passed. The Windows x64 build succeeded. These changes have not yet been installed or validated in a live game; this release is published first for updater testing.

## 1.0.69

- After confirmed POL-0003 Exit, recognize a stable exact-account Member List and continue the guarded login in the same POL process. Require verified character/world traffic before recording recovery.
- Recheck unresolved Exit outcomes rather than permanently abandoning a usable POL session. Preserve outage stabilization, maintenance holds, manual stops, credential rejection and other-terminal protection.
- Maintained member-list and recoverable service failures continue without an artificial retry-count stop or added backoff on healthy connectivity. Confirmed connectivity loss and maintenance retain their holds. Stop after two failed authentication attempts and show a warning; manual stops and other-terminal protection remain effective.

Validation: 828 core checks, desktop/dashboard safety smoke checks and a native Windows package check passed. After installation, a naturally stalled account completed a full verified login in its original POL process and recorded the recovery time. All three game processes retained their identities and reported fresh matching session/server traffic; account settings and credential files were unchanged. The POL-0003 Exit-to-Member-List transition, outage handling and credential retry guards were covered by isolated regressions; no healthy game or live network was deliberately disrupted.

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
