# **Convert a list to array**

***Method 1***

- create a duplicate of the original object

```python
import numpy as np

lst = [11, 21, 19, 18, 29]
arr = np.array(lst)

print(arr)
print(type(arr))
```

***Method 2***

- follow the changes in the original object
- modifications made in one array would be reflected in the other array

func syntax:
```python
def asarray(a, dtype=None, order=None):
    return array(a, dtype, copy=False, order=order)
```

example code:
```python
import numpy as np

lst = [11, 21, 19, 18, 29]
arr = np.asrray(lst)

print(arr)
print(type(arr))
```