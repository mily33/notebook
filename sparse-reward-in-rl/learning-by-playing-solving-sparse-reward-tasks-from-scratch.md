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

an MDP is defined as a tuple $$(\mathbb{S}, \mathbb{A}, \mathbb{R}, \mathbb{P}, \rho_0, \gamma)$$.

main task: $$\mathcal{M}$$

auxiliary task: $$\mathcal{A} = \{\mathcal{A}_1, \dots, \mathcal{A}_K\}$$

$$\mathcal{J} = \mathcal{M} \cup \mathcal{A}$$, $$\mathcal{M}$$ and $$\mathcal{A}$$ share $$\mathbb{S}, \mathbb{A}, \mathbb{P}, \gamma$$.

#### Learning the intentions

$$\theta$$ is parameters of policy $$\pi$$.


$$
\mathcal{L}(\theta) = \sum_{\mathcal{T} \in \mathcal{J}}\mathcal{L}(\theta; \mathcal{T}) \tag{1}
$$


For each task $$\mathcal{T}$$,


$$
\mathcal{L}(\theta; \mathcal{T}) = \sum_{\mathcal{B} \in \mathcal{J}} \mathbb{E}_{p(s|\mathcal{B})}[Q_\mathcal{T}(s,a)|a \sim \pi_\theta(\cdot|s, \mathcal{T})] \tag{2}
$$


where


$$
Q_\mathcal{T}(s, a) = r_\mathcal{T}(s,a) + \gamma \mathbb{E}_{\pi_\mathcal{T}}[R_\mathcal{T}(\tau_{t+1: \infty})],
$$



$$
\mathbb{E}_{\pi_\mathcal{T}}\left[R_\mathcal{T}(\tau_{t: \infty})\right] = \mathbb{E}_{\pi_\mathcal{T}}\left[\sum_{i=0}^\infty \gamma^i r_\mathcal{T}(s_{t+i}, a_{t+i})\right].
$$


#### Learning the scheduler $$\mathcal{S}$$

$$
\mathcal{L}(\mathcal{S}) = \mathbb{E}_{P_\mathcal{S}}\left[R_\mathcal{M}(\mathcal{T}_{0:H-1})|\mathcal{T}_h \sim P_\mathcal{S}(\mathcal{T}|\mathcal{T}_{0:{h-1}})\right] \tag{3}
$$

$$
R_\mathcal{M}(\mathcal{T}_{0:H-1}) = \sum_{h=0}^H \sum_{t=h\xi}^{(h+1)\xi-1}(\gamma^t r_\mathcal{M}(s_t, a_t)), \tag{4}
$$

where $$a_t \sim \pi_\theta(\cdot|s_t, \mathcal{T}_h)$$.

#### Estimate $$P_\mathcal{S}$$

$$
P_\mathcal{S} = \arg\max_{P_\mathcal{S}} \mathcal{L}(\mathcal{S}) \tag{5}
$$

$$P_\mathcal{S}(\mathcal{T}_h|\mathcal{T}_{1:h-1}; \eta)$$ is approximated by Boltzman distribution, 
$$
P_\mathcal{S}(\mathcal{T}_h|\mathcal{T}_{1:h-1}; \eta) = \frac{\exp(\mathbb{E}_{P_\mathcal{S}}[R_\mathcal{M}(\mathcal{T}_{h:H})] / \eta)}{\sum_{\mathcal{\bar T}_{h:H}}\exp(\mathbb{E}_{P_\mathcal{S}}[R_\mathcal{M}(\mathcal{\bar T}_{h:H})] / \eta)}. \tag{6}
$$

$$
\mathbb{E}_{P_\mathcal{S}}[R_\mathcal{M}(\mathcal{T}_{h:H})] \approx Q(\mathcal{T}_{1:h-1}, \mathcal{T}_h) = \frac{1}{M}\sum_{i=1}^M R_\mathcal{M}^\tau(\mathcal{T}_{h:H}) \tag{7}
$$


#### Policy evaluation

























