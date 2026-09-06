# 20.Techfrost ORB & PDH-PDL Multi-Condition Options Engine

## Overview
**Techfrost ORB & PDH-PDL Multi-Condition Options Engine** is an advanced options trading indicator designed for multi-asset confluence analysis across Spot Index, Call Options (CE), and Put Options (PE). It evaluates four high-probability structural confluence conditions in real-time, combining Opening Range Breakouts (ORB 5M / 15M / 30M), Day Open LTP reference levels, and Previous Day High/Low (PDH/PDL) boundaries.

The script automatically detects underlying instruments, strike prices, and option types across index futures/options, equity stocks, and commodities, enabling seamless execution without manual ticker entry.

---

## Key Features

- **4 Multi-Asset Confluence Engines**:
  1. 🟢 **Condition 1 (CE UP)**: Spot & ATM CE LTP above ORB High & Day Open + ATM PE LTP below ORB Low & Day Open. (Green `#00E676`)
  2. 🔴 **Condition 2 (PE UP)**: Spot & ATM CE LTP below ORB Low & Day Open + ATM PE LTP above ORB High & Day Open. (Red `#FF1744`)
  3. 🟢 **Condition 3 (CE Over PDH)**: Spot & ATM CE LTP above PDH & Day Open + ATM PE LTP below PDL & Day Open. Marked as **Over PDH** in **Green (`#00E676`)**.
  4. 🔴 **Condition 4 (PE Over PDH)**: Spot & ATM CE LTP below PDL & Day Open + ATM PE LTP above PDH & Day Open. Marked as **Over PDH** in **Red (`#FF1744`)**.
- **Universal Multi-Asset Auto-Detection**:
  - Automatically identifies root tickers for `NIFTY`, `BANKNIFTY`, `FINNIFTY`, `MIDCPNIFTY`, `CRUDEOIL`, `GOLD`, and Equity Stocks.
  - Automatically calculates At-The-Money (ATM) strike prices and strike steps based on asset price tiers.
  - Works seamlessly on **Spot Index Charts**, **Call (CE) Option Charts**, **Put (PE) Option Charts**, and **Stock Charts**.
- **Dynamic Chart Level Plot Scaling**:
  - Automatically scales plotted ORB, Day Open, PDH, and PDL reference lines to match the active chart symbol scale (CE Option levels on CE charts, PE levels on PE charts, Spot levels on Spot charts).
- **First Breakout State-Change Signal Filtering**:
  - Prevents alert spam and label clutter by triggering signals **only once** on the exact candle of an initial breakout or state transition.
- **Customizable Signal Styling**:
  - Full control over label text, background colors, text colors, label sizing, and arrow positioning (Above/Below bar).
- **Native Alerting System**:
  - Pre-configured `alertcondition()` triggers and tick-by-tick `alert()` calls for automated execution and push notifications.
- **Real-Time Analytics Dashboard**:
  - Displays live LTP, Day Open, ORB High/Low, PDH/PDL boundaries, and current confluence state for Spot, ATM CE, and ATM PE in an on-chart table.

---

## Mechanics & Calculation Logic

### 1. Symbol & Ticker Resolution
The indicator extracts exchange prefixes and strike prices directly from `syminfo.ticker`. If applied on a Spot chart or Stock chart, it queries the live spot price and rounds to the nearest strike step to construct ATM CE and PE symbols automatically:
- **NIFTY / FINNIFTY / MIDCPNIFTY**: 50 Points step
- **BANKNIFTY / GOLD**: 100 Points step
- **CRUDEOIL**: 50 Points step
- **Equity Stocks**: Dynamic auto-step (1, 2.5, 5, 10, 20, 50) based on stock price level.

### 2. ORB Engine
Computes Opening Range High and Low over user-selected timeframes (5M, 15M, or 30M) from the start of the trading session.

### 3. Fail-Safe Data Resolution
All security calls employ tuple packing `[close, high, low, open, pdh, pdl]` with fallback logic (`na(ce_c) ? spot_c : ce_c`) to guarantee zero runtime errors or missing data on non-option chart views.

---

## Input Settings & Configuration

### 1. Instrument Settings
- **Underlying Asset**: Auto-Detect (default) or override (`NIFTY`, `BANKNIFTY`, `FINNIFTY`, `MIDCPNIFTY`, `CRUDEOIL`, `GOLD`, `Stock`).
- **Option Type**: Auto-Detect or manual (`Call (CE)`, `Put (PE)`).
- **Manual Strike Selection / Override**: Enter custom strike price (0 = Auto-detect).
- **Spot Symbol Override**: Optional custom spot symbol (e.g. `NSE:NIFTY`).

### 2. ORB & Reference Level Settings
- **Opening Range (ORB) Period**: 5 Minutes, 15 Minutes (default), or 30 Minutes.
- **Show Lines**: Toggle visibility for ORB High/Low, Day Open, and PDH/PDL reference lines.

### 3. Signal Formatting & Controls
- **Condition 1 to 4 Label & Color Styling**: Custom text, background colors, text colors, and shape positions.
- **Signal Trigger Mode**:
  - *First Breakout Only (State Change)*: Triggers once per breakout (Recommended).
  - *Every Bar While Active*: Triggers continuously while condition is met.
- **Require Candle Close Confirmation**: Toggles confirmed candle vs real-time intra-bar alerts.

---

## How to Use & Trade

1. **Apply Indicator**: Add to any Spot chart (e.g. `NSE:NIFTY`) or Option chart (e.g. `NSE:NIFTY24000CE`).
2. **Review Confluence Dashboard**: Check the top-right table to verify that Spot, ATM CE, and ATM PE are aligned in direction.
3. **Take Signals**:
   - **CE UP**: Enter Long CE when green `CE UP` signal label appears above ORB breakout.
   - **PE UP**: Enter Long PE when red `PE UP` signal label appears below ORB breakdown.
   - **Over PDH / Over PDL**: Trade major daily structural trend continuation signals.
4. **Set Up Alerts**: Click TradingView's Alert icon, select `20.Techfrost ORB & PDH-PDL Multi-Condition Options Engine`, and choose desired condition trigger.
