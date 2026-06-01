# UNIT 6 HPC APPLICATIONS – EXAM ANSWERS (5–10 MARKS)

---

# PART 1: PARALLEL SORTING ALGORITHMS

---

# Q1-Q4. Odd-Even Transposition Sort / Parallel Bubble Sort / Comparison

(One answer can be written for all these questions)

## Introduction

Odd-Even Transposition Sort is a parallel version of Bubble Sort. Instead of comparing one pair at a time, multiple adjacent pairs are compared simultaneously using multiple processors.

The algorithm alternates between:

1. Even Phase
2. Odd Phase

until the array becomes sorted.

---

## Working

Consider:

```text
8 4 6 2
```

### Step 1: Even Phase

Compare simultaneously:

```text
(8,4) and (6,2)
```

After swap:

```text
4 8 2 6
```

---

### Step 2: Odd Phase

Compare:

```text
(8,2)
```

After swap:

```text
4 2 8 6
```

---

### Step 3: Even Phase

Compare:

```text
(4,2) and (8,6)
```

After swap:

```text
2 4 6 8
```

Sorted.

---

## Algorithm

```text
for phase = 1 to n
    if phase is even
       compare (0,1),(2,3),(4,5)
    else
       compare (1,2),(3,4),(5,6)

    perform swaps in parallel
```

---

## Parallel Formulation

Suppose n processors exist.

Processor P1:

```text
compare A[0],A[1]
```

Processor P2:

```text
compare A[2],A[3]
```

Processor P3:

```text
compare A[4],A[5]
```

All execute simultaneously.

---

## Complexity Analysis

### Sequential Bubble Sort

```text
O(n²)
```

---

### Parallel Bubble Sort

With enough processors:

```text
O(n)
```

Limited processors:

```text
O(n²/p)
```

where p = number of processors.

---

## Advantages

* Simple implementation
* Good parallelism
* Suitable for distributed systems

---

## Disadvantages

* Large number of phases
* Not efficient for huge datasets

---

## Comparison Table

| Feature         | Sequential    | Parallel     |
| --------------- | ------------- | ------------ |
| Processors      | 1             | Multiple     |
| Comparisons     | One at a time | Simultaneous |
| Complexity      | O(n²)         | O(n)         |
| Speed           | Slow          | Faster       |
| CPU Utilization | Low           | High         |

---

# Q5-Q7. Parallel Merge Sort / Short Note / Comparison

(One answer covers all 3 questions)

---

## Introduction

Parallel Merge Sort is a Divide-and-Conquer sorting algorithm in which different processors sort different parts of the array simultaneously.

It is highly scalable and commonly used in parallel systems.

---

## Working

Array:

```text
8 4 6 2
```

---

### Divide

```text
8 4 | 6 2
```

---

### Parallel Sort

Processor P1:

```text
8 4 → 4 8
```

Processor P2:

```text
6 2 → 2 6
```

---

### Merge

```text
4 8 + 2 6
```

↓

```text
2 4 6 8
```

---

## Algorithm

```text
ParallelMergeSort(A)

if size <=1
   return

divide array into left and right

sort left half in Processor P1

sort right half in Processor P2

merge both sorted halves
```

---

## Complexity

### Sequential Merge Sort

```text
O(n log n)
```

---

### Parallel Merge Sort

```text
O(log² n)
```

---

### Limited Processors

```text
O((n log n)/p)
```

---

## Advantages

* Faster execution
* Excellent scalability
* Suitable for large datasets

---

## Disadvantages

* Communication overhead
* Merge operation may become costly

---

## Comparison

| Feature     | Sequential | Parallel     |
| ----------- | ---------- | ------------ |
| Processor   | One        | Many         |
| Sorting     | Sequential | Simultaneous |
| Complexity  | O(n log n) | O(log² n)    |
| Scalability | Low        | High         |

---

# Q8. Recursive Decomposition in Parallel Quick Sort

## Introduction

Parallel Quick Sort uses Divide-and-Conquer and Recursive Decomposition.

The large array is recursively divided into smaller subarrays, and multiple processors sort them simultaneously.

---

## Working

Array:

```text
9 4 8 2 7
```

Choose pivot = 7

Partition:

```text
4 2 | 7 | 9 8
```

---

Processor P1 sorts:

```text
4 2
```

Processor P2 sorts:

```text
9 8
```

simultaneously.

---

## Recursive Decomposition

```text
Array
 ↓
Partition
 ↓
Left Subarray      Right Subarray
 ↓                    ↓
Processor P1      Processor P2
 ↓                    ↓
Recursive Sort
```

---

## Advantages

### Natural Parallelism

Independent subarrays can be processed separately.

### Faster Execution

Multiple processors work simultaneously.

### Scalability

Works efficiently on large parallel systems.

---

## Complexity

Sequential:

```text
O(n log n)
```

Parallel:

```text
O((n log n)/p)
```

approximately.

---

# Q9. Shared Address Space vs Message Passing Quick Sort

## Shared Address Space Formulation

All processors share common memory.

```text
P1
P2 ---> Shared Memory
P3
```

### Advantages

* Easy communication
* Fast data access

### Disadvantages

* Memory conflicts
* Synchronization needed

---

## Message Passing Formulation

Each processor has its own memory.

```text
P1 ↔ P2 ↔ P3
```

Data exchanged using messages.

---

### Advantages

* Better scalability
* No memory conflicts

### Disadvantages

* Communication overhead

---

## Comparison Table

| Feature         | Shared Memory | Message Passing |
| --------------- | ------------- | --------------- |
| Memory          | Common        | Separate        |
| Communication   | Direct        | Messages        |
| Synchronization | High          | Low             |
| Scalability     | Moderate      | High            |
| Memory Conflict | Possible      | Not Possible    |

---

# Q10. Issues in Sorting on Parallel Computers

## Introduction

Although parallel sorting increases speed, several challenges affect performance.

---

## Major Issues

### 1. Load Balancing

Some processors receive more work than others.

Example:

```text
P1 → 100 elements
P2 → 10 elements
```

P2 becomes idle.

---

### 2. Communication Overhead

Processors spend time exchanging data.

---

### 3. Synchronization Delay

Processors wait for slow processors.

---

### 4. Data Dependency

One operation depends on another.

---

### 5. Memory Conflicts

Multiple processors access same memory location.

---

### 6. Scalability Issues

Adding processors may not always improve performance.

---

### 7. Merging Complexity

Combining sorted subarrays requires extra time.

---

### 8. Network Latency

Slow network increases communication delay.

---

# PART 2: PARALLEL BFS & DFS

---

# Q11. Parallel DFS

## Introduction

Depth First Search explores one branch completely before backtracking.

Parallel DFS allows multiple processors to explore different branches simultaneously.

---

## Example

```text
       A
      / \
     B   C
    / \ / \
   D  E F  G
```

P1 explores:

```text
A → B → D → E
```

P2 explores:

```text
A → C → F → G
```

simultaneously.

---

## Components

* Shared Stack
* Visited Array
* Load Balancing

---

## Algorithm

```text
Push source node

while stack not empty

Processor takes node

mark visited

push neighbors

repeat
```

---

## Advantages

* Faster graph traversal
* Better CPU utilization

---

## Complexity

Sequential:

```text
O(V+E)
```

Parallel:

```text
O((V+E)/P)
```

---

# Q12-Q14. Parallel BFS / Short Note / Complexity Analysis

(One answer for all)

---

## Introduction

Breadth First Search explores a graph level by level.

Parallel BFS processes all nodes of the same level simultaneously.

---

## Example

```text
       A
      / \
     B   C
    / \ / \
   D  E F  G
```

Level 0:

```text
A
```

Level 1:

```text
B C
```

Level 2:

```text
D E F G
```

Processors work simultaneously on same level.

---

## Frontier Queue

Stores current level nodes.

```text
Current Frontier
        ↓
Next Frontier
```

---

## Algorithm

```text
Insert source node

while frontier not empty

assign frontier nodes
to processors

explore neighbors

build next frontier

synchronize

repeat
```

---

## Complexity

Sequential:

```text
O(V+E)
```

Parallel:

```text
O((V+E)/P)
```

---

## Advantages

* Faster graph exploration
* Suitable for large graphs
* Better resource utilization

---

# Q15. Communication Strategies in Parallel BFS

## Need

Processors must communicate to:

* Share discovered nodes
* Update frontier queue
* Avoid duplicate visits

---

## Types

### Frontier-Based Communication

Exchange only frontier nodes.

---

### Message Passing

Processors exchange messages.

---

### Shared Memory

Common visited array.

---

### Synchronization

Barrier after every level.

---

## Benefits

* Correct traversal
* Efficient load balancing
* Reduced duplicate work

---

# PART 3: COMMUNICATION STRATEGIES

---

# Q16. Random Communication Strategy

Processors randomly exchange tasks or graph nodes.

Example:

```text
P1 ↔ P4
P2 ↔ P5
```

---

## Advantages

* Easy implementation
* Good load balancing

---

## Limitation

High communication overhead.

---

# Q17. Ring Communication Strategy

Processors connected in circular ring.

```text
P1 → P2 → P3 → P4
↑               ↓
← ← ← ← ← ← ← ←
```

---

## Advantages

* Controlled communication
* Less network congestion

---

## Limitation

Slow information propagation.

---

# Q18. Blackboard Communication Strategy

All processors communicate through shared memory called Blackboard.

```text
        Blackboard
      /  |  |  \
    P1  P2 P3 P4
```

---

## Advantages

* Better coordination
* Dynamic load balancing

---

## Limitation

Synchronization overhead.

---

# PART 4: KUBERNETES

---

# Q19-Q23. Kubernetes / Framework / Features / Container Orchestration

(One master answer)

## Definition

Kubernetes (K8s) is an open-source container orchestration platform developed by Google to automate deployment, scaling, monitoring, and management of containers.

---

## Architecture

```text
            Control Plane

       API Server
       Scheduler
       Controller Manager
       etcd

               |
     ---------------------
     |                   |

 Worker Node         Worker Node

 Pods                Pods
 Kubelet             Kubelet
 Kube-proxy          Kube-proxy
```

---

## Components

### API Server

Entry point for requests.

### Scheduler

Assigns Pods to nodes.

### Controller Manager

Maintains desired state.

### etcd

Stores cluster information.

### Pods

Smallest deployment unit.

### Kubelet

Communicates with master.

### Kube-proxy

Handles networking.

---

## Features

* Load Balancing
* Self Healing
* Auto Scaling
* Automated Deployment
* Storage Orchestration
* Service Discovery
* Portability

---

## Applications

* DevOps / CI-CD
* Cloud Computing
* AI/ML Systems
* Big Data Analytics
* IoT
* Web Hosting

---

## Container Orchestration

Automatic management of containers.

Functions:

* Deployment
* Scaling
* Load Balancing
* Self-Healing
* Rolling Updates
* Rollback

---

# PART 5: DISTRIBUTED COMPUTING

---

# Q24-Q25. Distributed Computing for Document Classification

## Definition

Document Classification automatically assigns documents into predefined categories.

Examples:

```text
Sports
Health
Business
Education
```

---

## Algorithms Used

* KNN
* Naive Bayes
* SVM
* Neural Networks

---

## Distributed Classification Process

### Step 1

Divide dataset.

### Step 2

Assign partitions to nodes.

### Step 3

Nodes classify documents simultaneously.

### Step 4

Collect and combine results.

---

## Advantages

* Faster processing
* Better scalability
* Efficient resource utilization

---

## Applications

* Email filtering
* News categorization
* Spam detection
* Search engines

---

# PART 6: GPU & AI/ML

---

# Q26. GPU Applications

## Definition

GPU (Graphics Processing Unit) contains thousands of cores designed for parallel processing.

---

## Applications

1. Gaming & Graphics
2. Deep Learning
3. Scientific Simulations
4. Medical Imaging
5. Video Rendering
6. Cryptocurrency Mining
7. Autonomous Vehicles

---

## Benefits

* Massive parallelism
* High throughput
* Faster computation

---

# Q27-Q28. Parallel Computing for AI/ML

## Need

AI/ML models process huge datasets and billions of parameters.

Parallel computing reduces training time.

---

## Uses

### Faster Model Training

Multiple GPUs train simultaneously.

### Distributed Learning

Training across many machines.

### Big Data Processing

Handle huge datasets.

### Real-Time AI

Speech recognition, autonomous vehicles.

---

## Advantages

* Faster computation
* Reduced training time
* Better scalability
* Improved performance

---

# PART 7: PRAM

---

# Q29. CRCW PRAM

## Definition

CRCW = Concurrent Read Concurrent Write.

It is a PRAM (Parallel Random Access Machine) model where multiple processors can read and write the same memory location simultaneously.

---

## Structure

```text
P1
P2 ---> Shared Memory
P3
P4
```

---

## Features

* Shared memory model
* Concurrent read
* Concurrent write
* High parallelism

---

## Advantages

* Fast execution
* Simple programming model
* Efficient resource sharing

---

## Applications

* Sorting
* Searching
* Graph Algorithms
* Scientific Computing

---

# UNIVERSAL HPC POINTS (Write in Any Answer)

Add 3–4 of these at the end of almost every Unit-6 answer:

✅ Improves speedup and throughput.

✅ Utilizes multiple processors simultaneously.

✅ Reduces execution time.

✅ Provides scalability for large datasets.

✅ Improves resource utilization.

✅ Supports distributed and parallel processing.

✅ Suitable for large-scale scientific and industrial applications.

✅ Communication and synchronization overhead are important performance factors.

These generic points make a 5-mark answer look like a 7–8 mark answer in HPC exams.
