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

Species interaction encompass every action occuring between any set
of two species (or more?) which can be declined into two main types: 
positive and negative interactions (also neutral?) [@Morales-Castilla2015InfBio].
As listed by [@Jordano2016ChaEco], these types of interaction may take many
forms, where positive interactions could for example be mutualism, 
commensalism and symbiosis and negative interactions be predation, herbivory
and parasitism.

Despite the multitude type/form of interactions,
network ecologists have primarily focused their research on food webs 
[@Morales-Castilla2015InfBio, @Dunne2006NetStr, ...] when considering 
interactions across a community or pairwise interactions such as plant-pollinator
and host-parasite interactions. Arguably the main reason for the bulk of research 
focusing on these subsets of interaction types may, in part, be due to the difficulty
in accurately describing or observing other types of interactions and may be underpinning
a scarcity of data. However, a *mechanistic* understanding of what determines if
and how species will interact can be leveraged when trying to predict interactions 
when data are incomplete or missing.

The representation of species interactions or interaction networks in the
form of graphs and matrices is quite effective for their description and analysis.
It allows the calculation of many network properties (do we list some?), which
some can even be use to help the prediction of further interactions,
by for example applying a constraint on the possible number of links based on
the number of species present [@MacDonald2020RevLin].

In a graph, each species is represented as a node and each interaction as an edge
[@Delmas2018AnaEco, @Pascual2006EcoNet], whereas two nodes linked by
and edge represents a species interaction. When the matrix format is used,
each row represents a consumer species and each column represents a 
ressource species. For a presence/absence interaction network, the 
matrix is filled with 1 and 0 representing an interaction and an
absence of interaction respectfully [@Dunne2006NetStr]. 
 
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
