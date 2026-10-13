# allowme

Local push-to-talk dictation: hold a key, speak, and the text is typed where the cursor is. Nothing you say leaves the computer.

This repository only holds the downloads. For now allowme is built for Omarchy (Arch Linux with Hyprland) on 64-bit Intel/AMD computers.

## Install or update

```sh
curl -fsSL https://github.com/mfbaltaza/allowme-releases/releases/latest/download/install.sh | bash
```

It downloads the program and the speech models that fit the computer (about 5.5 GB with a graphics card of 6 GB or more, about 0.5 GB without), starts allowme with your session, and opens the settings page.

Running the command again updates allowme and keeps your settings.

## Start dictating in two minutes

1. **Open the settings page.** It opens by itself at the end of the install. Later: search for `allowme` in the app launcher, or run `allowme settings`.
2. **Pick your key** on the **Shortcut** tab: press `Change` next to Dictation key, then press the key (e.g. `F8`). The service binds it in Hyprland itself; nothing is written to your Hyprland config.
3. **Check your microphone** on the **Microphone** tab: speak and watch the level move. If it stays flat, pick the right input device.
4. **Dictate.** Click into any text field, hold the key, speak, and release — the words are typed where the cursor is.
   - **Tap** the key (a press under ~300 ms) to start hands-free; tap again to finish.
   - **`Esc`** cancels a running dictation.
   - A small pill shows what is happening: listening while you speak, thinking while it cleans up, and a failed state if something went wrong (the raw transcript is typed instead, so nothing is lost).
5. **Teach it names** on the **Dictionary** tab: add what the speech model writes and what should be typed instead (e.g. a name it keeps misspelling).

## Everyday use

- **The key just works** from login on: allowme starts with your graphical session.
- **Mode tab:** `Pro` cleans up filler words and grammar with a local model; `Light` only applies your dictionary and costs no extra time. On machines without a suitable graphics card only `Light` is available.
- **Tray icon:** an `a;` icon sits in the system tray; click it or choose `Open settings` to get back to the settings page.
- **It types, never posts:** line breaks in your speech are typed as Shift+Enter, so dictating in a chat app never sends the message by accident.

## Useful commands

```sh
allowme settings   # open the settings page again
allowme status     # is the service running, is clean-up on?
allowme mic        # record 3 seconds and report microphone loudness
allowme stop       # stop the service (the key does nothing until next start)
allowme start      # start it in the background
allowme restart    # stop + start
allowme cleanup off | on | toggle   # raw transcript vs cleaned-up text
```

## If the key does nothing

1. `allowme status` — is the service running?
2. Settings page → Shortcut tab — is a key set? A key another shortcut already uses is refused.
3. After a Hyprland reload the service puts its keys back by itself; if in doubt, `allowme restart`.
4. No Hyprland on the machine? The key binding works through Hyprland only; elsewhere bind `allowme press` / `allowme release` by hand (the Shortcut tab says so when it cannot bind).
