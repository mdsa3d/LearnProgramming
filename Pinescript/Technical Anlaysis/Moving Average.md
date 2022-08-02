# **Pine’s moving averages**
Pine Script has the following built-in functions for calculating moving averages [1] :
<table border=2>
<tr><th>Function</th><th>Type of moving average</th></tr>
<tr><td>ta.sma()</td><td>Simple Moving Average (<a href= https://www.tradingcode.net/tradingview/simple-moving-average/>SMA</a>)</td></tr>
<tr><td>ta.ema()</td><td>Exponential Moving Average (<a href=https://www.tradingcode.net/tradingview/exponential-moving-average/>EMA</a>)</td></tr>
<tr><td>ta.wma()</td><td>Weighted Moving Average (<a href=https://www.tradingcode.net/tradingview/weighted-moving-average/>WMA</a>)</td></tr>
<tr><td>ta.hma()</td><td>Hull Moving Average (<a href=https://www.tradingcode.net/tradingview/hull-moving-average/>HMA</a>)</td></tr>
<tr><td>ta.rma()</td><td>Relative Moving Average (<a href=https://www.tradingcode.net/tradingview/relative-moving-average/>RMA</a>)</td></tr>
<tr><td>ta.swma()</td><td>Symmetrically-Weighted Moving Average (<a href=https://www.tradingcode.net/tradingview/symmetrical-weighted-average/>SWMA</a>)</td></tr>
<tr><td>ta.alma()</td><td>Arnaud Legoux Moving Average (<a href=https://www.tradingcode.net/tradingview/arnaud-legoux-average/>ALMA</a>)</td></tr>
<tr><td>ta.vwma()</td><td>Volume-Weighted Moving Average (<a href=https://www.tradingcode.net/tradingview/volume-weighted-average/>VWMA</a>)</td></tr>
<tr><td>ta.vwap()</td><td>Volume-Weighted Average Price (<a href=https://www.tradingcode.net/tradingview/volume-weighted-price/>VWAP</a>)</td></tr>
</table>

## **SMA**

```
// Compute a 10-bar Simple Moving Average (SMA)
smaValue = ta.sma(close, 10)

plot(smaValue, color=color.navy)
```

## **EMA**
```
// Calculate the 10-bar  Exponential Moving Average (EMA)
emaValue = ta.ema(close, 10)

plot(emaValue, color=color.navy)
```

## **WMA**
```
// Get 20-bar Weighted Moving Average of close prices
wmaValue = ta.wma(close, 20)

plot(wmaValue, color=color.blue)
```

## **HMA**
```
// Get 20-bar Weighted Moving Average of close prices
hmaValue = ta.hma(close, 8)

plot(wmaValue, color=color.fuchsia)
```


## Reference:
- [Moving average overview](https://www.tradingcode.net/tradingview/moving-averages-overview/)