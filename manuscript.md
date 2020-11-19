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

Subsequent to the prediction of interaction itself comes the prediction of interaction strength. Interaction strength, unlike the qualitative presence/absence interaction, is quantified. It can be seen as its relative importance [@Heleno2014EcoNet] or the direct effect of one species on another over time [@Wootten1997EstTes]. It can be measured by a multitude of different metrics, generally depending on the type of interaction, whether it is at the individual link level or the ecosystem level and the study objectives [@Berlow2004IntStr, Wootten2005MeaInt]. Nonetheless, it is frequently reported as a frequency of interaction or as a flux of biomass [@Heleno2014EcoNet]. One recurring observation throughout many studies is that networks are often composed of many weak links and few strong links [@Berlow2004IntStr]. Even though empirical estimation of interaction strength is crucial [@Novak2008EstNon], it remains a hard task from natural communities [@Wootten1997EstTesa, @Sala2002ComDis, @Wootton2005MeaInt]. Its inference is thus a key step, as the distribution of interaction strength within communities governs their stability [@Neutel2002StaReaa, @Ruiter1995EnePat] and also influence ecosystem functions [@Duffy2002BioEco, @Montoya2003FooWeb]. To do so, the framework provided by the interaction strength seen as an energy flow might be well suited for our pipeline because they can be derived from relatively easily accesible data like body size, abundance and metabolic rates [@Berlow2004IntStr]. It could also possibly allow an integration with the Biodiversity-Ecosystem Functioning (BEF) framework [@Barnes2018EneFlua].

**I would argue for a certain homogenization of interaction strength between different types of network (interaction) to make comparison/analysis easier. Relevant? How? **

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
