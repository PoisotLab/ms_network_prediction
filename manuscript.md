---
  bibliography: [references.bib]
---
# Introduction

Ecosystems *are* interactions -- organisms interact with one-another and with
their environment, either directly or indirectly. Between organisms, these
interactions form networks of varying complexity, drive ecological and
evolutionary dynamics, and maintain ecosystem diversity and functioning
[@Delmas2018AnaEco; @Landi2018ComSta; @Albrecht2018PlaAni]. Networks of species
interactions underpin our understanding of key ecological processes
[@Pascual2006EcoNet; @Heleno2014EcoNet]. Yet, even basic knowledge of species
interactions (like being able to list them, or guess which ones may exist) is
one of the most severe shortfalls in biodiversity science [@Hortal2015SevSho].
This is due in large part to the tedious, time-consuming, and expensive data
collection process. As with many ecological systems, networks of species
interactions have entered their "long now" [@Carpenter2002EcoFut], where
contemporary actions have long-term, low-predictability consequences
[@Burkle2013PlaInt]. Therefore, our field needs a conceptual path forward toward
models that enable prediction (for the present) and forecasting (for the future)
of species interactions and the networks they form [@McCann2007ProBio;
@Seibold2018NecMul]. Here we provide a simple illustration to show how machine
learning approaches can enable unreasonably effective prediction of interactions
in a host-parasite system, which serves as a proof-of-concept for this
conceptual framework. We then propose a roadmap forward for improving
predictions using this approach, and provide a primer on the relevant tools and
methods that could be incorporated into models of this type in the future in
order to account for the spatial, temporal, and climatic dimensions of network
prediction [@Burkle2011FutPla]

Better prediction of ecological networks would help unify the fields of
community, network, and spatial ecology, improve the quantification of the
functional relationships between species [@Dehling2018BriElt;
@OConnor2020UnvFoo], re-evaluate metacommunities in light of network structure
[@Guzman2019MulExt], and enable a new line of research into the biogeography of
species interactions [@Massol2017ChaFou; @Braga2019SpaAna] which incorporates a
synthesis of both Eltonian and Grinnellian niche [@Gravel2019BriElt]. Further,
the ability to reliably predict and forecast species interactions would inform
conservation efforts for protecting species, communities, and ecosystems.
International panels draw on models to establish scientific consensus
[@Araujo2019StaDis]---IUCN Red List assessments includes an evaluation of a
species from known, inferred, and projected sites of occurrence
[@IUCNRedListTechnicalWorkingGroup2019MapSta], which can be improved through
more effective forecasts of species distributions and interactions
[@Syfert2014UsiSpe]. Integration of species interactions into the assessment of
vulnerability to climate change is a needed methodological advance
[@Foden2016IucSsc]. IPBES recognized that models for forecasting regional
biodiversity dynamics will need to incorporate species interactions
[@IPBES2016MetAss]. Moreover, recent studies argue for a shift in focus from
species to interaction networks for biodiversity conservation to better protect
species, ecosystem processes, and ecosystem services [@Harvey2017BriEco].
Interactions are a key element of the functional role of a species, which should
be considered for the evaluation of species recovery for the development of an
IUCN Green List of recovered species or similar [@Akcakaya2018QuaSpe].

# Proof-of-Concept

The core premise of this manuscript is that ecological networks can be
predicted. In this section, we provide a proof-of-concept, in which we (i)
aggregate a series of networks collected across space into a metaweb, (ii)
extract latent features based on the co-occurrence of species, (iii) use these
features to train a neural network to predict interactions, and (iv) apply this
classifier to the original features to predict possibly missing interactions
across the entire species pool. The entire analysis is presented in
@fig:example, and the code to reproduce it is available at **TODO OSF LINK**;
the entire example was carried out in *Julia 1.5.3* [@Bezanson2017JulFre], and
notably uses the *Flux* machine learning framework [@Innes2018FluEle]. Note that
this analysis is meant to serve as an *example only*, and should in practice be
fined-tuned according to the state of the art [*e.g.* @Goodfellow2016DeeLea].

![What does it actually mean to predict a species interaction network? An
overgeneralized version of the problem of taking incomplete sampled networks and
producing a metaweb with prediction about how species that have not been
observed co-occuring will interact.](./figures/network_prediction_problem.png)


 We used data from @Hadfield2014TalTwo, describing 51 host-parasite networks,
where not all species pairs co-occur across sites. This implies that there are
"negative associations" that might be biologically feasible but not observed
because the two species have not been observed in co-occurrence. As this dataset
has no features like species traits on which to base a predictive model, we have
aggregated all interactions into a binary metaweb [@Dunne2006NetStr], internally
represented as a sparse matrix. We have then transformed the (undirected)
metaweb through a probabilistic PCA [@Tipping1999ProPri], so as to create a
number of latent features for the species in a context where the dataset is both
unbalanced and likely to have many missing values. This frames the problem as
predicting a binary outcome, the interaction $M_{xy}$ represented as `true` or
`false`  based on a features vector $v_{xy} = [v_x, v_y]$ where $v_x$ is the
values of the selected features for the parasite and $v_y$ is the features of
the host. In the following example, we used the first 15 components of the
latent sub-space created by the probabilistic PCA. This features vector is then
fed into the input layer of a neural network, which uses three hidden layers
with appropriate dropout rates ($\frac{1}{2}$), and finally a two-neurons output
layer whose result is softmaxed to pick the most likely outcome,  *i.e.* the
interaction bit describing an interaction when equal to 1, and no interaction
when equal to 0.

![Overview of the imputation process. An empirical network [from
@Hadfield2014TalTwo] is converted intro latent features using probabilistic PCA,
then used to train a deep neural network to predict species interactions. The
initial and imputed networks are represented as their tSNE embedding, and the
colors of nodes are the cluster to which they are assigned based on a $k$-means
clustering of the tSNE
output.](figures/review-netwpred-example.png){#fig:example}

During the training of this neural network, we exploited ecological constraints
in two ways. First, the selection of features was done so that absent
interactions in a species pair with no co-occurrence were removed from the data.
This ensures that the network is trained only on the subset of the data for
which we have minimal ecological information. Second, the batches of 16 items
used for training were constrained to have at least 10 positive interactions.
The reasoning for this choice was made based on three observations: the network
is sparse (*i.e.* the prevalence of interactions is low); negative interactions
have a chance of being false negatives due to lack of reporting in the field;
there are no true negative interactions reported, *i.e.* interactions for which
we know that they almost never happen. Therefore, slightly inflating the dataset
with positive interactions enables us to counterbalance these biases.

After the training ($2.5\times 10^4$ epochs in @fig:example), our model reached
an accuracy of $\approx 0.8$, with no marked deviation between the training and
testing sets (respectively 80% and 20% of the data), suggesting no to minimal
overfitting. Applying this model to the entire dataset (including species pairs
never observed co-occuring in the dataset) identified 1831 new possible
interactions -- 382 of which were in species pairs where the pair of species was
never considered prior. This suggests that meaningful information about
ecological interaction is structured within network data, and our core argument
here is that we should embrace the prediction of species interaction networks as
a worthy topic of concept , and specifically strive to adopt an explicitly
spatial and temporal perspective on this question. Now, the question becomes:
home do we make our prediction of ecological networks _better_?

# A Roadmap Toward Better Prediction of Ecological Networks across Space and Time

Below we focus on and discuss integrating what we envisage to be the conceptual
and methodological pathway towards better prediction of
ecological networks (@fig:conceptual).

## Challenges: the many constraints on prediction

### Ecological network data are scarce and hard to obtain

At the moment, our understanding of the structure of ecological networks is
limited by the availability of data. Although we have seen a growth in species
occurrence data, this growth is much slower for ecological interactions because
species interactions are challenging to sample comprehensively
[@Bennett2019PotPit; @Jordano2016SamNet] and sampling methodology has strong
effects on the resulting data [@deAguiar2019RevBia]. In turn, the difficulty of
sampling interactions can lead to biases in our understanding of network
structure [@deAguiar2019RevBia]. This knowledge gap has motivated a variety of
approaches to deal with interactions in ecological research based on assumptions
that do not always hold, such as the assumption that co-occurrence is equivalent
to meaningful interaction strength, when it is known that co-occurrence is the
only prerequisite for an interaction to occur [@Blanchet2020CooNot]. Spatial
biases in data coverage are prevalent at the global scale (with South America,
Africa and Asia being under-represented) and different interaction types show
biases towards different biomes (or environmental conditions)
[@Poisot2020EnvBia]. These 'spatial gaps' serve as a limitation to our ability
to confidently make predictions when accounting for real-world environmental
conditions, especially in environments for which there are no analogous data.

Further, the analysis of interaction strength from empirical estimation is
highly prone to bias as existing data quantifying interaction strength are
usually lumped together, making it difficult to differentiate the strength in
per-individual interactions from the strength of a whole species interaction
[@Wells2013SpeInt]. Empirical estimations of interaction strength are still
crucial [@Novak2008EstNon], but are a hard task to quantify in natural
communities [@Wootton1997EstTes; @Sala2002ComDis; @Wootton2005MeaInt],
especially as the number of species composing communities increases, composed
with the possibility of higher-order interactions or non-linear responses in
interactions [@Wootton2005MeaInt]. Furthermore, interaction strength is
extremely variable and context dependent and can be influenced by density
dependence and spatiotemporal variation in abundances and community composition
[@Wootton2005MeaInt]. A better understanding of interaction strengths in
communities is a key step in linking species interactions to ecosystem processes
and functioning.

### Powerful predictive tools work better on large data volumes

This scarcity of data limits the range of computational tools than can be used
by network ecologists. Most deep learning methods, for instance, are very data
expensive. The paucity of data is compounded by a collection of biases that can
be found in existing datasets. Species interaction datasets are typically
dominated by food webs, pollination, and host-parasite networks
[@Ings2009EcoNet; @Poisot2020EnvBia]. This could prove to be a limiting factor
when trying to understand or predict networks of *underrepresented* interaction
types or when trying to integrate networks of different types
[@Fontaine2011EcoEvo], especially given the inherit structural variation of
ecological networks [@Michalska-Smith2019TelEco]. This stresses the need for an
integrated, flexible, and data-efficient set of computational tools which will
allow us to predict ecological networks accurately from existing and imperfect
datasets, but also enable us to perform model validation and comparison with
more flexibility than existing tools. We argue that @fig:example is an example
of the promise of these tools *even* when facing datasets of smaller size. When
carefully controlling for over-fitting (which is discussed in the next section),
machine learning systems are at least adequate at generalizing. The ability to
extract and engineer features, notably latent ones, also contributes to
bolstering our predictive ability. In short, the current lack of massive
datasets must not be an obstacle to prediction; it is an ideal testing ground to
understand how little data is sufficient to obtain actionable predictions.

### Scaling-up predictions requires scaled-up data

We are also currently limited by the the level of biological organisation at
which we can describe ecological networks. For instance, our understanding of
individual based networks [*e.g.* @Araujo2008NetAna; @Tinker2012StrMec] is still
in its infancy [@Guimaraes2020StrEco] and acts as a resolution-limit at which we
would be able to predict networks. On the note of scale, the resolution of
environmental (or landscape) data would also limit our ability to predict
networks at finer scales, although current trends in e.g. remote sensing would
suggest that with time this would become less of a hindrance
[@Makiola2020KeyQue]. Ecosystems are a quintessential complex-adaptive-system
[@Levin1998EcoBio]. In @fig:everything_is_connected, we see the myriad of ways
in which processes at different spatial, temporal, and organizational scales
influence and respond to one another. Understanding how the product of these
different processes drive the properties of ecosystem across different scales
remains a central challenge of ecological research, and we should strive to work
on methods that will integrate these different 'snapshots'.

## Opportunities: the emerging ecosystem of open tools and data

If we wish to predict the interactions between species we have not observed
together, using our knowledge of the structure of ecological networks to
interact in a particular ecosystem is one of our most useful assets. We are able
to infer species interactions using proxies such as traits, phylogenies,
geographical data and other frameworks [@Morales-Castilla2015InfBio]. Drawing on
elements that contribute to the realization of an interaction such as abundance
and traits matching in space and time, and the combination of these elements
allow us to infer potential from realized interactions and empirical data about
populations [@Poisot2016StrPro]. In turn, this effort is supported by a thriving
ecosystem of data sources and computational tools. In this section, we give a
brief overview of these resources.

### Open Data

The acquisition of biodiversity and environmental data has tremendously
increased over the past decades thanks to the rise of citizen science
[@Dickinson2010CitSci] and of novel technology [@Stephenson2020TecAdv],
including wireless sensors [@Porter2005WirSen], next-generation DNA sequencing
[@Creer2016EcoSF], and remote sensing [@Skidmore2015AgrBio; @Lausch2016LinEar].
Open access databases, such as [GBIF](https://www.gbif.org/) (for biodiversity
data), [NCBI](https://www.ncbi.nlm.nih.gov/) (for taxonomic and genomics data),
[TreeBASE](https://www.treebase.org/treebase-web/home.html) (for phylogenetics
data), [CESTE](https://icestes.github.io/) [@Jeliazkov2020GloDat] (for
metacommunity ecology and species traits data), and
[WorldClim](https://www.worldclim.org/data/bioclim.html) (for bioclimatic data)
contain millions of data points that can be integrated to monitor and model
biodiversity at the global scale. For species interactions data, at the moment
[Mangal](https://mangal.io/#/) is the most comprehensive open database of
published ecological networks [@Poisot2016ManMak], and
[GloBI](https://www.globalbioticinteractions.org/about) is an extensive database
of realized and potential species interactions [@Poelen2014GloBio]. Developing
standard practices in data integration and quality control [@Kissling2018BuiEss]
and in next-generation biomonitoring [NGB; @Makiola2020KeyQue] would improve our
ability to make reliable predictions of ecosystem properties on increasing
spatial and temporal scales. The advancement of prediction techniques coupled
with a movement towards standardising data collection protocols (e.g.
@Perez-Harguindeguy2013NewHan for plant functional traits) and metadata (e.g.
[DarwinCore](https://www.tdwg.org))---which facilitates interoperability and
integration of datasets---as well as a growing interest at the government level
[@Scholes2012BuiGlo] paints a positive picture for data access and usability in
the coming years.

### Open Tools and Methods

Machine learning encompasses a broad variety of techniques applied with or
without human supervision. These techniques can often be more flexible and
perform better than classical statistical methods, and can achieve a very high
level of accuracy in many predictive and classification tasks in a relatively
short amount of time [e.g. @Cutler2007RanFor; @Krizhevsky2017ImaCla]. Increasing
computing power combined with recent advances in machine learning techniques and
applications shows promise in ecology and environmental science (see
@Christin2019AppDee for an overview). Moreover, ongoing developments in the
field of artificial intelligence are aimed at using deep learning more
efficiently in low-data regimes [e.g. @Antoniou2018DatAug] and with unbalanced
datasets [@Chawla2010DatMin]. Machine learning is emerging as the new standard
in computational ecology in general [@Olden2008MacLea; @Christin2019AppDee], and
in network ecology in-particular [@Bohan2017NexGlo], as long as sufficient
relevant data are available. Many ecological and evolutionary processes underlie
species interactions and the structure of their ecological networks [e.g.
@Vazquez2009UniPat; @Segar2020RolEvo]. It can thus be difficult to choose
relevant variables and model species interactions networks explicitly. A
promising application of machine learning in natural sciences is
Scientific-Machine Learning (SciML), a framework that combines machine learning
with mechanistic models [@Chuang2018AdvCon; @Rackauckas2020UniDif]. Although
SciML has not yet been applied in ecology, it has the potential to combine
mechanistic models with black box machine-learning to predict ecological
networks with relatively small amounts of data using existing process-based
models. Considering the current biases in network ecology [@Poisot2020EnvBia]
and the scarcity of data of species interactions, the prediction of ecological
networks will undoubtedly benefit from these improvements. Many studies have
used machine learning models specifically with ecological interactions. Relevant
examples include species traits used to predict interactions and infer
trait-matching rules [@Desjardins-Proulx2017EcoInt; @Pichler2020MacLea],
automated discovery of food webs [@Bohan2011AutDis], reconstruction of
ecological networks using next-generation sequencing data [@Bohan2017NexGlo],
and network inference from presence-absence data [@Sander2017EcoNet].

![A conceptual roadmap highlighting key areas for the prediction of ecological
networks. Starting with the input of data from multiple sources, followed by a
modelling framework for ecological networks and the landscape, which are then
ultimately combined to allow for the prediction of spatially explicit
networks.](figures/conceptual_v2.png){#fig:conceptual}

# A Primer on Predictive Network Ecology

Below we provide a primer on predictive network ecology, with particular focus
on using machine learning approaches in the modelling process, in order to
provide a path forward toward building models to predict ecological networks and
interactions and to better understanding the relationship between species
interactions and network structure. Here adopt a question-driven approach to
serve as a guide through the path toward building models to predict and forecast
the structure of ecological networks across space.

## Models

### What is a predictive model?

Models are used for many purposes, and the term "model" embodies a wide variety
of meanings in scientific discourse. All models can be thought of as a function,
$f$, that takes a set of inputs $x$ (also called features, descriptors, or
independent variables) and some parameters $\theta$, and maps them to predicted
output states $y$ (also called label, response, or dependent variable) based on
the input to the model: $y=f(x,\theta)$. However, any given model $f$ can be
used for either descriptive or predictive purposes.

Many forms of scientific inquiry are based around inference (also called the
inverse problem, fitting a model, or training a model) [@Stouffer2019AllEco]. In
this context, the goal of using a model is to estimate the parameters, $\theta$,
that best explain a set of empirical observations, $\{\hat{x}, \hat{y}\}$. In
some cases, these parameter values are themselves of interest (e.g the strength
of selection, intrinsic growth rate, dispersal distance), but in others cases,
the goal is to compare different models $f_1, f_2, \dots$ to determine which
provides the most parsimonious explanation for a dataset. The quantitative
representation of "effects" in these models---the influence of each input on the
output---is often assumed to be linear, and in the frequentist context, the goal
is often to determine if the coeffecient corresponding with an input is non-zero
to determine its "significance" in influencing the outcome. Models designed for
inference have utility, however, in order for ecology to develop as a predictive
science [@Evans2012PreEco], interest has grown in developing models that are
used not just for description of data, but also for prediction. Predictive
models use _the forward problem_, where the aim is to predict new values of the
output $y$ given an input $x$ and our estimate value of $\theta$
[@Stouffer2019AllEco]. Because the forward problem relies on an estimate of
$\theta$, then, the problem of inference is nested within the forward problem
(@fig:models).

![The nested nature of developing predictive and forecasting models, showcases
the _forward problem_ and how this relies on a hierarchical structure of the
modelling process.](figures/forecasting_v3.png){#fig:models}

### What do you need to build a predictive model?

In order to build a predictive machine-learning model, one needs the following:
first, **data**, split into features $\hat{x}$ and labels $\hat{y}$ (Box Figure
Label). Second, a **model** $f$, which maps features $x$ to labels $y$ as a
function of parameters $\theta$, i.e. $y = f(x, \theta)$. Third, a loss function
$L(\hat{x}, x)$. Lastly, **priors** on parameters, $P(\theta)$. Often, before
fitting the model, the dataset will be split into a training and validation
subsets. The model is trained on the training subset, then the fit and model
performance are evaluated on the validation set [@Christin2020GoiFur]. Another
important step in predictive modelling is feature engineering: adjusting and
reworking the predictors to enable models to better uncover predictor-response
relationships [@Kuhn2019FeaEng]. For instance, this can include projecting the
predictors into principal component analysis space, and selecting only a set of
dimensions for the modelling, as in our machine learning illustration.

### How do we validate a predictive model?

After model fitting, we inevitably want to see how "good" it is. One of the
context for validation is _model comparison_, where we aim to see which of a
competing set of models provides the best explanation for a data set. A naive
initial approach is to simply compute the average error between the model's
prediction and the true data we have, and choose the model with the smallest
error---however this approach inevitably results in _overfitting_. One approach
to avoid overfitting is using information criteria (*e.g.* AIC, BIC, MDL, the
heavily maligned Bayes Factor), which are based around the heuristic that good
models maximize the ratio of information provided by the model to the number of
parameters it has.

However, when the intended use-case of a model is prediction, the relevant form
of validation is _predictive accuracy_. _Crossvalidation_ provides a better
alternative for validating a model's predictive capacity. Crossvalidation
methods divide the original dataset into two---one which is used to fit the
model (called the _training_ set) and one used to validate its predictive
accuracy on the data that is hasn't "seen" yet (called the _test_ set)
[@Bishop2006PatRec]. This procedure is often repeated for different subdivisions
of the dataset. One powerful approach is Leave-one-out-crossvalidation (LOOCV),
which considers each data points uniquely as a test set, enabling analysis of a
given models sensitivity to a single data point [@Arlot2010SurCro]. However,
these methods are typically limited by the ensuing computation time
requirements. Further adjustments can be done by adjusting the model structure
(layer compositions and network structures for neural networks, number of trees
and splits for tree-based models, etc.) and further tuning parameters.

## Networks and Interactions

### Why predict networks and interactions at the same time?

Ecological networks are quite sparse [@MacDonald2020RevLin]---composed of a set
of interactions, but also a larger set of non-interactions. If we aim to predict
the structure of networks from the "bottom-up"--- by considering each pairwise
combination of $S$ different species---we are left with $S^2$ interaction values
to estimate. Instead, we can use our existing understanding of the mechanisms
that structure ecological networks to widdle down the set of feasible adjacency
matrices, thereby reducing the amount of information we must predict, and making
the problem of predicting interactions less daunting. The processes that
structure ecological networks do not only occur at the scale of
interactions---there are also processes at the network level which limit what
interactions are possible. The realized structure of a network is the synthesis
of the interactions forming the basis for network structure, and the network
structure refining the possible interactions---"Part makes whole, and whole
makes part" [@Levins1987DiaBio].

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
it in mutualistic networks [@Vieira2015SimSto], and relate to stability
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
[@Poisot2015SpeWhy; @Pichler2020MacLea]. Given two species that co-occur, a
neutral approach to probabilistic interactions would be based on abundances and
trait matching would have no effect [@Canard2012EmeStr]. However, some proxies
can be used to make more accurate predictions of potential ecological
interactions. For instance, functional traits are good such proxies because they
are highly selected by ecological interactions and determine forbidden links
(such as the mechanical impossibility of a bird to consume seeds larger than its
beak). The fact that functional traits suffer some kind of selective pressure
and because niches tend to be conserved throughout a phylogenetic tree,
ecological interactions also tend to be conserved, and therefore we could also
use phylogenies to infer pairs of co-occurring species that could potentially
interact [@Gomez2010EcoInt]. In fact, the contribution of interactions to the
phylogenetic match between species is consistent even through scales
[@Poisot2018IntRet] and in neutral models [@Coelho2017NeuBio].

A separate family of methods that gained interest in recent years are the
network-based models. These models use the existing set of interactions to
identify the unmeasured traits (i.e. latent traits) driving the network
structure [@Becker2020PreWil]. Species positioned closely in the network should
interact with similar set of species [@Rossberg2006FooWeb; @Rohr2010ModFoo]. As
for functional traits, phylogenies can inform these models because these
unmeasured traits have evolved over time. [@Rossberg2006FooWeb;
@Elmasri2020HieBay]. These network-based models are unfortunately sensitive to
sampling biases and limited to prediction for species for which we already have
interaction data [@Becker2020PreWil].

### What is an interaction, really?

Interactions between species can be conceptualized in a multitude of ways (e.g.
different types, variable strengths, symmetric vs. asymmetric, direct vs.
indirect) [@Jordano2016ChaEco; @Morales-Castilla2015InfBio]. The common thread
between these forms of interactions is that *at least* one of the species is
affected by the presence of another, either positively or negatively
[@Morales-Castilla2015InfBio]. We can represent these networks of interactions
as graphs, where each species is represented as a node, and each interaction as
an edge [@Delmas2018AnaEco; @Pascual2006EcoNet]. The value of each edge each
represents information about that interaction. We can represent this network
using a matrix, using 1s and 0s to represent the presence or absence of an
interaction between species $i$ and species $j$ at each matrix entry $(i,j)$.
[@Dunne2006NetStr]. This construct allows for convenient computation of network
properties, particularly properties relating to network structure. Networks can
be used to represent a variety of interaction types, including: *unipartite
networks,* where each species can be linked any other species, species (these
are typically used to represent food webs), *bipartite networks* where there are
two pools of species, and all interactions occur between species in each pool,
are typically used for pairwise interactions (e.g. hosts and parasites), and
*k-partite networks:,* which serve as a way to expand to more than two discrete
sets of interacting species (e.g. parasitoid webs, seed dispersal networks, and
pollination networks) [@Pocock2012RobRes].

### What about interaction _strength_?

Species interaction networks can also be used as means to quantify and
understand _interaction strength_. Interaction strength, unlike the qualitative
presence or absence an interaction, is a continuous measurement which attempts
to quantify the effect of one species on another. While an interaction strength
can take multiple forms, they can generally be divided into two main categories
(as suggested by @Berlow2004IntStr): it can either be seen as the strength of an
individual species-to-species link or as the effect that the changes in one
species has on the dynamics of the other species. Interaction strength is
measured either as the relative importance of one species on another or the
direct effect of one species on another over a period of time, often in the
units of biomass [@Heleno2014EcoNet; @Berlow2004IntStr; @Wootton2005MeaInt].
This differentiates between interactions at the individual level and
interactions that are population level, and emphasizes the importance of
understanding the scaling of interactions from individuals to populations to
communities [@Berlow2004IntStr]. One recurring observation throughout studies of
interaction strengths is that networks are often composed of many weak links and
few strong links [@Berlow2004IntStr]. Knowing the distribution of interaction
strength within a network informs on its stability [@Neutel2002StaRea;
@Ruiter1995EnePat], influences on the ecosystem functioning [@Duffy2002BioEco;
@Montoya2003FooWeb] and our potential to improve on the development of
multispecies models [@Wootton2005MeaInt]. Seeing interaction strength within a
network as energy fluxes could also possibly lead to its integration within the
Biodiversity-Ecosystem Functioning (BEF) framework, which could in return
further improve even our understanding of community dynamics and ecosystem
functioning [@Barnes2018EneFlu].

### How are interaction strengths actually inferred?

Interaction strength can be inferred empirically or theoretically
[@Berlow2004IntStr]. While the development of theoretical predictive models to
infer interaction strength is important, the empirical sampling of quantitative
networks is not to be neglected as they are important to model parameterization
and validation [@Novak2008EstNon]. Before we attempt to make inferences from
data, we must adapt a conceptual framework to model interaction strength. One
such framework is functional foraging [@Portalier2019MecPre], where the primary
basis for inferring interaction is based on an organism's traits, the
environment, and foraging behavior such as searching, capture and handling
times. A different conceptual alternative, applicable in food-webs, is metabolic
based models, where body mass, metabolic demands, and energy loss are used to
infer energetic energy fluxes between organisms
[@Yodzis1992BodSiz;@Berlow2009SimPre].

Energy can be seen as the common currency that links every level of biology from
individual organisms to the whole ecosystem
[@Brown2004MetThe;@Barnes2018EneFlua]. Thus, predicting interaction strength as
energy fluxes could potentially open the way to the conciliation of the
different spheres of ecology. One bottom-up approach is to first estimate basal
species biomasses and from there the higher trophic-level species biomasses and
energetic demands are computed [@Berlow2009SimPre]. Alternatively, a top-down
approach, where energy fluxes are calculated starting from the top consumer
downward toward producers [@Barnes2018EneFlu]. Food-web energetics models can be
incorporated at various resolutions for a specific network, ranging from
individual-based data to more lumped data at the species level or trophic group,
depending on data availability [@Barnes2018EneFlu].

### What about indirect and higher-order interactions?

Although network ecology often assumes that interactions go strictly from one
node to the other, the web of life is made up of a variety of interactions where
species can form parts of different networks *e.g.* a plant species may be
included in both a plant-pollinator as well as herbivory network and we could
conceivably have a network of networks linked by shared species. Investigating
indirect interactions---either higher-order interactions between species, or
interaction strengths that themselves interact --- has gained interest in recent
years [@Golubski2016EcoNet; @Golubski2011ModMod]. One mathematical tool to
describe these situations is hypergraphs: hypergraphs are the generalization of
a graph, allowing a broad yet manageable approach to complex interactions
[@Carletti2020DynSys], allowing for particular interactions to occur beyond a
pair of nodes.

An additional degree of complexity is introduced by multi-layer networks
[@Hutchinson2019SeeFor]. Multi-layer networks offer links across "variants" of
the networks, which can include, timepoints, or environments. As such, these can
be particularly useful to account for the meta-community structure of ecological
networks [@Gross2020ModMod], or to understand how spatial dispersal graphs can
inform conservation actions [@Albert2017AppNet]. As @Pilosof2017MulNat suggest,
ecological networks intrinsically contain multi-layers, as they are shaped by
evolution, dispersal, environmental heterogeneity, among others.

However, the potential of links between larger subsets causes a combinatoric
explosion which increases the number of predictions we would need to make with
our already scarce data. *Prima facie*, increasing the dimensionality of the
object we need to predict (the multiple layers rather than a single network) may
make the problem complicated. But multi-layer networks encode ecological
constraints -- of dispersal, of evolution, and of niche suitability. One
question that is worth investigating is whether the multi-layer structure of
ecological networks may *improve* the predictibility of interactions. Indeed,
this is the case for social networks [@Jalili2017LinPre; @Najari2019LinPre;
@Yasami2018NovMul]. Although at the moment it seems bests to address our
understanding of simple networks, exploring the more intricate ways in which
species interact might require that we make room for hypergraphs and multi-layer
networks in our predictive framework.

### How do we determine what interaction networks are feasible?

For several decades, ecologists have aimed to understand how networks of many
interacting species persist through time. The diversity-stability "paradox",
first explored by May [@May1974StaCom], shows that under a neutral set of
assumptions, ecological networks should become decreasingly stable as the number
of species increases. However, in the natural world we observe networks of
interactions that consist of far more species than May's model predicts
[@Albouy2019MarFis]. As a result, understanding what aspects of the neutral
assumptions of May's model are incorrect has branched many investigations into
the relationship between ecological network structure and persistence
[@Allesina2012StaCri]. These assumptions can be split into dynamical assumptions
and topological assumptions.

On the topological side, we know that ecological networks are not structured
randomly. Some properties, like connectance, are highly predictable
[@MacDonald2020RevLin]. Various generative models of food-webs have been shown
to fit empirical networks more effectively than random models. These typically
rely on _network embeddings_---where each node (species) in the network is
assigned a value in a latent space, and the resulting network topology is
generated stochastically based on properties of the position of nodes in that
latent space. Generative network models have long used allometry as a
single-dimensional latent space---naturally we want to extend this to traits in
general [@Allesina2008GenMod].

The second approach to understand stability is through _dynamics_. Early models
of community dynamics (Lotka-Volterra, MacArthurs Consumer-Resource Model) rely
on the assumption of linear interaction effects. However, models of bioenergetic
community dynamics have shown promise in basing our understanding of dynamics in
food-webs, where the functional response of one species on another is grounded
in the understood relationship between allometry and metabolism
[@Delmas2017SimBio]. An additional consideration is the multidimensional nature
of "stability" and "feasibility" e.g resilience to environmental change vs
extinctions [@Dominguez-Garcia2019UnvDim] and how these different disturbances
will propagate along the various level of biological organization
[@Kefi2019AdvOur], as well as their effect over space such as dispersal
[@Gravel2016StaCom].

## Space

Although networks were initially used to describe the interactions *within* a
community, interest in the last decade has shifted towards understanding their
structure and variation over space [@Trojelsgaard2016EcoNet; @Baiser2019EcoRul],
and has established network ecology as an important emerging component of
biogeography and macroecology.

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
composition varies [@Poisot2015SpeWhy]. Intraspecific variations can result in
interaction turnovers without changes in species composition
[@Bolnick2011WhyInt]. Similarly, changes in species abundances can lead to
variation in interactions strengths [@Canard2014EmpEva; @Vazquez2007SpeAbu]. The
variation in the abiotic environment and indirect interactions
[@Golubski2016EcoNet] are also likely to modify the occurrence and strength of
individual interactions. Still, despite important species and interaction
turnovers, ecological networks tend to share a common backbone [@Mora2018IdeCom]
and functional composition [@Dehling2020SimCom]. In all, ecological networks do
vary considerably when looking at the identities of individual species and
interactions, but overall, the functional composition and structure of networks
is quite constant in space.

### How do we predict what the species pool at a particular location is?

As species form the basis of both network structure and interactions knowing
which species are present at a particular site will inform on the potential
interactions that _could_ occur. A common approach in biogeography to predict
whether a species will be present or absent at specific sites is to use species
distribution models (SDMs) based on known occurrences and environmental
conditions at these locations, such as climate and land cover (abiotic filter)
[@Guisan2005PreSpe, @Elith2006NovMet]. Including interactions or co-occurrences
in SDMs, therefore the biotic filter, generally improves predictive performance
[@Wisz2013RolBio] (discussed in more details in the next section). Several approaches have been proposed for multi-species predictions, as is
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
fluctuation of genomes and phenotypes across populations of a given species.
Additionally, there is a trade-off when we combine different taxonomic and
spatial scales: assessing interactions between higher taxonomic levels at a
microscale level ignores individual plasticity. As described above, we can use
different trait-based proxies to predict potential interactions. The choice of
such proxies should be theoretically linked to the spatial scale we are using in
our prediction [@Wiens1989SpaSca].
At some scales we can use morphological traits of co-occurring species to assess
the probability of interaction between them [@Bartomeus2016ComFra]. This
translates to a spatial extent that does not necessarily capture the entire
distribution of a given set of species, with a resolution that is sufficient to
capture the phenotypical variability of the species. At larger scales, we can
infer interactions through the phylogenetic similarity between species, assuming
their functional traits are themselves are phylogenetically conserved
[@Gomez2010EcoInt]. On scales where the niche is phylogenetically conserved, we
can think of the probability that one species will interact with another as the
"amount" of niche superposition between them [@Desjardins-Proulx2017EcoInt].
At the smallest scales, we may be interested in predicting behavioural traits
like foraging behavior [@Bartomeus2016ComFra]. At this point, the spatial
resolution in this case should is fine enough that a model may be precise in a
given system, but much less generalizable. At this scale it is also important to
consider abundance, it modulates the probability of encounter along with
behaviour [@Wells2013SpeInt].

### How do we combine spatial and network predictions?

In order to predict networks across space, we need to combine multiple
models---one which predicts what the species pool will be at a given location,
and one to predict what interaction networks composed from this species pool are
likely (see @fig:conceptual). Both of these models contain uncertainty. The
Bayesian paradigm provides a convenient solution to this---if we have a chain of
models where each model feeds into the next, we can sample from the posterior of
the input models. A different approach is _ensemble modeling_ which combines the
predictions made be several models, where each model is predicting the same
thing. Error propagation is an important step in the modeling of ecological systems, as
it provides estimates of the uncertainty around predictions. More generally,
error propagation describes the effect of the uncertainty of input variables on
the uncertainty of output variables [@Draper1995AssPro; @Parysow2000EffApp].
@Benke2018ErrPro identifies two broad approaches to model error propagation:
analytically using differential equations or stochastically using Monte-Carlo
simulation methods. The second approach is based upon samples of probability
distributions and is more readily applicable to our problem of predicting
ecological networks across space using our proposed methodological workflow.
Indeed, each model's inputs can be sampled from the outputs of the preceding
ones. Errors induced by the spatial or temporal extrapolation of data also need
to be taken into account when estimating the uncertainty of a model's output
[@Peters2004StrEco].

## Time

### Why should we forecast species interaction networks?

Forecasting species interactions are critical for informing ecosystem management
[@Harvey2017BriEco] and systematic conservation prioritization
[@Pollock2020ProBio], and for anticipating extinctions and their consequences
[@McDonald-Madden2016UsiFoo; @McWilliams2019StaMul]. Ecological interactions
shape species distributions at both local and broad spatial scales. Including
interactions in SDM models typically improves predictive performance
[@Araujo2007ImpBio; @Wisz2013RolBio; @Pigot2013SpeInt]---which tend to rely on
approaches involving estimating pairwise dependencies based on cooccurance,
using surrogates for biotic-interaction gradients, and hybridizing SDMs with
dynamic models [@Wisz2013RolBio]. Most existing models to predict the future
distribution of species ignore interactions [@Urban2016ImpFor]. Changes in
species ranges and phenology will inevitably create spatiotemporal mismatches
and affect encounter rates between species [@Gilman2010FraCom], which will
further shift the distribution of species across space. New interactions will
also appear between species that are not currently co-occuring
[@Gilman2010FraCom]. Only by forecasting how species will interact can we hope
to have an accurate portrait of how biodiversity will be distributed under the
future climate.

Forecasting how climate change will alter biodiversity is also crucial for
maximizing conservation outcomes. Improving SDMs through interactions is crucial
for conservation, as nearly 30% of models in SDM studies are used to assess
population declines or landscape ability to support populations
[@Araujo2019StaDis]. Reliable predictions about how ecological networks will
change over time will give us critical information that could be communicated to
decision-makers and the scientific community about what are future environmental
risks awaiting and how to mitigate them [@Kindsvater2018OveDat]. Not only this,
but how biodiversity is structured influence the functioning of the whole
ecosystem, community stability and persistence [@Thompson2012FooWeb,
@Stouffer2010UndFoo]. Will climate change impact the distribution of network
properties (e.g. connectance)? If so, which regions or species groups need
special conservation efforts? These overarching questions are yet to be answered
[but see @Albouy2013ProCli; @Kortsch2015CliCha; @Hattab2016ForFin]. We believe
that this roadmap towards forecasting ecological networks provide useful
guidelines to ultimately be able to predict more accurately how climate change
will affect the different dimensions of biodiversity and ecosystem functioning.

### How do we turn a predictive model into a forecasting model?

On some scales, empirical time-series encode enough information about ecological
processes for machine-learning approaches to make accurate forecasts. However,
there is an intrinsic limit to the predictability of ecological time-series
[@Pennekamp2019IntPre]. A forecast inherently has a _resolution limit_ in space,
time, and organization. For example, one could never hope to predict the precise
abundance of every species on Earth on every day hundreds of years into the
future. There is often a trade-off between the resolution and horizon of
forecast, *e.g.*, a lower resolution forecast, like primary production will be
at a maximum in the summer, is likely to be true much further into the future
than a higher resolution forecast, like where a specific species will be located
across space. If we want to forecast the structure of ecological networks beyond
the forecasting horizon of time-series based methods, we need forecasts of our
predictive model's inputs--- a forecast of the distribution of both
environmental conditions and the potential species pool across space
(@fig:models).

### How can we validate a forecasting model?

Often the purpose of building a forecasting model to inform _present_ action
[@Dietze2018IteNea]. Yet, the nature of forecasting---trying to predict the
future---is that you can only know if a forecast is "right" once it is too late
to change it. If we want to maximize the chance that "reality" falls within a
forecasting model's predictions, there are two directions to approach this
problem: the first is to extend model validation techniques to a forecasting
context, and the second is to attempt to maximize the amount of uncertainty in a
model without compromising its resolution. Crossvalidation (see _How do we
validate a predictive model?_) can be used to test the efficacy of a forecasting
model. Given a time-series of $N$ observations, a model can iteratively be
trained on the first $n$ time-points of data, and the forecasting model's
accuracy can be evaluated on the remaining time-points it hasn't "seen"
[@Bishop2006PatRec]. This enables us to understand both how much temporal data
is required for a model to be robust, and also enables us to explore the
_forecasting horizon_ of a process. Further, this approach can also be applied
in the opposite temporal direction--- if we have reliable data from the past,
"hindcasting" can also be used to test a forecast's accuracy.

However, these methods inevitably bump into a hard-limitation on what is
feasible for a forecasting model. The future is uncertain. Any empirical
time-series we use to validate a model was collected in past conditions that may
not persist into the future. Any system we wish to forecast will undergo only
one of many possible scenarios, yet we can only observe the realized outcome of
the system under the scenario that actually unfolds. It is therefore impossible
to assess the quality of a forecasting model in scenarios that remain
hypothetical. If the goal is to maximize the probability that reality will fall
within the forecast's estimates, forecasts should incorporate as much
uncertainty about the future scenario as possible. One way to do this is
_ensemble modeling_ which combines forecasts from multiple different models
[@Parker2013EnsMod]. However, as we increase the amount of uncertainty we
incorporate into a forecasting model, the resolution of the forecast's
predictions shrinks, and therefore the modeler be mindful of the trade-off
between resolution and accuracy in any forecasting model.

# Conclusion: why should we predict species interaction networks?

Because we almost can, and because we definitely should.

More accurately, we should invest in network prediction because the right
conditions to do so reliably and rapidly, including forecasting, are beginning
to emerge. Given the possible benefits to a variety of ecological disciplines
that would result from an increased ability to predict ecological networks and
their structure, we feel strongly that the research agenda we outline here
should be picked up by the community. Although novel technologies are bringing
massive amounts of data to some parts of ecology (primarily environmental DNA
and remote sensing, but now more commonly image analysis and bioacoustics), it
is even more important to be intentional about *reconciling* data. This involves
not only the scholarly work of understand the processes that the data encode,
and whether they speak to scales that are compatible, but also the groundwork of
developing pipelines to bridge the ever-expanding gap between "high-throughput"
and "low-throughput" sampling methods. An overall increase in the volume of data
will not result in an increase of our predictive capacity as long as this data
increase is limited to specific aspects of the problem. In the areas we
highlight in @fig:conceptual, many data steps are still limiting: documenting
empirical interactions is natural history work that doesn't lend itself to
systematic automation; expert knowldge is by design a social process that may be
slightly accelerated by text mining and natural language processing (but is not
yet, or not routinely or at scale). These limitations are affecting our ability
to reconstruct networks.

But the tools to which we feed these data, incomplete as they may be, are
gradually getting better; that is, they can do predictions faster, they handle
uncertainty and propagate it well, and they can accomodate data volumes than are
lower than we may expect. It is clear that attempting to predict the structure
of ecological networks at any scale is a methodological and ecological
challenge; yet it will result in qualitative changes in our understanding of
complex adaptive systems, as well as changes to our ability to leverage
information about network structure for conservation decision. It is perhaps
even more important to forecast the structure of ecological networks because it
is commonly neglected as a facet of biodiversity that can (and should) be
managed. In fact, none of the Aichi targets mention biostructure or its
protection, despite this being recognized as an important task
[@McCann2007ProBio], either implicitely or explicitely. Being able to generate
reliable datasets on networks in space or time will make this information more
actionable.

**Acknowledgements:** TS, NF, TP are funded by a donation from the Courtois
*Foundation; FB, NF, and TP are funded by IVADO; FB, GD, NF, and GH are funded
*by the NSERC BIOS² CREATE program; DC, TS, LP, and TP are funded by the
*Canadian Institute of Ecology & Evolution; this research was enabled in part by
*support provided by Calcul Québec (www.calculquebec.ca) and Compute Canada
*(www.computecanada.ca).

# References
