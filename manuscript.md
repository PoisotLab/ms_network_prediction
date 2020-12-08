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

# Interactions

**Box 2: Machine Learning Illustration**

## What is a species interaction?

Interactions between species can be manifested in a multitude of ways e.g. different 
types [@Jordano2016ChaEco], strengths, or symmetry and are not necessarily restricted 
between only a pair of species e.g indirect interactions [@Morales-Castilla2015InfBio]. The common thread 
between these multiple forms of interactions is that *at least* one of the species is 
affected by the interaction, this can be either positively or negatively [@Morales-Castilla2015InfBio]. Combine 
this high 'diversity' of interaction types with the sheer number of potential 
interactions that *could* occur in a community and it is understandable why attempting 
to sample species interaction empirically is a considerable task. However, inferring 
interactions through proxies such as traits, phylogenies, geographical data and other frameworks 
could prove to be promising [@Morales-Castilla2015InfBio]. This requires viewing (and constraining?) 
interaction networks in a variety of ways, such as using graphs or matrices.

In a graph, each species is represented as a node and each interaction as an edge
[@Delmas2018AnaEco, @Pascual2006EcoNet], thus the value/form an edge takes is a 
representation of the interaction. When using a matrix format we can construct them in 
such a way as to represent different interaction structures, namely bipartite 
networks where we have two interacting species guilds and have one guild be represented 
by rows and the other by columns e.g. hosts and parasites, k-partite networks which
can serve as a way to integrate various bipartite networks e.g. parasitoid webs, 
seed dispersal networks, and pollination networks [@Pocock2012RobRes],
or we can use unipartite networks where each species *appears* twice - 
both as a row and column species. For a presence/absence interaction network, the 
matrix is filled with 1 and 0 representing an interaction and an
absence of interaction respectively [@Dunne2006NetStr]. 

The representation of species interactions or interaction networks in the
form of graphs and matrices is quite effective for their description and analysis.
It allows the calculation of many network properties (particularly pertaining to structure), 
some of which can even be use to help the prediction of further interactions,
by for example applying a constraint on the possible number of links based on
the number of species present [@MacDonald2020RevLin].

 
## How do we predict how species that have never co-occurred will interact?

The probability of the realization of an ecological interaction depend on
co-occurrence in space and time, abundance and traits matching
[@Poisot2014SpeWhy; @Pichler2019MacLea]. Given two species that co-occur, a
neutral approach to probabilistic interactions would be based on abundances and
"neutralize" the effect of traits matching [@Canard2012EmeStr]. In this case we
can infer the probability of an interaction to occur by chance, just because two
species are abundant enough to bump into each other, and should be a good
parameter against which we could test other factors that limit the realization
of an interaction.   

However, some proxies can be used to make more accurate predictions of potential
ecological interactions. For instance, functional traits are good such proxies
because they are highly selected by ecological interactions and determine
forbidden links (such as the mechanical impossibility of a bird to consume seeds
larger than its beak). The fact that functional traits suffer some kind of
selective pressure and because niches tend to be conserved throughout a
phylogenetic tree, ecological interactions also tend to be conserved, and
therefore we could also use phylogenies to infer pairs of co-occurring species
that could potentially interact [@Gomez2010EcoInt]. In fact, the contribution of
interactions to the phylogenetic match between species is consistent even
through scales [@Poisot2018IntRet] and in neutral models [@Coelho2017NeuBio].  

A final family of methods that gained interest in recent years are the
network-based models. These models use the existing set of interactions to
identify the unmeasured traits (i.e. latent traits) driving the network
structure [@Becker2020PreWil]. Species positioned closely in the network should
interact with similar set of species [@Rossberg2006FooWeb; @Rohr2010ModFoo]. As
for functional traits, phylogenies can inform these models because these
unmeasured traits have evolved over time. [@Rossberg2006FooWeb;
@Elmasri2020HieBay]. These network-based models are unfortunatly sensitive to
sampling biases and limited to prediction for species for which we already have
interaction data [@Becker2020PreWil].

## What does interaction strength mean?

## How are interaction strengths actually inferred? 

## Can these predictions rely on hypergraphs and multi-layers networks?

Although network ecology often assumes that interactions go strictly from one
node to the other, the web of life is made up of a variety of interactions that
can vary over time and space; these interactions include facilitation, niche
construction, zoonoses, vector-borne diseases, among others
[@Garcia-Callejas2018MulInt], which all share the fact that interactions between
species are themselves interacting. One mathematical tool to describe these
situations is hypergraphs: hypergraphs are the generalization of a graph,
allowing a broad yet manageable approach to complex interactions
[@Carletti2020DynSys], allowing in particular interactions to occur beyond a
pair of nodes. @Golubski2011ModMod were among the first to show that interaction
modifiers are themselves interacting, which makes the complexity of ecological
networks explode. Investigating hypergraphical interactions can be more
important than previously thought, as they can reveal the importance of species
within a network based on *indirect* interactions [@Golubski2016EcoNet].

An additional degree of complexity is introduced by multi-layer networks
[@Hutchinson2019SeeFor]. Multi-layer networks offer links across "variants" of
the networks, which can include, timepoints, or environments. As such, these can
be particularly useful to account for the meta-community structure of ecological
networks [@Gross2020ModMod], or to understand how spatial dispersal graphs can
inform conservation actions [@Albert2017AppNet]. As @Pilosof2017MulNat suggest,
ecological networks intrinsically contain multi-layers, as they are shaped by
evolution, dispersal, environmental heterogeneity, among others. *Prima facie*,
increasing the dimensionality of the object we need to predict (the multiple
layers rather than a single network) may make the problem complicated. But
multi-layer networks encode ecological constraints -- of dispersal, of
evolution, and of niche suitability. One question that is worth investigating is
whether the multi-layer structure of ecological networks may *improve* the
predictibility of interactions. Indeed, this is the case for social networks
[@Jalili2017LinPre; @Najari2019LinPre; @Yasami2018NovMul]. In short, although
simple networks have captured a great deal of the complexity of interactions,
exploring more intricate ways in which species interact might require that we
make room for hypergraphs and multi-layer networks in our predictive framework.

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
