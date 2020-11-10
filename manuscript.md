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

## Can these predictions rely on hypergraphs and multi-layers networks?

Although network ecology often assumes that interactions go strictly from one
node to the other, the web of life is made up of a variety of interactions that
can vary over time and space; these interactions include facilitation, niche
construction, zoonoses, vector-borne diseases, among others
[@Garcia-Callejas2018MulInt], which all share the fact that interactions between
species are themselves interacting. One mathematical tool to describe these
situations is hypergraphs: hypergraphs are the generalization of a graph,
allowing a broad yet manageable approach to complex interactions
[@Carletti2020DynSys], allowing in particular interactions to occur beyond a
pair of nodes. @Golubski2011ModMod were among the first to show that interaction
modifiers are themselves interacting, which makes the complexity of ecological
networks explode. Investigating hypergraphical interactions can be more
important than previously thought, as they can reveal the importance of species
within a network based on *indirect* interactions [@Golubski2016EcoNet].

An additional degree of complexity is introduced by multi-layer networks
[@Hutchinson2019SeeFor]. Multi-layer networks offer links across "variants" of
the networks, which can include, timepoints, or environments. As such, these can
be particularly useful to account for the meta-community structure of ecological
networks [@Gross2020ModMod], or to understand how spatial dispersal graphs can
inform conservation actions [@Albert2017AppNet]. As @Pilosof2017MulNat suggest,
ecological networks intrinsically contain multi-layers, as they are shaped by
evolution, dispersal, environmental heterogeneity, among others. *Prima facie*,
increasing the dimensionality of the object we need to predict (the multiple
layers rather than a single network) may make the problem complicated. But
multi-layer networks encode ecological constraints -- of dispersal, of
evolution, and of niche suitability. One question that is worth investigating is
whether the multi-layer structure of ecological networks may *improve* the
predictibility of interactions. Indeed, this is the case for social networks
[@Jalili2017LinPre; @Najari2019LinPre; @Yasami2018NovMul]. In short, although
simple networks have captured a great deal of the complexity of interactions,
exploring more intricate ways in which species interact might require that we
make room for hypergraphs and multi-layer networks in our predictive framework.

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
