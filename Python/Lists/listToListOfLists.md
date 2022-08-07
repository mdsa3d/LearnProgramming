# **Convert list into list of lists**

```python
Input : ['alice', 'bob', 'cara']
Expected Output : [['alice'], ['bob'], ['cara']]
```

***Method 1***
```python
def extractDigits(lst):
    res = []
    for el in lst:
        sub = el.split(', ')
        res.append(sub)
      
    return(res)
                  
# Driver code
lst = ['alice', 'bob', 'cara']
print(extractDigits(lst))
```

***Method 2***
<br>List comprehension</br>

```python
def extractDigits(lst):
    return [[el] for el in lst]
                  
# Driver code
lst = ['alice', 'bob', 'cara']
print(extractDigits(lst))
```

***Method 3***
<br>map()</br>

```python
def extractDigits(lst):
    return list(map(lambda el:[el], lst))
      
              
# Driver code
lst = ['alice', 'bob', 'cara']
print(extractDigits(lst))
```

## **Reference:**
 - [List to list of lists](https://www.geeksforgeeks.org/python-convert-list-into-list-of-lists/)