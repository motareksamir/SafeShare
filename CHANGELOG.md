# Changelog

## 1.0.4

- Windows are now minimized through the Accessibility API instead of AppleScript. It is
  faster and far more reliable, and the Automation permission is no longer needed.
- Apps whose windows can't be minimized (full-screen, unresponsive) are hidden instead.
- New **Restore Windows & Icons** menu item.
- **Safe Share Now** waits for Finder to finish restarting before minimizing.
- **Toggle Desktop Icons** works correctly the first time it is used.
- The menu no longer freezes while an action is running.
- The app runs in the menu bar only, with no Dock icon.
- Asks for the Accessibility permission at launch.

## 1.0.0

- First version: hide desktop icons and minimize all windows from the menu bar.
