# Currency Converter

*Current version: v1.3.0 — matches what's live at the URL below. If you update the site, bump this number to keep this README in sync.*

A single-file, no-install currency converter and bill-splitting tool built for travel. Download `index.html` and it works completely offline — handy when you're traveling and don't have signal or don't want to pay for roaming data. Prefer not to download anything? Just use it directly from the live URL below instead.

**Live:** https://msui.github.io/currency-converter/

## Features

### Conversion
- Convert between **39+ built-in currencies**, including USD, EUR (with dedicated Spain 🇪🇸 and France 🇫🇷 entries), GBP, JPY, MXN, INR, THB, AED, BRL, TRY, and many more
- **Add a currency not listed** — type any ISO currency code and it's validated live against a real exchange-rate source before being added. If the code's smallest unit (like "cent" or "paisa") isn't already known, you'll be asked once; otherwise it's detected automatically
- **Edit or remove** any currency you've added yourself — rename it in place (handy for fixing a typo) or delete it, right from the currency picker
- **Add multiple amounts at once** — type `320 + 45 + 12` and hit Convert to sum everything before converting
- **"In words"** — for larger results, the exact amount is spelled out in full ("Twenty-nine million, six hundred sixty-four thousand, two hundred Indian Rupees and six paise"), using the correct minor-unit name for that specific currency, not just a generic rounded estimate

### Exchange rates
- Pulled from the **European Central Bank's official reference rates** (via the free, keyless [Frankfurter API](https://frankfurter.dev)), with an automatic backup source if the ECB feed is ever unavailable
- A visible warning banner appears if the rate hasn't refreshed in over 12 hours, dismissible per occurrence
- Tap anywhere on the Exchange Rate card to refresh, not just the refresh icon

### Splitting & tipping
- **Split the Cost** — pick a number of people and a tip percentage (0–20%, or a custom amount) to see what each person owes, with and without tip
- **Standalone Tip Calculator** — tucked into Settings, for calculating a tip without doing any currency conversion at all
- **Copy a plain-text summary** of any split to paste into a text message

### Appearance
- Light and dark mode
- Two background styles — **Basic & Flat** or a **Rainbow** gradient — each rendered correctly in both light and dark mode
- A liquid-glass visual style on the main cards, with color choices verified against WCAG 2.2 AA contrast requirements across every theme/background combination

### Other
- Recent conversion history
- Everything (currency pairs, custom currencies, theme, background) is remembered on that device via local storage — no account needed

## Usage

1. Download `index.html`
2. Open it in any modern browser (Chrome, Safari, Firefox, Edge)
3. That's it — everything runs client-side

## Hosting it for your group

- **GitHub Pages**: enable Pages for this repo (Settings → Pages → deploy from the `main` branch). Since this file is named `index.html`, it's served directly at your repo's root URL with no extra path.
- **Any static host** (Netlify, Vercel, a personal site, etc.) works the same way — it's just one HTML file.

## Accessibility

This app is built with the intention of meeting **WCAG 2.2 Level AA**. That's a goal we actively design and test against, not a certification — see the caveat at the end of this section. Things built in specifically:

- **Numerically verified color contrast** — every text/background combination (including across light mode, dark mode, and both background styles) has been checked against the actual 4.5:1 (text) and 3:1 (UI component) ratios WCAG AA requires, not just eyeballed
- **A consistent design-token system** for color, specifically so that a future change to one part of the app can't silently break contrast somewhere else without it being easy to re-check
- **Visible keyboard focus indicators** on every interactive control — inputs, buttons, tabs, and the currency toggle — not just the browser's default (or a silently removed one)
- **Real accessible names on every icon-only button** (refresh, settings, dismiss, edit), so screen readers announce what each one does, not just an unlabeled icon
- **Live regions** on key status messages (exchange rate freshness, currency add/validation feedback) so screen reader users are told about changes without needing to already be focused on that exact spot
- **Pinch-zoom and text resizing are never blocked** — the page doesn't disable browser zoom
- **Icon buttons use real SVG icons**, not text characters standing in for icons, so stroke weight and centering stay consistent regardless of font
- **No information is conveyed by color alone** — status messages (like a currency add succeeding or failing) differ in wording, not just color

**Caveat:** this reflects careful code-level review and testing against WCAG's technical criteria — it has not been audited by a professional accessibility auditor, nor tested by actual assistive-technology users. Anyone who runs into a real barrier using this app, please open an issue.

## Notes

- Exchange rates update once daily (the ECB's normal publishing schedule), not tick-by-tick — plenty accurate for trip budgeting, not for trading.
- Everything is saved locally in that browser only — nothing is sent to a server, and nothing is shared between devices.
- Currencies you add yourself are validated against a live exchange-rate source, but their display name and (when needed) minor-unit name are whatever was typed in — there's no spellcheck against those, which is why the edit/rename option exists.

## License

Feel free to use, modify, and share this with your travel group.

