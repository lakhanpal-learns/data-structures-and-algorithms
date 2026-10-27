# DSA Progress Dashboard & Roadmap

> **Repository:** [data-structures-and-algorithms](https://github.com/lakhanpal-learns/data-structures-and-algorithms)  
> **Purpose:** One place to track documented problems, the long-term DSA target, and next improvements.

## 1. Repository documentation snapshot

These counts are based on problem Markdown files currently stored in the repository's Easy/Medium/Hard problem folders. Folder-based categories reflect the repository structure, not necessarily the algorithm pattern used in every problem.

| Repository folder/category | Easy | Medium | Hard | Total |
|---|---:|---:|---:|---:|
| Arrays | 13 | 15 | 0 | **28** |
| Backtracking | 1 | 1 | 0 | **2** |
| Hash table folder* | 8 | 7 | 0 | **15** |
| Pointer / two-pointer folder | 7 | 0 | 0 | **7** |
| Recursion | 6 | 0 | 0 | **6** |
| Sliding window | 1 | 0 | 0 | **1** |
| Strings | 1 | 0 | 0 | **1** |
| **Total** | **37** | **23** | **0** | **60** |

- **Easy notes:** 37
- **Medium notes:** 23
- **Hard notes:** 0
- **Total problem write-ups:** 60

\*Counts follow folder names. Some files under the hash table folder cover linked lists or other concepts, so folder totals are not a perfect algorithm-pattern classification.

> **Important:** A note in the repository does not prove that a problem was independently solved or accepted on LeetCode. LeetCode submission status is not connected to this dashboard.

## 2. Long-term DSA learning roadmap

The roadmap below preserves the planned topic targets. The target is **465 problems** across 22 phases. Use it as a syllabus; the repository snapshot above is the current count of written problem notes. These are different measurements.

| Phase | Topic | Total target | Easy | Medium | Hard |
|---:|---|---:|---:|---:|---:|
| 1 | Arrays | 30 | 10 | 15 | 5 |
| 2 | Strings | 25 | 8 | 13 | 4 |
| 3 | Hash Table | 25 | 8 | 13 | 4 |
| 4 | Two Pointers | 20 | 7 | 10 | 3 |
| 5 | Sliding Window | 20 | 6 | 11 | 3 |
| 6 | Binary Search | 20 | 7 | 10 | 3 |
| 7 | Stack | 20 | 7 | 10 | 3 |
| 8 | Queue | 10 | 4 | 5 | 1 |
| 9 | Linked List | 20 | 7 | 10 | 3 |
| 10 | Recursion | 15 | 5 | 8 | 2 |
| 11 | Binary Tree | 35 | 10 | 18 | 7 |
| 12 | BST | 15 | 5 | 8 | 2 |
| 13 | Heap (Priority Queue) | 20 | 6 | 11 | 3 |
| 14 | Greedy | 25 | 7 | 14 | 4 |
| 15 | Backtracking | 20 | 5 | 11 | 4 |
| 16 | Graph (BFS + DFS) | 35 | 10 | 18 | 7 |
| 17 | Union Find | 10 | 3 | 5 | 2 |
| 18 | Topological Sort | 10 | 3 | 5 | 2 |
| 19 | Trie | 10 | 3 | 5 | 2 |
| 20 | Prefix Sum | 15 | 5 | 8 | 2 |
| 21 | Bit Manipulation | 20 | 7 | 10 | 3 |
| 22 | Dynamic Programming | 50 | 12 | 28 | 10 |
| **Total** | | **465** | **145** | **246** | **74** |

## 3. Curated Medium problem queue (40–70% acceptance)

A separate problem-by-problem queue is available, filtered for **LeetCode Medium problems with approximately 40–70% acceptance**. Acceptance rates change, so treat listed percentages as reference snapshots and verify on the linked LeetCode page.

- [Open the Medium Problem Roadmap](MEDIUM_PROBLEM_ROADMAP.md)
- The queue currently contains **40 selected problems** across arrays, hashing, sliding window, stack, greedy, graphs, trees, dynamic programming, and design.
- Status begins as `Planned`; update it only after attempting each problem.

## 4. Latest learning activity

- Added the LeetCode 14 — Longest Common Prefix write-up in `DSA/string/easy/`, including the C++ solution, dry runs, bounds-check explanation, complexity, and edge cases.
- Added the LeetCode 560 — Subarray Sum Equals K write-up, including the algorithm-discovery process and prefix-sum frequency reasoning.
- Added the LeetCode 209 — Minimum Size Subarray Sum write-up, deriving sliding window from brute force and explaining repeated shrinking, inclusive window length, and the sentinel initialization.
- Added the LeetCode 34 — Find First and Last Position of Element in Sorted Array write-up, covering `binary_search()`, `lower_bound()`, `upper_bound()`, and a step-by-step dry run.
- The Array folders currently contain **28 problem write-ups: 13 Easy and 15 Medium**, based on the latest folder screenshots. This is documentation progress, not a claim that every problem has been accepted on LeetCode.
- Dry-run test case for LeetCode 209: `target = 7`, `nums = [2, 3, 1, 2, 4, 3]` → output `2` (shortest valid subarray: `[4, 3]`).
- This records documentation and reviewed test cases only; it does **not** claim verified LeetCode Accepted submissions.

## 5. Next improvements

- [ ] Add or update each problem's status: `Planned`, `Attempted`, `Solved`, `Accepted`, or `Needs Revision`.
- [ ] Record the LeetCode URL and current acceptance status when known.
- [ ] Track date solved, attempts, and last revision date.
- [ ] Refresh repository note counts when files are added or removed.
- [ ] Track actual solved progress separately from written notes.

## 6. Repository links

- [README](README.md)
- [DSA cheat sheet](dsa_sheet.md)
- [Problem-solving patterns](07_Problem_Solving_Patterns.md)
- [Medium Problem Roadmap](MEDIUM_PROBLEM_ROADMAP.md)
