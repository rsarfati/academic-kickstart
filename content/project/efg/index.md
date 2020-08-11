---
title: Correlated Equilibria in Extensive Form Games
summary: Python package to represent extensive form games and compute various correlated equilibrium concepts via reinforcement learning algorithms.

tags:
- Reinforcement Learning
- Games
- Imperfect Information
- Correlated Equilibrium
- Theory

date: "2020-01-07T00:00:00Z"

# Optional external URL for project (replaces project detail page).
#external_link: "https://github.com/FRBNY-DSGE/ModelConstructors.jl"

links:
- icon: github
  icon_pack: fab
  name: GitHub Repository
  url: "https://github.com/rsarfati/ExtensiveFormGames"
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""
---

### Features
- Specify multi-player extensive form games as tree structures, with potentially imperfect information
  * Convert from extensive form to normal (strategic) form games
  * Convert from extensive form to sequence form games
- Compute correlated equilibria using linear programming techniques 
  * Simplex
  * Lemke-Howlson
- Reinforcement Learning Algorithms
  * Weighted Majority
  * Perturbed Follow-the-Leader
  * Regularized Follow-the-Leader 

### Coming Soon in Feb. 2020
+ Compute correlated equilibria using counterfactual regret minimization algorithms

### Reference Papers
+ [Correlated Q-Learning](https://www.aaai.org/Papers/ICML/2003/ICML03-034.pdf) (Greenwald and Hall, 2003)
+ [Combining No-regret and Q-learning](https://arxiv.org/pdf/1910.03094.pdf) (Kash, Sullins, and Hofmann, 2019)
+ [No-Regret Learning in Convex Games](https://www.cs.cmu.edu/~ggordon/gordon-greenwald-marks-icml-phi-regret.pdf) (Gordon, Greenwald, and Marks, 2008)

