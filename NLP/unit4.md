# Unit 4 – NLP & Information Retrieval (10 Marks Answers)

---

# 1. Information Retrieval (IR) Architecture

## Definition

Information Retrieval (IR) is the process of obtaining relevant information from a large collection of documents based on a user's query.

Examples:

* Google Search Engine
* Library Search Systems
* Document Retrieval Systems
* Digital Repositories

---

## Need for IR

With the enormous growth of digital information, users require efficient methods to find relevant documents quickly.

Example:

Collection:

* D1: "Machine Learning Basics"
* D2: "Deep Learning Applications"
* D3: "Natural Language Processing"

Query:
"Machine Learning"

IR system should retrieve D1 first because it is most relevant.

---

## Components of IR Architecture

### 1. Document Collection

Contains all documents stored in the database.

Example:

* Research Papers
* News Articles
* Books
* Web Pages

---

### 2. Document Processing

Documents are preprocessed before indexing.

Operations:

#### Tokenization

Sentence:
"Machine learning is powerful."

Tokens:
Machine, learning, is, powerful

#### Stop Word Removal

Remove common words:

"Machine learning is powerful"

→ Machine learning powerful

#### Stemming

Learning → Learn

Running → Run

---

### 3. Indexing

Creates an inverted index.

Example:

| Term     | Documents |
| -------- | --------- |
| Machine  | D1,D3     |
| Learning | D1,D2     |
| NLP      | D3        |

This speeds up searching.

---

### 4. Query Processing

User query undergoes the same preprocessing.

Query:
"Learning Machines"

Becomes:
"learn machine"

---

### 5. Matching Module

Compares query terms with indexed documents.

Methods:

* Boolean Matching
* Vector Space Model
* Probabilistic Models

---

### 6. Ranking

Documents are ranked according to relevance score.

Example:

Query: "machine learning"

Results:

1. D1 (Score 0.95)
2. D2 (Score 0.82)
3. D3 (Score 0.50)

---

### 7. Result Presentation

Top-ranked documents are shown to the user.

---

## IR Architecture Diagram

```text
Document Collection
        ↓
Document Processing
(Tokenization, Stemming)
        ↓
      Indexing
        ↓
     Database

User Query
      ↓
Query Processing
      ↓
Matching & Ranking
      ↓
Retrieved Documents
```

---

## Advantages

* Fast retrieval
* Efficient searching
* Handles huge datasets
* Supports ranking

---

## Applications

* Google Search
* Bing
* Digital Libraries
* E-commerce Search
* Question Answering Systems

---

# 2. Vector Space Model (VSM)

## Definition

Vector Space Model represents documents and queries as vectors in a multidimensional space.

Each term corresponds to one dimension.

Similarity between vectors determines document relevance.

Proposed by Gerard Salton.

---

## Idea

Documents with similar words are located close together in vector space.

---

## Representation

Documents:

D1 = "I like NLP"

D2 = "I like Machine Learning"

Vocabulary:

```text
[I, Like, NLP, Machine, Learning]
```

Vectors:

```text
D1 = [1,1,1,0,0]

D2 = [1,1,0,1,1]
```

---

## TF-IDF Weighting

### Term Frequency (TF)

Measures frequency of a term in a document.

Formula:

```text
TF = Number of occurrences of term
```

Example:

Word "NLP" appears 4 times.

TF = 4

---

### Inverse Document Frequency (IDF)

Measures importance of a term.

Formula:

```text
IDF = log(Total Documents / Documents containing term)
```

Rare terms receive higher weight.

---

### TF-IDF

```text
TF-IDF = TF × IDF
```

Used to assign weights to terms.

---

## Similarity Measurement

Cosine Similarity is commonly used.

Formula:

```text
Cos(Q,D)=
(Q·D)/(||Q|| ||D||)
```

Range:

* 1 → identical
* 0 → unrelated

---

## Example

Query:

"Machine Learning"

Documents:

D1: Machine Learning Basics

D2: Cricket Match Results

Vectors show D1 closer to query.

Thus D1 gets higher rank.

---

## Advantages

* Simple
* Effective
* Supports ranking
* Widely used

---

## Limitations

* Ignores word order
* Cannot understand meaning
* High dimensionality

---

## Applications

* Search Engines
* Document Ranking
* Text Classification
* Recommendation Systems

---

# 3. Cross-Lingual Information Retrieval (CLIR)

## Definition

Cross-Lingual Information Retrieval retrieves documents written in one language using queries written in another language.

Example:

Query:
English → "Computer Science"

Retrieved Documents:
Hindi, Marathi, French, etc.

---

## Need for CLIR

Many documents exist in multiple languages.

Users may not know the document language.

CLIR bridges the language gap.

---

## Working of CLIR

### Step 1: User Query

English:

"Artificial Intelligence"

---

### Step 2: Translation

Translate query into target language.

Hindi:

"कृत्रिम बुद्धिमत्ता"

---

### Step 3: Search

Search translated query in document database.

---

### Step 4: Ranking

Relevant documents ranked.

---

### Step 5: Retrieval

Results displayed to user.

---

## CLIR Architecture

```text
User Query
      ↓
Language Detection
      ↓
Translation Module
      ↓
Search Engine
      ↓
Ranking
      ↓
Retrieved Documents
```

---

## Approaches

### 1. Query Translation

Translate query.

English → Hindi

Most common approach.

---

### 2. Document Translation

Translate all documents into query language.

---

### 3. Interlingua Approach

Convert both query and documents into a language-independent representation.

---

## Example

Query:

"Tourism in India"

Translated:

"भारत में पर्यटन"

Searches Hindi document collection.

---

## Advantages

* Access multilingual information
* Global search capability
* Useful in international organizations

---

## Applications

* Google Search
* Digital Libraries
* Government Portals
* Multilingual Search Engines

---

# 4. Named Entity Recognition (NER)

## Definition

Named Entity Recognition identifies and classifies important entities in text.

Entities include:

* Person
* Organization
* Location
* Date
* Time
* Money
* Percentage

---

## Example

Sentence:

"Virat Kohli plays for BCCI in India."

NER Output:

```text
Virat Kohli → PERSON
BCCI → ORGANIZATION
India → LOCATION
```

---

## Working of NER

### Step 1: Tokenization

Break sentence into words.

---

### Step 2: Feature Extraction

Features:

* Capitalization
* Prefix/Suffix
* POS Tags
* Context Words

---

### Step 3: Classification

Machine Learning or Deep Learning model assigns labels.

---

### Step 4: Output

Entities extracted.

---

## NER Tags

| Entity      | Tag          |
| ----------- | ------------ |
| Virat Kohli | PERSON       |
| Mumbai      | LOCATION     |
| Infosys     | ORGANIZATION |
| ₹5000       | MONEY        |
| 12 Jan 2025 | DATE         |

---

## Techniques

### Rule-Based

Handwritten rules.

---

### Machine Learning

* HMM
* CRF
* SVM

---

### Deep Learning

* RNN
* LSTM
* BERT

---

## Applications

* Search Engines
* Chatbots
* Resume Parsing
* Information Extraction
* Healthcare Systems

---

## Advantages

* Automatic extraction
* Improves search
* Supports NLP pipelines

---

# 5. Entity Extraction

## Definition

Entity Extraction is the process of identifying and extracting useful entities from unstructured text.

NER is a part of Entity Extraction.

Entity Extraction may also include attributes and relationships.

---

## Example

Sentence:

"Apple launched iPhone 16 in California."

Extracted Entities:

```text
Apple → Organization
iPhone 16 → Product
California → Location
```

---

## Working

### Step 1: Text Input

Raw text collected.

---

### Step 2: Preprocessing

* Tokenization
* Stop-word removal
* POS tagging

---

### Step 3: Entity Identification

Find names and important terms.

---

### Step 4: Classification

Assign categories.

---

### Step 5: Storage

Store in structured format.

---

## Example Output

```text
Person:
Virat Kohli

Organization:
BCCI

Location:
India
```

---

## Difference between NER and Entity Extraction

| NER                 | Entity Extraction                        |
| ------------------- | ---------------------------------------- |
| Identifies entities | Identifies + extracts useful information |
| Limited categories  | Can include attributes and relations     |
| Subset              | Broader concept                          |

---

## Applications

* Knowledge Graphs
* Search Engines
* Business Analytics
* Recommendation Systems
* Healthcare Records

---

## Advantages

* Converts text into structured data
* Improves analytics
* Enhances information retrieval

---

# 6. Coreference Resolution

## Definition

Coreference Resolution identifies words or phrases that refer to the same entity in a text.

It determines who or what pronouns refer to.

---

## Example 1

Sentence:

"Rahul went to school. He was late."

Coreference:

```text
Rahul = He
```

---

## Example 2

Sentence:

"Priya bought a laptop. She likes it."

Coreference:

```text
Priya = She
Laptop = It
```

---

## Need for Coreference Resolution

Without coreference:

```text
Rahul went home.
He ate food.
```

Computer may not know "He" means Rahul.

Coreference resolution solves this problem.

---

## Types

### 1. Pronoun Resolution

```text
John is a student.
He studies NLP.

He = John
```

---

### 2. Noun Phrase Resolution

```text
The President gave a speech.
The leader addressed citizens.

President = Leader
```

---

### 3. Demonstrative Resolution

```text
I bought a car.
This is very expensive.

This = Car
```

---

## Working Steps

### Step 1: Identify Mentions

Find nouns and pronouns.

---

### Step 2: Candidate Selection

Possible references identified.

---

### Step 3: Similarity Analysis

Check:

* Gender
* Number
* Semantic meaning
* Context

---

### Step 4: Link Entities

Connect mentions to the same entity.

---

## Coreference Example

```text
Riya bought a book.
She read it at home.

Riya → She
Book → It
```

---

## Applications

* Question Answering
* Chatbots
* Machine Translation
* Text Summarization
* Information Extraction

---

## Advantages

* Better text understanding
* Improves NLP accuracy
* Helps context tracking

---

# Quick Exam Revision (2 Marks Each)

### IR Architecture

Document Collection → Processing → Indexing → Query Processing → Matching → Ranking → Retrieval

### VSM

Documents and queries represented as vectors; similarity measured using cosine similarity.

### CLIR

Retrieve documents in one language using a query written in another language.

### NER

Identifies named entities such as Person, Location, Organization, Date, Money.

### Entity Extraction

Extracts useful entities and structured information from text.

### Coreference Resolution

Finds words referring to the same entity (Rahul = He, Laptop = It).
