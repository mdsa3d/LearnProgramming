# Collect ranges values (convert range to list)

***Method 1***
```python
my_list = list(range(1, 1001))
```
***Method 2***
```python
r = range(10)
l = [*r]
print(l)
# output -> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
## Reference:
- [Turn range to list](https://stackoverflow.com/questions/11480042/python-3-turn-range-to-a-list)