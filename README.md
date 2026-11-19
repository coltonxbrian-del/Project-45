# TRADE//45 — iPhone Day Trading PWA

A dark, mobile-first trading dashboard for GitHub Pages. The included paper-trading engine is functional and stores its practice account in the browser's `localStorage`.

## Features

- Dashboard with account equity, cash, demo market snapshot and watchlist
- Demo market list with search and asset filters
- Generated candlestick chart with selectable timeframes
- Paper buy/sell order ticket, market and limit order types
- Portfolio holdings, unrealized P/L and allocation
- Order history and CSV export
- Local account persistence and reset
- Installable PWA manifest, service worker and app icons
- Responsive iPhone layout with safe-area spacing

## Important: demo data and live trading

This repository intentionally ships with **simulated sample prices**. It does not fetch live exchange quotes. The chart is generated locally. Do not treat any value, movement, or chart as a real quote, recommendation, or signal.

Paper trades are simulated locally in your browser and are not sent to a broker.

The Live connection selector is an integration placeholder. GitHub Pages is static hosting; it cannot safely hold brokerage API keys or perform secure server-side authorization. To enable real-money trading, build a separate backend service that:
1. Authenticates the user with the broker's supported OAuth/API flow.
2. Stores credentials only in server-side secret storage.
3. Validates symbol, side, quantity, order type, buying power and user confirmation.
4. Applies risk limits, rate limits, audit logging and idempotency.
5. Submits orders to the broker and returns verified order status.
6. Uses HTTPS, secure sessions, CSRF protections and least-privilege scopes.

Never commit API keys, tokens, passwords or account credentials to this repository or browser JavaScript. Connect only a regulated brokerage available in your jurisdiction and review its terms and trading risks.

## Run locally

You can open `index.html` for basic testing, but PWA installation and service workers require HTTPS or localhost.

With Python installed:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000` in your browser.

## Publish with GitHub Pages

1. Create a GitHub repository, for example `trade45`.
2. Upload all files and folders from this project to the repository root.
3. On GitHub, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose branch `main` and folder `/ (root)`, then save.
6. Wait for the Pages deployment to finish. Your URL will look like `https://YOUR-USERNAME.github.io/trade45/`.

If using a custom repository name, keep the relative asset paths (`./styles.css`, `./app.js`, etc.) as supplied.

## Install on iPhone

1. Open the published HTTPS GitHub Pages URL in Safari.
2. Tap the Share button.
3. Choose **Add to Home Screen**.
4. Edit the name to `TRADE//45` if desired, then tap **Add**.
5. Launch it from the Home Screen. The service worker caches the app shell for offline access after the first successful load.

Market data is not refreshed while offline. Browser storage is local to that browser/device and is not synced between devices.

## Project structure

```text
TRADE45/
├── index.html
├── styles.css
├── app.js
├── manifest.webmanifest
├── service-worker.js
├── assets/
│   ├── icon.svg
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## Testing checklist

- [ ] Navigate between all five bottom tabs and Settings
- [ ] Search/filter the demo market list
- [ ] Open a symbol and inspect its generated chart
- [ ] Place a paper buy order and confirm cash/position updates
- [ ] Sell a held quantity and confirm realized P/L
- [ ] Reload and confirm the paper account persists
- [ ] Export history to CSV
- [ ] Reset the paper account
- [ ] Verify Add to Home Screen on iPhone Safari
- [ ] Verify offline app-shell loading after first visit

## Customization

- Edit the `market` array at the top of `app.js` to change demo symbols and sample prices.
- Adjust colors in the `:root` variables in `styles.css`.
- Change the starting practice balance with `STARTING_CASH` in `app.js`.
- Update app name, theme color and icons in `manifest.webmanifest` and `assets/`.
