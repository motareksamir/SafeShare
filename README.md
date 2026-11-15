<p align="center">
  <img src="docs/icon.png" width="128" height="128" alt="SafeShare icon">
</p>

<h1 align="center">SafeShare</h1>

<p align="center">
  A tiny macOS menu bar app that gets your screen ready for sharing in one click:<br>
  it hides your desktop icons and minimizes every open window.
</p>

<p align="center">
  <img alt="Platform: macOS" src="https://img.shields.io/badge/platform-macOS-lightgrey">
  <img alt="Price: free" src="https://img.shields.io/badge/price-free-blue">
</p>

---

## Why

Right before a call you remember the messy desktop, the open chat window and the document
you'd rather not show. SafeShare clears all of it with one click, and puts it all back with
another when the call is over.

## Features

- **Safe Share Now** – hides desktop icons, then minimizes every open window.
- **Minimize All Windows** – minimizes windows only, and leaves the desktop alone.
- **Toggle Desktop Icons** – shows or hides desktop icons on their own.
- **Restore Windows & Icons** – brings back exactly the windows SafeShare minimized, the
  apps it hid, and your desktop icons.
- **Nothing left visible** – a window that can't be minimized (full-screen windows, apps that
  don't respond) gets its whole app hidden instead.
- **Menu bar only** – no Dock icon, no main window, no settings to configure.
- **Private by design** – no network access, no analytics, no data collected.
  See [PRIVACY.md](PRIVACY.md).

## The menu

| Menu item | Key (while the menu is open) | What it does |
| --- | --- | --- |
| Safe Share Now | `S` | Hide desktop icons and minimize all windows |
| Toggle Desktop Icons | `T` | Show or hide desktop icons |
| Minimize All Windows | `M` | Minimize every window on the current desktop |
| Restore Windows & Icons | `R` | Undo what SafeShare did |
| Quit | `Q` | Quit SafeShare |

## Requirements

- macOS 27 or later

## Install

1. Download **SafeShare.zip** from the [latest release](../../releases/latest).
2. Unzip it and move **SafeShare.app** to your **Applications** folder.
3. Open SafeShare. A viewfinder icon appears in the menu bar.
4. Grant the Accessibility permission when macOS asks (see below).

To update, quit SafeShare and replace the app with the new version.

## Permissions

SafeShare needs **one** permission.

| Permission | Why it is needed | Where to grant it |
| --- | --- | --- |
| **Accessibility** | macOS only lets an app minimize *other* apps' windows through the Accessibility API. | System Settings → Privacy & Security → Accessibility |

On first launch macOS shows a prompt. Click **Open System Settings** and switch **SafeShare** on.

SafeShare does **not** ask for Screen Recording, Automation, Full Disk Access, Files and
Folders, camera, microphone, contacts or location, and it makes no network connections.

**If minimizing does nothing after an update:** remove SafeShare from the
Accessibility list with the **–** button, then add it again. macOS sometimes keeps a stale
entry for an older version.

## How it works

- **Windows.** SafeShare asks each regular app for its windows through the macOS Accessibility
  API and minimizes every standard window. It never reads window titles or contents. Apps
  whose windows refuse are hidden instead.
- **Desktop icons.** SafeShare changes Finder's "show desktop icons" setting and restarts
  Finder, which is the only way to make Finder stop drawing desktop icons. It then waits for
  Finder to come back before minimizing.
- **Restore.** SafeShare remembers which windows it minimized and which apps it hid, in
  memory only, and reverses exactly those.

## Limitations

- **Hiding desktop icons restarts Finder.** Open Finder windows close and reopen, and a file
  copy in progress may be interrupted. If the icons are already hidden, Finder is not restarted.
- **Only the current desktop.** Windows on other Spaces are not touched.
- **Full-screen windows can't be minimized.** Their app is hidden instead.
- **Restore is per session.** If you quit SafeShare, it forgets which windows it minimized.
  Use **Toggle Desktop Icons** to bring the icons back.
- **Not on the Mac App Store.** The App Store requires the App Sandbox, which blocks
  controlling other apps' windows and changing Finder's settings. See [SECURITY.md](SECURITY.md).

## Uninstall

1. Choose **Restore Windows & Icons** (or **Toggle Desktop Icons**) so your icons are showing.
2. Quit SafeShare and move `SafeShare.app` to the Trash.
3. Remove SafeShare from System Settings → Privacy & Security → Accessibility.

If your desktop icons are still hidden after uninstalling, run this in Terminal:

```sh
defaults delete com.apple.finder CreateDesktop && killall Finder
```

## Feedback

Found a bug or have an idea? [Open an issue](../../issues). For security problems, see
[SECURITY.md](SECURITY.md).

## License

SafeShare is free to use. See [LICENSE](LICENSE).
