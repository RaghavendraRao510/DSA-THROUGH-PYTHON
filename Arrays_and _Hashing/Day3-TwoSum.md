# 🚀 100 Days of Coding Challenge

## 📅 Day 3: Two Sum

### 🧩 Problem

Given an integer array `nums` and an integer `target`, return the **indices of the two numbers** such that they add up to `target`.

You may assume that each input has **exactly one solution**.

You cannot use the same element twice.

---

## 📌 Examples

### Example 1

```text
Input:  nums = [2,7,11,15], target = 9
Output: [0,1]
```

Explanation:

```text
nums[0] + nums[1]
2 + 7 = 9
```

Therefore, the answer is `[0, 1]`.

### Example 2

```text
Input:  nums = [3,2,4], target = 6
Output: [1,2]
```

Because:

```text
2 + 4 = 6
```

### Example 3

```text
Input:  nums = [3,3], target = 6
Output: [0,1]
```

Because:

```text
3 + 3 = 6
```

---

## 💡 Approach

We can solve Two Sum efficiently using a **dictionary (hash map)**.

The main idea is:

```text
complement = target - current_number
```

Then we check whether that complement was already seen.

For example:

```text
nums = [2,7,11,15]
target = 9
```

For `2`:

```text
complement = 9 - 2
           = 7
```

We haven't seen `7` yet, so store `2`.

For `7`:

```text
complement = 9 - 7
           = 2
```

We have already seen `2`.

Therefore, return the indices of `2` and `7`.

---

## 💻 Python Solution

```python
class Solution(object):
    def twoSum(self, nums, target):
        seen = {}

        for i, num in enumerate(nums):
            complement = target - num

            if complement in seen:
                return [seen[complement], i]

            seen[num] = i
```

---

## 🔍 Code Explanation

### 1. Create a dictionary

```python
seen = {}
```

The dictionary stores:

```text
number → index
```

Example:

```text
{
    2: 0,
    7: 1
}
```

This means:

```text
2 is at index 0
7 is at index 1
```

---

### 2. Use `enumerate()`

```python
for i, num in enumerate(nums):
```

`enumerate()` gives us both:

* `i` → index
* `num` → value

For:

```text
nums = [2,7,11,15]
```

we get:

```text
i = 0, num = 2
i = 1, num = 7
i = 2, num = 11
i = 3, num = 15
```

---

### 3. Find the complement

```python
complement = target - num
```

The complement is the number we need to reach the target.

Example:

```text
target = 9
num = 2

complement = 9 - 2
           = 7
```

So we need `7`.

---

### 4. Check if complement exists

```python
if complement in seen:
```

This checks whether we have already encountered the required number.

For example:

```text
seen = {2: 0}
complement = 2
```

Since `2` is in `seen`, we found the pair.

---

### 5. Return the indices

```python
return [seen[complement], i]
```

`seen[complement]` gives the index of the previously seen number.

`i` gives the current index.

Example:

```text
seen = {2: 0}
i = 1
```

Therefore:

```text
[seen[2], 1]
[0, 1]
```

---

### 6. Store the current number

```python
seen[num] = i
```

If we haven't found the answer yet, store the current number and its index.

Example:

```text
num = 2
i = 0
```

Dictionary becomes:

```text
seen = {
    2: 0
}
```

---

## 🧠 Dry Run

### Input

```text
nums = [2,7,11,15]
target = 9
```

### Step 1

```text
i = 0
num = 2
```

Calculate:

```text
complement = 9 - 2
           = 7
```

`7` is not in `seen`.

Store:

```text
seen = {2: 0}
```

---

### Step 2

```text
i = 1
num = 7
```

Calculate:

```text
complement = 9 - 7
           = 2
```

`2` is already in `seen`.

```text
seen[2] = 0
```

Return:

```text
[0,1]
```

---

## 🔄 Why Do We Store the Index?

The question asks for **indices**, not the numbers themselves.

For:

```text
nums = [2,7,11,15]
```

We need:

```text
[0,1]
```

not:

```text
[2,7]
```

That's why we store:

```python
seen[num] = i
```

---

## ⏱️ Complexity

### Time Complexity

**O(n)**

We traverse the array once.

Dictionary lookup is approximately **O(1)** on average.

### Space Complexity

**O(n)**

The dictionary can store up to `n` elements.

---

## 🧠 Key Learning

Today I learned:

* How to use a **dictionary/hash map**
* How `enumerate()` works
* How to calculate a **complement**
* How to store a value with its index
* How hash maps can reduce an **O(n²)** solution to **O(n)**

### ⭐ Important Pattern

```text
target - current number = complement
```

Then:

```text
Check complement → Found? Return indices → Otherwise store number
```

This **hash map lookup pattern** is one of the most important techniques for coding interview problems.

---
