Quick Start
===========

.. _installation:

Installation
------------

To use evolearn, first install it using pip:

.. code-block:: console

   (.venv) $ pip install evolearn

Genetic Optimization CV
----------------

To perform hyperparameter tuning using genetic algoritm,
you need to first import other modules from 

1) ``evolearn.optimization.initialization``
2) ``evolearn.optimization.evaluation``
3) ``evolearn.optimization.selection``
4) ``evolearn.optimization.mating``
5) ``evolearn.optimization.reproduction``
6) ``evolearn.optimization.mutation``
7) ``evolearn.optimization.environment`` (optional)
8) ``evolearn.optimization.genetic_optimization`` 

Although the modules from ``environment`` are optional for you to determine to
use them in your search or not, the searching might end up stopping early or not 
finding the ideal results. These modules can help to prevent pre-mature convergence
and also control other hyperparameters for GA.

For example:

>>> from evolearn.optimization.initialization import Genes
>>> from evolearn.optimization.evaluation import FitnessFunction
>>> from evolearn.optimization.selection import (RankSelection,
                                                RouletteWheelSelection,
                                                SteadyStateSelection,
                                                TournamentSelection,
                                                StochasticUniversalSampling,
                                                BoltzmannSelection
                                                )
>>> from evolearn.optimization.mating import MatingFunction
>>> from evolearn.optimization.reproduction import (KPointCrossover,
                                                   LinearCombinationCrossover,
                                                   FitnessProportionateAverage
                                                   )
>>> from evolearn.optimization.mutation import (Boundary,
                                               Shrink
                                               )
>>> from evolearn.optimization.environment import (AdaptiveReproduction,
                                                  AdaptiveMutation,
                                                  Elitism
                                                  )
>>> from evolearn.optimization.genetic_optimization import GenesSearchCV
>>> from sklearn.ensemble import RandomForestRegressor
>>> search_space_rf = {
              'max_depth':(1, 16, 'uniform'),
              'n_estimators':(100, 1000, 'uniform'),
              'criterion':('squared_error', 'absolute_error', 'poisson')
          }  
>>> opt = GenesSearchCV(
          n_gen=10,
          initialization_fn=Genes(search_space=search_space_rf, pop_size=30),
          fitness_fn=FitnessFunction(
              estimator=RandomForestRegressor(n_jobs=-1),
              cv=3,
              scoring='neg_mean_absolute_error',
          ),
          selection_fn=StochasticUniversalSampling(.7),
          mating_fn=MatingFunction(increst_prevention=False),
          reproduction_fn=KPointCrossover(1),
          mutation_fn=Shrink(),
          adaptive_population=AdaptiveReproduction(10),
          elitism=Elitism(),
          adaptive_mutation=AdaptiveMutation()
      )   
>>> opt.fit(X_train, y_train)
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:37: UserWarning: [18:27:13] Population Decline Warning: The current population size is smaller than previous. This might lead to premature convergence.
  warnings.warn(f'[{current_time}] Population Decline Warning: The current population size is smaller than previous. This might lead to premature convergence.')
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:27:38] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:27:58] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:28:39] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:29:06] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:29:39] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:30:09] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:30:37] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:31:03] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
C:\Users\Hindy\PycharmProjects\test123\lib\site-packages\evolearn\optimization\environment.py:118: UserWarning: [18:31:03] Elitism Failed Warning: Elites selected from this generation is 0. Number of elite is automatically set to 1. Please consider increase "pct".
  warnings.warn(
Max Fitness: -2023.200579609583
{'max_depth': 5, 'n_estimators': 561, 'criterion': 'absolute_error'}


The choices of ``selection_fn``, ``reproduction_fn``, ``mutation_fn`` are
actually up to your personal preference. One can pick what they believe
are most benefit to their searching preocess.


Genetic Feature Selection
-------------------------

To perform feature selection using genetic algoritm,
you need to first import other modules from 

1) ``evolearn.feature_selection.initialization``
2) ``evolearn.feature_selection.evaluation``
3) ``evolearn.feature_selection.selection``
4) ``evolearn.feature_selection.mating``
5) ``evolearn.feature_selection.reproduction``
6) ``evolearn.feature_selection.mutation``
7) ``evolearn.feature_selection.environment`` (optional)
8) ``evolearn.feature_selection.genetic_optimization`` 

The modules looks similar to those modules from the 
``GenesSearchCV`` section, but in fact their internal mechanisim 
work slightly differently. You need to be ware of importing the 
wrong modules when using genetic feature selection.

For example:

>>> from evolearn.feature_selection.initialization import Genes
>>> from evolearn.feature_selection.evaluation import FitnessFunction
>>> from evolearn.feature_selection.selection import (RankSelection,
                                                       RouletteWheelSelection,
                                                       SteadyStateSelection,
                                                       TournamentSelection,
                                                       StochasticUniversalSampling,
                                                       BoltzmannSelection
                                                       )
>>> from evolearn.feature_selection.mating import MatingFunction
>>> from evolearn.feature_selection.reproduction import KPointCrossover
>>> from evolearn.feature_selection.mutation import (BitStringMutation,
                                                    ExchangeMutation,
                                                    ShiftMutation
                                                    )
>>> from evolearn.feature_selection.environment import (AdaptiveReproduction,
                                                    AdaptiveMutation,
                                                    Elitism
                                                    )
>>> from evolearn.feature_selection.genetic_feature_selection import GeneticFeatureSelection
>>> from sklearn.ensemble import RandomForestRegressor
>>> opt = GeneticFeatureSelection(
       n_gen=10,
       initialization_fn=Genes(pop_size=50),
       fitness_fn=FitnessFunction(
           estimator=RandomForestRegressor(n_jobs=-1),
           cv=3,
           scoring='neg_mean_absolute_error'
       ),
       selection_fn=RouletteWheelSelection(.7),
       mating_fn=MatingFunction(),
       reproduction_fn=KPointCrossover(k=4),
       mutation_fn=BitStringMutation(),
       adaptive_population=None,
       elitism=None,
       adaptive_mutation=None
   )
>>> opt.fit(X_train, y_train)
>>> print(opt.best_fitness_)
>>> print(opt.best_params_)
-2797.7245589631652
{'age': True, 'sex': False, 'bmi': True, 'children': True, 'smoker': True, 'region': False}