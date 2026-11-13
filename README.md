# ZCT Trade Replay

**Live:** https://tmoney-ak.github.io/zct-trade-replay/

A blind review for ZCT students. It replays their trades from their ZCT Trading Journal (Phase 4). Each chart stops on the candle before the entry, the student decides **Take it again** or **Wouldn't take it again**, and only then does the trade play out.

## For students

1. In your ZCT Trading Journal, click **Share** and set General access to **Anyone with the link · Viewer**. Copy the link.
2. Open the live page on a computer, paste the link and press **Load journal** (or upload the journal as .xlsx instead).
3. Check the detected timezone, choose how many trades (last 30 / 60 / 100, or a date range) and, ideally, your exchange. Press **Start replay**.
4. Judge each trade only on what you could see at the time. Add notes if you like.
5. On the summary, press **Export CSV** and send it to your coach.

## What the page does

- **Reads the journal** from its Google Sheets link (Trading Log tab: headers on row 5; B entry time, F strategy, G coin, H side, J entry, N stop, O target, R exit, S exit time, W result). Nothing is uploaded: the journal is only read in the student's browser.
- **Loads real 1-minute candles with USD volume** from the student's exchange first, then Binance, Bybit, Bitget, OKX, Gate and Hyperliquid (Binance and Bybit block US connections; Bitget and OKX answer there).
- **Works out the journal's timezone** from the trades themselves, including daylight saving (e.g. Central Europe), and corrects any single trade whose times don't match the candles.
- **Anchors the plan to the entry-time candle**: entry on that candle, stop / target / exit at the same % distances as in the journal (exchanges differ slightly in price).
- **Marks the systematic level** the trade was taken at, if any: previous 15m / 1h / 4h, day, week, month high or low, or all-time high / low (P15H, P1L, PDH…).
- **Summary**: take again vs wouldn't take again, the result of only the trades you'd take again, a breakdown by strategy and by direction, every trade with the student's notes, and CSV / JSON export.

## Updating it

The page is the single file `index.html` (plain HTML and JavaScript, no build step). Edit it, commit and push to `main`; GitHub Pages republishes within a minute or two. A copy also lives in the private ZCT-Journal repo at `trade-replay/trade-replay.html`.
