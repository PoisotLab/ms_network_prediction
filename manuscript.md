---
bibliography: [references.bib]
---

# Introduction

Ecosystems are composed of interactions---individual organisms interact 
with one-another either directly or indirectly through their shared 
environment. These interactions form complex networks that drive ecological 
and evolutionary dynamics and maintain ecosystem diversity and functioning 
[@Delmas2018AnaEco; @Landi2018ComSta; @Albrecht2018PlaAni].
Yet, knowledge of species interactions is one of the most severe contemporary 
shortfalls of knowledge in biodiversity science [@Hortal2015SevSho], primarily 
due to the tedious, time-consuming, and expensive nature of the data 
collection process.
As with many ecological systems, ecological networks have entered their 
"long now" [@Carpenter2002EcoFut], where contemporary actions will have 
long-term, low-predictability consequences,
sometimes over centuries [@Burkle2013PlaInt]. It is therefore imperative 
to develop a roadmap that would enable the prediction (for the present) 
and forecasting (for the future) of the structure of ecological networks 
[@McCann2007ProBio; @Seibold2018NecMul],
of the processes they encode [@Thompson2012FooWeb], and that can account 
for their spatial, temporal, and climatic dimensions [@Burkle2011FutPla].
In this paper, we adopt a question-driven approach to identify opportunities 
within this research agenda, and suggest a "roadmap" forward moving towards 
the prediction of species interactions across space and time.

## What is a species interaction network?

- *Box 1: What is a species interaction network?*
- Definitions
  - Species Interaction
  - Species Interaction Strength
  - Species Interaction Network
- _Example 1: Plant-Pollinator_
- _Example 2: Zoonotic Disease Spillover_


## Why should we predict species interaction networks?

Networks of species interactions underpin our understanding of key ecological 
processes [@Pascual2006EcoNet; @Heleno2014EcoNet]. Although they were initially 
used to describe the interactions *within* a community, interest in the last 
decade has shifted towards understanding their structure and variation over space 
[@Trojelsgaard2016EcoNet; @Baiser2019EcoRul], and has established network ecology 
as an important emerging component of biogeography and macroecology. 
Developing a unified methodology for prediction of the structure of ecological 
networks and the interactions that compose them would help unify the fields 
of community, network, and ecosystem ecology, improve the quantification of 
functional relationships of species [@Dehling2018BriThe; @O’Connor2020UnvThe], 
re-evaluate metacommunities in light of network structure [@Guzman2018TowMul], 
and enable a new line of research into the biogeography of species interactions
 [@Massol2017IslBio;Braga2019SpaAna] that incorporates both the Eltonian and 
 Grinnial niche [@Gravel2019BriElt].
Further, the ability to reliably predict and forecast species interactions 
would improve our understanding of how species function within ecosystems and 
inform conservation efforts for protecting species, communities and ecosystems.

## Who would benefit from better prediction of species interaction networks?

Reliable predictions for biodiversity change are increasingly sought after 
in international conservation programs (e.g. IPBES and GEO BON), and 
predictions that incorporate species interactions could substantially improve 
these assessments. International panels draw on these models to establish 
scientific consensus [@Araujo2019StaDis]. For example, IUCN Red List 
assessments includes an evaluation of a species from known, inferred, and 
projected sites of occurrence [@IUCNRedListTechnicalWorkingGroup2019MapSta], 
which can be improved through more effective forecasts of species 
distributions and interactions [@Syfert2014UsiSpe].

Interactions are fundamentally linked to conservation issues and are 
crucial to consider in conservation assessments.
According to IUCN, interactions represent an important gap and challenge 
in the assessment of species vulnerability to climate change, a 
"seldom considered, but important driver of climate change impact on 
species", and their integration was identified as an important methodological 
advance to come [@Foden2016IucSsc]. In addition, interactions were identified 
as a key element of the functional role of a species, which must be 
considered for the evaluation of species recovery for the development 
of an IUCN Green List of recovered species [@Akcakaya2018QuaSpe]. 
Similarly, IPBES recognized that models performing scenario analyses 
and projecting regional biodiversity dynamics will need to incorporate 
species interactions and community dynamics, which will benefit global 
and regional IPBES assessments [@IPBES2016MetAss]. Moreover, recent 
studies argue for a shift in focus from species to interaction networks 
for biodiversity conservation to better protect species, ecosystem 
processes,and ecosystem services [@Harvey2017BriEco]. Therefore, the 
framework we propose here will improve predictions by refining networks 
and interactions prediction in space, thus improving tools for conservation 
and biodiversity management.

## What is currently limiting our understanding of species interaction networks?

### Data

At the moment, our understanding of the structure of ecological networks is limited 
by the availability of data. Although we have seen a growth in species occurrences 
data, this growth is much slower for ecological interactions because species 
interactions are challenging to sample comprehensively [@Bennett2019PotPit; @Jordano2016SamNet]  
and sampling methodology matters [@deAguiar2019RevBia].
In turn, the difficulty of sampling interactions can lead to biases in our 
understanding of network structure [@deAguiar2019RevBia]. This knowledge gap has 
motivated a variety of approaches to deal with interactions in ecological research 
based on assumptions that do not always hold, such as the correlation between 
co-occurrence and meaningful interaction strength, when it is known that co-occurrence 
is the only prerequisite for an interaction to occur [@Blanchet2020CooNot].
Spatial biases in data coverage are
prevalent at the global scale (with South America, Africa and Asia being under-represented) 
and different interaction types show biases towards different biomes (or environmental conditions) 
[@Poisot2020EnvBia]. These 'spatial gaps' serve as a limitation to our ability to 
confidently make predictions when accounting for real-world environmental conditions, 
especially in environments for which there are no analogous data.

### Methods

This scarcity of data limits the range of computational tools than can be used 
by network ecologists. Most deep learning methods, for instance, are very data 
expensive.
The paucity of data is compounded by a collection of biases that can be found 
in existing datasets. Species interaction datasets are typically dominated by 
food webs, pollination, and host-parasite networks [@Ings2009EcoNet; @Poisot2020EnvBia]. 
This could prove to be a limiting factor when trying to understand or predict 
networks of *under represented* interaction types or trying to integrate networks 
of different types [@Fontaine2011EcoEvo], especially given the structural 
variation of ecological networks [@Michalska-Smith2019TelEco]. This stresses 
the need for an integrated, flexible, and data-efficient set of computational 
tools which will allow us to predict ecological networks accurately from 
existing and imperfect datasets.  

### Scale

We are also currently limited by the the level of biological organisation 
at which we can describe ecological networks. For instance, our understanding 
of individual based networks [see for example @Araujo2008NetAna; @Tinker2012StrMec] 
is still in its infancy [@Guimaraes2020StrEco] and acts as a resolution-limit 
at which we would be able to predict networks. On the note of scale, the 
resolution of environmental (or landscape) data would also limit our ability 
to predict networks at finer scales, although current trends in e.g. remote 
sensing would suggest that with time this would become less of a hindrance [@Makiola2020KeyQue].

Ecosystems are a quintessential complex-adaptive-system []. In 
figure +@fig:everything_is_connected, we see the myriad of ways in which 
processes at different spatial, temporal, and organizational scales influence 
and respond to one another. 
Understanding how the product of these different processes drive the properties 
of ecosystems, especially at different scales, remains difficult and we should 
strive to work on methods that will integrate these different 'snapshots'.

![](figures/everything_connected_v2.png){#fig:everything_is_connected}


## What is paving the path towards understanding species interaction networks?

### Open Data

The acquisition of biodiversity and environmental data has tremendously increased 
over the past decades thanks to the rise of citizen science [@Dickinson2010CitSci] 
and of novel technology [@Stephenson2020TecAdv], including wireless sensors [@Porter2005WirSen], 
next-generation DNA sequencing [@Creer2016EcoSF], and remote sensing 
[@Skidmore2015AgrBio; @Lausch2016LinEar].
Open access databases, such as [GBIF](https://www.gbif.org/) (for biodiversity data), 
[NCBI](https://www.ncbi.nlm.nih.gov/) (for taxonomic and genomics data), 
[TreeBASE](https://www.treebase.org/treebase-web/home.html) (for phylogenetics data),
[CESTE](https://icestes.github.io/) [@Jeliazkov2020GloDat] (for metacommunity ecology 
and species traits data), and [WorldClim](https://www.worldclim.org/data/bioclim.html) 
(for bioclimatic data) contain millions of data points that can be integrated to monitor 
and model biodiversity at the global scale.
For species interactions data, at the moment [Mangal](https://mangal.io/#/) is the most 
comprehensive open database of published ecological networks [@Poisot2016ManMak], and 
[GloBI](https://www.globalbioticinteractions.org/about) is an extensive database of 
realized and potential species interactions [@Poelen2014GloBio].
Developing standard practices in data integration and quality control [@Kissling2018BuiEss] 
and in next-generation biomonitoring [NGB; @Makiola2020KeyQue] would improve our 
ability to make reliable predictions of ecosystem properties (e.g.) on increasing 
spatial and temporal scales. The advancement of prediction techniques coupled with a 
movement towards standardising data collection protocols (e.g. @Perez-Harguindeguy2013NewHan 
for plant functional traits) and metadata (e.g. [DarwinCore](https://www.tdwg.org)), 
which would facilitate interoperability and integration of datasets, as well as a growing 
interest at the government level [@Scholes2012BuiGlo] paints a positive picture for data 
usability in the coming years.


### Open Tools and Methods

Machine learning encompasses a broad variety of techniques applied with 
or without human supervision. These techniques can often be more flexible 
and perform better than classical statistical methods, and can achieve a 
very high level of accuracy in many predictive and classification tasks 
in a relatively short amount of time [e.g. @Cutler2007RanFor; @Krizhevsky2017ImaCla].
Increasing computing power combined with recent advances in machine learning 
techniques and applications shows promise in ecology and environmental science 
(see @Christin2019AppDee for an overview).
Moreover, ongoing developments in the field of artificial intelligence are aimed 
at using deep learning more efficiently in low-data regimes [e.g. @Antoniou2018DatAug] 
and with unbalanced datasets [@Chawla2010DatMin].

Machine learning is emerging as the new standard in computational ecology 
in general [@Olden2008MacLea; @Christin2019AppDee], and in network ecology 
in-particular [@Bohan2017NexGlo], as long as sufficient relevant data are 
available.
Many ecological and evolutionary processes underlie species interactions 
and the structure of their ecological networks [e.g. @Vazquez2009UniPat; @Segar2020RolEvo].
It can thus be difficult to choose relevant variables and model species 
interactions networks explicitly.
A promising application of machine learning in natural sciences is 
Scientific-Machine Learning (SciML), a framework that combines machine 
learning with mechanistic models [@Chuang2018AdvCon; @Rackauckas2020UniDif].
Although SciML has not yet been applied in ecology, it has the potential 
to combine mechanistic models with black box machine-learning to predict 
ecological networks with relatively small amounts of data using existing 
process-based models.
Considering the current biases in network ecology [@Poisot2020EnvBia] and 
the scarcity of data of species interactions, the prediction of ecological 
networks will undoubtedly benefit from these improvements.


### Conceptual Synthesis


If we wish to predict the interactions between species we have not observed 
together, using our knowledge of the structure of ecological networks to 
interact in a particular ecosystem is one of our most useful assets. We are 
able to infer species interactions using proxies such as traits, phylogenies, 
geographical data and other frameworks [@Morales-Castilla2015InfBio]. Drawing 
on elements that contribute to the realization of an interaction such as 
abundance and traits matching in space and time, and the combination of these 
elements allow us to infer potential from realized interactions and empirical 
data about populations
[@Poisot2016StrPro].

# A Roadmap Toward Prediction of Ecological Networks across Space and Time
 
Below we focus on and discuss integrating what we envisage to be the key areas
 towards conceptualising and predicting ecological networks (+@fig:conceptual). 
 With particular focus on taking a machine learning approach to the modelling 
 process, the relationship between species interactions and network structure, 
 and how we would incorporate this across space.

![](figures/conceptual.png){#fig:conceptual}

## Models

### How do we fit a predictive model?

In machine learning, a predictive (supervised) model is trained on a dataset 
containing an outcome variable which we want to predict (also called label, 
response, or dependent variable) and predictor variables (also called features, 
descriptors, or independent variables) which will be used for 
prediction[@Kuhn2013AppPre; @KuhnTidMod].
Before fitting the model, the dataset will generally be split into a training 
and validation subset.
The model learns to predict the outcome from the training subset, then the 
fit and model performance are evaluated on the validation set [@Christin2020GoiFur].
Depending son the type of model, the validation step is part of the training 
and the model will keep learning until it reaches a certain threshold based 
on the loss function.
Fitting and adjusting the model can be done by adjusting the model parameters 
depending on the type of model (layer compositions and network structures for 
neural networks, number of trees and splits for tree-based models).

Another important step in predictive modelling is feature engineering, i.e. 
adjusting and reworking the predictors to enable models to better uncover
predictor-response relationships [@Kuhn2019FeaEng]. For instance, this can
include projecting the predictors into a principal component analysis space, and
selecting only a dimensions for the modelling, as in our machine learning
illustration. The modelling process can have a few more steps, some which worth
mentioning include: exploratory data analysis, model tuning and selection, and
model evaluation [@KuhnTidMod]. Model validation will be discussed in the next
section.

Many studies have used machine learning models specifically with ecological
interactions. Relevant examples include species traits used to predict
interactions and infer trait-matching rules [@Desjardins-Proulx2017EcoInt;
@Pichler2020MacLea], automated discovery of food webs [@Bohan2011AutDis],
reconstruction of ecological networks using next-generation sequencing data
[@Bohan2017NexGlo], and network inference from presence-absence data
[@Sander2017EcoNet]. However, few studies have ever used predictive ML models 
on network properties or structure.

### How do we validate a predictive model?

After model fitting, we inevitably want to see how "good" it is. One 
of the context for validation is _model comparison_, where we aim to 
see which of a competing set of models provides the best explanation 
for a data set.
A naive initial approach is to simply compute the average error between
the model's prediction and the true data we have, and choose the model 
with the smallest error---however this approach inevitably results in _overfitting_.
One approach to avoid overfitting is using information criteria (*e.g.* 
AIC, BIC, MDL, the heavily maligned Bayes Factor), which are based around 
the heuristic that good models maximize the ratio of information provided 
by the model to the number of parameters it has.

However, when the intended use-case of a model is prediction, the relevant
 form of validation is _predictive accuracy_. _Crossvalidation_ provides a 
 better alternative for validating a model's predictive capacity. Crossvalidation 
 methods divide the original dataset into two---one which is used to fit the model 
 (called the _training_ set) and one used to validate its predictive accuracy on 
 the data that is hasn't "seen" yet (called the _test_ set).
This procedure is often repeated for different subdivisions of the dataset. One 
powerful approach is Leave-one-out-crossvalidation (LOOCV), which considers each 
data points uniquely as a test set, enabling sensitivity analysis. However, these 
methods are typically limited by the ensuing computation time requirements.


### How do we propagate uncertainty through a predictive model?

In order to predict networks across space, we need to combine multiple 
models---one which predicts what the species pool will be at a given 
location, and one to predict what interaction networks composed from 
this species pool are likely (see _conceptual figure_).
Both of these models contain uncertainty.
The Bayesian paradigm provides a convenient solution to this---if 
we have a chain of models where each model feeds into the next, we can 
sample from the posterior of the input models.
A different approach is _ensemble modeling_ which combines the predictions 
made be several models, where each model is predicting the same thing.

Error propagation is an important step in the modeling of ecological 
systems, as it provides estimates of the uncertainty around predictions. 
More generally, error propagation describes the effect of the uncertainty 
of input variables on the uncertainty of output variables [@Draper1995AssPro; @Parysow2000EffApp]. 
@Benke2018ErrPro identifies two broad approaches to model error propagation: 
analytically using differential equations or stochastically using Monte-Carlo 
simulation methods. The second approach is based upon samples of probability 
distributions and is more readily applicable to our problem of predicting 
ecological networks across space using our proposed methodological workflow. 
Indeed, each model's inputs can be sampled from the outputs of the preceding 
ones. Errors induced by the spatial or temporal extrapolation of data also 
need to be taken into account when 
estimating the uncertainty of a model's output [@Peters2004StrEco].

**Box 2: Machine Learning Illustration**


## Networks and Interactions

### Why predict networks and interactions at the same time?

Ecological networks are quite sparse [@MacDonald2020RevLin]---composed of a 
set of interactions, but also a larger set of non-interactions.
If we aim to predict the structure of networks from the "bottom-up"---
by considering each pairwise combination of $S$ different species---we are 
left with $S^2$ interaction values to estimate. Instead, we can use our 
existing understanding of the mechanisms that structure ecological networks 
to widdle down the set of feasible adjacency matrices, thereby reducing the 
amount of information we must predict, and making the problem of predicting 
interactions less daunting.

The processes that structure ecological networks do not only occur at the 
scale of interactions---there are also processes at the network level which 
limit what interactions are possible.
The realized structure of a network is the synthesis of the interactions 
forming the basis for network structure, and the network structure refining 
the possible interactions---"Part makes whole, and whole makes part" [@Levins1987DiaBio].

### What is the most important property of a network to predict?

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


### How do we predict how species that have never co-occurred will interact?

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


### How are interaction strengths actually inferred?

### Can these predictions rely on hypergraphs and multi-layers networks?

Although network ecology often assumes that interactions go strictly from one
node to the other, the web of life is made up of a variety of interactions 
with species can forming parts of different networks *e.g.* a plant species 
may be included in potha plant-pollinator as well as herbivory network and 
we could conceivably have a network of networks linked by shared 
species. One mathematical tool to describe these
situations is hypergraphs: hypergraphs are the generalization of a graph,
allowing a broad yet manageable approach to complex interactions
[@Carletti2020DynSys], allowing for particular interactions to occur beyond a
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


### How do we determine what interaction networks are feasible?

For several decades, ecologists have aimed to understand how networks of
many interacting species persist through time. The diversity-stability
"paradox", first explored by May [@May1974StaCom], shows that under a
neutral set of assumptions, ecological networks should become decreasingly
stable as the number of species increases. However, in the natural world
we observe networks of interactions that consist of far more species than
May's model predicts [@Albouy2019MarFis].

As a result, understanding what aspects of the neutral assumptions of
May's model are incorrect has branched many investigations into the 
relationship between ecological network structure and persistence
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



## Space

### How much do networks vary over space?

Networks can vary either in their structural properties (e.g. changes in
connectance or degree distribution) or in their composition (e.g. changes in
nodes and links identity). Interestingly, variation in the structural properties
of ecological networks tend to respond mostly to changes in the size of the
network. First, the number of links in ecological networks scales with the
number of species [@MacDonald2020RevLin; @Brose2004UniSpa]. Second, connectance
and size are driving the rest of the structural properties of ecological
networks [@Poisot2014WheEco; @Dunne2002FooStr; @Riede2010ScaFoo].

On a lower level, species turnover in space results in changes in the
composition of ecological networks. But, this is not the only reason networks
composition varies [@Poisot2015BeySpe]. Intraspecific variations can result in
interaction turnovers without changes in species composition
[@Bolnick2011WhyInt]. Similarly, changes in species abundances can lead to
variation in interactions strengths [@Canard2014EmpEvi; @Vazquez2007SpeAbu]. The
variation in the abiotic environment and indirect interactions
[@Golubski2016EcoNet] are also likely to modify the occurrence and strength of
individual interactions. Still, despite important species and interaction
turnovers, ecological networks tend to share a common backbone [@Mora2018IdeCom]
and functional composition [@Dehling2020SimCom]. In all, ecological networks do
vary considerably when looking at the identities of individual species and
interactions, but overall, the functional composition and structure of networks
is quite constant in space.

### How do we predict what the species pool at a particular location is?

As species form the basis of both network structure and interactions knowing which 
species are present at a particular site will inforom on the potential interactions 
that _could_ occur. A common approach in biogeography to predict whether a species 
will be
present or absent at specific sites is to use species distribution models (SDMs)
based on known occurrences and environmental conditions at these locations, such
as climate and land cover (abiotic filter) [@Guisan2005PreSpe,
@Elith2006NovMet]. Including interactions or co-occurrences in SDMs, therefore
the biotic filter, generally improves predictive performance [@Wisz2013RolBio]
(discussed in more details in the next section).

Several approaches have been proposed for multi-species predictions, as is
required for the species pool. Community assemblage at a particular site can be
predicted either by combining independent single-species SDMs (stacked-SDMs,
SSDMs) or by directly modelling the entire species assemblage and multiple
species at the same time (joint SDMs, JSDMs) [@Norberg2019ComEva]. Building on
the JSDM framework, hierarchical modeling of species communities was also
suggested [@Ovaskainen2017HowMak], and has the advantage of capturing processes
that structure communities. An interesting approach, put forward by
@Guisan2011SesNew with spatially explicit species assemblage modeling (SESAM),
is to constrain the SDM predictions using macro-ecological models. Properties
such as species richness can be used to constrain assemblage predictions from
stacked species distribution models [@DAmen2015UsiSpe]. Similarly, the next step
we envision here, in light of the framework we proposed earlier, is to constrain
distribution predictions using network properties. This would also build on
previous calls to adopt a probabilistic view: there have been calls for a
probabilistic species pool [@Karger2016DelPro], and more importantly including
interactions through Bayesian networks and propagating conditional dependencies
has generated better range predictions [@Staniczenko2017LinMac].
@Blanchet2020CooNot argue that this is more mathematically explicit about the
relation between species, thus avoiding some confusion between interactions and
co-occurrences, but that it is also technically challenging and requires prior
knowledge of the interactions. This could potentially be solved through our
framework of predicting networks first, interactions next, and finally species.

### What is the spatial scale suitable for the prediction of species interactions?  

If we trace the mechanisms that result in a given interaction to the smallest
scale, we can end up looking at genes interacting with each other resulting in
fluctuation of genomes and phenotypes across populations of a given species. At
a planetary scale, however, interactions can seem too similar because individual
differences are grouped together at coarser resolutions. Additionally, there is
a trade-off when we combine different taxonomic and spatial scales: assessing
interactions between higher taxonomic levels at a microscale level ignores
individual plasticity, while individual-level interactions at a macroscale
tangents to stochasticity. Another component the interplay between scale and
interactions is *time*. Different timeframes enclosure different dynamics
[@Trojelsgaard2016EcoNeta]. For example, an observation made in a timeframe too
short can capture an opportunistic interaction, which, by definition, does not
frequently occur. If the time considered is too long, it will involve the
evolutionary history of species, adaptation and co-evolution. The spatial scale
is connected to the phylogenetic and time scales in the sense that individuals
are highly affected by the present, local environmental variables, while species
and clades have their evolutionary history defined by historical series of
events. Therefore, what should be the appropriate spatial scale for the
prediction of species interactions?  

As described above (PR #20), we can use different proxies to predict potential
interactions. The choice of such proxies should be theoretically linked to the
spatial scale we are using in our prediction [@Wiens1989SpaSca]. For example,
@Bartomeus2016ComFra describe how functional traits influence the structure of
ecological networks in three different ways: they are selected by the
environmental conditions, they alter the probability of interactions and finally
they determine the interaction functioning. The environmental filtering occurs
at a continental level, subsetting species from the regional pool to co-occur
locally. At this level we can not predict interactions properly, since we are
only assessing the probability that two species would occur at the same place. A
continental spatial scale in this case means that the total extent includes
all the species distribution limits, and the samples can include more than one
population.  

At a second level we can use morphological traits of co-occurring species to
assess the probability of interaction between them [@Bartomeus2016ComFra]. This
means that we are considering processes that act on a timescale large enough to
shape the population, but too small to shape its evolution. This translates at a
spatial extent that does not necessarily capture the entire distribution of a
given set of species, with a resolution that is sufficient to capture the
phenotypical variability of the species. At this intermediate scale, we can
infer interactions through the phylogenetic similarity (or match) between
species, assuming their functional traits and the interactions themselves are
phylogenetically conserved [@Gomez2010EcoInt]. In fact, if the niche is a
property of the species and it is phylogenetically conserved as well, we can
think of the probability that one species will interact with another as the
"amount" of niche superposition between them. This logic also applies when we
want to evaluate potential interactions for bipartite networks and identify
species that can replace one another inside each set
[@Desjardins-Proulx2017EcoInt].  

At an even smaller scale, behavioural traits would help us model interactions
efficiency [@Bartomeus2016ComFra], and take a step closer to realized
interactions. At this point, we would need a good amount of good quality
training data to model potential interactions. The spatial resolution in this
case should be fine enough to capture foraging area, and sometimes natural
history variation inside a population, and that would make our model more
precise, but much less generalizable. At this scale the abundance is also
important, as it modulates the probability of encounter along with behaviour
[@Wells2013SpeInt].  

Finally, ecological interactions can potentially be predicted at regional and
local scales as long as spatial resolution and extension are adequate to capture
the right variability of the data to be learned from. It is also fundamental to
have consistency among the variables used: life-history traits, for instance, are
variables that act at short timeframes and will add stochasticity to models
that predict interactions at coarse resolution, and vice-versa.  

### How do we combine spatial and network predictions?


## Time
Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

### What data do we need to turn a predictive model into a forecasting model?
Forecasts of the model's inputs

### How can we validate a forecasting model?
Often the purpose of building a forecasting model to inform _present_ action 
[@Dietze2018IteNea]. Yet, the nature of forecasting---trying to predict the future---is 
that you can only know if a forecast is "right" once it is too late to change it. 
If we want to maximize the chance that "reality" falls within a forecasting 
model's predictions, there are two directions to approach this problem: the 
first is to extend model validation techniques to a forecasting context, and 
the second is to attempt to maximize the amount of uncertainty in a model 
without compromising its resolution.

Crossvalidation (see _How do we validate a predictive model?_) can be used 
to test the efficacy of a forecasting model. Given a time-series of $N$ 
observations, a model can iteratively be trained on the first $n$ time-points 
of data, and the forecasting model's accuracy can be evaluated on the remaining 
time-points it hasn't "seen". This enables us to understand both how much 
temporal data is required for a model to be robust, and also enables us to 
explore the _forecasting horizon_ of a process.
Further, this approach can also be applied in the opposite temporal 
direction--- if we have reliable data from the past, "hindcasting" can also 
be used to test a forecast's accuracy.

However, these methods inevitably bump into a hard-limitation on what is 
feasible for a forecasting model. The future is uncertain.
Any empirical time-series we use to validate a model was collected in past 
conditions that may not persist into the future.
Any system we wish to forecast will undergo only one of many possible 
scenarios (see _Forecasting Box_), yet we can only observe the realized 
outcome of the system under the scenario that actually unfolds.
It is therefore impossible to assess the quality of a forecasting model 
in scenarios that remain hypothetical.
If the goal is to maximize the probability that reality will fall within 
the forecast's estimates, forecasts should incorporate as much uncertainty 
about the future scenario as possible.
One way to do this is _ensemble modeling_ which combines forecasts from  
multiple different models.
However, as we increase the amount of uncertainty we incorporate into a 
forecasting model, the resolution of the forecast's predictions shrinks,
and therefore the modeler be mindful of the trade-off between resolution 
and accuracy in any forecasting model (see _Forecasting Box_).

A forecast inherently has a _resolution limit_ in space, time, and  organization.
For example, one could never hope to predict the precise abundance of every 
species on Earth on every day hundreds of years into the future.
There is often a trade-off between resolution and a forecasting horizon.
However, a lower resolution forecast, like primary production will be at a 
maximum in the summer, is likely to be true.

Further, the inherent limitations on the "forecastability" of ecological time-series  [@Pennekamp2019IntPre] (see _Forecasting box_)


### What ecological knowledge would forecasting bring?
Forecasting how climate change will alter biodiversity is crucial for maximising
conservation outcomes. On the one hand, we know that biotic interactions
influence the distribution of species at different scale [@Araujo2007TheImp,
@Pigot2013SpeInt]. On the other hand, most existing models to predict the future
distribution of species ignore interactions [@Urban2016ImpFor]. Species range
shifts and phenological adaptations will inevitably create spatiotemporal
mistmatches and affect encounter rates between interacting species
[@Gilman2010FraCom]. New links will also be created between species that are not
currently co-occuring [@Gilman2010FraCom]. Only by forecasting how species will
interact can we hope to have an accurate portrait of how biodiversity will be
distributed under the future climate.

Not only this, but how biodiversity is structured influence the functioning of
the whole ecosystem, community stability and persistance [@Thompson2012FooWeb,
@Stouffer2010UndFoo]. Will climate change impact the distribution of network
properties (e.g. connectance)? If so, which regions or species groups need
special conservation efforts? These overarching questions are yet to be answered
[but see @Albouy2013FroPro; @Kortsch2015CliCha; @Hattab2016ForFin]. We believe
that this roadmap towards forecasting ecological networks provide useful
guidelines to ultimatly be able to predict more accuratly how climate change
will affect the different dimensions of biodiversity and ecosystem functioning.


## Why should we forecast species interaction networks?

Predictions of species interactions are critical for informing ecosystem 
management[@Harvey2017BriEco] and systematic conservation prioritization 
[@Pollock2020ProBio], and for anticipating extinctions and their consequences 
[@McDonald-Madden2016UsiFoo; @McWilliams2019TheSta].
Ecological interactions shape species distributions at both local and broad 
spatial scales. Including interactions in SDM models typically improves 
predictive performance [@Araujo2007ImpBio; @Wisz2013RolBio]---which tend to 
rely on approaches involving estimating pairwise dependencies based on 
co-occurance (JSDM paper?), using surrogates for biotic-interaction gradients, 
and hybridizing SDMs with dynamic models [@Wisz2013RolBio].
Improving SDMs through interactions is crucial for conservation, as nearly 
30% of models in SDM studies are used to assess population declines or landscape 
ability to support populations [@Araujo2019StaDis].


Ecosystem functioning promotes ecosystem services, which are related to basic 
issues of health and the economy of humans, including pathogen transmission, 
food security, or the availability of fresh water.
But in a world with a high rate of biodiversity loss, land transformation, and 
climate change, researchers are worried about how to protect human lives and 
improve life quality in different countries, having into account the measure 
of the change in the world in the following years.  

Because interactions carry a lot of ecological and evolutionary information 
about biodiversity, predicting links can give us a more complete framework 
tounderstand processes and forecast rearrangements of nature. Moreover, 
using data to make reliable predictions about how ecosystems will change 
over time will give us critical information that could be communicated to 
decision-makers and the scientific community about what are future 
environmental risks awaiting and how to mitigate them [@Kindsvater2018OveDat].





# Boxes

## Box 1: Biological Examples

### Definitions
#### What is a species interaction?

Interactions between species can be manifested in a multitude of ways e.g. different
types [@Jordano2016ChaEco], strengths, or symmetry and are not necessarily restricted
between only a pair of species e.g indirect interactions [@Morales-Castilla2015InfBio]. The common thread
between these multiple forms of interactions is that *at least* one of the species is
affected by the interaction, this can be either positively or negatively [@Morales-Castilla2015InfBio].

Interactions can be representad as graphs, where each species is represented as a node 
and each interaction as an edge
[@Delmas2018AnaEco, @Pascual2006EcoNet], and the value/form an edge takes is a
representation of the interaction. Using a matrix format we can construct 
interaction networks in using 1s and 0s to 
represent the presence or absence of interaction respectively [@Dunne2006NetStr].
This allows for the calculation of many network properties (particularly pertaining to structure),
with different ways being used so as to represent different interaction types 
including:

* *unipartite networks:* where each species *appears* twice -
both as a row and column species, these are typically used to
represent foodwebs
* *bipartite networks:* where we have two interacting species 
guilds and have one guild be represented
by rows and the other by columns, these are typically used for
paiewaise interactions *e.g.* hosts and parasites, 
* *k-partite networks:* serve as a way to integrate various bipartite 
networks e.g. parasitoid webs,
seed dispersal networks, and pollination networks [@Pocock2012RobRes].


#### What does interaction strength mean?

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

**I would argue for a certain homogenization of interaction strength between 
different types of network (interaction) to make comparison/analysis easier. Relevant? How? **


## Box 2: ML Case Study

## Box 3: Forecasting

# References
