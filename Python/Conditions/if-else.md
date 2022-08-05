# If-else conditions

### ***One Liner***
General ternary syntax for one liner if-else condition:
```python
value_when_true if condition else value_when_false
# or
value_true if <test> else value_false
```
Example 1
```python
if i > 3: print("We are done.")
```
Example 2
```python
field_plural = None
if field_plural is not None: print("insert into testtable(plural) '{0}'".format(field_plural)) 
```
Example 3
```python
count = 0 if count == N else N+1
```
***Another way to write these conditions can be:***
```python
[value_false, value_true][<test>]
```
e.g:
```python
count = [0,N+1][count==N]
# This evaluates both branches before choosing one. To only evaluate the chosen branch:
```
***We can also use lamda function:***
```python
[lambda: value_false, lambda: value_true][<test>]()
# for exampole:
count = [lambda:0, lambda:N+1][count==N]()
```

## **Reference:**
- [If-else statement in one line](https://stackoverflow.com/questions/2802726/putting-a-simple-if-then-else-statement-on-one-line)