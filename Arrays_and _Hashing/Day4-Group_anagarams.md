# 🚀 100 Days of Coding Challenge

## 📅 Day 4: Group Anagrams

### 🧩 Problem

Given an array of strings `strs`, group the **anagrams** together.

You can return the answer in **any order**.

Two strings are anagrams if they contain the same characters with the same frequencies, but their order can be different.

---

## 📌 Examples

### Example 1

```text
Input:
strs = ["eat","tea","tan","ate","nat","bat"]

Output:
[["bat"],["nat","tan"],["ate","eat","tea"]]
```

### Example 2

```text
Input:
strs = [""]
```

Output:

```text
[[""]]
```

### Example 3

```text
Input:
strs = ["a"]
```

Output:

```text
[["a"]]
```

---

## 💡 Approach

We can use a **dictionary (hash map)**.

The important idea is to create the same **key** for all anagrams.

For example:

```text
eat → aet
tea → aet
ate → aet
```

Since they all produce the same sorted string, they can be placed in the same group.

For:

```text
tan → ant
nat → ant
```

Both produce `ant`, so they belong to another group.

---

## 💻 Python Solution

```python
class Solution(object):
    def groupAnagrams(self, strs):
        dico = {}

        for word in strs:
            key = "".join(sorted(word))

            if key not in dico:
                dico[key] = []

            dico[key].append(word)

        return list(dico.values())
```

---

# 🔍 Code Explanation

## 1. Create a dictionary

```python
dico = {}
```

The dictionary will store:

```text
key → list of anagrams
```

For example:

```text
{
    "aet": ["eat", "tea", "ate"],
    "ant": ["tan", "nat"],
    "abt": ["bat"]
}
```

---

## 2. Loop through every word

```python
for word in strs:
```

For:

```text
["eat","tea","tan","ate","nat","bat"]
```

we process each word one by one.

---

## 3. Create a key

```python
key = "".join(sorted(word))
```

This is the most important line.

### `sorted(word)`

Sorts the characters alphabetically.

Example:

```text
eat → ['a', 'e', 't']
tea → ['a', 'e', 't']
ate → ['a', 'e', 't']
```

### `"".join(...)`

Converts the list back into a string:

```text
['a', 'e', 't'] → "aet"
```

Therefore:

```text
eat → aet
tea → aet
ate → aet
```

All anagrams get the same key.

---

## 4. Check if the key exists

```python
if key not in dico:
    dico[key] = []
```

If we see the key for the first time, create an empty list.

For example:

```text
word = "eat"
key = "aet"
```

Since `"aet"` doesn't exist:

```text
dico["aet"] = []
```

---

## 5. Add the word to its group

```python
dico[key].append(word)
```

Now:

```text
dico["aet"]
```

becomes:

```text
["eat"]
```

When `"tea"` comes:

```text
dico["aet"] = ["eat", "tea"]
```

When `"ate"` comes:

```text
dico["aet"] = ["eat", "tea", "ate"]
```

---

# 🧠 Dry Run

Input:

```text
["eat","tea","tan","ate","nat","bat"]
```

### Step 1

```text
word = "eat"
key = "aet"
```

Dictionary:

```text
{
    "aet": ["eat"]
}
```

### Step 2

```text
word = "tea"
key = "aet"
```

Dictionary:

```text
{
    "aet": ["eat", "tea"]
}
```

### Step 3

```text
word = "tan"
key = "ant"
```

Dictionary:

```text
{
    "aet": ["eat", "tea"],
    "ant": ["tan"]
}
```

### Step 4

```text
word = "ate"
key = "aet"
```

Dictionary:

```text
{
    "aet": ["eat", "tea", "ate"],
    "ant": ["tan"]
}
```

### Step 5

```text
word = "nat"
key = "ant"
```

Dictionary:

```text
{
    "aet": ["eat", "tea", "ate"],
    "ant": ["tan", "nat"]
}
```

### Step 6

```text
word = "bat"
key = "abt"
```

Dictionary:

```text
{
    "aet": ["eat", "tea", "ate"],
    "ant": ["tan", "nat"],
    "abt": ["bat"]
}
```

Finally:

```python
return list(dico.values())
```

gives:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

The order does not matter.

---

# ⭐ Why Does This Work?

The key idea is:

```text
Anagrams have the same sorted characters.
```

For example:

```text
eat → aet
tea → aet
ate → aet
```

But:

```text
bat → abt
```

So `"bat"` gets a different key and goes into a different group.

---

## ⏱️ Complexity

Let:

* `n` = number of strings
* `k` = maximum length of a string

### Time Complexity

**O(n × k log k)**

For every word, we sort its characters.

Sorting a string of length `k` takes approximately:

```text
O(k log k)
```

and we do this for `n` strings.

### Space Complexity

**O(n × k)**

We store all the strings in the dictionary groups.

---

## 🧠 Key Learning

Today I learned:

* How to group similar strings using a dictionary
* How `sorted()` works
* How `"".join()` works
* How to create a unique key for anagrams
* How dictionaries can group related values

### ⭐ Important Pattern

```text
Input string
     ↓
Sort characters
     ↓
Create key
     ↓
Use key in dictionary
     ↓
Append word to group
```

---
