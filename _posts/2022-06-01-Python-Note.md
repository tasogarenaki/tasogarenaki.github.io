---
title: Python Note
author:
  name: Terry
  link: https://github.com/tasogarenaki
date: 2022-06-01 11:11:11 +0100
categories: [Note, CS]
tags: [note, python]
math: true
mermaid: true
---




# 1 Fundations

- **install pip**:  

```console
  $ curl https://bootstrap.pypa.io/pip/get-pip.py -o get-pip.py
  $ sudo python3 get-pip.py
```

<br>

- **Some Commands**: 
  - control + d: `exit()`
  - control + l: `clear` 
  - `python3 -i name.py`
  - `handle = open(filename, mode)`
  - `quit(): break`
  - `dict_name.get(xxx, 0) + 1`: if in `dict()` has `xxx` then `xxx+1` otherwise `0+1`
  - `range(start, stop, step)`
  - `for j in range(i+1, xxx):` the step is `i+1`

<br>

- **Position of numbers without** `[]`:

```python
>>> n = 18117
>>> all_but_last, last = n // 10, n % 10
all_but_last = 1811   # via //
last = 7              # via %
```

<br>

- **Placeholder**: 
  - `%d`: decimal
  - `%f`: float
  - `%%`: percent
  - e.g.: `print('%d + %d = %d' % (a, b, a + b)) `


# 2 Coursera: PY4E

## 2.1 Fundations

- **Regular Expressions and Extracting Data**:
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

<br>

- **Socket**
  - `import socket`
  - `Port 80`: Web Server, HTTP(80) 
  - `decode()`

<br>

- **Retrieving Web Pages**
  - use Chrome to view the page source 
  - `import urllib.request, urllib.parse, urllib.error`

```python
fhand = urllib.request.urlopen('http://xxxxx')
for line in fhand:
	print(line.decode().strip())
```

<br>

- **Beautifulsoup4**: **e11.py**
  
  - `from bs4 import BeautifulSoup`
  - Example to get img: https://divertingpan.github.io/post/python_tieba/
  
  1) download `BeautifulSoup4`
  
  2) unzip and Terminal geht to the folder
  
  3) `sudo python3 ./setup.py i nstall`
  
  4) `pip install soupsieve`

<br>

- **eXtensible Markup Language (XML)**
  - share structured data 
  - `import xml.etree.ElementTree as ET`
  - `xxx.findall(‘a/b’)`: find all tags `b` from `a`

<br>

- **JavaScript Object Notation (JSON)**
  - `import json`
  - `'''[ xxx ]'''`
  - `info = json.loads(xxx)`

<br>

- **Service Oriented Approach**
  - Application Programming Interfaces (API)
  - `import twurl`
  - `twurl.augment(url, {‘xx’})`
  - GeoJason API: http://maps.googleapis.com/maps/api/geocode/json?

<br>

- **assert expression**: 
  - test if expression is `False`: `assert 1 == 0, 'xxx'`. This is `False`, so show `'xxx'`
  - `assert 1 == 1, ‘xxx’`. This is `True`, show nothing. 





## 2.2 Examples 

- Example **e1**:
  - if error, still accept, then run `yyy` and `continue`.

```python
try: 
	xxx      
except ValueError: 
	yyy 
	continue
```

<br>

- Example **e2**:
  - find position, print out xxx between position 1 and 2.

```python
text = abcdef 
n1 = text.find('c')
n2 = text.find('f')
n3 = text[n1:n2+1]
print(n3)
```

<br>

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

<br>

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

<br>

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

<br>

- **Databases**: **e17.py** and **e18.py**
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



# 3 CS61A Fall 2020

See [here](https://inst.eecs.berkeley.edu/~cs61a/fa20/) for this course.

## 3.1 Fundations

- **`*args` and `**kwargs`**: 
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

<br>

- **Higher-Order Functions:**
  - use function inside of function 
  
```python
def apply_twice(f, x):
    return f(f(x))  	# here call the f function with x, f can be i.e. square 

def square(x):
    return x * x

>>> apply_twice(square, 2)      # f is now the function square(x) with x = 2
16
```

<br>

- **Lambda Expressions:**
  - `lambda <parameters>: <return expression>`
  - `(lambda <parameters A>: <return function>)(lambda <parameters A>: lambda <parameters B>:  <return expression>)`
  - `lambda` is a function with formal parameter `x=10` that returns the value of `x*x`, it’s like `def`

```python
x = 10
square = x * x
square = lambda x: x * x	
print(square(4))
```

<br>

- **List**
  
  - Time increases with more elements
  
  - Memory small
  
  - `append()` to add an element in list
  
  - `insert()` to add an element in a position of list, e.g.: 
  
    ​		`>>> lst = [1, 2, 3]` 
  
    ​		`>>> lst.insert(1,5)`
  
    ​		`[1,5,2,3]` in position [1] add 5
  
  - `extend(['a', 'b'])` to add elements in list  
  - `pop()` to remove the final element or `pop(x)` to remove element at index `x`
  - `remove('xx')` remove the first element named `xx`
  - `sort()` to sort elements in list
  - `split()` to remove element (here (none)) from the list
  - `lst[::-1]` creates a reversed list

```python
>>> directors = ['jenkins', 'spielberg', 'bigelow', 'kubrick']
>>> directors[::-1]
['kubrick', 'bigelow', 'spielberg', 'jenkins']
```

<br>

- **List Comprehensions**
  - `[<expression> for <element> in <sequence> if <conditional>]` 

```python
>>> [x * x - 3 for x in [1, 2, 3, 4, 5] if x % 2 == 1]
[-2, 6, 22]

>>> [i ** 2 for i in [1, 2, 3, 4] if i % 2 == 0]
[4, 16]
```
First check the `if` statement with `x` from the List `[1, 2, 3, 4, 5]`, then apply with `x * x -3`.   

<br>

- **Linked Lists**
  - recursive object only stores 1) its first value 2) a reference to the rest of the list, which is another linked list.
  - Linked lists are a list of items pointing to their neighbors. Notice that there's no explicit index for each item. 
  - In Python, if want to add an item at the head of the list, must create a new list and move all the items in the new list. With a linked list, the neighbor of the new item is the old beginning of the list.
  - To get an Index from the built-in list: lst[x] with x is the index. But with the linked list must start at the first item, then repeatedly follow the `rest` attribute, e.g. `link.rest.rest.first`.

```python
class Link:
    empty = ()

    def __init__(self, first, rest=empty):
        assert rest is Link.empty or isinstance(rest, Link)
        self.first = first
        self.rest = rest

    def __repr__(self):
        if self.rest is not Link.empty:
            rest_repr = ', ' + repr(self.rest)
        else:
            rest_repr = ''
        return 'Link(' + repr(self.first) + rest_repr + ')'

    def __str__(self):
        string = '<'
        while self.rest is not Link.empty:
            string += str(self.first) + ' '
            self = self.rest
        return string + str(self.first) + '>'
```

<br>

- `enumerate()`

```python
# normal for-statement
>>> i = 0
>>> seq = ['one', 'two', 'three']
>>> for element in seq:
...     print i, seq[i]
...     i += 1
... 
0 one
1 two
2 three

# wih enumerate()
>>> seq = ['one', 'two', 'three']
>>> for i, element in enumerate(seq):
...     print i, element
... 
0 one
1 two
2 three
```

<br>

- **Trees**
  
  <img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/python_note/trees.png?raw=true" alt="trees" style="zoom:50%;" />
  
  - `from sklearn import tree`
  - consider **recursion**, a tree is a recursive abstract data type that has a `lable` and `branches`
  - remove a label use `remove()`
  - **root**: the node at the top of the tree, e.g. **7**
  - **label**: the value in a node, selected by the `label()` function, **up layer**, e.g. **all of the integers** are values of this picture
  - **branch**: a subtree of the root, selected by the `branches()` function, **under layer**, e.g. **1**
  - **leaf**: a node that has no branches, the **lowst layer**,  e.g. **-4, 0, 6, 17, 20**
  - **depth**: how far a node is from the root. e.g. the node **19** has depth 1 and the node **3** has depth 2
  - **height**: the depth of the lowest leaf, e.g. the nodes **-4, 0, 6 and 17** are lowest leaves, which means they have depth 4 and the entire tree has height **4**
  - some examples:

```python
# The Tree-ADTs
# Initial a tree
def tree(label, branches=[]):
    for branch in branches:
      assert is_tree(branch), 'branches must be trees'
    return [label] + list(branches)

# Define the label
def label(tree):
    return tree[0]

# Define the branches 
def branches(tree):
    return tree[1:]

# Check is tree or not 
def is_tree(tree):
    if type(tree) != list or len(tree) < 1:
      return False
    for branch in branches(tree):
      if not is_tree(branch):
        return False
    return True

# Check is tree or not 
def is_leaf(tree):
    return not branches(tree) 

# Print the tree
def print_tree(t, indent=0):
    print('  ' * indent + str(label(t)))
    for b in branches(t):
      print_tree(b, indent + 1)
  
  
# -------------------------- Some Solutions -------------------------- #
# Calculate the Height of Tree
def height(t):
    if is_leaf(t):
          return 0
      return max([height(branch) for branch in branches(t)]) + 1

# find the max value of the tree
def tree_max(t):
    if is_leaf(t):
        return label(t)
    else:
        return max([label(t)] + [tree_max(branch) for branch in branches(t)])

# find the path that has max sum
def max_path_sum(t):
    if is_leaf(t):
        return label(t)
    else:
        return max([max_path_sum(branch) for branch in branches(t)]) + label(t)

# square all value of the tree
def square_tree(t):
    return tree(label(t)**2, [square_tree(branch) for branch in branches(t)])

# find the path that has value x, and x can be list
def find_path(tree, x):
    if label(tree) == x:
        return [label(tree)] 
    for b in branches(tree):
        path = find_path(b, x) 
        if path:
            return [label(tree)] + path
```

<br>

- `zip(first_iter, second_iter)`
  - Iterate over co-indexed `(x,y)` pairs. Return a `list` with `tuple` from lists
  - by differen length, return the short one
  - `zip((iterable, ....))`

```python
>>> a = ['a', 'b', 'c', 'd']
>>> b = ['1', '2', '3', '4']
>>> list(zip(a,b))
[('a', '1'), ('b', '2'), ('c', '3'), ('d', '4')]
```

<br>

- **Dictionaries**
  - Quick even with Key increase 
  - More memory
  - Space trade time
  - **HashTable**


```python
>>> table = {}
>>> test1 = 'abc'
>>> test2 = '123'
# put 'test2' into table with label 'test1'
>>> table[test1] = [test2]
>>> table
{'abc': ['123']}

>>> dict([(3, 9), (4, 16), (5, 25)])
{3: 9, 4: 16, 5: 25}
```



```python
# Example from LeetCode #1 Two Sum
def two_sum(nums, target):
    dic = {}                                # initial a dic
    for i, num in enumerate(nums):              
        targ_num = target - num             # calc difference between targ and current value
        if targ_num in dic:                 # if the difference already in dic
            return [dic[targ_num], i]       # direct return the index of both nums 
        dic[num] = i                        # otherwise save the num in dic for next search
```

<br>

- **Non-Local and Global Assignment**
  - `nonlocal <var_name>`: defines outer function, which means only use it if there's a inside function. Otherwise should use `global <var_name>` 
  - place in top of inner function

```python
def outer_func():
    a = 1               # Initial a = 1
    
    # 1) Normal 
    def inner_func1():
        a = 2           # Update a = 2, irrelevant with `a = 1` above 
        print(a)        # -> 2
    inner_func()          
    print(a)            # -> 1, print a under `outer_func()` out
    
    # 2) UnboundLocalError
    def inner_func2():
        print(a)        # -> Error! Call `a` which didn't initialize yet 
        a = 2           # Initial
    inner_func()      
    print(a)
    
    # 3) with `nonlocal`
    def inner_func3():
        nonlocal a      # def a is a variabl from outside function `outer_func()`
        print(a)        # -> 1, here is `a` from outside
        a = 2           # Update a = 2  
    inner_func()      
    print(a)            # -> 2
```

<br>

```python
a = 1               # Initial a = 1
def func():
    global a        # def that a is global, which means inside this function is `a = 1`
    print(a)        # -> 1, here is `a` from outside
    a = 2           # Update a = 2  
inner_func()      
print(a)            # -> 2
```

<br>

- **Iterators**
  - `iter(iterable)`: Return an iterator over the elements of an iterable value
  - `next(iterator)`: Return the next element in an iterator 
  - print out an element in the list and remove it from the list at same time

<br>

- **Built-in functions for Iteration**
  - `map(func, iterable)`: Iterate over `func(x)` for `x` in `iterable`
  - `filter(func, iterable)`: Iterate over `x` iterable if `func(x)`
  - `reversed(sequence)`: Iterate over all the elements in a sequence in reverse order 
  - `list(iterable)`: Create a list containing all the elements in the input iterable 
  - `tuple(iterable)`: Creates a tuple containing all the elements in the input iterable
  - `sorted(iterable)`: Creates a sorted list containing all the elements in the input iterable

<br>

- **Generators and Generator Functions**
  - `yield var_name`: iterable '`return`'
  - A generator function is a function that `yield`s values insted of `return`ing them. And can `yield` multiple times. **Pro**: save the CPU.
  - `yield from`: will yield all values from an iterator or iterable, e.g. a list.

```python
>>> def foo():
...     print("starting...")
...     while True:
...             res = yield 4
...             print("res:", res)

>>> g = foo()
>>> print(next(g))			
starting...
4
>>> print(next(g))
res: None
4
```

1. Line 8: invoke `print(next(g))`, the `foo()` function starts executing. First invoke line 2 `print("starting...")` then get into the `while`. Finally at line 4 meet `yield`, so `return 4`. The process stopped. The line 5 `print("res:", res)` will **not** executed. So showing line 9 and 10, but remember the state of the function for future `next`calls.

   

2. Line 11: invoke `print(next(g))` again. But this time starts after the `yield` that was **previously executed**, which is line 4 to give `res` the value, but the **right** side of `=` has no value, because the `4` already `return`ed. So showing line 12 with `res: None`.  Then run until the next `yield` statement.

   

3. The process will continue to execute in the `while`-loop and meet `yield` again. At this time, it will returns `4` and then the process stops.

<br>

- **Object Oriented Programming (OOP)**
  - **class**: a template for creating objects, e.g. `Car`
  - **instance**: a single object created from a class, e.g. `my_car = Car('red')` and `my_car` is an instance of the `Car` class
  - **attribute**: a property of an object, specific to an instance. A **variable** that belongs to the class, e.g. `self.wheels` and `self.color`. Invoke: `my_car.wheels` and `    my_car.color` 
  - **class attribute**: a property of an object, shared by all instances of a class 
    - Accessing Attributes: `getattr(<name>, 'var')` and `hasattr(<name>, 'var')` 
    - e.g. `num_whells`
  - **method**: an action (function) that all instances of a class may perform, e.g. `drive` and `pop_tire`. Invoke: `my_car.drive()`
  - **constructor**: how to build an instance of the class. `__init__` is called with the new object as its first argument (named `self`), along with any additional arguments. 

```python
class Car(object):															 # class
    num_wheels = 4
	  
    def __init__(self, color):										# constructor 
        self.wheels = Car.num_wheels						   # attricute
        self.color = color

    def drive(self):															# method
        if self.wheels <= Car.num_wheels:
            return self.color + ' car cannot drive!'
        return self.color + ' car goes vroom!'

    def pop_tire(self):
        if self.wheels > 0:
            self.wheels -= 1
        
# ------------------------- Some Tests ------------------------- #
>>> my_car = Car('red')														# instance
>>> my_car.color																 # invoke the attribute 
'red'
>>> my_car.wheels
4
>>> my_car = Car('red')
>>> my_car.drive()																# invoke the method
'red car goes vroom!'
```

<br>

- **Inheritance**: to reduce the repeated code.
  - `class <name>(<base class>):`


```python
# ------------------------- Original ------------------------- #
class Dog():
    def __init__(self, name, owner):
        self.is_alive = True 
        self.name = name 
        self.owner = owner 
        
    def eat(self, thing):
        print(self.name + " ate a " + str(thing) + "!") 
        
    def talk(self):
        print(self.name + " says woof!")

class Cat():
    def __init__(self, name, owner, lives=9):
        self.is_alive = True 
        self.name = name 
        self.owner = owner 
        self.lives = lives 
    
    def eat(self, thing):
        print(self.name + " ate a " + str(thing) + "!") 
    
    def talk(self):
        print(self.name + " says meow!")
```

To avoid redefining attributes and methods for similar classes use **superclass** from which the similar classes **inherit**. For example, create a class `Pet` and redefine `Dog` as a subclass of `Pet`.

```python
# ------------------------- Inheritance ------------------------- #
class Pet():
    def __init__(self, name, owner):
        self.is_alive = True    
        self.name = name 
        self.owner = owner 
        
    def eat(self, thing):
        print(self.name + " ate a " + str(thing) + "!") 
        
    def talk(self):
        print(self.name)

class Dog(Pet):
    def talk(self):
        print(self.name + ' says woof!')
        
        
# ------------------------- Some Tests ------------------------- #       
>>> dog = Dog('doggy','my')
>>> dog.name									# invoke variable
'doggy'
>>> dog.owner
'my'
>>> dog.eat('meat')						 # invoke method
doggy ate a meat!
>>> dog.talk()
doggy says woof!
```

<br>

- **Order of Growth** (time): 
  - Exponential growth, incrementing n multiplies time by a constant: $O(b^n)$
  - Quadratic growth, incrementing n increases time by n times a constant: $O(n^2)$
  - Linear growth, incrementing n increases time by a constant: $O(n)$
  - Logarithmic growth, doubling n only increaments time by a constant: $O(\mathrm{log} \, n)$
  - Constant growth, increasing n doesn't affect time: $O(1)$

<br>

- **Str and Repr:**
  - Both are built-in functions. Be invoked by calling `repr(obj)` or `str(obj)` rather than `obj.__repr__()` or `obj.__str__()`.
  - `str()`: "Human-readable" form
  - `repr()`: "Computer-readable" form

<br>

- **Example for Iterable:**

```python
# Does every element equal some other element?
def all_have_an_equals(s):
  """
  >>> all_have_an_equals([4, 3, 2, 3, 2, 4])
  True
  """
  return all([s[i] in s[:i]+s[i+1:] for i in range(len(s))])
```

Example take `s[i]=s[1]=3`, we cann see `s[:i]=4` + `s[i+1:]=[2, 3, 2, 4]` = `[4, 2, 3, 2, 4]` without `[3]`. So simply use `for`-loop to checke if there has same element in the list as `s[i]`. 

```python
# V2
def all_have_an_equals(s):
  return min([s.count(x) for x in s]) > 1
```

The simply version, count if a element `x` comes at least twice.





























## 3.2 Examples 

- Some Examples from **lab02**:
  - full cases see [here](https://github.com/tasogarenaki/CS-Lectures/tree/master/Python/CS61A/Labor/lab02) 

```python
def cycle(f1, f2, f3):
    def func1(n):                                 # first to give is n times
        def func2(x):                             # second to give is x
            run = n                               # run n times 
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
                    order = order % 3 + 1         # f1 -> f2 -> f3 -> f1
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

<br>
<br>

- Some Examples from **project cats**:
  - full cases see [here](https://github.com/tasogarenaki/CS-Lectures/blob/master/Python/CS61A/Projects/cats/cats.py) 

```python
# ----------------------------------------- Q1 ---------------------------------- #
def choose(paragraphs, select, k):
    # Check the List with full Indexs
    for i in range(len(paragraphs)):
        if select(paragraphs[i]):
            # Check the corrected Index with right order
            if k == 0:
                return paragraphs[i]
            k -= 1
    return ''
```
1) Index must be corrected, it's like 'remove' all the `False` Index
   
2) In this case used two different Index Systems to locate the correct one

<br>

```python
# ----------------------------------------- Q2 ---------------------------------- #
def about(topic):
    assert all([lower(x) == x for x in topic]), 'topics should be lowercase.'
    # BEGIN PROBLEM 2
    "*** YOUR CODE HERE ***"
    # Use Higher-Order Function
    def check(x):
        # remove punctuations, lowercase of sentence then split via utils.py
        x = split(lower(remove_punctuation(x)))
        # use double for-statement to find the same key word
        for i in topic:
            # same as topic[i] == x[k]:
            if i in x:
                return True
        return False
    return check
```

<br>

```python
# ----------------------------------------- Q6 ---------------------------------- #
def shifty_shifts(start, goal, limit):
    diff = abs(len(start)-len(goal))

    # version 1: 
    count = 0
    # Question required
    if count > limit:
        return limit + 1
    # return diff_length + total 
    if len(start) == 0 or len(goal) == 0:
        return count + diff
    # count the different chars
    if start[0] != goal[0]:
        count += 1
    # recursion: use [1:] -> by running every time the length of string will -1
    # + count, cause will reset as 0 every time
    return shifty_shifts(start[1:], goal[1:], limit) + count

    # version 2: 
    def counting(start, goal, limit, count):
        if count > limit:
            return limit + 1
        if len(start) == 0 or len(goal) == 0:
            return count + diff
        if start[0] != goal[0]:
            count += 1
        return counting(start[1:], goal[1:], limit, count)
    return counting(start, goal, limit, 0)
```

There's two version to solve this question

1) `return` the correct answer for tests, but didn't pass the ok.py, can't figured out why
   
2) use Higher-Order function pass the ok.py

<br>

```python
# ----------------------------------------- Q7 ---------------------------------- #
def pawssible_patches(start, goal, limit):
    """A diff function that computes the edit distance from START to GOAL."""
    # similar as shifty_shifts
    def counting(start, goal, limit, count):
        diff = abs(len(start)-len(goal))
        if count > limit:
            return limit + 1
        # if one is empty, should change n times of lengh another word which is diff
        if len(start) == 0 or len(goal) == 0:
            return count + diff
        # if same char, skip with next char
        if start[0] == goal[0]:
            return counting(start[1:], goal[1:], limit, count)
        # minimize the amount
        return min(counting(start[1:], goal[1:], limit, count+1), 
        counting(start[1:], goal, limit, count+1), counting(start, goal[1:], limit, count+1))
    
    return counting(start, goal, limit, 0)
```

If there's different `char`, there's three conditions: 

1) compare with same index
   
2) /3) compare with one word each time, maybe `a[1] == b[0]` or `a[0] == b[1]`, e.g. `a, b = "ckiteus", "kittens"`
        

<br>       

```python
# ----------------------------------------- Q8 ---------------------------------- #
def report_progress(typed, prompt, user_id, send):
    i = 0
    for k in typed:
        # located the first incorrect word
        if k != prompt[i]:
            break
        i += 1
    # calculate the error ratio
    progress = i / len(prompt)
    # send --> "print"
    send({'id': user_id, 'progress': progress})
    return progress 
```

<br>

```python
# ----------------------------------------- Q9 ---------------------------------- #
def time_per_word(times_per_player, words):
    # Initial 2D-Array
    # times[i][j] with player i (num) and index of word j (num)
    times = [[0 for i in range(len(j)-1)] for j in times_per_player]
    i = 0
    for layer1 in times_per_player:
        # first value represents the initial starting time
        j = 0
        for layer0 in layer1:
            if j != 0:
                # e.g. times[0][0] = times_per_player[0][1] - times_per_player[0][0]
                #                  = 4 - 1 = 3
                times[i][j-1] = layer0 - layer1[j-1]
            j += 1
        i += 1
    # change the order as rrequested
    return game(words, times)
```

<br>

```python
# ----------------------------------------- Q10 ---------------------------------- #
def fastest_words(game):
    player_indices = range(len(all_times(game)))  # contains an *index* for each player
    word_indices = range(len(all_words(game)))    # contains an *index* for each word

    # see exmaple with time() by Q9
    # Initial a empty Array
    result = [[] for i in player_indices]
    # begin with compair for word 0 with different players 
    for word in word_indices:
        for player in player_indices:
            # default set the player 0 is always the winner
            # in the case of a tie, the player 0 wins 
            if player == 0:
                winer = 0
                # set the player's time as minimum
                min_time = time(game, player, word)
            # save the current time
            cur_time = time(game, player, word)
            # reset the minimum time 
            if cur_time < min_time:
                min_time = cur_time
                winer = player
        # add the word in the array
        result[winer] += [word_at(game, word)]
    return result 
```

<br>
<br>

- Some Examples from **lab05**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/tree/master/Python/CS61A/Labor/lab05)

```python
# ------------------------------------- Q5 ------------------------------------- #
def berry_finder(t):
    if label(t) == 'berry':
        return True
    # if branch is empty, return False, cause the label already checked 
    if is_leaf(t):
        return False
    # get into every branches
    for i in branches(t):
        # use recursion to locate all labels every leaves
        if berry_finder(i):
            return True
    return False
```

<br>

```python
# ------------------------------------- Q6 ------------------------------------- #
def sprout_leaves(t, leaves):
    # use recursion --> into lowest leaves that branch is empty (leaf)
    # if branch is empty, add the leaves
    if is_leaf(t):
        # the 'label()' here is now the 'lowest' leaves, simply use (label(), [xx]) to print it out 
        return tree(label(t), [tree(i) for i in leaves])
    # similar as Q5
    return tree(label(t), [sprout_leaves(i, leaves) for i in branches(t)])
```

<br>

**A tricky one**

```python
# ------------------------------------- Q10 ------------------------------------- #
def add_trees(t1, t2):
    # use ADT and recursion
    length1, length2 = len(branches(t1)), len(branches(t2))

    # 1) if both trees have same number of branches:
    if length1 == length2:
        # use zip() to iterate over multiple sequences at once  
        return tree(label(t1) + label(t2), [add_trees(b1, b2) for b1, b2 in zip(branches(t1), branches(t2))])

    # 2) if both trees have different number of branches:
    elif length1 < length2:
        # add n (different length of both trees) branches with value 0 to short tree
        new_branches = branches(t1) + [tree(0) for _ in range(length2 - length1)]
        # reset the new tree
        new_tree = tree(label(t1), new_branches)
        return add_trees(new_tree, t2)
    else:
        # if tree2 is smaller than tree1, just exchange the input place 
        # and below condition 'elif' works too
        return add_trees(t2, t1)
```
The idea of the solution for this question can split into two parts:

1. if both trees have **same** number of branches: add the roots `label()` of both trees directly, then for `branches()` via recursion, and because of that the next iteration: `branches()` ---> new `label()`

   

2. if both trees have **different** number of branches: this is the tricky part! Because of the different number of `branches()` (the length), part one will only add the lowest leaves. The simplest way may add the different of `brauches()` with value `0` for the **short** tree, so now they both have same `branches()`.

<br>
<br>

- Some Examples from **hw03**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/blob/master/Python/CS61A/HW/hw03/hw03.py)


 ```python
 # ------------------------------------- Q4 ------------------------------------- #
 def replace_leaf(t, find_value, replace_value):
     # use recursion into leaf
     if is_leaf(t):
         if label(t) == find_value:
             # replace the leaf value if matched 
             return tree(replace_value)
         # return the leaf value if didn't matched 
         return t
     temp_branch = []
     # let branches into recursion to located the leaf 
     for b in branches(t):
         # storage the value every recursion
         temp_branch += [replace_leaf(b, find_value, replace_value)]
     return tree(label(t), temp_branch)
 ```

For case like this, its usefull to via **recursion** to get into the `leaf` by `is_leaf()` then `label` it. The recursion is relate to `branches`.

<br>
<br>

- Some Examples from **lab06**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/blob/master/Python/CS61A/Labor/lab06/lab06.py)


```python
# -------------------------------------- Q1 -------------------------------------- #
def make_fib():
    pre, pro = -1, 1
    def count_fib():
        nonlocal pre, pro
        fib = pre + pro
        pre = pro
        pro = fib
        return fib
    return count_fib
  
  
# -------------------------------------- Q4 -------------------------------------- #
def insert_items(lst, entry, elem):
    new_lst = lst
    flag = 0
    for i, num in enumerate(lst):
        # additional conditions flag to avoid stuck in the loop
        if num == entry and flag == 0:
            # insert the value in position i + 1
            new_lst.insert(i+1, elem)
            # update flag with continue to get out of loop
            flag = 1
            continue
        flag = 0
    return new_lst
```

Q4: for case with quivalent value from `entry` and `elem` could caused the infinitely long list, e.g. `[1, 4, 8]` with `entry, elem = 4, 4`. That is because insert `4` after `4`, then for next loop checked the second `4` again, and so on. Thats why should add two additional conditions `flag` and `continue` to avoid this issue. Only one of them will not work. With `flag = 1` avoid get into the `if` condition and with `continue` to skip the current iteration.

<br>
<br>

- Some Examples from **hw04**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/tree/master/Python/CS61A/HW/hw04)


```python
# ------------------------------ Q3 ------------------------------ #
def repeated(t, k):
    assert k > 1

    # iter(): for-loop works like next()
    count = 1
    pro = 0
    for i in t:
        pre = i             # mark the current value
        if pre == pro:      # if the pre and pro value are the same
            count += 1
            if count == k:  # appears k times in a row 
                return i
        else:
            count = 1       # reset, if interrupted 
        pro = pre   
        
        
# ------------------------------ Q4 ------------------------------ #
def permutations(seq):
    # use recursion to get into the single value
    # use yield to invoke the function to get all the order 
    if len(seq) == 1:
        yield seq           
    else:
        # let the rest into next iteration, begin with the last one due to recursion 
        for i in permutations(seq[1:]):   
            for k in range(len(i)+1):
                lst = list(i[:])        # initial a list with current value(s)
                # add the pre-position value, [0] from last iteration due to [1:] 
                lst.insert(k, seq[0])    
                yield lst
```

<br>
<br>

- Some Examples from **lab07**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/tree/master/Python/CS61A/Labor/lab07)


```python
# This is a method from the class ProfessorCard
def effect(self, other_card, player, opponent):
        orig_opponent_deck_length = len(opponent.deck.cards)

        # adds the power of the opponent's card to all of mine 
        for my_card in player.deck.cards:
            my_card.attack += other_card.attack
            my_card.defense += other_card.defense

        # if a card in deck have same power as the opponent's card remove it
        for card in opponent.deck.cards[:]:             # copy the deck
            if card.attack == other_card.attack \
                or card.defense == other_card.defense:  # Check if same power
                opponent.deck.cards.remove(card)        # remove the card 

        discarded = orig_opponent_deck_length - len(opponent.deck.cards)
        if discarded:
            print('{} cards were discarded from {}\'s deck!'.format(discarded, opponent.name))
            return
          
# Copy a list 
>>> lst = [1, 2, 3, 4]
>>> copy = lst[:]
>>> copy
[1, 2, 3, 4]
>>> copy is lst
False
```

Copy a list to avoid trouble when mutate a list as iterating through it. In line 11 directly used the copy `opponent.deck.cards[:]` with for-loop.

<br>
<br>

Some Examples from **hw05**:

- full codes see [here](https://github.com/tasogarenaki/CS-Lectures/blob/master/Python/CS61A/HW/hw05/hw05.py)
- A tree is a binary search tree (BST) if:
  - Each `node` has at most two `children (branches)`, which means a `leaf` is automatically a valid BST
  - The `children` are valid binary search trees, which means both side of the tree must be BST
  - For every node, `node`'s **left** `child` are **less** than or **equal** to the `label` of the `node`
  - For every node, `node`'s **right** `child` are **greater** than the `label` of the `node`
  - If theres only **one** `child`, so it can consider as **left** or **right**, which means theres no rules, it's automatically a BST 

```python
def is_bst(t):
    # search for the minimum of the right child (branches)
    def bst_min(t):
        if t.is_leaf():
            return t.label
        return min(t.label, bst_min(t.branches[0]))

    # search for the maximum of the left child (branches)
    def bst_max(t):
        if t.is_leaf():
            return t.label
        return max(t.label, bst_max(t.branches[0]))

    if t.is_leaf():             # a leaf is automatically a bst
        return True

    if len(t.branches) == 1:    # if only one child
        return True             
    
    if len(t.branches) == 2:		# max 2 children
      	# 1) the label greater than or equal to all nodes on the left branches and
        # smaller than all nodes on the right branches 
        # 2) both children are BST
        if (bst_max(t.branches[0]) <= t.label < bst_min(t.branches[1]) and 
        is_bst(t.branches[0]) and is_bst(t.branches[1])):
                return True

    return False
```

Used two helper functions `bst_max()` and  `bst_min()` to find the max and the min of the left and right branches. So if the `label` is bigger than the max of the left and smaller than / equal to the min of the right branches, it's a BST. The helper function used the recursion to locate the min / max value, if didn't find it until the leaf, so the leaf is the min / max value. To be clear: `branches[0]` is the left side and `branches[1]` is the right side.

<br>
<br>

- Some Examples from **lab08**:
  - full codes see [here](https://github.com/tasogarenaki/CS-Lectures/blob/master/Python/CS61A/Labor/lab08/lab08.py)


```python
# -------------------------------------- Q3 -------------------------------------- # 
"""remove the odd-indiced (0-based) elements from a linked list, if only one elment, return it directly"""
def every_other(s):
    # while s != s.empty and s.rest != empty 
    # -> if only one element, will not get into the loop
    while s and s.rest:             
        s.rest = s.rest.rest        # remove the odd index (0-based)
        s = s.rest                  # let the rest elements into the loop
```

Linked list has no `len()` or index, so just "replace" the odd one with others. Set the loop condition with `and` so if a linked list has only one elment will not get into the loop.

<br>

```python
# -------------------------------------- Q4 -------------------------------------- # 
"""Mutates t so that each node's label becomes the product of all labels in the corresponding subtree rooted at t."""
def cumulative_mul(t):
    if t.is_leaf():             # if get the leaf, return nothing
        return
    for b in t.branches:        
        cumulative_mul(b)       # let the branches into the recursion
        t.label *= b.label      # product of layer by layer 
```

Use the recursion and definition of branches, multiply layer by layer. Line 8 make sure every time only calculate the "new" label from the "new" Tree with is the `branches`, it's like stairs.

<br>

```python
# -------------------------------------- Q5 -------------------------------------- # 
"""The idea is to check whether a link contains a cycle."""
# version 1
def has_cycle(link):
    # similar as Q2 (except Line 9!)
    lst = []                # create a list to save the passed link
    while link:
        if link in lst:     # if list contains the link, return True         
            return True
        lst.append(link)    # save the linked list in the list, thinking about two pointer!
        link = link.rest    # let the rest of the linked list in the loop
    return False 


# Version 2 with constant space 
def has_cycle_constant(link):
    # two pointers 
    if not link:                                    # if is empty, return False
        return False

    slow, fast = link, link.rest                    # define two ponters 

    while fast:                                     # while not empty
        # if fast is empty, which means no more elements to compair
        if not fast.rest:                           
            return False
        # if both pointers contain each other
        # which means, fast one catch up the slow one by one more cycle
        elif fast is slow or fast.rest is slow:     # compair two steps, faster     
            return True
        else:                                       # let rest elements into loop                                           
            slow, fast = slow.rest, fast.rest.rest  # let fast one two steps faster, otherwise too slow
    return False
```

**Version 1:** The idea of the solution is to create a **list** to save all linked list went through the loop. By next loop will only save the rest of the linked list. Eventuell has this **list** a whole variante of the linked list. Similar like two pointer. If the linked list is a cycle, it will find the same part of the elements in the **list**.

- e.g. by first run: original `link = [1 2 3 / 1 2 3 / 1 2 3 ....]`, `lst = [1 2 3 / 1 2 3 / 1 2 3/ ...]` $\neq$ `link = [2 3 / 1 2 3 / 1 2 3 ....]`. By 2. run: `lst = [1 2 3 /... 2 3 / 1 2 3 ...]` $\neq$ `link = [3 / 1 2 3 / 1 2 3 ....]`. By 3. run: `lst = [1 2 3 /... 2 3 / 1 2 3 .../ 3 / 1 2 3 ....]` $=$ `link = [1 2 3 / 1 2 3 ....]`. As the 3. run shows, the `lst` contains the `link`.

**Version 2:** The idea is to create two pointers, one fast and one slow, eventuell compair them, if is the same then is cycled. Important is Line 29: two conditions to compair two steps, it's faster. And Line 32, if the linked list is a cycle, so it's getting there how ever it takes. So with `fast.rest.rest` can make it faster, analog can with `fast.rest.rest.rest`.

<br>

```python
# -------------------------------------- Q6 -------------------------------------- # 
"""Reverse labels every odd level of the tree."""
def reverse_other(t):
    def subfunc(t, level):
        if t.is_leaf():                         # if get the leaf, return nothing
            return

        if level:                               # if it's odd level -> need reversed  
            temp = []                           # create a temp list to store the labels
            for b in t.branches:                # add all labels in the temp list,
                temp.append(b.label)
            temp.reverse()                      # then reverse it

            for i in range(len(t.branches)):    # save the reversed label for each level
              	t.branches[i].label = temp[i]   # in opposite position 

        for b in t.branches:                    # recursion for the next level
            subfunc(b, not level)               

    subfunc(t, False)                           # begin with the first level 0 -> even 
```

Just create a blank `temp` list to save all `label`s of odd level and reverse it, then replace it into the true `tree`. To locate the odd level, just simply use `flag` with `True` or `False` to marke it and starting by the even level with `False`.

<br>
<br>

- Some Examples from **lab09**:

  - full codes see [here]()

  - A **full binary tree (FBT)** is a tree with each node has either 0 or 2 branches (never 1 branch). 

```python
# -------------------------------------- Q3 -------------------------------------- #
def num_trees(n):
    if n == 1:
        return 1
    # 1) Catalan number with recursive formula: C_{n+1} = \sum C_i * C_{n-i}
    res = 0
    for i in range(1, n):
        res += num_trees(i) * num_trees(n - i)
    return res

    # 2) simplify the 1)
    return num_trees(n-1) * (4*n-6)//n
```

One can consider that the FBT can be used with the Catalan number formula is if the left tree has `1` node, then the right tree must has `n-1` nodes, which means there is `f(1)*f(n-1)` possibilies. Analog, if the left tree has `2` nodes, then the right tree must has `n-2` nodes, so there is `f(2)*f(n-2)` possibilities. And so on we can use the formula `f(i)*f(n-i)`, which is the Catalan number recursive formula.

<br>

```python
# -------------------------------------- Q10 ------------------------------------- #
# insert a value in an index of a linked list
def insert(link, value, index):
    if not index:                                   # to changed index is 0
        link.rest = Link(link.first, link.rest)     # let the rest of linked list as new linked list
        link.first = value                          # add the value in the index 0
    elif link.rest is link.empty:                   # out of the range
        print('IndexError')
    else:
         insert(link.rest, value, index-1)          # recursion with rest of linked list
```

Note that a linked list has no length or index. 

<br>

**Deep Linked List**

```python
# -------------------------------------- Q11 ------------------------------------- #
# Returns the deep length of a possibly deep linked list
def deep_len(lnk):
    if lnk is Link.empty:
        return 0
    elif not isinstance(lnk, Link):            # the deepest (which is not a linked list)
        return 1
    else:
        return deep_len(lnk.first) + deep_len(lnk.rest)     # split the list into the recursion
```

The idea is to split the list into the two lists and recurse on them (line 9). And if the list reaches the deppest, then `lnk.first` is not a linked list but a `int`, so can use `isinstance(object, classinfo)` to check if a object belongs to the classinfo, e.g. `a = 5` then `isinstance(a, int)` is `True`. So at line 6, if reaches the deppest, then will return `False`, so the length is `1`. 

<br>

```python
# -------------------------------------- Q13 ------------------------------------- #
# Prune the tree, keeping only the n branches of each node with the smallest label.
def prune_small(t, n):
    while len(t.branches) > n:                                  # prune tree until n branches
        largest = max(t.branches, key = lambda t: t.label)      # compair the branches due to their label
        t.branches.remove(largest)                              # remove the large branches
    for b in t.branches:
        prune_small(b, n)                                       # next leaf
```

Use `remove()` to remove the branches / labels. Line 5: The `Branches` of the trees are compaired with the largest being indicated by the `label`.









