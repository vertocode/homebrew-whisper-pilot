# homebrew-whisper-pilot

Homebrew tap for [Whisper Pilot](https://github.com/vertocode/whisper-pilot) — the ambient, local-first AI co-pilot for live conversations on macOS.

## Install

```sh
brew install --cask vertocode/whisper-pilot/whisper-pilot
```

That's it. The first time, Homebrew adds this tap automatically and then installs the latest signed `.dmg` from the [Whisper Pilot releases page](https://github.com/vertocode/whisper-pilot/releases).

## Update

```sh
brew upgrade --cask whisper-pilot
```

## Uninstall

```sh
brew uninstall --cask whisper-pilot

# Optionally clear preferences and Application Support too
brew uninstall --cask --zap whisper-pilot
```

The `--zap` form clears `~/Library/Preferences/com.whisperpilot.app.plist` and the cache, but **leaves your session transcripts and chats** in `~/Library/Application Support/com.whisperpilot.app/sessions/` alone — those are your data.

## What's in this repo

The single file `Casks/whisper-pilot.rb` is the Cask definition. It tells Homebrew where to download the DMG and which version is current. Every Whisper Pilot release updates two fields here (`version` and `sha256`) and that's the whole "ship a new version to Homebrew" workflow.

The canonical Cask file lives in the [main Whisper Pilot repo](https://github.com/vertocode/whisper-pilot/blob/main/Casks/whisper-pilot.rb). This repo mirrors it because Homebrew taps must be in a repo whose name starts with `homebrew-`.

## First-launch Gatekeeper note

Until Whisper Pilot is shipped signed with an Apple Developer ID and notarized, macOS Gatekeeper will warn on first launch *"WhisperPilot.app can't be opened because Apple cannot check it for malicious software."*

To bypass once:

- **Right-click** the app in `/Applications` → **Open** → click **Open** in the dialog. macOS remembers and won't ask again.
- Or in Terminal: `xattr -dr com.apple.quarantine /Applications/WhisperPilot.app`

This goes away entirely once the project upgrades to a fully notarized release.

## Issues

Tap-specific problems (cask doesn't install, wrong checksum, wrong version) → file here.
App-specific problems (crashes, transcription bugs, missing features) → file in the [main repo](https://github.com/vertocode/whisper-pilot/issues).

## License

MIT — same as Whisper Pilot itself.
