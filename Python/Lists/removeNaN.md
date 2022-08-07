# **Remove NaN values**

***Math***
```python
import math

mylist = [1,2,float('nan'),8,6,4,float('nan')]
print(mylist)
newlist = [x for x in mylist if math.isnan(x) == False]
print(newlist)
```

***NumPy***
```python
import numpy as np

mylist = [1,2,float('nan'),8,6,4,float('nan')]
print(mylist)
newlist = [x for x in mylist if np.isnan(x) == False]
print(newlist)
```

***Loop***
```python
mylist = [1,2,'nan',8,6,4,'nan']
mylist = [str(x) for x in mylist]
print(mylist)
newlist = [x for x in mylist if x != 'nan']
print(newlist)
```

***Pandas***
```python
import pandas as pd

mylist = ['John',23,'nan','New York',float('nan')]
print(mylist)
newlist = [x for x in mylist if pd.isnull(x) == False and x != 'nan']
print(newlist)
```

## **Reference:**
- [Remove nan from list in python](https://www.delftstack.com/howto/python/remove-nan-from-list-python/#remove-nan-from-the-list-in-python-using-the-numpy-isnan-method)