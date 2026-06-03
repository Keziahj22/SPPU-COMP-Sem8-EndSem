# UNIT 3 CNN – PYQ Analysis Based 10 Marks Answers

Many questions are repeated with different wording. You only need to prepare **8 major answers** and a few small theory points.

---

# 1. CNN ARCHITECTURE (Most Important)

### Covers Questions:

✅ Draw and explain CNN architecture in detail
✅ Explain CNN architecture with applications
✅ Describe typical CNN architecture and roles of components
✅ Explain flow of input image through CNN

---

# CNN Architecture

## Definition

Convolutional Neural Network (CNN) is a deep learning model specially designed for image processing and computer vision tasks. It automatically extracts features from images and performs classification.

---

## Diagram

```text
Input Image
      ↓
Convolution Layer
      ↓
ReLU Layer
      ↓
Pooling Layer
      ↓
Convolution Layer
      ↓
ReLU Layer
      ↓
Pooling Layer
      ↓
Flatten Layer
      ↓
Fully Connected Layer
      ↓
Softmax Output Layer
```

(Draw this in exam)

---

## Working of CNN

### 1. Input Layer

Receives image.

Example:

```text
64×64×3 RGB image
```

Contains raw pixel values.

---

### 2. Convolution Layer

Uses kernels/filters.

Extracts:

* Edges
* Shapes
* Corners
* Textures

Produces Feature Maps.

---

### 3. ReLU Layer

Applies:

[
f(x)=max(0,x)
]

Removes negative values and introduces non-linearity.

---

### 4. Pooling Layer

Reduces size of feature maps.

Benefits:

* Less computation
* Faster training
* Reduced overfitting

---

### 5. Flatten Layer

Converts 2D data into 1D vector.

Example:

```text
1 2
3 4
```

↓

```text
[1,2,3,4]
```

---

### 6. Fully Connected Layer

Combines extracted features and performs classification.

---

### 7. Softmax Layer

Converts outputs into probabilities.

Example:

```text
Cat = 0.85
Dog = 0.10
Car = 0.05
```

Prediction = Cat

---

## Advantages

* Automatic feature extraction
* High accuracy
* Less preprocessing
* Parameter sharing
* Efficient learning

---

## Applications

* Face Recognition
* Object Detection
* Medical Imaging
* Self Driving Cars
* Surveillance Systems

---

## Conclusion

CNN learns image features automatically and performs highly accurate classification and recognition tasks.

---

# 2. POOLING LAYER

### Covers Questions

✅ Pooling Layer with need
✅ Types of Pooling
✅ Features of Pooling
✅ Max Pooling and Average Pooling

---

# Pooling Layer

## Definition

Pooling is a down-sampling operation that reduces feature map dimensions while preserving important information.

---

## Need of Pooling

Without pooling:

* Large feature maps
* High memory usage
* Slow training
* Overfitting

Pooling solves these issues.

---

## Working

Input:

```text
1 3
2 9
```

Max Pooling Output:

```text
9
```

---

## Types

### 1. Max Pooling

Selects largest value.

Example:

```text
1 3
2 9
```

Output = 9

Most commonly used.

---

### 2. Average Pooling

Computes average.

Example:

```text
2 4
6 8
```

Output:

```text
(2+4+6+8)/4 = 5
```

---

### 3. Global Pooling

Pooling performed over complete feature map.

Produces single value.

---

## Features

### Dimensionality Reduction

Reduces data size.

### Translation Invariance

Small image shifts don't affect output.

### Faster Computation

Less processing required.

### No Learnable Parameters

No weights to train.

### Noise Reduction

Removes unnecessary information.

---

## Advantages

* Faster training
* Less memory
* Prevents overfitting
* Improves efficiency

---

# 3. ReLU LAYER

### Covers Questions

✅ Explain ReLU
✅ Advantages over Sigmoid
✅ Disadvantages
✅ Numerical Example

---

# ReLU (Rectified Linear Unit)

## Definition

ReLU is the most commonly used activation function in CNNs.

Introduces non-linearity.

---

## Mathematical Expression

[
f(x)=max(0,x)
]

---

## Numerical Example

Input:

```text
[-3,-2,-1,0,2,5,8]
```

Output:

```text
[0,0,0,0,2,5,8]
```

---

## Working

Negative values → 0

Positive values → unchanged

---

## Advantages

### Faster Training

Simple computations.

### Avoids Vanishing Gradient

Unlike Sigmoid.

### Sparse Activation

Many outputs become zero.

### Better Performance

Works well in deep networks.

---

## ReLU vs Sigmoid

| ReLU                      | Sigmoid                         |
| ------------------------- | ------------------------------- |
| Fast                      | Slow                            |
| Avoids vanishing gradient | Suffers from vanishing gradient |
| Simple                    | Complex                         |
| Better for deep CNN       | Less effective                  |

---

## Disadvantages

### Dying ReLU

Neuron may permanently output zero.

### Not Zero Centered

Output always positive.

---

## Conclusion

ReLU improves learning speed and training efficiency of CNN.

---

# 4. CONVOLUTION LAYER

### Covers Questions

✅ Working of convolution layer
✅ Features
✅ Stride convolution
✅ Applications

---

# Convolution Layer

## Definition

Convolution layer extracts important features from images using filters.

It is the core component of CNN.

---

## Working

Input Image:

```text
1 2 3
4 5 6
7 8 9
```

Kernel:

```text
1 0
0 1
```

Kernel slides over image.

Performs:

* Multiplication
* Addition

Produces Feature Map.

---

## Features

### Local Receptive Field

Looks at small image region.

### Parameter Sharing

Same filter used everywhere.

### Learnable Filters

Weights learned automatically.

### Feature Extraction

Detects:

* Edges
* Shapes
* Textures

---

## Stride Convolution

Stride = filter movement.

### Stride = 1

Detailed output.

### Stride = 2

Smaller output.

Faster computation.

---

## Applications

* Face Detection
* Medical Imaging
* Object Recognition
* Self Driving Cars
* Video Analytics

---

# 5. PADDING AND STRIDES

### Covers Questions

✅ Padding and types
✅ Strides
✅ Numerical output size question

---

# Padding

## Definition

Adding zeros around image boundaries.

---

## Need

Without padding:

* Output shrinks
* Edge information lost

Padding prevents this.

---

## Types

### 1. Valid Padding

No padding.

Output size decreases.

---

### 2. Same Padding

Output size remains same.

Most commonly used.

---

### 3. Full Padding

Maximum padding.

Output size increases.

---

# Strides

## Definition

Number of pixels filter moves each step.

---

### Stride = 1

More details.

Larger output.

---

### Stride = 2

Less details.

Smaller output.

Faster processing.

---

## Numerical Problem

Given:

```text
Input = 64×64
Kernel = 5×5
Stride = 2
Same Padding
```

Output:

[
64/2 = 32
]

Answer:

```text
Output Feature Map = 32×32
```

---

## How Padding Helps?

* Preserves border information
* Prevents shrinking
* Maintains spatial dimensions

---

# 6. DROPOUT + DATA AUGMENTATION

### Covers Questions

✅ Dropout Layer
✅ Data Augmentation and Regularization

---

# Dropout Layer

## Definition

Regularization technique used to reduce overfitting.

---

## Working

Random neurons are turned OFF during training.

Example:

```text
[2,4,6,8]
```

↓

```text
[2,0,6,0]
```

---

## Advantages

* Prevents overfitting
* Better generalization
* Improves robustness

---

# Data Augmentation

## Definition

Artificially increases dataset size by modifying existing images.

---

## Methods

* Rotation
* Cropping
* Zooming
* Flipping
* Brightness change

---

## Benefits

* More training data
* Better accuracy
* Better generalization
* Less overfitting

---

## Combined Role

Both techniques reduce overfitting and improve model performance.

---

# 7. LOCAL RESPONSE NORMALIZATION (LRN)

### Covers All LRN Questions

---

# Local Response Normalization

## Definition

LRN normalizes neuron outputs and creates competition among neighboring neurons.

---

## Need

Deep CNNs may produce extremely large activations.

LRN balances activations.

---

## Working

Strong activations become stronger.

Weak activations become weaker.

This improves feature discrimination.

---

## Benefits

### Stable Training

Prevents activation explosion.

### Better Generalization

Works better on unseen data.

### Reduced Overfitting

Controls excessive activations.

### Improved Accuracy

Enhances important features.

---

## Conclusion

LRN improves CNN learning by emphasizing useful features and suppressing weaker responses.

---

# 8. CNN TRAINING PROCESS

### Covers All Training Questions

---

# CNN Training Process

## Step 1

Input Image

---

## Step 2

Convolution Layer

Extract features.

---

## Step 3

ReLU

Add non-linearity.

---

## Step 4

Pooling

Reduce dimensions.

---

## Step 5

Flatten

Convert to 1D.

---

## Step 6

Fully Connected Layer

Perform classification.

---

## Step 7

Softmax Output

Generate probabilities.

---

## Step 8

Loss Calculation

Compare prediction with actual output.

Common Loss:

Cross Entropy Loss.

---

## Step 9

Backpropagation

Compute gradients.

---

## Step 10

Weight Update

Optimizer updates weights.

Examples:

* SGD
* Adam
* RMSProp

---

## Step 11

Testing and Evaluation

Measure accuracy.

---

## Why Normalization Important?

Convert:

```text
0–255
```

to

```text
0–1
```

Benefits:

* Faster convergence
* Stable gradients
* Better accuracy
* Faster learning

---

# 9. APPLICATIONS OF CNN

### Usually 5 Marks

Write Any 6–8 Points

### Applications

1. Face Recognition
2. Object Detection
3. Medical Image Analysis
4. Self Driving Cars
5. Video Surveillance
6. Speech Recognition
7. Natural Language Processing
8. Handwriting Recognition
9. Traffic Sign Detection
10. Drug Discovery

---

# 10. INTERLEAVING BETWEEN LAYERS

### Covers Entire Question

---

# Interleaving Between Layers

## Definition

Interleaving means arranging CNN layers repeatedly in a sequence.

---

## Example

```text
Convolution
      ↓
ReLU
      ↓
Pooling
      ↓
Convolution
      ↓
ReLU
      ↓
Pooling
```

---

## Why Important?

### Better Feature Extraction

Learns simple to complex features.

### Higher Accuracy

Captures detailed patterns.

### Reduced Overfitting

Pooling reduces redundant information.

### Faster Computation

Dimensionality gradually decreases.

---

## Role of Each Layer

### Convolution

Extracts features.

### ReLU

Adds non-linearity.

### Pooling

Reduces dimensions.

### Fully Connected

Classification.

### Softmax

Probability output.

---

# HIGH PRIORITY FOR EXAM (Must Do)

⭐⭐⭐⭐⭐ CNN Architecture
⭐⭐⭐⭐⭐ Pooling Layer
⭐⭐⭐⭐⭐ ReLU Layer
⭐⭐⭐⭐⭐ Convolution Layer
⭐⭐⭐⭐⭐ CNN Training Process

# MEDIUM PRIORITY

⭐⭐⭐⭐ Padding & Strides
⭐⭐⭐⭐ Dropout + Data Augmentation

# LOW BUT POSSIBLE

⭐⭐⭐ LRN
⭐⭐⭐ Interleaving Between Layers
⭐⭐⭐ Applications of CNN

If you finish the **first 5 topics thoroughly**, you can answer nearly **70–80% of CNN Unit-3 questions** from previous papers.
