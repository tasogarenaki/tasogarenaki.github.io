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

  <img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/stack_linked_pop.png?raw=true" alt="stack_linked_pop" style="zoom:80%;" />

- push: save a link to the list $\rightarrow$ create a new node for the beginning $\rightarrow$ set the instance variables in the new node

  <img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/stack_linked_push.png?raw=true" alt="stack_linked_push" style="zoom:80%;" />

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

# 5. Sorting

**Selection Sort:** In iteration i, find index min of smallest remaining entry. Then swap a[i] and a[min]. Each time must scan the full remaining entries.

**Insertion Sort:** In iteration i, swap a[i] with each larger entry to its left.

**Shellsort:** Move entries more than one position at a time by h-sorting the array. An h-sorted array is h interleaved sorted subsequences.

**Knuth Shuffling:** In iteration i, pick integer r between 0 and I uniformly at **random**. Then swap a[i] and a[r].

 ## 5.1 Mergesort

 Basic plan:

- Divide array into two halves.
- Recursively sort each half.
- Merge two halves.

Goal: Given two sorted subarrays a[lo] to a[mid] and a[mid+1] to a[hi], replace with sorted subarray a[lo] to a[hi].

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/mergesort1.png?raw=true" alt="mergesort1" style="zoom:50%;" />

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/mergesort2.png?raw=true" alt="mergesort2" style="zoom:50%;" />

Mergesort uses at most N lg N compares and 6 N lg N array accesses to sort any array of size N. Mergesort uses extra space proportional to N.

**Bottom-up Mergesort:**

- Pass through array, merging subarrays of size 1. 
- Repeat for subarrays of size 2, 4, 8, 16, ....

## 5.2 Comparators

Comparator interface: sort using an alternate order.

To support comparators in our sort implementations:

- Use **Object** instead of Comparable.
- Pass Comparator to `sort()` and `less()` and use it in `less()`.



## 5.3 Quicksort

**Basic plan:**

- Shuffle the array.
- Partition so that, for some j
  - entry a[j] is in place
  - no larger entry to the left of j
  - no smaller entry to the right of j 
- Sort each piece recursively.

# 6. Priority Queues

## 6.1 Binary Heaps

Binary heap: Array representation of a heap-ordered complete binary tree.

- Insert: Add node at the end, then swim it up.
- Remove the max: Exchange root with node at end, then sink it down.

Heap-ordered binary tree:

- Keys in nodes.
- Paren’s key no smaller than children’s keys.

Array representation:

- Indices start at 1.
- Take nodes in level order. 
- No explicit links needed!

## 6.2 Heapsort

Basic plan for in-place sort:

- Create max-heap with all N keys.
- Repeatedly remove the maximum key.

## 6.3 Symbol tables

Key-value pair abstraction:

- Insert a value with specified key.
- Given a key, search for the corresponding value.

# 7. Binary Search Trees

A binary tree is either:

- Empty.
- Two disjoint binary trees (left and right).

Symmetric order: Each node has a key, and every node’s key is:

- Larger than all keys in its left subtree. 
- Smaller than all keys in its right subtree.

A Node is comprised of four fields:

- A Key and a Value.
- A reference to the left and right subtree.

To delete the minimum key:

- Go left until finding a node with a null left link. 
- Replace that node by its right link.
- Update subtree counts.

To delete a node with key k: search for node t containing key k.

- Case 0 [0 children]: Delete t by setting parent link to null.
- Case 1 [1 child]: Delete t by replacing parent link.
- Case 2 [2 children]:
  -  Find successor x of t.
  - Delete the minimum in t's right subtree. 
  - Put x in t's spot.

# 8. Balanced Search Trees

## 8.1 2-3 Search Trees

Allow 1 or 2 keys per node.

- 2-node: one key, two children. 
- 3-node: two keys, three children.

Symmetric order: Inorder traversal yields keys in ascending order.

Perfect balance: Every path from root to null link has same length.

**Search:**

- Compare search key against keys in node. 
- Find interval containing search key.
- Follow associated link (recursively).

**Insert** into a 2-node at bottom:

- Search for key.
- Replace 2-node with 3-node.

**Insert** into a 3-node at bottom:

- Add new key to 3-node to create temporary 4-node.
- Move middle key in 4-node into parent.
- Repeat up the tree, as necessary.
- If you reach the root and it's a 4-node, split it into three 2-nodes.

## 8.2 Red-Black BSTs

Left-leaning red-black BSTs:

1. Represent 2–3 tree as a BST.

2. Use "internal" left-leaning links as "glue" for 3–nodes.

Search is the same as for elementary BST (ignore color), but runs faster because of better balance. 

Insertion in a LLRB tree:

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/llrb.png?raw=true" alt="llrb" style="zoom:100%;" />

**Insert into a 3-node at the bottom:**

1. Do standard BST insert; color new link red.
2. Rotate to balance the 4-node (if needed).
3. Flip colors to pass red link up one level.
4. Rotate to make lean left (if needed).
5. Repeat up the tree (if needed).

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/llrb2.png?raw=true" alt="llrb2" style="zoom:100%;" />

## 8.3 B-Trees

Searching in a B-Tree:

- Start at root. 
- Find interval for search key and take corresponding link. 
- Search terminates in external node.

Insertion in a B-tree

- Search for new key.
- Insert at bottom. 
- Split nodes with M key-link pairs on the way up the tree.

## 8.4 Kd-Trees

2-d orthogonal range search, Extension of ordered symbol-table to 2d keys.

- Insert a 2d key.
- Delete a 2d key.
- Search for a 2d key.
- Range search: find all keys that lie in a 2d range. 
- Range count: number of keys that lie in a 2d range.

Grid implementation.

- Divide space into M-by-M grid of squares.
- Create list of points contained in each square.
- Use 2d array to directly index relevant square.
- Insert: add (x, y) to list for corresponding square.
- Range search: examine only squares that intersect 2d range query.

# 9. Hash Tables

## 9.1 Hash Functions

All Java classes inherit a method `hashCode()`, which returns a 32-bit int. If `x.equals(y)`, then (`x.hashCode() == y.hashCode()`).

"Standard" recipe for **user-defined** types:

- Combine each significant field using the 31x + y rule.
- If field is a primitive type, use wrapper type hashCode().
- If field is null, return 0.
- If field is a reference type, use hashCode(). 
- If field is an array, apply to each entry.

Uniform hashing assumption. Each key is equally likely to hash to an integer between 0 and M - 1.

## 9.2 Separate Chaining

- Easier to implement delete.
- Performance degrades gracefully.
- Clustering less sensitive to poorly-designed hash function.

Use an array of M < N linked lists. 

- Hash: map key to integer i between 0 and M - 1. 
- Insert: put at front of i th chain (if not already there). 
- Search: need to search only i th chain.

## 9.3 Linear Probing

- Less wasted space.
- Better cache performance.

Open addressing: When a new key collides, find next empty slot, and put it there. 

- Hash. Map key to integer i between 0 and M-1. Array size M must be greater than number of key-value pairs N.
- Insert. Put at table index i if free; if not try i+1, i+2, etc.
- Search. Search table index i; if occupied but no match, try i+1, i+2, etc.

# 10. Graphs

Two vertices are connected if there is a path between them.

Vertex: use integers between 0 and V-1.

## 10.1 DFS

Put unvisited vertices on a stack.

To visit a vertex v:

- Marke vertex v as visited.
- Recursively visit all unmarked vertices adjacent to v.

The goal is find all vertices connected to s.

Algorithm:

- Use recursion (ball of string).
- Mark each visited vertex (and keep track of edge taken to visit it). 
- Return (retrace steps) when no unvisited options.

Data structures:

- `boolean[] marked` to mark visited vertices.
- `int[] edgeTo` to keep tree of paths. (edgeTo[w] == v) means that edge v-w taken to visit w for first time

## 10.2 BFS

Put unvisited vertices on a queue.

Repeat until queue is empty:

- Remove vertex v from queue.
- Add to queue all unmarked vertices adjacent to v and mark them.

## 10.3 Connected components

The relation "is connected to" is an equivalence relation:

- Reflexive: v is connected to v.
- Symmetric: if v is connected to w, then w is connected to v.
- Transitive: if v connected to w and w connected to x, then v connected to x.


## 10.4 Digraph Search

Depth first search, to visit a vertex v:

- Mark vertex v as visited.
- Recursively visit all unmarked vertices pointing from v.

BFS (from source vertex s): Put s onto a FIFO queue, and mark s as visited. Repeat until the queue is empty:

- remove the least recently added vertex v

- for each unmarked vertex pointing from v: add to queue and mark as visited.

## 10.5 Topological Sort

Directed acyclic graph.

- Run depth-first search.
- Return vertices in reverse postorder.

















