# 1. Problem

The task is to sort a singly linked list in ascending order.

A linked list consists of nodes. Each node stores a value and a reference to the next node. Unlike an array, a linked list does not provide direct access to elements by index.

For example:

Input: `4 -> 2 -> 1 -> 3`

Output: `1 -> 2 -> 3 -> 4`

# 2. Approach

I used the Merge Sort algorithm to sort the linked list.

First, I check whether the list is empty or contains only one node. If so, the list is already sorted.

Next, I use two pointers, called `slow` and `fast`, to find the middle of the list. The `slow` pointer moves one node at a time, while the `fast` pointer moves two nodes at a time.

When the fast pointer reaches the end, the slow pointer is approximately in the middle. I split the list into two separate lists and recursively sort both halves.

Finally, I merge the two sorted lists by comparing their node values.

## Example Trace

Consider this input:

`4 -> 2 -> 1 -> 3`

**Step 1: Find the middle**

The slow and fast pointers move through the list.

The list is divided into two parts:

Left: `4 -> 2`

Right: `1 -> 3`

**Step 2: Divide the left part**

`4 -> 2` becomes:

`4` and `2`

Each list contains one node, so both are already sorted.

Merge them:

`2 -> 4`

**Step 3: Divide the right part**

`1 -> 3` becomes:

`1` and `3`

Merge them:

`1 -> 3`

**Step 4: Merge the two sorted lists**

Now we have:

Left: `2 -> 4`

Right: `1 -> 3`

Compare their values:

- Compare `2` and `1`: select `1`.
- Compare `2` and `3`: select `2`.
- Compare `4` and `3`: select `3`.
- Add the remaining node `4`.

The final sorted list is:

`1 -> 2 -> 3 -> 4`

## Challenges and Testing

One challenge was finding the middle of the linked list without using array indexes. I used the slow and fast pointer technique to solve this problem.

Another important detail was splitting the list correctly. Setting `prev.next = null` separates the two halves and prevents the recursive calls from processing the same list repeatedly.

I would test the solution with an empty list, a single-node list, an already sorted list, a list sorted in descending order, duplicate values, and negative values.

These tests help check the correctness of the splitting and merging operations.

# 3. Time Complexity

**Time Complexity: O(n log n)**

Each recursive step divides the linked list into two approximately equal parts.

This creates approximately `log n` levels of recursion.

At each level, merging processes all `n` nodes in total, requiring `O(n)` time.

Therefore:

`O(n) × O(log n) = O(n log n)`

**Space Complexity: O(log n)**

The algorithm rearranges existing nodes instead of creating a new array containing all list elements.

However, recursive calls require additional stack space. Since the list is divided into halves at each step, the recursion depth is `O(log n)`.

Therefore, the auxiliary space complexity is `O(log n)`, excluding the input list itself.

# 4. Reflection / Improvement

Merge Sort is already an efficient approach for sorting a linked list, with `O(n log n)` time complexity.

One possible improvement is to implement an iterative bottom-up Merge Sort. Instead of using recursive calls, it merges increasingly larger parts of the list.

This approach can achieve `O(n log n)` time complexity while avoiding the recursive call stack, reducing auxiliary space to `O(1)` when implemented with constant extra storage.
