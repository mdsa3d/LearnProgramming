# **Find Peaks for a given distribution**

```python
from scipy.signal import find_peaks
from scipy.misc import electrocardiogram
import matplotlib.pyplot as plt
%matplotlib inline

#Generate an electrocardiogram using the below code.
value = electrocardiogram()[1000:5000]

#Now the peaks using the below code.
peak, _ = find_peaks(value, height=0)
plt.plot(value)
plt.plot(peak, value[peak], "*")
plt.plot(np.zeros_like(value), "--", color="green")
plt.show()
```

## References:
- [Find peaks SciPy](https://pythonguides.com/scipy-find-peaks/)