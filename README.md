# z.ai Billing Bookmarklet

One-click billing dashboard for [z.ai](https://z.ai). Fetches your complete usage history and shows it as an interactive overlay with charts, breakdowns, and CSV export.

No API keys to manage. No installation. Works right from your bookmarks bar.

## What you get

- **Summary cards** - total cost, API calls, tokens, active days
- **Daily cost chart** - color-coded bars for the last 60 days
- **Monthly breakdown** - cost per month at a glance
- **Model breakdown** - see which models cost the most
- **Token composition** - cache, input, and output split
- **Insights** - busiest day, costliest day, averages, monthly projection
- **CSV export** - download your full billing history as a spreadsheet

Everything runs in your browser. No data is sent anywhere else.

## Install

1. Show your **Bookmarks Bar** in Chrome: `Ctrl+Shift+B` (Mac: `Cmd+Shift+B`)
2. Open the [bookmarklet page](https://mufradhossain.github.io/z-ai-billing-bookmarklet/)
3. **Drag the button** onto your bookmarks bar

## Use

1. Go to [z.ai](https://z.ai) and make sure you're **logged in**
2. Click the bookmark
3. Your billing dashboard appears. Download CSV when you're done.

## How it works

- Reads your auth token from `localStorage` (key: `z-ai-open-platform-token-production`)
- Decodes your JWT to find your account creation date and customer ID
- Fetches billing data from `api.z.ai` for every month since account creation
- Handles pagination automatically (the API has a 30-day max range)
- Aggregates and renders everything as a dashboard overlay

No data leaves your browser. The token is used only for API calls to `api.z.ai` from your own session.

## Requirements

- A [z.ai](https://z.ai) account with billing history
- A modern browser (Chrome, Firefox, Edge, Safari)
- JavaScript enabled

## Limitations

- The z.ai billing API has a 30-day max range per request. The bookmarklet automatically chunks requests across all months.
- Some billing records may have zero token counts but non-zero cost (e.g., search/tool calls billed per request rather than per token).
- The token must be fresh. If you get an auth error, reload z.ai and try again.

## License

MIT
