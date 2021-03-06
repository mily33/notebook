 Reward Shaping
Reward shaping is a commonly used technique to deal with sparse reward, where additional training rewards are used to guide the learning agent. 

**Definition:**
A shaping reward function $$F: S \times A \times S \rightarrow \mathbb{R}$$ is potential-based if there exists $$\phi: S \rightarrow \mathbb{R}$$ s.t.
$$
F(s, a, s') = \gamma \Phi(s') - \Phi(s)
$$
**Theorem:**
If $$F$$ is a potential-based shaping function, then every optimal policy in $$M'= \langle S, A, P, \gamma, R+F \rangle$$ will also be an optimal policy in $$M = \langle S, A, P, \gamma, R \rangle$$.
