# LDPC_Decoding_for_5G_NR
LDPC codes are forward error correcting, which means they can efficiently correct transmission errors in noisy channels. Coding schemes in 5G technology provide increased speed and reliability, which allows developers to create applications faster and more responsively.
Low-density parity-check (LDPC) codes are a class of linear block codes that were first introduced by Gallager in his PhD thesis in 1960. The name comes from the characteristic of their parity-check matrix which contains only a few 1’s in comparison to the amount of 0’s. 
Their main advantage is that they provide a performance which is very close to the capacity for a lot of different channels and linear time complex algorithms for decoding. Furthermore, they are suited for implementations that make heavy use of parallelism.
We represents LDPC codes by Tanner Graphs-a bipartite graphical structure. It contains two types of nodes in the graph: Check nodes & Variable nodes. Each Check node follows (n, n-1) SPC code. Each Variable node follows repetition code.
<p>
There are 2 different ways of representing LDPC code: Linear block codes that are used via matrices. Second possibility is a graphical representation (Tanner Graph)
</p>
<p>
Performance Proximity: Both soft and hard decision decoding approaches for LDPC with large base matrices closely approach the Shannon capacity bound, indicating near-optimal performance.
Trade-offs: While soft decoding generally outperforms hard decoding, especially in low signal-to-noise ratio (SNR) scenarios, the performance gap diminishes with larger matrices, suggesting potential convergence in efficiency.
Complexity Considerations: Hard decision decoding offers simplicity and lower computational load compared to soft decision decoding, making it suitable for resource-constrained environments. However, soft decision decoding provides better error correction capabilities, crucial for low SNR environments.
</p>
