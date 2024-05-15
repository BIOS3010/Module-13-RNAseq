## 13.3 Suffix arrays and binary search

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

```diff
! Fill inn all places with `...` to extract the sorted suffixes and the corresponding indexes (i.e., the suffix array)
! Use the function `suffix_array_naive` to compute the suffix array of ``mississippi` and compare your manual results
! Experiment with a longer word: `pneumonoultramicroscopicsilicovolcanoconiosis`
```

*FYI*: pneumonoultramicroscopicsilicovolcanoconiosis, from the Cambridge English Dictionary: a name that has been invented 
for a lung disease caused by breathing in very small pieces of ash or dust.

You will now complete the following Python code and explore the utility of binary search when working with suffix 
arrays. 

```python
import os

def SA_binary_search(sa, x, text, L=0, R=None):
    if L < 0:
        raise ValueError('lo must be non-negative')
    if R is None:
        R = len(sa)

    # Binary search
    while L < R:
        print(f"L={L}, R={R}")
        M = (L + R) // 2

        suffix = text[sa[M]:]
        common_prefix = os.path.commonprefix([suffix, x])
        m = ...

        if m == len(x):
            ...
        
        if suffix > x:
            R = M
        else:
            L = M + 1 # Correction to make the algorithm terminate when the pattern is not found

    if L>=R:
        raise IndexError('not found')

    return sa[L]
```

```diff
! Fill inn all places with `...` to complete teh SA_binary_search function
! Use it in combination with the function `suffix_array_naive` to check whether the query "ACG" is contained in the 
string "TAAGGTGAGATAACTCCGTAACTGACTACGCCTTCCTCTAGACCTTACTTGACCAGATACAGTGTCTTTGACACGTTTATGGATTACAGCAATCACATCCAAGACTGGCT"
! Can you imagine a way to identify ALL positions of the query inside the string? Look at how the suffix array is defined.
```
