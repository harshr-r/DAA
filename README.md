---

## **1. Greedy Algorithms**
Greedy algorithms make locally optimal choices at each step to find a global solution.  

---

### **Activity Selection Problem**
📌 **Problem Statement:**  
Given `n` activities with start and end times, select the maximum number of non-overlapping activities.

#### **Algorithm:**
1. **Sort** activities based on their finishing times.
2. **Select** the first activity (it finishes the earliest).
3. **Iterate** through the sorted list:
   - If the start time of the current activity is greater than or equal to the end time of the last selected activity, select it.
4. **Continue until all activities are checked.**

#### **Example:**
```plaintext
Activities:  [(1,3), (2,5), (4,6), (6,8), (5,7), (8,9)]
```
**Step 1:** Sort by finishing time:
```plaintext
[(1,3), (4,6), (2,5), (5,7), (6,8), (8,9)]
```
**Step 2:** Select `1st` activity → `(1,3)`

**Step 3:** Next non-overlapping activity → `(4,6)`

**Step 4:** Next non-overlapping activity → `(6,8)`

**Step 5:** Next non-overlapping activity → `(8,9)`

✅ **Selected activities:** `[(1,3), (4,6), (6,8), (8,9)]`

---

### **Kruskal’s Algorithm (Minimum Spanning Tree)**
📌 **Problem Statement:**  
Find the **Minimum Spanning Tree (MST)** of a weighted graph using **Greedy approach**.

#### **Algorithm:**
1. **Sort** all edges in ascending order of weight.
2. **Pick** the smallest edge. If it **doesn’t form a cycle**, add it to the MST.
3. **Repeat** until we have `V-1` edges (where `V` is the number of vertices).
4. **Use Disjoint Set (Union-Find)** to detect cycles.

#### **Example:**
Graph:
```plaintext
Vertices: {A, B, C, D}
Edges: [(A,B,1), (B,C,3), (A,C,2), (C,D,4)]
```
**Step 1:** Sort edges: `[(A,B,1), (A,C,2), (B,C,3), (C,D,4)]`

**Step 2:** Add smallest edge: `[(A,B,1)]`

**Step 3:** Add next edge `(A,C,2)` → No cycle

**Step 4:** Add `(B,C,3)` → No cycle

**Step 5:** Add `(C,D,4)` → No cycle

✅ **Final MST:** `[(A,B), (A,C), (C,D)]`

---

### **Job Scheduling with Deadlines**
📌 **Problem Statement:**  
Given `n` jobs with deadlines and profits, schedule jobs to **maximize profit**.

#### **Algorithm:**
1. **Sort** jobs by profit (descending order).
2. **Create** a result array to store scheduled jobs.
3. **Iterate** through the sorted jobs:
   - Place the job in the latest available slot before its deadline.
4. **Return the scheduled jobs and maximum profit.**

#### **Example:**
```plaintext
Jobs: [(J1, deadline=2, profit=100), (J2, deadline=1, profit=50), (J3, deadline=2, profit=200)]
```
**Step 1:** Sort jobs by profit: `[(J3,2,200), (J1,2,100), (J2,1,50)]`

**Step 2:** Assign jobs:
```
Time slots: [_, _]
J3 → [_, J3]
J1 → [J1, J3]
J2 → Already occupied
```
✅ **Scheduled Jobs:** `[J1, J3]`  
✅ **Max Profit:** `300`

---

### **Huffman Encoding**
📌 **Problem Statement:**  
Find the **optimal binary prefix codes** for a set of characters.

#### **Algorithm:**
1. **Sort** characters by frequency.
2. **Create** a priority queue (min heap).
3. **Merge** the two least frequent nodes into a tree.
4. **Repeat** until one tree remains.
5. **Generate binary codes from the tree.**

#### **Example:**
```plaintext
Characters: [(A,5), (B,9), (C,12), (D,13)]
```
**Step 1:** Create nodes:  
```
    A(5)  B(9)  C(12)  D(13)
```
**Step 2:** Merge least frequent → `(A(5) + B(9) = 14)`

**Step 3:** Merge with next → `(C(12) + (AB)14 = 26)`

**Step 4:** Merge with last → `(D(13) + (C(AB))26 = 39)`

✅ **Final Huffman Codes:**  
```
A = 00
B = 01
C = 10
D = 11
```

---

### **Prim’s Algorithm**
📌 **Problem Statement:**  
Find the **Minimum Spanning Tree (MST)** from a weighted graph.

#### **Algorithm:**
1. **Start** from any vertex.
2. **Pick** the smallest edge to a new vertex.
3. **Repeat** until all vertices are included.

#### **Example:**
```plaintext
Graph:
  A - (2) - B
  |         |
 (1)       (3)
  |         |
  C - (4) - D
```
✅ **MST:** `[(A,C,1), (A,B,2), (B,D,3)]`

---

### **Dijkstra’s Algorithm**
📌 **Problem Statement:**  
Find the **shortest path** from a source node.

#### **Algorithm:**
1. **Initialize** distance array (set source = 0, rest = ∞).
2. **Pick** the minimum distance vertex.
3. **Update** adjacent vertices.
4. **Repeat** until all vertices are visited.

#### **Example:**
```plaintext
Graph: A → B(1), A → C(4), B → C(2), C → D(1)
```
**Shortest Path:**  
```
A → B → C → D  → Distances: [0, 1, 3, 4]
```

---

### **0/1 Knapsack Problem**
📌 **Problem Statement:**  
Given `n` items with weights and values, maximize value within weight `W`.

#### **Algorithm:**
1. **Create** a `dp[i][j]` table.
2. **Fill** the table by checking:
   - If the item **can fit**, take max of including or not including it.

#### **Example:**
```plaintext
Items: [(w=1,v=10), (w=2,v=20), (w=3,v=30)], W = 5
```
✅ **Max Profit:** `50`

---

### **Quick Sort**
📌 **Algorithm:**
1. **Pick** a pivot.
2. **Partition** into two halves.
3. **Recursively** sort each half.

#### **Example:**
```plaintext
Array: [3, 6, 2, 7, 5]
```
Pivot `5` → `[3,2]` `5` `[6,7]`

✅ **Sorted:** `[2,3,5,6,7]`

---

### **Merge Sort**
📌 **Algorithm:**
1. **Divide** array into two halves.
2. **Sort** recursively.
3. **Merge** halves.

#### **Example:**
```plaintext
Array: [3, 6, 2, 7, 5]
```
✅ **Sorted:** `[2,3,5,6,7]`

---

### **Fibonacci Using Matrix Exponentiation**
📌 **Formula:**
```
| F(n)   | = | 1 1 |^(n-1)  * | 1 |
| F(n-1) |   | 1 0 |         | 0 |
```
✅ **F(5) = 5**

---
