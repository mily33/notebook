### Learning by Playing-Solving Sparse Reward Tasks from Scratch

**key idea:** active scheduling and execution of auxiliary policies allows the agent to efficiently explore its environment.

**Existing methods:**

* shaping reward
* curriculum learning
* sim-to-real
* learning from demonstrations
* learning with model guidance
* inverse RL

**Problem:**  all these methods bias the policy \(suboptimal\)

#### Method

an MDP is defined as a tuple $$(\mathcal{S}, \mathcal{A}, \mathcal{R}, P, \gamma)$$.

main task: $$\mathcal{M}$$

auxiliary task: $$\mathcal{A} = \{\mathcal{A}_1, \dots, \mathcal{A}_K\}$$

$$\mathcal{J} = \mathcal{M} \cup \mathcal{A}$$

#### Learning the intentions

$$
\mathcal{L}(\theta) = \sum_{\mathcal{T} \in \mathcal{J}}\mathcal{L}(\theta; \mathcal{T}) \\
\mathcal{L}(\theta; \mathcal{T}) = \sum_{\mathcal{B} \in \mathcal{J}} \mathbb{E}_{p(s|\mathcal{B})}[]
$$
