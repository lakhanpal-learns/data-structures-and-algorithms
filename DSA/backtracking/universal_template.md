backtrack(...)
{
    if (answer is complete)
    {
        save answer;
        return;
    }

    for (every possible choice)
    {
        choose

        backtrack(next state)

        undo choice
    }
}

1. Base case

2. Loop over choices

3. Choose

4. Undo


# example 
A
B

Start
│
├── Choose A
│      │
│      ├── Choose A
│      └── Choose B
│
└── Choose B
       │
       ├── Choose A
       └── Choose B


# How do you recognize a backtracking problem?

Usually the problem asks for:

All combinations
All permutations
All subsets
Every possible path
Generate all valid strings
N-Queens
Sudoku solver
Word Search

The keywords "all possible" or "generate every..." are strong hints that backtracking may be appropriate.

