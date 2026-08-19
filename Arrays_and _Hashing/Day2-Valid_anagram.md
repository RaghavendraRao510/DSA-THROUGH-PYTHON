# 🚀 100 Days of Coding Challenge

## 📅 Day 2: Valid Anagram

### 🧩 Problem

Given two strings `s` and `t`, return `true` if `t` is an **anagram** of `s`, and `false` otherwise.

An **anagram** is a word or string formed by rearranging the characters of another string.

### 📌 Examples

**Example 1**

```text
Input:  s = "anagram", t = "nagaram"
Output: true
```

Both strings contain the same characters with the same frequencies.

**Example 2**

```text
Input:  s = "rat", t = "car"
Output: false
```

The characters are different, so `t` is not an anagram of `s`.

---

## 💡 Approach

We can solve this problem using a **dictionary (hash map)** called `counter`.

The dictionary stores:

```text
character → number of occurrences
```

For example:

```text
s = "aab"

counter = {
    'a': 2,
    'b': 1
}
```

Then we check the characters of `t` one by one and decrease their counts.

---

## 💻 Python Solution

```python
class Solution(object):
    def isAnagram(self, s, t):
        if len(s) != len(t):
            return False

        counter = {}

        for char in s:
            counter[char] = counter.get(char, 0) + 1

        for char in t:
            if char not in counter or counter[char] == 0:
                return False

            counter[char] -= 1

        return True
```

---

## 🔍 Code Explanation

### 1. Check the length

```python
if len(s) != len(t):
    return False
```

Anagrams must have the same number of characters.

For example:

```text
"rat" → 3 characters
"car" → 3 characters
```

But:

```text
"hello" → 5 characters
"hi"    → 2 characters
```

So `"hello"` and `"hi"` cannot be anagrams.

---

### 2. Create an empty dictionary

```python
counter = {}
```

This dictionary will store the frequency of every character.

---

### 3. Count characters in `s`

```python
for char in s:
    counter[char] = counter.get(char, 0) + 1
```

For:

```text
s = "anagram"
```

The dictionary becomes:

```text
{
    'a': 3,
    'n': 1,
    'g': 1,
    'r': 1,
    'm': 1
}
```

### What does this mean?

```python
counter.get(char, 0)
```

If the character already exists, get its current count.

If it doesn't exist, use `0`.

Then:

```python
+ 1
```

increases the count.

---

## 🔄 4. Check characters in `t`

```python
for char in t:
```

Now we go through every character in `t`.

For:

```text
t = "nagaram"
```

we check whether each character exists in `counter`.

---

### 5. Detect an invalid character

```python
if char not in counter or counter[char] == 0:
    return False
```

There are two situations where we return `False`:

**Case 1: Character doesn't exist**

```text
s = "abc"
t = "abd"
```

`d` is not present in `s`.

So:

```python
char not in counter
```

is `True`.

---

**Case 2: Character was already used too many times**

Suppose:

```text
s = "aab"
t = "aaa"
```

`s` contains only two `a`s, but `t` contains three.

After using both `a`s:

```text
counter['a'] == 0
```

The third `a` makes the condition true, so we return `False`.

---

## 6. Decrease the count

```python
counter[char] -= 1
```

This means:

```python
counter[char] = counter[char] - 1
```

Example:

```text
counter['a'] = 3
```

After finding one `a` in `t`:

```text
counter['a'] = 2
```

After another:

```text
counter['a'] = 1
```

After another:

```text
counter['a'] = 0
```

---

## 7. Return True

```python
return True
```

If every character in `t` can be matched with a character from `s`, the strings are anagrams.

---

## 🧠 Dry Run

### Input

```text
s = "rat"
t = "tar"
```

### Count `s`

```text
r → 1
a → 1
t → 1
```

Dictionary:

```text
{
    'r': 1,
    'a': 1,
    't': 1
}
```

### Check `t`

`'t'` → count becomes `0`

`'a'` → count becomes `0`

`'r'` → count becomes `0`

No invalid character was found.

```text
Output: True
```

---

## ❌ Another Dry Run

```text
s = "rat"
t = "car"
```

Count:

```text
{
    'r': 1,
    'a': 1,
    't': 1
}
```

Now `t` starts with:

```text
'c'
```

But `'c'` is not in `counter`.

Therefore:

```python
return False
```

Output:

```text
False
```

---

## ⏱️ Complexity

### Time Complexity

**O(n)**

We go through the strings a limited number of times.

### Space Complexity

**O(n)**

The dictionary can store up to `n` different characters.

---

## 🎯 Key Learning

Today I learned:

* How to use a **dictionary/hash map**
* How to count character frequencies
* How `.get()` works
* How `+= 1` increases a count
* How `-= 1` decreases a count
* How to use a hash map to solve an anagram problem

### ⭐ Important Pattern

```text
Count → Store → Check → Decrease
```

This **frequency-counting pattern** is very useful for many string and array problems.

---

## ✅ Day 2 Completed

**Problem:** Valid Anagram
**Language:** Python
**Topic:** Strings + Hash Map
**Difficulty:** Easy
**Status:** ✅ Completed

### 🔥 Progress

**Day 2 / 100 — Keep Coding, Keep Learning!**
