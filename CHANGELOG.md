# Release notes

## 1.0.63

- Recover from in-game **POL-2059** when a HaupBridge overlay covers part of the error message. The manager checks the exact error code, readable message fragments, and the visible **OK** button in two separate reads.
- Use FFXI's numeric Enter key to confirm the verified dialog. If the dialog fails to advance or the game loses focus after confirmation, pause automatic input for that process.
- Pause recovery while the Windower console is visible so pending text stays untouched.
- Live validation confirmed overlay recognition. A manual Enter press cleared the dialog and the manager completed the relogin. The automated Enter path was tested offline. Installing 1.0.63 preserved all three running sessions, account settings, and login validation.

This release was rebuilt from the cleaned source for the new downloads repository. Both Windows packages were verified before publication.
