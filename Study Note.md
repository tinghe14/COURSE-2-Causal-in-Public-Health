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
- important concepts for learning about causal effects
  - replication
    - need to have multi units
  - SUTBA: stable unit treatment value assumption
    - no interference干涉 between units: treatment assignment of one unit does not affect potential outcomes of another unit
    - only one version of each treatment 
  - assignment mechanism
    - process that determines which treatment each unit receives
    - randomized exeriments: known assignment mechanism
    - observational studies: have to posit an assignment mechianse
    
## W1P2: Discussion of "The C word", and Randomized Experiments
GOAL:
- basics of randomized exepriments: unconfounded assignment mechanisms, efficacy and effectiveness trials, cluster-based designs, increases in power when pretest measure of outcome available (eg: for use to calculate gain scores)
- concepts of internal, external, and target validity

Causal framework
- units
- covariates
- potential outcomes
- treatment
- control
- key: causal effects are not a comparison of outcomes for different groups. It is a comparision of potential outcoems under two conditions for the SAME group
Randomized experiments
- 3 key properties
  - treatment assignment is 'unconfounded'
    - mathmatical representation: <img src="https://render.githubusercontent.com/render/math?math=P(T|X, Y(O),Y(1)) = P(T|X)">
    - assignment does not depend on the potential outcomes
  - each unit has a positive proability of receiving each treatment
    - mathmatical representation: <img src="https://render.githubusercontent.com/render/math?math=0<P(T|X) <1 for all X">
  - study designed without use of the outcomes since they are not avaiable yet
- will provide an unbioased estimate of the "intent to treat" effect essentially the effect of being ranomized to treatment vs control
- also have complications
  - noncompliance 不合规
  - missing data
  - sometimes not balanced, especially with small sample sizes
  - interference between units (violation of SUTVA)
    - sometimes ameliorated(改善)through the use of cluster-or group-randomized designs
  - not always feasible or ethical
  - some fundamental problems with even very well-implemented RCT
    - are they really a gold standard
      - often do not enroll a representative sample of subjects
        - almost always have some implicit or explicit exclusion critiera 隐含的
        - how well you can generalize the results?
          - problems of scale-up
- questions is hard for RCT to answer
  - effects on long-term outcomes
  - effects in representative samples
  - effects of interventions we are not willing to withhold from some individuals
  - ...
Different trials of design
- efficacy
  - proof it can work in a strict groups but they don't necessary need to work at whole population
    - often carried out in lab or specificlized setting
    - criticized for not providing 'real-world' effects
    - but often a first step towards deciding if an intervention worth pursuing further
- effectiveness
  - test whether intervention are effective under 'real-world' conditions or in 'natural' settings
  - often large and expensive
- practical (pragmatic) clinical trials
  - very large-scale trials
  - if shows positive results, the intervention show a sign of 'really' works in usual practice
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
