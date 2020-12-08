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

After we fit a model, we inevitably want to see how "good" it is. One of the context for validation is _model comparison_, where we aim to see which of a competing set of models provides the best explanation for a data set.
A naive initial approach is to simply compute the average error between
the model's prediction and the true data we have, and choose the model with the smallest error---however this approach inevitably results in _overfitting_.
One approach to avoid overfitting is using information criteria (e.g. AIC, BIC, MDL, the heavily maligned Bayes Factor), which are based around the heuristic that good models maximize the ratio of information provided by the model to the number of parameters it has.

However, when the intended use-case of a model is prediction, the relevant form of validation is _predictive accuracy_. _crossvalidation_ provides a better alternative for validating a model's predictive capacity. Crossvalidation methods divide the original dataset into two---one which is used to fit the model (called the _training_ set) and one used to validate its predictive accuracy on the data that is hasn't "seen" yet (called the _test_ set).
This procedure is often repeated for different subdivisions of the dataset. One powerful approach is Leave-one-out-crossvalidation (LOOCV), which considers each data points uniquely as a test set, enabling sensitivity analysis. However, these methods are typically limited by the ensuing computation time requirements.


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

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
