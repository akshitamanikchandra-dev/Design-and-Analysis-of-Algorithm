# Task Assignment — Branch and Bound

Solves the **N×N assignment problem** (assign N tasks to N servers at minimum total cost) using a branch-and-bound algorithm with pruning.

## How it works

The algorithm explores every possible task-to-server assignment as a decision tree. At each node it prunes entire subtrees whose partial cost already equals or exceeds the best solution found so far, making it significantly faster than brute-force enumeration for many inputs.

```
branchAndBound(task, currentCost)
  ├── if currentCost ≥ bestCost → prune (return early)
  ├── if task == N → update best solution
  └── for each unassigned server → recurse
```

## Build and run

**Requirements:** any C99-compatible compiler (gcc, clang, etc.)

```bash
# Compile
gcc -O2 -o task_assignment task_assignment_bb.c

# Run
./task_assignment
```

**Example session (3 tasks, 3 servers):**

```
Enter number of tasks/servers (N): 3
Enter the cost matrix (3 x 3).
Cost for Task 0 to Server 0: 9
Cost for Task 0 to Server 1: 2
Cost for Task 0 to Server 2: 7
Cost for Task 1 to Server 0: 3
Cost for Task 1 to Server 1: 6
Cost for Task 1 to Server 2: 4
Cost for Task 2 to Server 0: 1
Cost for Task 2 to Server 1: 8
Cost for Task 2 to Server 2: 5

==================================
Minimum Total Cost Found: 10
Optimal Assignment:
  Task 0 -> Server 1
  Task 1 -> Server 2
  Task 2 -> Server 0
==================================
```

## Complexity

| Case | Time complexity |
|------|----------------|
| Worst case (no pruning) | O(N!) |
| Average case (with pruning) | Much better in practice |

Maximum supported N is `MAX_SIZE = 20` (configurable via the `#define`).

## File structure

```
.
└── task_assignment_bb.c   # Full source — single file, no dependencies
```

## License

MIT — feel free to use and adapt.
