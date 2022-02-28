## Course objectives
1. understand causal problems as potential interventions, through the framework of potential outcomes and assignment mechanisms
2. understand the spectrum of designs for both randomized and non-randomized studies
3. identify the suitations for which non-randomized designs are most appropriate
4. understand and be able to apply methods for estimating causal effects, including propensity score techniques, instrucmental variables ("encouragement designs "), and regression discontinuity
5. focus will be on learning how to critically review research that claims to estimate causal effects with non-experimental data. students will also understand complications encountered in causal studies, including missing data, noncompliance, and hidden bias.

## C1-W1P1: Intro and Framework
GOAL: 
- define casual effects and "the effect of a cause" vs "the cause of an effect", potential outcomes, assignment mechanism
- define estimands, including average treatment effects and average treatment effects for the treated.

What do we mean by a causal effect:
- what is the effect of some treatment T on an outcome Y
  - effect of a cause rather than cause of an effect
Framework:
- Rubin Causl model:
  - help us be clear about the effects we are estimating
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
  - SUTVA: stable unit treatment value assumption
    - no interference干涉 between units: treatment assignment of one unit does not affect potential outcomes of another unit
    - only one version of each treatment 
  - assignment mechanism
    - process that determines which treatment each unit receives
    - randomized exeriments: known assignment mechanism
    - observational studies: have to posit an assignment mechianse
    
## C2-W1P2: Discussion of "The C word", and Randomized Experiments
GOAL:
- basics of randomized exepriments: unconfounded assignment mechanisms, efficacy and effectiveness trials, cluster-based designs, increases in power when pretest measure of outcome available (eg: for use to calculate gain scores)
- concepts of internal, external, and target validity

Causal framework
- units
- covariates
- potential outcomes
- treatment
- control
- key: causal effects are not a comparison of outcomes for different groups. It is a comparision of potential outcomes under two conditions for the SAME group

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
 
## C3-W2P1: Observational Studies and the Importance of Design
GOAL:
- careful selection of comparison units and data
- dangers of regression on unmatched samples and assumptions underlying regression adjustment in non experimental studies
- definition and intuition behind propensity scores

benefit of randomized experiments:
- yield treated and control groups that are balanced: have similar covariate distributions
- technically, the treatment assignment is unconfounded (depends only on observed covariates, not unobserved variables). in other words, there are no unmeasured confounders

non-experimental studies
- just obserbed waht "treatment" people do or don't get+
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
           - ideal: exact matches on all covariates
             - for each treated individual, would like a control with exactly the same values of all covariates
             - this might be fairly easy with 1 covariate, but what if we have lots of covariates
             - instead, use propensity scores as summary of all the covariates
               - estimated propensity score with a large set of covariates
               - improved covariate balance after matching 
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
  - propensity score(con't)
    - don't care much about predictive ability of model (eg, c-statistics)
    - don't care about collinearity of covariates of coefficients themselves: only need predicted probabilities
    - just care about whether it results in balanced matched samples
## C4-W2P2: Introduction to Propensity Scores
GOAL:
- The theory underlying propensity scores
- basic steps in a propensity score analysis
- basic of propensity score matching, weighting, and subclassification

example 1
- two-pronged strategy:
  - propensity score methods to deal as well as possible with observed characteristics
  - sensitivity analysis to consider how an unobserved confounder may change study conclusions
- variable selections: 
  - best: lay out a conceptual model describing the factors that likely influence treatment selection and outcomes, and have deep understanding of treatment selection process
    - including more: unconfoundness more likeling
    - but including too many can lead to higher variance and worse balance on truly important variables
  - instructor ideas:
    - in large samples, be generous in what you include
    - in small samples (~100), concentrate on variables beleived to be strongly related to the outcomes
    - most important to include: 
      - pre-treatment measures of the outcome
    - prioritize variables in categories
      - thoese you think are the strongest confounders
      - those that you aren't sure or think are moderate confounders
      - those that you think may be condounders but would be weak
    - don't include variables that may have been affected by treatment
      - also can't include variables perfectly predictive of treatment assignment
    - high-dimensional setting (interesting for my final project proposal)
## C5-W3P1: Implementation of matching and related methods
Goal:
- more details on propensity score and related methods
- diagnostics for comparison group designs
- recent advances in propensity score and related methods

*section: the bastics of matching, weighting and subclassification*

Context:
- non-experimental setting: can't randomize
  - treatment groups differ on pre-treatment characteristics that affect the outcome: confounding
  - assuming strong ignorablity: no unmeasured confounding, all units are eligible for both treatment levels
- need to adjust for measured confounders
  - ? don't want to use regression - extrapolaiton, reliance on correct model specification, limited number of covariates in model
- instead using "design-based" methods: propensity scores
  - goal: mimic randomized experiment by attaining covariate balance
  - probability of treatment given covariates
  - it is a balanceing score
    - conditional on PS, treatment is independent of covariates
  - it can be used for weighting, subclassifcation, matching or regression adjustment
weighting:
  - basic idea: compute the weights from PS ->  weights balance covariates -> estimate treatment effect using weighted regression
    - formula for weights depends on estimand:
      - ![pic](https://github.com/tinghe14/COURSE-2-Causal-in-Public-Health/blob/main/Plot%20in%20Study%20Notes/weight%20ATE%2C%20ATT.png)
        - alternative methods:
          - generalized boosted modeling propensity score (GBM), covariate balancing propensity score (CBPS), entropy balancing
    - comments:
      - pros: 
        - easy to use, tends to work well, well understood, many modern advances
        - easy to combine with other data structures and complications (such as complex survey data)
      - cons:
        - model dependent
        - extreme weights yield imprecision and bias
   - subclassification:
     - basic idea: create subclassess on PS -> balance within subclasses -> estimate effects within subclasses
     - create bins based on quantiles of PS (5 often used, but others should be tried, estimates ATT or ATE)
     - two ways to use subclasses:
       - estimate effect within each subclass, then combine
       - marginal mean weighting through stratification - compute weights based on subclass membership, then treat as PS weights
     - comments:
       - pros: easy to use and explain, robust to PS model specification
       - cons: may be worse at removing bias, subclassess may not be balanced and may be small
   - matching:
     - basic idea: find subset of units similar on propensity score, drop the rest -> groups are balanced -> estimate effect in matched sample
       - matching yields matching weights - typically 1 for retained and 0 for discarded
     - basic matching is 1:1 PS matching without replacement
     - however, it is highly customizable
       - with replacement
       - k:1 matching - more than one control unit can be matched to each treated unit
       - fixed/variable ratio matching
       - full matching - all units included
         - sample is divided into subclasses with 1 treated or 1 control
       - pro: easy to explain, robust to model misspecification, customizable, data reduction
       - con: slow with large dataset, discarding units can decrease precision

*section: diagnostics for matching and related methods*

assessing balance:
- balance: degree to which covariate distributions are similar between treatment groupos
  - ideally could do this on the full covariate distributions
    - but this generally hard, so instead look at one- or two- dimensional summaries
      - means of covariates, variances of covariances, means of interactions of two covariates
      - calculate as if comparing outcomes after each approach:
        - 1:1 matching, use matched samples
        - subclassification, aggregate across subclasses
        - weighting, use weights

*Section: complications and conclusions*

other data types:
- multi-category treatments
  - estimand becomes more specific
- continuous treatments
  - weighting method for continuous treatments based on conditional density of treatment given covariates
- missing data, etc
the main ideas:
- a design approach: select treatment and comparision units to be as similar as possible on observed baseline characteristics
- rather than simply "controlling for" covariates through regression adjustment, use weighting, matching or subclassficiation
- many methods exist within this broad category, pick the approach that gives you the best balance in that dataset
- propensity scores a key tool to achieve balance
- three primary ways to use propensity scores, weighting, subclassification, matching (+ full matching)
  - when do these methods work?
    - when you can get goodf covariate balance on a large set of potential confounders
      - generally don't work well if all you have are basic 
    - what can go wrong?
      - of course these methods can't solve everything
      - there still can be unobserved differences between groups
        - sensitivity analysis can be used, to assess robustness of results to an unobserved confounder
      - you may not get good covariance balance
        - necessary to check
        - data could be insufficient for the question of interest
          - there might not be enough overlap
        - this is a limitation of the data, not the method
benefits of using propensity score and related methods:
- clear separation of designs and analysis
- forces you to see the amount of overlap (balance) in the data - standard regression diagnostics won't show this

## C6-W3P2: Assessing sensitivity to an unobserved confounder
Goal:
- introduction to analyses of sensitvity to the assumption of ignorable treatment assignment (tests for hidden bias)
- the e-value, and related methods

Unobserved confounders:
- propensity score methods (as well as standard regression adjustment) rely on unconfoundness assumption
  - no unobserved confounders, no hidden bias
- of course this often not completedly satisfied
  - two questions
    - how much would an unobserved confounder matter?
    - how do we limit sensivity to an unobserved confounder?
the setting
- unobserved U also related to T and Y and it gives us the bias here because unobserved u is here, the observed relationship between t and y is not fully accurate = the value of UT and UY relatinship to adjust the TY relationship:
- ![U plot](https://github.com/tinghe14/COURSE-2-Causal-in-Public-Health/blob/main/Plot%20in%20Study%20Notes/U%20plot.png)
types of questions sensitvity analysis asks/answers:
- given a certain (range of)U, what is the bias of the T-Y effect?
- given that U, what would the true T-Y effect be?
- with what U would the T-Y effect go away? (statistically non-significant, zero point estimate)
- could there be a U that makes the T-Y effect go away?
  - the main idea:
     - change vague statements about potential for unobserved confounding into quantitative ones about how large the bias would have to be to change the results
  - main message for today:
    - lots of options and flavors (with different settings, assumptions)
    - depends on specific situation (data, main analysis)
    - depends on the question
 One classic example:
 - smoking and lung cancer: 
   -  Fisher had written saying he thought observed relationship between smoking and lung cancer due to some unobserved genetic factor that made people more susceptible to both 
   -  Cornfield's analysis changed his mind: that genetic factor would have to be more strongly related to smoking and to lung cancer that anything already observed 
      - Thus, if cigarette smokers have 9 times the risk of nonsmokers for developing lung cancer, and this is not because cigarette smoke is a causal agent, but only because cigarette smokers produce hormone X, then the proportion OF HORMONE X-producers among cigarette smokers must be at least 9 times greater than that of nonsmokers. If the relative prevalance of hormone X-producers is considerably less than ninefold, then hormone X can't account for the magnitude of the apparent effect
   - formally statement:
     - what if treatment assignment is not unconfounded given X, but is unconfounded given observed X and unobserved U?
       - 2 stage process:
         - deal as well as possible with observed X's (eg, propensity score methods)
         - then worry about senstivity to an unobserved U, after accounting for X

## C7-W4P1: Encouragement designs and instrumental variables in randomized experiments
Goal:
- Identifying "natural experiments" to use instrumental variables methods in non-experimental studies
- Assumptions underlying instrumental variables estimation
- Examples of instruments in practice

## C8-W4P2: Instrumental variables as a non-experimental study design
Goal:
- Introduction to concepts behind principal stratification
- Concepts for dealing with post-treatment variables, including connection to mediation analysis and censoring by death
