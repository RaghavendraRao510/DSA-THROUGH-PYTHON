# 🚀 100 Days of Coding Challenge

## 📅 Day 5: Top K Frequent Elements

### 🧩 Problem

Given an integer array `nums` and an integer `k`, return the **`k` most frequent elements**.

The answer can be returned in **any order**.

---

## 📌 Examples

### Example 1

```text
Input:  nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

Frequency of each number:

```text
1 → 3 times
2 → 2 times
3 → 1 time
```

The 2 most frequent elements are:

```text
[1, 2]
```

### Example 2

```text
Input:  nums = [1], k = 1
Output: [1]
```

### Example 3

```text
Input:  nums = [1,2,1,2,1,2,3,1,3,2], k = 2
Output: [1,2]
```

Frequency:

```text
1 → 4 times
2 → 4 times
3 → 2 times
```

Therefore:

```text
[1, 2]
```

---

# 💡 Approach

We can solve this problem in **two steps**:

### Step 1: Count the frequency

Use a dictionary:

```text
number → frequency
```

For:

```text
nums = [1,1,1,2,2,3]
```

we get:

```text
{
    1: 3,
    2: 2,
    3: 1
}
```

### Step 2: Sort by frequency

Sort the dictionary items from **highest frequency to lowest frequency**.

Then take the first `k` elements.

---

# 💻 Python Solution

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:

        freq = {}

        for num in nums:
            freq[num] = freq.get(num, 0) + 1

        sorted_items = sorted(
            freq.items(),
            key=lambda x: x[1],
            reverse=True
        )

        return [num for num, freq in sorted_items[:k]]
```

---

# 🔍 Code Explanation

## 1. Create a dictionary

```python
freq = {}
```

This dictionary stores:

```text
number → how many times it appears
```

---

## 2. Count every number

```python
for num in nums:
    freq[num] = freq.get(num, 0) + 1
```

Suppose:

```text
nums = [1,1,1,2,2,3]
```

Initially:

```text
freq = {}
```

First `1`:

```text
freq = {1: 1}
```

Second `1`:

```text
freq = {1: 2}
```

Third `1`:

```text
freq = {1: 3}
```

Then `2`:

```text
freq = {1: 3, 2: 1}
```

Next `2`:

```text
freq = {1: 3, 2: 2}
```

Finally `3`:

```text
freq = {1: 3, 2: 2, 3: 1}
```

---

# 🧠 What Does `.get()` Do?

This line:

```python
freq.get(num, 0)
```

means:

> "If `num` exists in the dictionary, give me its value. Otherwise, give me `0`."

For example:

```python
freq = {1: 3}
```

Then:

```python
freq.get(1, 0)
```

returns:

```text
3
```

But:

```python
freq.get(5, 0)
```

returns:

```text
0
```

Therefore:

```python
freq[num] = freq.get(num, 0) + 1
```

simply means:

> Increase the frequency of `num` by 1.

---

# 🔄 Step 2: Sort by Frequency

```python
sorted_items = sorted(
    freq.items(),
    key=lambda x: x[1],
    reverse=True
)
```

This is the most important part after counting.

### `freq.items()`

If:

```text
freq = {
    1: 3,
    2: 2,
    3: 1
}
```

then:

```python
freq.items()
```

gives pairs like:

```text
(1, 3)
(2, 2)
(3, 1)
```

Each pair is:

```text
(number, frequency)
```

---

## 🔑 Understanding `lambda x: x[1]`

Each item looks like:

```text
(number, frequency)
```

For example:

```text
(1, 3)
```

Here:

```text
x[0] = 1
x[1] = 3
```

We want to sort using the **frequency**, so we use:

```python
key=lambda x: x[1]
```

This tells Python:

> Sort using the second value of each pair.

---

## 🔽 What Does `reverse=True` Do?

Normally, sorting goes from smallest to largest:

```text
1, 2, 3
```

But we want the **highest frequency first**.

So:

```python
reverse=True
```

gives:

```text
3, 2, 1
```

Therefore:

```text
(1,3)
(2,2)
(3,1)
```

---

# ✂️ Step 3: Take the First `k`

```python
sorted_items[:k]
```

If:

```text
k = 2
```

and:

```text
sorted_items = [(1,3), (2,2), (3,1)]
```

then:

```text
sorted_items[:2]
```

gives:

```text
[(1,3), (2,2)]
```

---

# 📦 Step 4: Return Only the Numbers

```python
return [num for num, freq in sorted_items[:k]]
```

We don't need the frequency in the answer.

We only need:

```text
1
2
```

So the result is:

```text
[1,2]
```

---

# 🧠 Dry Run

Input:

```text
nums = [1,1,1,2,2,3]
k = 2
```

### Count

```text
1 → 3
2 → 2
3 → 1
```

Dictionary:

```text
{
    1: 3,
    2: 2,
    3: 1
}
```

### Sort

```text
(1,3)
(2,2)
(3,1)
```

### Take first 2

```text
[(1,3), (2,2)]
```

### Extract numbers

```text
[1,2]
```

### Final Answer

```text
[1,2]
```

---

# ⏱️ Complexity

Let:

* `n` = number of elements in `nums`
* `m` = number of unique elements

### Time Complexity

Counting frequencies:

```text
O(n)
```

Sorting unique elements:

```text
O(m log m)
```

Overall:

```text
O(n + m log m)
```

Since `m ≤ n`, this is commonly written as:

```text
O(n log n)
```

### Space Complexity

The dictionary stores the unique elements:

```text
O(m)
```

---

# 🧠 Key Learning

Today I learned:

* How to count frequencies using a dictionary
* How `.get()` works
* How `dict.items()` works
* How `lambda` is used for sorting
* How `reverse=True` sorts in descending order
* How slicing `[:k]` gets the first `k` elements
* How to combine **Hash Map + Sorting**

### ⭐ Important Pattern

```text
Array
  ↓
Count frequency
  ↓
Dictionary
  ↓
Sort by frequency
  ↓
Take first K
  ↓
Answer
```

---

# 📊 100 Days Progress

| Day | Problem                 | Main Concept       | Status |
| --- | ----------------------- | ------------------ | ------ |
| 1   | Contains Duplicate      | Set                | ✅      |
| 2   | Valid Anagram           | Hash Map           | ✅      |
| 3   | Two Sum                 | Hash Map           | ✅      |
| 4   | Group Anagrams          | Hash Map + Sorting | ✅      |
| 5   | Top K Frequent Elements | Hash Map + Sorting | ✅      |

## 🔥 Day 5 / 100

**Problem:** Top K Frequent Elements
**Language:** Python
**Topic:** Hash Map + Sorting
**Difficulty:** Medium
**Status:** ✅ Completed
