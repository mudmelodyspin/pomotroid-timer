<div align="center">

# Pomotroid Desktop

Simple, configurable, and visually focused Pomodoro timer.

</div>

---

## 🍅 Overview

Pomotroid is a Pomodoro timer designed for tracking focused work sessions and breaks using the Pomodoro Technique. It provides configurable work and break durations, session statistics, themes, localization, tray behavior, desktop notifications, global shortcuts, and an optional local WebSocket server for integrations.

The application is built with Tauri 2, Rust, and Svelte 5.

## ✨ Features

- **Configurable Pomodoro timer**  
  Customize work duration, short breaks, long breaks, and the number of work rounds before a long break.

- **Session statistics**  
  View daily, weekly, and all-time session history, including charts and a 52-week heatmap.

- **Bundled themes**  
  Includes 38 themes such as Dracula, Nord, Tokyo Night, Catppuccin, Gruvbox, Rose Piné, and others.

- **Custom themes**  
  Supports user-created JSON themes with live hot-reload, so changes can be applied without restarting the app.

- **Automatic light/dark theme behavior**  
  Themes can switch based on the operating system light or dark preference.

- **Localization**  
  Supports English, Spanish, French, German, Japanese, Chinese Simplified, Turkish, and Portuguese, with OS language detection.

- **Global shortcuts**  
  Control the timer from outside the main window, including when the app is hidden.

- **Custom audio**  
  Replace built-in alert sounds with custom audio files.

- **Optional tick sounds**  
  Enable ticking during work rounds and break rounds independently.

- **Dynamic tray icon**  
  Shows timer progress and reflects round type and pause state.

- **Tray behavior**  
  Supports minimizing or closing to the system tray.

- **Desktop notifications**  
  Sends native OS notifications when the timer changes rounds.

- **Compact mode**  
  Shows a reduced control layout when the window is resized smaller.

- **Always on top**  
  Optionally keep the timer window above other windows.

- **WebSocket server**  
  Provides an opt-in local WebSocket server for external tools, stream overlays, and automation scripts.

- **Diagnostic logging**  
  Uses rotating log files and includes a shortcut to open the log folder.

## 🧰 Technology Stack

| Area | Technology |
| --- | --- |
| Desktop application framework | Tauri 2 |
| Native backend | Rust |
| Frontend | Svelte 5 |
| Localization build tooling | Paraglide |

## 📊 Statistics

Pomotroid records completed sessions and presents them through several views:

- a daily summary,
- an hourly breakdown,
- a weekly bar chart,
- streak tracking,
- and an all-time 52-week heatmap.

These statistics are intended to help users review focus patterns over time and understand how often Pomodoro sessions are completed.

## 🎨 Themes

Pomotroid includes 38 bundled themes and supports custom themes. Custom themes are defined as JSON and can be placed in the themes folder. Theme changes are applied automatically without restarting the application.

The bundled theme set includes well-known color palettes such as:

- Dracula
- Nord
- Tokyo Night
- Catppuccin
- Gruvbox
- Rose Piné

## 🌍 Localization

Pomotroid supports the following languages:

- English
- Spanish
- French
- German
- Japanese
- Chinese Simplified
- Turkish
- Portuguese

The app can automatically detect the operating system language. UI strings are stored by locale, and localized output is generated during the development/build workflow.

## 🔌 WebSocket API

Pomotroid includes an optional local WebSocket server. It is disabled by default and can be enabled from:

**Settings → Advanced → WebSocket Server**

When enabled, clients can connect to:

`ws://127.0.0.1:<port>`

The default port is:

`1314`

### Client to Server

| Message | Description |
| --- | --- |
| `{ "type": "getState" }` | Requests the current timer state |

### Server to Client

| Event | Payload | Description |
| --- | --- | --- |
| `state` | `TimerState` object | Response to `getState` |
| `roundChange` | `TimerState` object | Sent when the timer advances to a new round |
| `error` | `{ message }` | Protocol error |

### Timer State Fields

`TimerState` includes:

- `elapsed_secs`
- `total_secs`
- `is_running`
- `is_paused`
- `round_type`
- `work_round_number`
- `work_rounds_total`

## 🖥️ Linux Tray Note

On GNOME, tray icons are not displayed by default. To use Pomotroid’s tray icon on GNOME, the AppIndicator and KStatusNotifierItem Support extension is required. Other desktop environments such as KDE Plasma, XFCE, Cinnamon, and MATE support tray icons natively.

## 🛠️ Development

Pomotroid can be run and built using the Tauri development workflow.

```bash
npm install
npm run tauri dev
npm run tauri build
```

Localization output is generated automatically during development and build commands. After adding or changing message keys, the localization output can be regenerated explicitly:

```bash
npm run paraglide:compile
```

The project also runs this compilation as part of:

```bash
npm run check
```

## ❓ FAQ

### What is Pomotroid?

Pomotroid is a desktop Pomodoro timer for managing focused work sessions and breaks.

### Can the timer durations be changed?

Yes. Work duration, break duration, long break duration, and the number of rounds before a long break are configurable.

### Does Pomotroid track completed sessions?

Yes. It records completed sessions and provides daily, weekly, and all-time statistics.

### Does Pomotroid support themes?

Yes. It includes 38 bundled themes and supports custom JSON themes with live hot-reload.

### Can Pomotroid run in the background?

Yes. Pomotroid supports minimizing or closing to the system tray.

### Does Pomotroid support integrations?

Yes. It includes an optional local WebSocket server that can expose timer state to external tools, stream overlays, or automation scripts.

### Is Pomotroid localized?

Yes. It supports eight languages and can detect the operating system language.

## 📄 License

MIT © Christopher Murphy
