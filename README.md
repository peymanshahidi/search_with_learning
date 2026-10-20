# search_with_learning

A McCall-style job search model with distribution learning, applied to ride-hailing (online taxi) drivers deciding which ride offers to accept.

This code is part of my ride-hailing project, [Driver Experience or Price Effect](https://www.dropbox.com/scl/fi/u0x5m3bslevs8ap4pmhzi/tapsi_draft_application2022.pdf?rlkey=rect5ux5efkm1wl2hzj898tq1&dl=0).

## What the notebook does

[`search_with_learning.ipynb`](search_with_learning.ipynb) has three parts:

1. **Belief updating (Kalman filter).** A driver starts with a prior on the mean of the wage-offer distribution and updates it after each offer. The notebook simulates how fast beliefs converge to the true mean for different measurement-noise levels, and plots convergence paths, half-life, and post-convergence noise.
2. **Search theory primitives.** Sets up and plots the wage-offer distributions (normal and lognormal) used in the search problem.
3. **Ride search with learning.** Combines the two: drivers move across areas with different offer distributions, solve for a reservation wage via a finite-horizon value function over the shift, accept or reject each offer, and update area-level beliefs as offers arrive. It plots reservation wages, beliefs, offers, and cumulative earnings over the shift.

## Running it

Requires Python with `numpy`, `pandas`, `scipy`, `matplotlib`, and `numba`. Figures are written next to the notebook.
Note: the notebook dates from 2020 and imports `numba.autojit`, which recent numba versions have removed; drop that import (it isn't used) to run on a current setup.
