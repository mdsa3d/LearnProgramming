# **Properties of the DataFrame**

## **Content**
- Get Number of columns
- Get Number of rows
- Get Column Types
- Store types in a Dictionary

## **Get Number of columns**

### Method 1
```python
import pandas as pd
df = pd.DataFrame({"pear": [1,2,3], "apple": [2,3,4], "orange": [3,4,5]})

len(df.columns)
# Output -> 3
```

### Method 2
```python
import pandas as pd
df = pd.DataFrame({"pear": [1,2,3], "apple": [2,3,4], "orange": [3,4,5]})
df.shape[1]
# Output -> 3
```

### Method 3
```python
import pandas as pd
df = pd.DataFrame({"pear": [1,2,3], "apple": [2,3,4], "orange": [3,4,5]})

df.columns.size
# Output -> 3
```

## **Get Number of rows**
### Method 1
```python
import pandas as pd
df = pd.DataFrame({"pear": [1,2,3], "apple": [2,3,4], "orange": [3,4,5]})
len(df.index)
# Output -> 3
```

### Method 2
```python
import pandas as pd
df = pd.DataFrame({"pear": [1,2,3], "apple": [2,3,4], "orange": [3,4,5]})
df.index.size
# Output -> 3
```

-----
## **Types**

### Get column types
```python
import pandas as pd 
df = pd.DataFrame({'A': [1, 2], 
                   'B': [1., 2.], 
                   'C': ['a', 'b'], 
                   'D': [True, False]})
```
To get all the types as a series :
```python
df.dtypes
Out: 
A      int64
B    float64
C     object
D       bool
dtype: object
```
If you want to extract individual datatype:
```python
df.column.dtype
# for example
df.A.dtype
Out:
int64
```
### Store types in a dictionary
```python
df.dtypes.apply(lambda x: x.name).to_dict()
Out: {'A': 'int64', 'B': 'float64', 'C': 'object', 'D': 'bool'}
```