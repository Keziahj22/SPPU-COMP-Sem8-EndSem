# A. Information Retrieval (IR)

The following questions are repeated versions of the same concepts:

**Combined Questions:**

* Q1, Q2, Q3 → Information Retrieval Concept & NLP Role
* Q4 → IR Architecture
* Q5 → TF & IDF

---

# Question 1: What is Information Retrieval (IR)? Explain the concept of Information Retrieval and the significance of NLP in Information Retrieval.

*(Covers Q1, Q2, Q3)*

## Definition

Information Retrieval (IR) is the process of searching, retrieving, and presenting relevant information from a large collection of documents in response to a user's query.

The goal of IR is not simply to find exact matches but to retrieve the most relevant documents.

### Examples

* Google Search Engine
* Digital Libraries
* Web Search Systems
* Document Search Systems
* E-commerce Product Search

---

## Need for Information Retrieval

Today enormous amounts of information are available digitally.

Without IR:

* Searching becomes slow.
* Users must manually inspect documents.
* Finding relevant information becomes difficult.

IR helps retrieve relevant information efficiently.

---

## Working of Information Retrieval

### Step 1: Document Collection

Documents are gathered from various sources.

Examples:

* Books
* Articles
* Research Papers
* Web Pages

---

### Step 2: Document Processing

Documents undergo preprocessing:

#### Tokenization

Sentence:

```text
"NLP is an important field"
```

Tokens:

```text
NLP, is, an, important, field
```

---

#### Stop Word Removal

Remove common words.

```text
NLP important field
```

---

#### Stemming

```text
Learning → Learn
Running → Run
```

---

### Step 3: Indexing

An index is created to enable fast searching.

Example:

| Term     | Documents |
| -------- | --------- |
| NLP      | D1,D2     |
| Learning | D1,D3     |
| AI       | D2,D3     |

---

### Step 4: Query Processing

User query undergoes similar preprocessing.

Query:

```text
Machine Learning
```

becomes

```text
machine learn
```

---

### Step 5: Matching and Ranking

Documents are compared with query terms.

Relevant documents receive higher scores.

---

### Step 6: Retrieval

Ranked documents are shown to the user.

---

## Significance of NLP in Information Retrieval

NLP improves understanding of natural language queries and documents.

### 1. Query Understanding

User Query:

```text
"Best laptops for students"
```

NLP understands the intent rather than matching keywords only.

---

### 2. Stemming and Lemmatization

```text
Running
Runs
Ran
```

are treated as

```text
Run
```

---

### 3. Synonym Handling

```text
Car = Automobile
```

NLP identifies semantic similarity.

---

### 4. Named Entity Recognition

Identifies entities like:

```text
Virat Kohli → Person
India → Location
```

Improves retrieval accuracy.

---

### 5. Query Expansion

Query:

```text
AI
```

Expanded to:

```text
Artificial Intelligence
Machine Learning
Deep Learning
```

---

## Applications

* Search Engines
* Question Answering Systems
* Chatbots
* Recommendation Systems
* Digital Libraries

---

## Conclusion

Information Retrieval helps retrieve relevant information from large document collections. NLP enhances IR by understanding language, reducing ambiguity, and improving search accuracy.

---

# Question 2: Explain Information Retrieval Architecture with neat diagram.

*(Q4 – 8 Marks)*

## Definition

IR Architecture represents the complete workflow from storing documents to retrieving relevant information based on user queries.

---

## IR Architecture Diagram

```text
           DOCUMENTS
                |
                v
      -------------------
      | Preprocessing   |
      -------------------
                |
                v
      -------------------
      |   Indexing      |
      -------------------
                |
                v
      -------------------
      | Inverted Index  |
      -------------------

User Query
      |
      v
--------------------
| Query Processing |
--------------------
      |
      v
--------------------
| Matching Module  |
--------------------
      |
      v
--------------------
| Ranking Module   |
--------------------
      |
      v
 Retrieved Documents
```

---

## Components

### 1. Document Collection

Stores all available documents.

Examples:

* Articles
* Books
* Web Pages

---

### 2. Document Preprocessing

Performs:

* Tokenization
* Stop-word Removal
* Stemming
* Lemmatization

Example:

```text
"Machine Learning is Powerful"
```

↓

```text
Machine Learn Powerful
```

---

### 3. Indexing

Creates searchable indexes.

Example:

| Word    | Docs  |
| ------- | ----- |
| Machine | D1,D2 |
| Learn   | D1,D3 |

---

### 4. Query Processing

Processes the user query similarly.

Query:

```text
Machine Learning
```

↓

```text
Machine Learn
```

---

### 5. Matching Module

Compares query terms with indexed documents.

Methods:

* Boolean Model
* Vector Space Model
* Probabilistic Model

---

### 6. Ranking Module

Assigns relevance scores.

Example:

| Document | Score |
| -------- | ----- |
| D1       | 0.95  |
| D2       | 0.75  |
| D3       | 0.50  |

---

### 7. Result Presentation

Displays top-ranked documents.

---

## Advantages

* Faster searching
* Reduced retrieval time
* Efficient ranking
* Scalable for large datasets

---

## Conclusion

IR Architecture systematically processes documents and user queries to efficiently retrieve the most relevant information.

---

# Question 3: Define Term Frequency (TF) and Inverse Document Frequency (IDF).

*(Q5 – 6 Marks)*

## 1. Term Frequency (TF)

### Definition

Term Frequency measures how frequently a term appears in a document.

It indicates the importance of a word within a document.

---

### Formula

```text
TF(t,d) =
Number of occurrences of term t in document d
------------------------------------------------
Total terms in document d
```

---

### Example

Document:

```text
"NLP is useful. NLP is interesting."
```

Total words = 5

Occurrences of NLP = 2

Therefore,

```text
TF(NLP)=2/5=0.4
```

---

## Advantages of TF

* Simple to compute
* Measures local importance

---

## Limitation

Frequently occurring words may not always be important.

---

## 2. Inverse Document Frequency (IDF)

### Definition

IDF measures how unique or rare a term is across the document collection.

Rare terms receive higher weights.

---

### Formula

```text
IDF(t)=log(N/df)
```

Where:

N = Total number of documents

df = Number of documents containing the term

---

### Example

Suppose:

```text
Total Documents = 100
```

Word "NLP" appears in:

```text
5 documents
```

Then

```text
IDF(NLP)=log(100/5)
          =log(20)
```

High IDF indicates a more informative word.

---

## Why IDF is Needed?

Common words like:

```text
the
is
and
```

appear in almost every document.

Such words should receive lower importance.

---

## TF-IDF

TF and IDF are usually combined.

### Formula

```text
TF-IDF = TF × IDF
```

---

## Example

If:

```text
TF = 0.4
IDF = 2
```

Then:

```text
TF-IDF = 0.8
```

Higher TF-IDF means greater importance.

---

## Advantages of TF-IDF

* Widely used in search engines
* Identifies important words
* Improves document ranking

---

## Conclusion

TF measures frequency within a document, whereas IDF measures rarity across documents. Together TF-IDF provides a powerful weighting scheme for Information Retrieval.
# B. Vector Space Model (VSM)

The following questions are repeated versions of the same topic:

**Combined Questions:**

* Q6, Q7, Q8, Q9 → Vector Space Model (VSM), document/query representation, similarity calculation, strengths and weaknesses.

---

# Question 4: Explain the Vector Space Model (VSM) in Information Retrieval. How are documents and queries represented and how is relevance computed between them? Discuss its strengths and weaknesses.

*(Covers Q6, Q7, Q8, Q9 – 4M to 9M)*

---

## Introduction

The Vector Space Model (VSM) is one of the most widely used Information Retrieval models.

It represents documents and user queries as vectors in a multidimensional space.

Each unique term in the collection forms one dimension.

The relevance of a document to a query is determined by calculating the similarity between their vectors.

Proposed by **Gerard Salton**.

---

## Definition

Vector Space Model is a mathematical model in which:

* Documents are represented as vectors.
* Queries are represented as vectors.
* Similarity between vectors determines relevance.

The more similar the vectors, the more relevant the document is to the query.

---

## Basic Idea

Instead of exact keyword matching, VSM measures how closely a document resembles a query.

### Example

Query:

```text
Machine Learning
```

Documents:

```text
D1 = Machine Learning Basics
D2 = Cricket Match Analysis
```

D1 is more similar to the query than D2.

Therefore D1 gets a higher ranking.

---

# Document Representation

Consider two documents:

```text
D1 = "I like NLP"
D2 = "I like Machine Learning"
```

Vocabulary:

```text
[I, Like, NLP, Machine, Learning]
```

Each word becomes a dimension.

---

### Vector Representation

```text
D1 = [1,1,1,0,0]

D2 = [1,1,0,1,1]
```

Meaning:

| Term     | D1 | D2 |
| -------- | -- | -- |
| I        | 1  | 1  |
| Like     | 1  | 1  |
| NLP      | 1  | 0  |
| Machine  | 0  | 1  |
| Learning | 0  | 1  |

---

# Query Representation

Query:

```text
Machine Learning
```

Vector:

```text
Q = [0,0,0,1,1]
```

Now similarity between Q and each document can be calculated.

---

# Term Weighting using TF-IDF

Not all words are equally important.

Words are assigned weights using TF-IDF.

---

## Term Frequency (TF)

Measures frequency of a word in a document.

Formula:

```text
TF(t,d) =
Number of times term appears in document
```

Example:

```text
"NLP NLP NLP AI"
```

TF(NLP) = 3

---

## Inverse Document Frequency (IDF)

Measures rarity of a word.

Formula:

```text
IDF(t)=log(N/df)
```

Where:

* N = Total documents
* df = Number of documents containing term

Rare words receive higher weight.

---

## TF-IDF

Formula:

```text
TF-IDF = TF × IDF
```

Important words receive larger weights.

---

# Similarity Computation

Most commonly done using **Cosine Similarity**.

---

## Cosine Similarity Formula

```text
Cos(Q,D)=
(Q·D)/(||Q|| ||D||)
```

Where:

* Q = Query vector
* D = Document vector
* Q·D = Dot Product
* ||Q|| = Magnitude of Query
* ||D|| = Magnitude of Document

---

## Interpretation

| Cosine Value | Meaning             |
| ------------ | ------------------- |
| 1            | Perfect Match       |
| 0.8          | Highly Relevant     |
| 0.5          | Moderately Relevant |
| 0            | No Similarity       |

---

# Example of Similarity Calculation

Query:

```text
Machine Learning
```

Vocabulary:

```text
Machine Learning AI Cricket
```

Query Vector:

```text
Q=[1,1,0,0]
```

Document D1:

```text
Machine Learning AI
```

Vector:

```text
D1=[1,1,1,0]
```

Document D2:

```text
Cricket Match
```

Vector:

```text
D2=[0,0,0,1]
```

---

### Similarity with D1

Dot Product:

```text
1×1 + 1×1 = 2
```

High similarity.

---

### Similarity with D2

Dot Product:

```text
0
```

No similarity.

Therefore:

```text
D1 > D2
```

D1 is retrieved first.

---

# VSM Architecture

```text
Documents
     |
     v
Tokenization
     |
     v
TF-IDF Weighting
     |
     v
Vector Representation
     |
     v
Similarity Calculation
     |
     v
Ranking
     |
     v
Retrieved Documents
```

---

# Advantages of VSM

### 1. Partial Matching

Documents need not exactly match the query.

Example:

Query:

```text
Artificial Intelligence
```

Document:

```text
Introduction to AI
```

Still considered relevant.

---

### 2. Ranking Support

Documents are ranked by similarity score.

---

### 3. Easy Implementation

Simple mathematical model.

---

### 4. Efficient Retrieval

Works well for large collections.

---

### 5. Supports TF-IDF

Can identify important terms.

---

# Disadvantages of VSM

### 1. Ignores Word Order

Sentences:

```text
Dog bites man
Man bites dog
```

May appear similar.

---

### 2. High Dimensionality

Large vocabulary creates huge vectors.

---

### 3. Cannot Understand Meaning

```text
Car
Automobile
```

Different words despite same meaning.

---

### 4. Synonym Problem

Similar words treated differently.

---

### 5. Polysemy Problem

Same word with multiple meanings.

Example:

```text
Bank
```

Can mean:

* River bank
* Financial bank

VSM cannot distinguish easily.

---

# Applications of VSM

### Search Engines

Google-like retrieval systems.

### Document Ranking

Ranking web pages.

### Text Classification

Spam filtering.

### Recommendation Systems

Content recommendation.

### Question Answering

Finding relevant answers.

---

# Conclusion

The Vector Space Model is a fundamental Information Retrieval technique that represents documents and queries as vectors. Similarity is typically measured using cosine similarity and TF-IDF weighting. Despite limitations such as ignoring semantics and word order, VSM remains one of the most important and widely used retrieval models.

---

# Quick Exam Points (Last-Minute Revision)

### Definition

* Documents and queries represented as vectors.
* Similarity determines relevance.

### Key Components

* Vocabulary
* TF
* IDF
* TF-IDF
* Cosine Similarity

### Formula

```text
TF-IDF = TF × IDF
```

```text
Cos(Q,D)=
(Q·D)/(||Q|| ||D||)
```

### Advantages

* Partial matching
* Ranking support
* Easy implementation
* Efficient retrieval

### Disadvantages

* Ignores semantics
* Ignores word order
* High dimensionality
* Synonym & polysemy problems

---

# C. Named Entity Recognition (NER)

**Combined Questions:**

* Q10 + Q11 → NER with Evaluation Metrics
* Q12 → Short Definition
* Q13 → NER System Building Process

--- 
# C. Named Entity Recognition (NER)

The following questions are repeated versions of the same topic:

### Combined Questions

**Q10 + Q11**

* What is Named Entity Recognition (NER)?
* Evaluation metrics of NER.
* Methods used for evaluating NER systems.

**Q13**

* NER System Building Process using supervised learning.

**Q12**

* Short definition (2 marks).

---

# Question 5: What is Named Entity Recognition (NER)? Explain NER and the various metrics used for evaluation.

*(Covers Q10, Q11, Q12 – 2M, 4M, 8M, 9M)*

---

## Introduction

Named Entity Recognition (NER) is one of the most important tasks in Natural Language Processing.

NER identifies and classifies important entities in text into predefined categories such as:

* Person
* Organization
* Location
* Date
* Time
* Money
* Percentage
* Product

It converts unstructured text into structured information.

---

## Definition

Named Entity Recognition (NER) is the process of identifying named entities in text and classifying them into predefined categories.

---

## Example

Sentence:

```text
"Virat Kohli plays cricket for BCCI in India."
```

NER Output:

| Word        | Entity Type  |
| ----------- | ------------ |
| Virat Kohli | PERSON       |
| BCCI        | ORGANIZATION |
| India       | LOCATION     |

---

Another Example:

```text
"Apple launched iPhone 16 in California on 10 June 2026."
```

Output:

| Entity       | Type         |
| ------------ | ------------ |
| Apple        | ORGANIZATION |
| iPhone 16    | PRODUCT      |
| California   | LOCATION     |
| 10 June 2026 | DATE         |

---

# Need for NER

Large amounts of text contain useful information.

NER helps computers identify important entities automatically.

Without NER:

```text
Virat Kohli plays for India.
```

is just text.

With NER:

```text
Virat Kohli → PERSON
India → LOCATION
```

becomes structured data.

---

# Applications of NER

### 1. Search Engines

Understanding search queries.

Example:

```text
Hotels in Pune
```

Pune recognized as LOCATION.

---

### 2. Chatbots

Understanding people, places and organizations.

---

### 3. Question Answering Systems

Question:

```text
Who is the CEO of Google?
```

NER identifies person names.

---

### 4. Information Extraction

Extracting structured information from documents.

---

### 5. Healthcare

Extracting diseases, medicines and symptoms.

---

### 6. Financial Systems

Identifying company names, stock names and currencies.

---

# Approaches for NER

---

## 1. Rule-Based Approach

Uses manually written linguistic rules.

Example:

```text
Words starting with capital letters
→ Person names
```

Advantages:

* Easy for small datasets.

Disadvantages:

* Difficult to maintain.

---

## 2. Machine Learning Approach

Learns patterns from labeled data.

Algorithms:

* Hidden Markov Model (HMM)
* Maximum Entropy Model
* Conditional Random Field (CRF)
* Support Vector Machine (SVM)

---

## 3. Deep Learning Approach

Modern NER systems use:

* RNN
* LSTM
* Bi-LSTM
* Transformers
* BERT

Advantages:

* Higher accuracy.
* Learns contextual information.

---

# NER Evaluation Metrics

After building an NER model, its performance must be measured.

The most common metrics are:

### 1. Precision

### Definition

Precision measures how many identified entities are actually correct.

Formula:

```text
Precision =
Correctly Identified Entities
--------------------------------
Total Identified Entities
```

---

### Example

System predicts:

```text
10 entities
```

Correctly predicts:

```text
8 entities
```

Precision:

```text
8/10 = 0.8 = 80%
```

---

### Interpretation

High Precision means:

```text
Few False Positives
```

---

## 2. Recall

### Definition

Recall measures how many actual entities were successfully identified.

Formula:

```text
Recall =
Correctly Identified Entities
--------------------------------
Actual Entities Present
```

---

### Example

Actual entities:

```text
12
```

Detected entities:

```text
8
```

Recall:

```text
8/12 = 0.67 = 67%
```

---

### Interpretation

High Recall means:

```text
Few False Negatives
```

---

## 3. F1-Score

### Definition

F1 Score combines Precision and Recall.

Formula:

```text
F1 =
2 × Precision × Recall
-------------------------
Precision + Recall
```

---

### Example

Precision = 80%

Recall = 67%

F1:

```text
≈ 73%
```

---

### Importance

Provides balanced performance evaluation.

---

# Confusion Matrix Terms

NER evaluation also uses:

### True Positive (TP)

Correctly identified entity.

Example:

```text
Virat Kohli → PERSON
```

Predicted correctly.

---

### False Positive (FP)

Wrongly identified entity.

Example:

```text
Cricket → PERSON
```

Incorrect.

---

### False Negative (FN)

Entity exists but not detected.

Example:

```text
India
```

present but not recognized.

---

# Error Analysis of NER Systems

Evaluation results help improve systems.

Common errors:

### 1. Boundary Errors

Example:

```text
New York City
```

Predicted:

```text
New York
```

---

### 2. Classification Errors

Example:

```text
Apple
```

Predicted as PRODUCT instead of ORGANIZATION.

---

### 3. Missing Entity Errors

Entity not detected at all.

---

# Advantages of NER

* Converts text into structured data.
* Improves search engines.
* Helps information extraction.
* Useful for analytics and knowledge graphs.

---

# Limitations

* Ambiguous names.
* Domain dependence.
* Requires labeled training data.
* Multiple meanings of same entity.

Example:

```text
Apple
```

Can be:

* Fruit
* Company

---

# Conclusion

Named Entity Recognition is a fundamental NLP task that identifies and classifies entities such as people, organizations and locations. Performance is commonly measured using Precision, Recall and F1-score. Modern deep learning approaches have significantly improved NER accuracy.

---

# Question 6: Describe the Named Entity Recognition (NER) System Building Process using a supervised learning approach.

*(Q13 – 9 Marks)*

---

## Introduction

A supervised NER system learns from labeled examples where entities are already tagged.

The goal is to train a model that can identify entities in unseen text.

---

## Example Sentence

```text
"Virat Kohli plays for BCCI in India."
```

Training Labels:

| Word  | Label |
| ----- | ----- |
| Virat | B-PER |
| Kohli | I-PER |
| plays | O     |
| for   | O     |
| BCCI  | B-ORG |
| in    | O     |
| India | B-LOC |

---

# Steps in Building NER System

---

## Step 1: Data Collection

Collect text data.

Sources:

* News Articles
* Social Media
* Research Documents
* Medical Records

---

## Step 2: Data Annotation

Manually label entities.

Example:

```text
Virat Kohli → PERSON
India → LOCATION
```

Creates training dataset.

---

## Step 3: Text Preprocessing

Perform:

### Tokenization

```text
Virat | Kohli | plays | cricket
```

---

### Stop Word Handling

Optional.

---

### POS Tagging

Assign grammatical categories.

Example:

```text
Virat → Noun
plays → Verb
```

---

## Step 4: Feature Extraction

Extract useful information.

Features:

### Word Features

```text
Virat
```

---

### Capitalization

Starts with capital letter.

---

### Prefix/Suffix

```text
Kohli
```

suffix patterns.

---

### Context Words

Neighboring words.

---

### POS Tags

Grammatical information.

---

## Step 5: Model Selection

Train machine learning model.

Common models:

### Traditional

* HMM
* CRF
* SVM

### Deep Learning

* Bi-LSTM
* Bi-LSTM + CRF
* BERT

---

## Step 6: Training

Feed labeled examples to the model.

The model learns patterns.

Example:

```text
Capitalized words after "Mr."
→ likely PERSON
```

---

## Step 7: Prediction

Apply trained model to unseen text.

Input:

```text
Sachin lives in Mumbai.
```

Output:

```text
Sachin → PERSON
Mumbai → LOCATION
```

---

## Step 8: Evaluation

Evaluate using:

* Precision
* Recall
* F1 Score

---

## Step 9: Error Analysis and Improvement

Analyze mistakes.

Improve through:

* More training data
* Better features
* Better model architecture

---

# NER System Building Diagram

```text
Training Data
      ↓
Annotation
      ↓
Preprocessing
      ↓
Feature Extraction
      ↓
Model Training
      ↓
NER Model
      ↓
Prediction
      ↓
Evaluation
```

---

# Advantages of Supervised NER

* High accuracy.
* Learns complex patterns.
* Adaptable to domains.

---

# Disadvantages

* Requires large labeled datasets.
* Annotation is expensive.
* Domain specific.

---

# Conclusion

A supervised NER system is built by collecting labeled data, preprocessing text, extracting features, training a model and evaluating performance using Precision, Recall and F1-score. Modern systems use Bi-LSTM and BERT for state-of-the-art results.

---

## Quick 2-Mark Answer

### What is Named Entity Recognition (NER)?

**Definition:**

Named Entity Recognition (NER) is an NLP task that identifies and classifies named entities in text into predefined categories such as Person, Organization, Location, Date, Time and Money.

**Example:**

```text
"Virat Kohli lives in India."
```

Output:

```text
Virat Kohli → PERSON
India → LOCATION
```

---

Next Unit:
**D. Entity Extraction, Relation Extraction & Comparison with Coreference Resolution (Q14–Q18)** which is usually asked as an 8–9 mark question.
# D. Entity Extraction & Relation Extraction

The following questions are repeated versions of the same topic:

### Combined Questions

**Q14 + Q15 + Q16 + Q17**

* Entity Extraction
* Relation Extraction
* Difference between Entity Extraction and NER
* Importance, techniques and applications

**Q18**

* Compare Entity Extraction, Relation Extraction and Coreference Resolution

---

# Question 7: Explain Entity Extraction and Relation Extraction with examples. Discuss their importance, techniques, relationship with NER, and applications.

*(Covers Q14, Q15, Q16, Q17 – 6M to 9M)*

---

# Introduction

Large amounts of information exist in unstructured text such as:

* News articles
* Social media posts
* Research papers
* Medical records

To make this information useful, NLP systems extract entities and relationships from text.

These tasks form the foundation of:

* Knowledge Graphs
* Search Engines
* Question Answering Systems
* Information Retrieval Systems

---

# Entity Extraction

## Definition

Entity Extraction is the process of identifying and extracting meaningful entities from text.

Entities may include:

* Person
* Organization
* Location
* Product
* Date
* Event
* Disease
* Money

Entity Extraction converts unstructured text into structured information.

---

## Example

Sentence:

```text
"Virat Kohli plays for BCCI in India."
```

Extracted Entities:

| Entity      | Type         |
| ----------- | ------------ |
| Virat Kohli | Person       |
| BCCI        | Organization |
| India       | Location     |

---

## Another Example

Sentence:

```text
"Apple launched iPhone 16 in California."
```

Extracted Entities:

| Entity     | Type         |
| ---------- | ------------ |
| Apple      | Organization |
| iPhone 16  | Product      |
| California | Location     |

---

# Working of Entity Extraction

### Step 1: Input Text

```text
"Virat Kohli plays for BCCI."
```

↓

### Step 2: Tokenization

```text
Virat | Kohli | plays | for | BCCI
```

↓

### Step 3: Feature Extraction

Identify:

* Capitalization
* POS tags
* Context

↓

### Step 4: Entity Classification

```text
Virat Kohli → Person
BCCI → Organization
```

↓

### Step 5: Structured Output

Store extracted entities.

---

# Techniques Used for Entity Extraction

---

## 1. Rule-Based Methods

Uses handcrafted rules.

Example:

```text
Words beginning with capital letters
→ likely entity
```

Advantages:

* Simple

Disadvantages:

* Poor scalability

---

## 2. Machine Learning Methods

Algorithms:

* HMM
* CRF
* SVM

Learn patterns from annotated data.

---

## 3. Deep Learning Methods

Modern approaches use:

* RNN
* LSTM
* Bi-LSTM
* Transformers
* BERT

Advantages:

* Higher accuracy
* Better contextual understanding

---

# Importance of Entity Extraction

### 1. Information Retrieval

Improves search relevance.

---

### 2. Search Engines

Recognizes important entities in queries.

---

### 3. Knowledge Graph Construction

Creates entity databases.

---

### 4. Healthcare

Extracts:

* Diseases
* Medicines
* Symptoms

---

### 5. Financial Analysis

Extracts:

* Companies
* Stocks
* Financial events

---

# Entity Extraction vs NER

This is frequently asked in exams.

| NER                         | Entity Extraction                        |
| --------------------------- | ---------------------------------------- |
| Identifies named entities   | Extracts entities and useful information |
| Focused task                | Broader task                             |
| Finds PERSON, LOCATION etc. | Finds entities, attributes and metadata  |
| Subset of Entity Extraction | Parent concept                           |

---

## Example

Sentence:

```text
"Apple launched iPhone 16."
```

### NER Output

```text
Apple → Organization
iPhone 16 → Product
```

### Entity Extraction Output

```text
Organization: Apple
Product: iPhone 16
Event: Launch
```

More information is extracted.

---

# Relation Extraction

## Definition

Relation Extraction identifies relationships between extracted entities.

It answers:

```text
How are entities connected?
```

---

## Example

Sentence:

```text
"Virat Kohli plays for BCCI."
```

Entities:

```text
Virat Kohli
BCCI
```

Relation:

```text
plays_for
```

Output:

```text
(Virat Kohli, plays_for, BCCI)
```

---

# Another Example

Sentence:

```text
"Satya Nadella is CEO of Microsoft."
```

Entities:

```text
Satya Nadella
Microsoft
```

Relation:

```text
CEO_of
```

Output:

```text
(Satya Nadella, CEO_of, Microsoft)
```

---

# Relation Extraction Process

### Step 1

Entity Extraction

↓

### Step 2

Identify candidate entity pairs

↓

### Step 3

Analyze surrounding words

↓

### Step 4

Determine relationship

↓

### Step 5

Store relationship

---

# Example

Sentence:

```text
"Rohit Sharma plays for Mumbai Indians."
```

Entities:

```text
Rohit Sharma
Mumbai Indians
```

Relation:

```text
plays_for
```

Output:

```text
(Rohit Sharma, plays_for, Mumbai Indians)
```

---

# Techniques for Relation Extraction

---

## 1. Rule-Based

Uses predefined linguistic rules.

Example:

```text
X works at Y
```

Infer:

```text
works_for(X,Y)
```

---

## 2. Supervised Learning

Uses labeled examples.

Algorithms:

* SVM
* CRF
* Neural Networks

---

## 3. Deep Learning

Uses:

* CNN
* LSTM
* BERT

Learns relations automatically.

---

# Applications of Relation Extraction

### Knowledge Graphs

Google Knowledge Graph.

---

### Question Answering

Question:

```text
Who is CEO of Microsoft?
```

Uses extracted relations.

---

### Chatbots

Improves understanding.

---

### Information Retrieval

Enhances search relevance.

---

### Recommendation Systems

Identifies relationships among products and users.

---

# Entity Extraction + Relation Extraction Example

Sentence:

```text
"Sachin Tendulkar played for Mumbai Indians."
```

Entity Extraction:

```text
Sachin Tendulkar → Person
Mumbai Indians → Organization
```

Relation Extraction:

```text
(Sachin Tendulkar, played_for, Mumbai Indians)
```

This creates structured knowledge.

---

# Conclusion

Entity Extraction identifies important entities from text, while Relation Extraction identifies how those entities are connected. Together they convert unstructured text into structured knowledge useful for search engines, knowledge graphs, chatbots and question-answering systems.

---

# Question 8: Compare Entity Extraction, Relation Extraction and Coreference Resolution. How do they contribute to building knowledge from unstructured text?

*(Q18 – 8 Marks)*

---

# Introduction

Entity Extraction, Relation Extraction and Coreference Resolution are fundamental Information Extraction tasks.

Together they transform raw text into structured knowledge.

---

## Example Text

```text
"Virat Kohli plays for BCCI.
He is one of the best batsmen."
```

---

# 1. Entity Extraction

Identifies entities.

Output:

```text
Virat Kohli → Person
BCCI → Organization
```

Answers:

```text
Who are the important entities?
```

---

# 2. Relation Extraction

Identifies relationships.

Output:

```text
(Virat Kohli, plays_for, BCCI)
```

Answers:

```text
How are entities connected?
```

---

# 3. Coreference Resolution

Identifies references to the same entity.

Output:

```text
He → Virat Kohli
```

Answers:

```text
Who does "He" refer to?
```

---

# Comparison Table

| Feature           | Entity Extraction     | Relation Extraction         | Coreference Resolution         |
| ----------------- | --------------------- | --------------------------- | ------------------------------ |
| Purpose           | Identify entities     | Identify relationships      | Identify references            |
| Output            | Person, Location etc. | Entity pairs with relations | Linked mentions                |
| Question Answered | What entities exist?  | How are they related?       | Who/what is being referred to? |
| Example           | Virat Kohli → Person  | (Virat, plays_for, BCCI)    | He → Virat Kohli               |

---

# Combined Example

Sentence:

```text
"Ratan Tata joined Tata Group. He later became its chairman."
```

### Entity Extraction

```text
Ratan Tata → Person
Tata Group → Organization
```

### Relation Extraction

```text
(Ratan Tata, joined, Tata Group)
```

### Coreference Resolution

```text
He → Ratan Tata
its → Tata Group
```

---

# Contribution to Knowledge Building

These tasks collectively create structured knowledge.

Example:

```text
"Satya Nadella is CEO of Microsoft.
He joined Microsoft in 1992."
```

### Entity Extraction

```text
Satya Nadella
Microsoft
```

### Relation Extraction

```text
(Satya Nadella, CEO_of, Microsoft)
(Satya Nadella, joined, Microsoft)
```

### Coreference Resolution

```text
He → Satya Nadella
```

Final knowledge graph becomes possible.

---

# Conclusion

Entity Extraction identifies entities, Relation Extraction identifies connections between entities, and Coreference Resolution links references to the same entity. Together they are essential for building knowledge graphs, search engines, chatbots, information retrieval systems and intelligent NLP applications.

---

# Quick Exam Difference Table (Very Important)

| NER                   | Entity Extraction                 | Relation Extraction       | Coreference Resolution |
| --------------------- | --------------------------------- | ------------------------- | ---------------------- |
| Finds entities        | Extracts entities and information | Finds relationships       | Finds references       |
| Person, Location etc. | Broader task                      | Entity connections        | Pronoun/entity linking |
| Example: India → LOC  | Extract Apple, iPhone             | Apple manufactures iPhone | It → iPhone            |

---

Next Topic:

# E. Reference Resolution & Coreference Resolution (Q19–Q22)

(8-mark question with diagrams and examples) and then **F. CLIR (Q23–Q27)**.
    # F. Cross-Lingual Information Retrieval (CLIR)

### Combined Questions

The following questions are repeated versions of the same topic:

* Q23. What is Cross-Lingual Information Retrieval and how is it used in NLP?
* Q24. Explain CLIR with example.
* Q25. Explain the concept of CLIR. Discuss challenges and techniques used.
* Q26. Define CLIR and discuss challenges. How does machine translation assist?
* Q27. What is CLIR? Discuss challenges and different approaches.

---

# Question: Explain Cross-Lingual Information Retrieval (CLIR). Discuss its architecture, approaches, challenges, machine translation techniques, applications, advantages and limitations.

*(Covers Q23–Q27, 6M–9M)*

---

# Introduction

Traditional Information Retrieval (IR) assumes that the user's query and the documents are written in the same language.

However, information on the internet is available in many languages.

A user may submit a query in one language while relevant documents exist in another language.

Cross-Lingual Information Retrieval (CLIR) solves this problem.

---

# Definition

Cross-Lingual Information Retrieval (CLIR) is the process of retrieving documents written in one language using a query written in a different language.

In simple words:

```text
Query Language ≠ Document Language
```

Yet relevant documents can still be retrieved.

---

# Example

Suppose a user enters the query:

```text
"Artificial Intelligence"
```

in English.

The document collection contains Hindi documents:

```text
"कृत्रिम बुद्धिमत्ता"
```

A CLIR system translates and retrieves the relevant Hindi documents.

Thus:

```text
English Query
      ↓
Translation
      ↓
Hindi Documents Retrieved
```

---

# Need for CLIR

The internet contains multilingual information.

Many users:

* Know only one language.
* Need access to foreign-language information.
* Search across international databases.

Without CLIR:

```text
English query
```

cannot retrieve

```text
Hindi, Marathi, French, Chinese
```

documents.

With CLIR:

all relevant documents can be accessed.

---

# CLIR Architecture

### Neat Diagram

```text
             User Query
                   |
                   v
         Language Identification
                   |
                   v
         Translation Module
                   |
                   v
         Query Processing
                   |
                   v
          Search Engine
                   |
                   v
          Ranking Module
                   |
                   v
         Retrieved Documents
```

---

# Working of CLIR

---

## Step 1: User Query

User enters query.

Example:

```text
Tourism in India
```

---

## Step 2: Language Detection

System identifies query language.

Example:

```text
English
```

---

## Step 3: Translation

Query is translated into target language.

Example:

```text
Tourism in India
```

↓

```text
भारत में पर्यटन
```

---

## Step 4: Search

Translated query is searched against document collection.

---

## Step 5: Ranking

Relevant documents are ranked according to similarity.

---

## Step 6: Retrieval

Top matching documents are returned.

---

# Approaches to CLIR

This is one of the most important exam questions.

There are three major approaches.

---

# 1. Query Translation Approach

Most commonly used.

The user query is translated into the language of the documents.

---

### Example

English Query:

```text
Machine Learning
```

Translated to Hindi:

```text
मशीन लर्निंग
```

Search performed on Hindi documents.

---

### Advantages

* Fast
* Cheap
* Requires translating only query

---

### Disadvantages

* Translation errors affect retrieval
* Ambiguous words cause problems

---

# 2. Document Translation Approach

All documents are translated into the query language.

---

### Example

Hindi documents:

```text
भारत में पर्यटन
```

Translated into English:

```text
Tourism in India
```

Now search is performed.

---

### Advantages

* Accurate retrieval

---

### Disadvantages

* Expensive
* Time consuming
* Large storage requirement

---

# 3. Interlingua Approach

Both query and documents are converted into a language-independent representation.

---

### Example

English:

```text
Computer
```

Hindi:

```text
कंप्यूटर
```

French:

```text
Ordinateur
```

All mapped to a common concept:

```text
COMPUTER
```

Search is performed on the common representation.

---

### Advantages

* Supports many languages

---

### Disadvantages

* Difficult to design
* Complex implementation

---

# Role of Machine Translation in CLIR

Machine Translation (MT) is the backbone of CLIR.

It automatically converts text from one language to another.

---

## Example

Query:

```text
Climate Change
```

Machine Translation:

```text
जलवायु परिवर्तन
```

The translated query is then used for retrieval.

---

## Benefits of Machine Translation

* Eliminates language barriers
* Enables multilingual search
* Improves accessibility
* Supports global information sharing

---

# Challenges in CLIR

Very frequently asked in exams.

---

## 1. Translation Ambiguity

A word may have multiple meanings.

Example:

```text
Bank
```

Can mean:

```text
River Bank
```

or

```text
Financial Bank
```

Incorrect translation causes retrieval errors.

---

## 2. Synonym Problem

Different words may have the same meaning.

Example:

```text
Car
Automobile
Vehicle
```

System must recognize semantic similarity.

---

## 3. Morphological Differences

Languages have different grammatical structures.

Example:

English:

```text
play
playing
played
```

Hindi may use different word forms.

---

## 4. Resource Scarcity

Many languages lack:

* Dictionaries
* Corpora
* Annotated datasets

Example:

Low-resource Indian languages.

---

## 5. Cultural Differences

Certain concepts may not translate directly.

Example:

Idioms and expressions.

---

## 6. Named Entity Translation

Example:

```text
Mumbai
Google
Virat Kohli
```

Should remain unchanged.

Incorrect translation reduces accuracy.

---

## 7. Ranking Issues

Documents from different languages may receive different scores.

Ranking consistency becomes difficult.

---

# Techniques Used in CLIR

---

## 1. Dictionary-Based Translation

Uses bilingual dictionaries.

Example:

```text
Computer → कंप्यूटर
```

---

## 2. Machine Translation

Uses systems like:

* Google Translate
* Neural MT Models

Most widely used.

---

## 3. Statistical Translation Models

Uses probabilities learned from parallel corpora.

---

## 4. Neural Network Models

Uses:

* Transformer
* mBERT
* XLM-R

Provides higher accuracy.

---

## 5. Multilingual Embeddings

Words from different languages represented in a common vector space.

Example:

```text
Dog
कुत्ता
Chien
```

All represented closely in embedding space.

---

# Applications of CLIR

---

## 1. Search Engines

Users search in one language and retrieve results from multiple languages.

---

## 2. Digital Libraries

Access research papers written in various languages.

---

## 3. Government Portals

Access multilingual government documents.

---

## 4. E-Commerce

Search products across different languages.

---

## 5. Healthcare Systems

Retrieve medical information from international databases.

---

## 6. News Aggregation

Collect news from multiple languages.

---

## 7. Academic Research

Researchers access papers worldwide.

---

# Advantages of CLIR

### 1. Breaks Language Barriers

Users can access foreign-language information.

---

### 2. Global Information Access

Information becomes universally available.

---

### 3. Supports Multilingual Users

Useful in countries like India.

---

### 4. Improves Knowledge Sharing

Encourages international collaboration.

---

### 5. Expands Search Coverage

Retrieves more relevant documents.

---

# Limitations of CLIR

### 1. Translation Errors

Incorrect translations reduce accuracy.

---

### 2. High Computational Cost

Translation requires processing power.

---

### 3. Resource Requirements

Needs multilingual corpora and dictionaries.

---

### 4. Ambiguity Problems

Words with multiple meanings create confusion.

---

# CLIR vs Traditional IR

| Feature            | Traditional IR    | CLIR                     |
| ------------------ | ----------------- | ------------------------ |
| Query Language     | Same as documents | Different from documents |
| Translation Needed | No                | Yes                      |
| Complexity         | Low               | High                     |
| Search Scope       | Single language   | Multiple languages       |
| Example            | English → English | English → Hindi          |

---

# Conclusion

Cross-Lingual Information Retrieval (CLIR) is an advanced Information Retrieval technique that enables users to retrieve documents written in different languages from the query language. It relies heavily on machine translation, multilingual embeddings and cross-language semantic representations. Despite challenges such as translation ambiguity and resource scarcity, CLIR plays a crucial role in multilingual search engines, digital libraries, e-commerce platforms and global information access.

---

# 2-Mark Answer

### What is Cross-Lingual Information Retrieval (CLIR)?

**Definition:**

Cross-Lingual Information Retrieval (CLIR) is the process of retrieving documents written in one language using a query written in another language.

**Example:**

```text
English Query:
"Artificial Intelligence"

Retrieved Document:
"कृत्रिम बुद्धिमत्ता"
```

Thus, CLIR enables multilingual information access by overcoming language barriers.

---

# Last-Minute Revision (Exam Points)

### Definition

* Retrieval across different languages.
* Query language and document language are different.

### Approaches

1. Query Translation
2. Document Translation
3. Interlingua Approach

### Challenges

* Translation ambiguity
* Synonyms
* Morphological differences
* Resource scarcity
* Named entity handling

### Techniques

* Dictionary-based translation
* Machine Translation
* Statistical Models
* Neural Models
* Multilingual Embeddings

### Applications

* Search Engines
* Digital Libraries
* E-commerce
* Government Portals
* Research Databases

These points alone can fetch **6–8 marks** if remembered properly.
