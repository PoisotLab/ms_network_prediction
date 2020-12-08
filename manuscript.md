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

## What is the most important property of a network to predict?

Networks enclose a wealth of data that are explanatory for many types of
interactions and are informative for the understanding of a wide range of
ecological phenomena [@Delmas2018AnaEco]. This might make the task of network
structure prediction look daunting, as the number of properties to predict can
be immense. Yet there are two arguments to justify focusing on a single
property, namely connectance, the proportion of the interaction matrix filled
with interactions. First, connectance is ecologically informative. It ties into
resilience to invasion [@Baiser2010ConDet; @Smith-Ramesh2016GloSyn], can
increase robustness to extinction in food webs [@Dunne2002NetStr], and decrease
it in mutualistic networks[@Vieira2015SimSto], and relate to stability
[@Landi2018ComSta]. Second, most (if not all) network properties co-vary with
connectance [*e.g.* @Poisot2014WheEco]. @Dunne2002FooStr emphasize that most
network properties respond to network size (species richness) and connectance.
Diversity estimates can provide good baselines [@Jenkins2013GloPat] for species
richness over space; furthermore, recent advances in predicting the connectance
from species richness alone [@MacDonald2020RevLin] allow to derive distributions
of network properties for a given species richness. Connectance is defined as
$L/S^2$ in unipartite networks, and $L/(S_1\times S_2)$ in bipartite networks,
and therefore can be measured from the number of links and the species richness
only -- because it can be derived from coarse data and is informative on both
the ecology and structure of the network, we argue that predictions of
connectance are most likely to be immediately useful, and easy to formulate.

## What is the added value of using machine learning?

Many ecological and evolutionary processes underlie species interactions 
and the structure of their ecological networks [e.g. @Vazquez2009UniPat; @Segar2020RolEvo]. 
It can thus be difficult to choose relevant variables and model species 
interactions networks explicitly. Machine learning methods are particularly 
useful in predicting ecological networks as they can uncover hidden and 
complex relationships from vast amount of ecological data. Machine learning, 
including deep learning, encompasses a broad variety of techniques applied 
with or without human supervision. These techniques are typically more 
flexible and performant than standard statistical methods, and can achieve 
a very high level of accuracy in predictive and classification tasks in a 
relatively short amount of time [e.g. @Cutler2007RanFor; @Krizhevsky2017ImaCla]. 
Machine learning is emerging as the new standard in computational ecology in 
general [@Olden2008MacLea; @Christin2019AppDee], and in network ecology in 
particular [@Bohan2017NexGlo], as long as sufficient relevant data is available.

A promising application of machine learning in natural sciences is Scientific 
Machine Learning (SciML), a novel and very powerful predictive method that 
combines machine learning with mechanistic models [@Chuang2018AdvCon; @Rackauckas2020UniDif]. 
SciML may require smaller amounts of data than more traditional machine learning 
methods, in addition to being more interpretable than the black box of machine 
learning. Although SciML has not yet been applied in ecology, we believe it 
could prove very useful in the near future to predict ecological networks 
with relatively small amounts of data using existing process-based models.

## How do we fit a predictive model?

In machine learning, a predictive (supervised) model is trained on a dataset
containing an outcome variable which we want to predict (also called label,
response, or dependent variable) and predictor variables (also called features,
descriptors, or independent variables) which will be used for
prediction[@Kuhn2013AppPre; @KuhnTidMod]. Before fitting the model, the dataset
will generally be split into a training and validation subset. The model learns
to predict the outcome from the training subset, then the fit and model
performance are evaluated on the validation set [@Christin2020GoiFur]. Depending
on the type of model, the validation step is part of the training and the model
will keep learning until it reaches a certain threshold based on the loss
function. Fitting and adjusting the model can be done by adjusting the model
parameters depending on the type of model (layer compositions and network
structures for neural networks, number of trees and splits for tree-based
models).

Another important step in predictive modeling is feature engineering, i.e.
adjusting and reworking the predictors to enable models to better uncover
predictor-response relationships [@Kuhn2019FeaEng]. For instance, this can
include projecting the predictors into a principal component analysis space, and
selecting only a dimensions for the modeling, as in our machine learning
illustration. The modeling process can have a few more steps, some which worth
mentioning include: exploratory data analysis, model tuning and selection, and
model evaluation [@KuhnTidMod]. Model validation will be discussed in the next
section.

Many studies have used machine learning models specifically with ecological
interactions. Relevant examples include species traits used to predict
interactions and infer trait-matching rules [@Desjardins-Proulx2017EcoInt;
@Pichler2020MacLea], automated discovery of food webs [@Bohan2011AutDis],
reconstruction of ecological networks using next-generation sequencing data
[@Bohan2017NexGlo], and network inference from presence-absence data
[@Sander2017EcoNet]. However, few studies have ever used predictive ML models on
network properties, such as connectance as mentioned earlier, rather than
interactions.

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
