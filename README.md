# Apple Music for Stream Deck (Windows)

A Stream Deck plugin that controls **Apple Music on Windows**: play and pause, skip, now playing with album art, shuffle, repeat, and Stream Deck+ dials for volume and scrubbing.

> **AI disclosure:** This plugin was fully coded by AI. Every line of code, the helper program, the icons, and this README were written by AI tools, with a human choosing the features and testing it. Review it as you would any community plugin before installing.

## Install

1. Download `com.spud.applemusic.streamDeckPlugin` from the [latest release](https://github.com/jeremyp15/streamdeck-apple-music/releases/latest) (it's also in [`dist/`](dist/)).
2. Double-click it. Stream Deck installs the plugin and adds an **Apple Music** category to the actions list.
3. Drag the actions you want onto your keys or dials.

## Requirements

- Windows 10 or later
- Stream Deck software 6.5 or later (the plugin runs on Stream Deck's built-in Node.js 20)
- The Apple Music app for Windows (iTunes also works)
- A Stream Deck+ for the Volume and Scrub dial actions

## Actions

| Action | Where | What it does |
| --- | --- | --- |
| Play/Pause | Key | Toggles playback. The key shows Playing or Paused. |
| Next Track | Key | Skips to the next song. |
| Previous Track | Key | Goes back to the previous song. |
| Now Playing | Key | Shows the album art, title and artist, and refreshes when the song changes. |
| Shuffle | Key | Toggles shuffle (see the notes below). |
| Repeat | Key | Cycles repeat Off, All and One (see the notes below). |
| Volume | Dial | Turn to change the volume and press or tap to mute. You can set the step size from 1 to 10% per tick. |
| Scrub | Dial | Turn to move through the song, and press or tap to play or pause. |

## How it works

The plugin talks to Windows' built-in media controls (the media session Apple Music publishes) through a small helper program, `bin/media-helper.exe`. It doesn't need an Apple account and doesn't connect to the internet. It only reads and controls what's playing on your PC.

- If Apple Music has no media session open, the keys follow whatever app Windows treats as the current player, and the artist line names that app.
- Volume uses the app's level in the Windows volume mixer when one exists, and otherwise the default playback device.
- Scrubbing works when the session allows it. Live streams and some videos don't.

### Shuffle and Repeat notes

Apple Music on Windows usually doesn't report shuffle or repeat to Windows. When it doesn't, these keys bring the Apple Music window forward and send its menu access keys (**Alt, L, S** for shuffle and **Alt, L, R** for repeat). Because the app doesn't report the result, the key keeps its neutral icon. A song has to be playing first. Other players never get these keystrokes.

## Repository layout

```
com.spud.applemusic.sdPlugin/   plugin folder (manifest, compiled plugin.js, helper, UI, icons)
dist/                           packaged .streamDeckPlugin installer
```

`bin/plugin.js` is the compiled plugin and includes Elgato's Stream Deck SDK (MIT). `bin/media-helper.exe` is a prebuilt helper written in Rust. The original source for both wasn't preserved, so this repo ships the built files.

SHA-256 of the files:
- `com.spud.applemusic.streamDeckPlugin`: `bab23be2d40b721ee5ff3ab14579b967bca31b4794ca79fb8edba8742697172a`
- `media-helper.exe`: `2c16096c5a17ecebd20464fe105aa754654f79ed994ce8dab2adebdddbd97ae7`

## Uninstall

In Stream Deck, open Preferences, then Plugins, select Apple Music and click the minus button.

## License

[MIT](LICENSE). This project isn't affiliated with or endorsed by Apple or Elgato. Apple Music is a trademark of Apple Inc., and Stream Deck is a trademark of Corsair Memory Inc.
