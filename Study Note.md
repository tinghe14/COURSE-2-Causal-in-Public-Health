## W1P1: Intro and Framework
GOAL: 
- define casual effects and "the effect of a cause" vs "the cause of an effect", potential outcomes, assignment mechanism
- define estimands, including average treatment effects and average treatment effects for the treated.
What do we mean by a causal effect:
- what is the effect of some treatment T on an outcome Y
  - effect of a cause rather than cause of an effect
Framework:
- Rubin Causl model:
  - help us be clear abotu the effects we are estimating
  - treatments (intervention and control)
  - units (the entities at a particular point in time)
  - potential outcomes
    - potential outcome under treatment <img src="https://render.githubusercontent.com/render/math?math=Y(T=1) = Y(1)">
    - potential outcome under control <img src="https://render.githubusercontent.com/render/math?math=Y(T=0) = Y(0)">
  - causal effects are comparisons of these potential outcomes among the same!! group of people
    - causal effect for unit/individual i: <img src="https://render.githubusercontent.com/render/math?math=Y_i(1) - Y_i(0)">
    - average causal effect: average of <img src="https://render.githubusercontent.com/render/math?math=Y_i(1) - Y_i(0)"> across individual
 - fundamental problem of causal
  - only observe <img src="https://render.githubusercontent.com/render/math?math=Y_i(1)"> or <img src="https://render.githubusercontent.com/render/math?math=Y_i(0)"> for each i
  - mathematical representation: <img src="https://render.githubusercontent.com/render/math?math=Y_i = T_iY_i(1) + (1-T_i)Y_i(0)">
  - casual inference as missing data problem
- 2 types of causal effects
  - can't estimate individual-level causal effects (we can estimate the close as we can but never estimate the individual level)
  - average treatment effect
    - <img src="https://render.githubusercontent.com/render/math?math=ATE = \frac{1}{N} \sum_{i=1}^{N} (Y_i(1) - Y_i(0))">
  - average treatment effect on the treated
    - <img src="https://render.githubusercontent.com/render/math?math=ATT = \frac{1}{N_t} \sum_{i=1}^{N_t} (Y_i(1) - Y_i(0) | T_i = 1)">
## W1P2: Discussion of "The C word", and Randomized Experiments
GOAL:
- basics of randomized exepriments: unconfounded assignment mechanisms, efficacy and effectiveness trials, cluster-based designs, increases in power when pretest measure of outcome available (eg: for use to calculate gain scores)
- concepts of internal, external, and target validity

## W2P1: Observational Studies and the Importance of Design
GOAL:
- careful selection of comparison units and data
- dangers of regression on unmatched samples and assumptions underlying regression adjustment in non experimental studies
- definition and intuition behind propensity scores

## W2P2: Introduction to Propensity Scores
GOAL:
- The theory underlying propensity scores
- basic steps in a propensity score analysis
- basic of propensity score matching, weighting, and subclassification

## W3P1: Implementation of matching and related methods

## W3P2: Assessing sensitivity to an unobserved confounder
