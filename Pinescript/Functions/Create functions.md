# **Functions in Pinescript**

## ***Create Functions***

*Process of creating a function in pinescript*

- **Give it a name**: This can be anything you wish but it is recommended to use something which describes what the function does.
- **Declare the arguments**: This is done in the same way you submit arguments and keyword arguments when calling a function. We simply write names for the arguments between the brackets. Then in the following code, we decide how to handle the data that is given to that variable.
  - **Note**: At the time of writing declaring keyword arguments in a function is not supported in pine script. (as far as I can tell)
- **Add the pine script function syntax** =>at the end of the line: This lets the interpreter know you are declaring a function.
- **Indent the function’s code**: All code for the function must now be indented so that the interpreter knows it is part of the function and can tell where the function ends. To indent you can hit tab on the keyboard or press the space bar 4 times.
- **Return something**: This is the output of the function. I.e the result of the calculation (assuming you are making a calculation). In pine script, a variable or list of variables can be returned by writing them on the last line.


## ***Function Example***

A simple function that will return the followng built-in variables:Open highlowand closedepending on a string that is passed to it. 
```
get_src(str) =>
    x = str == 'Open' ?
      open:
     str == 'High' ? 
      high: 
     str == 'Low' ? 
      low: 
     str == 'Close' ? 
      close: 
     str == 'HL2' ? 
      hl2: 
     close
    x
```

### ***Combine functions***

```
//@version=3
study("Dual HULL Indicator", overlay=true)
 
h1=input(title="Fast MA Period",type=integer,defval=9)
h1_src= input(title='Fast MA Source', type=string, defval='Close', options=['Open', 'High','Low','Close','HL2'])
h2=input(title="Slow MA Period",type=integer,defval=18)
h2_src=input(title='Slow MA Source', type=string, defval='Close', options=['Open', 'High','Low','Close','HL2'])
 
get_src(str) =>
    x = str == 'Open' ?
      open:
     str == 'High' ? 
      high: 
     str == 'Low' ? 
      low: 
     str == 'Close' ? 
      close: 
     str == 'HL2' ? 
      hl2: 
     close
    x
 
hull_ind(_src, _length)=>
    //HMA = WMA(2*WMA(n/2) − WMA(n)),sqrt(n))
    _return = wma((2 * wma(_src, _length / 2)) - wma(_src, _length), round(sqrt(_length)))
 
x1= hull_ind(get_src(h1_src), h1)
y1 = hull_ind(get_src(h2_src), h2)
 
 
ma=plot(x1, title='Fast MA')
ma2=plot(y1, title='Slow MA')
```

## **Reference:**
- [Creating functions](https://backtest-rookies.com/2017/10/17/tradingview-creating-functions/)