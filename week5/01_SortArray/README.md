# 1. Problem

The task is to sort an integer array in ascending order. The smallest number should appear first, and the largest number should appear last.

For example:

Input: `[5, 2, 3, 1]`

Output: `[1, 2, 3, 5]`

# 2. Approach

I used the Merge Sort algorithm. It divides the array into smaller parts, sorts them, and then combines them in ascending order.

First, I check whether the array is empty or contains only one element. If so, it is already sorted.

Next, I divide the array into two halves. I recursively divide each half until every part contains only one element. Finally, I merge the parts by comparing their elements and selecting the smaller value first.

## Example Trace

Consider the input array:

`[5, 2, 3, 1]`

**Step 1: Divide the array**

`[5, 2, 3, 1]`

The array is divided into:

`[5, 2]` and `[3, 1]`

**Step 2: Divide again**

`[5, 2]` becomes `[5]` and `[2]`.

`[3, 1]` becomes `[3]` and `[1]`.

**Step 3: Sort and merge the smaller parts**

Compare `5` and `2`. Since `2` is smaller, the result is:

`[2, 5]`

Compare `3` and `1`. Since `1` is smaller, the result is:

`[1, 3]`

**Step 4: Merge the two sorted halves**

Compare the first elements of `[2, 5]` and `[1, 3]`.

- Compare `2` and `1`: select `1`.
- Compare `2` and `3`: select `2`.
- Compare `5` and `3`: select `3`.
- Add the remaining element `5`.

The final result is:

`[1, 2, 3, 5]`

## Challenges and Testing

One challenge was understanding how recursion divides the array and when the merging process should begin.

I also needed to handle arrays containing zero or one element because they do not require sorting.

To test the solution, I would check an unsorted array, an already sorted array, an array with duplicate values, an array containing negative numbers, and an array with a single element. These cases help verify that the algorithm works for different inputs.

# 3. Time Complexity

**Time Complexity: O(n log n)**

At each level, the algorithm divides the array into smaller parts. The number of levels is approximately `log n`.

At each level, merging processes all `n` elements, requiring `O(n)` time.

Therefore, the total time complexity is:

`O(n) × O(log n) = O(n log n)`

**Space Complexity: O(n)**

The merging process requires an additional temporary array containing up to `n` elements. The recursive calls also require a stack of depth `O(log n)`.

The temporary array dominates the additional space requirement, so the overall auxiliary space complexity is `O(n)`.

# 4. Reflection / Improvement

A more efficient approach is not generally necessary for this comparison-based sorting task because Merge Sort already provides `O(n log n)` time complexity in the worst case.

An alternative is Heap Sort, which also provides `O(n log n)` time complexity but can use `O(1)` auxiliary space in an in-place implementation.

Merge Sort is a good choice because its running time is predictable and its divide-and-conquer approach is relatively easy to analyze.
