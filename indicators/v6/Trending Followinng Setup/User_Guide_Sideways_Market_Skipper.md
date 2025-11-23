# User Guide: Trend Following Setup - Sideways Market Skipper Scanner

## Overview
The **Sideways Market Skipper Scanner** is a comprehensive trading tool designed to help you identify trend-following setups while avoiding choppy, sideways markets. It combines a **Supertrend** indicator with a **Volatility Range** (based on ATR) to filter out false signals. It also includes a **Multi-Symbol Scanner** to monitor up to 40 assets directly from your chart.

---

## Visual Elements: What You See on the Chart

### 1. Supertrend (The Trend Filter)
-   **Green Line (Below Price)**: Indicates a **Bullish (Up)** trend.
-   **Red Line (Above Price)**: Indicates a **Bearish (Down)** trend.
-   **Background Fill**: The area between the price and the Supertrend line is shaded (Green for Up, Red for Down) to visualize the trend direction clearly.

### 2. Volatility Range (The "Skipper")
This is the core feature that helps "skip" sideways markets.
-   **Top Range (Green Stepped Line)**: Plotted above the price during a bullish trend.
-   **Bottom Range (Red Stepped Line)**: Plotted below the price during a bearish trend.
-   **Logic**: A signal is only generated when the price **breaks out** of this volatility range, confirming strong momentum. If the price stays within the range, it's considered "sideways," and no signal is taken.

### 3. Signals
-   **Green Triangle (Below Bar)**: **LONG Signal**.
    -   *Condition*: Price is in an Uptrend AND breaks above the "Top Range" AND passes all enabled filters.
-   **Red Triangle (Above Bar)**: **SHORT Signal**.
    -   *Condition*: Price is in a Downtrend AND breaks below the "Bottom Range" AND passes all enabled filters.
-   **Bar Colors**:
    -   **Light Green Bar**: Indicates a Long Signal candle.
    -   **Light Red Bar**: Indicates a Short Signal candle.

### 4. Scanner Table
Located by default at the **Bottom Left** of your chart.
-   **Symbol**: The ticker name.
-   **Time**: Time of the signal.
-   **Price**: Current price or signal price.
-   **%Chg**: Daily percentage change.
-   **V %Chg**: Volume percentage change (relative to previous day).
-   **Colors**:
    -   **Green Row**: Active **LONG** signal.
    -   **Red Row**: Active **SHORT** signal.
    -   **Grey Row**: No active signal / Neutral.

---

## How to Configure (Settings)

Open the indicator settings (Gear icon) to customize:

### 1. Scanner
-   **Paste Symbols**: Enter a comma-separated list of symbols to scan (e.g., `NSE:RELIANCE, NASDAQ:AAPL`).
    -   *Note*: Maximum 40 symbols.
-   **Display Table**: Toggle the scanner table on/off.
-   **Long/Short Signals**: Choose which signals to display in the scanner.

### 2. Supertrend
-   **ATR Length**: The lookback period for ATR (default: 10).
-   **Factor**: The multiplier for the Supertrend (default: 3.0).

### 3. Volatility Range
-   **Range Type**:
    -   **Auto ATR**: Automatically calculates the range based on market volatility (Recommended).
    -   **Type Points**: Uses a fixed point value (e.g., 10 points) for the range.
-   **ATR Multiplier**: Adjusts the width of the volatility range. Higher values = stricter filtering (fewer signals).

### 4. Additional Filters
These filters help refine your entries. You can toggle them On/Off.
-   **% Change Filter**: Requires the daily % change to be above/below a threshold.
-   **Volume % Change**: Requires volume to be higher than the previous day by a certain %.
-   **ATR Filter**: Filters out candles that are too volatile (too long).
-   **Body % Filter**: Requires the candle body to be a certain % of the total range (filters out Dojis).
-   **Volume Filter**: Requires current volume to be above the Volume SMA.
-   **Relative Volume (RVol)**: Checks if volume is significantly higher than average.
-   **Time Filter**: Restricts signals to a specific time window (e.g., 09:15 to 10:15).

---

## Strategy Logic Summary

**Long Setup:**
1.  **Trend**: Supertrend is Green (Up).
2.  **Breakout**: Price closes **ABOVE** the calculated Volatility Range (Top Price).
3.  **Confirmation**: Candle passes all enabled filters (Volume, Body Size, etc.).

**Short Setup:**
1.  **Trend**: Supertrend is Red (Down).
2.  **Breakdown**: Price closes **BELOW** the calculated Volatility Range (Bottom Price).
3.  **Confirmation**: Candle passes all enabled filters.

**Exit:**
-   The indicator does not plot explicit exit signals, but a common method is to exit when the Supertrend changes color or price re-enters the sideways range.
