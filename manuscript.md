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

- A predictive (supervised) ML model is trained on a dataset containing features
  and labels, generally split into a training and validation subset. The model
  learns to predict the labels from the training subset, then the fit is
  evaluated on the validation set. Depending on the type of model, the
  validation step is part of the training and the model will keep learning until
  it reaches a certain threshold based on the loss function.
- Fitting and adjusting the model can be done by adjusting the model parameters
  depending on the type of model (layer compositions and network structures for
  neural networks, number of trees and splits for tree-based models).
- Studies with ML models predicting interactions, but not network properties:
  species traits used to predict interactions and infer trait-matching rules
  (Desjardins-Proulx et al., 2017; Pichler et al., 2020), automated discovery of
  food webs (Bohan et al., 2011), reconstruction of ecological networks using
  next-generation sequencing data (Bohan et al., 2017), network inference from
  presence-absence data (Sander et al., 2017)
- Ref 1, ref 2: Christin et al., 2019

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

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
