# **For loops in Pinescript**

## ***What are foor loops***

They allow you to perform repetitive tasks without needing to repeat line after line of code. I simple terms, they repeat the same lines of code over and over again. 
- saves time
- makes your code easier to read
- reduces your chance of making an error or bug. 

## ***Syntax***

```
var_declarationX = for counter = from_num to to_num [by step_num]
    var_decl0
    var_decl1
    …
    continue
    …
    break
    …
    var_declN
    return_expression
```

`var_declarationX =` **--->** It just a simple variable which stores the returned value from the loop after the loop is completed. In pine script, a loop can return a value at the end just like a [function](https://backtest-rookies.com/2017/10/17/tradingview-creating-functions/) and that value is stored in ***var_declarationX***.

`for counter = from_num to to_num` **--->**
 `for`, `=` and `to` are the key parameters. For example, `for i = 0 to 10`, which means *loop from number 0 to number 10*. And `counter` is just another variable name that **holds the loop number we are on**. 

`from_num` and `to_num` can be variables that we can declare before the loop or actual numbers like `for i = 0 to 10`. So if you have a variable called x that has a value 10,  you can write the same loop as `for i = 0 to x`

Simple Example:
```
//@version=3
study("For Loop tutorial - Example 1")
y = 0
for i = 0 to 10
    y := y + i    
plot(y)
```

`by step_num` **--->** It helps to pass or control iteration when values are in a range. For example, if you only want to get the close value every 2 bars, you can use a step number of two.
```
//@version=3
study("For Loop tutorial - Example 3")

y = 0
z = for i = 0 to 10 by 2
    z = 10
    y := y + i
    z
    
plot(y)
plot(z, color=green)
```
## ***Special keywords***
***continue***

The continuekeyword can be used to skip parts of the for loop code if certain conditions are met. When the condition is met all code following the continuekeyword is `NOT executed`. 
```
//@version=3
study("For Loop tutorial - Example 4")

y = 0
z = for i = 0 to 10 by 2
    z = 10
    if z == 10
        continue
    y := y + i
    z
    
plot(y)
plot(z, color=green)
```
```
//@version=3
study("For Loop tutorial - Example 5")

total_volume = volume - volume

for i = 0 to 10
    if close[i] >= open[i]
        continue
    total_volume := total_volume + volume[i]
    
plot(total_volume, style=columns, color=red)
```

***break***

It stops the loop when a condition is met. So instead of skipping lines of the loop, using breakskips the rest of the loops.
```
//@version=3
study("For Loop tutorial - Example 6")

y = 0
for i = 0 to 10
    if close[i] <= open[i]
        break    
    y := y + 1
    
plot(y, style=line, color=green, linewidth=3)
```

## **Reference:**

- [How to create for loop in Pinescript](https://backtest-rookies.com/2018/01/19/tradingview-create-loop/)