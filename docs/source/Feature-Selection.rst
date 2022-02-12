.. toctree::
   :maxdepth: 10
   :caption: Contents:

*************************
Genetic Feature Selection
*************************

GeneticFeatureSelectionCV
=========================


Initialization
==============
|
|
Genes
-----
* ``search_space``: dict 
* ``pop_size``: int 


Evaluation
==========
|
|
FitnessFunction
---------------
* ``estimator``: BaseEstimator
* ``cv``: int
* ``scoring``: str


Selection
=========
|
|
RankSelection
-------------
* ``pct_survivors``: int, float


|
|
RouletteWheelSelection
----------------------
* ``pct_survivors``: int, float


|
|
SteadyStateSelection
--------------------
* ``elimination_ratio``: float [default=.3]


|
|
TournamentSelection
-------------------
* ``k``: int [default=2] 
* ``preserve_remainders``: bool [default=True]


|
|
StochasticUniversalSampling
---------------------------
* ``pct_survivors``: int, float


|
|
BoltzmannSelection
------------------
* ``pct_survivors``: float
* ``T0``: int, float
* ``a``: int, float



Mating
======
|
|
MatingFunction
--------------
* ``pop_ratio``: int, float [default=1]
* ``increst_prevention``: bool [default=True]


|
|
Reproduction
============
|
|
KPointCrossover
---------------
* ``k``: int
* ``c_pt``: int, str [default='random']


|
|
Mutation
========
|
|
BitStringMutation
-----------------
* ``epsilon``: float [default=.15]


|
|
ExchangeMutation
----------------
* ``epsilon``: float [default=.15]


|
|
ShiftMutation
-------------
* ``epsilon``: float [default=.15]


|
|
Environment
===========
|
|
AdaptiveReproduction
--------------------
* ``pop_cap``: int [default=None]


|
|
AdaptiveMutation
----------------
* ``a``: int, float [default=.2]


|
|
Elitism
-------
* ``pct``: int, float [default=.05]

