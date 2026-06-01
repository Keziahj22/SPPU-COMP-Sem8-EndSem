That's too large to explain all 50 questions in one response (it would be tens of thousands of words). For exam preparation, the best approach is to **merge similar questions** into ~15 master answers. These master answers will cover almost all 50 PYQs.

---

# UNIT-5 MASTER ANSWER 1

# CUDA Basics, Programming Languages, Applications & Architecture

(Covers Q1, Q2, Q3, Q20, Q21, Q47, Q48, Q49)

## What is CUDA?

CUDA (Compute Unified Device Architecture) is a parallel computing platform developed by NVIDIA that enables programmers to use GPU resources for general-purpose computation.

Instead of executing tasks sequentially like a CPU, CUDA allows thousands of threads to execute simultaneously on the GPU.

---

## Languages Supported

1. CUDA C/C++
2. Fortran
3. Python (PyCUDA, CuPy)
4. MATLAB
5. Java Bindings

---

## CUDA Architecture

```text
CPU (Host)
     |
 PCIe Bus
     |
GPU (Device)
------------------------------------------------
| Global Memory                               |
|                                              |
| SM1   SM2   SM3   SM4                       |
| | |   | |   | |   | |                       |
| Cores Cores Cores Cores                     |
| Shared Memory in each SM                    |
------------------------------------------------
```

### Components

### Host

CPU + Main Memory

Functions:

* Controls execution
* Allocates memory
* Launches kernels

### Device

GPU + GPU Memory

Functions:

* Performs parallel computation

### Streaming Multiprocessor (SM)

Contains:

* CUDA Cores
* Registers
* Shared Memory

---

## Parallel Processing

CPU:

```text
Task1
Task2
Task3
Task4
```

Sequential Execution

GPU:

```text
Task1 Task2 Task3 Task4
```

Simultaneous Execution

CUDA uses SIMT:

**Single Instruction Multiple Threads**

Many threads execute same instruction on different data.

---

## Applications

### AI & Deep Learning

* Neural Networks
* LLM Training

### Scientific Computing

* Simulations
* Research

### Image Processing

* Face Detection
* Filtering

### Video Rendering

* Animation
* Encoding

### Medical Imaging

* MRI Analysis
* CT Scan Processing

---

## Advantages

* Massive Parallelism
* Faster Computation
* High Throughput
* Reduced Execution Time

---

## Limitations

* NVIDIA GPU Required
* Complex Programming
* CPU-GPU Transfer Overhead
* Not Suitable for Sequential Problems

---

# UNIT-5 MASTER ANSWER 2

# Grid, Block, Thread, Host, Device, Kernel

(Covers Q4, Q5, Q8, Q9, Q10)

---

## Thread

Smallest execution unit.

Each thread performs one operation.

Example:

```text
T0
T1
T2
T3
```

---

## Block

Collection of Threads.

```text
Block 0

T0 T1
T2 T3
```

Threads within same block can communicate using shared memory.

---

## Grid

Collection of Blocks.

```text
Grid

Block0
Block1
Block2
```

---

## Hierarchy

```text
Grid
 |
Blocks
 |
Threads
```

---

## Host

CPU + Main Memory

---

## Device

GPU + GPU Memory

---

## Device Code

Code executed on GPU.

---

## Kernel

A function executed on GPU by multiple threads.

```cpp
__global__ void add()
{
}
```

---

## Kernel Launch

Syntax:

```cpp
kernel<<<gridDim, blockDim>>>();
```

Example:

```cpp
add<<<4,256>>>();
```

Meaning:

* 4 Blocks
* 256 Threads per Block

Total Threads:

```text
4 × 256 = 1024
```

---

## Block Dimension

Number of threads inside a block.

Example:

```cpp
<<<2,128>>>
```

Block Dimension = 128

---

## Grid Dimension

Number of blocks in grid.

Example:

```cpp
<<<8,128>>>
```

Grid Dimension = 8

---

# UNIT-5 MASTER ANSWER 3

# CUDA Program Execution & Kernel Execution

(Covers Q6, Q7, Q11, Q12)

---

## CUDA Program Flow

### Step 1

Allocate Host Memory

```cpp
int h_A[100];
```

---

### Step 2

Allocate Device Memory

```cpp
cudaMalloc()
```

---

### Step 3

Copy Data CPU → GPU

```cpp
cudaMemcpy()
```

---

### Step 4

Launch Kernel

```cpp
kernel<<<blocks,threads>>>();
```

---

### Step 5

GPU Executes Threads

---

### Step 6

Copy Results GPU → CPU

```cpp
cudaMemcpy()
```

---

### Step 7

Free Memory

```cpp
cudaFree()
```

---

## CUDA Execution Diagram

```text
CPU Memory
      |
cudaMemcpy
      ↓
GPU Memory
      |
 Kernel
Execution
      |
cudaMemcpy
      ↓
CPU Memory
```

---

## Vector Addition Kernel

```cpp
__global__ void vectorAdd
(int *A,int *B,int *C,int N)
{
 int i=
 blockIdx.x*blockDim.x
 +threadIdx.x;

 if(i<N)
    C[i]=A[i]+B[i];
}
```

### Thread Working

```text
Thread0 → C[0]
Thread1 → C[1]
Thread2 → C[2]
```

---

## Integer Multiplication Kernel

```cpp
__global__ void multiply
(int a,int b,int *c)
{
 *c=a*b;
}
```

---

# UNIT-5 MASTER ANSWER 4

# CUDA Memory Model & Thread Hierarchy

(Covers Q13, Q14, Q15, Q16, Q17)

---

## CUDA Memory Hierarchy

```text
Registers
    ↓
Shared Memory
    ↓
Global Memory
```

Speed:

```text
Registers > Shared > Global
```

---

## Registers

* Fastest Memory
* Private to Thread

Example:

```cpp
int temp;
```

---

## Shared Memory

```cpp
__shared__ int data[256];
```

Properties:

* Fast
* Shared among block threads
* Used for communication

---

## Global Memory

Allocated by:

```cpp
cudaMalloc()
```

Properties:

* Large
* Accessible to all threads
* Slow

---

## Global vs Shared Memory

| Shared        | Global     |
| ------------- | ---------- |
| Fast          | Slow       |
| Small         | Large      |
| Block only    | Entire GPU |
| Communication | Storage    |

---

## Thread Hierarchy

```text
Grid
 |
Block
 |
Thread
```

---

## GPU Memory Management

### cudaMalloc()

Allocate memory

### cudaMemcpy()

Transfer memory

### cudaFree()

Release memory

Steps:

1. Allocate
2. Transfer
3. Execute
4. Retrieve
5. Free

---

# UNIT-5 MASTER ANSWER 5

# CUDA Communication & Synchronization

(Covers Q18, Q19)

---

## Communication

Threads communicate through:

### Shared Memory

Fast communication inside block.

```cpp
__shared__ int temp[256];
```

---

### Global Memory

Communication between blocks.

Slower.

---

## Synchronization

Required to avoid race conditions.

---

## __syncthreads()

```cpp
__syncthreads();
```

Meaning:

All threads in block must reach this statement before continuing.

Example:

```cpp
temp[threadIdx.x]=A[i];

__syncthreads();
```

Ensures every thread finishes writing before reading.

---

## cudaDeviceSynchronize()

```cpp
cudaDeviceSynchronize();
```

CPU waits until GPU finishes execution.

---

# UNIT-5 MASTER ANSWER 6

# Parallel Sorting

(Covers Q22, Q23, Q24, Q25, Q26)

---

## Compare Exchange

Two processors compare values.

```text
Before

9 4

After

4 9
```

---

## Compare Split

Processors exchange sorted halves.

```text
P1 = [1 7]

P2 = [3 5]

After

P1=[1 3]
P2=[5 7]
```

---

## Issues in Parallel Sorting

1. Communication Overhead
2. Synchronization Cost
3. Load Imbalance
4. Processor Idle Time

---

## Odd-Even Transposition Sort

### Odd Phase

```text
(1,2)
(3,4)
```

### Even Phase

```text
(0,1)
(2,3)
```

Repeat until sorted.

---

### Example

```text
5 2 8 1

Even:
2 5 1 8

Odd:
2 1 5 8

Even:
1 2 5 8
```

---

## Parallel Bubble Sort Algorithm

```text
for phase=1 to n
   if odd phase
      compare odd pairs
   else
      compare even pairs
```

---

## Complexity

Sequential Bubble Sort:

```text
O(n²)
```

Parallel Bubble Sort:

```text
O(n)
```

with n processors.

---

# UNIT-5 MASTER ANSWER 7

# Parallel Merge Sort & Quick Sort

(Covers Q27, Q28, Q29, Q30)

---

## Parallel Merge Sort

### Divide

Split array into parts.

### Sort

Processors sort independently.

### Merge

Merge results in parallel.

---

## Algorithm

```text
Divide array
Assign subarrays
Parallel sort
Parallel merge
```

---

## Complexity

Sequential:

```text
O(n log n)
```

Parallel:

```text
O((n log n)/P)
```

---

## Recursive Decomposition in Quick Sort

```text
Array

Partition

Left Part
Right Part
```

Assign different processors to each part.

---

## Shared Address Space Quick Sort

Processors access same memory.

Advantages:

* Easy communication
* Less copying

---

## Message Passing Quick Sort

Processors have local memory.

Communicate via messages.

Advantages:

* Scalable
* Distributed systems

---

# UNIT-5 MASTER ANSWER 8

# Parallel DFS & BFS

(Covers Q31-Q38)

---

## Parallel DFS

Different processors explore different branches.

```text
P1 → Left Branch

P2 → Right Branch
```

Complexity:

```text
O((V+E)/P)
```

---

## Parallel BFS

Level-by-Level traversal.

```text
Level 0

Level 1

Level 2
```

All vertices at same level explored simultaneously.

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

## Communication Strategies

### Random Communication

Processors communicate randomly.

Pros:

* Simple

Cons:

* Unpredictable

---

### Ring Communication

```text
P1 → P2 → P3 → P4 → P1
```

Pros:

* Structured

Cons:

* Delay possible

---

### Blackboard Communication

Shared memory area.

```text
Processor
     ↓
 Blackboard
     ↑
Processor
```

Pros:

* Easy sharing

Cons:

* Contention possible

---

# UNIT-5 MASTER ANSWER 9

# Parallel Dijkstra Algorithm

(Covers Q39)

---

## Steps

1. Partition graph
2. Find minimum distance vertex in parallel
3. Relax neighboring edges
4. Update distances

---

## Complexity

Sequential:

```text
O(V²)
```

Parallel:

Reduced by distributing computations among processors.

---

## Advantages

* Faster shortest path computation
* Suitable for large graphs
* Used in routing and navigation systems

---

# UNIT-5 MASTER ANSWER 10

# Kubernetes & Distributed Computing

(Covers Q40-Q46)

---

## What is Kubernetes?

Kubernetes is an open-source container orchestration platform used to automate deployment, scaling, and management of containers.

---

## Kubernetes Architecture

```text
Master Node
 |
 |-- API Server
 |-- Scheduler
 |-- Controller

Worker Nodes
 |
 |-- Pods
 |-- Containers
```

---

## Features

* Auto Scaling
* Self Healing
* Load Balancing
* Service Discovery
* Fault Tolerance

---

## Container Orchestration

Automatic management of containers.

Benefits:

* Easy deployment
* High availability
* Better resource utilization

---

## Distributed Document Classification

Large document collections are divided among multiple nodes.

Steps:

1. Data Partitioning
2. Parallel Processing
3. Classification
4. Result Aggregation

Benefits:

* Faster processing
* Better scalability

---

# UNIT-5 MASTER ANSWER 11

# GPU Applications, AI/ML & CRCW PRAM

(Covers Q47-Q50)

---

## GPU Applications

* Deep Learning
* Scientific Simulations
* Image Processing
* Video Rendering
* Medical Imaging

---

## Parallel Computing for AI/ML

AI requires huge matrix operations.

GPUs perform these operations simultaneously.

Benefits:

* Faster training
* Reduced computation time
* Better scalability

---

## AI/ML in Parallel Computing

Applications:

* Neural Networks
* NLP
* Computer Vision
* Recommendation Systems

---

## CRCW PRAM

### Full Form

Concurrent Read Concurrent Write Parallel Random Access Machine.

Multiple processors:

* Read same memory simultaneously
* Write same memory simultaneously

Example:

```text
P1 → Memory X

P2 → Memory X

P3 → Memory X
```

Used for designing theoretical parallel algorithms.

---

# Universal Points to Add in Any 5–10 Mark Answer

### Introduction

* Parallel computing improves performance by executing multiple tasks simultaneously.
* CUDA is NVIDIA's parallel computing platform for GPU programming.

### Advantages

* High Performance
* Scalability
* Reduced Execution Time
* Better Resource Utilization

### Key Formulae

```cpp
i = blockIdx.x * blockDim.x + threadIdx.x
```

(Global Thread ID)

```text
Parallel DFS/BFS Complexity

O((V+E)/P)
```

```text
Sequential Bubble Sort = O(n²)

Parallel Bubble Sort = O(n)
```

```text
Merge Sort = O(n log n)
```

### Conclusion Line (Write at End of Almost Any Answer)

> Thus, parallel computing using CUDA and distributed algorithms significantly improves computational performance, scalability, and efficiency for large-scale applications such as AI/ML, graph processing, scientific computing, and data analytics.
