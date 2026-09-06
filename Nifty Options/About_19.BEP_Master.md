# 19.BEP Master

## Overview
**19.BEP Master** (formerly *Techfrost Multi-Strike BEP & Dynamic Step-Up Extension Analytics*) is a comprehensive options analytics engine built to plot Multi-Strike Break-Even Price (BEP) levels, Dynamic Realtime Step-Up Extension lines, and real-time tick-by-tick opposite option candles directly on TradingView charts.

It combines both **Realtime Dynamic BEP** (moving with tick-by-tick LTP) and **Static Reference BEP** (anchored to Day Open, Previous Close, or First 5 Min Close) across 7 strikes: At-The-Money (ATM), 3 In-The-Money (ITM 1..3), and 3 Out-Of-The-Money (OTM 1..3).

---

## Key Features

- **Multi-Strike BEP Grid (7 Strikes)**:
  - Plots **ATM (L0)**, **ITM (L-1, L-2, L-3)**, and **OTM (L+1, L+2, L+3)** Break-Even Price lines.
  - Supports separate **BEP Lines Offset Step** (5, 10, 15, 20, 25, 40, 50, 100, 150, 200 Points) to scale ITM and OTM levels at custom strike distances from ATM.
- **Dynamic Realtime Step-Up Extension Line**:
  - Plots an extension line formed immediately upon the **first crossover OR bounce back** of ATM/OTM/ITM BEP lines.
  - Automatically resets every morning to form a fresh daily line.
  - Breaks down instantly when price breaks through the level, initiating a fresh extension line on the next BEP crossover.
- **Tick-by-Tick Real-Time Opposite Option Candles**:
  - Overlays opposite option price candles directly on your primary chart in real-time (plots PE candles when viewing a CE chart; plots CE candles when viewing a PE chart).
- **Static BEP Reference Modes**:
  - Choice of reference basis: *Day Open LTP*, *Previous Day Settlement LTP*, or *First 5 Min Close LTP*.
- **Chart Symbol Isolation**:
  - Intelligently filters signals so Call (CE) charts display Call signals and Put (PE) charts display Put signals.
- **Universal Asset Auto-Detection**:
  - Supports `NIFTY`, `BANKNIFTY`, `FINNIFTY`, `MIDCPNIFTY`, `CRUDEOIL`, `GOLD`, and Equity Stocks.
- **Optimized Performance**:
  - Packed tuple security calls guarantee strict compliance under TradingView's 40-security-call limit, preventing plot wipes or performance slowdowns.

---

## Technical Mechanics & Formulas

1. **Break-Even Price (BEP) Formula**:
   $$\text{BEP}_{\text{CE}} = \text{Spot Price} + \text{Call Premium}$$
   $$\text{BEP}_{\text{PE}} = \text{Spot Price} - \text{Put Premium}$$
2. **Offset Resolution**:
   - `BEP Lines Offset Step` scales ITM and OTM strike distances (e.g. 50 pts, 100 pts) independently from the underlying strike step without altering the Dynamic Extension line calculation.
3. **Extension Line State Machine**:
   - Resets daily (`ext_stage = 0`).
   - On first BEP crossover or bounce back: Locks extension price and plots dynamic level.
   - On breakdown: Erases current line and primes state for next crossover.

---

## Input Settings & Configuration

### 1. Instrument Settings
- **Underlying Asset**: Auto-Detect, `NIFTY`, `BANKNIFTY`, `FINNIFTY`, `MIDCPNIFTY`, `CRUDEOIL`, `GOLD`, or `Stock`.
- **Option Type**: Auto-Detect, `Call (CE)`, or `Put (PE)`.
- **Manual Strike Selection / Override**: Custom strike price entry (0 = Auto-detect).

### 2. BEP Calculation Settings
- **Strike Offset Points**: 5, 10, 15, 20, 25, 40, 50, 100, 150, 200 Points.
- **Static BEP Basis**: Day Open LTP (default), Prev Day Settlement, or First 5 Min Close.

### 3. Feature Enable / Disable Switches
- Toggle Realtime BEP Lines, Static BEP Lines, ATM/ITM/OTM levels, Dynamic Extension Line, Opposite Candles Overlay, Signal Labels, Dashboard Table, and Alert Engine.

---

## How to Use & Trade

1. **Identify Key Levels**: Watch for interactions between option price and the Realtime vs Static BEP lines.
2. **Track Extension Line**: Use the Dynamic Step-Up Extension line as a trailing stop-loss or dynamic support/resistance level.
3. **Observe Opposite Candles**: Gauge relative strength between Call and Put option buyers/sellers directly on one chart.
