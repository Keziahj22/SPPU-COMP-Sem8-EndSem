# UNIT 5: Impact of Machine Learning in Business Intelligence (BI)

---

# 1. Write a Short Note on Classification

## Definition

Classification is a **supervised machine learning technique** used to assign data into predefined categories or classes based on historical data.

In classification, the model learns from labeled training data and predicts the class of new observations.

### Examples

| Input          | Output Class         |
| -------------- | -------------------- |
| Email Message  | Spam / Not Spam      |
| Customer Data  | Buy / Not Buy        |
| Loan Applicant | Approved / Rejected  |
| Medical Report | Disease / No Disease |

---

## Steps in Classification

### 1. Collect Data

Gather historical records.

### 2. Label Data

Each record belongs to a known class.

### 3. Train Model

Algorithms learn patterns from data.

### 4. Test Model

Measure prediction accuracy.

### 5. Predict New Data

Assign class labels to unseen records.

---

## Common Classification Algorithms

1. Naive Bayes
2. Logistic Regression
3. Decision Tree
4. Random Forest
5. Support Vector Machine (SVM)

---

## Applications in BI

* Customer churn prediction
* Fraud detection
* Medical diagnosis
* Credit risk analysis
* Email spam filtering

---

## Advantages

* Easy decision-making
* High predictive capability
* Automates business processes

## Disadvantages

* Requires labeled data
* Accuracy depends on training data quality

---

# 2, 3, 4. Difference Between Classification and Clustering with Applications and Examples

## Classification vs Clustering

| Feature       | Classification   | Clustering        |
| ------------- | ---------------- | ----------------- |
| Learning Type | Supervised       | Unsupervised      |
| Data          | Labeled          | Unlabeled         |
| Goal          | Predict category | Discover groups   |
| Output        | Known classes    | Unknown clusters  |
| Example       | Spam/Not Spam    | Customer Segments |

---

## Example

### Classification

Customer Data:

| Age | Income | Buy Product |
| --- | ------ | ----------- |
| 25  | 30000  | Yes         |
| 40  | 70000  | No          |

Model predicts whether a new customer will buy.

---

### Clustering

Customer Data:

| Customer | Spending |
| -------- | -------- |
| A        | High     |
| B        | Medium   |
| C        | Low      |

Algorithm automatically forms:

Cluster 1 → High Spenders

Cluster 2 → Low Spenders

---

## Applications

### Classification

* Fraud detection
* Loan approval
* Disease prediction

### Clustering

* Market segmentation
* Customer grouping
* Recommendation systems

---

## Exam Conclusion

Classification predicts predefined classes while clustering discovers hidden groups in data.

---

# 5. State Different Formulae for Evaluation of Classification Models

Classification performance is evaluated using a **Confusion Matrix**.

|                 | Predicted Positive | Predicted Negative |
| --------------- | ------------------ | ------------------ |
| Actual Positive | TP                 | FN                 |
| Actual Negative | FP                 | TN                 |

Where:

TP = True Positive

TN = True Negative

FP = False Positive

FN = False Negative

---

## 1. Accuracy

[
Accuracy=\frac{TP+TN}{TP+TN+FP+FN}
]

Measures overall correctness.

---

## 2. Precision

[
Precision=\frac{TP}{TP+FP}
]

Measures correctness of positive predictions.

---

## 3. Recall (Sensitivity)

[
Recall=\frac{TP}{TP+FN}
]

Measures ability to identify positives.

---

## 4. Specificity

[
Specificity=\frac{TN}{TN+FP}
]

Measures ability to identify negatives.

---

## 5. F1 Score

[
F1=2\times \frac{Precision \times Recall}{Precision+Recall}
]

Balances Precision and Recall.

---

# 6. Advantages and Disadvantages of Naive Bayes Classifier

## Definition

Naive Bayes is a probabilistic classifier based on Bayes Theorem.

It assumes all features are independent.

---

## Advantages

### 1. Fast Training

Requires less computation.

### 2. Works with Small Datasets

### 3. Handles High-Dimensional Data

### 4. Good for Text Classification

Example:
Spam detection.

### 5. Easy to Implement

---

## Disadvantages

### 1. Independence Assumption

Features are rarely independent.

### 2. Lower Accuracy for Complex Data

### 3. Zero Frequency Problem

If an event never occurred in training data, probability becomes zero.

---

## Applications

* Email filtering
* Sentiment analysis
* Medical diagnosis

---

# 7. Explain Bayes Theorem in Detail

## Formula

[
P(A|B)=\frac{P(B|A)\times P(A)}{P(B)}
]

Where:

P(A|B) = Posterior Probability

P(B|A) = Likelihood

P(A) = Prior Probability

P(B) = Evidence

---

## Example

Suppose:

Disease probability = 0.01

Positive test if disease exists = 0.95

Positive test overall = 0.05

Find probability patient has disease after positive test.

[
P(Disease|Positive)=
\frac{0.95\times0.01}{0.05}
]

[
=0.19
]

Therefore probability = 19%.

---

## Applications

* Spam filtering
* Medical diagnosis
* Fraud detection

---

# 8, 9, 10, 11. Logistic Regression with Types and Example

## Definition

Logistic Regression is a supervised learning algorithm used for classification problems.

It predicts probability values between 0 and 1.

---

## Logistic Function

[
P=\frac{1}{1+e^{-z}}
]

where

[
z=b_0+b_1x
]

Output lies between 0 and 1.

---

## Example

Predict whether a student passes.

| Study Hours | Result |
| ----------- | ------ |
| 2           | Fail   |
| 8           | Pass   |

Model predicts probability of passing.

If probability > 0.5 → Pass

Else → Fail

---

## Types

### 1. Binary Logistic Regression

Two outcomes.

Example:

Pass/Fail

Yes/No

---

### 2. Multinomial Logistic Regression

More than two categories.

Example:

Product A/B/C

---

### 3. Ordinal Logistic Regression

Ordered categories.

Example:

Low, Medium, High

---

## Advantages

* Easy interpretation
* Fast training
* Good for binary classification

---

## Disadvantages

* Cannot model complex non-linear relationships

---

## Applications

* Customer churn prediction
* Disease diagnosis
* Credit approval

---

# 12, 13. What is Clustering? Explain K-Means Clustering

## Definition

Clustering is an unsupervised learning technique that groups similar data objects together.

---

## K-Means Clustering

Partitions data into K clusters.

Each cluster is represented by a centroid.

---

## Working Steps

### Step 1

Choose K clusters.

Example:

K = 2

---

### Step 2

Select initial centroids.

---

### Step 3

Calculate distance of each point from centroids.

Usually Euclidean Distance.

[
d=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}
]

---

### Step 4

Assign points to nearest centroid.

---

### Step 5

Recalculate centroids.

---

### Step 6

Repeat until centroids stop changing.

---

## Example

Data:

(2,3), (3,4), (10,11), (11,12)

K=2

Final Clusters:

Cluster 1:
(2,3), (3,4)

Cluster 2:
(10,11), (11,12)

---

## Applications

* Customer segmentation
* Market analysis
* Image segmentation

---

# 14. Numerical on K-Means (K=2)

### Procedure

1. Select K=2
2. Choose initial centroids
3. Calculate distances
4. Assign nearest cluster
5. Recompute centroid
6. Repeat until stable

**Exam Tip:** Always show distance table, cluster assignment, new centroid calculation, and final clusters.

---

# 15. Difference Between Hierarchical and Partitioning Clustering

| Feature    | Hierarchical | Partitioning (K-Means) |
| ---------- | ------------ | ---------------------- |
| Structure  | Tree         | Flat Clusters          |
| K Required | No           | Yes                    |
| Output     | Dendrogram   | Cluster Groups         |
| Speed      | Slow         | Fast                   |
| Large Data | Not Suitable | Suitable               |

---

# 16. Define Hierarchical Clustering

## Definition

Hierarchical clustering builds a hierarchy of clusters represented using a dendrogram.

---

## Types

### 1. Agglomerative

Bottom-Up

Each object starts as separate cluster.

Clusters merge gradually.

---

### 2. Divisive

Top-Down

One large cluster split repeatedly.

---

## Output

Dendrogram (tree structure)

---

## Applications

* Gene analysis
* Customer segmentation
* Document grouping

---

# 17, 18, 19, 20. Association Rules, Support and Confidence

## Definition

Association Rule Mining discovers relationships among items in large datasets.

---

## Rule Format

[
X \rightarrow Y
]

Meaning:

If X occurs, Y also tends to occur.

---

## Example

Market Basket:

Customers buying:

Bread → Butter

Milk → Bread

---

## Types

### 1. Single-Dimensional Rules

Bread → Butter

### 2. Multi-Dimensional Rules

Age=Young → Buys Laptop

---

## Support

Measures frequency of rule.

[
Support=
\frac{Transactions(X \cup Y)}
{Total Transactions}
]

---

## Confidence

Measures strength.

[
Confidence=
\frac{Transactions(X \cup Y)}
{Transactions(X)}
]

---

### Example

10 transactions

Bread and Butter together = 4

Bread appears = 5

Support

[
4/10=40%
]

Confidence

[
4/5=80%
]

---

# 21. Define Frequent Item Set

## Definition

An item set whose support is greater than or equal to minimum support threshold.

---

### Example

Min Support = 3

| Itemset       | Count |
| ------------- | ----- |
| Bread         | 5     |
| Milk          | 4     |
| Bread, Butter | 3     |

All are Frequent Item Sets.

---

## Importance

Used in Apriori algorithm for rule generation.

---

# 22. Define Minimum Support Count

## Definition

Minimum Support Count is the minimum number of transactions in which an itemset must appear to be considered frequent.

---

### Example

Min Support Count = 2

| Itemset | Count |
| ------- | ----- |
| Bread   | 5     |
| Milk    | 3     |
| Jam     | 1     |

Frequent:
Bread, Milk

Not Frequent:
Jam

---

# 23 & 24. Apriori Algorithm with Applications and Example

## Definition

Apriori is a frequent itemset mining algorithm used to generate association rules.

---

## Apriori Principle

"If an itemset is frequent, all its subsets must also be frequent."

---

## Steps

### Step 1

Generate 1-itemsets

### Step 2

Remove infrequent itemsets

### Step 3

Generate candidate 2-itemsets

### Step 4

Calculate support

### Step 5

Repeat until no frequent itemsets remain

### Step 6

Generate association rules

---

## Example

Transactions:

T1 = Bread, Milk

T2 = Bread, Butter

T3 = Bread, Milk, Butter

T4 = Milk, Butter

Min Support = 2

---

### Frequent Itemsets

L1:

Bread(3), Milk(3), Butter(3)

L2:

Bread-Milk(2)

Bread-Butter(2)

Milk-Butter(2)

L3:

Bread-Milk-Butter(1) ❌

---

### Strong Rule

Bread → Milk

Confidence

[
2/3=66.7%
]

---

## Applications

* Market basket analysis
* Recommendation systems
* Cross-selling
* Inventory planning

---

# 26. What is a Decision Tree? Explain with Case Study

## Definition

Decision Tree is a supervised learning algorithm that predicts outcomes using tree-like decisions.

---

## Components

### Root Node

Starting point.

### Internal Node

Decision condition.

### Leaf Node

Final output.

---

## Case Study: Loan Approval

```
Income > 50000?
      |
   Yes/No
    /   \
 Approved Rejected
```

---

## Advantages

* Easy interpretation
* Visual representation
* Handles categorical data

---

## Applications

* Loan approval
* Medical diagnosis
* Customer segmentation

---

# 27. Define Regression

## Definition

Regression is a supervised learning technique used to predict continuous numerical values.

---

## Examples

| Input       | Output            |
| ----------- | ----------------- |
| Area        | House Price       |
| Advertising | Sales             |
| Temperature | Electricity Usage |

---

## Regression Equation

[
Y=a+bX
]

Where:

Y = Predicted value

a = Intercept

b = Slope

X = Independent Variable

---

## Applications

* Sales forecasting
* Stock prediction
* Demand estimation

---

# 28. Discuss Parameter Tuning and Optimization

## Definition

Parameter Tuning is the process of selecting the best model parameters to improve performance.

Optimization aims to maximize accuracy and minimize errors.

---

## Common Parameters

### Decision Tree

* Max Depth
* Min Samples Split

### K-Means

* Number of Clusters (K)

### Logistic Regression

* Learning Rate

---

## Techniques

### 1. Grid Search

Try all combinations.

### 2. Random Search

Random parameter combinations.

### 3. Cross Validation

Evaluate on multiple datasets.

---

## Benefits

* Higher accuracy
* Better predictions
* Reduced overfitting

---

# Most Important 10-Mark Questions for Exam

1. Classification vs Clustering (Very Important)
2. Bayes Theorem and Naive Bayes
3. Logistic Regression with Types
4. K-Means Clustering Algorithm
5. Association Rules, Support & Confidence
6. Apriori Algorithm with Example
7. Decision Tree with Case Study
8. Evaluation Metrics (Accuracy, Precision, Recall, F1)
9. Regression
10. Parameter Tuning and Optimization

These 10 answers cover almost the entire Unit 5 syllabus and are the highest-probability long-answer questions.
