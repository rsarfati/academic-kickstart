---
title: Model Constructors
summary: Julia package to build custom model types for simulation and estimation exercises.

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

This package contains the building blocks of model objects, such as `Parameter`, `Observable`, `Setting`, and `State` types. You may define any custom model, so long as it has parameters. The model object is used in both [DSGE.jl](https://github.com/FRBNY-DSGE/DSGE.jl) and [SMC.jl](https://github.com/FRBNY-DSGE/SMC.jl).

See `/docs/examples` for scripts demonstrating how to construct a custom model, then use [SMC.jl](https://github.com/FRBNY-DSGE/SMC.jl) to estimate it with sequential Monte Carlo - an algorithm applicable for any type of model (so long as it has free parameters). Should you build a DSGE model, you can use [DSGE.jl](https://github.com/FRBNY-DSGE/DSGE.jl) to construct forecasts, shock decompositions, impulse responses, etc.

### Installation
`ModelConstructors.jl` is a registered Julia package in the [general registry](https://github.com/JuliaRegistries/General).  To install, open your Julia REPL, type `]` (enter Julia's package manager), and run

```
pkg> add ModelConstructors
```

### Versioning
`ModelConstructors.jl` is currently compatible with Julia `v0.7`, `v1.0`, and `v1.1`.
