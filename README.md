# Large Scale Data Processing: Project 1

**Eagle ID:** 80948485  
**Name:** Rafael Espinoza

## 1. Local Machine Execution

For each difficulty level `k`, the program was run to find a nonce that satisfies the given difficulty level. The results are as follows:

| Difficulty (k) | Number of Trials (n) | Time Elapsed | Resulting String and Hash Value |
| -------------- | -------------------- | ------------ | ------------------------------- |
| 2              | 100                  | 3s           | `00717100cc9ce86bdaa64966022780f12deec80c6de4938b03b3cced9c9debae` |
| 3              | 10,000               | 3s           | `000427d2c9e9a30e2b3c784b897922d9d2df583a4d020e71d80902add5945c18` |
| 4              | 1,000,000            | 5s           | `0000efa806085c56fe9aff2ff8616406ddab7c91199b09b4fa8202e2ade67e6a` |
| 5              | 10,000,000           | 14s          | `00000f5566cc3da73ac8cb1bbc4014e1e1b97fc0314351b7e2777a47685fb82c` |
| 6              | 10,000,000           | 14s          | `0000005a822aa1ef31447849ffaba48a5b00e7c6cd5f06340eb05538103d23a5` |

## 2. Execution on Google Cloud Platform (GCP)

Using GCP's Dataproc service, the program was configured to solve for difficulty level `k=7`:

- **String and Hash Value**: `1483112146this_is_a_bitcoin_block_of_80948485,000000069ecc67c348630e1eec1a01d911c895e196f345668dd5e97c9cd8f33a`
- **Number of Trials (n)**: 10,000,000
- **Time Elapsed**: 330s
- **Cluster Configuration**:
    - The cluster, named espinorb-csci3390-cluster, was configured with a single master node of type n2-standard-4, which includes 4 vCPUs and 15 GB of memory. It did not utilize any worker nodes. The process for estimating the number of trials needed to find the nonce involved considering the difficulty level and the computational power of the cluster. Given the nature of the task and the hardware capabilities, a larger number of trials was deemed necessary for higher difficulty levels to increase the probability of finding a valid nonce within a reasonable time frame.

## 3. Sequential vs. Random Nonce Generation

A modification was made in `src/main/scala/project_1/main.scala` to change the nonce generation from random to sequential. This approach was tested to determine its efficiency compared to the original randomized method.

- **Observations**: The randomized approach showed to be faster, with a test on difficulty 6 on my local system taking about 17 seconds with the sequential method compared to 14 seconds with the random method.
- **Conclusion**: It appears that the randomized approach is generally more effective and efficient for this task. The randomness potentially allows for a broader coverage of the nonce space in less time, whereas sequential searching might systematically go through less optimal sequences before finding a solution, especially as the difficulty increases.

