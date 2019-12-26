---
title: Sequential Monte Carlo
summary: A Julia implementation of the sequential Monte Carlo algorithm for approximation of posterior distributions.

tags:
- Bayesian Econometrics
- Simulation Methods
- State Space Models
- Time-Series Models

date: "2019-08-26T00:00:00Z"

links:
- icon: github
  icon_pack: fab
  name: GitHub Repository
  url: "https://github.com/FRBNY-DSGE/SMC.jl"
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""
---

[![Build Status](https://travis-ci.com/FRBNY-DSGE/SMC.jl.svg?branch=master)](https://travis-ci.com/FRBNY-DSGE/SMC.jl) [![](https://img.shields.io/badge/docs-latest-blue.svg)](https://frbny-dsge.github.io/SMC.jl/latest)

This package implements the Sequential Monte Carlo (SMC) sampling algorithm, an alternative to Metropolis Hastings Markov Chain Monte Carlo sampling for approximating posterior distributions. The SMC algorithm implemented here is based upon Edward Herbst and Frank Schorfheide's paper "[Sequential Monte Carlo Sampling for DSGE Models](http://dx.doi.org/10.1002/jae.2397)" and the code accompanying their book, *Bayesian Estimation of DSGE Models*. More information and the original MATLAB scripts from which this code was derived can be found at Frank Schorfheide's [website](https://sites.sas.upenn.edu/schorf/pages/bayesian-estimation-dsge-models).

This implementation features what we term *generalized tempering* for "online" estimation, as outlined in our recent paper, "[Online Estimation of DSGE Models](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3426004)." For a broad overview of the algorithm, one may refer to the following *Liberty Street Economics* [article](https://libertystreeteconomics.newyorkfed.org/2019/08/online-estimation-of-dsge-models.html).

Comments and suggestions are welcome, and best submitted as either an issue or a pull request. :point_up:

## Installation and Versioning

`SMC.jl` is a registered Julia package in the [`General`](https://github.com/JuliaRegistries/General) registry, compatible with Julia `v0.7`, `v1.0`, and `v1.1`. To install it, open your Julia REPL, type `]` to enter the package manager, and run

```julia
pkg> add SMC
```

## Usage

The package requires our auxiliary package, [ModelConstructors.jl](https://github.com/FRBNY-DSGE/ModelConstructors.jl), which contains useful data structures for creating custom models (e.g. `Parameter`, `State`, `Observable`, `Setting` types).

For examples of how to set up a model in the form SMC can estimate, see scripts in the [`examples/`](https://github.com/FRBNY-DSGE/SMC.jl/tree/master/examples) folder.