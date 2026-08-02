# Interview Patterns

## Pattern 1
<!-- Frequency Counting -->

Example

1 2 2 3 3 3 4

Need frequency

Answer

1 → 1

2 → 2

3 → 3

4 → 1

Use

unordered_map<int,int> freq;

Example

for(int num : nums)
{
    freq[num]++;
}

## Pattern 2
<!-- Duplicate Detection -->

Example

1 2 3 4 5 2

Need

Does duplicate exist?

Use

unordered_set<int>

Example

unordered_set<int> s;

for(int x : nums)
{
    if(s.find(x)!=s.end())
        return true;

    s.insert(x);
}

## Pattern 3
Fast Lookup

Question

Is 105 present?

Instead of

O(n)

search,

use

unordered_set

Average

O(1)

## Pattern 4
Key → Value Mapping

Example

Student

↓

Marks

unordered_map<string,int>

## Pair Finding

Question

Find two numbers whose sum is 9.

Use

unordered_map

instead of nested loops.

This is the famous Two Sum problem.

## Pattern 6
Grouping

Example

eat

tea

ate

Need

[eat tea ate]

Use

unordered_map<string, vector<string>>

This is the Group Anagrams problem.

## Pattern 7
Memoization

Store already computed results.

Example

Fibonacci

Instead of recomputing,

store

5 → 5

6 → 8

7 → 13



# How to Recognize a Hash Table Problem

When reading a problem, ask yourself these questions:

1. Do I need fast searching?
Is x present?

Use

unordered_set
2. Do I need frequencies?
How many times does each number occur?

Use

unordered_map<int,int>
3. Do I need key → value?

Example

Student

↓

Marks

Use

unordered_map
4. Have I seen this value before?

Example

Duplicate detection

Use

unordered_set

5. Can I solve it in one pass while remembering previous elements?

If yes, a hash table is often the right choice.

# LeetCode Roadmap
Beginner
| Problem                    | Main Concept               |
| -------------------------- | -------------------------- |
| Two Sum                    | HashMap lookup             |
| Contains Duplicate         | HashSet                    |
| Valid Anagram              | Frequency counting         |
| Intersection of Two Arrays | HashSet                    |
| Happy Number               | Detect cycles with HashSet |

Intermediate
| Problem                       | Main Concept             |
| ----------------------------- | ------------------------ |
| Group Anagrams                | HashMap + grouping       |
| Top K Frequent Elements       | Frequency map            |
| Longest Consecutive Sequence  | HashSet                  |
| Isomorphic Strings            | Two HashMaps             |
| Find All Anagrams in a String | Sliding Window + HashMap |

Advanced
| Problem                       | Main Concept                 |
| ----------------------------- | ---------------------------- |
| LRU Cache                     | HashMap + Doubly Linked List |
| Subarray Sum Equals K         | Prefix Sum + HashMap         |
| Minimum Window Substring      | Sliding Window + HashMap     |
| Copy List with Random Pointer | Node mapping                 |
| Word Ladder                   | HashSet + BFS                |


# cheat- sheet 
| Situation                   | Best STL Container                  |
| --------------------------- | ----------------------------------- |
| Store `Key → Value`         | `unordered_map`                     |
| Store only unique values    | `unordered_set`                     |
| Need sorted keys            | `map`                               |
| Need sorted unique values   | `set`                               |
| Count frequencies           | `unordered_map<T, int>`             |
| Check duplicates            | `unordered_set<T>`                  |
| Fast existence check        | `unordered_set<T>`                  |
| Pair lookup (e.g., Two Sum) | `unordered_map`                     |
| Group related items         | `unordered_map<Key, vector<Value>>` |
