## 13.3 Suffix arrays and pattern search

In this exercise, you will have the opportunity to work with suffix arrays and binary search in Python.

You will start by computing the suffix array of a given string manually: `mississippi`. This hands-on approach will
allow you to grasp the underlying process. Once you have computed the suffix array by hand, you will move on to the coding part.

```python
def suffix_array_naive(s):
    suffixes = [(s[i:], i) for i in range(len(s))]
    print(f"Suffixes paired with indices: {suffixes}")
    suffixes.sort()
    print(f"Suffixes paired with indices -- after lexicographic sorting: {suffixes}")

    sorted_suffixes = [...]
    print(f"Just the sorted suffixes: {sorted_suffixes}")

    suffix_array = [...]
    print(f"Just the sorted indices (i.e., the suffix array): {suffix_array}")
    return suffix_array
```
## 13.3.1 Creating a suffix array

```diff
! Fill inn all places with `...` to extract the sorted suffixes and the corresponding indexes (i.e., the suffix array)
! Use the function `suffix_array_naive` to compute the suffix array of ``mississippi` and compare your manual results
! Experiment with a longer word: `pneumonoultramicroscopicsilicovolcanoconiosis`
```

*FYI*: pneumonoultramicroscopicsilicovolcanoconiosis, from the Cambridge English Dictionary: a name that has been invented
for a lung disease caused by breathing in very small pieces of ash or dust.

## 13.3.2 Binary search and suffix arrays
You will now complete the following Python code and explore the utility of binary search when working with suffix arrays.

```python
import os

def SA_binary_search(x, q, sa):
    L = ...
    R = ...

    # Binary search
    while L < R:

        M = (L + R) // 2
        suffix = x[sa[M]:]
        common_prefix = ... #HINT: check os.path.commonprefix

        if len(common_prefix) == len(q):
            print(f"Query {q} found at index {sa[M]} in the string {x}")
            return sa[M]

        if ...:
            R = M
        else:
            L = ...

    if L >= R:
        print(f"Query {q} not found!")
        return None
```

```diff
! Fill inn all places with `...` to complete the SA_binary_search function
! Use it in combination with the function `suffix_array_naive` to  experiment with the string "banana" and queries "ban",
"na", and "xan" respectively. What does it return? To make things less messy, comment all "print" commands inside
`suffix_array_naive`.
! Check whether the query "ACG" is contained in the string
"TAAGGTGAGATAACTCCGTAACTGACTACGCCTTCCTCTAGACCTTACTTGACCAGATACAGTGTCTTTGACACGTTTATGGATTACAGCAATCACATCCAAGACTGGCT".
! Can you imagine a way to identify ALL positions of the query inside the string? Look at how the suffix array is defined.
```
