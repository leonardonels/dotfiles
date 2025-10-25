# Omarchy Dotfiles — Surface Laptop Go (1)

Personal setup for Omarchy (Hyprland + Waybar) tuned for a lightweight laptop with great touchpad gestures. The goal is fast, distraction‑free productivity: quick app/web‑app launchers, useful gestures, and a minimal icon‑first Waybar.

If you know the stock Omarchy dotfiles, this README highlights what’s different here and how to adopt it quickly.

## What’s different vs stock Omarchy

### Hyprland — shortcuts and launchers
File: `config/hypr/bindings.conf`

- Terminal with current working directory: Super + Enter opens `$TERMINAL` in the active folder (via `omarchy-cmd-terminal-cwd`).
- App and web‑app launchers you’ll actually use:
	- Super + Shift + F → File manager (Nautilus)
	- Super + Shift + B → Default browser
	- Super + Shift + Alt + B → Private browser window
	- Super + Shift + N → Editor
	- Super + Shift + T → btop (system monitor)
	- Super + Shift + D → lazydocker
	- Super + Shift + O → Obsidian
	- Super + Shift + / → 1Password
	- Super + Shift + Alt + M → Spotify
	- Productivity web‑apps: Calendar, Gmail, Gemini, YouTube, WhatsApp, Google Messages, X/Twitter, X Post, Microsoft Teams, Apple Music
		- Examples: Super + Shift + C → Calendar, Super + Shift + E → Gmail, Super + Shift + A → Gemini, Super + Shift + Y → YouTube, Super + Shift + G → WhatsApp, Super + Shift + Ctrl + G → Google Messages, Super + Shift + X → X, Super + Shift + Alt + X → New post, Super + Shift + Alt + T → Teams, Super + Shift + M → Apple Music
	- Super + Shift + Alt + A → “Invoke AI” (dedicated webapp)

Note: There are commented lines to move Omarchy Menu to Super Shift + Space if you prefer.

### Hyprland — input and gestures
File: `local/share/omarchy/default/hypr/input.conf`

- Keyboard: `us` layout with `compose:caps` (Caps Lock as Compose).
- `follow_mouse = 1` for hover‑to‑focus.
- Touchpad tuned for laptop flow:
	- 3‑finger horizontal → next workspace
	- 3‑finger vertical → scale 1.5× and fullscreen
	- 3‑finger up/down with Super → scale 1.5× and toggle float
	- 4‑finger down → close
	- 4‑finger up → scale 1.5× and float

The idea: manage windows comfortably without leaving the touchpad.

### Waybar — minimal, icon‑first, with useful clicks
File: `config/waybar/config.jsonc`

- Top bar, 26px height, zero spacing for crisp alignment.
- Left: Omarchy logo (click → `omarchy-menu`, right‑click → terminal) + Workspaces (iconic, persistent 1‑5).
- Center: Clock (alt weekly format), Omarchy update indicator, screen‑recording indicator.
- Right: Tray with expander, Bluetooth, Network, Audio, CPU, Battery.
- Key interactions:
	- CPU click → `btop`
	- Clock right‑click → `omarchy-tz-select`
	- Network click → Omarchy Wi‑Fi launcher
	- Battery click → Omarchy power menu
	- Audio click → Wiremix, right‑click → mute via `pamixer`
	- Bluetooth click → Blueberry
- Custom indicators:
	- `custom/update` checks Omarchy updates hourly and opens them in a floating terminal
	- `custom/screenrecording-indicator` shows recording status (Omarchy script)

Overall, it’s more icon‑driven than stock and emphasizes click actions you’ll use daily.

## Repository layout

```
bashrc
README.md
config/
	hypr/
		bindings.conf
	waybar/
		config.jsonc
local/
	share/
		omarchy/
			default/
				hypr/
					input.conf
```

## Quick setup

Create symlinks into `$XDG_CONFIG_HOME` and `$XDG_DATA_HOME` so Omarchy picks up the overrides.

1) Hyprland (custom bindings)
- Link `config/hypr/bindings.conf` to `~/.config/hypr/bindings.conf`

2) Input/Gestures (override Omarchy defaults)
- Link `local/share/omarchy/default/hypr/input.conf` to `~/.local/share/omarchy/default/hypr/input.conf`

3) Waybar
- Link `config/waybar/` to `~/.config/waybar/`

Restart Hyprland or reload Waybar to apply changes.

## Notes

- Some bindings depend on your browser and installed apps (espetially web-apps); if missing, remove or replace the relevant lines in `bindings.conf`.
- If you don’t use Wiremix/Blueberry/pamixer, swap the Waybar actions for your stack.

---

Want more tweaks or to align styles across hosts? Open an issue or PR.
