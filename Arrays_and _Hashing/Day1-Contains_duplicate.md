# 🚀 100 Days of Coding Challenge

## 📅 Day 1: Contains Duplicate

### 🧩 Problem

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array.

Return `false` if every element is distinct.

### 📌 Examples

**Example 1**

```text
Input:  nums = [1,2,3,1]
Output: true
```

**Explanation:**
The element `1` appears at indices `0` and `3`.

**Example 2**

```text
Input:  nums = [1,2,3,4]
Output: false
```

**Explanation:**
All elements are distinct.

**Example 3**

```text
Input:  nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

---

## 💡 Approach

We can solve this problem using a **set**.

A set stores only unique values.

### Steps

1. Create an empty set called `seen`.
2. Traverse each number in the array.
3. Check whether the number already exists in `seen`.
4. If it exists, return `True`.
5. Otherwise, add the number to `seen`.
6. If the loop finishes without finding a duplicate, return `False`.

---

## 💻 Python Solution

```python
class Solution:
    def containsDuplicate(self, nums):
        seen = set()

        for num in nums:
            if num in seen:
                return True

            seen.add(num)

        return False
```

---

## 🔍 Code Explanation

```python
seen = set()
```

Creates an empty set to store numbers that we have already visited.

```python
for num in nums:
```

Loops through every element in the array.

```python
if num in seen:
    return True
```

If the number is already in the set, it means the number appeared before, so we found a duplicate.

```python
seen.add(num)
```

If the number is not already present, add it to the set.

```python
return False
```

If no duplicate is found after checking all elements, return `False`.

---

## ⏱️ Complexity

### Time Complexity

**O(n)**

We traverse the array once.

### Space Complexity

**O(n)**

In the worst case, the set stores all `n` elements.

---

## 🧠 Key Learning

Today I learned how to use a **Python Set** to efficiently detect duplicate values.

> **Set → Unique values → Fast lookup**

This is a common technique for solving array and hashing problems.

---

## ✅ Day 1 Completed

**Problem:** Contains Duplicate
**Language:** Python
**Topic:** Arrays + Hash Set
**Difficulty:** Easy
**Status:** ✅ Completed

### 🔥 Goal

**Day 1 / 100 — Keep Coding, Keep Learning!**
