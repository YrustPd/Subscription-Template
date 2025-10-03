# Marzban Installation Notes

Deploy the Subscription Template alongside an existing Marzban setup by following the steps below.

## Enable Subscription Links
1. Generate an SSL certificate for your domain using Marzban's "How to generate SSL" guide.
2. Enable HTTPS on the panel with the "Activating SSL in Marzban" tutorial so both the dashboard and subscription URL serve over TLS.
3. If panel and subscription pages use different hostnames, obtain a multi-domain certificate and edit `/opt/marzban/.env`:
   ```env
   XRAY_SUBSCRIPTION_URL_PREFIX=https://YOUR_DOMAIN:PORT
   ```
   Include the panel port when it differs from `443`.
4. Apply the changes:
   ```bash
   marzban restart
   ```

## Install the Subscription Page
1. Ensure the custom template directory exists:
   ```bash
   sudo mkdir -p /var/lib/marzban/templates/subscription/
   ```
2. Copy the desired template (English or Persian) and favicon:
   ```bash
   sudo cp /path/to/Subscription-Template/template/index.html /var/lib/marzban/templates/subscription/index.html
   ```
   ```bash
   sudo cp /path/to/Subscription-Template/template/leaves-icon.png /var/lib/marzban/templates/subscription/leaves-icon.png
   ```
   *Swap `index.html` with `index.fa.html` for the Persian interface.*
3. Register the template in `/opt/marzban/.env`:
   ```env
   CUSTOM_TEMPLATES_DIRECTORY="/var/lib/marzban/templates/"
   SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
   ```
   *Change the filename to `subscription/index.fa.html` when deploying the Persian template.*
4. Restart Marzban and open any subscriber link in a browser to verify the new layout.

## Customisation Checklist
- Provide a `support_url` value or edit the template placeholders for your preferred contact channel.
- Refresh client download URLs to match the applications you promote.
- Align imagery, copy, and colours with your brand guidelines while retaining the hosted favicon reference.

## License
See `../LICENSE` for licensing terms.
