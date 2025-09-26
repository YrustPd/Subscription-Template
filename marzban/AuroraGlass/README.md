# AuroraGlass Template

AuroraGlass is a Marzban dashboard skin that pairs a glassmorphism aesthetic with responsive telemetry and one-tap client imports.

## Key Features

- Animated usage meter with unlimited-plan awareness.
- Live subscription countdown with graceful "Endless" handling.
- Instant launch buttons for Sing Box, V2Box, v2rayNG, v2rayN, and Hiddify.
- Accessible modal QR importer with lazy-loaded QRCodeJS and a floating quick-action dock.

## Favicon & Link Preview

- `favicon.png` (included) is used automatically for the site favicon and Open Graph/Twitter previews. Replace it with your own 256×256 image to rebrand the template.
- Social previews surface the username, humanised status, and traffic summary for quick account checks inside messaging apps. Set `support_url` (used to populate `<meta name="support-url">`) to append a sponsor link in previews; leave it blank to hide it.

## Installation Steps

1. **Download the template assets**
   ```sh
   sudo wget -N -P /var/lib/marzban/templates/subscription/ https://raw.githubusercontent.com/x0sina/marzban-sub/main/index.html
   sudo wget -N -P /var/lib/marzban/templates/subscription/ https://raw.githubusercontent.com/x0sina/marzban-sub/main/favicon.png
   ```

2. **Point Marzban at your custom templates directory**
   ```sh
   echo 'CUSTOM_TEMPLATES_DIRECTORY="/var/lib/marzban/templates/"' | sudo tee -a /opt/marzban/.env
   echo 'SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"' | sudo tee -a /opt/marzban/.env
   ```

   Alternatively, edit `/opt/marzban/.env` and uncomment or add:
   ```env
   CUSTOM_TEMPLATES_DIRECTORY="/var/lib/marzban/templates/"
   SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
   ```

3. **Restart Marzban**
   ```sh
   sudo marzban restart
   ```

### Update
To update the template, repeat step 1 (re-download the `index.html` and `favicon.png`).

## Customisation

- Modify CSS custom properties under `:root` to retheme colours and radii.
- Extend the `data-open-template` anchors for additional client apps. The script provides `{url}`, `{url_encoded}`, `{username}`, and `{username_encoded}` placeholders.
- Maintain the SVG symbol registry (`#icon-v2ray`, `#icon-hiddify`) if you add further inline icons to keep markup lean.

## License

This template is distributed under the GNU AGPL-3.0. See the repository [LICENSE](../../LICENSE).
