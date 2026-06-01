# CUDA + Parallel Algorithms (Exam-Oriented Detailed Notes)

---

# 1. CUDA Basics & Architecture

## What is CUDA?

**CUDA (Compute Unified Device Architecture)** is a parallel computing platform and programming model developed by NVIDIA.

It allows programmers to use the **GPU (Graphics Processing Unit)** not only for graphics but also for **general-purpose computing**.

### Why CUDA?

Normally:

* CPU has few powerful cores.
* GPU has thousands of smaller cores.

Therefore GPU can perform many calculations simultaneously.

### Example

Suppose we want to add 1000 numbers.

**CPU:**

```
1 + 1
1 + 1
1 + 1
...
1000 times
```

One after another.

**GPU:**

```
1000 additions at same time
```

This is called **parallel processing**.

---

## Languages Supported by CUDA

CUDA supports:

1. CUDA C/C++
2. Fortran
3. Python (PyCUDA, CuPy)
4. MATLAB
5. Java Bindings

---

## Applications of CUDA

### 1. Deep Learning

Training neural networks.

Examples:

* ChatGPT
* Image Recognition
* Speech Recognition

### 2. Image Processing

* Filters
* Face Detection
* Edge Detection

### 3. Video Processing

* Video rendering
* Video encoding

### 4. Scientific Simulations

* Weather forecasting
* Molecular simulation

### 5. Medical Imaging

* MRI Processing
* CT Scan Analysis

---

# CUDA Architecture

## Basic Architecture

```text
CPU (Host)
     |
PCI Express Bus
     |
GPU (Device)
```

Inside GPU:

```text
GPU
|
|-- Global Memory
|
|-- SM1
|-- SM2
|-- SM3
|-- SM4
```

Each SM contains many CUDA cores.

---

## Components

### CPU (Host)

Controls the execution.

Responsibilities:

* Runs main program
* Allocates memory
* Launches kernels

---

### GPU (Device)

Performs heavy computations.

Contains:

* Thousands of cores
* Large number of threads

---

### Streaming Multiprocessor (SM)

Main execution unit inside GPU.

Each SM:

* Executes thread blocks
* Contains CUDA cores
* Contains shared memory

Example:

```text
SM
|
|-- Core
|-- Core
|-- Core
|-- Shared Memory
```

---

## CPU vs GPU

| CPU                   | GPU                 |
| --------------------- | ------------------- |
| Few cores             | Thousands of cores  |
| Sequential processing | Parallel processing |
| Complex tasks         | Repetitive tasks    |
| Large cache           | Large parallelism   |

### Exam Point

CPU = Latency optimized

GPU = Throughput optimized

---

# Parallel Processing in CUDA

CUDA follows:

### SIMT

**Single Instruction Multiple Threads**

Meaning:

Many threads execute the same instruction on different data.

Example:

```text
Array:

1 2 3 4 5

Threads:

T1 -> square(1)
T2 -> square(2)
T3 -> square(3)
T4 -> square(4)
T5 -> square(5)
```

All execute simultaneously.

---

# Grid, Block and Thread

Most important topic.

---

## Thread

Smallest execution unit.

Example:

```text
Thread 0
Thread 1
Thread 2
```

Each thread performs one task.

---

## Block

Collection of threads.

```text
Block 0

T0 T1
T2 T3
```

Threads inside same block can:

* Communicate
* Share memory

---

## Grid

Collection of blocks.

```text
Grid

Block0
Block1
Block2
```

Kernel launch creates a grid.

---

## Hierarchy

```text
Grid
 |
 +-- Block
        |
        +-- Thread
```

### Exam Definition

Thread → Smallest execution unit

Block → Group of threads

Grid → Group of blocks

---

# CUDA Terminology

## Host

CPU + Main Memory

---

## Device

GPU + GPU Memory

---

## Kernel

A function executed on GPU.

Syntax:

```cpp
__global__ void add()
{
}
```

`__global__` means GPU kernel.

---

## Device Code

Code executed on GPU.

---

# Example Kernel

```cpp
__global__ void add(int *a,int *b,int *c)
{
    c[0]=a[0]+b[0];
}
```

Execution:

```text
a[0] = 10
b[0] = 20

c[0] = 30
```

---

# 2. CUDA Program Execution & Kernel

---

## CUDA Program Flow

### Step 1

Allocate memory on Host.

```cpp
int h_A[100];
```

---

### Step 2

Allocate memory on Device.

```cpp
cudaMalloc()
```

---

### Step 3

Copy CPU → GPU

```cpp
cudaMemcpy()
```

---

### Step 4

Launch Kernel

```cpp
kernel<<<...>>>();
```

---

### Step 5

GPU Executes

Thousands of threads run.

---

### Step 6

Copy GPU → CPU

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

## Diagram

```text
CPU Memory
    |
cudaMemcpy
    ↓
GPU Memory
    |
Kernel Execution
    |
cudaMemcpy
    ↓
CPU Memory
```

---

# CUDA Kernel Execution

Example:

```cpp
__global__ void square(int *a)
{
    int i = threadIdx.x;

    a[i] = a[i]*a[i];
}
```

Launch:

```cpp
square<<<1,5>>>(d_a);
```

---

### Meaning

```cpp
<<<1,5>>>
```

means

```text
1 Block

5 Threads
```

Threads:

```text
T0 → a[0]^2
T1 → a[1]^2
T2 → a[2]^2
T3 → a[3]^2
T4 → a[4]^2
```

---

# Kernel Launch Syntax

```cpp
kernel<<<gridDim, blockDim>>>(arguments);
```

Example:

```cpp
square<<<4,256>>>();
```

Meaning:

```text
4 Blocks

256 Threads per block

Total = 1024 Threads
```

---

# Important Built-in Variables

## threadIdx.x

Thread number inside block.

---

## blockIdx.x

Block number.

---

## blockDim.x

Threads per block.

---

## Global Thread ID

Most important formula.

```cpp
i = blockIdx.x * blockDim.x + threadIdx.x;
```

### Example

Block ID = 2

Block Size = 256

Thread ID = 10

```cpp
i = 2*256 + 10

i = 522
```

Global Thread Number = 522

---

# Vector Addition Kernel

```cpp
__global__ void vectorAdd
(int *A,int *B,int *C,int N)
{
   int i=
   blockIdx.x * blockDim.x
   + threadIdx.x;

   if(i<N)
      C[i]=A[i]+B[i];
}
```

---

### Example

```text
A = [1 2 3]

B = [4 5 6]

C = [5 7 9]
```

Each thread computes one element.

---

# Integer Multiplication Kernel

```cpp
__global__ void multiply
(int a,int b,int *c)
{
    *c=a*b;
}
```

Example:

```text
a=10
b=20

Result=200
```

---

# 3. CUDA Memory Model

---

# CUDA Memory Hierarchy

```text
Registers
   ↓
Shared Memory
   ↓
Global Memory
```

Speed:

```text
Registers (Fastest)

Shared Memory

Global Memory (Slowest)
```

---

## Registers

Fastest memory.

Private to each thread.

Example:

```cpp
int temp;
```

Stored in register.

---

## Shared Memory

Shared among threads of same block.

```cpp
__shared__ int data[256];
```

Advantages:

* Very fast
* Thread communication

---

## Global Memory

Available to all threads.

```cpp
cudaMalloc()
```

allocates global memory.

Advantages:

* Large size

Disadvantage:

* Slow access

---

# Global vs Shared Memory

| Shared        | Global       |
| ------------- | ------------ |
| Fast          | Slow         |
| Small         | Large        |
| Block only    | Entire GPU   |
| Communication | Data Storage |

---

# GPU Memory Management

---

## cudaMalloc()

Allocate memory.

```cpp
cudaMalloc((void**)&d_A,
100*sizeof(int));
```

---

## cudaMemcpy()

Copy memory.

CPU → GPU

```cpp
cudaMemcpy(
d_A,
h_A,
size,
cudaMemcpyHostToDevice
);
```

GPU → CPU

```cpp
cudaMemcpy(
h_A,
d_A,
size,
cudaMemcpyDeviceToHost
);
```

---

## cudaFree()

Release memory.

```cpp
cudaFree(d_A);
```

---

# 4. CUDA Communication & Synchronization

---

## Why Synchronization?

Many threads run simultaneously.

Without synchronization:

* Wrong results
* Race conditions

---

# Thread Communication

Using:

### Shared Memory

Fast communication.

```cpp
__shared__ int temp[256];
```

---

### Global Memory

Communication across blocks.

Slower.

---

# __syncthreads()

Most important synchronization function.

```cpp
__syncthreads();
```

Meaning:

> Every thread in block must reach this point before any thread continues.

---

### Example

```cpp
temp[threadIdx.x]=A[i];

__syncthreads();
```

All threads finish writing before reading.

---

# cudaDeviceSynchronize()

```cpp
cudaDeviceSynchronize();
```

CPU waits until GPU finishes execution.

Used after kernel launch.

---

# Important CUDA Functions

| Function                | Purpose            |
| ----------------------- | ------------------ |
| cudaMalloc()            | Allocate memory    |
| cudaMemcpy()            | Copy memory        |
| cudaFree()              | Free memory        |
| __syncthreads()         | Synchronize block  |
| cudaDeviceSynchronize() | Synchronize device |

---

# 5. CUDA Applications, Advantages & Limitations

## Advantages

### 1. High Speed

Thousands of cores.

---

### 2. Massive Parallelism

Millions of operations together.

---

### 3. Better Performance

Especially for matrix operations.

---

### 4. Reduced Execution Time

Large workloads complete quickly.

---

## Limitations

### 1. NVIDIA GPU Required

CUDA works only on NVIDIA GPUs.

---

### 2. Complex Programming

More difficult than CPU programming.

---

### 3. Memory Transfer Overhead

CPU ↔ GPU transfers take time.

---

### 4. Poor for Sequential Tasks

Not every problem is parallel.

---

# 6. Parallel Algorithms & Sorting

---

# Compare-Exchange

Two processors compare values.

Swap if necessary.

Example:

```text
Before

9 4

Compare

After

4 9
```

Used in sorting networks.

---

# Compare-Split

Used in parallel sorting.

Processors exchange data.

Example:

```text
P1 = [1 7]

P2 = [3 5]

After compare-split

P1=[1 3]
P2=[5 7]
```

Smaller values move left.

Larger values move right.

---

# Issues in Parallel Sorting

### 1. Communication Overhead

Processors must exchange data.

---

### 2. Synchronization Cost

Need waiting between phases.

---

### 3. Load Imbalance

Some processors get more work.

---

### 4. Processor Idle Time

Some processors may remain unused.

---

# Odd-Even Transposition Sort

Also called Parallel Bubble Sort.

---

## Odd Phase

Compare:

```text
(1,2)
(3,4)
(5,6)
```

---

## Even Phase

Compare:

```text
(0,1)
(2,3)
(4,5)
```

---

## Example

```text
5 2 8 1

Even:
5 2 → 2 5
8 1 → 1 8

Result:
2 5 1 8

Odd:
5 1 → 1 5

Result:
2 1 5 8

Continue until sorted.

Final:
1 2 5 8
```

### Complexity

Sequential:

```
O(n²)
```

Parallel:

```
O(n)
```

with n processors.

---

# Parallel DFS (Depth First Search)

DFS explores graph depth-wise.

---

## Sequential Complexity

```text
O(V + E)
```

Where:

* V = Vertices
* E = Edges

---

## Parallel DFS

Different processors explore different branches simultaneously.

```text
Processor 1 → Left subtree

Processor 2 → Right subtree

Processor 3 → Another branch
```

---

## Parallel Complexity

```text
O((V+E)/P)
```

Where:

P = Number of processors

---

# Parallel Dijkstra Algorithm

Used for shortest path.

---

## Steps

### Step 1

Distribute graph among processors.

---

### Step 2

Find minimum distance vertex in parallel.

---

### Step 3

Relax neighboring edges simultaneously.

---

### Example

```text
A → B = 2
A → C = 4
B → D = 3
C → D = 1
```

Processors update distances together.

---

## Advantage

* Faster shortest path computation
* Suitable for large graphs
* Useful in road networks and routing

---

# Last-Minute Exam Questions (Very Important)

1. What is CUDA? Explain CUDA architecture.
2. Differentiate CPU and GPU.
3. Explain Grid, Block and Thread hierarchy.
4. What is a Kernel? Explain kernel launch syntax.
5. Explain CUDA program execution flow.
6. Explain CUDA memory hierarchy.
7. Differentiate Shared Memory and Global Memory.
8. Explain `cudaMalloc()`, `cudaMemcpy()`, `cudaFree()`.
9. Explain `__syncthreads()` and `cudaDeviceSynchronize()`.
10. Explain Odd-Even Transposition Sort.
11. Explain Compare-Exchange and Compare-Split.
12. Explain Parallel DFS.
13. Explain Parallel Dijkstra Algorithm.

If you can write these 13 answers with diagrams and the key formulas (`i = blockIdx.x * blockDim.x + threadIdx.x` and `O((V+E)/P)`), you can comfortably cover most CUDA and Parallel Algorithm exam questions.
