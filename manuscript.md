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

**General discussion of interaction strength inference method**
- Interaction strength can either be infered empirically or theoretically [@Berlow2004IntStr]. Theoretical inference can be more mechanistic or with the Lotka-Volterra framework.
- Theoretical methods which have already been done are for example based on foraging theory [@Petchey2008], more physical/functionnal theory [@Portalier2018, ]
- Over different approaches to infer interaction strength, body-size or predator-prey body-size ratios have largerly been used as a predictor [@]

**Method we suggest**
- I would suggest to go, in general, with the inference of energy fluxes since it can be done with relatively accessible data like body-sizes, metabolic rates and abundances [@Berlow2004IntStr. Barnes2018EneFlua], thus probably being the easiest framework to work with and integrate in this immense pipeline.
- Could it be based on how @Barnes2018EneFlua do it, but since I doubt we will have individual-based information, just start at the species-level? 
- At the same time, some variable like metabolic rates can vary dependin on the stage of life of a species?

Not sure I understand the ATN model from @Berlow2009: They mesure interaction strength of a species as the difference of biomass in that species when another species is removed?

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
