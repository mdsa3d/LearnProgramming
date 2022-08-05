# **Enter position when multiple conditions are true**

Example:
```pinescript
//@version=3
strategy("Easy BTC Trading", overlay=true,pyramiding = 0, default_qty_type = strategy.percent_of_equity, default_qty_value = 10)

Multiple = input(2, minval=0,step=0.01)
ATR1 = atr(21)*Multiple
volumeavg = (volume[2]+volume[3]+volume[4])/3
//I guess that you want to know the highest value for the last 5 bars
//if yes, in the highest & lowest functions, you need to use close[1]
//which is the previous close before the actual one
//if you just use close, your actual close can be the highest one
//so your long order would never trigger as your close would never
//be higher than the highest
highest = highest(close[1],5)
lowest = lowest(close[1],5)

long1 = close > highest
long2 = volume[1] >= (volumeavg*2)


//go_long = high > highest and volume[1] > volumeavg*2
//there was a problem with that condition above, so I wrote it a clearer way,
// with an if and it works better
go_long = 0
if (close > highest and volume[1] > volumeavg)
    go_long := 1
exit_long = close < lowest

strategy.entry("Long",strategy.long, when = go_long)
strategy.exit("Exit long","Long", profit = 5, stop = strategy.position_avg_price - ATR1, when = exit_long)
```

## Reference:
- [Multiple condition as entry point](https://stackoverflow.com/questions/51121138/pine-script-enter-position-when-multiple-conditions-are-true)