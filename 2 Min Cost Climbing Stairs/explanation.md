# 🧩 Dynamic Programming Notes – 746. Min Cost Climbing Stairs

## Problem Restatement
You are given an integer array `cost` where `cost[i]` is the cost of the `i`th step.  
You can start at step `0` or step `1`.  
From step `i`, you can move either to `i+1` or `i+2`.  
You pay `cost[i]` when you land on step `i`.  

Return the **minimum cost to reach the top**, which is *just beyond the last step*.

---

## 1. Problem Intuition

👉 Think of it as **minimum cost to cross the array `cost[]`**.

- Steps are `0 … n-1` (with cost).  
- The "top" is step `n` (beyond the array, with **no cost**).  

So you only pay costs if you step on `0 … n-1`.  
Reaching `n` itself is free.

---

## 2. Define the State

We can define the DP in two common ways:

### Definition A
`dp[i] = minimum cost to reach step i` (including step `n` as the top).  
- Answer = `dp[n]`.

### Definition B
`dp[i] = minimum cost to stand on step i` (only 0 … n-1).  
- Answer = `min(dp[n-1], dp[n-2])`.

Both are valid — just two perspectives.

---

## 3. Recurrence Relation

From a step `i`, we pay `cost[i]` and move forward:

