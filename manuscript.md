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

The next step in the predictive approach we put forward, starting with networks
prediction, then interactions, is to focus on species themselves. The species
present at a particular site who can interact form the species pool of the
network. A common approach in biogeography to predict whether a species will be
present or absent at specific sites is to use species distribution models (SDMs)
based on known occurrences and environmental conditions at these locations, such
as climate and land cover (abiotic filter) [@Guisan2005PreSpe,
@Elith2006NovMet]. Including interactions or co-occurrences in SDMs, therefore
the biotic filter, generally improves predictive performance [@Wisz2013RolBio]
(discussed in more details in the next section).

Several approaches have been proposed for multi-species predictions, as is
required for the species pool. Community assemblage at a particular site can be
predicted either by combining independent single-species SDMs (stacked-SDMs,
SSDMs) or by directly modelling the entire species assemblage and multiple
species at the same time (joint SDMs, JSDMs) [@Norberg2019ComEva]. Building on
the JSDM framework, hierarchical modeling of species communities was also
suggested [@Ovaskainen2017HowMak], and has the advantage of capturing processes
that structure communities. An interesting approach, put forward by
@Guisan2011SesNew with spatially explicit species assemblage modeling (SESAM),
is to constrain the SDM predictions using macro-ecological models. Properties
such as species richness can be used to constrain assemblage predictions from
stacked species distribution models [@DAmen2015UsiSpe]. Similarly, the next step
we envision here, in light of the framework we proposed earlier, is to constrain
distribution predictions using network properties. This would also build on
previous calls to adopt a probabilistic view: there have been calls for a
probabilistic species pool [@Karger2016DelPro], and more importantly including
interactions through Bayesian networks and propagating conditional dependencies
has generated better range predictions [@Staniczenko2017LinMac].
@Blanchet2020CooNot argue that this is more mathematically explicit about the
relation between species, thus avoiding some confusion between interactions and
co-occurrences, but that it is also technically challenging and requires prior
knowledge of the interactions. This could potentially be solved through our
framework of predicting networks first, interactions next, and finally species.

## How could predictions for individual species, such as those used by IPBES/IUCN, be improved by considering ecological interactions?

## What is the spatial scale suitable for the prediction of species interactions?

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
