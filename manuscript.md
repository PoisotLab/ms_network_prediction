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

## How can we validate a forecasting model?


Often the purpose of building a forecasting model to inform _present_ action [@Dietze2018IteNea]. Yet, the nature of forecasting---trying to predict the future---is that you can only know if a forecast is "right" once it is too late to change it. If we want to maximize the chance that "reality" falls within a forecasting model's predictions, there are two directions to approach this problem: the first is to extend model validation techniques to a forecasting context, and the second is to attempt to maximize the amount of uncertainty in a model without compromising its resolution.

Crossvalidation (see _How do we validate a predictive model?_) can be used to test the efficacy of a forecasting model. Given a time-series of $N$ observations, a model can iteratively be trained on the first $n$ time-points of data, and the forecasting model's accuracy can be evaluated on the remaining time-points it hasn't "seen". This enables us to understand both how much temporal data is required for a model to be robust, and also enables us to explore the _forecasting horizon_ of a process.
Further, this approach can also be applied in the opposite temporal direction--- if we have reliable data from the past, "hindcasting" can also be used to test a forecast's accuracy.


However, these methods inevitably bump into a hard-limitation on what is feasible for a forecasting model. The future is uncertain.
Any empirical time-series we use to validate a model was collected in past conditions that may not persist into the future.
Any system we wish to forecast will undergo only one of many possible scenarios (see _Forecasting Box_), yet we can only observe the realized outcome of the system under the scenario that actually unfolds.
It is therefore impossible to assess the quality of a forecasting model in scenarios that remain hypothetical.
If the goal is to maximize the probability that reality will fall within the forecast's estimates, forecasts should incorporate as much uncertainty about the future scenario as possible.
One way to do this is _ensemble modeling_ which combines forecasts from  multiple different models.
However, as we increase the amount of uncertainty we incorporate into a forecasting model, the resolution of the forecast's predictions shrinks,
and therefore the modeler be mindful of the trade-off between resolution and accuracy in any forecasting model (see _Forecasting Box_).

A forecast inherently has a _resolution limit_ in space, time, and  organization.
For example, one could never hope to predict the precise abundance of every species on Earth on every day hundreds of years into the future.
There is often a trade-off between resolution and a forecasting horizon.
However, a lower resolution forecast, like primary production will be at a maximum in the summer, is likely to be true.

Further, the inherent limitations on the "forecastability" of ecological time-series  [@Pennekamp2019IntPre] (see _Forecasting box_)



## What ecological knowledge would forecasting bring?

# References
