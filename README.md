# Subscription Template

Glassmorphism subscription landing template tailored for Marzban deployments. It surfaces real-time usage metrics, account status, client download links, and support routes using the data Marzban injects into Jinja templates.

## Key Features
- Responsive layout optimised for desktop and mobile subscribers.
- Data-driven quota, status, expiry, and sync details sourced from `user` and `panel` variables.
- Hosted 512×512 PNG favicon referenced by URL to avoid bundling extra assets.
- CDN-delivered modern-normalize and Font Awesome for consistent baseline styling.
- Fully localised Persian (RTL) variant at `template/index.fa.html` alongside the English template.

## Template Variants
- `template/index.html` – English interface.
- `template/index.fa.html` – Persian interface using the Shabnam font stack.
- `template/leaves-icon.png` – Shared favicon served from the repository.

## Usage
1. Copy the preferred template file into your Marzban subscription templates directory (see `docs/README.md` for deployment steps).
2. Update support metadata (`support_url`, social links, sponsor text) to align with your brand.
3. Adjust client download destinations or platform cards as needed; keep `template/leaves-icon.png` in sync if you change the favicon URL.

## Roadmap
Soon as possible we will support Marzneshin if peaple support us.

## License
See `LICENSE` for full licensing terms.
