---
bibliography: [references.bib]
---

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

For several decades, ecologists have aimed to understand how networks of
many interacting species persist through time. The diversity-stability
"paradox", first explored by May [@May1974StaCom], shows that under a
neutral set of assumptions, ecological networks should become decreasingly
stable as the number of species increases. However, in the natural world
we observe networks of interactions that consist of far more species than
May's model predicts [@Albouy2019MarFis].

As a result, understanding what aspects of the neutral assumptions of
May's model are incorrect has branched many investigations into the relationship between ecological network structure and persistence
[@Allesina2012StaCri]. These assumptions can be split into dynamical
assumptions and topological assumptions.

On the topological side, we know that ecological networks are not
structured randomly. Some properties, like connectance, are highly
predictable [@MacDonald2020RevLin]. Various generative models of food-webs
have been shown to fit empirical networks more effectively than random
models. These typically rely on _network embeddings_---where each node
(species) in the network is assigned a value in a latent space, and the
resulting network topology is generated stochastically based on properties
of the position of nodes in that latent space. Generative network models
have long used allometry as a single-dimensional latent space---naturally
we want to extend this to traits in general [@Allesina2008GenMod].

The second approach to understand stability is through _dynamics_.
Early models of community dynamics (Lotka-Volterra, MacArthurs
Consumer-Resource Model) rely on the assumption of linear interaction
effects. However, models of bioenergetic community dynamics have shown
promise in basing our understanding of dynamics in food-webs, where the
functional response of one species on another is grounded in the
understood relationship between allometry and metabolism
[@Delmas2017SimBio].

An additional consideration is the multidimensional nature of "stability"
and "feasibility" e.g resilience to environmental change vs extinctions
[@Dominguez-Garcia2019UnvDim] and how these different disturbances will
propagate along the various level of organisations within a network
[@Kefi2019AdvOur], as well as their effect over space such as considering
metacommunities and the affect of dispersal/linkages between them in 
dampening these effects e.g building on the work of @Gravel2016StaCom.


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

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
