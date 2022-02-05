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
