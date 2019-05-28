# Reward Shaping

**Definition:**
A shaping reward function $$F: S \times A \times A \rightarrow \mathbb{R}$$ is potential-based if there exists $$\phi: S \rightarrow \mathbb{R}$$ s.t.
$$
F(s, a, s') = \gamma \Phi(s') - \Phi(s)
$$
**Theorem:**
If $$F$$ is a potential-based shaping function, then every optimal policy in $$M'= \langle S, A, T, \gamma, R+F \rangle$$ will also be an optimal policy in $$M = \langle S, A, T, \gamma, R \rangle$$