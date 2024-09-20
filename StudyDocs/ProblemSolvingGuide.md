## Prefix Sum

Prefix Sum involves preprocessing an array to create a new array where each element at index `i` represents the sum of the array from the start up to `i`. This allows for efficient sum queries on subarrays.

Use this pattern when you need to perform multiple sum queries on a subarray or need to calculate cumulative sums.

**Clues:**

You're asked to find sums over different ranges in an array (e.g., subarrays, subranges).
Frequent updates to an array, where recalculating sums would be inefficient.
Questions related to cumulative sums, or checking if a subarray with a specific sum exists.
Common problems: Range sum queries, subarray sum equal to target.

### Sample Problem:
Given an array `nums`, answer multiple queries about the sum of elements within a specific range `[i, j]`.

**Example**:
- Input: `nums = [1, 2, 3, 4, 5, 6], i = 1, j = 3`
- Output: `9`

**Explanation**:
1. Preprocess the array `A` to create a prefix sum array: `P = [1, 3, 6, 10, 15, 21]`.
2. To find the sum between indices `i` and `j`, use the formula: `P[j] - P[i-1]`.

### Formula:
- Preprocess the array to create a prefix sum array, then use:  
  **Sum from `i` to `j`** = `P[j] - P[i-1]`

### Java Code:
```java
class PrefixSum {
    private int[] prefix;

    public PrefixSum(int[] nums) {
        prefix = new int[nums.length];
        prefix[0] = nums[0];
        for (int i = 1; i < nums.length; i++) {
            prefix[i] = prefix[i - 1] + nums[i];
        }
    }

    public int rangeSum(int i, int j) {
        if (i == 0) {
            return prefix[j];
        }
        return prefix[j] - prefix[i - 1];
    }
}
```

### LeetCode Problems:
1. [Range Sum Query - Immutable (LeetCode #303)](https://leetcode.com/problems/range-sum-query-immutable)
2. [Contiguous Array (LeetCode #525)](https://leetcode.com/problems/contiguous-array)
3. [Subarray Sum Equals K (LeetCode #560)](https://leetcode.com/problems/subarray-sum-equals-k)

---

## Two Pointers

The Two Pointers pattern involves using two pointers to iterate through an array or list, often used to find pairs or elements that meet specific criteria.

Use this pattern when dealing with sorted arrays or lists where you need to find pairs that satisfy a specific condition.

**Clues**:
   - You need to process pairs in a sorted array or linked list.
   - The question involves searching for pairs that satisfy a certain condition (e.g., sum equals target).
   - You're trying to reduce a brute-force \(O(n^2)\) solution to \(O(n)\).
   
   **Common problems**: Pair with a target sum, finding triplets, comparing two arrays, palindromes.


### Sample Problem:
Find two numbers in a sorted array that add up to a target value.

**Example**:
- Input: `nums = [1, 2, 3, 4, 6], target = 6`
- Output: `[1, 3]`

**Explanation**:
1. Initialize two pointers, one at the start (`left`) and one at the end (`right`) of the array.
2. Check the sum of the elements at the two pointers.
3. If the sum equals the target, return the indices.
4. If the sum is less than the target, move the left pointer to the right.
5. If the sum is greater than the target, move the right pointer to the left.


### Formula:
- Use two pointers to find two numbers that add up to a target. Adjust pointers based on the sum.

### Java Code:
```java
class TwoPointers {
    public int[] findTwoSum(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int sum = nums[left] + nums[right];
            if (sum == target) {
                return new int[]{left, right}; 
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
        return new int[]{-1, -1}; 
    }
}
```

### LeetCode Problems:
1. [Two Sum II - Input Array is Sorted (LeetCode #167)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)
2. [3Sum (LeetCode #15)](https://leetcode.com/problems/3sum)
3. [Container With Most Water (LeetCode #11)](https://leetcode.com/problems/container-with-most-water)

---

## Sliding Window

The Sliding Window pattern is used to find a subarray or substring that satisfies a specific condition, optimizing the time complexity by maintaining a window of elements.

Use this pattern when dealing with problems involving contiguous subarrays or substrings.

**Clues**:
   - You're asked to find a subarray or substring that satisfies a specific condition (e.g., maximum sum, longest length).
   - The problem asks for an optimal or sub-optimal solution.
   - The problem involves continuous subarrays of dynamic lengths.

   **Common problems**: Longest substring without repeating characters, maximum sum subarray of fixed length, smallest subarray with a given sum.

### Sample Problem:
Find the maximum sum of a subarray of size `k`.

**Example**:
- Input: `nums = [2, 1, 5, 1, 3, 2], k = 3`
- Output: `9`

**Explanation**:
1. Start with the sum of the first `k` elements.
2. Slide the window one element at a time, subtracting the element that goes out of the window and adding the new element.
3. Keep track of the maximum sum encountered.


### Formula:
- Maintain a window of `k` elements and update the sum by sliding the window.

### Java Code:
```java
class SlidingWindow {
    public int maxSumSubarray(int[] nums, int k) {
        int maxSum = 0, windowSum = 0;

        for (int i = 0; i < k; i++) {
            windowSum += nums[i];
        }

        maxSum = windowSum;

        for (int i = k; i < nums.length; i++) {
            windowSum += nums[i] - nums[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }

        return maxSum;
    }
}
```

### LeetCode Problems:
1. [Maximum Average Subarray I (LeetCode #643)](https://leetcode.com/problems/maximum-average-subarray-i)
2. [Longest Substring Without Repeating Characters (LeetCode #3)](https://leetcode.com/problems/longest-substring-without-repeating-characters)
3. [Minimum Window Substring (LeetCode #76)](https://leetcode.com/problems/minimum-window-substring)

---

## Fast & Slow Pointers

The Fast & Slow Pointers (Tortoise and Hare) pattern is used to detect cycles in linked lists and other similar structures.

**Clues**:
   - You're working with a linked list or array and need to detect cycles or midpoints.
   - Problems that involve repeated elements or cyclic behavior.
   - You need to find circular patterns or determine the length of cycles.

   **Common problems**: Linked list cycle detection, finding the middle of a linked list, rearranging linked lists.

### Sample Problem:
Detect if a linked list has a cycle.

**Explanation**:
1. Initialize two pointers, one moving one step at a time (slow) and the other moving two steps at a time (fast).
2. If there is a cycle, the fast pointer will eventually meet the slow pointer.
3. If the fast pointer reaches the end of the list, there is no cycle.


### Formula:
- Use two pointers (fast and slow) to detect cycles in linked lists.

### Java Code:
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; next = null; }
}

class FastSlowPointers {
    public boolean hasCycle(ListNode head) {
        if (head == null) return false;
        
        ListNode slow = head, fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            
            if (slow == fast) {
                return true;
            }
        }
        
        return false;
    }
}
```

### LeetCode Problems:
1. [Linked List Cycle (LeetCode #141)](https://leetcode.com/problems/linked-list-cycle)
2. [Happy Number (LeetCode #202)](https://leetcode.com/problems/happy-number)
3. [Find the Duplicate Number (LeetCode #287)](https://leetcode.com/problems/find-the-duplicate-number)

---

## LinkedList In-place Reversal

The In-place Reversal of a LinkedList pattern reverses parts of a linked list without using extra space.

Use this pattern when you need to reverse sections of a linked list.

**Clues**:
   - The problem asks for in-place modifications on a linked list (without using extra memory).
   - The task involves reversing a section of the linked list.
   - The problem involves processing nodes in a reversed order.

   **Common problems**: Reversing a linked list, reversing sub-lists, rearranging nodes.

### Sample Problem:
Reverse a sublist of a linked list from position `m` to `n`.

**Example**:
- Input: `head = [1, 2, 3, 4, 5], m = 2, n = 4`
- Output: `[1, 4, 3, 2, 5]`

**Explanation**:
1. Identify the start and end of the sublist.
2. Reverse the nodes in place by adjusting the pointers.


### Formula:
- Reverse the linked list or a part of it by adjusting the pointers.

### Java Code:
```java
class LinkedListReversal {
    public ListNode reverseBetween(ListNode head, int m, int n) {
        if (head == null) return null;

        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;

        for (int i = 0; i < m - 1; i++) {
            pre = pre.next;
        }

        ListNode start = pre.next;
        ListNode then = start.next;

        for (int i = 0; i < n - m; i++) {
            start.next = then.next;
            then.next = pre.next;
            pre.next = then;
            then = start.next;
        }

        return dummy.next;
    }
}
```

### LeetCode Problems:
1. [Reverse Linked List (LeetCode #206)](https://leetcode.com/problems/reverse-linked-list)
2. [Reverse Linked List II (LeetCode #92)](https://leetcode.com/problems/reverse-linked-list-ii)
3. [Swap Nodes in Pairs (LeetCode #24)](https://leetcode.com/problems/swap-nodes-in-pairs)
...

## Monotonic Stack

The Monotonic Stack pattern uses a stack to maintain a sequence of elements in a specific order (increasing or decreasing).

Use this pattern for problems that require finding the next greater or smaller element.

**Clues**:
   - The problem involves finding the next greater/smaller element in an array.
   - You're asked to maintain some order while processing elements.
   - Problems involving intervals, temperature, stock prices where you need to maintain a decreasing or increasing sequence.

   **Common problems**: Next greater element, stock span problems, trapping rainwater.

### Sample Problem:
Find the next greater element for each element in an array. Output -1 if the greater element doesn’t exist.

**Example:**

- **Input:** nums = [2, 1, 2, 4, 3]  
- **Output:** [4, 2, 4, -1, -1]

**Explanation:**
- Use a stack to keep track of elements for which we haven't found the next greater element yet.
- Iterate through the array, and for each element, pop elements from the stack until you find a greater element.
- If the stack is not empty, set the result for index at the top of the stack to the current element.
- Push the current element onto the stack.

### LeetCode Problems:
- [Next Greater Element I (LeetCode #496)](https://leetcode.com/problems/next-greater-element-i)
- [Daily Temperatures (LeetCode #739)](https://leetcode.com/problems/daily-temperatures)
- [Largest Rectangle in Histogram (LeetCode #84)](https://leetcode.com/problems/largest-rectangle-in-histogram)

---

## Top ‘K’ Elements

The Top 'K' Elements pattern finds the top k largest or smallest elements in an array or stream of data using heaps or sorting.

**Clues**:
   - The problem asks for the top 'K' largest/smallest/frequent elements.
   - You're trying to optimize solutions that involve repeated comparisons.
   - Problems where sorting would be inefficient and can be replaced by using a heap.

   **Common problems**: Kth largest element in a stream, finding the most frequent elements, top K numbers.

### Sample Problem:
Find the k-th largest element in an unsorted array.

**Example:**

- **Input:** nums = [3, 2, 1, 5, 6, 4], k = 2  
- **Output:** 5

**Explanation:**
- Use a min-heap of size `k` to keep track of the `k` largest elements.
- Iterate through the array, adding elements to the heap.
- If the heap size exceeds `k`, remove the smallest element from the heap.
- The root of the heap will be the `k`-th largest element.


### Formula:
- Use a min-heap to maintain the top `k` largest elements efficiently.

### Java Code:
```java
import java.util.*;

class TopKElements {
    public int[] findTopKElements(int[] nums, int k) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        
        for (int i = 0; i < k; i++) {
            minHeap.add(nums[i]);
        }
        
        for (int i = k; i < nums.length; i++) {
            if (nums[i] > minHeap.peek()) {
                minHeap.poll();
                minHeap.add(nums[i]);
            }
        }
        
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = minHeap.poll();
        }
        
        return result;
    }
}
```


### LeetCode Problems:
- [Kth Largest Element in an Array (LeetCode #215)](https://leetcode.com/problems/kth-largest-element-in-an-array)
- [Top K Frequent Elements (LeetCode #347)](https://leetcode.com/problems/top-k-frequent-elements)
- [Find K Pairs with Smallest Sums (LeetCode #373)](https://leetcode.com/problems/find-k-pairs-with-smallest-sums)

---

## Overlapping Intervals

The Overlapping Intervals pattern is used to merge or handle overlapping intervals in an array.

In an interval array sorted by start time, two intervals `[a, b]` and `[c, d]` overlap if `b >= c` (i.e., the end time of the first interval is greater than or equal to the start time of the second interval).

**Clues**:
   - The problem involves intervals (e.g., time slots, ranges) and asks about merging, intersecting, or counting.
   - Tasks related to schedules, meeting rooms, or ranges where events overlap.
   - The problem mentions intervals or ranges of values.

   **Common problems**: Merging intervals, checking for overlapping meetings, interval intersections.

### Sample Problem:
Problem Statement: Merge all overlapping intervals.

**Example:**

- **Input:** intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]  
- **Output:** [[1, 6], [8, 10], [15, 18]]

**Explanation:**
- Sort the intervals by their start time.
- Create an empty list called `merged` to store the merged intervals.
- Iterate through the intervals and check if it overlaps with the last interval in the merged list.
- If it overlaps, merge the intervals by updating the end time of the last interval in `merged`.
- If it does not overlap, simply add the current interval to the `merged` list.


### Formula:
- Sort intervals by their start time and **merge overlapping** ones.

### Java Code:
```java
import java.util.*;

class MergeIntervals {
    public int[][] merge(int[][] intervals) {
        if (intervals.length == 0) return new int[0][];
        
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        
        List<int[]> result = new ArrayList<>();
        int[] currentInterval = intervals[0];
        result.add(currentInterval);
        
        for (int[] interval : intervals) {
            int currentEnd = currentInterval[1];
            int nextStart = interval[0];
            int nextEnd = interval[1];
            
            if (currentEnd >= nextStart) {
                currentInterval[1] = Math.max(currentEnd, nextEnd);
            } else {
                currentInterval = interval;
                result.add(currentInterval);
            }
        }
        
        return result.toArray(new int[result.size()][]);
    }
}
```


### LeetCode Problems:
- [Merge Intervals (LeetCode #56)](https://leetcode.com/problems/merge-intervals)
- [Insert Interval (LeetCode #57)](https://leetcode.com/problems/insert-interval)
- [Non-Overlapping Intervals (LeetCode #435)](https://leetcode.com/problems/non-overlapping-intervals)

---

## Modified Binary Search

The Modified Binary Search pattern adapts binary search to solve a wider range of problems, such as finding elements in rotated sorted arrays.

Use this pattern for problems involving sorted or rotated arrays where you need to find a specific element.

**Clues**:
   - The problem asks to search for an element in a sorted or rotated array.
   - You need to find a minimum/maximum, or perform an efficient search in log(n) time.
   - The array is sorted but modified in some way (e.g., rotation, peaks and valleys).
   
   **Common problems**: Searching in rotated sorted arrays, finding the peak element, binary search variations.

### Sample Problem:
Find an element in a rotated sorted array.

**Example:**

- **Input:** nums = [4, 5, 6, 7, 0, 1, 2], target = 0  
- **Output:** 4

**Explanation:**
- Perform binary search with an additional check to determine which half of the array is sorted.
- We then check if the target is within the range of the sorted half.
- If it is, we search that half; otherwise, we search the other half.

### LeetCode Problems:
- [Search in Rotated Sorted Array (LeetCode #33)](https://leetcode.com/problems/search-in-rotated-sorted-array)
- [Find Minimum in Rotated Sorted Array (LeetCode #153)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array)
- [Search a 2D Matrix II (LeetCode #240)](https://leetcode.com/problems/search-a-2d-matrix-ii)


## Binary Tree Traversal

Binary Tree Traversal involves visiting all the nodes in a binary tree in a specific order.

- **PreOrder**: root -> left -> right
- **InOrder**: left -> root -> right
- **PostOrder**: left -> right -> root

 **Clues**:
   - The problem involves a binary tree and asks for node traversal in a specific order (preorder, inorder, postorder).
   - You need to visit all the nodes of a tree systematically.
   - You're asked to perform operations on a binary tree (e.g., find height, level order traversal).
   
   **Common problems**: Binary tree traversal, finding depth/height, printing nodes by levels.

### Sample Problem:
Perform inorder traversal of a binary tree.

**Example:**

- **Input:** root = [1, null, 2, 3]  
- **Output:** [1, 3, 2]

**Explanation:**
- Inorder traversal visits nodes in the order: left, root, right.
- Use recursion or a stack to traverse the tree in this order.

### LeetCode Problems:
- [PreOrder → Binary Tree Paths (LeetCode #257)](https://leetcode.com/problems/binary-tree-paths)
- [InOrder → Kth Smallest Element in a BST (LeetCode #230)](https://leetcode.com/problems/kth-smallest-element-in-a-bst)
- [PostOrder → Binary Tree Maximum Path Sum (LeetCode #124)](https://leetcode.com/problems/binary-tree-maximum-path-sum)

---

## Depth-First Search (DFS)

Depth-First Search (DFS) is a traversal technique that explores as far down a branch as possible before backtracking.

Use this pattern for exploring all paths or branches in graphs or trees.

**Clues**:
   - You're asked to explore all possible paths or solutions (e.g., in a graph or tree).
   - The problem involves traversing deep into structures like trees, graphs, or matrices.
   - You're tasked with visiting all nodes but not necessarily in level order.
   
   **Common problems**: Finding connected components, traversing graphs, recursive tree traversal, pathfinding in mazes.

### Sample Problem:
Find all paths from the root to leaves in a binary tree.

**Example:**

- **Input:** root = [1, 2, 3, null, 5]  
- **Output:** ["1->2->5", "1->3"]

**Explanation:**
- Use recursion or a stack to traverse each path from the root to the leaves.
- Record each path as you traverse.

### LeetCode Problems:
- [Clone Graph (LeetCode #133)](https://leetcode.com/problems/clone-graph)
- [Path Sum II (LeetCode #113)](https://leetcode.com/problems/path-sum-ii)
- [Course Schedule II (LeetCode #210)](https://leetcode.com/problems/course-schedule-ii)

---

## Breadth-First Search (BFS)

Breadth-First Search (BFS) is a traversal technique that explores nodes level by level in a tree or graph.

Use this pattern for finding the shortest paths in unweighted graphs or level-order traversal in trees.

**Clues**:
   - You're asked to find the shortest path or solution.
   - The problem involves level-by-level processing (e.g., shortest path in an unweighted graph).
   - Questions where you need to explore all neighbors before moving deeper.
   
   **Common problems**: Shortest path in an unweighted graph, level-order traversal of a tree, flood fill algorithms.

### Sample Problem:
Perform level-order traversal of a binary tree.

**Example:**

- **Input:** root = [3, 9, 20, null, null, 15, 7]  
- **Output:** [[3], [9, 20], [15, 7]]

**Explanation:**
- Use a queue to keep track of nodes at each level.
- Traverse each level and add the children of the current nodes to the queue.

### LeetCode Problems:
- [Binary Tree Level Order Traversal (LeetCode #102)](https://leetcode.com/problems/binary-tree-level-order-traversal)
- [Rotting Oranges (LeetCode #994)](https://leetcode.com/problems/rotting-oranges)
- [Word Ladder (LeetCode #127)](https://leetcode.com/problems/word-ladder)

---

## Matrix Traversal

Matrix Traversal involves traversing elements in a matrix using different techniques (DFS, BFS, etc.).

Use this pattern for problems involving traversing 2D grids or matrices horizontally, vertically, or diagonally.

**Clues**:
   - The problem gives you a grid or matrix and asks to traverse it in a specific manner (row by row, column by column, or diagonally).
   - You're asked to find a path, region, or pattern in a matrix/grid.
   
   **Common problems**: Searching for a path in a grid (e.g., islands, number of regions), matrix diagonals, pathfinding in 2D arrays.

### Sample Problem:
Perform flood fill on a 2D grid. Change all the cells connected to the starting cell to a new color.

**Example:**

- **Input:** image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2  
- **Output:** [[2,2,2],[2,2,0],[2,0,1]]

**Explanation:**
- Use DFS or BFS to traverse the matrix starting from the given cell.
- Change the color of the connected cells to the new color.

### LeetCode Problems:
- [Flood Fill (LeetCode #733)](https://leetcode.com/problems/flood-fill)
- [Number of Islands (LeetCode #200)](https://leetcode.com/problems/number-of-islands)
- [Surrounded Regions (LeetCode #130)](https://leetcode.com/problems/surrounded-regions)

---

## Backtracking

Backtracking explores all possible solutions and backtracks when a solution path fails.

Use this pattern when you need to find all (or some) solutions to a problem that satisfies given constraints. For example: combinatorial problems, such as generating permutations, combinations, or subsets.

**Clues**:
   - The problem asks for all possible combinations, permutations, or subsets.
   - You need to find solutions for a decision-making problem (e.g., placing queens, generating subsets, or solving mazes).
   - You're looking for an optimal solution but also need to explore many possibilities.

   **Common problems**: N-Queens problem, Sudoku solver, generating subsets/permutations, solving a maze.

### Sample Problem:
Generate all permutations of a given list of numbers.

**Example:**

- **Input:** nums = [1, 2, 3]  
- **Output:** [[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]]

**Explanation:**
- Use recursion to generate permutations.
- For each element, include it in the current permutation and recursively generate the remaining permutations.
- Backtrack when all permutations for a given path are generated.

### Formula:
- Explore all possible solutions by building them incrementally and backtracking.

### Java Code:
```java
import java.util.*;

class Backtracking {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, int index, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));
        
        for (int i = index; i < nums.length; i++) {
            current.add(nums[i]);
            backtrack(nums, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }
}
```

### LeetCode Problems:
- [Permutations (LeetCode #46)](https://leetcode.com/problems/permutations)
- [Subsets (LeetCode #78)](https://leetcode.com/problems/subsets)
- [N-Queens (LeetCode #51)](https://leetcode.com/problems/n-queens)

---

## Dynamic Programming Patterns

Dynamic Programming (DP) involves breaking down problems into smaller subproblems and solving them using a bottom-up or top-down approach.

Use this pattern for problems with overlapping subproblems and optimal substructure.

DP itself has multiple sub-patterns. Some of the most important ones are:
- Fibonacci Numbers
- 0/1 Knapsack
- Longest Common Subsequence (LCS)
- Longest Increasing Subsequence (LIS)
- Subset Sum
- Matrix Chain Multiplication

**Clues**:
   - The problem involves optimization (e.g., maximizing/minimizing a value).
   - The question asks for solutions to problems involving overlapping subproblems or optimal substructure.
   - You need to solve the problem in a bottom-up or top-down manner (usually with memoization or tabulation).
   
   **Common problems**: Fibonacci sequence, knapsack problem, longest common subsequence, matrix chain multiplication, optimal game strategies.

### Sample Problem:
Calculate the n-th Fibonacci number.

**Example:**

- **Input:** n = 5  
- **Output:** 5 (The first five Fibonacci numbers are 0, 1, 1, 2, 3, 5)

**Explanation:**
- Use a bottom-up approach to calculate the n-th Fibonacci number.
- Start with the first two numbers (0 and 1) and iterate to calculate the next numbers like (dp[i] = dp[i - 1] + dp[i - 2]).


### Formula:
- Break problems into subproblems, store results to avoid recomputation.

### Java Code:
```java
class DynamicProgramming {
    public int fib(int n) {
        if (n <= 1) return n;
        
        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n];
    }
}
```

### LeetCode Problems:
- [Climbing Stairs (LeetCode #70)](https://leetcode.com/problems/climbing-stairs)
- [House Robber (LeetCode #198)](https://leetcode.com/problems/house-robber)
- [Coin Change (LeetCode #322)](https://leetcode.com/problems/coin-change)
- [Longest Common Subsequence (LCS) (LeetCode #1143)](https://leetcode.com/problems/longest-common-subsequence)
- [Longest Increasing Subsequence (LIS) (LeetCode #322)](https://leetcode.com/problems/longest-increasing-subsequence)
- [Partition Equal Subset Sum (LeetCode #416)](https://leetcode.com/problems/partition-equal-subset-sum)



## Some Other types


##  **Cyclic Sort**

### Formula:
- Place each element in its correct position (1 to n) using index swaps.

### Java Code:
```java
class CyclicSort {
    public void cyclicSort(int[] nums) {
        int i = 0;
        while (i < nums.length) {
            int correctIndex = nums[i] - 1;
            if (nums[i] != nums[correctIndex]) {
                swap(nums, i, correctIndex);
            } else {
                i++;
            }
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

---

## **Binary Search**

### Formula:
- Search for a target value in a sorted array by dividing the search space in half.

### Java Code:
```java
class BinarySearch {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        
        return -1;
    }
}
```

---

## 12. **Greedy Algorithm**

### Formula:
- Make the most optimal choice at each step to solve optimization problems.

### Java Code:
```java
import java.util.*;

class GreedyAlgorithm {
    public int findMinMeetingRooms(int[][] intervals) {
        if (intervals == null || intervals.length == 0) return 0;

        int[] startTimes = new int[intervals.length];
        int[] endTimes = new int[intervals.length];
        for (int i = 0; i < intervals.length; i++) {
            startTimes[i] = intervals[i][0];
            endTimes

[i] = intervals[i][1];
        }
        Arrays.sort(startTimes);
        Arrays.sort(endTimes);

        int startPointer = 0, endPointer = 0, rooms = 0, maxRooms = 0;

        while (startPointer < intervals.length) {
            if (startTimes[startPointer] < endTimes[endPointer]) {
                rooms++;
                startPointer++;
            } else {
                rooms--;
                endPointer++;
            }
            maxRooms = Math.max(maxRooms, rooms);
        }

        return maxRooms;
    }
}
```