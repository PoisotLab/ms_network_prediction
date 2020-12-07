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

Interaction strength, unlike the qualitative presence/absence interaction, 
is the quantification of an interaction. It can be seen as its relative 
importance [@Heleno2014EcoNet] or the direct effect of one species on 
another over a period of time [@Wootten1997EstTes]. Interaction strength 
can be expressed by a multitude of different metrics, generally depending 
on the type of interaction, for example trophic interaction versus 
plant-pollinator interactions, and the study objectives 
[@Berlow2004IntStr, Wootten2005MeaInt] but the general measure is usually 
expressed as a frequency or biomass [@Heleno2014EcoNet] over a period of 
time. While interaction strength might take multiple forms, it can generally 
be divided into two main categories as suggested by @Berlow2004IntStr: it 
can either be seen as the strength of an individual species-to-species 
link or as the effect that the changes in one species has on the dynamic 
of other species or on the whole community. Despite the multiple 
possibilities, one recurring observation throughout many studies is 
that networks are often composed of many weak links and few strong 
links [@Berlow2004IntStr]. 

The additional layer of information brought by interaction strength to 
the underlying network topology is an important one. Indeed, knowing the 
distribution of interaction strength within a network informs on 
its stability [@Neutel2002StaReaa, @Ruiter1995EnePat], influences on 
the ecosystemic functions [@Duffy2002BioEco, @Montoya2003FooWeb] 
and our potential to improve on the development of multispecies models [@Wootten2005MeaInt]. 
Seeing interaction strength within a network as energy fluxes could also possibly 
lead to its integration within a the Biodiversity-Ecosystem Functioning (BEF) 
framekwork, which could in return further improve even our understanding of community 
dynamics and ecosystem functioning [@Barnes2018EneFlua]. 

It remains that the analysis of interaction strength from empirical estimation 
is highly prone to biases since networks quantifying interaction strength are usually 
lumped together, making it difficult to differentiate the strength in per-individual 
interactions from strength of a whole species interaction [@Wells2013SpeInt]. 
Empirical estimations of interaction strength are still crucial [@Novak2008EstNon], 
but are a hard task to do from natural communities [@Wootten1997EstTesa, @Sala2002ComDis, @Wootten2005MeaInt], 
espically due to the large number of species composing communities, the 
multiple paths species can affect one another, and the possibility that the 
interaction strength functions might not have a linear response [@Wootten2005MeaInt]. 
Furthermore, interaction strength is extremely variable and context dependant 
and can be influenced by indirect effects, density dependence, spatial and 
temporal variation, and community composition [@Wootten2005MeaInt]. Inferring 
interaction strengths is a key step in linking species interactions to broader ecosystem processes 
and has the possibility to be done with relatively easily accessible 
data such as body size, abundance, density and metabolic rates [@Berlow2004IntStr].

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
