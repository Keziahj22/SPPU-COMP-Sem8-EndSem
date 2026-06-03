For an **8-mark answer**, don't just write definitions. Follow this structure:

**Definition → Need → Architecture/Working → Diagram → Advantages → Applications → Limitations**

This will easily fill 1–2 pages per question.

**Source Notes:** Based on your uploaded Unit-3 RNN notes. 

---

# 1. Recurrent Neural Network (RNN)

## Definition

A Recurrent Neural Network (RNN) is a type of neural network designed for processing **sequential data**, where the current output depends not only on the current input but also on previous inputs.

Unlike Feed Forward Networks, RNN has a **memory mechanism** called the hidden state that stores information from previous time steps.

---

## Need of RNN

Traditional Neural Networks:

* Process inputs independently.
* Cannot remember previous information.
* Unsuitable for sequence data.

RNN:

* Maintains memory using hidden states.
* Learns temporal relationships.
* Suitable for data where order matters.

Examples:

* Text processing
* Speech recognition
* Language translation
* Stock prediction

---

## Architecture

```
x1 → [RNN] → y1
      ↓
x2 → [RNN] → y2
      ↓
x3 → [RNN] → y3
```

Where:

* xₜ = current input
* hₜ = hidden state (memory)
* yₜ = output

---

## Working

At each time step:

### Step 1

Receive current input xₜ

### Step 2

Receive previous hidden state hₜ₋₁

### Step 3

Compute new hidden state

```
hₜ = f(Wxh xₜ + Whh hₜ₋₁ + bh)
```

### Step 4

Generate output

```
yₜ = Why hₜ + by
```

Thus,

**Current Output = Current Input + Previous Memory**

---

## Advantages

* Captures sequential information
* Remembers previous inputs
* Learns contextual relationships
* Suitable for time-series data

---

## Limitations

* Vanishing Gradient Problem
* Exploding Gradient Problem
* Slow training
* Poor long-term memory

---

## Applications

* Chatbots
* Text prediction
* Speech recognition
* Language translation
* Weather forecasting

---

## Conclusion

RNN is the foundation of sequence learning models and forms the basis of advanced architectures such as LSTM and GRU.

---

# 2. Types of RNN

RNNs are categorized according to the number of inputs and outputs.

---

## 1. One-to-One

Single Input → Single Output

```
Input → Neural Network → Output
```

Example:

* Image Classification

Input: Image

Output: Cat/Dog

---

## 2. One-to-Many

Single Input → Multiple Outputs

```
Input → RNN → Output1 Output2 Output3
```

Example:

* Image Captioning

Input: Image

Output: "A dog is running"

---

## 3. Many-to-One

Multiple Inputs → Single Output

```
Word1 → Word2 → Word3 → Output
```

Example:

* Sentiment Analysis

Input: Review

Output: Positive/Negative

---

## 4. Many-to-Many

Multiple Inputs → Multiple Outputs

```
Input Sequence → RNN → Output Sequence
```

Example:

* Machine Translation

English → French

---

## Comparison Table

| Type      | Input    | Output   | Example              |
| --------- | -------- | -------- | -------------------- |
| One-One   | Single   | Single   | Image Classification |
| One-Many  | Single   | Multiple | Image Captioning     |
| Many-One  | Multiple | Single   | Sentiment Analysis   |
| Many-Many | Multiple | Multiple | Translation          |

---

# 3. RNN vs Feed Forward Neural Network

| Feature           | Feed Forward NN | RNN     |
| ----------------- | --------------- | ------- |
| Memory            | No              | Yes     |
| Sequence Handling | No              | Yes     |
| Context Awareness | No              | Yes     |
| Hidden State      | Absent          | Present |
| Suitable for NLP  | No              | Yes     |

---

## Example

Sentence:

"I love machine learning"

### Feed Forward NN

Treats each word separately.

Cannot understand sentence meaning.

### RNN

Processes words sequentially.

Uses memory to understand context.

Learns complete sentence meaning.

---

## Advantages of RNN over FFNN

* Maintains context
* Learns temporal patterns
* Better for NLP applications

---

## Conclusion

RNN extends Feed Forward Networks by introducing memory and sequence learning capability.

---

# 4. Computational Graph / Unfolding of RNN

## Definition

Unfolding converts the cyclic RNN structure into a time-based sequence representation.

---

## Unfolded Representation

```
x1 → h1 → y1
      ↓
x2 → h2 → y2
      ↓
x3 → h3 → y3
```

---

## Why Unfolding is Needed

* Shows data flow clearly.
* Helps understand memory propagation.
* Required for training using BPTT.

---

## Working

At every time step:

1. Input enters network.
2. Hidden state updated.
3. Output generated.
4. Hidden state passed forward.

---

## Advantages

* Easy visualization
* Better understanding of sequence learning
* Used in gradient calculation

---

## Applications

* Language models
* Speech processing
* Time-series forecasting

---

# 5. Long-Term Dependencies

## Definition

Long-term dependency occurs when current output depends on information received many time steps earlier.

---

## Example

Sentence:

"I grew up in France. ... I speak fluent French."

To predict "French", the network must remember "France".

---

## Challenges

* Information gets diluted over time.
* Difficult optimization.
* Poor long-term memory in simple RNN.

---

## Effects

* Reduced prediction accuracy.
* Failure to capture distant relationships.

---

## Solution

LSTM and GRU architectures were introduced to solve long-term dependency problems.

---

# 6. Vanishing Gradient Problem

## Definition

During backpropagation, gradients become extremely small as they travel backward through many layers or time steps.

---

## Working

Gradient:

```
0.5 × 0.5 × 0.5 × 0.5 ...
```

After many multiplications:

```
≈ 0
```

---

## Effects

* Earlier layers stop learning.
* Old information is forgotten.
* Training becomes ineffective.

---

## Consequences

* Poor long-term memory.
* Reduced accuracy.
* Slow convergence.

---

## Solutions

* LSTM
* GRU
* Proper weight initialization
* Gradient clipping

---

# 7. Exploding Gradient Problem

## Definition

Gradients become excessively large during training.

---

## Example

```
2 × 2 × 2 × 2 × 2 ...
```

Result becomes huge.

---

## Effects

* Very large weight updates
* Unstable learning
* Oscillating loss values
* Training failure

---

## Solutions

### Gradient Clipping

Limit gradient value:

```
if gradient > threshold
    gradient = threshold
```

### LSTM

Provides controlled memory flow.

---

## Conclusion

Exploding gradients cause instability, whereas vanishing gradients cause loss of memory.

---

# Quick 8-Mark Exam Tip

**Most Important Questions (Highest Probability):**

1. RNN Architecture & Working ⭐⭐⭐⭐⭐
2. Types of RNN ⭐⭐⭐⭐
3. RNN vs Feed Forward NN ⭐⭐⭐⭐
4. Computational Graph / Unfolding ⭐⭐⭐⭐
5. Long-Term Dependencies ⭐⭐⭐⭐
6. Vanishing Gradient Problem ⭐⭐⭐⭐⭐
7. Exploding Gradient Problem ⭐⭐⭐⭐

These 7 topics alone usually cover a large portion of Unit 3 RNN questions.