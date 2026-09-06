# 4.Techfrost Multi Strike BEP Lines

## Overview
**4. Techfrost Multi-Strike BEP Lines Analytics** is a specialized Pine Script v6 indicator designed to plot 7 distinct Break-Even Price (BEP) levels—At-The-Money (ATM), In-The-Money (ITM 1..3), and Out-Of-The-Money (OTM 1..3)—across multiple option strikes in real-time.

It provides traders with instant visual reference of institutional break-even thresholds, previous day settlement levels, and daily high/low boundaries for both Call and Put options.

---

## Key Features

- **7 Multi-Strike BEP Levels**:
  - **ATM (L0)**: At-The-Money Break-Even Level.
  - **ITM 1, ITM 2, ITM 3 (L-1, L-2, L-3)**: In-The-Money Break-Even Levels.
  - **OTM 1, OTM 2, OTM 3 (L+1, L+2, L+3)**: Out-Of-The-Money Break-Even Levels.
- **Customizable Strike Offset Steps**:
  - Select offset intervals: 5, 10, 15, 20, 25, 40, 50, 100, 150, or 200 Points to space out ITM and OTM strikes relative to ATM.
- **Dual BEP Plotting Engines**:
  - **Realtime Dynamic BEP**: Adjusts continuously tick-by-tick with live LTP movements.
  - **Static Level BEP**: Anchored to reference prices (*Day Open Price*, *Previous Day Close*, *Previous Day Settlement*, or *First 5 Min Close*).
- **Previous Day High, Low & Settlement Lines (PDC / PDH / PDL)**:
  - Plots Previous Day Settlement, High, and Low lines for both Call and Put options with color-coded transparency.
- **Opposite Option Candles Overlay**:
  - Displays real-time opposite option price candles directly on the chart for instant multi-asset price action comparison.
- **BEP Analytics Table**:
  - Displays live Call LTP, Put LTP, Static BEP, Realtime BEP, High, and Low values for all 7 strike levels in a clean table format.

---

## Mechanics & Formula

- **Call Break-Even Price**:
  $$\text{BEP}_{\text{CE}} = \text{Strike Price} + \text{Call Premium}$$
- **Put Break-Even Price**:
  $$\text{BEP}_{\text{PE}} = \text{Strike Price} - \text{Put Premium}$$

The indicator automatically constructs option symbols using user-selected or auto-detected root tickers (`NIFTY`, `BANKNIFTY`, `FINNIFTY`, `MIDCPNIFTY`, `CRUDEOIL`) and expiry formatting (`YYMdd`).

---

## Input Settings & Configuration

1. **Instrument & Strike Selection**:
   - Strike selection mode: *Auto-Detect (Chart Ticker)* or *Manual*.
   - Preset underlying or custom ticker entry.
   - Option suffix style (`C/P` or `CE/PE`).
2. **BEP Calculation Settings**:
   - Strike Offset Points (5..200 Points).
   - Static BEP Calculation Basis (Day Open, Prev Close, Prev Settlement, First 5 Min Close).
3. **Plot & Visual Controls**:
   - Toggle Realtime BEP, Static BEP, PDC lines, PDH/PDL lines, Opposite Candles, and Table Display.
   - Fully customizable line and candle colors.

---

## Use Cases

- **Intraday Options Trading**: Determine whether current option LTP is trading above or below institutional break-even thresholds.
- **Support & Resistance**: Use Static BEP lines as reliable intraday pivot boundaries.
