# RISC-V Edge AI using SiFive Freedom Studio

> Hands-on implementation of Artificial Intelligence and Machine Learning algorithms using Python, followed by an exploration of deployment on the RISC-V ecosystem through **SiFive Freedom Studio** as part of the **VSD RISC-V Edge AI Workshop**.

---

# Course Information

| Details | Description |
|----------|-------------|
| Course | RISC-V Edge AI |
| Organization | VLSI System Design (VSD) |
| Platform | VLSI System Design |
| Course Link | https://www.vlsisystemdesign.com/riscv_edgeai/ |

---

# Project Overview

This repository documents my learning journey through the **RISC-V Edge AI Workshop** conducted by **VLSI System Design (VSD)**.

The objective of this course was to understand the complete workflow of developing Artificial Intelligence models and deploying them onto RISC-V based embedded systems.

Unlike traditional Machine Learning tutorials that stop after model training, this course introduces the concepts of **Edge AI**, where inference is performed directly on embedded hardware instead of cloud servers.

Throughout this workshop I implemented:

- Linear Regression
- Polynomial Regression
- Gradient Descent
- Neural Networks
- MNIST Handwritten Digit Classification
- Multi-Layer Perceptron (MLP)
- AI model deployment workflow
- RISC-V development using SiFive Freedom Studio

The practical implementation was performed using Python (Google Colab) while deployment experiments were carried out using SiFive Freedom Studio and the RISC-V toolchain.

---

# Repository Structure

```
.
├── README.md
├── files/
│   ├── Module 2.pdf
│   ├── Student Scores Comparison.pdf
│   ├── Startup Regression Comparison.pdf
│   ├── Neural Network Notes.pdf
│   └── ...
├── screenshots/

```

The **files/** directory contains exported PDFs documenting each experiment, plots, and implementation carried out during the course.

---

# Learning Objectives

Through this workshop, I learned to:

- Understand Artificial Intelligence fundamentals
- Differentiate Machine Learning techniques
- Implement Regression algorithms
- Understand Gradient Descent mathematically
- Build Neural Networks
- Train AI models using MNIST
- Understand Edge AI deployment
- Explore the RISC-V software ecosystem
- Use SiFive Freedom Studio
- Understand embedded AI workflows

---

# Artificial Intelligence Fundamentals

Artificial Intelligence (AI) enables computers to perform tasks that typically require human intelligence, such as:

- Image Recognition
- Speech Recognition
- Language Understanding
- Decision Making
- Prediction
- Learning from Experience

Unlike traditional programming, AI systems **learn patterns from data** instead of following fixed rules.

---

## Traditional Programming

```
Input + Rules
       │
       ▼
    Output
```
The programmer manually writes every rule.

The computer never learns.

---

## Artificial Intelligence

```
Input + Output
       │
       ▼
Model learns Rules
```

Instead of explicitly writing rules, we provide many examples.

The AI model automatically discovers hidden relationships within the data.

Example:

Thousands of handwritten digits

↓

AI observes patterns

↓

Learns how each digit looks

↓

Predicts unseen digits

---

# What is Machine Learning?

Machine Learning (ML) is a branch of Artificial Intelligence where computers improve automatically through experience without being explicitly programmed.

Instead of memorizing rules, Machine Learning discovers mathematical relationships between inputs and outputs.

General workflow:

```
Collect Dataset
        │
        ▼
Preprocess Data
        │
        ▼
Train Model
        │
        ▼
Evaluate Accuracy
        │
        ▼
Deploy Model
```

---

# Types of Machine Learning

## 1. Supervised Learning

The model learns from labeled data.

Example:

```
Study Hours
       │
       ▼
Exam Score
```

or

```
House Size
      │
      ▼
House Price
```

The correct answers are already known during training.

Examples implemented in this repository:

- Student Scores Dataset
- Startup Profit Prediction

---

## 2. Unsupervised Learning

The model receives only input data.

There are no labels.

Its objective is to discover hidden patterns or clusters.

Example:

Customer Segmentation

↓

Groups customers having similar buying behaviour.

---

## 3. Reinforcement Learning

The model learns through rewards and penalties.

Example:

Robot Navigation

```
Correct Action

↓

Reward

Wrong Action

↓

Penalty
```

Applications include:

- Robotics
- Autonomous Vehicles
- Game Playing AI

---

# Artificial Intelligence Workflow

```
Dataset
      │
      ▼
Data Cleaning
      │
      ▼
Feature Extraction
      │
      ▼
Model Training
      │
      ▼
Evaluation
      │
      ▼
Deployment
      │
      ▼
Prediction
```

Every AI project follows approximately the same pipeline.

---

# Regression

Regression predicts **continuous numerical values**.

Examples include:

- Salary Prediction
- House Price Prediction
- Student Marks
- Startup Profit

Regression answers the question:

> "How much?"

instead of

> "Which class?"

---

# Linear Regression

Linear Regression finds the **best fitting straight line** through the data.

Mathematical Equation

```
Y = mX + c
```

Where

- **m** = slope
- **c** = intercept

The objective is to minimize the prediction error between the line and the actual dataset.

### Analogy

Imagine placing a ruler over scattered points on paper.

You continuously rotate and shift the ruler until it passes as close as possible to every point.

That ruler represents the Linear Regression model.

---

# Polynomial Regression

Real-world data is often nonlinear.

Instead of fitting a straight line, Polynomial Regression fits a curve.

General Equation

```
Y = aX³ + bX² + cX + d
```

Higher-order polynomials allow the model to capture curved relationships.

### Analogy

Suppose you are constructing a road across mountains.

A straight road cannot follow the terrain.

A curved road adapts naturally to the landscape.

Polynomial Regression behaves similarly by bending to better fit nonlinear data.

---

# Model Training

Training is the process through which an AI model gradually learns the relationship between inputs and outputs.

During training:

```
Predict

↓

Measure Error

↓

Update Parameters

↓

Predict Again

↓

Repeat
```

After many iterations, the prediction error becomes very small.

The model is then considered trained.

---

# Loss Function

A Loss Function measures how incorrect a prediction is.

```
Small Loss

↓

Good Model

Large Loss

↓

Poor Predictions
```

The goal of every learning algorithm is to minimize the loss value throughout training.

---

# Gradient Descent

Gradient Descent is the optimization algorithm responsible for updating model parameters.

Each iteration consists of:

```
Initialize Weights

↓

Predict

↓

Calculate Error

↓

Compute Gradient

↓

Update Weights

↓

Repeat
```

Eventually the model reaches the minimum possible error.

### Analogy

Imagine standing blindfolded on top of a hill.

You cannot see the valley.

You only feel the slope beneath your feet.

By repeatedly taking small downhill steps, you eventually reach the lowest point.

Gradient Descent follows exactly this principle to minimize prediction error.

---


# Neural Networks

A Neural Network is a computational model inspired by the human brain.

Instead of relying on a single equation like Linear Regression, Neural Networks consist of multiple interconnected layers of neurons capable of learning highly complex patterns.

General Architecture

```
Input Layer
      │
      ▼
Hidden Layer
      │
      ▼
Hidden Layer
      │
      ▼
Output Layer
```

Each neuron performs a mathematical operation and passes its result to the next layer.

---

# Activation Function

Without activation functions, a Neural Network behaves like a Linear Regression model regardless of the number of layers.

Activation functions introduce **non-linearity**, allowing the network to solve complex problems.

The network implemented in this project uses the **ReLU (Rectified Linear Unit)** activation function.

```
ReLU(x)

if x < 0

↓

0

if x > 0

↓

x
```

Advantages of ReLU:

- Computationally efficient
- Faster convergence
- Prevents vanishing gradients
- Widely used in modern Deep Learning models

---

# Weights and Biases

Every neuron contains:

- Weights
- Biases

### Weight

Weights determine the importance assigned to each input.

Higher weight

↓

Greater influence

Lower weight

↓

Less influence

### Bias

Bias shifts the activation function and helps the model fit data more accurately.

### Analogy

Imagine asking three teachers whether a student deserves admission.

Teacher A has extensive experience.

Teacher B has moderate experience.

Teacher C is a beginner.

Naturally, Teacher A's opinion influences the final decision more.

Neural Networks work the same way using weights.

---

# Epoch

An Epoch means one complete pass through the entire training dataset.

Example

Training Images

```
60,000
```

One Epoch

↓

Model processes all 60,000 images once.

Multiple epochs allow the model to gradually improve its predictions.

---

# MNIST Dataset

The MNIST dataset is one of the most widely used benchmark datasets for handwritten digit recognition.

Dataset Statistics

Training Images

```
60,000
```

Testing Images

```
10,000
```

Image Size

```
28 × 28 pixels
```

Each image contains

```
784 pixels
```

After flattening,

```
28 × 28

↓

784 Features
```

Output Classes

```
0
1
2
3
4
5
6
7
8
9
```

---

# Multi-Layer Perceptron (MLP)

For handwritten digit classification, a Multi-Layer Perceptron (MLP) classifier was implemented.

Architecture used:

```
Input Layer

784 neurons

↓

Hidden Layer 1

64 neurons

↓

Hidden Layer 2

64 neurons

↓

Output Layer

10 neurons
```

Training Configuration

- Activation Function: ReLU
- Optimizer: Adam
- Hidden Layers: (64, 64)
- Maximum Iterations: 300

The trained model achieved approximately **97% accuracy** on the MNIST test dataset.

---

# Edge AI

Traditional AI systems generally rely on cloud computing.

```
Sensor

↓

Internet

↓

Cloud Server

↓

Prediction
```

This introduces:

- Internet dependency
- Higher latency
- Privacy concerns

Edge AI performs inference directly on embedded hardware.

```
Sensor

↓

Embedded Processor

↓

Prediction
```

Advantages

- Low latency
- Improved privacy
- Lower power consumption
- Offline operation
- Reduced cloud dependency

---

# Why RISC-V?

RISC-V is an open-source Instruction Set Architecture (ISA) designed for flexibility and scalability.

Advantages include:

- Open standard
- Low power consumption
- Custom instruction extensions
- Cost effectiveness
- Suitable for Embedded AI applications

The workshop demonstrates how AI models developed in Python can eventually be deployed onto RISC-V based embedded platforms.

---

# Experiment 1 — Student Scores Prediction

The first experiment introduces supervised learning using a simple Student Scores dataset.

Input

- Study Hours

Output

- Student Score

The following steps were performed:

- Data visualization
- Scatter plot generation
- Train-Test Split
- Linear Regression
- Polynomial Regression
- Performance comparison

### Learning Outcome

This experiment demonstrates how increasing study hours generally improves examination performance while introducing the fundamentals of regression.

---

# Experiment 2 — Startup Profit Prediction

The second experiment uses the **50 Startups** dataset.

Input Features

- Research & Development Spend
- Administration Cost
- Marketing Spend

Target

- Company Profit

Regression models were trained to understand how company investments affect overall profitability.

The experiment compares:

- Linear Regression
- Polynomial Regression

to observe differences in prediction capability.

---

# Experiment 3 — Linear Regression from Scratch

Instead of relying solely on Scikit-Learn, Linear Regression was implemented manually.

The implementation included:

- Weight Initialization
- Prediction Function
- Cost Function
- Gradient Descent
- Parameter Updates

### Learning Outcome

This experiment provides insight into how machine learning algorithms optimize themselves during training rather than functioning as black boxes.

---

# Experiment 4 — Neural Network Classification

The final experiment uses an MLP classifier to recognize handwritten digits from the MNIST dataset.

Workflow

```
Load Dataset

↓

Flatten Images

↓

Train Neural Network

↓

Evaluate Accuracy

↓

Predict Digits
```

The trained model achieved approximately **97% classification accuracy**, demonstrating the effectiveness of neural networks for image recognition tasks.

---

# AI Development Workflow Followed

```
Problem Statement

↓

Dataset Collection

↓

Data Preprocessing

↓

Feature Engineering

↓

Model Selection

↓

Training

↓

Testing

↓

Evaluation

↓

Embedded Deployment
```

This workflow forms the foundation of most practical AI applications.

---

# SiFive Freedom Studio

To explore deployment on embedded hardware, SiFive Freedom Studio was used.

The software environment included:

- SiFive Freedom Studio
- Freedom Metal SDK
- RISC-V GCC Toolchain
- QEMU Emulator

The objective was to understand how trained AI applications can be compiled and prepared for execution on RISC-V embedded processors.

---

# Challenges Faced

Although the AI models were successfully implemented and validated in Python, the embedded deployment stage presented several practical challenges.

The primary limitations encountered during this project were:

- The **VSDSquadron RISC-V development board** was not available, preventing deployment and testing on actual hardware.
- Setting up **SiFive Freedom Studio**, the RISC-V toolchain, and the Freedom Metal SDK involved multiple configuration and compatibility issues.
- Considerable time was spent resolving build errors, compiler path issues, BSP configuration, and project setup.
- Due to these hardware and software limitations, only the software workflow and QEMU-based experimentation could be explored.

Despite these challenges, the project provided valuable experience in understanding the complete Edge AI pipeline—from machine learning model development to embedded deployment concepts.

---

# Files Included

The `files/` directory contains supporting documentation for all experiments performed during the workshop, including:

- Student Scores Regression
- Startup Profit Regression
- Gradient Descent Implementation
- Neural Network Training
- MNIST Classification Results
- Comparison Graphs
- Training Outputs

These documents showcase the implementation process, observations, plots, and outputs generated throughout the course.

---

# Skills Gained

Throughout this workshop, I developed practical knowledge in:

### Programming

- Python

### Libraries

- NumPy
- Pandas
- Matplotlib
- Scikit-Learn
- TensorFlow (MNIST Dataset)

### Machine Learning

- Supervised Learning
- Linear Regression
- Polynomial Regression
- Gradient Descent
- Neural Networks
- Multi-Layer Perceptron
- MNIST Classification

### Embedded Systems

- RISC-V Ecosystem
- SiFive Freedom Studio
- Freedom Metal SDK
- GCC Toolchain
- QEMU Emulator

### Concepts

- Edge AI
- AI Deployment Workflow
- Model Training
- Model Evaluation
- Embedded Inference

---

# References

- VLSI System Design – RISC-V Edge AI Workshop  
  https://www.vlsisystemdesign.com/riscv_edgeai/

- TensorFlow MNIST Dataset

- Scikit-Learn Documentation

- SiFive Freedom Studio

- RISC-V International

---

# Acknowledgement

I would like to express my sincere gratitude to the mentors and instructors at **VLSI System Design (VSD)** for designing and delivering this practical RISC-V Edge AI workshop.

Special thanks to:

- **Kunal Ghosh** – Co-Founder, VLSI System Design, for creating an industry-oriented learning platform and providing practical insights into RISC-V, VLSI, and semiconductor education. :contentReference[oaicite:0]{index=0}
- **Anagha Ghosh** – VLSI System Design, for her support in the workshop and contributions to the VSD learning initiatives. :contentReference[oaicite:1]{index=1}
- **Ankit Mawle** – for conducting the hands-on sessions and explaining the Artificial Intelligence, Python, and Edge AI implementation workflow.
- **Dhanvanti Bhavskar** – for guidance during the workshop and support throughout the practical implementation of the RISC-V Edge AI course.


---
## Note

This repository documents my complete learning process throughout the workshop.

While all Machine Learning experiments were successfully implemented and evaluated in Python, real-time deployment on hardware could not be completed because the **VSDSquadron development board was unavailable**. Additionally, significant time was spent resolving **SiFive Freedom Studio configuration, BSP, and toolchain setup issues**.

Nevertheless, the project successfully demonstrates the complete software workflow for developing, training, evaluating, and preparing AI models for deployment on RISC-V based embedded systems.
