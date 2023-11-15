---
title: Princeton Algorithms
author:
  name: Terry
  link: https://github.com/tasogarenaki
date: 2023-11-01 10:00:00 +0200
categories: [Note, CS]
tags: [note, java, algorithms]
math: true
mermaid: true


---



# 1. Introduction

The textbook is seen [here](https://algs4.cs.princeton.edu/home/), and the code is seen [here](https://algs4.cs.princeton.edu/code/).

# 2. Union-Find

## 2.1 Quick Find

Data structure

- Integer array id[] of length N.

- Interpretation: p and q are connected iff they have the same id.

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/quickfind1.png?raw=true" alt="quickfind1" style="zoom:70%;" />

**Find:** Check if p and q have the same id.

**Union:** To merge components containing p and q, change all entries whose id equals id[p] to id[q].

## 2.2 Quick Union

Data structure

- Integer array id[] of length N. 
- Interpretation: id[i] is parent of i. 
- Root of i is id[id[id[...id[i]...]]].

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/quickunion1.png?raw=true" alt="quickunion1" style="zoom:40%;" />

**Find:** Check if p and q have the same root.

**Union:** To merge components containing p and q, set the id of p's root to the id of q's root.

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/quickunion2.png?raw=true" alt="quickunion2" style="zoom:40%;" />

## 2.3 Weighted Quick Union

Data structure: Same as quick-union, but maintain extra array sz[i] to count number of objects in the tree rooted at i.

- Modify quick-union to avoid tall trees.
- Keep track of size of each tree (number of objects). 
- Balance by linking root of smaller tree to root of larger tree.

Finde: Identical to quick union.

Union: Modify quick-union to:

- Link root of smaller tree to root of larger tree. 
- Update the sz[] array.

# 3. Analysis of Algorithms

## 3.1 Order-of-Growth Classifications 

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/orderofgrowth.png?raw=true" alt="orderofgrowth" style="zoom:30%;" />

# 4. Stacks and Queues

## 4.1 Stacks

Stack: 

- LIFO
- push: insert
- pop: remove and return most recently added

**Linked-List Implementation:** A stack with N items uses 40 N bytes.

- pop: save item to return $\rightarrow$ delete first node and point to next $\rightarrow$ return saved item

  <img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/stack_linked_pop.png?raw=true" alt="stack_linked_pop" style="zoom:30%;" />

- push: save a link to the list $\rightarrow$ create a new node for the beginning $\rightarrow$ set the instance variables in the new node

  <img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/stack_linked_push.png?raw=true" alt="stack_linked_push" style="zoom:30%;" />

**Array Implementation:**

- pop(): add new item at s[N].
- push(): remove item from s[N-1].

**Resizing-Array Implementation:** 

- If array is full, create a new array of twice the size, and copy items.
- To shrink array: push() $\rightarrow$ double size of s[] when array is full; pop() $\rightarrow$ halve size of s[] when array is 1/4 full.

## 4.2 Queues

Queue: with two pointers.

- FIFO
- enqueue: insert
- dequeue: remove and return least recently added

**Linked-List Implementation:** 

- pop: identical to Stack.
- push: save a link to the last node $\rightarrow$ create a new node for the end $\rightarrow$ link the new node to the end of the list.

**Resizing-Array Implementation:** 

- Use array q[] to store items in queue.
- enqueue(): add new item at q[tail].
- dequeue(): remove item from q[head].
- Update head and tail modulo the capacity.
- Add resizing array.

## 4.3 Iteration

Iterable has a method that returns an Iterator and `Iterator` has methods `hasNext()` and `next()`.

```java
/* "foreach" statement (shorthand) */
for (String s : stack) 
  StdOut.println(s);

/* equivalent code (longhand) */
Iterator<String> i = stack.iterator();
while (i.hasNext()) {
  String s= i.next();
  StdOut.println(s);
}
```



 































