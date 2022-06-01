---
title: Python Note
author:
  name: Terry
  link: https://github.com/tasogarenaki
date: 2022-06-01 11:11:00 +0100
categories: [Note, CS]
tags: [note]
math: true
mermaid: true
---




# 1 Fundations

- install pip:  

```console
  $ curl https://bootstrap.pypa.io/pip/get-pip.py -o get-pip.py
  $ sudo python3 get-pip.py
```

- Some Commands: 
  - control + d: `exit()`
  - control + l: `clear` 
  - `python3 -i name.py`
  - `handle = open(filename, mode)`
  - `quit(): break`
  - `append()` to add elements in list
  - `sort()` to sort elements in list
  - `split()` to remove element (here (none)) from the list
  - `dict_name.get(xxx, 0) + 1`: if in `dict()` has `xxx` then `xxx+1` otherwise `0+1`

- Position of numbers without `[]`:

```python
>>> n = 18117
>>> all_but_last, last = n // 10, n % 10
all_but_last = 1811   # via //
last = 7              # via %
```
- Placeholder: 
  - `%d`: decimal
  - `%f`: float
  - `%%`: percent
  - e.g.: `print('%d + %d = %d' % (a, b, a + b)) `


# 2 Coursera: PY4E

## 2.1 Fundations

- Regular Expressions and Extracting Data:
  - `import re`
  - `re.search()`
  - `re.findall()`
  - see **e9.py**

|  **Symbol**  | Explanation                                         |
|:------------:|-----------------------------------------------------|
|     **^**    | Matches the beginning of a line                     |
|     **$**    | Matches the end of the line                         |
|     **.**    | Matches any character                               |
|    **\s**    | Matches whitespace                                  |
|    **\S**    | Matches any non-whitespace character                |
|     *****    | Repeats a character zero or more times              |
|    ***?**    | Repeats a character zero or more times (non-greedy) |
|     **+**    | Repeats a character one or more times               |
|    **+?**    | Repeats a character one or more times (non-greedy)  |
|  **[aeiou]** | Matches a single character in the listed set        |
|  **[^XYZ]**  | Matches a single character not in the listed set    |
| **[a-z0-9]** | The set of characters can include a range           |
|    **( )**   | Only show date inside of ()                         |


- Socket
  - `import socket`
  - `Port 80`: Web Server, HTTP(80) 
  - `decode()`


- Retrieving Web Pages
  - use Chrome to view the page source 
  - `import urllib.request, urllib.parse, urllib.error`

```python
fhand = urllib.request.urlopen('http://xxxxx')
for line in fhand:
	print(line.decode().strip())
```

- Beautifulsoup4: **e11.py**
  - `from bs4 import BeautifulSoup`
  - Example to get img: https://divertingpan.github.io/post/python_tieba/
  
  1) download `BeautifulSoup4`
   
  2) unzip and Terminal geht to the folder
   
  3) `sudo python3 ./setup.py i nstall`
   
  4) `pip install soupsieve`


- eXtensible Markup Language (XML)
  - share structured data 
  - `import xml.etree.ElementTree as ET`
  - `xxx.findall(‘a/b’)`: find all tags `b` from `a`


- JavaScript Object Notation (JSON)
  - `import json`
  - `'''[ xxx ]'''`
  - `info = json.loads(xxx)`


- Service Oriented Approach
  - Application Programming Interfaces (API)
  - `import twurl`
  - `twurl.augment(url, {‘xx’})`
  - GeoJason API: http://maps.googleapis.com/maps/api/geocode/json?

- Class and Object
  - `class xxx:` 
  - object: `test = xxx():`
  - function: `def xxx:`
  - subclass: `class name2(class_name1):`



- assert expression: 
  - test if expression is `False`: `assert 1 == 0, 'xxx'`. This is `False`, so show `'xxx'`
  - `assert 1 == 1, ‘xxx’`. This is `True`, show nothing. 





## 2.2 Examples 

- Example **e1**:
  - if error, still accept, then run yyy and continue.

```python
try: 
	xxx      
except ValueError: 
	yyy 
	continue
```

- Example **e2**:
  - find position, print out xxx between position 1 and 2.

```python
text = abcdef 
n1 = text.find('c')
n2 = text.find('f')
n3 = text[n1:n2+1]
print(n3)
```

- Example **e3**:
  - use os function to use `os.getcwd()` to now the path and use `os.chdir()` to change the path
  - `rstrip()`: move the blank line

```python
import os
print(os.getcwd())
os.chdir('/Users/Terry/Desktop')

# Use words.txt as the file name
fname = input("Enter file name: ")
fh = open(fname)

for line in fh:
    line = line.rstrip()
    line = line.upper()
    print(line)
```


- Example **e5**:
  - `lst.split()` error, so should use `lst[0].split()` to remove blank.
  - `list(set(xx))` to remove repeated elements

```python
fname = input("Enter file name: ")
fh = open(fname)
lst = list()
new = list()
count = 0 
for line in fh:
    line = line.rstrip()
    lst.append(line)
    new = new + lst[count].split() 
    count = count + 1 


new = list(set(new))
new.sort()
print(new)
```



- Example **e14**:

```python
# compute the sum of the numbers in the file and enter the sum
# the numbers are inside tag 'count'

address = input('Enter location: ')

url = address 
print('Retrieving', url)
uh = urllib.request.urlopen(url, context=ctx)


data = uh.read()
print('Retrieved', len(data), 'characters')


tree = ET.fromstring(data)
sum = 0
# locatate 'count' and find them all
counts = tree.findall('.//count')
print('Count:', len(counts))

for count in counts:
    # the numbers are 'text' from count
    sum += int(count.text)

print(sum)
```





- Databases: **e17.py** and **e18.py**
  - SQLite Browser
  - `import sqlite3`
  - Reconstructing Data with JOIN: select … from … join … on …
  - inside python code, should use SQL code: 

```sql
xyz.execute('UPDATE xxx SET yyy=xxx WHERE xxxx')
```

```python
xxx = sqlite.connect('xxx.sqlite')
yyy = xxx.cursor()
yyy.execute('SQL code')
```



# 3 CS61A


## 3.1 Fundations

- `*args` and `**kwargs`: 
  - `*args`: unknown functions/parameters 
  - `**kwargs`: same but list 

```python
def printed(f):
     	def print_and_return(*args):
         	result = f(*args)
         	print('Result:', result)
         	return result
     	return print_and_return

>>> printed_pow = printed(pow)
>>> printed_pow(2, 8)
Result: 256
256

>>> printed_abs = printed(abs)
>>> printed_abs(-10)
Result: 10
10
```




- Higher-Order Functions:
  - use function inside of function 
  
```python
def apply_twice(f, x):
    return f(f(x))  	# here call the f function with x, f can be i.e. square 

def square(x):
    return x * x

>>> apply_twice(square, 2)      # f is now the function square(x) with x = 2
16
```


- Lambda Expressions:
  - `lambda <parameters>: <return expression>`
  - `(lambda <parameters A>: <return function>)(lambda <parameters A>: lambda <parameters B>:  <return expression>)`
  - `lambda` is a function with formal parameter `x=10` that returns the value of `x*x`, it’s like `def`

```python
x = 10
square = x * x
square = lambda x: x * x	
print(square(4))
```










## 3.2 Examples 



- Example **lab02**:

```python
def cycle(f1, f2, f3):
    def func1(n):                               # first to give is n times
        def func2(x):                           # second to give is x
            run = n                                # run n times 
            order = 1                             # f1, f2, f3
            result = x
            if run:
                while run:
                    if order == 1:
                        result = f1(result)
                    elif order == 2:
                        result = f2(result)
                    elif order == 3:
                        result = f3(result)
                    order = order % 3 + 1       # f1 -> f2 -> f3 -> f1
                    run -= 1
            return result
        return func2
    return func1
```
To run this function i.e. `my_cycle = cycle(add1, times2, add3)(2)(1)`: 

1) inside function `cycle` has input `f1`, `f2`, `f3` 
   
2) then has inside function `func1(n)` and `func2(x)` which in this case `n = 2` and `x = 1`, cause `func1` first defined.


**Alternative i.e.**

```python
>>> my_cycle = cycle(add1, times2, add3)
>>> add_one_then_double = my_cycle(2)
>>> add_one_then_double(1)
4
```





