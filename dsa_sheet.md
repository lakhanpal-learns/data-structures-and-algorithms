# DSA Cheat Sheet (Technical Interview Revision)

> A one-stop revision sheet for coding interviews.
> Revise this before every OA, technical interview, or contest.

---

# Time Complexity

| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Array Access |
| O(log n) | Logarithmic | Binary Search |
| O(√n) | Square Root | Prime Checking |
| O(n) | Linear | Linear Search |
| O(n log n) | Linearithmic | Merge Sort |
| O(n²) | Quadratic | Bubble Sort |
| O(2ⁿ) | Exponential | Backtracking |
| O(n!) | Factorial | Permutations |

---

# STL Complexities

## Vector

| Operation | Complexity |
|------------|------------|
| Access | O(1) |
| push_back | O(1) amortized |
| pop_back | O(1) |
| insert(begin) | O(n) |
| erase | O(n) |
| size | O(1) |
| clear | O(n) |
| front | O(1) |
| back | O(1) |

---

## String

| Operation | Complexity |
|------------|------------|
| Access | O(1) |
| substr | O(k) |
| append | O(k) |
| find | O(n) |
| erase | O(n) |

---

## Stack

| Operation | Complexity |
|------------|------------|
| push | O(1) |
| pop | O(1) |
| top | O(1) |

---

## Queue

| Operation | Complexity |
|------------|------------|
| push | O(1) |
| pop | O(1) |
| front | O(1) |
| back | O(1) |

---

## Priority Queue

| Operation | Complexity |
|------------|------------|
| push | O(log n) |
| pop | O(log n) |
| top | O(1) |

---

## Set / Map

| Operation | Complexity |
|------------|------------|
| insert | O(log n) |
| erase | O(log n) |
| find | O(log n) |

---

## unordered_set / unordered_map

Average

O(1)

Worst

O(n)

---

# Array Complexities

| Operation | Complexity |
|------------|------------|
| Access | O(1) |
| Search | O(n) |
| Insert | O(n) |
| Delete | O(n) |

---

# Linked List Complexities

| Operation | Complexity |
|------------|------------|
| Insert Head | O(1) |
| Insert Tail | O(1)* |
| Delete Head | O(1) |
| Search | O(n) |
| Random Access | O(n) |

---

# Binary Search Tree

Average

Search → O(log n)

Insert → O(log n)

Delete → O(log n)

Worst Case

O(n)

---

# Heap

| Operation | Complexity |
|------------|------------|
| Insert | O(log n) |
| Delete | O(log n) |
| Peek | O(1) |

---

# Graph

Adjacency List

Space → O(V + E)

Adjacency Matrix

Space → O(V²)

DFS

O(V + E)

BFS

O(V + E)

---

# Sorting Algorithms

| Algorithm | Best | Average | Worst | Stable |
|------------|------|----------|--------|---------|
| Bubble | O(n) | O(n²) | O(n²) | ✅ |
| Selection | O(n²) | O(n²) | O(n²) | ❌ |
| Insertion | O(n) | O(n²) | O(n²) | ✅ |
| Merge | O(n log n) | O(n log n) | O(n log n) | ✅ |
| Quick | O(n log n) | O(n log n) | O(n²) | ❌ |
| Heap | O(n log n) | O(n log n) | O(n log n) | ❌ |

---

# Searching

Linear Search

O(n)

Binary Search

O(log n)

Requirements

- Sorted Array
- Monotonic Condition

---

# Binary Tree Traversals

Preorder

```
Root
Left
Right
```

Inorder

```
Left
Root
Right
```

Postorder

```
Left
Right
Root
```

Level Order

```
Queue (BFS)
```

---

# DFS vs BFS

DFS

- Stack
- Recursion
- Backtracking
- Trees

BFS

- Queue
- Shortest Path (Unweighted)
- Level Order

---

# Problem Solving Patterns

## Two Pointer

Use When

- Sorted Array
- Pair Problems
- Remove Duplicates

Examples

- Two Sum II
- 3Sum
- Container With Most Water

---

## Sliding Window

Use When

- Contiguous Subarray
- Substring
- Maximum/Minimum Window

Examples

- Longest Substring Without Repeating Characters
- Maximum Sum Subarray

---

## Prefix Sum

Use When

- Repeated Range Sum
- Subarray Sum

Examples

- Subarray Sum Equals K
- Range Sum Query

---

## Fast & Slow Pointer

Use When

- Linked List
- Cycle Detection

Examples

- Middle Node
- Linked List Cycle
- Happy Number

---

## Binary Search

Use When

- Sorted Data
- Monotonic Answer

Examples

- Search Insert Position
- Koko Eating Bananas

---

## Hashing

Use When

- Frequency Count
- Fast Lookup

Data Structures

- unordered_map
- unordered_set

Examples

- Two Sum
- Group Anagrams

---

## Heap

Use When

- Top K
- Largest
- Smallest
- Streaming Data

Examples

- Kth Largest
- Top K Frequent

---

## Recursion

Use When

- Divide Problem
- Tree
- Backtracking

---

## Backtracking

Template

```
Choose

Explore

Undo
```

Examples

- N Queens
- Sudoku
- Subsets
- Permutations

---

## Dynamic Programming

Identify

- Overlapping Subproblems
- Optimal Substructure

Techniques

- Memoization
- Tabulation

---

## Greedy

Use When

Local optimum always leads to global optimum.

Examples

- Activity Selection
- Jump Game
- Minimum Arrows

---

# Binary Search Template

```cpp
while(left<=right){

    int mid=left+(right-left)/2;

    if(arr[mid]==target)
        return mid;

    else if(arr[mid]<target)
        left=mid+1;

    else
        right=mid-1;
}
```

---

# DFS Template

```cpp
void dfs(int node){

    visited[node]=true;

    for(auto next:adj[node]){

        if(!visited[next])
            dfs(next);

    }
}
```

---

# BFS Template

```cpp
queue<int> q;

q.push(start);

visited[start]=true;

while(!q.empty()){

    int node=q.front();

    q.pop();

    for(auto next:adj[node]){

        if(!visited[next]){

            visited[next]=true;

            q.push(next);

        }

    }

}
```

---

# Union Find Template

```cpp
find(x)

union(x,y)

path compression

union by rank
```

---

# Monotonic Stack Template

```cpp
while(!st.empty() && st.top()<current){

    st.pop();

}

st.push(current);
```

---

# Sliding Window Template

```cpp
left=0;

for(right=0;right<n;right++){

    expand window

    while(window invalid){

        shrink window

        left++;

    }

    update answer;

}
```

---

# Two Pointer Template

```cpp
left=0;

right=n-1;

while(left<right){

    if(condition)

        left++;

    else

        right--;

}
```

---

# Recursion Template

```cpp
solve(){

    if(base case)

        return;

    recursive call;

}
```

---

# Backtracking Template

```cpp
backtrack(){

    if(goal){

        answer.push_back(path);

        return;

    }

    for(each choice){

        choose;

        backtrack();

        undo;

    }

}
```

---

# Common Interview Edge Cases

Always Test

- Empty Array
- Single Element
- Duplicate Values
- Negative Numbers
- Large Input
- Already Sorted
- Reverse Sorted
- All Same Values
- Integer Overflow
- Null Pointer

---

# Coding Interview Checklist

Before Coding

☐ Understand problem

☐ Clarify constraints

☐ Discuss brute force

☐ Think optimization

---

During Coding

☐ Clean variable names

☐ Handle edge cases

☐ Avoid repeated code

☐ Follow correct syntax

---

After Coding

☐ Dry Run

☐ Time Complexity

☐ Space Complexity

☐ Explain optimization

---

# Must-Know Algorithms

Searching

- Binary Search

Sorting

- Merge Sort
- Quick Sort
- Heap Sort

Array

- Kadane's Algorithm
- Prefix Sum
- Difference Array

Strings

- Sliding Window

Linked List

- Floyd Cycle Detection

Trees

- DFS
- BFS

Graphs

- BFS
- DFS
- Dijkstra
- Topological Sort
- Union Find

DP

- Memoization
- Tabulation

---

# Frequently Asked LeetCode Problems

Arrays

- Two Sum
- Best Time to Buy and Sell Stock
- Product Except Self
- 3Sum

Strings

- Valid Anagram
- Longest Substring Without Repeating Characters

Linked List

- Reverse Linked List
- Merge Two Sorted Lists
- Linked List Cycle

Trees

- Maximum Depth
- Invert Binary Tree
- Validate BST
- LCA

Graphs

- Number of Islands
- Clone Graph
- Course Schedule

DP

- Climbing Stairs
- House Robber
- Coin Change
- Longest Increasing Subsequence

---

# Final Rule

> **Learn Patterns, not Problems.**

Every new problem should strengthen one of these patterns:

- Two Pointer
- Sliding Window
- Binary Search
- Hashing
- Prefix Sum
- Stack
- Queue
- Heap
- DFS
- BFS
- Backtracking
- Dynamic Programming

If you can identify the correct pattern quickly, you're already halfway to the solution.