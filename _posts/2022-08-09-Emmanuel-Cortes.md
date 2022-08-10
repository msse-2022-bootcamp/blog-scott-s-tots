---
layout: post
title: "Molecular Simulations: Cutoffs and Periodic Boundaries"
author: Emmanuel Cortes
---
## Cutoffs
Cutoff distances are utilized extensively by molecular simulations to reduce the amount of calculations required. Cutoffs are based on the heuristic that particles afar from one another produce negligible forces. However, given cutoffs are a heuristic device, the method might ignore anomalies or potentially significant interactions.


If we have a system of 10 particles, then there will be 45 pairwise particle-particle interactions to consider. We know this since the number of interactions for a N particle system is `N choose 2`. Thus, for 100 particle system, there will have 4950 interactions. And for 1000 interactions, there will be 499500 interactions. As you can see, the number of interactions increases quite drastically and thus the need for cutoffs in simulations.

| # particles | # pairwise interactions |
|---|---|
|10|45|
|100|4950|
|1000|499500|

Given a system with a density of 1, then in the table we can see the number of particles in spheres with varying radii.

| radius (unit) | # particles in sphere |
|---|---|
|1|1|
|2|8|
|5|125|
|10|1000|


## Periodic Boundaries
To model large bulk systems, periodic boundaries conditions are used which entails creating a (2D or 3D) lattice of small (2D or 3D) unit cells. 

There are two important implications when working in 3D system. 
1. When a particle exits from one edge, an identical particle enters from the opposite edge.
2. You should use utilize the the minimum distance when evaluating LJ potentials.

Given the two implications, we can determine that the maximum distance any particle can be from another in each dimension will have to be `l/2` where `l` is the length of the unit cell.

Thus, the actual interaction distance between a particle at `(0, 0, 0)` and another at `(0, 0, 8)` is not `8` but `2` since there is an identical particle (to `(0, 0, 8)`) at `(0, 0, -2)` 
