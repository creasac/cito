<h3 align="center">🔍 cito</h3>

<p align="center">Search the web from anywhere on your desktop.<br>The name <code>cito</code> comes from Latin, meaning “quickly” or “swiftly.”</p>

---

A tiny Linux launcher that opens websites or searches Google in your default browser, from a keyboard shortcut. No autocomplete, bookmarks or history suggestions.

## Install

Requires Python 3, PyGObject, and GTK 3. On Ubuntu/Debian, install any missing dependencies:

```sh
sudo apt install python3 python3-gi gir1.2-gtk-3.0
```

From the directory containing `cito`:

```sh
install -Dm755 cito "$HOME/.local/bin/cito"
```

Run it to check the dialog:

```sh
"$HOME/.local/bin/cito"
```

In GNOME Settings, open **Keyboard → Custom Shortcuts** and add:

- **Name:** cito
- **Command:** the absolute path to the installed executable
- **Shortcut:** an unused combination, such as **Super+G**

Print the exact command to paste into the shortcut settings:

```sh
printf '%s\n' "$HOME/.local/bin/cito"
```

On other desktops, bind the same command using their keyboard shortcut settings.

## Use

Press your shortcut, type, and press **Enter**:

| Input | Action |
| --- | --- |
| `https://example.com/page?q=hello#section` | Open the URL, preserving its query and fragment |
| `example.com` | Open `https://example.com` |
| `C++ & C#` | Search Google for the text |

The dialog opens empty. **Escape** or an empty submission cancels. Pressing the shortcut again clears and reuses the open dialog. Control characters are rejected; ambiguous input becomes a search.

## Privacy and browser behavior

The launcher does not save your input. It makes no network requests before you submit; searches go to Google. Your browser's normal history, cookies, and privacy settings still apply.

Links open through the system's default HTTP/HTTPS browser handler. The browser chooses the profile, window, and workspace; the launcher does not force them. There is no background daemon, extension, or server.

## Platform support

Tested on Ubuntu GNOME with X11. The launcher uses GTK 3 and standard browser dispatch, without X11-specific runtime tools. Other desktops, Wayland, and browser selection between multiple profiles have not been verified.

## Uninstall

Remove the custom shortcut in your desktop's settings, then delete the executable:

```sh
rm "$HOME/.local/bin/cito"
```

## License

[MIT](LICENSE), copyright 2026 creasac.
