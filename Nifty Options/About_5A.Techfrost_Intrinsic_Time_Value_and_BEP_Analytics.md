# 5A.Techfrost Intrinsic Time Value and BEP Analytics

## Overview
**5A. Techfrost Intrinsic Time Value and BEP Analytics** is an advanced options valuation indicator designed to isolate and decompose Option Premiums into their two core component values: **Intrinsic Value (IV)** and **Time Value (TV / Extrinsic Value)** for both Call (CE) and Put (PE) contracts.

By separating price movements into real intrinsic equity value and decaying time premium, traders can identify option mispricings, volatility expansion/compression, and high-probability entry setups.

---

## Key Features

- **Real-Time Intrinsic & Time Value Decomposition**:
  - Computes real-time **Call Intrinsic Value**, **Put Intrinsic Value**, **Call Time Value**, and **Put Time Value**.
- **PE Intrinsic Inversion (Zero-Line Oscillator View)**:
  - Option to plot Call Intrinsic above the 0 line (+y) and Put Intrinsic below the 0 line (-y), creating a clean zero-centered momentum oscillator.
- **Multi-Strike Modes**:
  - Select between **ATM (At The Money)**, **ITM (In The Money)**, **OTM (Out of The Money)**, or **Both ITM & OTM**.
- **Average Intrinsic & Time Value Analytics**:
  - Calculates real-time average Intrinsic and Time Value across corresponding ITM and OTM strikes to evaluate overall option basket pricing.
- **5-Day Static Historical Reference Metrics**:
  - Plots 5-day historical static reference lines for CE/PE Intrinsic, Time Value, Prev Day Close, and Static BEP.
- **Signal Shape Labels (BC / BP)**:
  - Generates **Buy Call (BC)** and **Buy Put (BP)** signal labels based on Intrinsic & Time Value crossovers.
  - Supports signal filtering: *All Candles (Raw)*, *Initial Trigger Only*, or *Alternate Signals Only (Wait for Opposite)*.
- **Analytics Dashboard Table**:
  - Displays real-time breakdown of Call/Put LTP, Intrinsic Value, Time Value, and BEP levels in an on-chart table.

---

## Technical Formulas & Mechanics

1. **Intrinsic Value (IV)**:
   $$\text{CE Intrinsic} = \max(0, \text{Spot Price} - \text{Strike Price})$$
   $$\text{PE Intrinsic} = \max(0, \text{Strike Price} - \text{Spot Price})$$
2. **Time Value (TV / Extrinsic Value)**:
   $$\text{Time Value} = \text{Option LTP} - \text{Intrinsic Value}$$
3. **Break-Even Price (BEP)**:
   $$\text{BEP}_{\text{CE}} = \text{Strike Price} + \text{Call Premium}$$
   $$\text{BEP}_{\text{PE}} = \text{Strike Price} - \text{Put Premium}$$

---

## Input Settings & Configuration

### 1. Calculation Settings
- **Strike Selection Mode**: `ATM`, `ITM`, `OTM`, or `Both ITM & OTM`.
- **Strike Offset Points**: 5, 10, 15, 20, 25, 40, 50, 100, 150, 200 Points.
- **Static Calculation Basis**: Day Open Price (default), Prev Day Close, First 5 Min Close.
- **Time Value Formula**: Standard (`LTP - IV`) or Custom (`Strike - IV`).

### 2. Plot Visibility & Visuals
- Toggle Realtime CE/PE Intrinsic, Invert PE Intrinsic, Avg Intrinsic, CE/PE Time Value, 5-Day Static Metrics, Signal Shapes (`BC`/`BP`), and Analytics Table.

---

## How to Trade with IV & TV Analytics

1. **Spot Intrinsic Expansion**: Rapid expansion in Intrinsic Value indicates strong directional momentum driven by underlying asset price movement.
2. **Time Decay Tracking**: Shrinking Time Value near key support/resistance signals option premium deflation, helping options sellers time theta decay or buyers avoid elevated implied volatility.
