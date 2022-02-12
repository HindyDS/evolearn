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
Genes
-----
* ``search_space``: dict 
  - Defines the search range of the algorithm. Where keys are parameter names (strings) and values are int, float or str. Represents search spaceover parameters of the provided  estimator.
  
* ``pop_size``: int 
  - Size of the initial population.


Evaluation
==========
|
FitnessFunction
---------------
* ``estimator``: BaseEstimator
  - A object of that type is instantiated for each search point. This object is assumed to implement the scikit-learn estimator api. Either estimator needs to provide a   ``score`` function, or ``scoring`` must be passed.
  
* ``cv``: int
  - cross-validation generator or an iterable, optional Determines the cross-validation splitting strategy.
        Possible inputs for cv are:
          - None, to use the default 3-fold cross validation,
          - integer, to specify the number of folds in a `(Stratified)KFold`,
          - An object to be used as a cross-validation generator.
          - An iterable yielding train, test splits.
        For integer/None inputs, if the estimator is a classifier and ``y`` is
        either binary or multiclass, :class:`StratifiedKFold` is used. In all
        other cases, :class:`KFold` is used.
  
* ``scoring``: str
  - 


Selection
=========
|
RankSelection
-------------
* ``pct_survivors``: int, float
  - 


|
RouletteWheelSelection
----------------------
* ``pct_survivors``: int, float
  - 


|
SteadyStateSelection
--------------------
* ``elimination_ratio``: float [default=.3]
  - 


|
TournamentSelection
-------------------
* ``k``: int [default=2] 
  - 
  
* ``preserve_remainders``: bool [default=True]
  - 


|
StochasticUniversalSampling
---------------------------
* ``pct_survivors``: int, float
  - 


|
BoltzmannSelection
------------------
* ``pct_survivors``: float
  - 
  
* ``T0``: int, float
  - 
  
* ``a``: int, float
  - 



Mating
======
|
MatingFunction
--------------
* ``pop_ratio``: int, float [default=1]
  - 
  
* ``increst_prevention``: bool [default=True]
  - 
  


|
Reproduction
============
|
KPointCrossover
---------------
* ``k``: int
  - 
  
* ``c_pt``: int, str [default='random']
  - 


|
Mutation
========
|
BitStringMutation
-----------------
* ``epsilon``: float [default=.15]
  - 


|
ExchangeMutation
----------------
* ``epsilon``: float [default=.15]
  - 
  

|
ShiftMutation
-------------
* ``epsilon``: float [default=.15]
  - 


|
Environment
===========
|
AdaptiveReproduction
--------------------
* ``pop_cap``: int [default=None]
  - 


|
AdaptiveMutation
----------------
* ``a``: int, float [default=.2]
  - 


|
Elitism
-------
* ``pct``: int, float [default=.05]
  - 

