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
*Whose interaction are you looking for?* The spatial scale of interactions vary with species behaviour, size, phenological characteristics, and also with phylogenetic resolution (whether we are investigating individual-based networks or food webs, for example). Having that in mind, we can think of “small scale” and “large scale” as a property relative to the overall system we are investigating.  
*Small scale, if time-specific.* Small scale would focus on interactions that occur at individual and population levels, and therefore are much more prone to variability. In this sense, the spatial scale of prediction would have to be sufficient to capture life-range variation (both in the environment and in the species pool). The downside is that it would probably require a lot of high quality training data. As we gain on precision, we would lose on generality.  
*Large scale, when phenology is irrelevant.* When investigating interactions between species and higher levels, the evolutionary timescale takes place. This means that population and individual variation “average out”, and now spatial scale can be large enough to capture steep environmental changes, extinctions and species turnover. The downside is that it would be cool only at large temporal scales too, as it would ignore ongoing population dynamics. As we gain on generality, we would lose on precision.  
[@Bartomeus2016ComFra; @Trojelsgaard2016EcoNeta]

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
