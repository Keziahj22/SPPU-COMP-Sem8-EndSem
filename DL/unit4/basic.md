Perfect. These questions can be merged into **13 major answers**. If you prepare these thoroughly, you'll cover almost all Unit-3 RNN questions.

**Source:** Based on your uploaded Unit-3 notes. 

---

# 1. RNN (Architecture, Need, Working, Types, Training, RNN vs FFNN)

**Covers Questions:**

* 1, 2, 3, 4, 5, 6, 7

---

## Definition

Recurrent Neural Network (RNN) is a neural network specially designed for processing **sequential data** where previous information influences current output.

Unlike Feed Forward Neural Networks, RNN contains a **hidden state (memory)** that stores information from previous inputs.

---

## Need of RNN

Traditional Feed Forward Networks:

* Cannot remember previous inputs
* Treat each input independently
* Cannot model sequences

Examples where sequence matters:

* Text sentences
* Speech signals
* Stock prices
* Weather forecasting

Hence RNN was developed.

---

## Architecture

```text
x₁ → h₁ → y₁
      ↓
x₂ → h₂ → y₂
      ↓
x₃ → h₃ → y₃
```

Where:

* xₜ = input
* hₜ = hidden state
* yₜ = output

---

## Working of RNN

At every time step:

### Step 1

Receive current input xₜ

### Step 2

Receive previous hidden state hₜ₋₁

### Step 3

Generate new hidden state

[
h_t=f(W_{xh}x_t+W_{hh}h_{t-1}+b_h)
]

### Step 4

Generate output

[
y_t=W_{hy}h_t+b_y
]

Thus:

**Current Output = Current Input + Previous Memory**

---

## Types of RNN

### 1. One-to-One

Single Input → Single Output

Example:

Image Classification

---

### 2. One-to-Many

Single Input → Multiple Outputs

Example:

Image Captioning

---

### 3. Many-to-One

Multiple Inputs → Single Output

Example:

Sentiment Analysis

---

### 4. Many-to-Many

Multiple Inputs → Multiple Outputs

Example:

Machine Translation

---

## Training of RNN

RNN is trained using:

### Backpropagation Through Time (BPTT)

Steps:

1. Forward propagation
2. Compute loss
3. Unfold network through time
4. Backpropagate errors
5. Update weights using Gradient Descent

---

## RNN vs Feed Forward Neural Network

| Feature          | FFNN | RNN       |
| ---------------- | ---- | --------- |
| Memory           | No   | Yes       |
| Sequence Data    | No   | Yes       |
| Context Learning | No   | Yes       |
| Hidden State     | No   | Yes       |
| NLP Tasks        | Poor | Excellent |

### Example

Sentence:

"I love machine learning"

FFNN:

Processes words separately.

RNN:

Understands complete context.

---

## Advantages

* Remembers previous information
* Suitable for sequence data
* Learns temporal relationships

---

## Limitations

* Vanishing Gradient
* Exploding Gradient
* Slow training

---

# 2. LSTM and Bidirectional LSTM

**Covers Questions:**

* 2.1, 2.2, 2.3, 2.4, 2.5

---

## Introduction

LSTM (Long Short-Term Memory) is an advanced RNN designed to solve the **vanishing gradient problem** and learn long-term dependencies.

---

## Why LSTM?

Normal RNN:

* Forgets old information
* Cannot learn long sequences

LSTM:

* Stores important information
* Removes unnecessary information

---

# Architecture of LSTM

Main Components:

1. Cell State (Ct)
2. Hidden State (ht)
3. Forget Gate
4. Input Gate
5. Output Gate

```text
Input
   ↓
Forget Gate
   ↓
Input Gate
   ↓
Cell State
   ↓
Output Gate
   ↓
Output
```

---

# Memory Cell Computational Implementation

### Forget Gate

Decides what to remove

[
f_t=\sigma(W_f[h_{t-1},x_t]+b_f)
]

Output:

0 → Forget

1 → Keep

---

### Input Gate

Decides what to store

[
i_t=\sigma(W_i[h_{t-1},x_t]+b_i)
]

Candidate memory:

[
\tilde{C}*t=tanh(W_c[h*{t-1},x_t]+b_c)
]

---

### Update Cell State

[
C_t=f_tC_{t-1}+i_t\tilde{C}_t
]

---

### Output Gate

Produces output

[
o_t=\sigma(W_o[h_{t-1},x_t]+b_o)
]

[
h_t=o_t*tanh(C_t)
]

---

## Three Gates Summary

### Forget Gate

Removes unwanted information.

### Input Gate

Adds useful information.

### Output Gate

Generates final output.

---

# Bidirectional LSTM

Uses:

* Forward LSTM
* Backward LSTM

```text
Forward →→→
Sentence
←←← Backward
```

Combined outputs produce final prediction.

---

## Advantages

* Uses past context
* Uses future context
* Better accuracy

---

## Applications

* NLP
* Translation
* Speech Recognition
* Chatbots

---

# 3. Computational Graph / Unfolding

**Covers Questions:**

* 3.1, 3.2, 3.3

---

## Definition

Unfolding converts the cyclic RNN into a time-expanded computational graph.

---

## Example

Original RNN

```text
h → h
↑   ↓
x   y
```

Unfolded

```text
x₁→h₁→y₁
     ↓
x₂→h₂→y₂
     ↓
x₃→h₃→y₃
```

---

## Importance

* Shows data flow clearly
* Enables BPTT
* Helps understand memory transfer

---

## Difference from Feed Forward Network

| FFNN        | RNN            |
| ----------- | -------------- |
| Fixed graph | Dynamic graph  |
| No loops    | Contains loops |
| No memory   | Memory exists  |

---

# 4. Encoder–Decoder (Sequence-to-Sequence)

**Covers Questions:**

* 4.1 to 4.4

---

## Definition

Encoder–Decoder is a sequence-to-sequence architecture where:

* Input = sequence
* Output = sequence

---

## Components

### Encoder

Reads entire input sequence.

Creates Context Vector.

---

### Context Vector

Stores summarized information.

---

### Decoder

Generates output sequence from context.

---

## Architecture

```text
Input Sequence
      ↓
   Encoder
      ↓
 Context Vector
      ↓
   Decoder
      ↓
Output Sequence
```

---

## Working

Example:

Input:

"I am learning AI"

Encoder generates context vector.

Decoder translates:

"Je suis en train d'apprendre l'IA"

---

## Applications

* Machine Translation
* Text Summarization
* Speech Recognition
* Chatbots

---

## Advantages

* Handles variable-length sequences
* Good for language processing

---

# 5. Recursive Neural Network vs Recurrent Neural Network

**Covers Questions:**

* 5.1, 5.2

---

## Recursive Neural Network

Processes hierarchical structures like trees.

---

## Example

Sentence Parsing Tree

```text
        Sentence
       /       \
   Subject    Predicate
```

---

## Difference

| RNN             | Recursive NN          |
| --------------- | --------------------- |
| Sequential Data | Tree Data             |
| Time-based      | Structure-based       |
| Text sequence   | Parse trees           |
| Hidden State    | Recursive Composition |

---

## Applications

* Natural Language Parsing
* Syntax Trees
* Scene Understanding

---

# 6. Long-Term Dependencies, Vanishing and Exploding Gradient

**Covers Questions:**

* 6.1, 6.2, 6.3

---

## Long-Term Dependency

Current prediction depends on very old information.

Example:

"I grew up in France ... I speak fluent French."

---

## Challenges (Write Any Seven)

### 1. Vanishing Gradient

Gradients become very small.

---

### 2. Exploding Gradient

Gradients become huge.

---

### 3. Memory Loss

Older information forgotten.

---

### 4. Slow Learning

Training becomes slow.

---

### 5. High Computation

Long sequences require more computation.

---

### 6. Optimization Difficulty

Hard to converge.

---

### 7. Temporal Credit Assignment

Difficult to identify important past events.

---

### 8. Instability

Weight updates become unstable.

---

## Solutions

* LSTM
* GRU
* Gradient Clipping
* Echo State Networks

---

# 7. Performance Metrics & Baseline Models

**Covers Questions:**

* 7.1, 7.2, 7.3

---

## Performance Metrics

### 1. Accuracy

[
Accuracy=\frac{Correct Predictions}{Total Predictions}
]

---

### 2. Loss Function

Measures prediction error.

Examples:

* Cross Entropy
* MSE

---

### 3. Perplexity

Used in language models.

Lower Perplexity = Better Model

---

### 4. BLEU Score

Used in machine translation.

Higher BLEU = Better Translation

---

### 5. Confusion Matrix

Shows:

* TP
* TN
* FP
* FN

---

# Default Baseline Models

Simple models used for comparison.

Examples:

* Random Predictor
* Majority Class Predictor
* Mean Predictor
* Rule-Based Predictor

Importance:

* Benchmarking
* Detecting overfitting
* Performance comparison

---

# 8. Bidirectional RNN

**Covers Questions:**

* 8.1, 8.2

---

## Architecture

Contains two RNNs:

### Forward RNN

Left → Right

### Backward RNN

Right → Left

Outputs are combined.

---

## Advantages

* Uses past context
* Uses future context
* Better understanding

---

## Example

"He went to bank to deposit money"

BiRNN understands bank = financial institution.

---

## Limitations

* High computation
* Slow training
* Requires complete sequence

---

# 9. Echo State Network (ESN)

---

## Definition

Special RNN where:

* Hidden layer fixed
* Only output layer trained

---

## Main Component

### Reservoir

Stores dynamic patterns called echoes.

---

## Advantages

* Fast training
* Less computation
* Better long-term memory

---

## ESN vs Traditional RNN

| Traditional RNN    | ESN                |
| ------------------ | ------------------ |
| Trains all weights | Trains output only |
| Slow               | Fast               |
| Complex            | Simple             |

---

# 10. Leaky Units

---

## Definition

Leaky Units update memory gradually instead of completely replacing it.

---

## Working

[
h_t=(1-\alpha)h_{t-1}+\alpha\tilde{h_t}
]

where α = leakage factor.

---

## Advantages

* Preserves old memory
* Learns multiple time scales
* Better long-term learning

---

## Applications

* Weather Prediction
* Financial Forecasting
* Time Series Analysis

---

# 11. CNN vs RNN

| Feature          | CNN                | RNN              |
| ---------------- | ------------------ | ---------------- |
| Data Type        | Images             | Sequences        |
| Memory           | No                 | Yes              |
| Context Learning | Limited            | Excellent        |
| Architecture     | Convolution Layers | Recurrent Layers |
| Application      | Vision             | NLP/Speech       |

---

# 12. Different Types of Deep Learning

1. CNN (Convolutional Neural Network)

   * Image processing

2. RNN (Recurrent Neural Network)

   * Sequential data

3. Recursive Neural Network

   * Tree structures

4. Autoencoders

   * Feature extraction

5. GANs

   * Image generation

6. Deep Belief Networks

   * Probabilistic learning

---

# 13. Implicit Memory vs Explicit Memory

| Implicit Memory      | Explicit Memory        |
| -------------------- | ---------------------- |
| Stored in weights    | Stored separately      |
| Difficult to access  | Directly accessible    |
| Used by simple RNN   | Used by LSTM           |
| Fixed representation | Dynamic representation |

### Example

Implicit Memory:

RNN hidden weights.

Explicit Memory:

LSTM Cell State.

---

## Most Important Questions for Tomorrow (Must Do)

⭐⭐⭐⭐⭐ RNN Architecture + Working + Types
⭐⭐⭐⭐⭐ LSTM Architecture + Gates
⭐⭐⭐⭐⭐ Encoder–Decoder Architecture
⭐⭐⭐⭐⭐ Long-Term Dependency + Vanishing Gradient
⭐⭐⭐⭐ Computational Graph / Unfolding
⭐⭐⭐⭐ Bidirectional RNN
⭐⭐⭐ Performance Metrics
⭐⭐⭐ Recursive NN vs RNN

If you prepare the first **5 answers thoroughly**, you can comfortably answer **70–80% of Unit-3 RNN exam questions**.
