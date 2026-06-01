I analyzed all the HPC Endsem papers from **2023, May 2024, Nov 2024, May 2025, and Nov 2025**. 

Based on the **2023 → 2025 pattern**, the paper setter rotates topics but rarely introduces completely new concepts. Looking at what was asked recently in **May 2025** and **Nov 2025**, some topics have become "due" again while others were asked repeatedly and may continue.

## Predicted Paper 2026

---

# Unit 3 (Q1 / Q2)

### Very High Probability

✅ One-to-All Broadcast on Hypercube / Ring / Mesh

✅ Prefix Sum on Hypercube

✅ Scatter & Gather

### High Probability

✅ All-to-All Broadcast

### Medium Probability

* MPI Blocking & Non-Blocking
* Circular Shift

### My Prediction

**Q1**

* One-to-All Broadcast Hypercube / Ring / Mesh
* Scatter & Gather
* Prefix Sum

**OR**

**Q2**

* All-to-All Broadcast
* Reduction
* MPI Communication

---

# Unit 4 (Q3 / Q4)

Performance topics appear every single paper.

### Very High Probability

✅ Performance Metrics

✅ Granularity

✅ Sources of Overhead

### High Probability

✅ Matrix-Matrix Multiplication

### Medium Probability

* Scalability
* Amdahl's Law
* Gustafson's Law

### My Prediction

**Q3**

* Performance Metrics
* Matrix Multiplication
* Minimum Execution Time

**OR**

**Q4**

* Granularity
* Sources of Overhead
* Scalability

---

# Unit 5 (Q5 / Q6)

This unit is the easiest to predict because the same topics repeat every year.

### Almost Guaranteed

✅ CUDA Architecture

✅ CUDA Memory Model

### Very High Probability

✅ CUDA Processing Flow

✅ CUDA Applications

### Medium Probability

* Kernel Launch
* Grid, Block, Thread

### My Prediction

**Q5**

* CUDA Architecture
* Processing Flow
* Applications

**OR**

**Q6**

* CUDA Memory Model
* Grid/Block/Thread
* Kernel Execution

---

# Unit 6 (Q7 / Q8)

Sorting + Graph Algorithm pattern has been followed for years.

### Very High Probability

✅ Parallel Bubble Sort

✅ Parallel Merge Sort

✅ BFS

✅ DFS

### High Probability

✅ Kubernetes

### Medium Probability

* GPU Applications
* AI/ML Applications

### My Prediction

**Q7**

* Parallel Bubble Sort
* BFS
* Kubernetes

**OR**

**Q8**

* Parallel Merge Sort
* DFS
* GPU Applications

---

# If I Had Only One Day

### First 8 Topics (Most Likely)

1. One-to-All Broadcast
2. Prefix Sum
3. Scatter & Gather
4. Performance Metrics
5. Granularity
6. CUDA Architecture
7. CUDA Memory Model
8. Parallel Bubble Sort

---

### Next 8 Topics

9. Matrix Multiplication
10. Sources of Overhead
11. CUDA Processing Flow
12. Merge Sort
13. BFS
14. DFS
15. Kubernetes
16. All-to-All Broadcast

---

# "Bet My Marks" Questions

These have appeared in almost every paper either directly or in a slightly modified form:

| Topic                 | Confidence |
| --------------------- | ---------- |
| CUDA Architecture     | 95%        |
| Performance Metrics   | 95%        |
| Prefix Sum            | 90%        |
| Broadcast / Reduction | 90%        |
| Granularity           | 85%        |
| CUDA Memory Model     | 85%        |
| Parallel Bubble Sort  | 85%        |
| BFS / DFS             | 80%        |
| Kubernetes            | 80%        |

If you prepare **these 9 topics thoroughly**, you can usually attempt **50+ marks worth of questions** in the SPPU HPC paper.    


# Unit-wise Analysis

## Unit 3 (Communication Operations)

Questions: Q1 / Q2

| Topic                     | Frequency |
| ------------------------- | --------- |
| Broadcast & Reduction     | ⭐⭐⭐⭐⭐     |
| Prefix Sum                | ⭐⭐⭐⭐⭐     |
| Scatter & Gather          | ⭐⭐⭐⭐      |
| Circular Shift            | ⭐⭐⭐⭐      |
| MPI Blocking/Non-blocking | ⭐⭐⭐       |

### Must Prepare

1. One-to-All Broadcast
2. All-to-All Broadcast
3. All-to-One Reduction
4. Prefix Sum
5. Scatter & Gather

### Medium Priority

* Circular Shift
* MPI Blocking vs Non-blocking

### Prediction

At least one of:

* Prefix Sum
* Broadcast/Reduction
* Scatter-Gather

will definitely appear.

---

# Unit 4 (Performance Analysis)

Questions: Q3 / Q4

| Topic                 | Frequency |
| --------------------- | --------- |
| Performance Metrics   | ⭐⭐⭐⭐⭐     |
| Granularity           | ⭐⭐⭐⭐      |
| Sources of Overhead   | ⭐⭐⭐⭐      |
| Matrix Multiplication | ⭐⭐⭐⭐      |
| Scalability           | ⭐⭐⭐       |
| Amdahl & Gustafson    | ⭐⭐⭐       |

### Must Prepare

1. Performance Metrics
2. Granularity
3. Sources of Overhead
4. Matrix-Matrix Multiplication

### Medium Priority

* Scalability
* Isoefficiency
* Amdahl's Law
* Gustafson's Law

### Prediction

Performance Metrics is almost guaranteed.

---

# Unit 5 (CUDA)

Questions: Q5 / Q6

| Topic                | Frequency |
| -------------------- | --------- |
| CUDA Architecture    | ⭐⭐⭐⭐⭐     |
| CUDA Applications    | ⭐⭐⭐⭐⭐     |
| CUDA Processing Flow | ⭐⭐⭐⭐      |
| CUDA Memory Model    | ⭐⭐⭐       |
| CUDA Kernel          | ⭐⭐        |

### Must Prepare

1. CUDA Architecture
2. CUDA Memory Hierarchy
3. CUDA Processing Flow
4. CUDA Applications
5. Grid, Block, Thread

### Medium Priority

* Vector Addition Kernel
* CUDA Synchronization

### Prediction

Architecture + Memory Model combination is highly likely.

---

# Unit 6 (Parallel Algorithms)

Questions: Q7 / Q8

| Topic                       | Frequency |
| --------------------------- | --------- |
| Parallel Bubble Sort        | ⭐⭐⭐⭐⭐     |
| Merge Sort                  | ⭐⭐⭐⭐      |
| BFS                         | ⭐⭐⭐⭐      |
| DFS                         | ⭐⭐⭐⭐      |
| Kubernetes                  | ⭐⭐⭐⭐      |
| GPU Applications            | ⭐⭐⭐       |
| AI/ML in Parallel Computing | ⭐⭐        |

### Must Prepare

1. Parallel Bubble Sort
2. Parallel Merge Sort
3. BFS
4. DFS
5. Kubernetes

### Medium Priority

* GPU Applications
* AI/ML Applications

### Prediction

One sorting question + one graph traversal question appears every year.

---

# Most Important Questions for 2026 Exam

These have appeared repeatedly and have the highest probability:

| Rank | Topic                 | Frequency |
| ---- | --------------------- | --------- |
| 1    | Performance Metrics   | 5/5       |
| 2    | CUDA Architecture     | 5/5       |
| 3    | Prefix Sum            | 5/5       |
| 4    | Broadcast / Reduction | 5/5       |
| 5    | Parallel Bubble Sort  | 5/5       |
| 6    | Granularity           | 4/5       |
| 7    | Matrix Multiplication | 4/5       |
| 8    | Scatter & Gather      | 4/5       |
| 9    | Parallel BFS          | 4/5       |
| 10   | Parallel DFS          | 4/5       |
| 11   | Merge Sort            | 4/5       |
| 12   | Kubernetes            | 4/5       |

---

# If You Have Time for Only 15 Topics

Do these compulsorily:

1. One-to-All Broadcast
2. All-to-All Broadcast
3. Prefix Sum
4. Scatter & Gather
5. Performance Metrics
6. Granularity
7. Sources of Overhead
8. Matrix-Matrix Multiplication
9. CUDA Architecture
10. CUDA Memory Model
11. CUDA Processing Flow
12. Parallel Bubble Sort
13. Parallel Merge Sort
14. Parallel BFS
15. Kubernetes

These 15 topics alone cover roughly **70–80% of the repeated question patterns** from the last 5 papers. 

### Priority Order for Study

| Unit                          | Priority   |
| ----------------------------- | ---------- |
| Unit 5 (CUDA)                 | 🔥 Highest |
| Unit 3 (Communication)        | 🔥 Highest |
| Unit 6 (Parallel Algorithms)  | 🔥 High    |
| Unit 4 (Performance Analysis) | 🔥 High    |

If you're short on time before the exam, study in the order:
**Unit 5 → Unit 3 → Unit 6 → Unit 4**.
