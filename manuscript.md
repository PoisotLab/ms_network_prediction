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

Networks can vary either in their structural properties (e.g. changes in connectance or degree distribution) or in their composition (e.g. changes in nodes and links identity). Interestingly, variation in the structural properties of ecological networks tend to respond mostly to changes in the size of the network. First, the number of links in ecological networks scales with the number of species [@MacDonald2020RevLin; @Brose2004UniSpa]. Second, connectance and size are driving the rest of the structural properties of ecological networks [@Poisot2014WheEco; @Dunne2002FooStr; @Riede2010ScaFoo]. So, network properties do vary in space, but this variation is mainly explained by the spatial variation in species richness.

On a lower level, species turnover in space obviously results in changes in the composition of ecological networks. But, this is not the only reason networks composition varies [@Poisot2015BeySpe]. Intraspecific variations can result in interaction turnovers without changes in species composition [ADD REF]. Similarly, changes in species abundances can lead to variation in interactions [ADD REF].


Finding generalities in network structures have been central in ecological network theory [@Dunne2006TheNet]. One interesting fact about ecological network is how most of its structural properties can be predicted using species richness. On the one part, the number of links in ecological networks tends to scale with the number of species either following a beta-binomial model or a power-law [@Macdonald2020RevTeh, @Brose2004UniSpa]. Meaning that the connectance of a model can usually be predicted solely from the number of species. On the other hand, connectance is degree distribution (i.e. how interactions are distributed across species). This means that network structure tends to vary 

**P2** 
Variation in interaction networks over space arises through changes in species composition and realised interactions [@Poisot2012TheDis].

"These changes are the results of local processes" [@Poisot2015BeySpe]
How network structure may change on macroecological scale [@Baiser2019EcoRul]
Some empirical studies [@Baiser2012GeoVar, @Cirtwill2015LatGra]


**P1** 
A lot of early ecological network research have focused on finding generalities in network structure across systems [@Dunne2006TheNet].

Species Richness -> Connectance -> Everything else! [@Macdonald2020RevThe, @Brose2004UniSpa]
Species role are conserved over spatial scale [@Baker2015SpeRol]
Functional role composition did not change across space [@Dehling2020SimCom]
Food webs shared a common structural backbone [@Mora2018IdeCom]

## How do we predict what the species pool at a particular location is?

## How could predictions for individual species, such as those used by IPBES/IUCN, be improved by considering ecological interactions?

## What is the spatial scale suitable for the prediction of species interactions?

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
