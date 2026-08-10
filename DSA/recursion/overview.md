# Recursion for DSA & LeetCode — Complete Guide

Bro, if your goal is **LeetCode**, don't learn recursion as just “a function calling itself.” You need to understand **how to think recursively**, identify when recursion is appropriate, and know the standard patterns.

The goal is:

> **Given a problem, recognize the recursive state → define the base case → make the recursive call → trust the smaller problem → combine the result.**

---

# 1. What is Recursion?

A function calling itself with a **smaller/simpler version of the same problem**.

```cpp
void solve(int n) {
    if (n == 0) return;  // base case

    cout << n << " ";

    solve(n - 1);        // recursive call
}
```

Calling:

```cpp
solve(5);
```

produces:

```text
5
4
3
2
1
```

The important thing isn't the syntax.

The important question is:

> **What smaller problem can I give to the same function?**

---

# 2. The 3 Things Every Recursive Solution Needs

Almost every recursive solution can be understood through three components.

### ① State / Parameters

What information does the function need to know?

```cpp
solve(index)
```

or

```cpp
solve(node)
```

or

```cpp
solve(index, target)
```

or

```cpp
solve(row, col)
```

---

### ② Base Case

When should recursion stop?

```cpp
if (index == n)
    return;
```

Without a base case:

```text
function
 ↓
function
 ↓
function
 ↓
function
 ↓
...
```

Eventually stack overflow.

---

### ③ Recursive Case

Move toward the base case.

```cpp
solve(index + 1);
```

or

```cpp
solve(n - 1);
```

or

```cpp
solve(node->left);
```

---

# 3. The Most Important Mental Model

Suppose:

```cpp
int factorial(int n) {
    if (n == 0)
        return 1;

    return n * factorial(n - 1);
}
```

For:

```cpp
factorial(5)
```

think:

```text
5 * factorial(4)
        ↓
     4 * factorial(3)
             ↓
          3 * factorial(2)
                  ↓
               2 * factorial(1)
                       ↓
                    1 * factorial(0)
                              ↓
                              1
```

Then it comes back:

```text
factorial(0) = 1

factorial(1) = 1 × 1 = 1
factorial(2) = 2 × 1 = 2
factorial(3) = 3 × 2 = 6
factorial(4) = 4 × 6 = 24
factorial(5) = 5 × 24 = 120
```

This is called **unwinding**.

---

# 4. Recursion Has Two Phases

This is extremely important for LeetCode.

## Going DOWN

Recursive calls happen:

```text
solve(5)
 ↓
solve(4)
 ↓
solve(3)
 ↓
solve(2)
 ↓
solve(1)
 ↓
solve(0)
```

## Coming BACK UP

After base case:

```text
solve(0)
 ↑
solve(1)
 ↑
solve(2)
 ↑
solve(3)
 ↑
solve(4)
 ↑
solve(5)
```

A lot of tree problems depend on what you do **while going down vs while coming back up**.

---

# 5. Example: Print 1 to N

```cpp
void print(int n) {
    if (n == 0)
        return;

    print(n - 1);

    cout << n << " ";
}
```

For:

```cpp
print(5);
```

Call stack:

```text
print(5)
 print(4)
  print(3)
   print(2)
    print(1)
     print(0)
```

Then printing happens while returning:

```text
1 2 3 4 5
```

Compare:

```cpp
cout << n;
print(n - 1);
```

gives:

```text
5 4 3 2 1
```

Where you put the operation matters.

---

# 6. Recursion vs Iteration

Many recursive problems **can** be solved using loops.

Example:

```cpp
int factorial(int n) {
    int ans = 1;

    for(int i = 1; i <= n; i++)
        ans *= i;

    return ans;
}
```

Recursion:

```cpp
int factorial(int n) {
    if(n == 0)
        return 1;

    return n * factorial(n - 1);
}
```

Don't think:

> “Recursion is always better.”

It isn't.

Use recursion when the problem naturally has:

* nested structure
* trees
* graphs
* divide-and-conquer
* backtracking
* subproblems
* repeated branching

---

# 7. The Golden Recursive Thinking Pattern

When you see a problem, ask:

### Step 1

**What is changing?**

Example:

```text
index
```

### Step 2

**What is the smallest problem?**

Example:

```text
index == n
```

### Step 3

**What choices do I have?**

Example:

```text
take
don't take
```

### Step 4

**What does the smaller recursive problem return?**

### Step 5

**How do I use that returned answer?**

That's recursive problem solving.

---

# 8. Recursion Template #1 — Simple Linear Recursion

```cpp
void solve(int i, int n) {

    if(i == n)
        return;

    // work

    solve(i + 1, n);
}
```

Used for:

* arrays
* strings
* printing
* traversing
* simple recursion

Example:

```cpp
void printArray(vector<int>& arr, int i) {
    if(i == arr.size())
        return;

    cout << arr[i] << " ";

    printArray(arr, i + 1);
}
```

---

# 9. Template #2 — Recursion Returning an Answer

```cpp
int solve(int n) {

    if(base case)
        return base_answer;

    return something + solve(smaller_problem);
}
```

Example:

```cpp
int sum(int n) {
    if(n == 0)
        return 0;

    return n + sum(n - 1);
}
```

This pattern appears everywhere.

---

# 10. Template #3 — Multiple Recursive Calls

Example Fibonacci:

```cpp
int fib(int n) {

    if(n <= 1)
        return n;

    return fib(n - 1) + fib(n - 2);
}
```

The recursion tree:

```text
                fib(5)
              /       \
          fib(4)       fib(3)
         /    \        /    \
      fib(3) fib(2) fib(2) fib(1)
```

This is called **branching recursion**.

The problem:

```text
Time = O(2^n)
```

because you're repeatedly solving the same subproblems.

This leads to **Dynamic Programming**.

---

# 11. Recursion → Memoization → DP

This connection is VERY important.

Consider:

```cpp
fib(5)
```

You calculate:

```text
fib(3)
```

multiple times.

So store the result.

```cpp
vector<int> dp(n + 1, -1);

int fib(int n) {

    if(n <= 1)
        return n;

    if(dp[n] != -1)
        return dp[n];

    return dp[n] = fib(n - 1) + fib(n - 2);
}
```

Now:

```text
Time = O(n)
Space = O(n)
```

So remember:

```text
Recursion
    ↓
Repeated subproblems
    ↓
Memoization
    ↓
Dynamic Programming
```

Not every recursive problem is DP, though.

---

# 12. Recursion + Backtracking

This is one of the **most important recursion patterns for LeetCode**.

Typical problems:

* subsets
* permutations
* combinations
* combination sum
* N-Queens
* Sudoku
* word search

The basic idea:

```text
Choose
 ↓
Explore
 ↓
Undo
```

Template:

```cpp
void backtrack(...) {

    if(base case) {
        // answer
        return;
    }

    for(each choice) {

        // choose

        backtrack(...);

        // undo
    }
}
```

---

# 13. Subsets — The Most Important Example

Suppose:

```text
[1,2,3]
```

Every element has two choices:

```text
Take
Don't take
```

So:

```text
                 []
              /      \
            [1]       []
           /   \      /  \
        [1,2] [1]   [2]   []
```

Code:

```cpp
void solve(int index, vector<int>& nums,
           vector<int>& current,
           vector<vector<int>>& ans) {

    if(index == nums.size()) {
        ans.push_back(current);
        return;
    }

    // Take
    current.push_back(nums[index]);

    solve(index + 1, nums, current, ans);

    current.pop_back();

    // Don't take
    solve(index + 1, nums, current, ans);
}
```

This is a pattern you should memorize conceptually, not blindly memorize code.

---

# 14. Why `pop_back()`?

This is the part beginners usually don't understand.

Suppose:

```text
current = [1,2]
```

You choose:

```text
3
```

Now:

```text
current = [1,2,3]
```

After exploring all possibilities involving `3`, you need to go back:

```text
current = [1,2]
```

Therefore:

```cpp
current.pop_back();
```

That's the **backtracking** part.

---

# 15. Permutations

For:

```text
[1,2,3]
```

we want:

```text
123
132
213
231
312
321
```

Template:

```cpp
void solve(vector<int>& nums,
           vector<bool>& used,
           vector<int>& current,
           vector<vector<int>>& ans) {

    if(current.size() == nums.size()) {
        ans.push_back(current);
        return;
    }

    for(int i = 0; i < nums.size(); i++) {

        if(used[i])
            continue;

        used[i] = true;
        current.push_back(nums[i]);

        solve(nums, used, current, ans);

        current.pop_back();
        used[i] = false;
    }
}
```

Important pattern:

```text
choose
 ↓
mark
 ↓
recursive call
 ↓
unchoose
 ↓
unmark
```

---

# 16. Combination Problems

Combination problems usually have:

```text
start index
```

Example:

```text
[1,2,3,4]
choose 2
```

You don't want:

```text
1,2
2,1
```

because combinations don't care about order.

So:

```cpp
for(int i = start; i < nums.size(); i++) {

    current.push_back(nums[i]);

    solve(i + 1, ...);

    current.pop_back();
}
```

The key:

```cpp
solve(i + 1)
```

prevents using the same element again.

---

# 17. Tree Recursion

This is where recursion becomes extremely natural.

A tree is already recursive:

```text
        1
       / \
      2   3
     / \
    4   5
```

Every node has:

```text
left subtree
right subtree
```

So:

```cpp
void preorder(TreeNode* root) {

    if(root == nullptr)
        return;

    cout << root->val;

    preorder(root->left);

    preorder(root->right);
}
```

The structure is literally:

```text
Node
 ↓
Left subtree
 ↓
Right subtree
```

---

# 18. Three Basic Tree Traversals

### Preorder

```text
Root → Left → Right
```

```cpp
void preorder(TreeNode* root) {

    if(!root)
        return;

    cout << root->val << " ";

    preorder(root->left);
    preorder(root->right);
}
```

### Inorder

```text
Left → Root → Right
```

```cpp
void inorder(TreeNode* root) {

    if(!root)
        return;

    inorder(root->left);

    cout << root->val << " ";

    inorder(root->right);
}
```

### Postorder

```text
Left → Right → Root
```

```cpp
void postorder(TreeNode* root) {

    if(!root)
        return;

    postorder(root->left);
    postorder(root->right);

    cout << root->val << " ";
}
```

---

# 19. Why Tree Recursion Is So Powerful

Suppose you want the maximum depth.

```cpp
int maxDepth(TreeNode* root) {

    if(root == nullptr)
        return 0;

    int left = maxDepth(root->left);
    int right = maxDepth(root->right);

    return 1 + max(left, right);
}
```

The key thinking:

> “I don't need to calculate the entire tree myself. I'll ask the left subtree for its answer and the right subtree for its answer.”

This is one of the biggest upgrades in recursive thinking.

---

# 20. The "Trust the Recursion" Principle

This is probably the hardest thing for you initially.

Don't mentally execute every recursive call.

Suppose:

```cpp
int maxDepth(TreeNode* root) {

    if(!root)
        return 0;

    int left = maxDepth(root->left);
    int right = maxDepth(root->right);

    return 1 + max(left, right);
}
```

Don't think:

> “Okay, now `left` calls recursion, then that calls recursion, then…”

Instead think:

> **`maxDepth(root->left)` will correctly return the depth of the left subtree.**

Trust it.

Then:

```text
left = left subtree answer
right = right subtree answer

current answer = 1 + max(left,right)
```

This concept is essential for solving recursive LeetCode problems.

---

# 21. Recursion on Linked Lists

Linked lists are also naturally recursive.

Example: reverse a linked list.

One recursive solution:

```cpp
ListNode* reverseList(ListNode* head) {

    if(head == nullptr || head->next == nullptr)
        return head;

    ListNode* newHead = reverseList(head->next);

    head->next->next = head;
    head->next = nullptr;

    return newHead;
}
```

The important concept is:

```text
Reverse the rest of the list.
Then put current node at the end.
```

---

# 22. Divide and Conquer

Another major recursion pattern.

General idea:

```text
Problem
   ↓
Divide
   ↓
Solve smaller problems
   ↓
Combine
```

Examples:

* Merge Sort
* Quick Sort
* Binary Search
* Maximum Subarray variants
* Tree algorithms

---

# 23. Binary Search Is Recursive

```cpp
int binarySearch(vector<int>& nums,
                 int low,
                 int high,
                 int target) {

    if(low > high)
        return -1;

    int mid = low + (high - low) / 2;

    if(nums[mid] == target)
        return mid;

    if(nums[mid] > target)
        return binarySearch(nums, low, mid - 1, target);

    return binarySearch(nums, mid + 1, high, target);
}
```

Every call cuts the search space approximately in half.

Therefore:

```text
Time = O(log n)
```

---

# 24. Merge Sort

Classic divide-and-conquer recursion:

```text
[5 2 4 1]

       [5 2 4 1]
        /      \
     [5 2]    [4 1]
     /  \      /  \
   [5] [2]   [4] [1]
```

Then merge upward.

Complexity:

```text
Time = O(n log n)
Space = O(n)
```

---

# 25. Recursion on Strings

Example: palindrome.

```cpp
bool isPalindrome(string& s, int left, int right) {

    if(left >= right)
        return true;

    if(s[left] != s[right])
        return false;

    return isPalindrome(s, left + 1, right - 1);
}
```

Notice the state:

```text
left
right
```

Each recursive call moves inward.

---

# 26. Recursion on Arrays

Example: check if array is sorted.

```cpp
bool sorted(vector<int>& arr, int i) {

    if(i == arr.size() - 1)
        return true;

    if(arr[i] > arr[i + 1])
        return false;

    return sorted(arr, i + 1);
}
```

Again:

```text
State = i
Base = last element
Smaller problem = i + 1
```

---

# 27. Recursion on a Grid

Used in:

* Number of Islands
* Flood Fill
* Word Search
* Maze problems
* DFS

Example:

```cpp
void dfs(vector<vector<char>>& grid, int r, int c) {

    if(r < 0 || c < 0 ||
       r >= grid.size() ||
       c >= grid[0].size() ||
       grid[r][c] == '0')
        return;

    grid[r][c] = '0';

    dfs(grid, r + 1, c);
    dfs(grid, r - 1, c);
    dfs(grid, r, c + 1);
    dfs(grid, r, c - 1);
}
```

This is recursion + DFS.

---

# 28. Graph DFS

Same concept.

```cpp
void dfs(int node,
         vector<vector<int>>& graph,
         vector<bool>& visited) {

    visited[node] = true;

    for(int neighbor : graph[node]) {

        if(!visited[neighbor]) {
            dfs(neighbor, graph, visited);
        }
    }
}
```

So don't treat:

```text
Tree recursion
Graph DFS
Grid DFS
```

as completely different things.

They're variations of the same recursive idea:

```text
Visit current
 ↓
Visit connected children/neighbors
```

---

# 29. Recursion + State

This is a huge LeetCode concept.

The parameters of your recursive function represent the **state**.

Examples:

### Array

```cpp
solve(index)
```

### Subset

```cpp
solve(index, current)
```

### Combination

```cpp
solve(start, current)
```

### Grid

```cpp
solve(row, col)
```

### Tree

```cpp
solve(node)
```

### Binary search

```cpp
solve(low, high)
```

### DP

```cpp
solve(index, remaining)
```

### Knapsack

```cpp
solve(index, capacity)
```

When stuck, ask:

> **What information do I need to describe where I currently am in the problem?**

Those usually become your parameters.

---

# 30. How to Find the Base Case

Use this rule:

> **What is the smallest input for which I already know the answer?**

Examples:

### Factorial

```cpp
n == 0
```

### Array traversal

```cpp
i == n
```

### Linked list

```cpp
head == nullptr
```

### Tree

```cpp
root == nullptr
```

### Palindrome

```cpp
left >= right
```

### Subsets

```cpp
index == nums.size()
```

### Backtracking

```cpp
current.size() == targetSize
```

### Binary search

```cpp
low > high
```

---

# 31. Common Recursion Mistake #1

### No progress toward base case

Bad:

```cpp
solve(n);
```

inside:

```cpp
solve(n)
```

Nothing changes.

Correct:

```cpp
solve(n - 1);
```

or:

```cpp
solve(index + 1);
```

Your recursive state must move toward termination.

---

# 32. Common Mistake #2 — Wrong Base Case

Example:

```cpp
int factorial(int n) {

    if(n == 1)
        return 1;

    return n * factorial(n - 1);
}
```

This works for positive `n`.

But:

```cpp
factorial(0)
```

would never reach the base case.

Better:

```cpp
if(n <= 1)
    return 1;
```

---

# 33. Common Mistake #3 — Forgetting Return

Wrong:

```cpp
int solve(int n) {

    if(n == 0)
        return 0;

    solve(n - 1);
}
```

The function returns `int`, but you're not returning the recursive result.

Correct:

```cpp
return solve(n - 1);
```

or combine it:

```cpp
return n + solve(n - 1);
```

---

# 34. Common Mistake #4 — Confusing Recursive Call With Answer

This:

```cpp
solve(n - 1);
```

is just a function call.

This:

```cpp
return solve(n - 1);
```

means:

> “Whatever answer the smaller problem gives me, return that answer.”

And:

```cpp
return n + solve(n - 1);
```

means:

> “Take the smaller problem's answer and combine it with my current value.”

Very important distinction.

---

# 35. Common Mistake #5 — Modifying `vector` Without Undoing

Wrong backtracking:

```cpp
current.push_back(x);

solve(...);
```

If the vector is shared by reference, the modification remains.

Usually:

```cpp
current.push_back(x);

solve(...);

current.pop_back();
```

This gives:

```text
choose
explore
undo
```

---

# 36. Common Mistake #6 — Passing Huge Objects by Value

Bad:

```cpp
void solve(vector<int> nums)
```

Every call may copy the vector.

Usually:

```cpp
void solve(vector<int>& nums)
```

or:

```cpp
void solve(const vector<int>& nums)
```

depending on whether you modify it.

---

# 37. Recursion Stack

Each recursive call gets a stack frame.

Example:

```cpp
solve(3)
```

creates:

```text
Stack:

solve(3)
solve(2)
solve(1)
solve(0)
```

If each call uses O(1) extra memory:

```text
Space = O(number of recursive calls)
```

For:

```cpp
solve(n - 1)
```

usually:

```text
O(n)
```

stack space.

---

# 38. Time Complexity of Recursion

Don't automatically say:

> “Recursion = O(n).”

Wrong.

It depends on the recursion tree.

### One recursive call

```cpp
solve(n - 1)
```

Usually:

```text
O(n)
```

### Two recursive calls

```cpp
solve(n - 1)
solve(n - 2)
```

Potentially:

```text
O(2^n)
```

### Divide by 2

```cpp
solve(n / 2)
```

Usually:

```text
O(log n)
```

### Merge sort

```text
2 subproblems of size n/2
```

Result:

```text
O(n log n)
```

---

# 39. Recursion Complexity Cheat Sheet

| Pattern                   |   Typical Time |
| ------------------------- | -------------: |
| `f(n-1)`                  |           O(n) |
| `f(n/2)`                  |       O(log n) |
| `f(n-1) + f(n-2)`         |          O(2ⁿ) |
| Two halves + linear merge |     O(n log n) |
| Generate subsets          |          O(2ⁿ) |
| Generate permutations     |          O(n!) |
| Tree traversal            |           O(n) |
| Graph DFS                 |       O(V + E) |
| Grid DFS                  | O(rows × cols) |

These are typical patterns, not universal laws.

---

# 40. Recursion Problem Categories You Should Know

For LeetCode, I'd divide recursion into these categories:

```text
                    RECURSION
                       │
       ┌───────────────┼────────────────┐
       │               │                │
   Linear          Tree/DFS         Backtracking
       │               │                │
 arrays           binary tree       subsets
 strings          graph             permutations
 linked list      grid              combinations
       │               │                │
       └───────────────┼────────────────┘
                       │
                Divide & Conquer
                       │
              binary search
              merge sort
              quick sort
                       │
                       ↓
                 Recursion + DP
                       │
                 memoization
```

---

# 41. Problems You Should Solve in Order

Don't randomly jump into hard recursion problems.

## Level 1 — Basic Recursion

Learn the mechanics.

1. Print N to 1
2. Print 1 to N
3. Sum of N numbers
4. Factorial
5. Power of a number
6. Fibonacci
7. Reverse a string
8. Check palindrome
9. Check sorted array
10. Find maximum in array

---

# 42. Level 2 — Array/String Recursion

Then:

1. Reverse array
2. Linear search
3. Binary search
4. Check palindrome
5. Remove duplicates recursively
6. Generate subsequences
7. Generate subsets

---

# 43. Level 3 — Tree Recursion

Very important for LeetCode.

Practice:

1. Maximum Depth of Binary Tree
2. Same Tree
3. Invert Binary Tree
4. Symmetric Tree
5. Path Sum
6. Diameter of Binary Tree
7. Balanced Binary Tree
8. Lowest Common Ancestor
9. Binary Tree Level/Traversal problems

These teach you:

```text
return values from children
```

which is a critical recursion skill.

---

# 44. Level 4 — Backtracking

Then:

1. Subsets
2. Subsets II
3. Permutations
4. Permutations II
5. Combinations
6. Combination Sum
7. Combination Sum II
8. Letter Combinations of a Phone Number
9. Generate Parentheses
10. Word Search
11. N-Queens
12. Sudoku Solver

You don't need to master all immediately.

Start with:

```text
Subsets
↓
Combinations
↓
Permutations
↓
Combination Sum
↓
Generate Parentheses
↓
Word Search
```

---

# 45. Level 5 — Recursion + DP

Then learn:

* Climbing Stairs
* House Robber
* Coin Change
* 0/1 Knapsack
* Longest Common Subsequence
* Longest Increasing Subsequence
* Partition Equal Subset Sum

The important transition:

```text
Recursive solution
       ↓
Notice repeated states
       ↓
Memoization
       ↓
Bottom-up DP
```

---

# 46. The Most Important Backtracking Template

Memorize this **structure**:

```cpp
void backtrack(state) {

    if(goal_reached) {
        save_answer();
        return;
    }

    for(choice : choices) {

        if(invalid(choice))
            continue;

        make_choice(choice);

        backtrack(new_state);

        undo_choice(choice);
    }
}
```

Whenever you see:

> “Generate all possible…”

immediately consider backtracking.

Examples:

```text
all subsets
all permutations
all combinations
all valid parentheses
all paths
all arrangements
```

---

# 47. The Most Important Tree Template

```cpp
ReturnType solve(TreeNode* root) {

    if(root == nullptr)
        return base_value;

    ReturnType left = solve(root->left);
    ReturnType right = solve(root->right);

    return combine(root, left, right);
}
```

This single template can solve a huge number of tree problems.

---

# 48. The Most Important DFS Template

```cpp
void dfs(Node* node) {

    if(node == nullptr)
        return;

    // process current

    for(auto neighbor : node->neighbors) {

        if(!visited[neighbor]) {
            dfs(neighbor);
        }
    }
}
```

For grids:

```cpp
void dfs(int r, int c) {

    if(out_of_bounds || invalid)
        return;

    mark_visited();

    dfs(r + 1, c);
    dfs(r - 1, c);
    dfs(r, c + 1);
    dfs(r, c - 1);
}
```

---

# 49. How to Recognize a Recursion Problem on LeetCode

Look for phrases like:

### "Generate all..."

```text
Generate all subsets
Generate all permutations
Generate all combinations
```

→ **Backtracking**

---

### "For every node..."

```text
For each node in a tree...
```

→ **Tree recursion / DFS**

---

### "Explore connected..."

```text
Explore neighboring cells
Find connected components
```

→ **DFS recursion**

---

### "Split into smaller..."

```text
Divide the array
Search half
Sort halves
```

→ **Divide and conquer**

---

### "Choose or skip..."

```text
Take / don't take
Include / exclude
```

→ **Binary recursion / backtracking / DP**

---

### "Find maximum/minimum from subtrees"

```text
maximum depth
diameter
best path
```

→ **Tree recursion returning values**

---

# 50. A Powerful Question to Ask Yourself

When you see a recursion problem, literally write:

```text
What is my state?
What is my base case?
What is my choice?
What smaller problem do I call?
What do I do with the answer?
```

For example, maximum depth:

```text
State:
    root

Base:
    root == NULL

Choice:
    left subtree
    right subtree

Smaller problems:
    maxDepth(root->left)
    maxDepth(root->right)

Combine:
    1 + max(left, right)
```

That's the whole solution.

---

# 51. Recursion vs Backtracking

Don't confuse them.

**Recursion** is the mechanism:

```cpp
solve(...)
```

calling itself.

**Backtracking** is a problem-solving strategy:

```text
choose
↓
explore
↓
undo
```

So:

> **Backtracking usually uses recursion, but recursion doesn't necessarily mean backtracking.**

For example:

```cpp
maxDepth(root)
```

is recursion but not backtracking.

---

# 52. Recursion vs DFS

Same idea:

> DFS can be implemented recursively or iteratively.

Recursive DFS:

```cpp
dfs(node);
```

Iterative DFS:

```cpp
stack<int> st;
```

So:

```text
DFS = traversal strategy
Recursion = implementation technique
```

---

# 53. Recursion vs DP

Also different.

```text
Recursion
    ↓
calls itself
```

```text
DP
    ↓
avoid solving same subproblem repeatedly
```

You can have:

```text
Recursion without DP
Recursion + Memoization
Bottom-up DP without recursion
```

---

# 54. Your Recursion Learning Roadmap

For LeetCode, I would do it like this:

### Phase 1 — Understand mechanics

```text
factorial
sum
power
reverse
palindrome
array traversal
```

↓

### Phase 2 — Return values

```text
max/min
count
search
tree height
tree properties
```

↓

### Phase 3 — Divide & conquer

```text
binary search
merge sort
quick sort
```

↓

### Phase 4 — Tree recursion

```text
DFS
traversals
depth
diameter
path problems
LCA
```

↓

### Phase 5 — Backtracking

```text
subsets
combinations
permutations
combination sum
parentheses
word search
N-Queens
```

↓

### Phase 6 — Recursion → DP

```text
memoization
state
overlapping subproblems
bottom-up DP
```

---

# 55. Your Recursion Cheat Sheet

Keep this mentally available:

```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        RECURSION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Identify STATE
2. Identify BASE CASE
3. Make PROGRESS
4. Make recursive call
5. COMBINE returned answer

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LINEAR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

solve(i)
    ↓
solve(i + 1)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TREE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

left  = solve(root->left)
right = solve(root->right)

return combine(left, right)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BACKTRACKING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

choose
solve()
undo

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DFS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

process
mark visited
visit neighbors recursively

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DIVIDE & CONQUER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

divide
solve smaller problems
combine

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

recursive state
     ↓
repeated state?
     ↓
memoization
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

# 56. The Biggest Reality Check

You **will not become good at recursion by reading 50 explanations**.

At some point, your brain has to struggle with the call stack.

For every problem you solve, initially do this on paper:

```text
Function parameters
        ↓
Base case
        ↓
First recursive call
        ↓
What does it return?
        ↓
What happens after return?
```

Especially for the first **10–15 problems**, manually draw the recursion tree.

After that, you'll start recognizing patterns instead of trying to mentally execute every call.

And don't try to memorize 30 recursive codes. **Memorize 5 structures:**

```text
1. Linear recursion
2. Return-value recursion
3. Tree recursion
4. DFS
5. Backtracking
```

Most LeetCode recursion problems are variations of these.
