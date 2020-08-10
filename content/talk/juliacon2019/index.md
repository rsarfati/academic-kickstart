---
title: Heterogeneous Agent DSGE Models in Julia at the NY Fed
event: JuliaCon 2019
event_url: https://juliacon.org/2019/

location: University of Maryland, Baltimore
address:
  street: 621 Lombard St
  city: Baltimore
  region: MD
  postcode: '21201'
  country: United States

#summary: ""#Discussion of heterogeneous agent modeling in Julia."
abstract: "This talk provides an overview of the Federal Reserve Bank of New York's heterogeneous agent dynamic stochastic general equilibrium (DSGE) model development process in the open-source computing language, Julia. Comparisons of performance relative to MATLAB and FORTRAN are provided."

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: "2019-07-24T14:30:00Z"
date_end: "2019-07-24T15:00:00Z"
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: "2019-07-24"

authors: []
tags: []

# Is this a featured talk? (true/false)
featured: true

image: 
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/bzdhc5b3Bxs)'
  focal_point: Right

links:
- icon: youtube
  icon_pack: fab
  name: Watch
  url: https://www.youtube.com/watch?v=Et-5AncK8TU
- name: Description
  url: https://pretalx.com/juliacon2019/talk/K9BBNX/

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
#- internal-project

# Enable math on this page?
math: true
---

### Overview:

Over the past few decades, income and wealth inequality have emerged as defining fixtures of the modern U.S. economy. Born of a desire to study the differential effects of policy decisions on a variegated group of economic actors, heterogeneous agent (HA) models enable researchers to incorporate critical differentiation in household income, wealth, and consumption behavior into their analyses of economic phenomena. Yet, while great academic progress has been made developing such models, many policy institutions have been slow to shift from the “representative agent” paradigm. This is due, in large part, to computational strain surrounding HA models' solution and estimation. However, thanks to speed gains made possible by innovations in computing languages like Julia, what was once too computationally taxing for policy purposes has become both feasible to run and elegant to implement. This talk provides an overview of the Federal Reserve Bank of New York's (NY Fed) HA dynamic stochastic general equilibrium (DSGE) model development process in Julia, walking through our navigation of Julia-specific functionality in the process. Comparisons of performance relative to MATLAB and FORTRAN are provided.

### Description: 

Heterogeneous agent models, in contrast to representative agent models, allow for heterogeneity in various features among agents in an economy, at both the household and firm level. Examples of such heterogeneity might include age, risk-tolerance, skill, and discounting of the future -- features that manifest themselves in heterogeneity in the wealth distribution. Recent work in macroeconomic literature reveals the monetary and fiscal policy implications for HA models may differ widely from their representative agent counterparts. Such models may be implemented in either discrete or continuous time, posing challenges for their intuitive out-of-the-box deployment, as well as succinct tailoring of model-specific solution methods. The solving of large-scale macroeconomic models is sufficiently complex in the representative agent case; the dimensionality of problems increases considerably with the addition of heterogeneity, especially in continuous-time, lending well to Julia’s strengths.

In the past year, our team has ported several HA models - along with algorithms to discretize, linearize, and solve them - from both MATLAB and FORTRAN for integration into our codebase. This addition comes at the heels of the release of our [DSGE.jl](https://github.com/FRBNY-DSGE/DSGE.jl) package, whose other components, such as representative agent model solution, estimation, and forecasting, were the subject of past presentations at JuliaCons 2016-2018. I discuss the respects Julia has provided us technical flexibility in constructing coherent type hierarchies, employing multiple dispatch, and utilizing distributed computing, as well as how we managed various design decisions pertaining to variable scope, typing, and parallelization, so as to optimize for memory usage and runtime. I cover the technical constraints and considerations imposed by our production environment at the NY Fed, and offer advice for what we found accommodated our cluster setup. Finally, I shed light on how HA models may expand the toolkit for policymakers and academics.

### Disclaimer: 

This talk reflects the experience of the author and does not represent an endorsement by the Federal Reserve Bank of New York or the Federal Reserve System of any particular product or service, The views expressed in this talk are those of the authors and do not necessarily reflect the position of the Federal Reserve Bank of New York or the Federal Reserve System. Any errors or omissions are the responsibility of the authors.