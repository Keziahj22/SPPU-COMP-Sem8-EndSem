This question bank covers almost the **entire Unit 3 (Parallel Communication)**. Instead of memorizing 33 separate answers, focus on **12 core topics** because many questions are repeated in different forms.

---

# PRIORITY 1 (VERY HIGH) ⭐⭐⭐⭐⭐

These are asked repeatedly and can come for 7–10 marks.

---

# Q1. What is One-to-All Broadcast?

## Definition

One-to-All Broadcast is a collective communication operation in which one source processor (root) sends the same message to all processors in the system.

### Diagram

```text
        P0 (Root)
      /    |    \
     /     |     \
   P1     P2     P3
```

After Broadcast:

```text
P0 = M
P1 = M
P2 = M
P3 = M
```

---

## Applications

* Matrix multiplication
* Parallel sorting
* Distributed databases
* Scientific simulations

---

## Cost

[
T=\log_2(p)(t_s+t_wm)
]

Where:

* p = processors
* ts = startup time
* tw = transfer time/word
* m = message size

---

## Advantages

* Efficient data distribution
* Reduces redundant communication

---

## Conclusion

Broadcast spreads identical data from one process to all processes.

---

# Q2. One-to-All Broadcast on Hypercube

(Extremely Important)

---

## Hypercube Overview

For d-dimensional hypercube:

[
p=2^d
]

Example:

8 Nodes → 3D Hypercube

```text
000 ----- 001
 |         |
010 ----- 011

 |         |

100 ----- 101
 |         |
110 ----- 111
```

---

## Algorithm

At each dimension:

```text
neighbor = node XOR 2^i
```

where

```text
i = 0,1,2,...,d-1
```

---

## Example (8 Nodes)

Source = 000

### Step 1

```text
000 → 001
```

---

### Step 2

```text
000 → 010
001 → 011
```

---

### Step 3

```text
000 → 100
001 → 101
010 → 110
011 → 111
```

All nodes receive message.

---

## Cost Analysis

Steps:

[
\log_2(p)
]

Cost:

[
T=\log_2(p)(t_s+t_wm)
]

---

## Advantages

* Fastest broadcast topology
* Scalable
* Low diameter

---

# Q3. One-to-All Broadcast on 8-Node Ring using Recursive Doubling

---

## Ring Topology

```text
      P0
    /    \
   P7    P1
   |      |
   P6    P2
    \    /
      P5
       |
      P4
       |
      P3
```

---

## Step 1

```text
P0 → P1
P0 → P7
```

Nodes informed = 3

---

## Step 2

```text
P1 → P2
P7 → P6
```

Nodes informed = 5

---

## Step 3

```text
P2 → P3
P6 → P5
```

Nodes informed = 7

---

## Step 4

```text
P3 → P4
```

All informed.

---

## Cost

Ring diameter:

[
\frac{p}{2}
]

Cost:

[
T \approx \frac{p}{2}(t_s+t_wm)
]

---

# Q4. One-to-All Broadcast on 16-Node Mesh

(Important Numerical)

---

## Mesh Arrangement

```text
P0  P1  P2  P3
P4  P5  P6  P7
P8  P9 P10 P11
P12 P13 P14 P15
```

---

## Phase 1

Row Broadcast

```text
P0 → P1 → P2 → P3
```

---

## Phase 2

Column Broadcast

```text
P0 ↓ P4 ↓ P8 ↓ P12

P1 ↓ P5 ↓ P9 ↓ P13

P2 ↓ P6 ↓ P10 ↓ P14

P3 ↓ P7 ↓ P11 ↓ P15
```

---

## Complexity

Mesh dimension:

[
\sqrt{p}
]

Cost:

[
O(\sqrt p)
]

---

# Q6. All-to-All Broadcast

(Repeatedly Asked)

---

## Definition

Each processor sends its data to every other processor.

---

### Before

```text
P0=A
P1=B
P2=C
P3=D
```

---

### After

```text
P0=ABCD
P1=ABCD
P2=ABCD
P3=ABCD
```

---

## Ring Algorithm

Communication occurs in p−1 phases.

Example:

Phase 1

```text
P0→P1
P1→P2
P2→P3
P3→P0
```

Phase 2

Repeat forwarding.

---

## Cost

[
T=(p-1)(t_s+t_wm)
]

---

# Q12. All-to-One Reduction

---

## Definition

All processors send data to one destination processor and combine values.

Operations:

* SUM
* MAX
* MIN
* PRODUCT

---

### Example

```text
P0=10
P1=20
P2=30
P3=40
```

SUM:

```text
Result = 100
```

---

## Recursive Doubling

Step 1

```text
P1→P0
P3→P2
```

Step 2

```text
P2→P0
```

Final:

```text
P0=100
```

---

## Cost

[
T=\log_2(p)(t_s+t_wm)
]

---

# PRIORITY 2 ⭐⭐⭐⭐

---

# Q15. Scatter Operation

## Definition

Root divides data into pieces and distributes different portions.

---

### Example

Root:

```text
[10 20 30 40]
```

After Scatter

```text
P0=10
P1=20
P2=30
P3=40
```

---

### Diagram

```text
         Root
      /   |   \
    P0   P1   P2   P3
```

---

## MPI Function

```c
MPI_Scatter()
```

---

## Applications

* Load balancing
* Parallel search
* Data partitioning

---

# Q16. Gather Operation

## Definition

All processes send results to root process.

---

### Diagram

```text
P0 \
P1  \
P2 ---> Root
P3  /
```

---

## MPI Function

```c
MPI_Gather()
```

---

## Applications

* Result collection
* Parallel reduction

---

# Q19. Prefix Sum Operation

(Important)

---

## Definition

Computes cumulative sum.

---

### Example

Input

```text
1 2 3 4
```

Output

```text
1 3 6 10
```

---

## Formula

[
Prefix(i)=\sum_{j=0}^{i} a_j
]

---

## Applications

* Sorting
* GPU algorithms
* Graph processing

---

# Q20. Prefix Sum on 8-Node Hypercube

---

Values

```text
P0=1
P1=2
P2=3
P3=4
P4=5
P5=6
P6=7
P7=8
```

---

Final Prefix Sums

```text
1
3
6
10
15
21
28
36
```

---

## Steps

Dimension 0 exchange

Dimension 1 exchange

Dimension 2 exchange

Total:

[
\log_2(8)=3
]

steps.

---

# PRIORITY 3 ⭐⭐⭐

---

# Q22. Circular Shift Operation

---

## Definition

Data rotates among processors.

---

### Right Shift

```text
Pi → P(i+1) mod N
```

Example:

```text
P0→P1
P1→P2
P2→P3
P3→P0
```

---

### Left Shift

```text
Pi → P(i−1+N) mod N
```

---

## Applications

* Load balancing
* Matrix algorithms
* Data movement

---

# Q25. Blocking Communication using MPI

---

## Definition

Process waits until communication completes.

---

### MPI Functions

```c
MPI_Send()
MPI_Recv()
```

---

### Diagram

```text
P0 ----Send----> P1

Wait            Wait
```

---

## Advantages

* Easy programming
* Easy debugging

---

## Disadvantages

* CPU idle time
* Deadlock possible

---

# Q26. Non-Blocking Communication using MPI

(VERY IMPORTANT)

---

## Definition

Communication begins and process continues execution.

---

## MPI Functions

```c
MPI_Isend()
MPI_Irecv()
MPI_Wait()
MPI_Test()
```

---

### Diagram

```text
P0 starts send
↓
Computes simultaneously

P1 starts receive
↓
Computes simultaneously
```

---

## Advantages

* Better utilization
* Overlap computation and communication

---

## Disadvantages

* More complex

---

# Q29. MPI_Isend() and MPI_Irecv()

## MPI_Isend()

Starts send and immediately returns.

```c
MPI_Isend(buffer,count,
datatype,dest,
tag,comm,&request);
```

---

## MPI_Irecv()

Starts receive and immediately returns.

```c
MPI_Irecv(buffer,count,
datatype,source,
tag,comm,&request);
```

---

## Completion

```c
MPI_Wait(&request,&status);
```

or

```c
MPI_Test()
```

---

# Q31. All-to-All Personalized Communication on 3D Hypercube

(Important Long Answer)

---

## Definition

Each processor sends different data to every other processor.

Unlike broadcast, messages are unique.

---

## Example

```text
P0 → P1 : A
P0 → P2 : B
P0 → P3 : C
```

Different messages.

---

## Hypercube Algorithm

For each dimension:

```text
partner = node XOR 2^i
```

Exchange data with partner.

---

### 8-Node Hypercube

Dimension 0

```text
000 ↔ 001
010 ↔ 011
100 ↔ 101
110 ↔ 111
```

---

Dimension 1

```text
000 ↔ 010
001 ↔ 011
100 ↔ 110
101 ↔ 111
```

---

Dimension 2

```text
000 ↔ 100
001 ↔ 101
010 ↔ 110
011 ↔ 111
```

---

## Complexity

[
O(\log p)
]

communication rounds.

---

# Q32 & Q33. Improving Communication Speed

(Theory Question)

## Methods

### 1. Use Non-Blocking Communication

Overlap communication and computation.

---

### 2. Minimize Message Count

Send fewer large messages instead of many small messages.

---

### 3. Use Efficient Topologies

Hypercube:

[
O(\log p)
]

Mesh:

[
O(\sqrt p)
]

Ring:

[
O(p)
]

---

### 4. Use Collective Communication

* MPI_Bcast()
* MPI_Reduce()
* MPI_Gather()

Optimized internally.

---

### 5. Reduce Synchronization

Avoid unnecessary waiting.

---

### 6. Load Balancing

Equal work distribution avoids communication bottlenecks.

---

# Most Important Questions for Exam

**Must Prepare (Almost Guaranteed Topic Area)**

1. One-to-All Broadcast on Hypercube ⭐⭐⭐⭐⭐
2. Broadcast on Mesh ⭐⭐⭐⭐⭐
3. All-to-All Broadcast ⭐⭐⭐⭐⭐
4. All-to-One Reduction ⭐⭐⭐⭐⭐
5. Prefix Sum on Hypercube ⭐⭐⭐⭐⭐
6. Scatter & Gather ⭐⭐⭐⭐
7. Blocking vs Non-Blocking MPI ⭐⭐⭐⭐⭐
8. MPI_Isend(), MPI_Irecv(), MPI_Wait() ⭐⭐⭐⭐
9. Personalized Communication on Hypercube ⭐⭐⭐⭐
10. Improving Communication Speed ⭐⭐⭐⭐

If you prepare these 10 thoroughly, you can answer almost every Unit 3 question from your list.
