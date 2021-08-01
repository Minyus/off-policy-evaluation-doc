---
marp: true
---
<!--
headingDivider: 1
-->

# Introduction to Off-policy Evaluation of Recommendation Systems 
## &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  Yusuke Minami

# What is Policy?

Policy = How to determine which item to recommend

# Policies with or without randomness

Policies without randomness (always take the same action)
- Rule-based policy -> Exploit
  - (e.g. games for teenagers, Apple Airpods for iPhone users, etc.) 
- Always choose the item with highest probability estimated by a Machine Learning Model -> Exploit

Policies with randomness (throw a dice)
- Uniformly random assignment (throw an unbiased dice) -> Explore
- Randomly choose the item based on probability estimated by a Machine Learning Model (throw biased dice) -> Explore & Exploit
- Multi-armed Bandit (throw biased dice) -> Explore & Exploit
  - Epsilon Greedy, Upper Confidence Bound, Thompson Sampling, etc.

![bg 90% right:10%](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUY97spTjTr8zFRxMTiwtCyK1-hCFCT8wHjknhYbZ-2NWCdivNNl2JfaozhO1kqKje9BoC6Q3TzA0&usqp=CAU)

# Why randomness?

Explore
- Keep learning, keep open to discoveries, and adapt to changes!

![h:400px](https://miro.medium.com/max/875/1*bpE-3aBYsetOLL0GG8pGDQ.jpeg)

# Policy evaluation

Online policy evaluation
- Evaluate based on Randomized Controlled Trial (RCT) or A/B Testing of policies

Offline policy evaluation (OPE)
- Counterfacturial: What if a new policy (model) was used?

Proposed Offline policy evaluation methods:
- Replay Method (RM)
- Inverse Probability Weighting (IPW) a.k.a Inverse Probability Scoring (IPS)
- Direct Method (DM)
- Doubly Robust (DR)
- and many more

# Replay Method (RM)

Replay Method (RM)
- Use fraction of users with recommended item matches the random assignment
- Requires uniform random assignment
- Used by Netflix around 2017: [Artwork Personalization at Netflix](https://netflixtechblog.com/artwork-personalization-c589f074ad76)

![](https://miro.medium.com/max/3000/0*gcQNqEUdCfWMTv0i.)


# Inverse Probability Weighting (IPW)

Inverse Probability Weighting (IPW)
- Weight each sample by inverse probability to be recommended.
  - e.g. for item A with propensity = 0.2 (20%), weight by 5
- Requires probability (propensity) to be recommended
- Unstable if the propensity is near 0% (or 100%)

![bg 100% right:50%](https://miro.medium.com/max/788/1*t_rbWJNhM7u-3h3uBi301g.jpeg)

[Source: Solving Simpson’s Paradox with Inverse Probability Weighting](https://towardsdatascience.com/solving-simpsons-paradox-with-inverse-probability-weighting-79dbb1395597)

# Direct Method (DM)

Direct Method (DM)

- Use estimation (based on another Machine Learning model for evaluation)

# Doubly Robust (DR)

- Combine DM and IPW

[Source: Causally regularized machine learning](https://www.slideshare.net/ssuser2ff343/causally-regularized-machine-learning)

![bg 80% right:70%](https://image.slidesharecdn.com/causallyregularizedmachinelearning-190826085536/95/causally-regularized-machine-learning-44-638.jpg?cb=1566809782)

# Python packages for OPE

- https://github.com/st-tech/zr-obp

- https://github.com/banditml/offline-policy-evaluation

# Simplest way for OPE

1. Apply random assignment for subset of users
2. Use Replay Method to evaluate your new model

# References

[Artwork Personalization at NetflixArtwork Personalization at Netflix](https://netflixtechblog.com/artwork-personalization-c589f074ad76)

[Unbiased Offline Evaluation of Contextual-bandit-based News Article Recommendation Algorithms](https://arxiv.org/pdf/1003.5956.pdf)

[Recommendations as Treatments: Debiasing Learning and Evaluation](https://arxiv.org/pdf/1602.05352.pdf)

[Offline Evaluation to Make Decisions About Playlist Recommendation Algorithms](http://pchandar.github.io/static/Gruson2019-a2c9a8576182dcb33019d20a7c7a51b7.pdf)

[Open Bandit Dataset and Pipeline: Towards Realistic and Reproducible Off-Policy Evaluation](https://arxiv.org/pdf/2008.07146.pdf)
