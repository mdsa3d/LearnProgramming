# Plot arrows on the chart
```
//@version=4
study('Ex 1', overlay=true)
data = close >= open
plotshape(data, color=color.lime, style=shape.arrowup, text="Buy")
plotshape(not data, color=color.red, style=shape.arrowdown, text="Sell")
```
You may use plotchar function with any unicode character:
```
//@version=4
study('buy/sell arrows', overlay=true)
data = close >= open
plotchar(data, char='↓', color=color.lime, text="Buy")
plotchar(data, char='↑', location=location.belowbar, color=color.red, text="Sell")
```

## Reference
- [How tos](https://www.tradingview.com/pine-script-docs/en/v4/appendix/HOWTOs.html)