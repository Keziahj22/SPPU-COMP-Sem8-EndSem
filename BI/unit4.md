# UNIT 4: DATA PREPARATION (10 Marks Answers)

---

# Q1. Explain Data Exploration in Detail with Example.

## Definition

Data Exploration is the process of examining, understanding, and summarizing data before performing analysis or building reports/models. It helps identify patterns, trends, anomalies, missing values, and relationships among variables.

It is also known as **Exploratory Data Analysis (EDA).**

---

## Objectives of Data Exploration

1. Understand the structure of data
2. Detect missing values
3. Identify outliers
4. Discover patterns and relationships
5. Check data quality
6. Select suitable preprocessing techniques

---

## Steps in Data Exploration

### 1. Data Collection

Gather data from various sources.

Example:
Student database containing:

* Roll No
* Name
* Age
* Marks

---

### 2. Data Summary

Calculate:

* Mean
* Median
* Mode
* Minimum
* Maximum
* Standard Deviation

Example:

Marks: 45, 50, 55, 60, 90

Mean = 60

---

### 3. Visualization

Tools:

* Histogram
* Bar Chart
* Pie Chart
* Scatter Plot
* Box Plot

Example:
Histogram of marks shows most students scored between 50-60.

---

### 4. Detect Missing Values

Example:

| Student | Marks |
| ------- | ----- |
| A       | 80    |
| B       | NULL  |
| C       | 75    |

Missing value identified.

---

### 5. Detect Outliers

Example:

Marks:
45, 50, 55, 60, 250

250 is an outlier.

---

### 6. Relationship Analysis

Example:

Study Hours vs Marks

Scatter plot may show positive correlation.

---

## Example

Retail Company Dataset

Attributes:

* Product
* Price
* Sales
* Region

Data exploration can reveal:

* Highest selling products
* Seasonal trends
* Regions with maximum sales
* Missing records

---

## Advantages

* Improves data quality
* Better decision making
* Reduces analysis errors
* Helps choose proper models

---

## Conclusion

Data Exploration is the first and most important step in data preparation that helps understand data characteristics and improve analysis accuracy.

---

# Q2. Explain Data Transformation in Detail with Example.

# OR

# Q3. What is Data Transformation? Explain Data Transformation Process.

# OR

# Q4. What is Data Transformation? Why is it Needed? Explain Techniques.

# OR

# Q5. Explain Any One Data Transformation Technique with Example.

(All combined answer)

---

## Definition

Data Transformation is the process of converting data from one format, structure, or value range into another suitable format for analysis and reporting.

It converts raw data into meaningful and usable data.

---

## Need of Data Transformation

1. Improve data quality
2. Standardize data
3. Make data compatible
4. Improve mining accuracy
5. Reduce inconsistencies

---

## Data Transformation Process

### Step 1: Data Extraction

Collect data from sources.

Example:
Excel, Database, CRM

↓

### Step 2: Data Cleaning

Remove errors and missing values.

↓

### Step 3: Transformation

Apply required transformation techniques.

↓

### Step 4: Loading

Store transformed data into warehouse.

---

## Techniques of Data Transformation

### 1. Normalization

Converts values into common scale.

Formula:

[
X'=\frac{X-Min}{Max-Min}
]

Example:

Age values:
20, 40, 60

Normalized:
0, 0.5, 1

---

### 2. Aggregation

Combines multiple records.

Example:

Daily Sales:

| Day | Sales |
| --- | ----- |
| Mon | 1000  |
| Tue | 1200  |

Weekly Sales = 2200

---

### 3. Generalization

Replace detailed values with higher level values.

Example:

Pune → Maharashtra → India

---

### 4. Attribute Construction

Create new attributes.

Example:

DOB → Age

---

### 5. Smoothing

Removes noise.

Example:
Marks:
45,46,47,120

120 may be smoothed using averaging.

---

## Detailed Example

Raw Data

| Employee | Salary |
| -------- | ------ |
| A        | 25000  |
| B        | 45000  |
| C        | 80000  |

After Normalization

| Employee | Salary |
| -------- | ------ |
| A        | 0      |
| B        | 0.36   |
| C        | 1      |

---

## Advantages

* Better analysis
* Improved data quality
* Consistent reports
* Increased mining accuracy

---

## Conclusion

Data Transformation converts raw data into an appropriate form suitable for BI reporting and analytics.

---

# Q6. Explain Data Validation, Incompleteness, Noise and Inconsistency of Quality Input Data.

# OR

# Q7. Write Short Note on Data Validation.

---

## Data Validation

### Definition

Data Validation is the process of checking whether data is correct, complete, and follows predefined rules before analysis.

---

## Purpose

* Improve accuracy
* Reduce errors
* Ensure consistency

---

## Types

### Range Validation

Age must be between 1 and 100.

---

### Format Validation

Email:
[abc@gmail.com](mailto:abc@gmail.com)

Valid format required.

---

### Type Validation

Age must be numeric.

---

### Uniqueness Validation

Employee ID must be unique.

---

# Data Quality Problems

## 1. Incompleteness

Some values are missing.

Example:

| Name | Age  |
| ---- | ---- |
| John | NULL |

Problems:

* Incorrect reports
* Reduced accuracy

---

## 2. Noise

Random errors in data.

Example:

Temperature:
25,26,27,200

200 is noisy value.

---

## 3. Inconsistency

Conflicting data values.

Example:

Gender:
Male, M, male

Different representations of same value.

---

## Methods to Improve Data Quality

* Validation rules
* Data cleaning
* Standardization
* Missing value handling

---

## Conclusion

Data Validation ensures high-quality data by detecting incompleteness, noise, and inconsistencies before analysis.

---

# Q8. Discuss Need for Data Preprocessing and Explain Any Two Techniques.

# OR

# Q9. Explain Need of Data Cleaning and Different Methods.

# OR

# Q10. How Mean, Median and Mode are Used During Data Cleaning?

# OR

# Q11. Define Dirty Data. What are Reasons of Dirty Data?

(All Combined)

---

# Data Preprocessing

## Definition

Data preprocessing converts raw data into clean and useful data before analysis.

---

## Need

* Improve quality
* Remove errors
* Handle missing values
* Increase accuracy

---

# Dirty Data

Dirty data refers to incorrect, incomplete, duplicate, noisy, or inconsistent data.

---

## Reasons

1. Human entry errors
2. Missing records
3. Sensor failures
4. Duplicate entries
5. Integration errors

---

# Data Cleaning Methods

## 1. Handling Missing Values

### Using Mean

Marks:
50,60,NULL,70

Mean = 60

Replace NULL by 60.

---

### Using Median

Marks:
10,20,NULL,90,100

Median = 55

Replace NULL by 55.

---

### Using Mode

Gender:
Male, Female, Male, NULL

Mode = Male

Replace NULL with Male.

---

## 2. Remove Duplicate Records

Example:

Same customer entered twice.

Keep only one record.

---

## 3. Noise Removal

Use smoothing and binning.

---

## 4. Standardization

Convert:

Male, M, male

to

Male

---

## Advantages

* Better reporting
* Improved accuracy
* Reliable decisions

---

## Conclusion

Data preprocessing and cleaning are essential to ensure high-quality data for BI systems.

---

# Q12. Explain Data Reduction in Detail with Example.

# OR

# Q13. Explain Data Reduction, Dimensionality Reduction and Data Compression.

# OR

# Q14. Explain Sampling, Feature Selection and PCA.

(All Combined)

---

# Data Reduction

## Definition

Data Reduction reduces data size while preserving important information.

---

## Need

* Reduce storage
* Faster processing
* Simplify analysis

---

## Techniques

### 1. Sampling

Use representative subset.

Example:

100000 customers

Sample = 1000 customers

Analysis performed on sample.

---

### 2. Feature Selection

Remove irrelevant attributes.

Example:

Employee Dataset

Attributes:

* Name
* Salary
* Blood Group
* Experience

Blood Group may be removed.

---

### 3. Dimensionality Reduction

Reduce number of features.

Example:

50 variables → 10 variables

---

### 4. Data Compression

Compress storage size.

Example:

100 MB → 20 MB

---

### 5. PCA (Principal Component Analysis)

Converts many variables into fewer principal components.

---

## Advantages

* Faster computation
* Lower storage
* Better visualization

---

## Conclusion

Data Reduction improves efficiency while maintaining useful information.

---

# Q15. Explain Working of PCA and State Applications.

---

# PCA (Principal Component Analysis)

## Definition

PCA is a dimensionality reduction technique that transforms many correlated variables into a smaller number of uncorrelated variables called Principal Components.

---

## Working of PCA

### Step 1

Collect dataset.

↓

### Step 2

Standardize data.

↓

### Step 3

Compute covariance matrix.

↓

### Step 4

Calculate Eigenvalues and Eigenvectors.

↓

### Step 5

Select principal components having highest Eigenvalues.

↓

### Step 6

Transform original data.

---

## Example

Student Dataset:

* Maths
* Physics
* Chemistry

Instead of 3 variables,

PCA may create:

PC1 = Overall Academic Performance

PC2 = Subject Variation

---

## Applications

1. Image Compression
2. Face Recognition
3. Data Visualization
4. Stock Market Analysis
5. Customer Segmentation
6. Machine Learning

---

## Advantages

* Reduces dimensions
* Removes redundancy
* Faster processing

---

## Conclusion

PCA efficiently reduces data complexity while preserving maximum information.

---

# Q16. Write Short Note on Data Discretization.

# OR

# Q17. Explain Data Discretization and its Methods.

# OR

# Q18. Explain Working of Binning with Example.

# OR

# Q19. What is Binning? How is it Used for Report Creation?

(All Combined)

---

# Data Discretization

## Definition

Data Discretization converts continuous data into discrete intervals or categories.

---

## Need

* Simplifies data
* Improves report readability
* Reduces noise

---

## Methods

### 1. Binning

Most important method.

---

### 2. Histogram Analysis

Create intervals using histogram.

---

### 3. Cluster Analysis

Create groups based on similarity.

---

### 4. Decision Tree Based

Generate intervals using splits.

---

# Binning

## Definition

Grouping values into intervals called bins.

---

## Example

Ages:

18,20,21,22,24,25,27,30

Bins:

18-20

21-23

24-26

27-30

---

## Types

### Equal Width Binning

0-10, 10-20, 20-30

---

### Equal Frequency Binning

Each bin contains same number of records.

---

## Use in Reporting

Age groups:

* Teenagers
* Adults
* Seniors

Reports become easier to understand.

---

## Advantages

* Reduces noise
* Better visualization
* Easier reporting

---

# Q20. Difference Between Univariate, Bivariate and Multivariate Analysis.

# OR

# Q21. Explain Univariate, Bivariate and Multivariate Analysis with Examples.

# OR

# Q22. What is Bivariate Analysis? Explain Types.

---

| Feature   | Univariate | Bivariate        | Multivariate        |
| --------- | ---------- | ---------------- | ------------------- |
| Variables | 1          | 2                | More than 2         |
| Purpose   | Describe   | Relationship     | Complex Analysis    |
| Example   | Marks      | Height vs Weight | Height, Weight, Age |

---

# Univariate Analysis

Study of one variable.

Example:

Student Marks

Methods:

* Mean
* Median
* Histogram

Application:
Understanding distribution.

---

# Bivariate Analysis

Study relationship between two variables.

Example:

Study Hours vs Marks

Methods:

* Scatter Plot
* Correlation
* Regression

Applications:
Trend analysis.

---

## Types of Bivariate Analysis

### Numerical-Numerical

Height vs Weight

---

### Numerical-Categorical

Salary vs Department

---

### Categorical-Categorical

Gender vs Purchase

---

# Multivariate Analysis

Study more than two variables simultaneously.

Example:

Age, Income, Education → Purchase Decision

Methods:

* PCA
* Multiple Regression
* Cluster Analysis

Applications:
Business forecasting.

---

# Conclusion

Univariate analyzes one variable, Bivariate studies relationships, and Multivariate handles complex real-world problems involving multiple variables.

---

# Q23. What is a Contingency Table?

# Q24. What is Marginal Distribution?

# Q25. Explain Contingency Table and Marginal Distribution with Example.

(Combined Answer)

---

# Contingency Table

## Definition

A contingency table is a table used to show the relationship between two categorical variables.

---

## Example

| Gender | Buy Product | Don't Buy | Total |
| ------ | ----------- | --------- | ----- |
| Male   | 40          | 20        | 60    |
| Female | 30          | 10        | 40    |
| Total  | 70          | 30        | 100   |

---

## Uses

* Analyze association
* Calculate probabilities
* Market research

---

# Marginal Distribution

## Definition

Marginal Distribution shows totals of rows or columns in a contingency table.

These totals appear on the margins (edges) of the table.

---

## Example

From above table:

Gender Distribution

Male = 60%

Female = 40%

Purchase Distribution

Buy = 70%

Don't Buy = 30%

These are marginal distributions.

---

## Applications

1. Probability calculation
2. Customer behavior analysis
3. Market segmentation
4. Business reporting

---

# Exam Priority (Most Important 10-Mark Questions)

1. Data Transformation (Very Important)
2. Data Reduction + PCA (Very Important)
3. Data Preprocessing & Data Cleaning
4. Data Exploration
5. Data Discretization & Binning
6. Univariate/Bivariate/Multivariate Analysis
7. Contingency Table & Marginal Distribution
8. Data Validation & Data Quality Issues

These 8 answers cover almost all repeated Unit-4 questions that typically appear in BI examinations.
