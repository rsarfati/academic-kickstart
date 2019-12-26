---
title: Model Constructors
summary: A Julia package to build custom model types for estimation.

tags:
- Bayesian Econometrics
- State Space Models
- Time-Series Models

date: "2019-08-11T00:00:00Z"

# Optional external URL for project (replaces project detail page).
#external_link: "https://github.com/FRBNY-DSGE/ModelConstructors.jl"

links:
- icon: github
  icon_pack: fab
  name: GitHub Repository
  url: "https://github.com/FRBNY-DSGE/ModelConstructors.jl"
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""
---

[![Build Status](https://travis-ci.com/FRBNY-DSGE/ModelConstructors.jl.svg?branch=master)](https://travis-ci.com/FRBNY-DSGE/ModelConstructors.jl) [![](https://img.shields.io/badge/docs-latest-blue.svg)](https://frbny-dsge.github.io/ModelConstructors.jl/latest)

This package contains the building blocks of model objects, such as `Parameter`, `Observable`, `Setting`, and `State` types. You may define any custom model, so long as it has parameters. The model object is used in both [DSGE.jl](https://github.com/FRBNY-DSGE/DSGE.jl) and [SMC.jl](https://github.com/FRBNY-DSGE/SMC.jl).

See `/docs/examples` for examples of how to construct your custom model, then use [SMC.jl](https://github.com/FRBNY-DSGE/SMC.jl) to estimate it (available for any type of model) and [DSGE.jl](https://github.com/FRBNY-DSGE/DSGE.jl) to construct forecasts, shock decompositions, impulse responses, etc. (available for DSGE models).

## Installation
`ModelConstructors.jl` is a registered Julia package in the [`General`](https://github.com/JuliaRegistries/General) registry.  To install, open your Julia REPL, type `]` (enter package manager), and run

```julia
pkg> add ModelConstructors
```

## Versioning
`ModelConstructors.jl` is currently compatible with Julia `v0.7`, `v1.0`, and `v1.1`.
