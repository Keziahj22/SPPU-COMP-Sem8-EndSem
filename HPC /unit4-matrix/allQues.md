# UNIT SUMMARY FOR EXAM (Most Questions Repeat Around Same Core Concepts)

This entire unit can be grouped into **10 master answers**. If you understand these, you can answer almost every question.

---

# MASTER ANSWER 1

# Parallel Matrix Multiplication & Dense Matrix Algorithms

(Covers Q1, Q2, Q3, Q4, Q5, Q6)

---

## Introduction

Matrix operations are among the most important computations in parallel computing because they require a large number of arithmetic operations.

Applications include:

* Artificial Intelligence
* Machine Learning
* Image Processing
* Scientific Simulations
* Weather Forecasting

---

# A. Matrix–Matrix Multiplication

Consider:

[
C=A\times B
]

where

[
C_{ij}=\sum_{k=1}^{n} A_{ik}B_{kj}
]

Each element of matrix C is obtained by multiplying a row of A with a column of B.

---

## Example

[
A=
\begin{bmatrix}
1&2\
3&4
\end{bmatrix}
]

[
B=
\begin{bmatrix}
5&6\
7&8
\end{bmatrix}
]

Calculation:

[
C_{11}=1\times5+2\times7=19
]

[
C_{12}=1\times6+2\times8=22
]

[
C_{21}=3\times5+4\times7=43
]

[
C_{22}=3\times6+4\times8=50
]

Result:

[
C=
\begin{bmatrix}
19&22\
43&50
\end{bmatrix}
]

---

## Parallel Matrix Multiplication

Instead of one processor computing everything:

| Processor | Computes |
| --------- | -------- |
| P0        | C11      |
| P1        | C12      |
| P2        | C21      |
| P3        | C22      |

All processors work simultaneously.

---

## Advantages

* Faster execution
* Better processor utilization
* Scalable for large matrices
* Suitable for GPU computing

---

# B. Matrix–Vector Multiplication

[
Y=A\times X
]

where:

* A = Matrix
* X = Vector
* Y = Result Vector

---

## Example

[
A=
\begin{bmatrix}
1&2\
3&4
\end{bmatrix}
]

[
X=
\begin{bmatrix}
5\
6
\end{bmatrix}
]

Result:

[
Y=
\begin{bmatrix}
17\
39
\end{bmatrix}
]

---

# Row-wise 1D Partitioning

Rows divided among processors.

Example:

8 rows and 4 processors

| Processor | Assigned Rows |
| --------- | ------------- |
| P0        | 1–2           |
| P1        | 3–4           |
| P2        | 5–6           |
| P3        | 7–8           |

Each processor computes its rows independently.

---

### Advantages

* Simple implementation
* Less communication
* Easy load distribution

---

# 2D Partitioning

Matrix divided into blocks.

Example:

```
A11 A12
A21 A22
```

Each block assigned to a processor.

---

### Advantages

* Better load balancing
* Better scalability
* Suitable for large matrices

---

# Comparison of 1D and 2D Partitioning

| Parameter      | 1D       | 2D     |
| -------------- | -------- | ------ |
| Complexity     | Low      | High   |
| Communication  | Low      | High   |
| Scalability    | Moderate | High   |
| Load Balancing | Average  | Better |

---

# Dense Matrix Algorithms

Dense Matrix:

Most entries are non-zero.

Example:

[
\begin{bmatrix}
2&4&5\
3&6&7\
1&8&9
\end{bmatrix}
]

Important operations:

1. Matrix Vector Multiplication
2. Matrix Matrix Multiplication

---

## Conclusion

Parallel matrix algorithms reduce computation time by dividing matrix operations among processors and are widely used in scientific and engineering applications.

---

# MASTER ANSWER 2

# Performance Metrics

(Covers Q7–Q12)

---

## Introduction

Performance metrics evaluate the effectiveness and efficiency of parallel systems.

---

# 1. Execution Time

Time required to complete a task.

[
T_p
]

Smaller execution time indicates better performance.

---

# 2. Speedup

Measures improvement due to parallelization.

[
Speedup=\frac{T_s}{T_p}
]

where:

Ts = Sequential Time

Tp = Parallel Time

---

### Example

Ts = 100 sec

Tp = 20 sec

[
S=\frac{100}{20}=5
]

System is 5 times faster.

---

# 3. Efficiency

Measures processor utilization.

[
E=\frac{Speedup}{P}
]

where P = Number of processors.

---

### Example

Speedup = 8

Processors = 10

[
E=0.8
]

80% efficiency.

---

# 4. Cost

Total resources consumed.

[
Cost=P\times T_p
]

---

# 5. Throughput

Number of tasks completed per unit time.

Higher throughput means better system performance.

---

# 6. Parallel Overhead

Extra work introduced by parallelization.

[
Overhead=P\times T_p-T_s
]

---

## Conclusion

Execution Time, Speedup, Efficiency, Cost, Throughput, and Overhead are the most important metrics used to evaluate parallel systems.

---

# MASTER ANSWER 3

# Minimum Execution Time & Cost Optimality

(Covers Q13–Q16)

---

## Minimum Execution Time

Minimum possible time to solve a problem using maximum parallelism.

---

# Adding n Numbers

Example:

8 numbers

```
1 2 3 4 5 6 7 8
```

---

### Level 1

4 additions

```
3 7 11 15
```

---

### Level 2

2 additions

```
10 26
```

---

### Level 3

1 addition

```
36
```

---

Total levels:

[
\log_2 n
]

Execution Time:

[
O(\log n)
]

---

# Cost Optimality

A parallel algorithm is cost-optimal if:

[
Cost=Sequential\ Complexity
]

or

[
P\times T_p=T_s
]

---

### For Adding n Numbers

Sequential:

[
O(n)
]

Parallel:

[
T_p=O(\log n)
]

Processors:

[
P=O(n/\log n)
]

Cost:

[
P\times T_p
]

[
=(n/\log n)\times \log n
]

[
=O(n)
]

Thus cost-optimal.

---

## Conclusion

Tree reduction achieves minimum execution time and cost-optimal performance.

---

# MASTER ANSWER 4

# Granularity

(Covers Q17–Q21)

---

## Definition

Granularity is the amount of computation performed before communication occurs.

---

# Fine-Grained Parallelism

Small tasks assigned.

Communication is frequent.

Example:

Pixel-level image processing.

---

### Advantages

* Better load balancing
* More parallelism

### Disadvantages

* High communication overhead
* High synchronization cost

---

# Coarse-Grained Parallelism

Large tasks assigned.

Communication less frequent.

Example:

Different neural networks trained independently.

---

### Advantages

* Lower overhead
* Higher efficiency

### Disadvantages

* Load imbalance possible

---

# Effect of Granularity

Too Fine:

* Excessive communication
* Reduced performance

Too Coarse:

* Processor idle time

Balanced Granularity:

* Best performance

---

# Granularity for Adding n Numbers

If every addition is assigned separately:

Fine-grained.

Communication increases.

If groups are assigned:

Coarse-grained.

Communication decreases.

---

## When Fine-Grained is Preferred

* Large number of processors
* Highly parallel problems
* Dynamic workloads

---

# MASTER ANSWER 5

# Parallel Overheads

(Covers Q22–Q24)

---

## Definition

Extra time spent because of parallelization.

---

# Sources of Overhead

### 1. Communication Overhead

Data exchange among processors.

---

### 2. Synchronization Overhead

Waiting for other processors.

---

### 3. Load Imbalance

Unequal distribution of work.

---

### 4. Process Creation Overhead

Thread/process generation cost.

---

### 5. Memory Contention

Processors competing for memory.

---

# Reducing Overhead

* Minimize communication
* Use efficient scheduling
* Improve load balancing
* Reduce synchronization points
* Use faster networks

---

# MASTER ANSWER 6

# Scalability & Isoefficiency

(Covers Q25–Q29)

---

## Scalability

Ability of a system to maintain performance as processors increase.

---

# Strong Scalability

Problem size fixed.

Processors increase.

Execution time should decrease.

---

# Weak Scalability

Problem size increases with processors.

Execution time should remain constant.

---

# Factors Limiting Scalability

1. Communication overhead
2. Synchronization delays
3. Sequential portions
4. Load imbalance

---

# Isoefficiency Metric

Measures scalability.

Shows how much problem size must increase to maintain constant efficiency.

---

## Perfect Scalability

Isoefficiency = 1

Meaning:

Problem size increases at the same rate as processors.

Efficiency remains constant.

---

# MASTER ANSWER 7

# Amdahl's Law & Gustafson's Law

(Covers Q30–Q32)

---

# Amdahl's Law

States that a program always contains a sequential part.

This limits speedup.

Formula:

[
Speedup=\frac1{S+\frac{1-S}{P}}
]

where:

S = Sequential Fraction

P = Processors

---

### Interpretation

Even with infinite processors:

[
Max\ Speedup=\frac1S
]

Sequential part becomes bottleneck.

---

# Gustafson's Law

Assumes problem size grows with processors.

Formula:

[
Speedup=P-S(P-1)
]

---

# Comparison

| Amdahl                | Gustafson          |
| --------------------- | ------------------ |
| Fixed Problem         | Increasing Problem |
| Pessimistic           | Optimistic         |
| Limited Speedup       | Higher Speedup     |
| Sequential Bottleneck | Better Utilization |

---

# MASTER ANSWER 8

# Asymptotic Analysis

(Covers Q33)

---

## Definition

Studies growth rate of algorithms for large input sizes.

Machine-independent analysis.

---

# Notations

### Big O

Upper Bound

[
O(n^2)
]

Worst Case.

---

### Omega

Lower Bound

[
\Omega(n)
]

Best Case.

---

### Theta

Exact Bound

[
\Theta(n\log n)
]

---

# Importance

* Compare algorithms
* Predict scalability
* Analyze performance

---

# MASTER ANSWER 9

# Scaling Down (Downsizing)

(Covers Q34)

---

## Definition

Reducing number of processors when workload decreases.

---

## Example

Earlier:

100 processors used.

Smaller workload arrives.

Use 20 processors instead.

---

## Advantages

* Reduced cost
* Reduced power consumption
* Better utilization

---

## Applications

* Cloud Computing
* Data Centers
* HPC Systems

---

# MASTER ANSWER 10

# Communication & Basic Parallel Computing

(Covers Q35–Q42)

---

# Circular Shift

Data moved from one processor to its neighboring processor.

Example:

Before:

```
P0=A
P1=B
P2=C
P3=D
```

After:

```
P0=D
P1=A
P2=B
P3=C
```

---

# Circular Shift on Mesh

Processors arranged in rows and columns.

Example:

```
P0 P1 P2
P3 P4 P5
P6 P7 P8
```

Communication occurs through neighboring nodes.

Advantages:

* Simple
* Low cost

Disadvantages:

* More communication steps

---

# Circular Shift on Hypercube

Processors connected according to binary addresses.

For n dimensions:

[
2^n
]

processors.

Example:

3D Hypercube

[
2^3=8
]

nodes.

Advantages:

* Fast communication
* Fewer steps

Disadvantages:

* Complex structure

---

# Mesh vs Hypercube

| Feature             | Mesh     | Hypercube              |
| ------------------- | -------- | ---------------------- |
| Structure           | Grid     | Multi-dimensional Cube |
| Diameter            | High     | Low                    |
| Communication Speed | Lower    | Higher                 |
| Scalability         | Moderate | Excellent              |

---

# Improving Communication Speed

1. Reduce communication frequency
2. Increase bandwidth
3. Better topology
4. Shared memory
5. Overlap computation and communication
6. Reduce synchronization

---

# Basic Parallel Computing Concepts

### Parallel Computing

Using multiple processors simultaneously to solve a problem.

---

### Processor/Core

Processing unit performing computations.

---

### Sequential Execution

One instruction at a time.

---

### Parallel Execution

Multiple instructions simultaneously.

---

### Bottleneck

Part limiting overall performance.

Examples:

* Sequential code
* Communication delay
* Memory access delay

---

# 2-MARK KEYWORDS FOR ANY ANSWER

Write these somewhere in long answers:

* Parallelism
* Load Balancing
* Scalability
* Processor Utilization
* Communication Overhead
* Synchronization
* Speedup
* Efficiency
* Cost Optimality
* Throughput
* Granularity
* Tree Reduction
* Strong Scalability
* Weak Scalability
* Amdahl's Law
* Gustafson's Law
* Isoefficiency
* Hypercube
* Mesh Network
* Bottleneck

These keywords alone often fetch 1–2 extra marks because examiners look for standard parallel computing terminology.
