# **Moving Average**

## **Hull Moving Average (HMA) & Weighted Moving Average (WMA)**
***Method 1***
```python
import numpy as np
def WMA(s, period):
       return s.rolling(period).apply(lambda x: ((np.arange(period)+1)*x).sum()/(np.arange(period)+1).sum(), raw=True)

def HMA(s, period):
       return WMA(WMA(s, period//2).multiply(2).sub(WMA(s, period)), int(np.sqrt(period)))
```

***Method 2***
```python
def weighted_moving_average(series: List[float], lookback: Optional[int] = None) -> float:
    if not lookback:
        lookback = len(series)
    if len(series) == 0:
        return 0
    assert 0 < lookback <= len(series)

    wma = 0
    lookback_offset = len(series) - lookback
    for index in range(lookback + lookback_offset - 1, lookback_offset - 1, -1):
        weight = index - lookback_offset + 1
        wma += series[index] * weight
    return wma / ((lookback ** 2 + lookback) / 2)


def hull_moving_average(series: List[float], lookback: int) -> float:
    assert lookback > 0
    hma_series = []
    for k in range(int(lookback ** 0.5), -1, -1):
        s = series[:-k or None]
        wma_half = weighted_moving_average(s, min(lookback // 2, len(s)))
        wma_full = weighted_moving_average(s, min(lookback, len(s)))
        hma_series.append(wma_half * 2 - wma_full)
    return weighted_moving_average(hma_series)
```
## **Reference:**
- [Hull Moving Average](https://stackoverflow.com/questions/64500904/how-to-calculate-hull-moving-average-in-python)