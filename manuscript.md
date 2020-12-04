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

Ecological interactions shape species distributions at both local and broad
spatial scales, and including them in SDM models generally improves predictive
performance [@Araujo2007ImpBio; @Wisz2013RolBio]. Categories of approaches to
account for interactions in SDM models include integrating pairwise
dependencies, using surrogates for biotic-interaction gradients, and hybridizing
SDMs with dynamic models [@Wisz2013RolBio]. Improving SDMs through
interactions is crucial for conservation, as nearly 30% of models in SDM studies
are used to assess population declines or landscape ability to support
populations [@Araujo2019StaDis]. International panels such as IPBES and IUCN
draw on these models to establish scientific consensus [@Araujo2019StaDis]. For
example, IUCN Red List assessments includes an evaluation of the extent of
occurrence of a species from known, inferred, and projected sites of occurrence
[@IUCNRedListTechnicalWorkingGroup2019MapSta], which can be improved through
SDMs [@Syfert2014UsiSpe]. 

While interactions improve SDM predictions for individual species, their
importance for conservation goes beyond the scope of just SDMs. Interactions are
fundamentally linked to conservation issues and are crucial to consider in
conservation assessments, which is increasingly recognized by conservation
organisations. According to IUCN, interactions represent an important gap and
challenge in the assessment of species vulnerability to climate change, a
"seldom considered, but important driver of climate change impact on species",
and their integration was identified as an important methodological advance to
come [@Foden2016IucSsc]. In addition, interactions were identifid as a key
element of the functional role of a species, which must be considered for the
evaluation of species recovery for the development of an IUCN Green List of
recovered species [@Akcakaya2018QuaSpe]. Similarly, IPBES recognized that models
performing scenario analyses and projecting regional biodiversity dynamics will
need to incorporate species interactions and community dynamics, which will
benefit global and regional IPBES assessments [@IPBES2016MetAss]. Moreover,
recent studies argue for a shift in focus from species to interaction networks
for biodiversity conservation to better protect species, ecosystem processes,
and ecosystem services [@Harvey2017BriEco]. Therefore, the framework we propose
here will improve predictions by refining networks and interactions prediction
in space, thus improving tools for conservation and biodiversity management.

## What is the spatial scale suitable for the prediction of species interactions?

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
