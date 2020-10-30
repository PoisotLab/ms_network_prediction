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

*Traits matching*: Functional traits can be used as a proxy for the inference of interactions because, well, ecological interactions require some kind of match between functional traits. However these data are lacking, especially for large scale analyses. 

*Phylogenetic inertia*: Because niche conservatism is a thing, the phylogenetic inertia of functional traits could help us infer the trait data that are missing. However, its efficacy could depend on the spatial scale of analysis since the phylogenetic signal present on a metaweb is lost on local webs.

*Network-based methods*: We can use latent traits of the species (i.e. unmeasured traits inferred from the known network) to predict missing interactions. However, these methods are sensitive to sampling biases and can only be used for species for which we have interaction data.

*The probabilistic approach*: We can combine local traits distributions, local abundances and Everything Else™ to infer the probability of interaction at a regional scale as a result of local observations.

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
