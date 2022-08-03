# **Sorting Pandas DataFrame**

```python
df = pd.DataFrame({
    'col1': ['A', 'A', 'B', np.nan, 'D', 'C'],
    'col2': [2, 1, 9, 8, 7, 4],
    'col3': [0, 1, 9, 4, 2, 3],
    'col4': ['a', 'B', 'c', 'D', 'e', 'F']
})
df
""" Output
  col1  col2  col3 col4
0    A     2     0    a
1    A     1     1    B
2    B     9     9    c
3  NaN     8     4    D
4    D     7     2    e
5    C     4     3    F
"""

# sort by col1
df.sort_values(by=['col1'])
""" Ouput for sorting by `col1`
  col1  col2  col3 col4
0    A     2     0    a
1    A     1     1    B
2    B     9     9    c
5    C     4     3    F
4    D     7     2    e
3  NaN     8     4    D
"""
# Sort by multiple columns

df.sort_values(by=['col1', 'col2'])
""" Ouput for sorting by multiple columns
  col1  col2  col3 col4
1    A     1     1    B
0    A     2     0    a
2    B     9     9    c
5    C     4     3    F
4    D     7     2    e
3  NaN     8     4    D
"""
#Sort Descending

df.sort_values(by='col1', ascending=False)
"""
  col1  col2  col3 col4
4    D     7     2    e
5    C     4     3    F
2    B     9     9    c
0    A     2     0    a
1    A     1     1    B
3  NaN     8     4    D
"""
#Putting NAs first

df.sort_values(by='col1', ascending=False, na_position='first')
"""
  col1  col2  col3 col4
3  NaN     8     4    D
4    D     7     2    e
5    C     4     3    F
2    B     9     9    c
0    A     2     0    a
1    A     1     1    B
"""
#Sorting with a key function

df.sort_values(by='col4', key=lambda col: col.str.lower())
"""
   col1  col2  col3 col4
0    A     2     0    a
1    A     1     1    B
2    B     9     9    c
3  NaN     8     4    D
4    D     7     2    e
5    C     4     3    F
"""
# Natural sort with the key argument, using the natsort <https://github.com/SethMMorton/natsort> package.

df = pd.DataFrame({
   "time": ['0hr', '128hr', '72hr', '48hr', '96hr'],
   "value": [10, 20, 30, 40, 50]
})
df
"""    
time  value
0    0hr     10
1  128hr     20
2   72hr     30
3   48hr     40
4   96hr     50
"""
from natsort import index_natsorted
df.sort_values(
   by="time",
   key=lambda x: np.argsort(index_natsorted(df["time"]))
)
"""    
time  value
0    0hr     10
3   48hr     40
2   72hr     30
4   96hr     50
1  128hr     20
"""
```
## References:
- [Sorting pandas](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html)