---
title: Tempered Particle Filter
summary: Julia implementation of self-tuning tempered particle filter from Herbst and Schorfheide (2017) for likelihood evaluation of non-linear models with non-Gaussian innovations. Code is integrated into the NY Fed's package of filtering and smoothing routines for state-space models, StateSpaceRoutines.jl.

tags:
- Bayesian Econometrics
- Simulation Methods
- State Space Models
- Time-Series Models

date: "2019-08-26T00:00:00Z"

image:
 caption: "Herbst, Edward and Schorfheide, Frank, ''Tempered Particle Filtering.'' *Journal of Econometrics*, vol. 210, no. 1, 2019, pp. 26-44., doi:10.1016/j.jeconom.2018.11.003."
 focal_point: ""
 preview_only: false

links:
- icon: github
  icon_pack: fab
  name: GitHub Repository
  url: "https://github.com/FRBNY-DSGE/StateSpaceRoutines.jl"
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""
---

The tempered particle filter is a particle filtering method which can approximate the log-likelihood value implied by a general (potentially non-linear) state space system (with potentially non-Gaussian innovations) of the following representation:

### General State Space System
```
s_{t+1} = Phi(s_t, eps_t)  (transition equation)
y_t     = Psi(s_t) + u_t   (measurement equation)

eps_t ~ F_{eps}( . ; 0)
u_t   ~ N(0, E)
Cov(eps_t, u_t) = 0
```

Notice above that unlike the Kalman filter, the tempered particle filter does not impose that one's model is linear and shocks `eps_t` are Gaussian.

Documentation and code are located in [src/filters/tempered_particle_filter](https://github.com/FRBNY-DSGE/StateSpaceRoutines.jl/tree/master/src/filters/tempered_particle_filter). An example script is located in [docs/examples/tempered_particle_filter](https://github.com/FRBNY-DSGE/StateSpaceRoutines.jl/tree/master/docs/examples/tempered_particle_filter).

### Installation and Versioning
`StateSpaceRoutines.jl` is a registered Julia package in the [general registry](https://github.com/JuliaRegistries/General), currently compatible with Julia `v1.0` and `v1.1`.  To install, open your Julia REPL, type `]` (enter Julia's package manager), and run

```
pkg> add StateSpaceRoutines
```