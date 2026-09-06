# 18.Techfrost Nifty_V6_SR

## Overview
**18.Techfrost Nifty_V6_SR** is a comprehensive options chain support and resistance (S/R) engine designed for index futures, equity options, and underlying spot charts. It constructs dynamic Pivot, Resistance (R1–R5), and Support (S1–S5) levels derived directly from option chain pricing, implied volatility, Intrinsic/Extrinsic values, Option VWAP, and Cumulative Volume Delta (CVD) across an 11-strike array (ATM-5 to ATM+5).

---

## Key Features

- **Options-Chain Support & Resistance (S/R) Projections**:
  - Plots **Pivot (BEP)**, **R1 to R5 (Resistance)**, and **S1 to S5 (Support)** levels projection-mapped directly onto option or spot charts.
  - Supports multiple rendering modes: *Standard Plots*, *Horizontal Lines (Projected to Right)*, *Circles (Dotted Pattern)*, *Solid Line*, *Stepline*, *Line with Breaks*, and *Crosses*.
  - Option to enable **Dynamic Volume Delta Colors** (Bullish Green / Bearish Red) based on net volume flow at S/R levels.
- **Intrinsic & Extrinsic (Time Value) Overlays**:
  - Calculates real-time **Call Intrinsic**, **Put Intrinsic**, **Call Extrinsic**, **Put Extrinsic**, **Average Intrinsic**, and **Average Extrinsic** values.
  - Features dedicated **Spot Chart Overlay Modes** (*Symmetric Channels*, *Option-Chain Level Projections*) to prevent y-axis scale distortion on spot index charts.
- **Option VWAP Analytics**:
  - Plots real-time Volume Weighted Average Price (VWAP) for both Call (CE VWAP) and Put (PE VWAP) selected contracts.
- **Cumulative Volume Delta (CVD) & Volume Analytics (11-Strike Array)**:
  - Queries real-time tick-by-tick data across 11 strikes (ATM-5 to ATM+5) using optimized fixed-iteration loops and tuple security calls.
  - Evaluates volume delta and CVD across configurable timeframes (1M, 3M, 5M, 15M, 30M, or Chart Timeframe).
- **Swing Reversal & Probability Analytics**:
  - Marks major swing high/low reversal points with volume delta and reversal probability metrics.
- **Opening Range Breakout (ORB) & Running BEP Lines**:
  - Configurable ORB breakout duration (1M, 3M, 5M, 15M, 30M) and strike modes (ATM, ITM, OTM).
  - Plots continuous real-time Running BEP lines.
- **Opposite Option Historical Candles Overlay**:
  - Renders opposite option historical candles (CE on PE charts / PE on CE charts) with custom body and wick color controls.
- **Previous Day High/Low (PDH / PDL)**:
  - Displays previous session high and low boundary reference lines.

---

## Technical Mechanics & Calculation Logic

### 1. 11-Strike Options Array
Queries an 11-strike array (`ATM - 5 * Step` to `ATM + 5 * Step`) on every tick using packed tuple security calls:
- Extracts Day Open, Previous Day Close, High, Low, Volume, and VWAP for CE and PE contracts.
- Consumes only 6 explicit security calls for CVD volume queries, ensuring strict adherence to TradingView runtime limits.

### 2. Spot Chart Scale Distortion Prevention
When applied to a Spot Index chart (e.g. `NSE:NIFTY`), options S/R levels and Intrinsic values are projected relative to spot strike channels (`Strike ± Option Premium`) to prevent squishing spot candles.

---

## Input Settings & Configuration

1. **Symbol & Strike Parsing**:
   - Strike step size (default 50 for Nifty, 100 for BankNifty).
   - Exchange prefix (`NSE`), underlying ticker (`NIFTY`, `BANKNIFTY`), and expiry format (`YYMMDD`).
   - ATM strike selection mode (*Automatic* or *Manual*).
2. **Base Calculation Preferences**:
   - Calculation basis: *Day Open Price* or *Previous Day Settlement/Close*.
3. **Plot & Style Settings**:
   - Toggles for Intrinsic/Extrinsic, S/R, Opposite Candles, VWAP, ORB, PDH/PDL, and Swing Reversals.
   - Customized color palette for Pivot, R1-R5, S1-S5, VWAPs, and Intrinsic/Extrinsic lines.
4. **CVD & Volume Settings**:
   - Timeframe selection for CVD & Volume Delta calculations.

---

## How to Trade with Nifty_V6_SR

1. **Targeting & Breakout Validation**: Use R1-R5 and S1-S5 as dynamic price targets and invalidation zones during intraday breakout moves.
2. **Institutional VWAP Confluence**: Trade breakouts when option LTP crosses above both its Option VWAP and the Pivot (BEP) line with positive CVD volume delta.
3. **Swing Reversals**: Look for exhaustion signals near S4/S5 or R4/R5 when volume delta diverges from price direction.
