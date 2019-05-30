#
## Learning by Playing-Solving Sparse Reward Tasks from Scratch

**key idea:** active scheduling and execution of auxiliary policies allows the agent to efficiently explore its environment.

**Existing methods:**

* shaping reward
* curriculum learning
* sim-to-real
* learning from demonstrations
* learning with model guidance
* inverse RL

**Problem:** all these methods bias the policy \(suboptimal\)

#### Method

an MDP is defined as a tuple $$(\mathcal{S}, \mathcal{A}, \mathcal{R}, P, \rho_0, \gamma)$$.

main task: $$\mathcal{M}$$

auxiliary task: $$\mathcal{A} = \{\mathcal{A}_1, \dots, \mathcal{A}_K\}$$

$$\mathcal{J} = \mathcal{M} \cup \mathcal{A}$$

#### Learning the intentions

$$
\mathcal{L}(\theta) = \sum_{\mathcal{T} \in \mathcal{J}}\mathcal{L}(\theta; \mathcal{T}) \tag{1}
$$
for each task $$\mathcal{T}$$,
$$
\mathcal{L}(\theta; \mathcal{T}) = \sum_{\mathcal{B} \in \mathcal{J}} \mathbb{E}_{p(s|\mathcal{B})}[Q_\mathcal{T}(s,a)|a \sim \pi_\theta(\cdot|s, \mathcal{T})] \tag{2}$$
where

$$
Q_\mathcal{T}(s, a) = r_\mathcal{T}(s,a) + \gamma \mathbb{E}_{\pi_\mathcal{T}}[R_\mathcal{T}(\tau_{t+1: \infty})],
$$,

$$
\mathbb{E}_{\pi_\mathcal{T}}[R_\mathcal{T}(\tau_{t: \infty})] = \mathbb{E}_{\pi_\mathcal{T}}[\sum_{i=0}^\infty \gamma^i r_\mathcal{T}(s_{t+i}, a_{t+i})].
$$

