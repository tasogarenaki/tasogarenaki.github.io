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
  - consider **recursion**
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
    """Return the Kth paragraph from PARAGRAPHS for which SELECT called on the
    paragraph returns true. If there are fewer than K such paragraphs, return
    the empty string.
    """
    # BEGIN PROBLEM 1
    "*** YOUR CODE HERE ***"    
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
    """Return a select function that returns whether a paragraph contains one
    of the words in TOPIC.

    >>> about_dogs = about(['dog', 'dogs', 'pup', 'puppy'])
    >>> choose(['Cute Dog!', 'That is a cat.', 'Nice pup!'], about_dogs, 0)
    'Cute Dog!'
    >>> choose(['Cute Dog!', 'That is a cat.', 'Nice pup.'], about_dogs, 1)
    'Nice pup.'
    
    >>> dogs = about(['dogs', 'hounds'])
    >>> dogs('A paragraph about cats.')
    False
    >>> dogs('"DOGS" stands for Department Of Geophysical Science.')
    True
    """
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
    """A diff function for autocorrect that determines how many letters
    in START need to be substituted to create GOAL, then adds the difference in
    their lengths.
    """
    # BEGIN PROBLEM 6
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
    """Send a report of your id and progress so far to the multiplayer server."""
    # BEGIN PROBLEM 8
    "*** YOUR CODE HERE ***"
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
    """Given timing data, return a game data abstraction, which contains a list
    of words and the amount of time each player took to type each word.
    
    >>> p = [[1, 4, 6, 7], [0, 4, 6, 9]]
    >>> words = ['This', 'is', 'fun']
    >>> game = time_per_word(p, words)
    >>> all_words(game)   ----> game[0]
    ['This', 'is', 'fun']
    >>> all_times(game)   ----> game[1]
    [[3,2,1],[4,2,3]]

    >>> p = [[0, 2, 3], [2, 4, 7]]
    >>> game = time_per_word(p, ['hello', 'world'])
    >>> word_at(game, 1)   ----> game[0][word_index]
    'world'
    >>> all_times(game)
    [[2,1],[2,3]]
    >>> time(game, 0, 1)   ----> game[1][player_num][word_index]
    1: 0 -> [2,1] -> 1 -> [1]
    """
    # BEGIN PROBLEM 9
    "*** YOUR CODE HERE ***"
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
    """Return a list of lists of which words each player typed fastest.
    >>> p0 = [2, 2, 3]
    >>> p1 = [6, 1, 2]
    >>> fastest_words(game(['What', 'great', 'luck'], [p0, p1]))
    # p0 has only 'What' faster than p1, so ['What']
    # p1 has both 'great' and 'luck' faster than p0, so ['great','luck']
    [['What'],['great','luck']]

    >>> p0 = [2, 2, 3]
    >>> p1 = [6, 1, 3]
    >>> fastest_words(game(['What', 'great', 'luck'], [p0, p1]))  
    # with a tie, choose the first player
    [['What','luck'],['great']]
    """
    player_indices = range(len(all_times(game)))  # contains an *index* for each player
    word_indices = range(len(all_words(game)))    # contains an *index* for each word
    # BEGIN PROBLEM 10
    "*** YOUR CODE HERE ***"
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
    """Returns True if t contains a node with the value 'berry' and 
    False otherwise.

    >>> scrat = tree('berry')
    >>> berry_finder(scrat)
    True
    >>> sproul = tree('roots', [tree('branch1', [tree('leaf'), tree('berry')]), tree('branch2')])
    >>> berry_finder(sproul)
    True
    """
    "*** YOUR CODE HERE ***"
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
    """Sprout new leaves containing the data in leaves at each leaf in
    the original tree t and return the resulting tree.

    >>> t1 = tree(1, [tree(2), tree(3)])
    >>> print_tree(t1)
    1
      2
      3
    >>> new1 = sprout_leaves(t1, [4, 5])
    >>> print_tree(new1)
    1
      2
        4
        5
      3
        4
        5
    """
    "*** YOUR CODE HERE ***"
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
    """
    >>> print_tree(add_trees(tree(2), tree(3, [tree(4), tree(5)])))
    5
      4
      5
    """
    "*** YOUR CODE HERE ***"
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
     """Returns a new tree where every leaf value equal to find_value has
     been replaced with replace_value.
 
     >>> yggdrasil = tree('odin',
     ...                  [tree('balder',
     ...                        [tree('thor'),
     ...                         tree('freya')])])
     >>> print_tree(replace_leaf(yggdrasil, 'thor', 'freya'))
     odin
       balder
         freya
         freya
     """
     "*** YOUR CODE HERE ***"
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
  - full codes see [here]()


```python
# -------------------------------------- Q1 -------------------------------------- #
def make_fib():
    """Returns a function that returns the next Fibonacci number
    every time it is called."""
    "*** YOUR CODE HERE ***"
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
    """
    >>> test_lst = [1, 5, 8, 5, 2, 3]
    >>> new_lst = insert_items(test_lst, 5, 7)
    >>> new_lst
    [1, 5, 7, 8, 5, 7, 2, 3]
    >>> large_lst = [1, 4, 8]
    >>> large_lst2 = insert_items(large_lst, 4, 4)
    >>> large_lst2
    [1, 4, 4, 8]
    """
    "*** YOUR CODE HERE ***"
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
    """Return the first value in iterator T that appears K times in a row.

    >>> s = iter([3, 2, 2, 2, 1, 2, 1, 4, 4, 5, 5, 5])
    >>> repeated(s, 3)
    2
    >>> repeated(s, 3)
    5
    """
    assert k > 1
    "*** YOUR CODE HERE ***"
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
    """
    >>> sorted(permutations([1, 2, 3])) 
    [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
    """
    "*** YOUR CODE HERE ***"
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
        "*** YOUR CODE HERE ***"
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



























