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

Interaction strength can either be infered/predicted empirically of theoretically [@Berlow2004IntStr]. While the development of theoretical predictive models to infer interaction strength is important, the empirical sampling of quantitative networks is although not to be neglected as they are important to model parameterization and validation [@Novak2008EstNon]. As for theoretical prediction and its integration into our pipeline, it has usually been done, but not limited to, three main theoretical frameworks with similar ideas and parameters that span over the different methods. The Lotka-Volterra framework is one of them and was used by [@Yodzis1992BodSiz] to predict consumer-resource dynamics and the transfer of energy between organisms. Another suitable framework is the functional foraging one as used by [@Portalier2019MecPre], where organisms traits related to the physical environment and foraging traits such as searching, capture and handling times were used to infer energy transfer from prey to predator. Finally, Allometric-Scalling uses organisms morphological traits such as body mass related to metabolism to infer energetic demands and biomasses to predict energy fluxes between organisms in a network [@Berlow2009SimPre].

Energy can be seen as the common currency that links every level of biology from individual organisms to the whole ecosystem [@Brown2004MetThe,@Barnes2018EneFlua]. Thus, predicting interaction strength as energy fluxes could potentially open the way to the conciliation of the different spheres of ecology. Preceded by the prediction of network topology itself, a bottom-up or top-down approach could either be used to quantitatively predict interaction strength using the relativaly easily accessible traits mention previously (or mention here? "such as body size, abundance, density and metabolic rates"). A bottom-up approach like the one used in [@Berlow2009SimPre] could be implemented, where the basal species biomasses are first infered and from there the higher trophic-level species biomasses and energetic demands would be computed. Otherwise, a top-down approach like the one used in [@Barnes2018EneFlua] could be implemetend, where energy fluxes are calculated starting from the top consumer to the bottom ones, based on species body-masses, metabolic rates and assimilation effeciencies. One flexible and useful characteristic of the 'Food web energetics' model used by [@Barnes2018] is that it can either incorporate individual-based data or more lumped data to the species level or trophic group depending on what is available for a specific network.

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
