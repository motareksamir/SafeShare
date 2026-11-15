# Privacy

**SafeShare collects no data.** It has no accounts, no analytics, no crash reporting and no
network code. Everything it does happens on your Mac.

## What SafeShare accesses

| What | Why | Stored? | Sent anywhere? |
| --- | --- | --- | --- |
| The list of running apps | To know which apps have windows to minimize | No | No |
| Each app's window list, and whether a window is minimized, full-screen or a standard window | To minimize the right windows | Only in memory while the app runs, so Restore can undo it | No |
| Finder's "show desktop icons" setting (`CreateDesktop`) | To show or hide desktop icons | macOS stores this setting in Finder's own preferences | No |

## What SafeShare does not access

- Window titles, window contents, or anything displayed on your screen
- Your screen itself: it does not record, capture or share the screen
- Your files, documents, clipboard or keystrokes
- Camera, microphone, contacts, calendar, photos or location
- The network: it makes no connections of any kind

## The Accessibility permission

macOS requires the Accessibility permission for any app that controls another app's windows.
This permission is broad: in general it allows an app to read and control other apps'
interfaces. SafeShare uses it for one thing only, which is setting the *minimized* state of
standard windows.

You can withdraw the permission at any time in
**System Settings → Privacy & Security → Accessibility**.

## Changes

If this ever changes, this file and the [changelog](CHANGELOG.md) will say so.
