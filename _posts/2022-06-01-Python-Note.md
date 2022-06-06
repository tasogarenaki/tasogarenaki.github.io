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

- List
  - `lst[::-1]` creates a reversed list

```python
>>> directors = ['jenkins', 'spielberg', 'bigelow', 'kubrick']
>>> directors[::-1]
['kubrick', 'bigelow', 'spielberg', 'jenkins']
```

- List Comprehensions
  - `[<map exp> for <name> in <iter exp> if <filter exp>]` 

```python
>>> [x * x - 3 for x in [1, 2, 3, 4, 5] if x % 2 == 1]
[-2, 6, 22]
```
First check the `if` statement with `x` from the List `[1, 2, 3, 4, 5]`, then apply with `x * x -3`.

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


## 3.2 Examples 



- Some Example from **lab02**:

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


- Some Examples from **project cats**:
  - full cases see [here](url) 

```python
# ----------------------------------------- Q1 ---------------------------------- #
def choose(paragraphs, select, k):
    """Return the Kth paragraph from PARAGRAPHS for which SELECT called on the
    paragraph returns true. If there are fewer than K such paragraphs, return
    the empty string.
    """
    # BEGIN PROBLEM 1
    "*** YOUR CODE HERE ***"
    # Index must be corrected, it's like 'remove' all the False Index
    # In this case used 2 different Index Systems to locate the correct one
    
    # Check the List with full Indexs
    for i in range(len(paragraphs)):
        if select(paragraphs[i]):
            # Check the corrected Index with right order
            if k == 0:
                return paragraphs[i]
            k -= 1
    return ''






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





# ----------------------------------------- Q6 ---------------------------------- #
def shifty_shifts(start, goal, limit):
    """A diff function for autocorrect that determines how many letters
    in START need to be substituted to create GOAL, then adds the difference in
    their lengths.
    """
    # BEGIN PROBLEM 6
    diff = abs(len(start)-len(goal))

    # version 1: return the correct answer for tests, but didn't pass the ok.py
    # can't figured out why
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


    # version 2: use Higher-Order function pass the ok.py
    def counting(start, goal, limit, count):
        if count > limit:
            return limit + 1
        if len(start) == 0 or len(goal) == 0:
            return count + diff
        if start[0] != goal[0]:
            count += 1
        return counting(start[1:], goal[1:], limit, count)
    return counting(start, goal, limit, 0)




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
        # if diff char, there's three conditions 
        # 1) compare with same index
        # 2)/3):
        # compare with one word each time, maybe a[1] == b[0]
        # or a[0] == b[1], e.g. a, b = "ckiteus", "kittens"
        return min(counting(start[1:], goal[1:], limit, count+1), 
        counting(start[1:], goal, limit, count+1), counting(start, goal[1:], limit, count+1))
    
    return counting(start, goal, limit, 0)




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
    # "print"
    send({'id': user_id, 'progress': progress})
    return progress 





# ----------------------------------------- Q9 ---------------------------------- #
def time_per_word(times_per_player, words):
    """Given timing data, return a game data abstraction, which contains a list
    of words and the amount of time each player took to type each word.

    Arguments:
        times_per_player: A list of lists of timestamps including the time
                          the player started typing, followed by the time
                          the player finished typing each word.
        words: a list of words, in the order they are typed.
    """
    # BEGIN PROBLEM 9
    "*** YOUR CODE HERE ***"

    """
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




# ----------------------------------------- Q10 ---------------------------------- #
def fastest_words(game):
    """Return a list of lists of which words each player typed fastest.

    Arguments:
        game: a game data abstraction as returned by time_per_word.
    Returns:
        a list of lists containing which words each player typed fastest
    """
    player_indices = range(len(all_times(game)))  # contains an *index* for each player
    word_indices = range(len(all_words(game)))    # contains an *index* for each word
    # BEGIN PROBLEM 10
    "*** YOUR CODE HERE ***"

    """
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

    # see exmaple with time() by Q9
    # Initial a empty 2D-Array
    result = [[] for i in player_indices]
    # begin with compair for word 1 with different players 
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





