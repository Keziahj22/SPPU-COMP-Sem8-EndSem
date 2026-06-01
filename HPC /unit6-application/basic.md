# Unit 6 – HPC Applications (Exam-Oriented Detailed Notes)

---

# 1. Parallel DFS (Depth First Search)

## What is DFS?

DFS explores a graph by going as deep as possible along one branch before backtracking.

Example:

```
A
├── B
│   ├── D
│   └── E
└── C
    └── F
```

Traversal:

```
A → B → D → E → C → F
```

---

## Sequential DFS

Uses:

* Stack
* Recursion
* Visited Array

Complexity:

[
O(V+E)
]

where

* V = Vertices
* E = Edges

---

## Parallel DFS

Idea:

Different processors explore different branches simultaneously.

Example:

```
        A
      /   \
     B     C
    / \   / \
   D  E  F  G
```

Processor P1:

```
A → B → D → E
```

Processor P2:

```
A → C → F → G
```

Both run simultaneously.

---

## Components

### Shared Stack

Stores unexplored nodes.

### Visited Array

Prevents revisiting nodes.

### Load Balancing

Idle processors take work from busy processors.

---

## Advantages

✔ Faster execution

✔ Better CPU utilization

✔ Suitable for large graphs

---

## Complexity

Sequential:

[
O(V+E)
]

Parallel:

[
O((V+E)/P)
]

where P = number of processors

---

# 2. Parallel BFS (Breadth First Search)

## What is BFS?

Explores graph level by level.

Example:

```
        A
      /   \
     B     C
    / \   / \
   D  E  F  G
```

Traversal:

```
A → B → C → D → E → F → G
```

---

## Sequential BFS

Uses Queue.

Complexity:

[
O(V+E)
]

---

## Parallel BFS

All nodes at same level are processed simultaneously.

Example:

Level 0:

```
A
```

Level 1:

```
B C
```

Level 2:

```
D E F G
```

Processors:

```
P1 → B
P2 → C
P3 → D
P4 → E
...
```

---

## Frontier Queue

Stores current level nodes.

```
Current Frontier → Next Frontier
```

---

## Synchronization

Required after every level.

Reason:

All processors must finish current level before next level begins.

---

## Complexity

Sequential:

[
O(V+E)
]

Parallel:

[
O((V+E)/P)
]

---

# 3. Communication Strategies in BFS

Purpose:

Processors must communicate to:

### 1. Share discovered nodes

Example:

Processor 1 finds node X.

Processor 2 should know X is already visited.

---

### 2. Update Frontier

New nodes added to next level queue.

---

### 3. Avoid Duplicate Visits

Prevents repeated work.

---

## Types

### A) Frontier-Based Communication

Processors exchange frontier nodes only.

Efficient for large graphs.

---

### B) Message Passing

Processors send messages.

```
P1 → P2
```

Used in clusters.

---

### C) Shared Memory

Common memory area.

All processors access same visited array.

---

### D) Synchronization

Barrier after each level.

Ensures correctness.

---

# 4. Random Communication Strategy

Processors randomly exchange nodes.

Example:

```
P1 ↔ P4
P2 ↔ P5
P3 ↔ P1
```

---

## Advantages

* Good load balancing
* Easy implementation

---

## Limitation

Large communication overhead.

---

# 5. Ring Communication Strategy

Processors arranged in ring.

```
P1 → P2 → P3 → P4
↑             ↓
← ← ← ← ← ← ←
```

Each processor communicates only with neighbors.

---

## Advantages

* Simple
* Controlled communication

---

## Limitation

Information spreads slowly.

---

# 6. Blackboard Communication Strategy

Shared memory board.

```
        Blackboard
      /   |   |   \
    P1   P2  P3  P4
```

All processors:

* Read
* Write

through common board.

---

## Advantages

* Better coordination
* Dynamic load balancing

---

## Limitation

Synchronization overhead

Processors may wait for access.

---

# 7. Odd-Even Transposition Sort

Parallel version of Bubble Sort.

---

## Even Phase

Compare:

```
(0,1)
(2,3)
(4,5)
```

Simultaneously.

---

## Odd Phase

Compare:

```
(1,2)
(3,4)
(5,6)
```

Simultaneously.

---

Repeat until sorted.

Example:

```
8 4 6 2
```

Even:

```
4 8 2 6
```

Odd:

```
4 2 8 6
```

Continue.

---

## Complexity

Sequential:

[
O(n^2)
]

Parallel:

[
O(n)
]

(with enough processors)

---

# 8. Parallel Bubble Sort

Multiple adjacent comparisons occur simultaneously.

Example:

```
8 4 6 2
```

P1 compares:

```
8,4
```

P2 compares:

```
6,2
```

at same time.

---

## Complexity

Sequential:

[
O(n^2)
]

Parallel:

[
O(n)
]

Enough processors

Limited processors:

[
O(n^2/p)
]

---

# 9. Sequential vs Parallel Bubble Sort

| Feature    | Sequential | Parallel |
| ---------- | ---------- | -------- |
| Processors | 1          | Many     |
| Speed      | Slow       | Faster   |
| Complexity | O(n²)      | O(n)     |
| CPU Usage  | Low        | High     |

---

# 10. Parallel Merge Sort

Based on Divide and Conquer.

---

## Steps

### Divide

```
8 4 6 2
```

↓

```
8 4 | 6 2
```

---

### Sort Simultaneously

P1:

```
8 4 → 4 8
```

P2:

```
6 2 → 2 6
```

---

### Merge

```
4 8 + 2 6
```

↓

```
2 4 6 8
```

---

## Complexity

Sequential:

[
O(n\log n)
]

Parallel:

[
O(\log^2 n)
]

Limited processors:

[
O((n\log n)/p)
]

---

# 11. Sequential vs Parallel Merge Sort

| Feature     | Sequential | Parallel |
| ----------- | ---------- | -------- |
| Processor   | 1          | Many     |
| Speed       | Lower      | Higher   |
| Complexity  | O(nlogn)   | O(log²n) |
| Scalability | Low        | High     |

---

# 12. Recursive Decomposition in Parallel Quick Sort

Idea:

Break problem recursively.

Example:

```
[9 4 8 2 7]
```

Pivot = 7

```
[4 2] 7 [9 8]
```

Processors sort both sides simultaneously.

---

## Advantages

### Natural Parallelism

Independent subarrays.

### Faster Execution

Many processors work together.

### Scalability

Works well on large systems.

---

# 13. Shared Address vs Message Passing Quick Sort

## Shared Address Space

All processors share memory.

```
Processor → Shared Memory
```

### Advantages

* Easy communication
* Fast access

### Disadvantage

Memory conflicts.

---

## Message Passing

Each processor has separate memory.

```
P1 ↔ P2 ↔ P3
```

Communication via messages.

---

### Advantages

* No memory conflicts
* Better scalability

### Disadvantage

Communication cost.

---

# 14. Issues in Parallel Sorting

### 1. Load Balancing

Some processors may get more work.

---

### 2. Communication Overhead

Processors spend time exchanging data.

---

### 3. Synchronization Delay

Processors wait for others.

---

### 4. Data Dependency

One task depends on another.

---

### 5. Memory Conflicts

Multiple writes to same memory.

---

### 6. Scalability Issues

Performance may stop improving.

---

### 7. Merging Complexity

Combining sorted parts is costly.

---

### 8. Network Latency

Slow communication between nodes.

---

# 15. What is Kubernetes?

Kubernetes (K8s) is an open-source container orchestration platform developed by Google.

Used to:

* Deploy containers
* Scale containers
* Monitor containers

Think:

```
Docker = Creates containers

Kubernetes = Manages thousands of containers
```

---

# 16. Kubernetes Architecture

## Diagram

```
          Control Plane
         (Master Node)

      API Server
      Scheduler
      Controller
      etcd

             |
             |
      ----------------
      |              |
 Worker Node     Worker Node

 Pods          Pods
 Kubelet       Kubelet
 Kube-proxy    Kube-proxy
```

---

## Control Plane

### API Server

Main entry point.

### Scheduler

Assigns pods to nodes.

### Controller Manager

Maintains desired state.

### etcd

Stores cluster information.

---

## Worker Node

### Pods

Smallest deployable unit.

### Kubelet

Communicates with master.

### Kube-proxy

Handles networking.

---

# 17. Features of Kubernetes

1. Load Balancing
2. Self-Healing
3. Auto Scaling
4. Storage Orchestration
5. Automated Deployment
6. Service Discovery
7. Portability

---

# 18. Applications of Kubernetes

* DevOps / CI-CD
* Big Data
* AI/ML Workloads
* Cloud Applications
* IoT
* Web Hosting

---

# 19. Container Orchestration

Automatic management of containers.

Functions:

### Deployment

Start containers automatically.

### Scaling

Increase/decrease containers.

### Self-Healing

Restart failed containers.

### Load Balancing

Distribute traffic.

### Rollback

Return to previous version.

---

# 20. Document Classification

Automatically categorizing documents.

Examples:

```
Sports
Business
Health
Politics
```

---

## Algorithms Used

### KNN

Nearest documents decide category.

### Naive Bayes

Probability-based.

### SVM

Separates classes using hyperplane.

### Neural Networks

Deep learning models.

---

# 21. Distributed Document Classification

Large dataset split across nodes.

---

## Steps

### Step 1

Divide dataset.

### Step 2

Assign to nodes.

### Step 3

Parallel classification.

### Step 4

Collect results.

---

## Advantages

* Faster processing
* Scalability
* Better resource utilization

---

# 22. GPU Applications

GPUs contain thousands of cores.

Suitable for massive parallel processing.

### Applications

1. Gaming & Graphics
2. Deep Learning
3. Scientific Simulations
4. Autonomous Vehicles
5. Medical Imaging
6. Cryptocurrency Mining
7. Video Rendering

---

# 23. Parallel Computing for AI/ML

## Why Needed?

AI models process:

* Huge datasets
* Millions/Billions of parameters

---

## Uses

### Faster Training

Multiple GPUs train simultaneously.

### Big Data Processing

Large datasets processed quickly.

### Distributed Learning

Training across many machines.

### Real-Time AI

Speech recognition, self-driving cars.

---

## Advantages

✔ Faster computation

✔ Reduced training time

✔ Scalability

---

# 24. CRCW PRAM

## Full Form

Concurrent Read Concurrent Write

---

## PRAM Model

Parallel Random Access Machine

Shared memory model.

---

## CRCW Property

Multiple processors can:

### Read Same Memory

```
P1 → X
P2 → X
P3 → X
```

simultaneously.

---

### Write Same Memory

```
P1 → X
P2 → X
P3 → X
```

simultaneously.

---

## Advantages

* Maximum parallelism
* Fast computation

---

## Applications

* Sorting
* Searching
* Graph Algorithms
* Scientific Computing

---

# Most Important Exam Questions (Very High Probability)

1. Parallel DFS with diagram and complexity.
2. Parallel BFS with frontier queue and complexity.
3. Communication strategies in BFS.
4. Odd-Even Transposition Sort.
5. Parallel Merge Sort.
6. Recursive Decomposition in Parallel Quick Sort.
7. Issues in Parallel Sorting.
8. Kubernetes Architecture (diagram compulsory).
9. Features and Applications of Kubernetes.
10. Distributed Document Classification.
11. GPU Applications and AI/ML Parallel Computing.
12. CRCW PRAM model.

If you have only **2–3 hours before the exam**, focus on **Parallel BFS, Parallel DFS, Parallel Merge Sort, Kubernetes Architecture, Container Orchestration, GPU Applications, and CRCW PRAM** first—they are the easiest to score and frequently asked.
