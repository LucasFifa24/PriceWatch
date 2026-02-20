# PriceWatch — PWA Price Alert App

A **Progressive Web App** that lets users set price alerts for stocks, crypto, forex, and indices using TradingView data. Installable on mobile and desktop, with browser push notifications.

## Features
- 🔍 Search stocks (NASDAQ/NYSE), crypto, forex, and indices
- 📊 Live prices fetched from TradingView's scanner
- 🔔 Push notifications when your price target is hit
- 📱 Installable as a mobile app (PWA)
- 🔄 Checks prices every 30 seconds in the background
- 💾 Alerts saved locally (persists across sessions)

## Deploy to GitHub Pages

### 1. Create a GitHub repository
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/pricewatch.git
git push -u origin main
```

### 2. Enable GitHub Pages
1. Go to your repo → **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Select branch: `main`, folder: `/ (root)`
4. Click **Save**

Your app will be live at:
`https://YOUR_USERNAME.github.io/pricewatch/`

### 3. Update manifest start_url (important!)
In `manifest.json`, update the `start_url` to match your GitHub Pages path:
```json
"start_url": "/pricewatch/"
```

## How It Works

### Price Data
Prices are fetched from **TradingView's free scanner API** via a CORS proxy (`allorigins.win`). Data updates every 30 seconds for active alerts.

### Notifications
The app uses the **Web Push API** + **Service Worker** to show native push notifications — even when the browser tab is closed (as long as the browser is running).

On iOS: notifications work when the app is installed to the home screen (iOS 16.4+).

### Supported Assets

| Category | Examples |
|----------|---------|
| Crypto | BTC, ETH, SOL, BNB, XRP |
| NASDAQ | AAPL, NVDA, TSLA, META, GOOGL |
| NYSE | JPM, WMT, SPY, QQQ, GLD |
| Forex | EURUSD, GBPUSD, USDJPY |
| Indices | SPX, NDX, VIX, DAX, NI225 |

## File Structure
```
/
├── index.html       # Main app
├── sw.js            # Service Worker (background & push)
├── manifest.json    # PWA manifest
├── icons/
│   ├── icon-72.png
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## CORS Note
TradingView's API is called through `allorigins.win` as a CORS proxy. This is fine for personal/low-traffic use. For production, consider hosting your own simple proxy or backend.
