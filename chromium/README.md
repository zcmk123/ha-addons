# Chromium (Home Assistant Add-on)

Chromium browser exposed through a web-based GUI (Ingress supported). This add-on is based on the `jlesage/chromium` container image.

## Usage

- Open the add-on panel from the Home Assistant sidebar.
- Use Ingress for normal usage (no manual port mapping required).

## Ports

- `5800/tcp`: Web UI (not required when using Ingress)
- `5900/tcp`: VNC (optional, not required when using Ingress)

## Persistent storage

- The container uses `/config` for its internal state.
- Downloads are typically stored under the mapped Home Assistant folders (for example `/share`), depending on your usage inside Chromium.

## Configuration

This add-on exposes common `jlesage/chromium` environment variables via the add-on configuration.

Notable options:

- `LANG`, `TZ`: Locale and timezone.
- `DISPLAY_WIDTH`, `DISPLAY_HEIGHT`: Default window size.
- `WEB_AUDIO`: Enable audio over the web UI.
- `WEB_FILE_MANAGER`, `WEB_TERMINAL`: Enable file manager / terminal in the web UI.
- `WEB_AUTHENTICATION`: Enable login protection for the web UI (requires secure connection/HTTPS).
- `SECURE_CONNECTION`: Enable HTTPS and encrypted VNC.
- `VNC_PASSWORD`: Set a VNC password.
- `CHROMIUM_APP_URL`: Start Chromium in “app mode” for a specific URL.

## Notes

- Enabling secure features (HTTPS, authentication) is recommended if you expose this add-on beyond a trusted network.
