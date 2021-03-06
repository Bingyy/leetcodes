# Decode Ways

## Problem Description

A message containing letters from`A-Z`is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given an encoded message containing digits, determine the total number of ways to decode it.

For example,  
Given encoded message`"12"`, it could be decoded as`"AB"`\(1 2\) or`"L"`\(12\).

The number of ways decoding`"12"`is 2.

> Companies: Microsoft, Uber, Facebook

## Analysis

This problem can be solved with Dynamic Programming

If string starts with zero, return 0.



dp\[i\] means number of decode ways for string s\[0:i\].

dp\[0\] = 1 

dp\[1\] = 1

dp\[n\] = dp\[n-1\] + dp\[n-2\] if s\[n\] can combine with s\[n-1\] else dp\[n\] = dp\[n-1\]

**Optimize: Here we only use two variables, because only last two states matter.**

## Solution





