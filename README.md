#  Decoding for 5G NR Using LDPC Codes

This repository contains the documentation, analysis, and simulation results of our academic project on **Low-Density Parity-Check (LDPC) Codes** and their implementation in the **5G New Radio (NR)** standard. This project was developed as part of the course **CT-216: Introduction to Communication Systems** at [Your Institution Name], under the guidance of Professor **Yash Vasavada** and Mentor TA **Khushi Shah**.

---

##  Table of Contents

- [Overview](#overview)
- [What is LDPC?](#what-is-ldpc)
- [LDPC in 5G Standards](#ldpc-in-5g-standards)
- [Base Graphs and Expansion Factors](#base-graphs-and-expansion-factors)
- [Encoding & Modulation](#encoding--modulation)
- [AWGN Channel Modeling](#awgn-channel-modeling)
- [Decoding Techniques](#decoding-techniques)
- [Tanner Graph Representation](#tanner-graph-representation)
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Performance Analysis](#performance-analysis)
- [Conclusion](#conclusion)
- [Team Members](#team-members)
- [References](#references)
- [Honour Code](#honour-code)

##  Overview

The purpose of this project is to explore the significance of LDPC codes in 5G NR and analyze their performance using various decoding techniques. LDPC codes offer near-Shannon-limit performance and are thus crucial for high-speed and reliable communication.

---

##  What is LDPC?

**Low-Density Parity-Check (LDPC)** codes are a class of linear block codes first introduced by **Robert Gallager** in his PhD thesis (1960). The term "low-density" refers to the sparse nature of the **parity-check matrix (H)**, which contains significantly fewer 1s than 0s.

### Key Properties:
- **Forward Error Correcting**: LDPC codes can efficiently correct transmission errors in noisy channels.
- **Close to Shannon Limit**: Their performance approaches the theoretical maximum capacity of a channel.
- **Linear-Time Decoding Algorithms**: Iterative decoding methods make LDPC codes computationally practical.
- **Parallelization**: Ideal for hardware implementations that leverage parallel computation.

### Representation:
There are two main ways to represent LDPC codes:
1. **Matrix Representation**: Using a sparse parity-check matrix.
2. **Graphical Representation**: Using a **Tanner Graph**, a bipartite graph with:
   - **Variable Nodes (VNs)** – Represent bits in the codeword.
   - **Check Nodes (CNs)** – Represent parity constraints.
   - Each CN follows an \((n, n-1)\) SPC code; each VN follows a repetition code.

---

##  LDPC in 5G Standards

The **3GPP** (3rd Generation Partnership Project) selected LDPC codes as the primary forward error correction (FEC) scheme for user data in 5G NR. Their ability to offer both high throughput and robustness makes them suitable for 5G’s diverse applications, from mobile broadband to ultra-reliable low-latency communications.

### Advantages in 5G:
- High speed and low complexity
- Flexible code lengths and rates
- Robust against noisy environments
- Enhanced application responsiveness

### Other Codes in 5G:
- **Polar Codes**: Used for control channels
- **Turbo and Convolutional Codes**: Used for backward compatibility

---

##  Base Graphs and Expansion Factors

LDPC codes in 5G use **two base graphs**:
- **BG1**: 46 × 68 matrix
- **BG2**: 42 × 52 matrix

### Expansion:
The base graphs are expanded using **right-shifted identity matrices** to form large LDPC matrices:
- Expansion factor **Z** scales the matrix dimensions
- Permutation matrices ensure structured sparsity
- Puncturing and shortening adjust the final code rate

---

##  Encoding & Modulation

We encoded data using the base matrices and applied **BPSK modulation**:
- \( s = 1 - 2a \)
- \( r(t) = s + n(t) \), where \( n(t) \) is AWGN

### Rate Matching:
- Adjusts the encoded block size to match the desired transmission rate
- Uses puncturing and expansion techniques

---

##  AWGN Channel Modeling

In real communication, signals are distorted by **Additive White Gaussian Noise (AWGN)**.

- **SNR (Signal-to-Noise Ratio)** is used to measure channel quality.
- At low SNR, bit errors increase unless FEC codes like LDPC are applied.
- We modeled both **continuous-time** and **discrete-time** AWGN channels.

---

##  Decoding Techniques

###  Hard Decision Decoding
- Based on thresholding received signal (e.g., 0)
- Low complexity, suitable for real-time or embedded systems

###  Soft Decision Decoding
- Computes **Log-Likelihood Ratios (LLRs)** based on probabilistic models
- More accurate, especially in low SNR scenarios
- Includes **SISO Decoders** and **Extrinsic vs Intrinsic LLRs**

###  Min-Sum and Offset Min-Sum Approximation
- Simplifies the Sum-Product algorithm by taking the minimum instead of full probabilities
- **Offset Min-Sum** further improves performance by biasing toward lower magnitudes

---

##  Tanner Graph Representation

Tanner Graphs are essential to LDPC decoding:

- **Variable Nodes (VNs)** send messages to **Check Nodes (CNs)** and vice versa.
- The messages are iteratively updated to converge on a valid codeword.
- In **hard decision decoding**, nodes use majority logic and SPC constraints.
- In **soft decision decoding**, nodes pass LLR values.

---

##  Monte Carlo Simulation

We used Monte Carlo simulations to:
- Predict the probability of decoding success
- Estimate **Bit Error Rate (BER)** under various conditions
- Compare performances for different base matrices, expansion factors, and code rates

---

##  Performance Analysis

We performed simulations using:
- **Custom 9x12 H-matrix**
- **Base Matrices NR_2_6_52 and NR_1_5_352**
- Various code rates: 1/4, 1/3, 1/2, 3/5, 4/5

### Observations:

####  Performance Proximity
- Both hard and soft decision decoding for large LDPC matrices **approach the Shannon capacity bound**, indicating near-optimal performance.

####  Trade-offs
- Soft decision decoding offers better performance at low SNRs.
- Performance gap between hard and soft decoding narrows for larger matrices.

####  Complexity Considerations
- Hard decision decoding is simpler and suitable for **resource-constrained** devices.
- Soft decision decoding provides superior error correction at the cost of computational resources.

####  Practical Applications
- Choose hard decoding for real-time systems with limited hardware.
- Choose soft decoding for systems demanding **high reliability** in noisy environments.

---

##  Conclusion

LDPC codes are a cornerstone of modern communication, especially 5G. Our project demonstrates:
- Their theoretical foundations and practical implementations
- Trade-offs between decoding techniques
- Their exceptional performance under realistic noise models
- Their ability to **approach channel capacity**, enabling efficient communication

---
