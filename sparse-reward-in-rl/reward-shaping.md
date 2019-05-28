# Reward Shaping

**Definition:**
A shaping reward function $$F: S \times A \times A \rightarrow \mathbb{R}$$ is potential-based if there exists $$\phi: S \rightarrow \mathbb{R}$$ s.t.
$$
F(s, a, s') = \gamma \Phi(s') - \Phi(s)
$$
