# A. Language Models, Markov Models & Generative Models

(Combines Q1–Q7)

# Question

**What is a Markov Model and how is it used in Language Modelling? Explain the process of building a Markov Model for next-word prediction. Describe probabilistic language modelling using Markov assumptions. Explain Generative Models of Language and differentiate them from Discriminative Models with examples.**

---

# Answer

## Introduction

Language modelling is one of the fundamental tasks in Natural Language Processing (NLP). A language model estimates the probability of occurrence of a sequence of words and predicts the next word based on previous words.

Example:

```text
I love ______
```

Possible predictions:

```text
NLP
AI
Programming
```

The model assigns probabilities to each possible next word.

---

# Markov Model

## Definition

A Markov Model is a probabilistic model based on the **Markov Assumption**:

> The probability of the next state depends only on the current state and not on the complete history.

Mathematically:

[
P(w_n|w_1,w_2,...,w_{n-1})
]

is approximated as

[
P(w_n|w_{n-1})
]

This assumption greatly simplifies language modelling.

---

# Building a Simple Markov Model

Consider Corpus:

```text
I love NLP
I love AI
I study NLP
```

---

## Step 1: Tokenize Text

Words:

```text
I, love, NLP
I, love, AI
I, study, NLP
```

---

## Step 2: Generate Bigrams

```text
(I,love)
(love,NLP)

(I,love)
(love,AI)

(I,study)
(study,NLP)
```

---

## Step 3: Count Frequencies

| Bigram    | Count |
| --------- | ----- |
| I love    | 2     |
| I study   | 1     |
| love NLP  | 1     |
| love AI   | 1     |
| study NLP | 1     |

---

## Step 4: Compute Transition Probabilities

For word "I":

Total occurrences after I

```text
love = 2
study = 1
```

Total = 3

[
P(love|I)=\frac{2}{3}
]

[
P(study|I)=\frac{1}{3}
]

---

## Step 5: Prediction

Input:

```text
I
```

Predicted next word:

```text
love
```

because it has highest probability.

---

# Language Generation using Markov Models

Starting word:

```text
I
```

Possible generation:

```text
I → love → NLP
```

Generated sentence:

```text
I love NLP
```

Thus Markov models can generate new text sequences based on learned probabilities.

---

# Probabilistic Language Modelling

The probability of a sentence is calculated using the chain rule.

Sentence:

```text
I love NLP
```

[
P(I,love,NLP)
]

[
=P(I)\times P(love|I)\times P(NLP|I,love)
]

Computing the full probability is difficult.

Therefore Markov assumption is used.

---

# Trigram Language Model

A trigram considers two previous words.

[
P(w_n|w_{n-2},w_{n-1})
]

Sentence:

```text
I love NLP
```

Probability:

[
P(I)\times P(love|I)\times P(NLP|I,love)
]

---

## MLE (Maximum Likelihood Estimation)

MLE estimates probability from corpus frequencies.

Formula:

[
P(w_n|w_{n-2},w_{n-1})
======================

\frac{Count(w_{n-2},w_{n-1},w_n)}
{Count(w_{n-2},w_{n-1})}
]

---

### Example

Corpus:

```text
I love NLP
I love AI
```

Counts:

```text
Count(I,love,NLP)=1
Count(I,love)=2
```

Therefore

[
P(NLP|I,love)
=============

\frac{1}{2}
]

---

# Generative Models of Language

## Definition

Generative Models learn the probability distribution of data and generate new samples from it.

They model:

[
P(X)
]

or

[
P(X,Y)
]

where X represents words and Y represents labels.

---

## Working

Training Text:

```text
I love NLP
I love AI
```

Model learns patterns.

Generated output:

```text
I love Machine Learning
```

---

## Examples of Generative Models

### Traditional Models

* N-gram Models
* Markov Models
* Hidden Markov Models

### Modern Models

* GPT
* LLaMA
* Gemini

---

# Generative vs Discriminative Models

| Generative Model         | Discriminative Model                          |    |
| ------------------------ | --------------------------------------------- | -- |
| Learns data distribution | Learns decision boundary                      |    |
| Models P(X,Y)            | Models P(Y                                    | X) |
| Can generate text        | Cannot generate text                          |    |
| Used in text generation  | Used in classification                        |    |
| Example: HMM, GPT        | Example: Logistic Regression, BERT Classifier |    |

---

## Example

### Generative

Input:

```text
The weather is
```

Output:

```text
The weather is pleasant today.
```

### Discriminative

Input:

```text
This movie is amazing
```

Output:

```text
Positive Sentiment
```

---

# Applications

* Text Generation
* Chatbots
* Machine Translation
* Speech Recognition
* Next Word Prediction
* Auto Completion

---

# Advantages

* Simple and intuitive
* Efficient training
* Useful for sequence generation

---

# Limitations

* Markov assumption ignores long context
* Sparse data problem
* Cannot capture deep semantics

---

# Conclusion

Markov Models are probabilistic language models that predict future words based on previous words using the Markov assumption. They form the basis of N-gram language models and many generative models. Generative models learn language patterns and generate new text, while discriminative models focus on predicting labels or classes.

---

# Exam Keywords

**Language Model, Markov Assumption, State Transition, MLE, Trigram Model, Probability Estimation, Generative Model, Discriminative Model, Next Word Prediction, Text Generation**

---

# B. Bigram, Trigram & Smoothing

(Combines Q8–Q11)

# Question

**Explain Bigram and Trigram Language Models. What is Smoothing? Explain Laplace (Add-1) Smoothing with suitable numerical examples.**

---

# Answer

## Bigram Model

A Bigram Model predicts a word using one previous word.

[
P(w_n|w_{n-1})
]

Example:

```text
I love NLP
```

Bigrams:

```text
(I,love)
(love,NLP)
```

Probability:

[
P(NLP|love)
===========

\frac{Count(love,NLP)}
{Count(love)}
]

---

## Trigram Model

A Trigram Model predicts a word using two previous words.

[
P(w_n|w_{n-2},w_{n-1})
]

Example:

```text
I love NLP
```

Trigram:

```text
(I,love,NLP)
```

Probability:

[
P(NLP|I,love)
]

---

# Why Smoothing is Needed?

Suppose test sentence:

```text
I love Python
```

If Python never appears in training corpus:

[
P(Python|love)=0
]

Whole sentence probability becomes zero.

This is called the **zero-frequency problem**.

---

# Laplace (Add-1) Smoothing

Formula:

[
P(w|h)
======

\frac{Count(h,w)+1}
{Count(h)+V}
]

where

* h = history
* V = vocabulary size

---

## Example

Corpus:

```text
I love NLP
I love AI
```

Vocabulary:

```text
I
love
NLP
AI
Python
```

V = 5

Counts:

```text
Count(love)=2
Count(love,Python)=0
```

Without smoothing:

[
P(Python|love)=0
]

With Add-1:

[
P(Python|love)
==============

# \frac{0+1}{2+5}

\frac{1}{7}
]

Thus unseen words get non-zero probability.

---

# Advantages

* Removes zero probabilities
* Improves generalization
* Handles unseen words

---

# Conclusion

Bigram and Trigram models estimate next-word probabilities using previous context, while smoothing techniques such as Add-1 smoothing prevent unseen events from receiving zero probability.

---

# C. Latent Semantic Analysis (LSA)

(Combines Q12–Q14)

# Question

**Explain Latent Semantic Analysis (LSA) and its role in Topic Modelling. How does LSA identify relationships between words and documents?**

---

# Answer

## Definition

Latent Semantic Analysis (LSA) is a technique used to discover hidden semantic relationships between words and documents.

It reduces the dimensionality of text data and extracts latent topics.

---

## Main Idea

Words that occur in similar contexts tend to have similar meanings.

Example:

```text
car
automobile
vehicle
```

Although different words, LSA identifies them as semantically related.

---

## Working of LSA

### Step 1: Create Term-Document Matrix

| Word       | D1 | D2 |
| ---------- | -- | -- |
| Car        | 2  | 0  |
| Vehicle    | 1  | 1  |
| Automobile | 2  | 0  |

---

### Step 2: Apply SVD

Singular Value Decomposition

[
A = USV^T
]

Where:

* U = word matrix
* S = singular values
* V = document matrix

---

### Step 3: Dimension Reduction

Less important information is removed.

Hidden concepts emerge.

---

## Topic Modelling Example

Topic:

```text
Cricket
Match
Player
Runs
```

LSA automatically groups these words together.

---

## Applications

* Search Engines
* Information Retrieval
* Document Clustering
* Topic Modelling

---

## Advantages

* Captures semantic similarity
* Reduces noise

## Disadvantages

* Topics difficult to interpret
* Computationally expensive

---

# Conclusion

LSA uses matrix decomposition (SVD) to discover hidden semantic structures and identify relationships among words and documents.


# D. Latent Dirichlet Allocation (LDA)

(Combines Q15–Q17)

# Question

**Define Latent Dirichlet Allocation (LDA). Explain the LDA algorithm and how it is used for topic modelling with a suitable example. Discuss the key components of LDA including topics, documents and word distributions.**

---

# Answer

## Introduction

Topic Modelling is an unsupervised machine learning technique used to discover hidden topics from a collection of documents.

One of the most popular topic modelling algorithms is **Latent Dirichlet Allocation (LDA)**.

LDA was proposed by **David Blei, Andrew Ng and Michael Jordan (2003).**

---

# Definition

**Latent Dirichlet Allocation (LDA)** is a probabilistic topic modelling technique that assumes:

> Documents are mixtures of topics and topics are mixtures of words.

Thus:

```text
Document → Multiple Topics
Topic → Multiple Words
```

---

# Main Idea of LDA

Consider three documents:

### Document 1

```text
Virat Kohli scored a century in cricket match
```

### Document 2

```text
Rohit Sharma hit sixes in IPL
```

### Document 3

```text
Deep learning improves AI applications
```

LDA automatically discovers:

### Topic 1 : Cricket

```text
cricket
match
player
century
runs
IPL
```

### Topic 2 : Technology

```text
AI
machine
learning
data
algorithm
```

Without any labels.

---

# Key Components of LDA

## 1. Document

A collection of words.

Example:

```text
AI improves healthcare systems
```

---

## 2. Topic

A probability distribution over words.

Example:

Technology Topic

| Word     | Probability |
| -------- | ----------- |
| AI       | 0.25        |
| Data     | 0.20        |
| Learning | 0.18        |

---

## 3. Word Distribution

Each topic contains words with different probabilities.

[
P(Word|Topic)
]

---

## 4. Topic Distribution

Each document contains multiple topics.

[
P(Topic|Document)
]

Example:

Document:

```text
AI is used in cricket analytics
```

May contain:

| Topic      | Probability |
| ---------- | ----------- |
| Technology | 70%         |
| Sports     | 30%         |

---

# LDA Generative Process

For each document:

### Step 1

Choose topic distribution

[
\theta
]

---

### Step 2

For each word:

Select a topic.

---

### Step 3

Generate a word from selected topic.

---

## Flow Diagram

```text
Document
    ↓
Topic Distribution
    ↓
Choose Topic
    ↓
Generate Word
```

---

# Working of LDA Algorithm

## Step 1: Choose Number of Topics (K)

Example:

```text
K = 2
```

Topics:

```text
Sports
Technology
```

---

## Step 2: Random Topic Assignment

Initially assign random topics to all words.

Example:

```text
Cricket → Technology
AI → Sports
```

(Randomly)

---

## Step 3: Iterative Updating

LDA repeatedly updates assignments using probabilities.

Questions asked:

* How common is this word in the topic?
* How common is the topic in this document?

---

## Step 4: Convergence

After many iterations:

Stable topics emerge.

---

# Example

Documents:

```text
D1: cricket match player runs
D2: cricket team wins match
D3: AI machine learning data
D4: neural network deep learning
```

LDA discovers:

### Topic 1

```text
cricket
match
player
team
```

### Topic 2

```text
AI
learning
network
data
```

---

# Applications

* News Categorization
* Research Paper Analysis
* Customer Review Mining
* Search Engines
* Recommendation Systems

---

# Advantages

* Unsupervised learning
* Discovers hidden topics automatically
* Interpretable results

---

# Limitations

* Need to choose K beforehand
* Computationally expensive
* Topics may overlap

---

# Conclusion

LDA is a probabilistic topic modelling algorithm that represents documents as mixtures of topics and topics as mixtures of words. It is one of the most widely used techniques for discovering hidden themes in large collections of documents.

---

# Exam Keywords

**Topic Modelling, Document-Topic Distribution, Topic-Word Distribution, Dirichlet Distribution, Unsupervised Learning, Gibbs Sampling, Latent Topics**

---

# E. BERT

(Combines Q18–Q20)

# Question

**Explain BERT. What are contextualized word representations? Discuss the architecture, working, advantages and disadvantages of BERT.**

---

# Answer

# Introduction

Traditional word embeddings such as Word2Vec generate only one vector for a word.

Example:

```text
bank
```

has same representation in:

```text
I deposited money in a bank.
```

and

```text
The boat is near the river bank.
```

This creates ambiguity.

BERT solves this problem using contextual representations.

---

# Definition

**BERT**
(Bidirectional Encoder Representations from Transformers)

Developed by:

Google

in 2018.

It is a transformer-based language model that understands context from both left and right sides of a word.

---

# Why BERT?

Traditional models:

```text
Left → Right
```

or

```text
Right → Left
```

only.

BERT reads:

```text
Left ↔ Right
```

simultaneously.

Hence it is called **Bidirectional**.

---

# Example

Sentence 1:

```text
I deposited money in the bank.
```

BERT understands:

```text
bank = financial institution
```

---

Sentence 2:

```text
The fisherman sat near the bank.
```

BERT understands:

```text
bank = river side
```

---

# Architecture of BERT

BERT is based on:

## Transformer Encoder

Only Encoder stack is used.

Architecture:

```text
Input Text
      ↓
Tokenization
      ↓
Embedding Layer
      ↓
Transformer Encoders
      ↓
Contextual Representation
      ↓
Output Task
```

---

# Input Representation

BERT combines:

### 1. Token Embeddings

Word representations.

### 2. Segment Embeddings

Differentiate sentences.

### 3. Position Embeddings

Store word positions.

---

# Pretraining Tasks

## 1. Masked Language Model (MLM)

Some words are hidden.

Example:

```text
I love [MASK]
```

Prediction:

```text
NLP
```

---

## 2. Next Sentence Prediction (NSP)

Sentence A:

```text
I am hungry.
```

Sentence B:

```text
Let's eat food.
```

Model predicts whether B follows A.

---

# Contextualized Representations

Traditional embedding:

```text
bank → one vector
```

BERT:

```text
bank(finance) → vector 1

bank(river) → vector 2
```

Different contexts generate different vectors.

This is called a **contextualized representation**.

---

# Applications

* Sentiment Analysis
* Question Answering
* Chatbots
* Machine Translation
* Text Summarization
* Named Entity Recognition

---

# Advantages

### 1. Bidirectional Learning

Uses both left and right context.

### 2. Better Understanding

Captures semantic meaning.

### 3. Transfer Learning

Can be fine-tuned for many tasks.

### 4. High Accuracy

State-of-the-art performance.

---

# Disadvantages

### 1. Computationally Expensive

Requires powerful GPUs.

### 2. Large Memory Requirement

Millions of parameters.

### 3. Slow Training

Compared to simpler models.

---

# Conclusion

BERT is a transformer-based bidirectional language model that produces contextualized word representations and significantly improves performance in NLP tasks.

---

# Exam Keywords

**Transformer Encoder, Bidirectional Context, MLM, NSP, Contextual Embedding, Fine-Tuning, Transfer Learning**

---

# F. TF-IDF

(Combines Q21–Q23)

# Question

**Explain TF-IDF representation. Derive TF-IDF formula and calculate TF-IDF score with an example.**

---

# Answer

# Introduction

In NLP, not all words are equally important.

Words like:

```text
the
is
and
```

occur frequently but carry little meaning.

TF-IDF helps identify important words.

---

# Definition

**TF-IDF (Term Frequency – Inverse Document Frequency)** measures the importance of a word in a document relative to a collection of documents.

---

# Formula

## 1. Term Frequency (TF)

Measures frequency of a term within a document.

[
TF(t,d)=\frac{\text{Number of occurrences of term}}
{\text{Total terms in document}}
]

---

## 2. Document Frequency (DF)

Number of documents containing the term.

[
DF(t)
]

---

## 3. Inverse Document Frequency (IDF)

Measures uniqueness.

[
IDF(t)=\log \left(\frac{N}{DF(t)}\right)
]

where

N = Total documents

---

## Final TF-IDF

[
TF-IDF=TF\times IDF
]

---

# Numerical Example

Documents:

```text
D1: neural networks are powerful

D2: deep learning powers neural models

D3: networks and models are important
```

---

## Step 1: Calculate TF

Word:

```text
neural
```

In D1:

Occurs = 1

Total words = 4

[
TF=\frac{1}{4}
]

---

## Step 2: Calculate DF

"neural" appears in:

```text
D1
D2
```

Thus

[
DF=2
]

Total documents:

[
N=3
]

---

## Step 3: Calculate IDF

[
IDF=\log\left(\frac{3}{2}\right)
]

[
IDF=0.176
]

(approximately using log10)

---

## Step 4: TF-IDF

[
TF-IDF
======

\frac14 \times 0.176
]

[
=0.044
]

---

# Interpretation

High TF-IDF:

```text
Important and unique word
```

Low TF-IDF:

```text
Common word
```

---

# Applications

* Search Engines
* Information Retrieval
* Text Classification
* Keyword Extraction
* Recommendation Systems

---

# Advantages

* Simple and effective
* Removes importance of common words

---

# Limitations

* Ignores word order
* Ignores semantics

---

# Conclusion

TF-IDF is a statistical representation that measures how important a term is within a document collection by combining local frequency and global rarity.

---

# Exam Keywords

**Term Frequency, Document Frequency, Inverse Document Frequency, Feature Extraction, Information Retrieval, Keyword Weighting**

--- 

# G. Hidden Markov Model (HMM)

(Combines Q24)

# Question

**Describe Hidden Markov Model (HMM) with the help of an example. Explain its components and applications in NLP.**

---

# Answer

# Introduction

A Hidden Markov Model (HMM) is an extension of the Markov Model in which the actual states are hidden and only the outputs (observations) are visible.

It is one of the most important probabilistic models used in NLP for sequence prediction tasks such as Part-of-Speech (POS) tagging and Speech Recognition.

---

# Definition

A **Hidden Markov Model (HMM)** is a statistical model in which:

* The system moves through a sequence of hidden states.
* Each hidden state produces an observable output.
* The next state depends only on the current state (Markov Property).

---

# Why "Hidden"?

Consider POS Tagging.

Sentence:

```text
Dogs bark loudly
```

Observed words:

```text
Dogs bark loudly
```

Hidden states:

```text
Noun Verb Adverb
```

We can see the words but not their grammatical tags directly.

Therefore states are called **hidden**.

---

# Components of HMM

## 1. Hidden States

States that cannot be directly observed.

Example:

```text
Noun
Verb
Adjective
Adverb
```

---

## 2. Observations

Actual words observed.

Example:

```text
Dogs
Bark
Loudly
```

---

## 3. Transition Probability

Probability of moving from one hidden state to another.

[
P(S_t|S_{t-1})
]

Example:

[
P(Verb|Noun)
]

Meaning:

Probability that a Verb follows a Noun.

---

## 4. Emission Probability

Probability that a state emits a particular word.

[
P(Word|State)
]

Example:

[
P(Dogs|Noun)
]

---

## 5. Initial Probability

Probability of starting in a state.

[
P(State_1)
]

---

# HMM Structure

```text
Hidden States:

Noun → Verb → Adverb

      ↓      ↓      ↓

Observed Words:

Dogs → Bark → Loudly
```

---

# Example

Sentence:

```text
Time flies fast
```

Possible Hidden States:

```text
Time  → Noun
flies → Verb
fast  → Adverb
```

The HMM computes:

### Transition Probabilities

[
P(Verb|Noun)
]

[
P(Adverb|Verb)
]

### Emission Probabilities

[
P(Time|Noun)
]

[
P(flies|Verb)
]

[
P(fast|Adverb)
]

Final probability:

[
P(Sentence)=P(States)\times P(Observations|States)
]

---

# Working of HMM

### Step 1

Start from initial state.

---

### Step 2

Move to next state using transition probabilities.

---

### Step 3

Generate observed word using emission probabilities.

---

### Step 4

Repeat until sentence ends.

---

# Applications in NLP

### 1. Part-of-Speech Tagging

```text
Book a ticket
```

Determine whether "Book" is:

```text
Noun or Verb
```

---

### 2. Speech Recognition

Convert speech signals into text.

---

### 3. Named Entity Recognition

Identify names, places, organizations.

---

### 4. Machine Translation

Used in early statistical translation systems.

---

# Advantages

* Handles sequential data efficiently.
* Probabilistic framework.
* Works well for sequence labeling.

---

# Limitations

* Limited memory (Markov assumption).
* Cannot capture long-range dependencies.
* Less powerful than modern deep learning models.

---

# Conclusion

HMM is a probabilistic sequence model consisting of hidden states and observable outputs. It is widely used in NLP tasks such as POS tagging, speech recognition, and sequence prediction.

---

# Exam Keywords

**Hidden States, Observations, Transition Probability, Emission Probability, Sequence Modelling, POS Tagging, Viterbi Algorithm**

---

# H. Log-Linear Models

(Combines Q25)

# Question

**Explain the concept of Log-Linear Models in NLP. How do these models work and what are their applications?**

---

# Answer

# Introduction

Traditional probabilistic models estimate probabilities using frequency counts.

However, many NLP tasks require combining multiple features simultaneously.

Log-Linear Models provide a flexible framework for incorporating different features and assigning weights to them.

---

# Definition

A **Log-Linear Model** is a discriminative probabilistic model that predicts outcomes using weighted feature functions.

Instead of using direct counts, probabilities are calculated using exponentials of weighted features.

---

# Mathematical Formula

[
P(y|x)
======

\frac{\exp(w\cdot f(x,y))}
{Z(x)}
]

Where:

* (x) = input
* (y) = output
* (f(x,y)) = feature vector
* (w) = weight vector
* (Z(x)) = normalization factor

---

# Working

### Step 1: Extract Features

Example: Spam Detection

Email:

```text
Free offer! Click here.
```

Features:

```text
Contains "free"
Contains "offer"
Contains URL
```

---

### Step 2: Assign Weights

| Feature | Weight |
| ------- | ------ |
| free    | 2.0    |
| offer   | 1.5    |
| URL     | 1.8    |

---

### Step 3: Compute Score

[
Score=w\cdot f
]

Higher score ⇒ Higher probability.

---

### Step 4: Normalize

Convert scores into probabilities.

---

# Example

Sentence Classification

Input:

```text
I love this movie
```

Features:

```text
Contains positive words
Contains exclamation
Sentiment score
```

Model predicts:

```text
Positive
```

---

# Applications

### Text Classification

Spam detection.

### POS Tagging

Predict grammatical tags.

### Named Entity Recognition

Identify names and locations.

### Sentiment Analysis

Positive/negative classification.

---

# Advantages

* Can use many features.
* High prediction accuracy.
* Flexible and scalable.

---

# Limitations

* Feature engineering required.
* Training can be expensive.

---

# Conclusion

Log-linear models predict outcomes using weighted features and are widely used in classification and sequence-labeling tasks in NLP.

---

# Exam Keywords

**Feature Functions, Weighted Features, Conditional Probability, Discriminative Model, Maximum Entropy Model**

---

# I. Doc2Vec

(Combines Q26)

# Question

**Explain Doc2Vec and its use in generating document embeddings. Differentiate between Doc2Vec and Word2Vec.**

---

# Answer

# Introduction

Word2Vec generates vector representations for words.

However, many NLP tasks require representations of entire documents rather than individual words.

Doc2Vec extends Word2Vec to generate document-level embeddings.

---

# Definition

**Doc2Vec** is an unsupervised algorithm that learns fixed-length vector representations for documents, paragraphs, or sentences.

Proposed by:

**Le and Mikolov (2014).**

---

# Need for Doc2Vec

Consider two documents:

### D1

```text
Machine learning improves healthcare
```

### D2

```text
Deep learning improves medical diagnosis
```

Although words differ, meanings are similar.

Doc2Vec produces similar document vectors.

---

# Working of Doc2Vec

Each document is assigned a unique document ID.

Training learns:

* Word vectors
* Document vectors

Simultaneously.

---

# Types of Doc2Vec

## 1. PV-DM (Distributed Memory)

Similar to CBOW.

Uses:

```text
Context Words + Document Vector
```

to predict next word.

---

## 2. PV-DBOW (Distributed Bag of Words)

Similar to Skip-Gram.

Uses:

```text
Document Vector
```

to predict words.

---

# Example

Document:

```text
Artificial Intelligence improves healthcare
```

Output Vector:

```text
[0.25, 0.67, 0.12, ...]
```

Entire document represented by a single vector.

---

# Applications

### Document Classification

Classify news articles.

### Search Engines

Find similar documents.

### Recommendation Systems

Recommend articles.

### Clustering

Group similar documents.

---

# Doc2Vec vs Word2Vec

| Word2Vec                 | Doc2Vec                      |
| ------------------------ | ---------------------------- |
| Represents words         | Represents documents         |
| Output = word vectors    | Output = document vectors    |
| Captures word similarity | Captures document similarity |
| Smaller context          | Larger context               |
| Example: "king" vector   | Entire article vector        |

---

# Advantages

* Captures document meaning.
* Fixed-length representation.
* Useful for classification.

---

# Limitations

* Computationally expensive.
* Requires large training data.

---

# Conclusion

Doc2Vec extends Word2Vec by learning vector representations of complete documents and is widely used for document classification, retrieval, and similarity analysis.

---

# Exam Keywords

**Document Embeddings, Distributed Memory, PV-DM, PV-DBOW, Semantic Similarity, Vector Representation**

---

# J. Non-Negative Matrix Factorization (NMF)

(Combines Q27–Q28)

# Question

**Explain Non-Negative Matrix Factorization (NMF) in topic modelling. How does NMF differ from LDA? Show how NMF factorizes a document-term matrix and interpret the result.**

---

# Answer

# Introduction

Topic modelling aims to discover hidden topics from a collection of documents.

Besides LDA, another important topic modelling technique is **Non-Negative Matrix Factorization (NMF).**

---

# Definition

NMF is a matrix decomposition technique that factorizes a non-negative matrix into two smaller non-negative matrices.

[
V = W \times H
]

Where:

* (V) = Original Document-Term Matrix
* (W) = Document-Topic Matrix
* (H) = Topic-Word Matrix

---

# Basic Idea

Suppose:

```text
Documents
     ↓
Document-Term Matrix
     ↓
Factorization
     ↓
Topics
```

NMF discovers hidden topics by decomposing the matrix.

---

# Example

Document-Term Matrix

| Word    | D1 | D2 |
| ------- | -- | -- |
| AI      | 5  | 1  |
| GPU     | 4  | 1  |
| Cricket | 0  | 6  |
| Match   | 1  | 5  |

Matrix:

[
V=
\begin{bmatrix}
5 & 1\
4 & 1\
0 & 6\
1 & 5
\end{bmatrix}
]

---

# Factorization

NMF computes:

[
V=W\times H
]

### W (Document-Topic Matrix)

| Document | Topic 1 | Topic 2 |
| -------- | ------- | ------- |
| D1       | 0.9     | 0.1     |
| D2       | 0.2     | 0.8     |

---

### H (Topic-Word Matrix)

Topic 1:

```text
AI
GPU
Learning
```

Topic 2:

```text
Cricket
Match
Player
```

---

# Interpretation

### Topic 1

Technology

```text
AI
GPU
Learning
```

### Topic 2

Sports

```text
Cricket
Match
Player
```

Document D1 mainly belongs to Technology.

Document D2 mainly belongs to Sports.

---

# NMF vs LDA

| NMF                         | LDA                            |
| --------------------------- | ------------------------------ |
| Matrix factorization method | Probabilistic model            |
| Uses linear algebra         | Uses probability distributions |
| Faster training             | More computationally intensive |
| Easier interpretation       | More statistically rigorous    |
| Produces sparse topics      | Produces probabilistic topics  |
| Deterministic approach      | Generative approach            |

---

# Applications

* Topic Modelling
* Document Clustering
* Text Mining
* Recommendation Systems

---

# Advantages

* Easy to interpret.
* Fast computation.
* Produces meaningful topics.

---

# Limitations

* Need number of topics beforehand.
* May converge to local optimum.

---

# Conclusion

NMF is a matrix factorization-based topic modelling technique that decomposes a document-term matrix into document-topic and topic-word matrices. Compared to LDA, it is simpler, faster, and often easier to interpret.

---

# Unit 3 Most Important Topics for Exam (Priority Order)

⭐⭐⭐⭐⭐ **LDA**
⭐⭐⭐⭐⭐ **BERT**
⭐⭐⭐⭐⭐ **Bigram/Trigram + Smoothing Numericals**
⭐⭐⭐⭐⭐ **Language Models + Markov Models + Generative Models**
⭐⭐⭐⭐ **TF-IDF Numerical**
⭐⭐⭐⭐ **HMM**
⭐⭐⭐ **LSA**
⭐⭐⭐ **NMF vs LDA**
⭐⭐⭐ **Doc2Vec**
⭐⭐ **Log-Linear Models**

If you are short on time before tomorrow's exam, study in this order:

**LDA → BERT → Bigram/Trigram Numericals → Language Models/Markov Models → TF-IDF → HMM → LSA → NMF → Doc2Vec → Log-Linear Models.**

This covers almost all repeated long-answer questions and numericals from Unit 3.

