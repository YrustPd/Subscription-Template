# Subscription Template for Marzban

![CI](https://github.com/YrustPd/Subscription-Template/actions/workflows/ci.yml/badge.svg)

A refined, dark-themed landing page that gives Marzban subscribers everything they need at a glance: account status, traffic usage, quick client links, QR sharing, and support resources. The template is written in Jinja-compatible HTML so it can be dropped straight into Marzban’s custom template directory.  
**Current release:** v1.0.0

---

## Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Enable Marzban subscription links](#enable-marzban-subscription-links)
  - [Deploy the subscription page](#deploy-the-subscription-page)
- [Customisation](#customisation)
- [Support & Contributions](#support--contributions)
- [License](#license)

---

## Features
- **Interactive actions:** One-tap copy, QR modal, and deep links for popular Marzban clients across iOS, Android, Windows, and Linux.
- **Live insight:** Status pills, usage meters with animated rails, renewal countdowns, and parsed server lists fed directly from Marzban context.
- **Support hooks:** Optional sponsor, support, and how-to URLs reveal extra buttons and content blocks for your users.
- **Accessibility polish:** Keyboard focus management, reduced-motion fallbacks, and safe-area padding for devices with display cut-outs.
- **Multilingual editions:** English (`template/index.html`) and Persian (`template/index.fa.html`) variants ship side-by-side with mirrored layout and typography.

## Prerequisites
- Marzban installed with shell access (Linux, macOS, or WSL recommended)
- An SSL certificate for your Marzban domain(s)
- `wget` or equivalent tool for fetching template assets

## Installation

### Enable Marzban subscription links
1. Generate an SSL certificate for your domain using the Marzban guide **How to generate SSL**, then activate it via **Activating SSL in Marzban** so both the dashboard and subscription link are served over HTTPS.
2. If the panel and subscription link share a domain, HTTPS activation is enough. For separate domains, obtain a multi-domain certificate and expose the subscription prefix in your `.env` (remove the leading `#`):
   ```dotenv
   XRAY_SUBSCRIPTION_URL_PREFIX=https://YOUR_DOMAIN:PORT
   ```
   **Attention:** If the panel listens on a port other than 443, include that port in the value above. Telegram bot integrations also require this variable; without it, links copied from the bot will be malformed.
3. Apply the changes by restarting Marzban:
   ```bash
   sudo marzban restart
   ```

The subscription link is now active. New users created via the Marzban panel or Telegram bot receive an up-to-date subscription URL; consult the official Configuration tutorial for details on optional variables.

### Deploy the subscription page
1. Download the template:
   ```bash
   sudo mkdir -p /var/lib/marzban/templates/subscription
   sudo wget -N -P /var/lib/marzban/templates/subscription/ https://raw.githubusercontent.com/YrustPd/Subscription-Template/main/template/index.html
   ```
   _Optional – Persian layout:_ replace the default template with the RTL version:
   ```bash
   sudo wget -N -O /var/lib/marzban/templates/subscription/index.html https://raw.githubusercontent.com/YrustPd/Subscription-Template/main/template/index.fa.html
   ```
2. Point Marzban to the template by editing `/opt/marzban/.env` (or the dotenv file used in your deployment) and uncommenting:
   ```dotenv
   CUSTOM_TEMPLATES_DIRECTORY="/var/lib/marzban/templates/"
   SUBSCRIPTION_PAGE_TEMPLATE="subscription/index.html"
   ```
3. Restart Marzban to load the new page:
   ```bash
   sudo marzban restart
   ```

Open any user’s subscription link in a browser to verify the result. The default favicon and preview banner are served from GitHub—no additional download is required. To change the default language, adjust the `<select>` element near the end of `index.html`.

## Customisation
- **Branding:** The template intentionally comments out both the `<link rel="icon">` tag and the `og:image` / `twitter:image` meta tags. By default they point to the hosted `logo-dark.png` on GitHub, so no extra download is required. Uncomment them (in `template/index.html` and `index.fa.html` if used) and, if desired, swap in your own icon/banner URL to enable the favicon and rich previews simultaneously.
- **Language:** Swap `index.fa.html` in place of `index.html` for a full Persian experience, or simply change the selected option in the language dropdown.
- **Client catalogue:** Update platform cards (icons, descriptions, and links) to match the client lineup you promote.
- **Support links:** Populate `support_url`, `sponsor_url`, and `how_to_url` when provisioning users (see `.env.example`) so the relevant buttons surface in the UI.

## Support & Contributions
- Track notable updates in [`CHANGELOG.md`](CHANGELOG.md).
- Community contributions are welcome; read [`CONTRIBUTING.md`](CONTRIBUTING.md) before opening a pull request.

## License
Distributed under the terms of the [GNU Affero General Public License v3.0](LICENSE).
