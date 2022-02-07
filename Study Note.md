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

non-experimental studies
- main problem:
  - people in treatment and control groups likely systematically different in both observed and unobserved ways
    - treated and control individuals very different on lots of things (confounding)
      - overt/observed bias
      - hidden/unoberserved bias
        - main idea of propensity score and related methods: deal as well as possible with overt bias, then worry hidden bias
- difference
  - in an RCT we don't have to worry about bias, and so can be concerned with variance
    - similarly, we have internal validity and so might then also care about external validity
  - in a non-experimental study, internal validity bias likely the first order concern
- traditional non-experimental design options
  - stratification
    - put people into groups with same values of covariates
      - cons:
        - lots of variables to stratify on, limited sample size
  - regression analysis
    - dangers of regression adjustment on full samples
      - see the answer each time a model is run
      - when the treated and control groups have very different distributions of the confounders, can lead to bias if model misspecificied
      - regression is only 'trustworthy' if the treatment and comparison groups look similar on covariates
      - when is regression adjustment trustworthy?
        - if difference between groups not lagre(eg, <.1 or <0.2 standard deviations) regression work fine
        - and in fact, matching meethods (like propensity score) work best in conjuction with regression
          - we should use propensity score methods to ensure comparing similar individuals
  - graphical form
    - ![plot1](https://github.com/tinghe14/COURSE-2-Causal-in-Public-Health/blob/main/Plot%20in%20Study%20Notes/plot%201.png)
propensity score method
- attempt to replicate two features of randomized experiments
  - create groups that look only randomly different from one another at least on observed variables
  - don't use outcome when setting up the design
 - idea is to find treated and control indiviudals with similar covariate
  - increase balance
- propensity scores
  - def: probablity of receiving the treatment (T) given the covariates (x)
    - math:  <img src="https://render.githubusercontent.com/render/math?math=e_i = P(T_i =1 | x_i)">
    - two key features
      - balancing score: at each value of the propensity score, the distribution of observed covariates the same in the treated and control groups
        - difference in outcomes within groups with same/similar propebnsity scores gives unbiased estimate of treatment effect
      - non unmeasured confounders
        - if treatment assignment independent of potential outcomes given covariates, then also independent of potential outcomes given the propensity score
          - no unobserved confounders, no hidden bias. ignorable
            - can help make unconfoundedness assumption more realistic if think about it during data collection
            - can also do sensitivity analyses to assess how sensitive results are to violation of this assumption
            - math: ![plot 2](https://github.com/tinghe14/COURSE-2-Causal-in-Public-Health/blob/main/Plot%20in%20Study%20Notes/plot%202.png)
      - however, the theory does depend on knowing the true propensity score and of the covaraies having particular distributions
        - in practice, need to check that balancing property holds
        - central goal is to get balance
        - addtional requirement for causal inference:
          - common support
            - if someone has 0 probability of receiving one of the treatments, we have no way of learning what their outcomes would be under treatment, so can't learn about hteir causal effects
              - in practice, this examined by looking at common suppor/overlap of the propensity score distrbution
                - ![plot 3](https://github.com/tinghe14/COURSE-2-Causal-in-Public-Health/blob/main/Plot%20in%20Study%20Notes/plot%203.png)
           - different types of propensity scores of 'matching'
             - k to 1 nearest neigbhor matching
               - for each treated unit, select k controls with closest propensity scores
             - subclassification/ stratification
               - group individuals into groups with similar propensity score values
             - weighting adjustments
                - IPTW: inverse probability of exposure weights 
                  - weighting by the odds
           - what about just including the propensity score in the outcome model
             - common way but not good strategy
               - commonly used as predictor in regression using full sample
                 - if sample unbalanced on covariates, will be unbalanced on propensity score
             - best approach is to combine a propensity score approach with regression adjustment
               - use covariate twice 
                 - once in propensity score model and once in outcome model
                   - not double dipping since they are modeling different associations (with treatment vs with outcome)
## W2P2: Introduction to Propensity Scores
GOAL:
- The theory underlying propensity scores
- basic steps in a propensity score analysis
- basic of propensity score matching, weighting, and subclassification

## W3P1: Implementation of matching and related methods

## W3P2: Assessing sensitivity to an unobserved confounder
