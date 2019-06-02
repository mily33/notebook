** Sparse Reward in RL**

In reinforcement learning, an agent learns a policy based on feedback from the environment. However, in many real-world scenarios, rewards extrinsic to the agent are extremely sparse, or absent altogether.

**Existing methods:**

* reward shaping 
* curriculum learning
* sim-to-real
* learning from demonstrations
* learning with model guidance
* inverse RL

** Reward Shaping**
Reward shaping is a commonly used technique to deal with sparse reward, where additional training rewards are used to guide the learning agent. 
**potential-based reward **
Andrew Ng first proposed a potential-based 


The goal of RL is to find a policy $$\pi(s, a;\theta)$$ that maximize the expected culmulative reward,
$$
\theta^* = \arg\max_\theta \mathbb{E}_\pi\left[\sum_t r_t\right] 
$$

There are two important terms, $$i.e.$$ policy $$\pi$$ and $$r_t$$.

additional reward term
