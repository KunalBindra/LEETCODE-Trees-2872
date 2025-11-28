# LEETCODE-Trees-2872
**complete dry run** 

* `n = 5`
* `edges = [[0,2],[1,2],[1,3],[2,4]]`
* `values = [1,8,1,4,4]`
* `k = 6`

---

# ✅ **Step 1: Build adjacency list**

Edges → adjacency:

```
0 → [2]
1 → [2,3]
2 → [0,1,4]
3 → [1]
4 → [2]
```

---

# ✅ **Step 2: Call `dfs(0, -1)`**

We will compute `sum` (mod 6) for each subtree, and increase `count` whenever sum ≡ 0 (mod 6).

---

# 🌿 Start DFS

## 🔹 **dfs(0, -1)**

Neighbors: `{2}`

### ➤ Go to **dfs(2, 0)**

Neighbors: `{0,1,4}`
Skip parent (=0).

---

## 🔹 **dfs(2, 0)**

### ➤ Go to **dfs(1, 2)**

Neighbors: `{2,3}`
Skip parent (=2).

---

## 🔹 **dfs(1, 2)**

### ➤ Go to **dfs(3, 1)**

Neighbors: `{1}` → only parent, so leaf.

### ✔ **dfs(3,1)**

```
sum = 0 + values[3] = 4  
4 % 6 = 4  
Not divisible → count stays same  
Return 4
```

Back to node **1**:

```
sum = 4    (from child 3)
sum += values[1] = 8 → 4 + 8 = 12
12 % 6 = 0
sum == 0 → count++
count = 1
Return 0
```

---

Back to **dfs(2,0)**
We received `0` from child 1:

```
sum = 0
```

---

### ➤ Next child → **dfs(4,2)**

Neighbors: `{2}` → only parent → leaf.

#### ✔ dfs(4,2)

```
sum = 0 + values[4] = 4
4 % 6 = 4
Not divisible
Return 4
```

Back to node **2**:

```
sum = 0 + 4 = 4
```

Now add own value:

```
sum += values[2] = 1  
4 + 1 = 5  
5 % 6 = 5  
sum != 0 → count stays 1  
Return 5
```

---

## Back to **dfs(0,-1)**

Child 2 returned 5:

```
sum = 5
```

Add own value:

```
sum += values[0] = 1 → 5 + 1 = 6  
6 % 6 = 0  
sum == 0 → count++  
count = 2
Return 0
```

---

# 🎉 **Final Answer**

```
count = 2
```

---

# ✅ **Final Output: `2`**
