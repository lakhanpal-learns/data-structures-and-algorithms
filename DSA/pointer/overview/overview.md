# overview 

# What is the Two Pointer Technique?

The Two Pointer technique means using **two indices (pointers)** to traverse a data structure (usually an array or string) instead of one.

**Instead of checking every possible pair (O(n²))**, two pointers often reduce **the solution to O(n)**.

Array
0   1   2   3   4   5
2   4   6   8   9  10
^                   ^
L                   R

Here,

Left Pointer (L)
Right Pointer (R)

<!-- Both move according to some condition. -->


# Why use Two Pointers?

Suppose you want to find two numbers whose sum is 12.

Normal way:
2 + 4
2 + 6
2 + 8
2 + 9
...

<!-- Every pair is checked.

Time Complexity

O(n²) -->

With two pointers (sorted array):

2 4 6 8 9 10
L         R

<!-- Current Sum

2 + 10 = 12

Found immediately. -->

Only one comparison.



# Different Types of Two Pointer Problems

There are five major patterns.

## Pattern 1: Opposite Direction

Pointers start from opposite ends.

0 1 2 3 4 5

2 4 6 8 9 10

L         R

They move toward each other.

Used in

Two Sum II
Palindrome
Container With Most Water
Trapping Rain Water

### Movement example

If

sum < target

Move left pointer.

L++

If

sum > target

Move right pointer.

R--

## Pattern 2: Same Direction

Both pointers move left to ight.

Slow
↓

1 2 2 3 3 4

Fast
      ↓

Used in

Remove Duplicates
Remove Element
Move Zeroes

<!-- Usually

Slow = answer position

Fast = searching position -->

## Pattern 3: Fast and Slow Pointer
Slow

↓

1 → 2 → 3 → 4 → 5

↓

Fast

Fast moves twice.

Slow +=1

Fast +=2

**Mostly for Linked Lists.**

Used in

Detect cycle
Find middle node

## Pattern 4: Sliding Window

Both pointers move forward.

L

↓

1 2 3 4 5 6 7

      ↑
      R

Window expands.

Sometimes it shrinks.

Used in

Longest substring
Minimum window
Maximum sum subarray


## Pattern 5: Partition Pointer

Mostly used in Quick Sort.

< Pivot | > Pivot

Pointer rearranges elements.


# core logic 
Every problem has one question:

Which pointer should move?

Suppose

2 4 6 8 10
L       R

Target = 15

Current

2 + 10 = 12

Too small.

Can moving Right help?

No.

Right already points to the biggest number.

Only Left can increase the sum.

So

L++

Now

4 + 10 = 14

Still small.

Again

L++
6 + 10 = 16

Too large.

Now decrease.

R--
6 + 8 = 14

Continue...

This reasoning is why the algorithm works on sorted arrays.

# Common LeetCode Problems
Beginner
Valid Palindrome
Reverse String
Remove Duplicates from Sorted Array
Remove Element
Move Zeroes
Squares of a Sorted Array

Intermediate
Two Sum II
Container With Most Water
3Sum
4Sum
Trapping Rain Water

# How to Recognize a Two Pointer Problem

Ask yourself these questions:

Is the array sorted?
Am I comparing pairs?
Can one pointer move based on the current answer?
Am I using nested loops that might be optimized?
Can each pointer move only forward (or inward) once?

If yes to several of these, think about the two-pointer technique.









