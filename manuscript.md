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

## How can we validate a forecast?


Often the purpose of building a model to predict how a system will behave in the future is to inform _present_ action [@Dietze]. Yet, the nature of forecasting---trying to predict the future---is that you can only know if a forecast "works" once it is too late to change it. Therefore, we want to maximize the chance a forecasting model is right.

Methods for model validation can be applied to forecasting context.
Crossvalidation (see _How do we validate a predictive model?_) can be used for forecasting.
A model can iteratively be trained on data, adding time series

Hindcasting based on known observations.
However, these all rely on existing time-series of data, which is collected in
past conditions that may not persist into the future.



The future is uncertain. Any system we wish to forecast will undergo only one of many possible scenarios (see _Forecasting Box_), yet we can only observe the realized outcome of the system under the scenario that actually unfolds.
It is therefore impossible to assess the quality of a forecasting model in scenarios that remain hypothetical.
If the goal is to maximize the probability that reality will fall within the forecast's estimates, forecasts should incorporate as much uncertainty about the future scenario as possible.
One way to do this is _ensemble modeling_ which combines forecasts from  multiple different models.
However, as we increase the amount of uncertainty we incorporate into a forecasting model, the resolution of the forecast's predictions shrinks,
and therefore the modeler be mindful of the trade-off between resolution and accuracy in any forecasting model (see _Forecasting Box_).
A forecast inherently has a _resolution limit_ in space, time, and  organization.
For example, one could never hope to predict the precise abundance of every species on Earth on every day hundreds of years into the future.
However, a lower resolution forecast, like primary production will be at a maximum in the summer, is likely to be true. but at some point.



## What ecological knowledge would forecasting bring?

# References
