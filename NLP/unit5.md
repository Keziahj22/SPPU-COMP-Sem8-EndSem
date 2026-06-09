# UNIT 5 – Lexical Resources, WSD, NLP Tools (Exam Answers)

---

# A. WORDNET

## Q1. Write a note on WordNet.

## OR

## Explain the concept of WordNet as a lexical knowledge network. How can WordNet be used in NLP, and what are its limitations?

### Definition

**WordNet** is a large lexical database of the English language developed at Princeton University.

It groups words into sets of synonyms called **Synsets** and represents semantic relationships among words.

WordNet acts as a **Lexical Knowledge Network** because words are connected through various semantic and lexical relations.

---

## Components of WordNet

### 1. Synset

A Synset is a group of words having similar meanings.

Example:

Synset for "Car":

{car, automobile, motorcar}

All words represent the same concept.

---

### 2. Gloss

Each synset contains a definition and example sentence.

Example:

Car:
"A motor vehicle with four wheels."

Example:
"He bought a new car."

---

## Semantic Relations in WordNet

### 1. Synonymy

Words having similar meanings.

Example:

happy → joyful

---

### 2. Antonymy

Words having opposite meanings.

Example:

hot ↔ cold

---

### 3. Hypernym (IS-A)

General category.

Example:

Car → Vehicle

Vehicle is hypernym of car.

---

### 4. Hyponym

Specific category.

Example:

Vehicle → Car

Car is hyponym of vehicle.

---

### 5. Meronym (PART-OF)

Part-whole relationship.

Example:

Wheel → Car

Wheel is part of car.

---

### 6. Holonym

Whole object.

Example:

Car → Wheel

Car contains wheel.

---

## Structure of WordNet

```text
Entity
  |
Vehicle
  |
Car
  |
Sports Car
```

Words are organized in a hierarchy.

---

## Applications of WordNet in NLP

### 1. Word Sense Disambiguation (WSD)

Determines correct meaning of ambiguous words.

Example:

"I deposited money in the bank."

WordNet identifies:
Bank = Financial Institution

---

### 2. Information Retrieval

Improves search by expanding queries using synonyms.

Search:
"Automobile"

Also retrieves:
"Car", "Motorcar"

---

### 3. Machine Translation

Helps select correct translation based on meaning.

---

### 4. Question Answering Systems

Improves semantic understanding.

---

### 5. Text Classification

Uses semantic relations to improve categorization.

---

### 6. Semantic Similarity

Measures similarity between words.

Example:

Car and Vehicle → Highly related

Car and Banana → Less related

---

## Advantages

1. Rich lexical resource
2. Organized semantic structure
3. Useful for WSD
4. Improves search systems
5. Supports machine translation
6. Freely available

---

## Limitations

1. Mostly English-focused
2. Limited domain-specific vocabulary
3. Manual maintenance required
4. Cannot always capture context
5. Static knowledge base

---

## Conclusion

WordNet is a semantic lexical database that organizes words into synsets and connects them through semantic relations such as synonymy, antonymy, hypernymy, and meronymy. It is widely used in NLP applications including WSD, information retrieval, machine translation, and semantic analysis.

---

# B. INDOWORDNET

## Q2. Compare IndoWordNet with traditional WordNet. Explain advantages of IndoWordNet.

### Definition

**IndoWordNet** is a multilingual lexical database designed for Indian languages.

It extends the WordNet concept to Indian languages such as:

* Hindi
* Marathi
* Bengali
* Gujarati
* Tamil
* Telugu
* Kannada
* Punjabi
* Sanskrit

and many others.

---

## Working Principle

IndoWordNet is built around a common Hindi synset structure.

Equivalent concepts are linked across different Indian languages.

Example:

English:
Car

Hindi:
कार

Marathi:
गाडी

Tamil:
கார்

All belong to the same synset.

---

## Comparison: WordNet vs IndoWordNet

| Feature             | WordNet                  | IndoWordNet               |
| ------------------- | ------------------------ | ------------------------- |
| Language            | English                  | Multiple Indian Languages |
| Purpose             | English Lexical Resource | Multilingual Resource     |
| Synsets             | English Synsets          | Cross-lingual Synsets     |
| Translation Support | Limited                  | Strong                    |
| Cultural Concepts   | Limited                  | Rich Indian Context       |
| NLP Applications    | English NLP              | Indian Language NLP       |

---

## Advantages of IndoWordNet

### 1. Supports Multiple Indian Languages

Useful for multilingual NLP.

---

### 2. Machine Translation

Improves translation between Indian languages.

---

### 3. Cross-Language Information Retrieval

User can search in one language and retrieve results in another.

---

### 4. Preserves Indian Cultural Concepts

Captures concepts unique to Indian languages.

---

### 5. Resource for Low-Resource Languages

Provides lexical knowledge for languages having limited datasets.

---

## Applications

1. Machine Translation
2. Search Engines
3. WSD
4. Information Retrieval
5. Question Answering
6. Multilingual NLP

---

## Conclusion

IndoWordNet extends WordNet to Indian languages by linking equivalent concepts across languages, making it valuable for multilingual NLP and machine translation systems.

---

# C. LESK ALGORITHM (WORD SENSE DISAMBIGUATION)

## Q3. Explain the Lesk Algorithm for Word Sense Disambiguation (WSD).

### Definition

The **Lesk Algorithm** is a knowledge-based WSD technique proposed by Michael Lesk in 1986.

It identifies the correct meaning of a word by comparing dictionary definitions (glosses) and selecting the sense with the maximum overlap.

---

## Idea

Words occurring in the same context tend to have related meanings.

The correct sense is chosen by finding the largest number of common words between definitions.

---

## Steps

### Step 1

Identify ambiguous word.

Example:

"I deposited money in the bank."

Ambiguous word:
Bank

---

### Step 2

Obtain all possible senses.

Sense 1:
Bank = Financial institution

Sense 2:
Bank = River side

---

### Step 3

Collect surrounding context words.

Context:

deposited, money

---

### Step 4

Compare gloss overlap.

Financial institution gloss:

"Organization handling money and deposits"

Overlap:
money, deposits

Score = 2

River bank gloss:

"Land beside river"

Overlap = 0

Score = 0

---

### Step 5

Choose highest overlap.

Correct sense:

Bank = Financial Institution

---

## Algorithm

```text
For each sense:
   Compute overlap with context words
Select sense with maximum overlap
```

---

## Advantages

1. Simple
2. No training data required
3. Uses dictionary knowledge
4. Language independent

---

## Limitations

1. Depends on gloss quality
2. Small overlaps possible
3. Computationally expensive
4. Lower accuracy in complex contexts

---

## Conclusion

Lesk Algorithm resolves ambiguity by selecting the sense whose dictionary definition shares maximum words with surrounding context.

---

# D. WALKER'S ALGORITHM

## Q4. Describe Walker's Algorithm for WSD.

### Definition

Walker’s Algorithm is a graph-based Word Sense Disambiguation method.

It uses semantic relationships among words and senses present in lexical networks such as WordNet.

---

## Working

Instead of comparing glosses directly, it builds a semantic graph.

Nodes:
Word senses

Edges:
Semantic relations

* Synonymy
* Hypernymy
* Hyponymy

---

## Steps

### Step 1

Identify ambiguous word.

Example:

bank

---

### Step 2

Generate all possible senses.

---

### Step 3

Create semantic graph connecting neighboring words.

---

### Step 4

Measure semantic connectivity.

---

### Step 5

Choose the sense most strongly connected to context.

---

## Example

Sentence:

"The fisherman sat on the bank of the river."

Context:
fisherman, river

River-bank sense has stronger connections.

Chosen sense:
River side

---

## Walker vs Lesk

| Feature               | Lesk                   | Walker                   |
| --------------------- | ---------------------- | ------------------------ |
| Approach              | Gloss Matching         | Graph Based              |
| Knowledge Source      | Dictionary Definitions | Semantic Network         |
| Complexity            | Lower                  | Higher                   |
| Accuracy              | Moderate               | Better in large networks |
| Context Understanding | Limited                | Better                   |

---

## Advantages

1. Uses semantic relations
2. Better contextual understanding
3. Works well with WordNet

---

## Limitations

1. Complex
2. Requires lexical network
3. Higher computation cost

---

# E. LEXICAL KNOWLEDGE NETWORKS

## Q5. Explain WordNet, IndoWordNet, VerbNet, PropBank and Treebanks.

### 1. WordNet

* Lexical database of English
* Organizes words into synsets
* Supports WSD and semantic analysis

---

### 2. IndoWordNet

* Multilingual WordNet for Indian languages
* Cross-language synset mapping
* Useful in translation

---

### 3. VerbNet

Largest verb lexicon.

Groups verbs into classes based on:

* Meaning
* Syntax
* Semantic behavior

Example:

Give, Send, Transfer

belong to transfer class.

Used in semantic role labeling.

---

### 4. PropBank

Predicate-Argument Bank.

Adds semantic roles to sentences.

Example:

John gave Mary a book.

ARG0 = John (giver)

ARG1 = book (thing given)

ARG2 = Mary (receiver)

---

### 5. Treebanks

Annotated corpora containing syntactic parse trees.

Example:

```text
(S
 (NP John)
 (VP eats
   (NP apple)))
```

Used for parser training.

---

# F. VERBNET AND PROPBANK

## Q6. Significance of PropBank and VerbNet in NLP

### VerbNet

Provides:

* Verb classes
* Thematic roles
* Syntactic patterns

Example:

Verb:
Give

Roles:

Agent → John

Theme → Book

Recipient → Mary

---

### PropBank

Provides semantic role annotations.

Example:

"John gave Mary a book."

ARG0 = John

ARG1 = Book

ARG2 = Mary

---

## Applications

1. Information Extraction
2. Question Answering
3. Machine Translation
4. Semantic Role Labeling
5. Event Extraction

---

## Difference

| VerbNet             | PropBank            |
| ------------------- | ------------------- |
| Verb Classification | Semantic Annotation |
| Verb Behavior       | Predicate Arguments |
| Lexicon             | Annotated Corpus    |

---

# G. TREEBANKS

## Q7. Discuss the role of Treebanks and Universal Dependency Treebanks in NLP.

### Definition

Treebanks are annotated corpora containing syntactic structures of sentences.

---

## Types

### 1. Constituency Treebank

Represents phrase structure.

Example:

```text
(S
 (NP Ram)
 (VP eats
  (NP apple)))
```

---

### 2. Dependency Treebank

Represents grammatical dependencies.

```text
eats → Ram
eats → apple
```

---

## Universal Dependency (UD) Treebanks

Standardized dependency annotations across many languages.

Purpose:

* Cross-language NLP
* Consistent grammar representation

---

## Applications

1. Parser Training
2. POS Tagging
3. Machine Translation
4. Information Extraction
5. Grammar Checking

---

## Advantages

1. High-quality annotations
2. Multilingual support
3. Better syntactic analysis

---

## Conclusion

Treebanks provide structured linguistic annotations that help machines learn sentence grammar and improve parsing performance.

---

# H. NLP DEVELOPMENT TOOLS / LIBRARIES

## Q8. Compare NLTK, spaCy, TextBlob and Gensim

| Feature        | NLTK                 | spaCy          | TextBlob   | Gensim         |
| -------------- | -------------------- | -------------- | ---------- | -------------- |
| Purpose        | Education & Research | Industrial NLP | Simple NLP | Topic Modeling |
| Speed          | Slow                 | Fast           | Moderate   | Fast           |
| POS Tagging    | Yes                  | Yes            | Yes        | No             |
| Parsing        | Basic                | Advanced       | Limited    | No             |
| Topic Modeling | Limited              | No             | No         | Excellent      |
| Ease of Use    | Medium               | Medium         | Easy       | Medium         |

---

## NLTK Features

* Tokenization
* Stemming
* Lemmatization
* POS Tagging
* Parsing
* Corpora support

---

## spaCy Features

* Industrial NLP
* Fast tokenizer
* NER
* Dependency Parsing
* Word Vectors

---

## TextBlob Features

* Simple API
* Sentiment Analysis
* POS Tagging
* Translation

---

## Gensim Features

* Topic Modeling
* LSA
* LDA
* Word2Vec
* Document Similarity

---

# I. GENSIM

## Q9. Which tasks are performed by Gensim? Give example.

### Definition

Gensim is an open-source Python library used for unsupervised NLP.

---

## Tasks

### 1. Topic Modeling

Using LDA

Example:

News articles → Politics, Sports, Business topics

---

### 2. Word Embeddings

Word2Vec

Example:

King - Man + Woman ≈ Queen

---

### 3. Document Similarity

Compare text documents.

---

### 4. Text Summarization

Generate concise summaries.

---

### 5. Semantic Search

Retrieve similar documents.

---

## Advantages

1. Efficient for large datasets
2. Memory optimized
3. Supports streaming data

---

# J. NLTK PROGRAMMING

## Q10. Write Python code using NLTK library for tokenization.

### 1. Whitespace Tokenization

```python
from nltk.tokenize import WhitespaceTokenizer

text = "Natural Language Processing is interesting"

tokenizer = WhitespaceTokenizer()

tokens = tokenizer.tokenize(text)

print(tokens)
```

Output:

```text
['Natural', 'Language', 'Processing', 'is', 'interesting']
```

---

### 2. Punctuation-Based Tokenization

```python
from nltk.tokenize import WordPunctTokenizer

text = "Hello, NLP students!"

tokenizer = WordPunctTokenizer()

tokens = tokenizer.tokenize(text)

print(tokens)
```

Output:

```text
['Hello', ',', 'NLP', 'students', '!']
```

---

### 3. Default Tokenization

```python
from nltk.tokenize import word_tokenize

text = "Natural Language Processing is interesting."

tokens = word_tokenize(text)

print(tokens)
```

Output:

```text
['Natural', 'Language', 'Processing', 'is', 'interesting', '.']
```

---

# Last-Minute Exam Priority (Most Important)

Study in this order:

1. **WordNet** ⭐⭐⭐⭐⭐
2. **IndoWordNet** ⭐⭐⭐⭐⭐
3. **Lesk Algorithm** ⭐⭐⭐⭐⭐
4. **Walker's Algorithm** ⭐⭐⭐⭐
5. **Treebanks & Universal Dependencies** ⭐⭐⭐⭐
6. **VerbNet & PropBank** ⭐⭐⭐⭐
7. **NLTK vs spaCy vs TextBlob vs Gensim** ⭐⭐⭐⭐
8. **Gensim Tasks** ⭐⭐⭐
9. **NLTK Programs** ⭐⭐⭐

These 9 topics cover almost the entire Unit 5 question bank and are enough for most 8–10 mark questions.
