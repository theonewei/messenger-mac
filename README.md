# Messenger for Mac

A standalone desktop app for Facebook Messenger on macOS. Chat with friends without opening a browser.

**Why this exists:** Meta discontinued the official Messenger desktop app. This is a lightweight replacement that lets you use Messenger without keeping a browser tab open.

<img src="icon.png" width="128" alt="Messenger for Mac">

## Download

This fork adds native Apple Silicon (`arm64`) builds alongside Intel (`x64`) builds.

Builds from this fork are not Developer ID signed or notarized. Upstream's signing credentials do not apply to this fork. No fork release is published yet; build locally using the steps below, or download build artifacts from a successful [macOS build workflow](https://github.com/theonewei/messenger-mac/actions/workflows/build.yml).

Choose `MessengerApp-<version>-arm64.dmg` for Apple Silicon (M-series Macs), or `MessengerApp-<version>-x64.dmg` for Intel. ZIP builds are also available. Electron 33 requires macOS 11 or later.

## Features

- **Native macOS App** - Runs as a standalone application in your dock
- **No Browser Required** - Access Messenger without opening Chrome, Safari, or Firefox
- **Persistent Login** - Stay logged in between app restarts
- **Native Notifications** - Get notified of new messages
- **Minimal & Fast** - Lightweight app with low memory footprint
- **Privacy Focused** - No tracking, no analytics, no data collection
- **Dark Mode Support** - Follows your macOS appearance settings
- **External Links** - Shared links open in your default browser
- **Power Saving Mode** - Automatically throttles when in background to reduce CPU/battery usage
- **Auto-Update Check** - Get notified when a new version is available
- **Keyboard Shortcuts** - Quick navigation with custom shortcuts

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Cmd + N` | New message |
| `Cmd + 1-9` | Switch to conversation 1-9 |
| `Cmd + Shift + S` | Toggle sidebar visibility |

All settings (sidebar visibility) are persisted across app restarts.

## Screenshots

| Chat View | Login |
|-----------|-------|
| Native macOS window | Secure Facebook login |

## Installation

1. Build locally or download the DMG matching your Mac from the workflow artifacts linked above (GitHub sign-in required).
2. Open the DMG
3. Drag **MessengerApp** to your **Applications** folder
4. Launch from Applications or Spotlight

## Build from Source

### Prerequisites

- macOS 11+ (Apple Silicon or Intel)
- Node.js 22 LTS
- npm

### Steps

```bash
# Clone the repository
git clone https://github.com/theonewei/messenger-mac.git
cd messenger-mac

# Install dependencies
npm ci

# Run in development mode
npm start

# Check JavaScript syntax
npm run check

# Build native Apple Silicon DMG and ZIP
CSC_IDENTITY_AUTO_DISCOVERY=false npm run build:arm64

# Or build Intel DMG and ZIP
CSC_IDENTITY_AUTO_DISCOVERY=false npm run build:x64

# Or build both architectures
CSC_IDENTITY_AUTO_DISCOVERY=false npm run build
```

The built apps and installers will be in `dist/`, with `arm64` or `x64` in each installer filename. ARM64 builds run natively without Rosetta. The build workflow checks both packaged executables with `lipo` and uploads the installers as artifacts.

Local and CI examples disable certificate discovery and notarization. Distribution with Developer ID signing and notarization requires your own Apple Developer credentials and a separate electron-builder signing/notarization configuration. macOS may block downloaded unsigned builds; only open builds whose source and origin you trust.

## Tech Stack

- [Electron](https://www.electronjs.org/) - Cross-platform desktop apps
- JavaScript/Node.js

## FAQ

### Is this the official Messenger app?
No, this is an unofficial wrapper around messenger.com. It's not affiliated with Meta/Facebook.

### Is it safe?
This fork is not Developer ID signed or notarized. It loads messenger.com in an Electron window. Review the source before building or installing it.

### Why use this instead of the browser?
- Dedicated app in your dock
- Separate from browser tabs
- Stays logged in
- Cleaner experience
- Less resource usage than a full browser

### Does it support voice/video calls?
Yes, all Messenger features work including voice and video calls.

### My login isn't persisting?
Make sure to quit the app with `Cmd+Q` (not just close the window) to save your session.

## Keywords

Facebook Messenger Mac, Messenger Desktop App, Messenger macOS, Facebook Chat Mac App, Messenger without browser, Standalone Messenger Mac, Messenger Mac download, Facebook Messenger native app, Messenger Electron app, Mac Messenger client

## License

MIT License - feel free to modify and distribute.

## Disclaimer

This project is not affiliated with, authorized, maintained, sponsored, or endorsed by Meta/Facebook or any of its affiliates or subsidiaries. This is an independent and unofficial app. Use at your own risk.

---

**Star this repo if you find it useful!**
