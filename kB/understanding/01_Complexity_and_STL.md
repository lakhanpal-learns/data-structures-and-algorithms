# Complexity & STL

## Why DSA?

- Solve problems efficiently.
- Write optimized code.
- Crack coding interviews.
- Improve logical thinking.

---

# Time Complexity

Measures how execution time grows as input size increases.

| Complexity | Meaning |
|------------|----------|
| O(1) | Constant |
| O(log n) | Logarithmic |
| O(n) | Linear |
| O(n log n) | Linearithmic |
| O(n²) | Quadratic |
| O(2ⁿ) | Exponential |
| O(n!) | Factorial |

---

# Space Complexity

Measures extra memory used.

Examples

Variables → O(1)

Array → O(n)

Recursion Stack → O(n)

---

# STL

## Sequence Containers

- vector
- string
- deque

## Associative Containers

- set
- unordered_set
- map
- unordered_map

## Container Adaptors

- stack
- queue
- priority_queue

---

# Iterators

Iterator behaves like a pointer.

```cpp
auto it = v.begin();

cout<<*it;

it++;

it--;

it-v.begin();