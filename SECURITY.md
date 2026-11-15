# Security

## Permissions SafeShare uses

| Item | Status | Reason |
| --- | --- | --- |
| Accessibility (user-granted) | **Required** | Minimizing other apps' windows is only possible through the Accessibility API |
| Hardened Runtime | **Enabled** | Protects the app from code injection and tampering |
| App Sandbox | **Disabled** | The sandbox blocks both things the app exists to do (see below) |
| Automation / Apple Events | Not used | |
| Screen Recording | Not used | |
| Full Disk Access, Files and Folders | Not used | |
| Network (incoming or outgoing) | Not used | |
| Hardened Runtime exceptions (entitlements) | None | |

## Why the App Sandbox is off

A sandboxed app cannot use the Accessibility API to control other apps' windows, cannot write
Finder's preferences, and cannot restart Finder. Those are SafeShare's two features, so the
app is distributed outside the Mac App Store, unsandboxed, with the Hardened Runtime on.

## What the app runs

SafeShare starts exactly three system tools, always by absolute path and with fixed arguments.
Nothing typed, downloaded or read from a file is ever passed to them, and no shell is involved.

| Tool | Arguments | Purpose |
| --- | --- | --- |
| `/usr/bin/defaults` | `read` / `write com.apple.finder CreateDesktop` | Read or change whether Finder draws desktop icons |
| `/usr/bin/killall` | `Finder` | Restart Finder so the change takes effect |
| `/usr/bin/pgrep` | `-x -U <your uid> Finder` | Wait until the new Finder is running |

SafeShare does not download or load code, does not install helpers, launch agents or login
items, and never asks for an administrator password.

## Verifying your download

Only download SafeShare from this repository's Releases page. You can check that your copy is
signed and notarized by Apple:

```sh
codesign --verify --deep --strict --verbose=2 /Applications/SafeShare.app
spctl --assess --type execute --verbose /Applications/SafeShare.app
```

## Supported versions

Only the latest release receives fixes.

## Reporting a vulnerability

Please do not open a public issue for a security problem. Use **Security → Report a
vulnerability** on this repository (GitHub private vulnerability reporting). You can expect a
reply within a week.
