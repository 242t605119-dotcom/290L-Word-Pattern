# LeetCode 290 - Word Pattern

## Problem Statement

Given a pattern and a string `s`, determine whether `s` follows the same pattern.

A string follows the pattern if there is a **bijection** between a letter in the pattern and a non-empty word in `s`.

This means:

* Each pattern character maps to exactly one word.
* Each word maps to exactly one pattern character.
* Two different characters cannot map to the same word.

---

## Example 1

### Input

```text
pattern = "abba"
s = "dog cat cat dog"
```

### Output

```text
True
```

### Explanation

The mapping is:

```text
a → dog
b → cat
```

Therefore:

```text
a b b a
↓ ↓ ↓ ↓
dog cat cat dog
```

The pattern matches.

---

## Example 2

### Input

```text
pattern = "abba"
s = "dog cat cat fish"
```

### Output

```text
False
```

### Explanation

The pattern requires:

```text
a → dog
b → cat
```

Therefore the last character `a` should map to `dog`.

But the last word is `fish`.

So the pattern does not match.

---

## Approach

We use **two hash maps**.

### Map 1

```text
character → word
```

This ensures that each pattern character always maps to the same word.

### Map 2

```text
word → character
```

This ensures that two different pattern characters cannot map to the same word.

Both maps are necessary because the relationship must be one-to-one.

---

## Algorithm

1. Split the string `s` into individual words.
2. If the number of pattern characters is different from the number of words, return `False`.
3. Create two dictionaries:

   * `char_to_word`
   * `word_to_char`
4. Traverse the pattern and words together.
5. For every character and word:

   * If the character already has a different word, return `False`.
   * If the word already has a different character, return `False`.
6. Store the mapping in both dictionaries.
7. If all mappings are valid, return `True`.

---

## Example Walkthrough

Given:

```text
pattern = "abba"
s = "dog cat cat dog"
```

After splitting:

```text
["dog", "cat", "cat", "dog"]
```

### Step 1

```text
a → dog
dog → a
```

### Step 2

```text
b → cat
cat → b
```

### Step 3

```text
b → cat
```

This is consistent.

### Step 4

```text
a → dog
```

This is also consistent.

Therefore:

```text
True
```

---

## Why Two Maps?

Consider:

```text
pattern = "ab"
s = "dog dog"
```

If we only checked:

```text
character → word
```

we could get:

```text
a → dog
b → dog
```

But this is invalid because two different characters map to the same word.

The second map prevents this:

```text
dog → a
```

When we try:

```text
b → dog
```

we detect that `dog` is already mapped to `a`.

Therefore, we return `False`.

---

## Time Complexity

We process every character and word once.

**Time Complexity:** `O(n)`

where `n` is the number of words.

---

## Space Complexity

The two dictionaries store the mappings.

**Space Complexity:** `O(n)`

---

## Key Concept

The main concepts used are:

* Hash Map
* Dictionary
* String splitting
* Bijection
* One-to-one mapping

---

## Language

Python

## LeetCode Problem

290 - Word Pattern

## Author

T. Nandhini
