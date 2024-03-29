# **The Average True Range (ATR) indicator**

This indicator interprets price volatility.
Developed by J. Welles Wilder and shared in his 1978 book New Concepts In Technical Trading Systems (StockCharts, n.d.).

## ***Formula***
Average True Range value (Mitchell, 2018; StockCharts, n.d.)
```
ATR = ((Prior ATR * 13) + true range) / 14
```
The ATR depends on previous values, it starts calculating on the 15th bar on the chart. After that there’s still a small effect of previous ATR values, but that effect becomes less the more price data the indicator processes.

## ***ATR Code***
```pinescript
//@version=3
// Step 1. Script settings
study(title="Average True Range", shorttitle="ATR", overlay=false)

// ATR input options
atrType = input(title="ATR Type", type=string, defval="Regular",
     options=["Regular", "Percentage", "Ticks", "Currency"])

atrLen    = input(title="ATR Length", type=integer, defval=14)
atrSmooth = input(title="Smoothing Type", type=string, defval="RMA",
     options=["EMA", "RMA", "SMA", "WMA"])

posSize = input(title="Position Size (For Currency ATR)", type=integer, defval=1)

// To disable the ATR's moving average, set its length to 1
maLength = input(title="MA Length", type=integer, defval=21, minval=1)
colourMA = input(title="Colour MA Line?", type=bool, defval=true)

highlight = input(title="Highlight ATR Signals?", type=bool, defval=false)

// Step 2. Calculate indicator values
// Custom function that calculates the Average True Range
// based on the smoothing type set by the input option
AvgTrueRange() =>
    if (atrSmooth == "EMA")
        ema(tr, atrLen)
    else
        if (atrSmooth == "RMA")
            rma(tr, atrLen)
        else
            if (atrSmooth == "SMA")
                sma(tr, atrLen)
            else
                wma(tr, atrLen)

// Calculate the Average True Range value
// based on the 'ATR Type' input option
atrValue = if (atrType == "Regular")
    AvgTrueRange()
else
    if (atrType == "Percentage")
        (AvgTrueRange() / close) * 100
    else
        if (atrType == "Ticks")
            AvgTrueRange() / syminfo.mintick
        else
            // Calculate ATR currency with two decimals
            round(AvgTrueRange() * syminfo.pointvalue * posSize * 100) / 100

// Calculate ATR moving average, provided input length is > 1
atrMA  = (maLength > 1) ? ema(atrValue, maLength) : na

// Step 3. Determine indicator signals
risingMA  = (atrMA > atrMA[1]) and (atrMA[1] > atrMA[2])
fallingMA = (atrMA < atrMA[1]) and (atrMA[1] < atrMA[2])

atrCrossover  = crossover(atrValue, atrMA)
atrCrossunder = crossunder(atrValue, atrMA)

highAtr = atrValue > highest(atrValue, 20)[1]
lowAtr  = atrValue < lowest(atrValue, 20)[1]

// Step 4. Output indicator data
plot(series=atrValue, color=orange, title="ATR")

// Show ATR moving average
maColour = not colourMA ? teal :
     risingMA ? green :
     fallingMA ? red :
     teal

plot(series=atrMA, color=maColour, title="ATR EMA")

// Highlight ATR signals
bgColour = (atrCrossover or atrCrossunder) ? orange :
     highAtr ? red :
     lowAtr ? green :
     na

bgcolor(color=highlight ? bgColour : na)

// Step 5. Create indicator alerts
// Alerts based on the ATR's EMA
alertcondition(condition=risingMA,
     title="Rising ATR",
     message="The Average True Range's average increased 2 bars in a row")

alertcondition(condition=fallingMA,
     title="Declining ATR",
     message="The Average True Range's average decreased 2 bars in a row")

// Alerts for when the ATR crosses its average
alertcondition(condition=atrCrossover,
     title="ATR Crossover",
     message="The Average True Range crossed above its EMA")

alertcondition(condition=atrCrossunder,
     title="ATR Crossunder",
     message="The Average True Range crossed under its EMA")

// Alerts for when the ATR reaches a recent high or low
alertcondition(condition=highAtr,
     title="ATR New High",
     message="The Average True Range crossed its 20-bar high")

alertcondition(condition=lowAtr,
     title="ATR New Low",
     message="The Average True Range crossed its 20-bar low")
```

## **References**
- [ATR](https://kodify.net/tradingview/indicators/average-true-range/)