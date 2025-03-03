---

## **1. Greedy Algorithms**

### **Activity Selection Problem**
📌 **Problem Statement:**  
You are given `n` activities, each with a start and end time. Select the **maximum number of non-overlapping activities**.

### **Algorithm Steps**
1. **Sort** activities by their finishing times (ascending order).
2. **Select** the first activity and mark its end time.
3. **Iterate** over the remaining activities:
   - If an activity starts **after or exactly at** the last selected activity’s end time, select it.
4. **Continue until all activities are checked.**

---

### **Example Walkthrough**
```plaintext
Activities:  [(1,3), (2,5), (4,6), (6,8), (5,7), (8,9)]
```

#### **Step 1: Sort by finishing time**
```plaintext
Sorted: [(1,3), (4,6), (2,5), (5,7), (6,8), (8,9)]
```

#### **Step 2: Select first activity**
```plaintext
Selected activities: [(1,3)]
Last end time = 3
```

#### **Step 3: Iterate through activities**
1. **Check (4,6)**:  
   - Start time `4` is **>=** last end time `3` ✅ **(Select)**  
   - Update last end time → `6`

2. **Check (2,5)**:  
   - Start time `2` is **<** last end time `6` ❌ **(Reject)**

3. **Check (5,7)**:  
   - Start time `5` is **<** last end time `6` ❌ **(Reject)**

4. **Check (6,8)**:  
   - Start time `6` is **>=** last end time `6` ✅ **(Select)**  
   - Update last end time → `8`

5. **Check (8,9)**:  
   - Start time `8` is **>=** last end time `8` ✅ **(Select)**  
   - Update last end time → `9`

#### **Final Selected Activities:**
```plaintext
[(1,3), (4,6), (6,8), (8,9)]
```

---

## **2. Kruskal’s Algorithm (Minimum Spanning Tree)**
📌 **Problem Statement:**  
Find the **Minimum Spanning Tree (MST)** of a weighted graph using **Greedy approach**.

### **Algorithm Steps**
1. **Sort** all edges in **ascending order** of weight.
2. **Initialize** an empty MST and a **Union-Find** data structure to check for cycles.
3. **Iterate** over edges:
   - If adding an edge **doesn’t form a cycle**, include it in MST.
4. **Repeat** until `V-1` edges are included (`V = number of vertices`).

---

### **Example Walkthrough**
#### **Graph Representation (Adjacency List)**
```plaintext
Vertices: {A, B, C, D}
Edges: [(A,B,1), (B,C,3), (A,C,2), (C,D,4)]
```

#### **Step 1: Sort edges by weight**
```plaintext
Sorted edges: [(A,B,1), (A,C,2), (B,C,3), (C,D,4)]
```

#### **Step 2: Initialize MST**
```plaintext
MST = []
```

#### **Step 3: Iterating through sorted edges**
1. **Add (A,B,1)** ✅ (No cycle)
   ```plaintext
   MST = [(A,B)]
   ```

2. **Add (A,C,2)** ✅ (No cycle)
   ```plaintext
   MST = [(A,B), (A,C)]
   ```

3. **Add (B,C,3)** ❌ (Forms cycle, so reject)

4. **Add (C,D,4)** ✅ (No cycle)
   ```plaintext
   MST = [(A,B), (A,C), (C,D)]
   ```

#### **Final MST:**
```plaintext
[(A,B), (A,C), (C,D)]
```

---

## **3. Fractional Knapsack**
📌 **Problem Statement:**  
Given `n` items with weights and values, maximize the **total value** that can be carried in a knapsack of capacity `W`. Unlike 0/1 Knapsack, **fractions of items** can be taken.

### **Algorithm Steps**
1. **Compute value/weight ratio** for each item.
2. **Sort** items by this ratio in **descending order**.
3. **Iterate** through items:
   - If the full item fits, take it.
   - Otherwise, take a fraction until the bag is full.
4. **Stop when the knapsack is full.**

---

### **Example Walkthrough**
```plaintext
Items: [(weight=10, value=60), (weight=20, value=100), (weight=30, value=120)]
Knapsack capacity: W = 50
```

#### **Step 1: Compute value/weight ratio**
```plaintext
Item 1: 60/10 = 6
Item 2: 100/20 = 5
Item 3: 120/30 = 4
```

#### **Step 2: Sort items by ratio (Descending order)**
```plaintext
Sorted items: [(10, 60), (20, 100), (30, 120)]
```

#### **Step 3: Iterating through items**
1. **Take full item (10, 60)**  
   ```plaintext
   Remaining W = 50 - 10 = 40
   Total value = 60
   ```

2. **Take full item (20, 100)**  
   ```plaintext
   Remaining W = 40 - 20 = 20
   Total value = 160
   ```

3. **Take fraction of (30, 120)**  
   ```plaintext
   Remaining W = 20 (out of 30)
   Value taken = (20/30) * 120 = 80
   ```

#### **Final Answer:**
```plaintext
Total value = 160 + 80 = 240
```

---
---

# **4. Divide and Conquer Algorithms**

## **Quick Sort**
📌 **Problem Statement:**  
Sort an array using the **divide and conquer** strategy.

### **Algorithm Steps**
1. **Choose a pivot element** (usually the last or middle element).
2. **Partition the array**:
   - Place elements **smaller** than the pivot on the left.
   - Place elements **greater** than the pivot on the right.
3. **Recursively** apply Quick Sort on the left and right partitions.
4. **Combine the sorted partitions.**

---

### **Example Walkthrough**
```plaintext
Input: [6, 3, 8, 5, 2, 7, 4]
```
✅ **Step 1: Choose pivot (last element: `4`)**  
✅ **Step 2: Partition**  
- Move elements < `4` to the left, > `4` to the right  
- Swaps: `[3, 2, 4, 6, 8, 7, 5]`  
✅ **Step 3: Recursively sort left and right**  
Left: `[3, 2]` → Pivot: `2` → `[2, 3]`  
Right: `[6, 8, 7, 5]` → Pivot: `5` → `[5, 6, 7, 8]`  

✅ **Final Sorted Array:**  
```plaintext
[2, 3, 4, 5, 6, 7, 8]
```

---

## **Merge Sort**
📌 **Problem Statement:**  
Sort an array using **Divide and Conquer**.

### **Algorithm Steps**
1. **Divide** array into two halves.
2. **Recursively sort** both halves.
3. **Merge** the two sorted halves.

---

### **Example Walkthrough**
```plaintext
Input: [6, 3, 8, 5, 2, 7, 4]
```
✅ **Step 1: Split recursively**
```plaintext
Left: [6, 3, 8, 5]
Right: [2, 7, 4]
```
✅ **Step 2: Split further**
```plaintext
Left: [6, 3] → Sorted: [3, 6]
Right: [8, 5] → Sorted: [5, 8]
```
✅ **Step 3: Merge sorted halves**
```plaintext
[3, 6] + [5, 8] → [3, 5, 6, 8]
[2, 7] + [4] → [2, 4, 7]
```
✅ **Step 4: Merge final arrays**
```plaintext
[3, 5, 6, 8] + [2, 4, 7] → [2, 3, 4, 5, 6, 7, 8]
```

✅ **Final Sorted Array:**  
```plaintext
[2, 3, 4, 5, 6, 7, 8]
```

---

## **Min-Max Algorithm (Finding Min & Max)**
📌 **Problem Statement:**  
Find the **minimum** and **maximum** values in an array.

### **Algorithm Steps**
1. **Divide** the array into two halves.
2. **Recursively find** min & max in each half.
3. **Compare** results from both halves to get the final min & max.

---

### **Example Walkthrough**
```plaintext
Input: [7, 2, 9, 1, 5, 6]
```
✅ **Step 1: Split into halves**
```plaintext
Left: [7, 2, 9]
Right: [1, 5, 6]
```
✅ **Step 2: Find min & max in each half**
```plaintext
Left: Min = 2, Max = 9
Right: Min = 1, Max = 6
```
✅ **Step 3: Compare across halves**
```plaintext
Overall Min = min(2, 1) = 1
Overall Max = max(9, 6) = 9
```

✅ **Final Result:**  
```plaintext
Min = 1, Max = 9
```

---

## **Matrix Chain Multiplication**
📌 **Problem Statement:**  
Find the optimal way to **multiply matrices** to minimize computations.

### **Algorithm Steps**
1. **Use a DP table `dp[i][j]`** to store min multiplication costs.
2. **Iterate** through matrix chains of increasing length.
3. **Compute the minimum multiplications** needed for each split.
4. **Return the optimal cost from `dp[1][n]`.**

---

### **Example Walkthrough**
```plaintext
Matrices: A1 (10×20), A2 (20×30), A3 (30×40)
```
✅ **Step 1: Compute multiplication cost**
```plaintext
(A1×A2) = 10×20×30 = 6000
(A2×A3) = 20×30×40 = 24000
```
✅ **Step 2: Choose the optimal order**
```plaintext
(A1×A2) first, then (A1A2 × A3)
Total cost = 6000 + 24000 = 30000
```

✅ **Final Answer:**  
```plaintext
Optimal cost = 30000
```

---

# **5. Fibonacci Series (Matrix Exponentiation)**
📌 **Problem Statement:**  
Compute the `n`th Fibonacci number efficiently.

### **Algorithm Steps**
1. **Use the matrix recurrence formula**:
   ```
   | F(n)   | = | 1 1 |^(n-1)  * | 1 |
   | F(n-1) |   | 1 0 |         | 0 |
   ```
2. **Exponentiate** the matrix in `O(log n)`.
3. **Extract** the Fibonacci number from the result.

---

### **Example Walkthrough**
```plaintext
Find F(5)
```
✅ **Step 1: Compute matrix power**
```plaintext
M^4 = | 1 1 |^4 = | 5 3 |
      | 1 0 |   | 3 2 |
```
✅ **Step 2: Multiply with initial vector**
```plaintext
Result = M^4 × | 1 | = | 5 |
                 | 0 |   | 3 |
```
✅ **Final Answer:**  
```plaintext
F(5) = 5
```

---
