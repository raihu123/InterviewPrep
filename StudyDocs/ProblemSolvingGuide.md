# 1. Prefix Sum

![Prefix Sum](https://blog.algomaster.io)

Prefix Sum involves preprocessing an array to create a new array where each element at index `i` represents the sum of the array from the start up to `i`. This allows for efficient sum queries on subarrays.

Use this pattern when you need to perform multiple sum queries on a subarray or need to calculate cumulative sums.

### Sample Problem:
Given an array `nums`, answer multiple queries about the sum of elements within a specific range `[i, j]`.

**Example**:
- Input: `nums = [1, 2, 3, 4, 5, 6], i = 1, j = 3`
- Output: `9`

**Explanation**:
1. Preprocess the array `A` to create a prefix sum array: `P = [1, 3, 6, 10, 15, 21]`.
2. To find the sum between indices `i` and `j`, use the formula: `P[j] - P[i-1]`.

### LeetCode Problems:
1. [Range Sum Query - Immutable (LeetCode #303)](https://leetcode.com/problems/range-sum-query-immutable)
2. [Contiguous Array (LeetCode #525)](https://leetcode.com/problems/contiguous-array)
3. [Subarray Sum Equals K (LeetCode #560)](https://leetcode.com/problems/subarray-sum-equals-k)

---

# 2. Two Pointers

The Two Pointers pattern involves using two pointers to iterate through an array or list, often used to find pairs or elements that meet specific criteria.

Use this pattern when dealing with sorted arrays or lists where you need to find pairs that satisfy a specific condition.

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

### LeetCode Problems:
1. [Two Sum II - Input Array is Sorted (LeetCode #167)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)
2. [3Sum (LeetCode #15)](https://leetcode.com/problems/3sum)
3. [Container With Most Water (LeetCode #11)](https://leetcode.com/problems/container-with-most-water)

---

# 3. Sliding Window

The Sliding Window pattern is used to find a subarray or substring that satisfies a specific condition, optimizing the time complexity by maintaining a window of elements.

Use this pattern when dealing with problems involving contiguous subarrays or substrings.

### Sample Problem:
Find the maximum sum of a subarray of size `k`.

**Example**:
- Input: `nums = [2, 1, 5, 1, 3, 2], k = 3`
- Output: `9`

**Explanation**:
1. Start with the sum of the first `k` elements.
2. Slide the window one element at a time, subtracting the element that goes out of the window and adding the new element.
3. Keep track of the maximum sum encountered.

### LeetCode Problems:
1. [Maximum Average Subarray I (LeetCode #643)](https://leetcode.com/problems/maximum-average-subarray-i)
2. [Longest Substring Without Repeating Characters (LeetCode #3)](https://leetcode.com/problems/longest-substring-without-repeating-characters)
3. [Minimum Window Substring (LeetCode #76)](https://leetcode.com/problems/minimum-window-substring)

---

# 4. Fast & Slow Pointers

The Fast & Slow Pointers (Tortoise and Hare) pattern is used to detect cycles in linked lists and other similar structures.

### Sample Problem:
Detect if a linked list has a cycle.

**Explanation**:
1. Initialize two pointers, one moving one step at a time (slow) and the other moving two steps at a time (fast).
2. If there is a cycle, the fast pointer will eventually meet the slow pointer.
3. If the fast pointer reaches the end of the list, there is no cycle.

### LeetCode Problems:
1. [Linked List Cycle (LeetCode #141)](https://leetcode.com/problems/linked-list-cycle)
2. [Happy Number (LeetCode #202)](https://leetcode.com/problems/happy-number)
3. [Find the Duplicate Number (LeetCode #287)](https://leetcode.com/problems/find-the-duplicate-number)

---

# 5. LinkedList In-place Reversal

The In-place Reversal of a LinkedList pattern reverses parts of a linked list without using extra space.

Use this pattern when you need to reverse sections of a linked list.

### Sample Problem:
Reverse a sublist of a linked list from position `m` to `n`.

**Example**:
- Input: `head = [1, 2, 3, 4, 5], m = 2, n = 4`
- Output: `[1, 4, 3, 2, 5]`

**Explanation**:
1. Identify the start and end of the sublist.
2. Reverse the nodes in place by adjusting the pointers.

### LeetCode Problems:
1. [Reverse Linked List (LeetCode #206)](https://leetcode.com/problems/reverse-linked-list)
2. [Reverse Linked List II (LeetCode #92)](https://leetcode.com/problems/reverse-linked-list-ii)
3. [Swap Nodes in Pairs (LeetCode #24)](https://leetcode.com/problems/swap-nodes-in-pairs)
...
