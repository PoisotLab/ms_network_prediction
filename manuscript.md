# Meta

**BOX 1: Biological Examples**

## What is the paper about?

## Who would benefit from it?

## Why do we need to predict interactions between species?

## Why predict networks before interactions?

## What is currently limiting our ability to predict network structure?

## What is currently enabling our ability to predict network structure?

![TODO](figures/conceptual.png){#fig:conceptual}

# A primer on predictive (network) ecology

## What are the most important properties of networks to predict?

## What is the added value of using machine learning?

## How do we fit a predictive model?

## How do we validate a predictive model?

## How do we propagate uncertainty through a predictive model?

In order to predict networks across space, we need to combine multiple models---one which predicts what the species pool will be at a given location, and one to predict what interaction networks composed from this species pool are likely (see _conceptual figure_).
Both of these models contain uncertainty.
The Bayesian paradigm provides a convenient solution to this---if we have a chain of models where each model feeds into the next, we can sample from the posterior of the input models.
A different approach is _ensemble modeling_ which combines the predictions made be several models, where each model is predicting the same thing.


TO DO:
- Bayesian paradigm produces a posterior distribution as an output for each model. For each model in a chain, sample the inputs from the posterior of the input models.
- Ensemble modeling

Error propagation is an important step in the modeling of ecological systems, as it provides estimates of the uncertainty around predictions. More generally, error propagation describes the effect of the uncertainty of input variables on the uncertainty of output variables [@Draper1995AssPro; @Parysow2000EffApp]. @Benke2018ErrPro identifies two broad approaches to model error propagation: analytically using differential equations or stochastically using Monte-Carlo simulation methods. The second approach is based upon samples of probability distributions and is more readily applicable to our problem of predicting ecological networks across space using our proposed methodological workflow. Indeed, each model's inputs can be sampled from the outputs of the preceding ones. Errors induced by the spatial or temporal extrapolation of data also need to be taken into account when estimating the uncertainty of a model's output [@Peters2004StrEco].


## How do we determine what interaction networks are feasible?

# Interactions

**Box 2: Machine Learning Illustration**

## What is a species interaction?

## How do we predict how species that have never co-occurred will interact?

## What does interaction strength mean?

## How are interaction strengths actually inferred?

## Could we use hypergraphs and multi-layer networks to predict more interactions?

# Network predictions must have a spatial component

**Everything is connected figure**

## How much do networks vary over space?

## How do we predict what the species pool at a particular location is?

## How could predictions for individual species, such as those used by IPBES/IUCN, be improved by considering ecological interactions?

## What is the spatial scale suitable for the prediction of species interactions?

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
