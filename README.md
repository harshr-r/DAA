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
