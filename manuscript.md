---
bibliography: [references.bib]
---

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

## What is the most important property of a network to predict?

Networks enclose a wealth of data that are explanatory for many types of
interactions and are informative for the understanding of a wide range of
ecological phenomena [@Delmas2018AnaEco]. This might make the task of network
structure prediction daunting, as the number of properties to predict can be
immense. Yet there are two arguments to justify focusing on a single property,
namely connectance (the proportion of the interaction matrix filled with
interactions). First, connectance is ecologically informative. It ties into
resilience to invasion [@Baiser2010ConDet; @Smith-Ramesh2016GloSyn], can
increase robustness to extinction in food webs [@Dunne2002NetStr], and decrease
it in mutualistic networks[@Vieira2015SimSto], and relate to stability
[@Landi2018ComSta]. Second, most (if not all) network properties co-vary with
connectance [*e.g.* @Poisot2014WheEco]. @Dunne2002FooStr emphasize that most
network properties respond to network size (species richness) and connectance.
Diversity estimates can provide good baselines [@Jenkins2013GloPat] for species
richness over space; furthermore, recent advances in predicting the connectance
from species richness alone [@MacDonald2020RevLin] allow to derive distributions
of network properties for a given species richness. As such, we argue that
predictions of connectance are most likely to be immediately useful, and easy to
formulate.

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

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
