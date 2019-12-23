---
title: Online Estimation of DSGE Models

authors: 
- Michael Cai
- Marco Del Negro
- Ethan Matlin
- admin
- Frank Schorfheide

date: "2019-09-04T00:00:00Z"
featured: true

summary: ""  # Add a page description.

links:
- icon: dungeon
  icon_pack: fas
  name: "Liberty Street Economics"
  url: "https://libertystreeteconomics.newyorkfed.org/2019/08/online-estimation-of-dsge-models.html"
---

The estimation of dynamic stochastic general equilibrium (DSGE) models is a computationally demanding task. As these models change to address new challenges (such as household and firm heterogeneity, the lower bound on nominal interest rates, and occasionally binding financial constraints), they become even more complex and difficult to estimate—so much so that current estimation procedures are no longer up to the task. This post discusses a new technique for estimating these models which belongs to the class of [sequential Monte Carlo](https://en.wikipedia.org/wiki/Particle_filter) (SMC) algorithms, an approach we employ to estimate the [New York Fed DSGE model](https://github.com/FRBNY-DSGE/DSGE.jl). To learn more, check out [this paper](https://www.newyorkfed.org/medialibrary/media/research/staff_reports/sr893.pdf) of ours.

DSGE models are typically estimated with [Bayesian](https://en.wikipedia.org/wiki/Bayesian_probability) techniques. To do so, a researcher represents her or his initial information about the model parameters by a probability distribution (called the [prior](https://en.wikipedia.org/wiki/Prior_probability)) and then updates this probability distribution in view of the observed time-series data. This updated distribution is called the posterior. In practice, generating random samples from the [posterior](https://en.wikipedia.org/wiki/Posterior_probability) distribution is a rather involved endeavor.

Currently, the most widely used method is the so-called random walk [Metropolis–Hastings](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm) algorithm. It is implemented, for instance, in the popular [Dynare](https://www.dynare.org/) software package. While this algorithm has been the bread and butter of [Bayesian macroeconometrics](https://www.oxfordhandbooks.com/abstract/10.1093/oxfordhb/9780199559084.001.0001/oxfordhb-9780199559084-e-8) for the past twenty years, it has two key disadvantages relevant to central bank applications.

First, it cannot take advantage of parallel computing. Intuitively, Metropolis–Hastings algorithms work by letting one particle (that is, one vector containing all the model’s parameters) travel through the parameter space, spending more time in areas associated with a high posterior probability than in areas associated with a low posterior probability. The algorithm keeps track of all the parameter values visited during this journey and passes this information back to the user.

Because this one particle moves sequentially, and you don’t know where it’s heading (it’s a random walk, after all!), there is no way to get a head start on future computations you will need to perform. This limitation may be tolerable for plain vanilla DSGE models, like the New York Fed’s, where each of these sequential computations takes a negligible amount of computing time. But, if you want to estimate a more complex monetary policy model where households are heterogeneous (like we do at times!), you may find yourself waiting for months (and that’s not fun).

SMC changes the game: instead of sending a single particle to explore the vast expanse of the posterior by itself, you send thousands, and let each particle travel a shorter distance. What’s the advantage? Each particle goes its own way, independently from the others (for the most part). This means that if you have many cores in your parallel computing system (we used the National Science Foundation-funded Extreme Science and Engineering Discovery Environment, or [XSEDE](https://www.xsede.org/) for short, and the Dallas Fed’s BigTex cluster), you can allocate each particle to a core and let them all work at the same time. Further, as each particle now travels a far shorter distance, what otherwise might take months can be done in just a few hours! (Note, since you have many more particles, the full posterior is still well-explored.) [*Divide et impera*](https://en.wikipedia.org/wiki/Divide_and_rule), as the Latins used to say. This approach has been around in the statistics literature for quite a while (covered by [Chopin](https://academic.oup.com/biomet/article-abstract/89/3/539/251804), among others), but was only recently applied to macroeconometrics (see, for example, [this paper](https://onlinelibrary.wiley.com/doi/abs/10.1002/jae.2397) by Herbst and Schorfheide, as well as [their book](https://books.google.com/books?hl=en&lr=&id=KGqYDwAAQBAJ&oi=fnd&pg=PA15&dq=Herbst+and+Schorfheide+&ots=_Ft1utL1be&sig=nnOe_4rt2xZMZ9gUANwBFe9kc7Y)).

The second disadvantage of Metropolis–Hastings algorithms is that whenever your data change, or your model is modified slightly, you need to start the estimation over from scratch. If you are in the business of forecasting, as some of us are (see, for example, the latest New York Fed DSGE Model [forecast](https://libertystreeteconomics.newyorkfed.org/2019/06/the-new-york-fed-dsge-model-forecastjune-2019.html), as well as an [assessment](https://www.sciencedirect.com/science/article/pii/S0169207018302012?via%3Dihub) of the model’s forecasting performance), this is annoying. Say you have estimated your model with data up to last quarter, and now you have a new quarter of data. As you might imagine, the bunch of particles obtained from the estimation three months ago will still provide a pretty good approximation for the posterior incorporating the newest quarter of data. SMC offers a way out: instead of starting the estimation over, you can simply initialize the old particles from where they left off, and let them travel for a little longer, so as to adapt to the new posterior. This short traveling should not take much time, and is definitely much faster than starting again! This is what we call “online” estimation of DSGE models.

Modifying the SMC algorithm so that you can start from an existing estimation is one innovation of our paper. The other is to make SMC “adaptive” in choosing the speed at which particles travel. Such calibration requires finesse: if your particles travel too fast, the estimation may go haywire; if they travel too slowly, you will waste time. So it is a step forward to be able to adapt the speed of particle movement to how hard a problem is. In this way, online and adaptive estimation naturally go hand-in-hand: when starting from a previous estimation, we can spend more time exploring the distribution when economic conditions are novel than when the data are similar to what the model has already seen. Our algorithm can recognize and handle such situations without any additional input from the user.

In keeping with a [tradition of posting our code](https://libertystreeteconomics.newyorkfed.org/2015/12/the-frbny-dsge-model-meets-julia.html), the New York Fed DSGE team is sharing the [SMC Julia package](https://github.com/FRBNY-DSGE/SMC.jl) on Github. Reader, take advantage of our code, and go estimate even harder models than you once dared!


> **How to cite this post:**

> Michael Cai, Edward Herbst, Marco Del Negro, Ethan Matlin, Reca Sarfati, and Frank Schorfheide, “Online Estimation of DSGE Models,” Federal Reserve Bank of New York *Liberty Street Economics*, August 21, 2019, https://libertystreeteconomics.newyorkfed.org/2019/08/online-estimation-of-dsge-models.html.

> **Disclaimer:**

> The views expressed in this post are those of the authors and do not necessarily reflect the position of the Federal Reserve Bank of New York or the Federal Reserve System. Any errors or omissions are the responsibility of the authors.