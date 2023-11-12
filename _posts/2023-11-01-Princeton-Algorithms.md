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

<img src="https://github.com/tasogarenaki/tasogarenaki.github.io/blob/main/pics/algorithms/part_i/orderofgrowth.png?raw=true" alt="orderofgrowth" style="zoom:50%;" />







 







