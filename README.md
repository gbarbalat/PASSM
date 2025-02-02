# PASSM
This tests the effect of a peer-support programme improving mental health awareness on medical registrars' well-being in a non-randomized controlled study.

# Research question and specific aims
P: In a population of medical registrars, what is the effect of  
E: exposure to peers trained in MHFA  
C: compared to a population that is not exposed  
O: on their well-being  
Study design: cohort prospective (12 months), comparing 1st to 2nd year medical registrars  

SA  
- Effect on well-being vs. depression
- HTE? (Sex, Medical Specialty)
- Has the exposed population reached out to the trainees?
- Which resources did they utilize?

# Analysis plan

_Variables_ that may explain the systematic differences between first and second years and influence well-being are important to consider, e.g. age, prior education and experience (including know-hows, self-confidence), stressors and well-being, relationships (second year may have developed better strategies for maintaining work-life balence), being involved in a mentorship prgm/support organization.  Other variables will be collected, such as previous mental and somatic hx, personal and family hx, and socio-demographic/economic characteristics.  Variables will be collected longitudinally, every 3 months for a year.

_Analysis_ will try and make use of the longitudinal design. One model will be run at each measurement (Month3, Month6, Month9, Month12). Month6, Month9, Month12 analyses will include multiple time points.  
In the main analysis, we will investigate the effect of exposure to trainees on well-being at every time point, including 3 time-dependent confounders (intermediate measures of well-being, stressors and help seeking). The main analysis will be performed with the _lmtp_ R package, using sequential doubly-robust (preferably to?) longitudinal tml estimator.   
In the causal mediation analysis, we will specifically test whether help seeking is a mediator of the relationship between exposure to trainees and well-being. In particular, the three variables that we will collect longitudinally will have a temporal relationship: the exposure is thought to influence all three factors. Yet, levels of stress is thought to influence help seeking behaviours, which itself is thought to influence well-being. Analysis will be performed with the _lcmmtp_ R package. Checks will be performed with the _medoutcon_ R package, which performs causal mediation in the same way (e.g. with doubly-robust estimators) with a single time point. Because of intermediate confounders, which impacts both the mediator and the outcome, we will investigate interventional rather than natural direct and indirect effects, bearing in mind that interventional effects have some limitations: they do not decompose the ATE, and the interventional indirect effect can be non-zero even when there are no paths of the type A -> M -> Y.  
We will let A be the exposure, Y the outcome, L the time-dependent confounders, M the mediator, and Z the intermediate confounders. Note that baseline covariates will also be included (measured at baseline) and denoted L1.  

using 
- https://github.com/nt-williams/lcm/tree/main/lcm/man
- https://github.com/nt-williams/lcmmtp/blob/main/README.md
- https://github.com/bjg345/lcmmtp_sim/blob/main/sim.R
- https://github.com/CI-NYC/lcmmtp-application/blob/main/scripts/0-functions.R
- https://github.com/nt-williams/medoutcon/blob/master/paper/paper.md (for single time-point mediator analysis)

Missing data will likely be a problem as we expect a high rate of non-response. We will try and minimize missing data with a research assistant. Missing data in the final database will be processed with multiple imputation (ideally using Multiple Imputation by SuperLearning) and inverse probability of attrition weighting. 

