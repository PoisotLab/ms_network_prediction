---
bibliography: [references.bib]
---

# Introduction

Ecosystems *are* interactions --- organisms interact with one-another and
with their environment, either directly or indirectly. Between organisms,
these interactions are assembled in networks of varying complexity, that
drive ecological and evolutionary dynamics, and maintain coexistence,
diversity and ecosystem functioning [@Delmas2018AnaEco; @Landi2018ComSta;
@Albrecht2018PlaAni]. A knowledge of the structure of networks of species
interactions underpin our understanding of numerous ecological processes
[@Pascual2006EcoNet; @Heleno2014EcoNet]. Yet, even basic knowledge of
species interactions (like being able to list them, or guess which ones may
exist) is still one of the most severe shortfalls in biodiversity science
[@Hortal2015SevSho], in large part due to the tedious, time-consuming, and
expensive process of collecting species interaction data. Comprehensively
sampling every possible interaction is not feasible given the sheer number of
species on Earth, and the data we can collect about interactions is biased and
noisy [@deAguiar2019RevBia]. This is then compounded as species interactions
are typically measured as a binary variable---present or absent--- even though
it is evident interactions are not all-or-nothing. Species interactions
occur probabilistically due to variation in species abundances in space
and time [@Poisot2015SpeWhy]. Different types of interactions vary in their
intrinsic predictability (*e.g.* some fungal species engage in opportunistic
saprotrophy [@Smith2017GroEvi], obligate parasites are more deterministic
in their interactions than facultative parasites [@Poisot2013FacObl;
@Luong2019FacPar]). In addition to this variance in predictability, networks
from different systems are structured by different mechanisms. Interaction
networks are embodied in numerous forms: host and parasites, plants and
pollinators, predators and prey, disease and host, and so on, and network
types may require different approaches and methods for prediction.

Still, species interaction networks have entered their "long now"
[@Carpenter2002EcoFut], where anthropogenic change will have long-term,
low-predictability consequences [@Burkle2013PlaInt] for our planet's ecology.
Therefore, our field needs a conceptual path forward toward models that
enable prediction (for the present) and forecasting (for the future) of
species interactions and the networks they form, which accounts for their
spatial and temporal variation [@McCann2007ProBio; @Seibold2018NecMul]. For
example, in disease ecology, predicting potential hosts of novel
disease [*e.g.* wildlife hosts of betacoronaviruses; @Becker2020PreWil;
@Wardeh2021PreMam] has received much attention. Network approaches have
been used for the prediction of dengue [@Zhao2020MacLea], Chagas disease
[@Rengifo-Correa2017UndTra], Rickettsiosis [@Morand2020DisEco], Leishmaniasis
[@Stephens2009UsiBio], and infectious diseases in livestock and wildlife
[@Craft2015InfDis]. Additionally, prediction of interaction networks is a
growing imperative for next-generation biodiversity monitoring, requiring
a conceptual framework and a flexible set of tools to predict interactions
that is explicitly spatial and temporal in perspective [@Edwards2021TroLan;
@Magioli2021DefLea; @Zhang2021PlaBre]. Developing better models for prediction
of these interactions will rely on assimilation of data from many sources,
and the sources for this data may differ depending on the type of interaction
we wish to predict [@Gibb2021DatPro].

Methods for predicting interactions between species exist, but at the moment
are limited in that they are typically based around a single mechanism at a
single scale: position in the trophic niche [@Gravel2013InfFoo;
@Petchey2008SizFor], phylogenetic distance [@Pomeranz2018InfPre;
@Elmasri2020HieBay], functional trait matching [@Bartomeus2016ComFra],
interaction frequency [@Young2021RecPla], or other network properties
[@Terry2020FinMis; @Stock2017LinFil]. These approaches are difficult to
generalise across systems as species interaction networks are the product of
ecological and evolutionary mechanisms interacting across spatial, temporal and
organisational scales. The interwoven nature of these processes imposes
structure on biodiversity data which is invisible when examined only through the
lens of a single scale. Machine learning (ML) methods have enormous potential in
finding this structure [@Desjardins-Proulx2019ArtInt], and have the potential to
be used together with mechanistic models in order to make prediction of
ecological dynamics more robust [@Rackauckas2020UniDif; @Becker2020PreWil].

Here we use a case study to show how machine-learning models can enable
unreasonably effective prediction of species interactions, whereby we
construct a metaweb of host-parasite interactions across space. We then use
this case study to illustrate a roadmap for improving predictions using
open data and machine-learning methods. We then provide a non-exhaustive
primer on the literature on interaction prediction, and identify the tools
and methods most suited for the future of interaction network prediction
models, covering the spatial, temporal, and climatic dimensions of network
prediction [@Burkle2011FutPla]. Adopting more predictive approaches to complex
ecological systems (like networks) will establish a positive feedback loop
with our understanding of these systems [@Houlahan2017PriPre]: the tasks of
understanding and predicting are neither separate nor opposed; instead, ML
tools have the ability to capture a lot of our understanding into working
assumptions, and comparing predictions to empirical data gives us better
insights about how much we ignore about the systems we model.

# A Case Study: Predicting a Host-Parasite Network

The premise of this manuscript is that we can predict interactions between
species. In this section we provide a proof-of-concept, where we use data from
@Hadfield2014TalTwo describing 51 host-parasite networks sampled across space.
In this data not all species co-occur across sites, so there are pairs of
species that may or may not interact for which we have no data. It is possible
that these species have never been observed because of negative associations,
however it is also possible this is only due to random chance as to which species
are observed.

Without any species-level information, we resort to using co-occurrence to
predict interactions. To do this we (i) extract features for each species
based on co-occurrence, (ii) use these features to train a neural network
to predict interactions, and (iii) apply this classifier to the original
features to predict possibly missing interactions across the entire species
pool. The outputs of the analysis are presented in @fig:example, and the code
to reproduce it is available at `https://osf.io/6jp4b/`; the entire example
was carried out in *Julia 1.5.3* [@Bezanson2017JulFre], using the *Flux*
machine learning framework [@Innes2018FluEle].

We first aggregate all species into a co-occurrence matrix $A$ which
represents whether a given pair of species $(i,j)$ was observed coexisting
across any location. We then transform this co-occurrence
matrix $A$ via probabilistic PCA [@Tipping1999ProPri] and use the first 15
values from this PCA as the features vector for each species $i$. For each pair
of (host, parasite) species $(i,j)$, we then feed the features vectors $(v_i,
v_j)$ into a neural network. The neural network uses four feed-forward layers
(the first $\text{RELU}$, the rest $\sigma$) with appropriate dropout rates
($0.5$). This produces an output layer which is the probability-score for
interaction between species $i$ and $j$.

We then train this neural network by dividing the original dataset into
test and training sets (split 80-20 for training and testing respectively).
During the training of this neural network, the
batches of 64 items used for training were constrained to have at least 25%
of positive interactions, as @Poisot2021ImpMam show slightly inflating
the dataset with positive interactions enables us to counterbalance
sampling biases. Furthermore, setting a minimum threshold of response
balance is an established approach for datasets with strong biases
[@Lemaitre2017ImbPyt]. Validating this model on the test data shows our
model provides highly effective prediction of interactions between pairs of
species not present in the training data (@fig:example).

![Proof-of-Concept: An empirical metaweb [from @Hadfield2014TalTwo], *i.e.* a
list of known possible interactions within a species pool, is converted into
latent features using probabilistic PCA, then used to train a deep neural
network to predict species interactions. The imputed networks are represented as
their t-distributed stochastic neighbour embedding (tSNE) embedding, and the
colours of nodes are the cluster to which they are assigned based on a $k$-means
clustering of the tSNE output. Empirical interactions are shown in purple, and
imputed interactions in grey. Panels A and B represent, respectively, the ROC
curve and the precision-recall curve, with the best classifier (according to
Youden's J) represented by a black dot. The expected performance of a neutral
"random-guessing" classifier is shown with a dashed
line.](figures/figure1.png){#fig:example}

This case study shows that a simple neural network can be very effective in
predicting species interactions even without additional species-level data.
Applying this model to the entire dataset (including species pairs never
observed to co-occur) identified 1546 new possible interactions -- 746
(48%) of which were between pairs of species for which no co-occurrence
was observed in the original dataset. This model reaches similar levels of
predictive efficacy as previous studies that use far more species-level data
and mechanistic assumptions [@Gravel2013InfFoo], which serves to highlight the
potential for including external sources of data for *improving* our prediction
of interaction networks even further. For example, @Krasnov2016TraPhy collected traits
data for this system that could be added to the model, in addition or in
substitution to latent variables derived from observed interactions.

# Predicting species interaction networks across space: challenges and opportunities

Here we present a conceptual roadmap (@fig:conceptual), which we envisage to
be the path towards improving our prediction of species interaction networks,
and developing spatially explicit models of network structure. We discuss
the challenges and opportunities going forward for this research agenda,
and highlight two specific areas where it can have a strong impact: the
temporal forecasting of species interaction networks structure, and the use
of predicted networks for applied ecology or conservation biology.

![A conceptual roadmap highlighting key areas for the prediction of ecological
networks. Starting with the input of data from multiple sources, followed by
a modelling framework for ecological networks and the landscape, which are
then ultimately combined to allow for the prediction of spatially explicit
networks.](figures/concept_v6.png){#fig:conceptual}

## Challenges: the many constraints on prediction

### Ecological network data are scarce and hard to obtain

At the moment, we are primarily limited by the availability of data. Although
we have seen a growth in species occurrence data, this growth is much slower
for ecological interactions because species interactions are challenging to
sample comprehensively [@Bennett2019PotPit; @Jordano2016SamNet] and sampling
methodology has strong effects on the resulting data [@deAguiar2019RevBia]. In
turn, the difficulty of sampling interactions can lead to biases in our
understanding of network structure [@deAguiar2019RevBia]. This knowledge
gap has motivated a variety of approaches to deal with interactions in
ecological research based on assumptions that do not always hold, such as
the assumption that co-occurrence is equivalent to meaningful interaction
strength, when it is known that co-occurrence is not the only prerequisite
for an interaction to occur [@Blanchet2020CooNot]. Spatial biases in data
coverage are prevalent at the global scale (with South America, Africa and
Asia being under-represented) and different interaction types show biases
towards different biomes [@Poisot2021GloKno]. These "spatial gaps" serve as
a limitation to our ability to confidently make predictions when accounting
for real-world environmental conditions, especially in environments for
which there are no analogous data.

Further, empirical estimation of interaction _strength_ is highly prone
to bias as existing data are usually summarised at the taxonomic scale of
the species or higher, thereby losing information that differentiates the
strength in per-individual interactions from the strength of a whole species
interaction [@Wells2013SpeInt]. Empirical estimations of interaction strength
are still crucial [@Novak2008EstNon], but are a hard task to quantify in
natural communities [@Wootton1997EstTes; @Sala2002ComDis; @Wootton2005MeaInt],
especially as the number of species composing communities increases, compounded
by the possibility of higher-order interactions or non-linear responses in
interactions [@Wootton2005MeaInt]. Further, interaction strength is often
variable and context dependent and can be influenced by density-dependence
and spatiotemporal variation in community composition [@Wootton2005MeaInt].

### Powerful predictive tools work better on large data volumes

This scarcity of data limits the range of computational tools that
can be used by network ecologists. Most deep learning methods, for
instance, are very data expensive. The paucity of data is compounded by
a collection of biases in existing datasets. Species interaction data are
typically dominated by food webs, pollination, and host-parasite networks
[@Ings2009EcoNet; @Poisot2020EnvBia]. This could prove to be a limiting
factor when trying to understand or predict networks of underrepresented
interaction types or when trying to integrate networks of different types
[@Fontaine2011EcoEvo], especially given their inherent structural variation
[@Michalska-Smith2019TelEco]. This stresses the need for an integrated,
flexible, and data-efficient set of computational tools which will allow us to
predict ecological networks accurately from existing and imperfect datasets,
but also enable us to perform model validation and comparison with more
flexibility than existing tools. We argue that @fig:example is an example of
the promise of these tools *even* when facing datasets of small size. When
carefully controlling for overfitting, machine learning systems are at least
adequate at generalising. The ability to extract and engineer features also
serves to bolster our predictive power. Although it may be tempting to
rely on approaches like bootstrapping to estimate the consistency of the
predictions, the low data volume, and the fact that we are more likely to
observe interactions between some pairs of species (*i.e.* those that co-occur
a lot, *e.g.* @Cazelles2015TheSpe, and those that reach high abundances,
*e.g.* @Vazquez2009UniPat), introduces a significant risk to train models on
pseudo-replicated data. In short, the current lack of massive datasets must
not be an obstacle to prediction; it is an ideal testing ground to understand
how little data is sufficient to obtain actionable predictions, and how much
we can rely on data inflation procedures to reach this minimal amount.

### Scaling-up predictions requires scaled-up data

We are also currently limited by the level of biological organisation
at which we can describe ecological networks. For instance, our
understanding of individual-based networks [*e.g.* @Araujo2008NetAna;
@Tinker2012StrMec] is still in its infancy [@Guimaraes2020StrEco] and acts as
a resolution-limit. Similarly, the resolution of environmental (or landscape)
data also limits our ability to predict networks at small scales, although
current trends in remote sensing would suggest that this will become less of
a hindrance with time [@Makiola2020KeyQue]. Ecosystems are a quintessential
complex-adaptive-system [@Levin1998EcoBio] with a myriad of ways in which
processes at different spatial, temporal, and organisational scales can
influence and respond to one another. Understanding how the product of these
different processes drive the properties of ecosystems across different scales
remains a central challenge of ecological research, and we should strive to
work on methods that will integrate different empirical "snapshots" of this
larger system.

## Opportunities: the emerging ecosystem of open tools and data

The acquisition of biodiversity and environmental data has tremendously
increased over the past decades thanks to the rise of citizen science
[@Dickinson2010CitSci] and of novel technology [@Stephenson2020TecAdv],
including wireless sensors [@Porter2005WirSen], next-generation DNA sequencing
[@Creer2016EcoSF], and remote sensing [@Skidmore2015AgrBio; @Lausch2016LinEar].
Open access databases, such as [GBIF](https://www.gbif.org/) (for biodiversity
data), [NCBI](https://www.ncbi.nlm.nih.gov/) (for taxonomic and genomics
data), [TreeBASE](https://www.treebase.org/treebase-web/home.html)
(for phylogenetics data), [CESTE](https://icestes.github.io/)
[@Jeliazkov2020GloDat] (for metacommunity ecology and species traits data),
and [WorldClim](https://www.worldclim.org/data/bioclim.html) (for bioclimatic
data) contain millions of data points that can be integrated to monitor
and model biodiversity at the global scale. For species interactions data,
at the moment [Mangal](https://mangal.io/#/) is the most comprehensive
open database of published ecological networks [@Poisot2016ManMak],
and [GloBI](https://www.globalbioticinteractions.org/about) is an
extensive database of realised and potential species interactions
[@Poelen2014GloBio]. Developing standard practices in data integration
and quality control [@Kissling2018BuiEss] and in next-generation
biomonitoring [NGB; @Makiola2020KeyQue] would improve our ability to
make reliable predictions of ecosystem properties on increasing spatial
and temporal scales. The advancement of prediction techniques coupled
with a movement towards standardising data collection protocols (*e.g.*
@Perez-Harguindeguy2013NewHan for plant functional traits) and metadata (*e.g.*
[DarwinCore](https://www.tdwg.org))---which facilitates interoperability and
integration of datasets---as well as a growing interest at the government
level [@Scholes2012BuiGlo] paints a positive picture for data access and
usability in the coming years.

In turn, this effort is supported by a thriving ecosystem of data sources
and novel tools. Machine learning encompasses a broad variety of techniques
applied with or without human supervision. These techniques can often be
more flexible and perform better than classical statistical methods, and can
achieve a very high level of accuracy in many predictive and classification
tasks in a relatively short amount of time [*e.g.* @Cutler2007RanFor;
@Krizhevsky2017ImaCla]. Increasing computing power combined with
recent advances in machine learning techniques and applications shows
promise in ecology and environmental science (see @Christin2019AppDee
for an overview). Moreover, ongoing developments in deep learning are
aimed at improvement in low-data regimes and with unbalanced datasets
[@Antoniou2018DatAug; @Chawla2010DatMin]. Considering the current biases in
network ecology [@Poisot2020EnvBia] and the scarcity of data of species
interactions, the prediction of ecological networks will undoubtedly
benefit from these improvements. Machine learning methods are emerging
as the new standard in computational ecology in general [@Olden2008MacLea;
@Christin2019AppDee], and in network ecology in particular [@Bohan2017NexGlo],
as long as sufficient, relevant data are available. As many ecological and
evolutionary processes underlie species interactions and the structure of their
ecological networks [*e.g.* @Vazquez2009UniPat; @Segar2020RolEvo], it can be
difficult to choose relevant variables and model species interactions networks
explicitly. A promising application of machine learning in natural sciences
is Scientific-Machine Learning (SciML), a framework that combines machine
learning with mechanistic models [@Chuang2018AdvCon; @Rackauckas2020UniDif].
Many studies have used machine learning models specifically with ecological
interactions. Relevant examples include species traits used to predict
interactions and infer trait-matching rules [@Desjardins-Proulx2017EcoInt;
@Pichler2020MacLea], automated discovery of food webs [@Bohan2011AutDis],
reconstruction of ecological networks using next-generation sequencing
data [@Bohan2017NexGlo], and network inference from presence-absence data
[@Sander2017EcoNet].

# A primer on predicting ecological networks

Below we provide a primer on the background concepts necessary to build
predictive models of species interaction networks, with a focus on using machine
learning approaches in the modelling process.

## Models

### What is a predictive model?

Models are used for many purposes, and the term "model" embodies a wide
variety of meanings in scientific discourse. All models can be thought of
as a function, $f$, that takes a set of inputs $x$ (also called features,
descriptors, or independent variables) and parameters $\theta$, and maps them
to predicted output states $y$ (also called label, response, or dependent
variable) based on the input to the model: $y=f(x,\theta)$.

A given model $f$ can be used for either descriptive or predictive purposes.
Many forms of scientific inquiry are based around using models _descriptively_
(also called inference, the inverse problem, fitting a model, or training a
model) [@Stouffer2019AllEco]. In this context, the goal of using a model is
to estimate the parameters, $\theta$, that best explain a set of empirical
observations, $\{\hat{x}, \hat{y}\}$. In some cases, these parameter values
are themselves of interest (*e.g.* the strength of selection, intrinsic growth
rate, dispersal distance), but in others cases, the goal is to compare a set
of competing models $f_1, f_2, \dots$ to determine which provides the most
parsimonious explanation for a dataset. The quantitative representation of
"effects" in these models---the influence of each input on the output---is
often assumed to be linear, and in the frequentist context, the goal is often
to determine if the coefficient corresponding with an input is non-zero to
determine its "significance" in influencing the outcome.

Models designed for inference have utility---descriptive models of networks
can reveal underlying mechanisms that structure ecological communities,
given a proper null model [@Connor2017UsiNul]. However, in order for ecology
to develop as a predictive science [@Evans2012PreEco], interest has grown
in developing models that are used not just for description of data, but
also for prediction. Predictive models are based in _the forward problem_,
where the aim is to predict new values of the output $y$ given an input $x$
and our estimate value of $\theta$ [@Stouffer2019AllEco]. Because the forward
problem relies on an estimate of $\theta$, then, the problem of inference
is nested within the forward problem (@fig:models).

![The nested nature of developing predictive and forecasting models, showcases
the _forward problem_ and how this relies on a hierarchical structure of the
modelling process. The choice of a specific modelling technique and framework,
as well as the data retained to be part of this model, proceeds directly from
our assumptions about which ecological mechanisms are important in shaping
both extant and future data.](figures/forecasting_v4.png){#fig:models}

### What do you need to build a predictive model?

To build a (Bayesian) predictive model one needs the following: first, **data**,
split into features $\hat{x}$ and labels $\hat{y}$ (@fig:models). Second, a
**model** $f$, which maps features $x$ to labels $y$ as a function of parameters
$\theta$, i.e. $y = f(x, \theta)$. Third, a **loss function** $L(\hat{y}, y)$,
which describes how far a model's prediction $y$ is from an empirical value
$\hat{y}$. Lastly, **priors** on parameters, $P(\theta)$, which describe the
modeller's _a priori_ belief about the value of the parameters. Often an
important step before fitting a model is feature engineering: adjusting and
reworking the features to better uncover feature-label relationships
[@Kuhn2019FeaEng]. This can include projecting the features into a lower
dimensional space, as we did via PCA in the case study. Then, when a model is
fitted (synonymous with parameter inference or the inverse problem, see
@fig:models), a fitting algorithm attempts to estimate the values of $\theta$
that minimises the mean value of loss function $L(\hat{y},y)$ for all labels $y$
in the provided data $Y$. These typically rely on drawing candidate parameter
values from priors and applying some form of Bayesian sampling to generate a
posterior estimate of parameters, $P(\theta | \hat{x}, \hat{y})$.


### How do we validate a predictive model?

After we fit a model, we inevitably want to see how "good" it is. This process
can be divided into two parts: 1) model selection, where the modeller
chooses from a set of possible models and 2) model assessment, where the
modeller determines the performance characteristics of the chosen model
[@Hastie2009EleSta].

In the context of _model selection_, a naïve initial approach is to simply
compute the average error between the model's prediction and the true data we
have, and choose the model with the smallest error---however this approach
inevitably results in _overfitting_. One approach to avoid overfitting is
using information criteria (*e.g.* AIC, BIC, MDL) based around the heuristic
that good models maximise the ratio of information provided by the model
to the number of parameters it has. However, when the intended use-case
of a model is prediction the relevant form of validation is _predictive
accuracy_, which should be tested with _crossvalidation_. Crossvalidation
methods divide the original dataset into two---one which is used to fit the
model (called the _training_ set) and one used to validate its predictive
accuracy on the data that it hasn't "seen" yet (called the _test_ set)
[@Bishop2006PatRec]. This procedure is often repeated across different
test and training subdivisions of the dataset to determine the uncertainty
associated with our measurement due to our choice of test and training sets
[@Arlot2010SurCro], in the same conceptual vein as data bootstrapping.

We still have to define what _predictive accuracy_ means in the context
of interaction network prediction. In the proof-of-concept, we used
a neural-network to perform binary classification by predicting the
presence/absence of an interaction between any two species. There are two
ways for the model to be right: the model predicts an interaction and there
is one (a _true positive_ (TP)), or the model predicts no interaction and
there isn't one (a _true negative_ (TN)). Similarly, there are two ways for
the model to be wrong: the model predicts an interaction which does not exist
(a _false positive_ (FP)), or the model predicts no interaction but it does
exist (a _false negative_ (FN)).

A naïve initial approach to measure how well a model does is _accuracy_,
*i.e.* the proportion of values it got correct. However, consider what we
know about interaction networks: they are often very sparse, with connectance
between $0.1$ and $0.3$. If we build a model that always guesses there will
be no interaction between two species, it will be correct in the majority of
cases because the majority of potential interactions in a network typically
do not exist.  Therefore this "empty-matrix" model would always have an
_accuracy_ of $1-C$, where $C$ is the observed connectance, which would
almost always be greater than 50%. Understanding model performance within
sensitivity-specificity space may be more informative, where sensitivity
evaluates how good the model is at predicting true interactions (True Positive
Rate) and specificity refers to the prediction of true "non-interactions"
(True Negative Rate). It must be noted that in ecological networks,
there is no guarantee that the "non-interactions" (assumed true negatives)
in the original dataset are indeed true negatives [@Jordano2016ChaEco;
@Jordano2016SamNet]. This can result in the positive/negative values, and
the false omission/discovery being artificially worse, and specifically
decrease our confidence in predicted interactions.

In response to the general problem of biases in classifiers, many metrics
have been proposed to measure binary-classifiers (see @tbl:validation,
[@Gu2009EvaMea; @Drummond2006CosCur]) and are indicative of how well the model
performs with regards to some aspect of accuracy, sensitivity, specificity
and/or precision. Ultimately the choice of metric will depend on the
intended use of the model.

| Name                      | Value | Success         | Description                                                   |
|:--------------------------|:------|:----------------|:--------------------------------------------------------------|
| Random accuracy           | 0.56  |                 | Fraction of correct predictions if the classifier is random   |
| Accuracy                  | 0.81  | $\rightarrow 1$ | Observed fraction of correct predictions                      |
| Balanced accuracy         | 0.80  | $\rightarrow 1$ | Average fraction of correct positive and negative predictions |
|                           |       |                 |                                                               |
| True Positive Rate        | 0.77  | $\rightarrow 1$ | Fraction of interactions predicted                            |
| True Negative Rate        | 0.83  | $\rightarrow 1$ | Fraction of non-interactions predicted                        |
| False Positive Rate       | 0.16  | $\rightarrow 0$ | Fraction of non-interactions predicted as interactions        |
| False Negative Rate       | 0.22  | $\rightarrow 0$ | Fraction of interactions predicted as non-interactions        |
|                           |       |                 |                                                               |
| ROC-AUC                   | 0.86  | $\rightarrow 1$ | Proximity to a perfect prediction (ROC-AUC=1)                 |
| Youden's J                | 0.60  | $\rightarrow 1$ | Informedness of predictions (trust in individual prediction)  |
| Cohen's $\kappa$          | 0.58  | $\ge 0.5$       |                                                               |
|                           |       |                 |                                                               |
| Positive Predictive Value | 0.66  | $\rightarrow 1$ | Confidence in predicted interactions                          |
| Negative Predictive Value | 0.89  | $\rightarrow 1$ | Confidence in predicted non-interactions                      |
| False Omission Rate       | 0.10  | $\rightarrow 0$ | Expected proportion of missed interactions                    |
| False Discovery Rate      | 0.33  | $\rightarrow 0$ | Expected proportion of wrongly imputed interactions           |

Table: Overview of the validation statistics applied to the case study,
alongside the criteria indicating a successful classifier and a guide to
interpretation of the values. Taken together, these validation measures
indicate that the model performs well, especially considering that it is
trained from a small volume of data. {#tbl:validation}

In the machine learning literature, a common way of visualising
this extensive list of possible metrics is through the use of ROC
(receiver-operating-characteristic; False Positive Rate on the
x-axis, and True Positive Rate on the y-axis) and PR (precision-recall;
True-Positive-Rate on the x-axis, Positive-predictive-value on the y-axis)
curves (see @fig:example). These curves are generated by considering a continuum of thresholds
of classifier acceptance, and computing the values of ROC/PR metrics for
each value of the threshold. The area-under-the-curve (AUC) is then used as
a validation metric and are typically called AUC-ROC (Area-Under-the-Curve
Receiver-Operator-Curve) and AUC-PR (Area-Under-the-Curve Precision-Recall)
(_e.g._ ROC-AUC in @tbl:validation).


## Networks and Interactions

### What is an interaction, really?

Interactions between species can be conceptualised in a multitude of ways
(mutualistic vs. antagonistic, strong vs. weak, symmetric vs. asymmetric,
direct vs. indirect) [@Jordano2016ChaEco; @Morales-Castilla2015InfBio]. What
is common to all definitions of an interaction is that *at least* one of
the species is affected by the presence of another, either positively or
negatively [@Morales-Castilla2015InfBio]. Networks can be used to represent
a variety of interaction types, including: *unipartite networks*, where each
species can be linked to other species (these are typically used to represent
food webs), *bipartite networks* where there are two pools of species, and
all interactions occur between species in each pool, are typically used for
pairwise interactions (*e.g.* hosts and parasites), and *k-partite networks,*
which serve as a way to expand to more than two discrete sets of interacting
species (*e.g.* some parasitoid webs, seed dispersal networks, and pollination
networks [@Pocock2012RobRes]). These different network types can be leveraged
within the modelling process and may dictate what is the best approach _e.g._
using network-based features for _k-partite networks_ as a means to account
for indirect interactions.

### What about interaction _strength_?

Species interaction networks can also be used as a means to quantify and
understand _interaction strength_. Interaction strength, unlike the qualitative
presence or absence of an interaction, is a continuous measurement which
attempts to quantify the effect of one species on another. This results in
weighted networks representing different patterns of 'flows' between nodes
-- which can be modelled in a variety of ways [@Borrett2019WalPar]. Interaction
strength can generally be divided into two main categories (as suggested by
@Berlow2004IntStr): 1) the strength of an interaction between individuals of
each species, or 2) the effect that changes in one species population has on
the dynamics of the other species. It can be measured as the effect over a
period of time (in the units of biomass or energy flux [@Barnes2018EneFlu;
@Brown2004MetThe]) or the relative importance of one species on another
[@Heleno2014EcoNet; @Berlow2004IntStr; @Wootton2005MeaInt]. One recurring
observation is that networks are often composed of many weak interactions
and few strong interactions [@Berlow2004IntStr]. The distribution of
interaction strength within a network effects its stability [@Neutel2002StaRea;
@Ruiter1995EnePat] and functioning [@Duffy2002BioEco; @Montoya2003FooWeb], and
serves to benefit multi-species models [@Wootton2005MeaInt]. Alternatively,
understanding flow in modules within networks can aid in understanding the
organisation of networks [@Farage2021IdeFlo; @Montoya2002SmaWor] or the
cascading effects of perturbations [@Gaiarsa2019IntStr].

Much like quantifying the occurrence of an interaction, quantifying interaction
_strength_ in the field is challenging. However, in some contexts, interaction
strength can be estimated via functional foraging [@Portalier2019MecPre],
where the primary basis for inferring interaction is foraging behaviour like
searching, capture and handling times. In food-webs, metabolic based models
use body mass, metabolic demands, and energy loss to infer energy fluxes
between organisms [@Yodzis1992BodSiz; @Berlow2009SimPre]. In addition,
food-web energetics models can be incorporated at various resolutions
for a specific network, ranging from individual-based data to more lumped
data at the species level or trophic group, depending on data availability
[@Barnes2018EneFlu; @Berlow2009SimPre].

### Why predict networks and interactions at the same time?

Ecological networks are quite sparse [@MacDonald2020RevLin]---composed of a set
of interactions, but also a larger set of species that do not interact. If
we aim to predict the structure of networks from the "bottom-up"--- by
considering each pairwise combination of $S$ different species---we are
left with $S^2$ interaction values to estimate. Instead, we can use our
existing understanding of the mechanisms that structure ecological networks
to whittle down the set of feasible adjacency matrices, thereby reducing the
amount of information we must predict, and making the problem of predicting
interactions less daunting. The processes that structure ecological networks
do not only occur at the scale of interactions---there are also processes at
the network level which limit what interactions are possible. The realised
structure of a network is the synthesis of the interactions forming the
basis for network structure, and the network structure refining the possible
interactions---"Part makes whole, and whole makes part" [@Levins1987DiaBio].

Another argument for the joint prediction of networks and interactions
is to reduce circularity and biases in the predictions. As an example,
models like linear filtering [@Stock2017LinFil] generate probabilities of
non-observed interactions existing, but do so based on measured network
properties. Some recent models make interaction-level predictions [*e.g.*
@Gravel2019BriElt]; these are not unlike stacked species distribution models,
which are individually fit, but collectively outperformed by joint models
or rule-based models [@Zurell2020TesSpe]. By relying on adequate testing
of model performance of biases (*i.e.* optimising not only accuracy, but
paying attention to measures like false discovery and false omission rates),
and developing models around a feedback loop between network and interaction
prediction, it is likely that the quality of the predicted networks will be
greatly improved compared to current models.

### What network properties should we use to inform our predictions of interactions?

There are many dimensions of network structure [@Delmas2018AnaEco], yet
there are two arguments to support basing network prediction around a single
property: _connectance_ (the ratio of actual edges to possible edges in
the network).  First, connectance is ecologically informative---it relates
to resilience to invasion [@Baiser2010ConDet; @Smith-Ramesh2016GloSyn],
can increase robustness to extinction in food webs [@Dunne2002NetStr],
while decreasing it in mutualistic networks [@Vieira2015SimSto], and
connectance relates to network stability [@Landi2018ComSta]. Second, most
(if not all) network properties covary with connectance [@Poisot2014WheEco;
@Dunne2002FooStr].

Within the network science literature, there are numerous methods
for predicting edges based on network properties (*e.g.* block
models [@Yen2020ComDet] based on modularity, hierarchical models
[@Kawakatsu2021EmeHie] based on embedding, etc.). However, in the context of
species interaction networks, these properties often covary with connectance. As
a result we suggest that using connectance as the primary property of interest
is most likely to be practical to formulate at the moment. We have models
to estimate species richness over space [@Jenkins2013GloPat], and because we
can predict connectance from species richness [@MacDonald2020RevLin], we can
then derive distributions of network properties from richness estimates alone.

### How do we predict how species that we have never observed together will interact?

A neutral approach would assume the probability of an interaction is
only a function of abundance and trait variation would have no
effect [@Poisot2015SpeWhy; @Pichler2020MacLea],
and that the effect of abundances and traits would have no effect
[@Canard2012EmeStr]. However, functional-trait based proxies could enable
better predictions of ecological interactions. Selection on functional
traits could cause interactions to be conserved at some evolutionary scales,
and therefore predictions of interaction could be informed by phylogenetic
analyses [@Davies2021EcoRed; @Elmasri2020HieBay; @Gomez2010EcoInt].
Phylogenetic matching in bipartite networks is consistent across scales
[@Poisot2018IntRet], even in the absence of strong selective pressure
[@Coelho2017NeuBio].

A separate family of methods are based on network embedding (as in the
proof-of-concept). A network embedding projects each node of the network
into a lower-dimensional latent space. This enables us to represent the
structure of a network, which previously required the $S^2$ dimensions
of an adjacency matrix, with a smaller number of dimensions. The position
of each node in this lower dimensional space is then treated as a latent
measurement corresponding to the role of that species in the network [*e.g.*
@Poisot2021ImpMam]. Species close together in the latent space should interact
with similar set of species [@Rossberg2006FooWeb; @Rohr2010ModFoo]. However,
these models are sensitive to sampling biases as they are limited to species
for which there is already interaction data, and as a result a methodological
breakthrough is needed to extend these models to species for which there is
little or no interaction data.

### How do we determine what interaction networks are feasible?

For several decades, ecologists have aimed to understand how networks of many
interacting species persist through time. The diversity-stability paradox,
first explored by @May1974StaCom, shows that under a neutral set of assumptions
ecological networks should become decreasingly stable as the number of species
increases. Yet, in the natural world we observe networks of interactions that
consist of far more species than May's model predicts [@Albouy2019MarFis]. As
a result, understanding what aspects of the neutral assumptions of May's model
are incorrect has branched many investigations into the relationship between
ecological network structure and persistence [@Allesina2012StaCri]. These
assumptions can be split into dynamical assumptions and topological
assumptions.  Topologically, we know that ecological networks are not
structured randomly.  Some properties, like the aforementioned connectance,
are highly predictable [@MacDonald2020RevLin]. Generative models of food-webs
(based on network embeddings) fit empirical networks more effectively
than random models [@Allesina2008GenMod]. These models have long used
allometry as a single-dimensional niche space---naturally we want to
extend this to traits in general. The second approach to stability is through
_dynamics_. Early models of community dynamics rely on the assumption of
linear interaction effects, but in recent years models of bioenergetic
community dynamics have shown promise in basing our understanding of
energy flow in food-webs in the understood relationship between allometry
and metabolism [@Delmas2017SimBio]. An additional consideration is the
multidimensional nature of "stability" and "feasibility" (*e.g.* resilience to
environmental change vs extinctions) [@Dominguez-Garcia2019UnvDim] and how
different disturbances propagate across levels of biological organisation
[@Kefi2019AdvOur; @Gravel2016StaCom]. Recent approaches such as structural
stability [@Saavedra2017StrApp; @Ferrera2016EffCom] allow to think of
network feasibility in rigorous mathematical terms, which may end up as
usable parameters to penalise network predictions.

### What taxonomic scales are suitable for the prediction of species interactions?

If we use different trait-based proxies to predict potential interactions
between species the choice of such proxies should be theoretically
linked to the taxonomic and spatial scale we are using in our prediction
[@Wiens1989SpaSca]. At some scales we can use morphological traits of
co-occurring species to assess the probability of interaction between them
[@Bartomeus2016ComFra]. On broader taxonomic scales we can infer interaction
probability through the phylogenetic distance, assuming that functional traits
themselves are conserved [@Gomez2010EcoInt]. In this case, we can think of
the probability that one species will interact with another as the distance
between them in niche-space [@Desjardins-Proulx2017EcoInt], and this can be
modelled by simulating neutral expectations of trait variation on phylogenetic
trees [@Davies2021EcoRed]. At the narrowest scales, we may be interested in
predicting behavioural traits like foraging behaviour [@Bartomeus2016ComFra],
and at this scale we may need to consider abundance's effect on the probability
of an encounter [@Wells2013SpeInt].

### What about indirect and higher-order interactions?

Although network ecology often assumes that interactions go strictly from one
node to the other, the web of life is made up of a variety of interactions.
Indirect interactions---either higher-order interactions between species,
or interaction strengths that themselves interact --- have gained interest in
recent years [@Golubski2016EcoNet; @Golubski2011ModMod]. One mathematical tool
to describe these situations is hypergraphs: hypergraphs are the generalisation
of a graph, allowing a broad yet manageable approach to complex interactions
[@Carletti2020DynSys], by allowing for particular interactions to occur beyond a
pair of nodes. An additional degree of complexity is introduced by multi-layer
networks [@Hutchinson2019SeeFor]. Multi-layer networks include edges across
"variants" of the networks (timepoints, locations, or environments). These
can be particularly useful to account for the metacommunity structure
[@Gross2020ModMod], or to understand how dispersal can inform conservation
action [@Albert2017AppNet].  Ecological networks are intrinsically
multi-layered [@Pilosof2017MulNat]. However, *prima facie*, increasing the
dimensionality of the object we need to predict (the multiple layers rather
than a single network) makes the problem more complicated. Yet, multi-layer
approaches improve prediction in social networks [@Jalili2017LinPre;
@Najari2019LinPre; @Yasami2018NovMul], and they may prove useful  in
network ecology going forward.

## Space

Although networks were initially used to describe the interactions *within*
a community, interest in the last decade has shifted towards understanding
their structure and variation over space [@Trojelsgaard2016EcoNet;
@Baiser2019EcoRul], and has established network ecology as an important
emerging component of biogeography and macroecology.

### How much do networks vary over space?

Networks can vary across space either in their structural properties (*e.g.*
connectance or degree distribution) or in their composition (identity of
nodes and edges). Interestingly, variation in the structural properties
of ecological networks primarily responds to changes in the size of the
network. The number of links in ecological networks scales with the number of
species [@MacDonald2020RevLin; @Brose2004UniSpa], and connectance and size
drive the rest of network structure [@Poisot2014WheEco; @Dunne2002FooStr;
@Riede2010ScaFoo]. Species turnover in space results in changes in the
composition of ecological networks. But, this is not the only reason
network composition varies [@Poisot2015SpeWhy]. Intraspecific variation
can result in interaction turnovers without changes in species composition
[@Bolnick2011WhyInt]. Similarly, changes in species abundances can lead to
variation in interaction strengths [@Canard2014EmpEva; @Vazquez2007SpeAbu].
Variation in the abiotic environment and indirect interactions
[@Golubski2016EcoNet] could modify the occurrence and strength of individual
interactions. Despite this, empirical networks tend to share a common backbone
[@Mora2018IdeCom] and functional composition [@Dehling2020SimCom] across space.

### How do we predict what the species pool at a particular location is?

As the species pool forms the basis for network structure, predicting which
species are present at a particular location is essential to predict networks
across space. Species distribution models (SDMs) are increasingly ubiquitous
in macroecology--- these models predict the range of a species based on
known occurrences and environmental conditions, such as climate and land cover
[@Guisan2005PreSpe; @Elith2006NovMet]. Including interactions or co-occurrences
in SDMs generally improves predictive performance [@Wisz2013RolBio]. Several
approaches exist to combine multiple SDMs: community assemblage at a particular
site can be predicted either by combining independent single-species SDMs
(stacked-SDMs, SSDMs) or by directly modelling the entire species assemblage
and multiple species at the same time (joint SDMs, JSDMs) [@Norberg2019ComEva].
Building on the JSDM framework, hierarchical modelling of species communities
[@Ovaskainen2017HowMak] has the advantage of capturing processes that
structure communities. Spatially Explicit Species Assemblage Modelling (SESAM)
constrains SDM predictions using macro-ecological models [@Guisan2011SesNew]
--- for example, variation in species richness across space can constrain
assemblage predictions [@DAmen2015UsiSpe].

The next step is to constrain distribution predictions using network
properties. This builds on previous calls to adopt a probabilistic view: a
probabilistic species pool [@Karger2016DelPro], and probabilistic interactions
through Bayesian networks [@Staniczenko2017LinMac]. @Blanchet2020CooNot
argue that the probabilistic view avoids confusion between interactions and
co-occurrences, but that it requires prior knowledge of interactions. This
could potentially be solved through our framework of predicting networks
first, interactions next, and finally the realised species pool.

### How do we combine spatial and network predictions?

In order to predict networks across space, we need to combine multiple
models---one which predicts what the species pool will be at a given
location, and one to predict what interaction networks composed from this
species pool are likely to be (see @fig:conceptual). Both of these models
contain uncertainty, and when we combine them the uncertainty from each
model should be propagated into the combined model. The Bayesian paradigm
provides a convenient solution to this---if we have a chain of models where
each model feeds into the next, we can sample from the posterior of the
input models. A different approach is _ensemble modelling_ which combines
the predictions made by several models, where each model is predicting the
same thing [@Parker2013EnsMod]. Error propagation, an important step in
building any ecological model, describes the effect of the uncertainty of
input variables on the uncertainty of output variables [@Draper1995AssPro;
@Parysow2000EffApp]. @Benke2018ErrPro identifies two broad approaches
to model error propagation: analytically using differential equations or
stochastically using Monte-Carlo simulation methods. Errors induced by the
spatial or temporal extrapolation of data also need to be taken into account
when estimating the uncertainty of a model's output [@Peters2004StrEco].

## Time

### Why should we forecast species interaction networks?

Forecasting species interactions are critical for informing ecosystem
management [@Harvey2017BriEco] and systematic conservation prioritisation
[@Pollock2020ProBio], and for anticipating extinctions and their consequences
[@McDonald-Madden2016UsiFoo; @McWilliams2019StaMul]. Ecological interactions
shape species distributions at both local and broad spatial scales,
and including interactions in SDM models typically improves predictive
performance [@Araujo2007ImpBio; @Wisz2013RolBio; @Pigot2013SpeInt]. However,
these tend to rely on approaches involving estimating pairwise dependencies
based on co-occurrence, using surrogates for biotic-interaction gradients,
and hybridising SDMs with dynamic models [@Wisz2013RolBio]. Most existing
models to predict the future distribution of species ignore interactions
[@Urban2016ImpFor]. Changes in species ranges and phenology will inevitably
create spatiotemporal mismatches and affect encounter rates between species
[@Gilman2010FraCom], which will further shift the distribution of species
across space. New interactions will also appear between species that are not
currently co-occurring [@Gilman2010FraCom]. Only by forecasting how species
will interact can we hope to have an accurate portrait of how biodiversity
will be distributed under the future climate.

Forecasting how climate change will alter biodiversity is also crucial for
maximising conservation outcomes. Improving SDMs through interactions is
crucial for conservation, as nearly 30% of models in SDM studies are used
to assess population declines or landscape ability to support populations
[@Araujo2019StaDis]. Reliable predictions about how ecological networks
will change over time will give us critical information that could
be communicated to decision-makers and the scientific community about
what future environmental risks we are awaiting and how to mitigate them
[@Kindsvater2018OveDat]. Not only this, but how biodiversity is structured
influences the functioning of the whole ecosystem, community stability and
persistence [@Thompson2012FooWeb; @Stouffer2010UndFoo]. Will climate change
impact the distribution of network properties (*e.g.* connectance)? If so,
which regions or species groups need special conservation efforts? These
overarching questions are yet to be answered [but see @Albouy2013ProCli;
@Kortsch2015CliCha; @Hattab2016ForFin]. We believe that the path toward
forecasting ecological networks provides useful guidelines to ultimately
better predict how climate change will affect the different dimensions of
biodiversity and ecosystem functioning.

### How do we turn a predictive model into a forecasting model?

On some scales, empirical time-series encode enough information about
ecological processes for machine-learning approaches to make accurate
forecasts. However, there is an intrinsic limit to the predictability of
ecological time-series [@Pennekamp2019IntPre]. A forecast inherently has a
_resolution limit_ in space, time, and organisation. For example, one could
never hope to predict the precise abundance of every species on Earth on every
day hundreds of years into the future. There is often a trade-off between
the resolution and horizon of forecast, *e.g.*, a lower resolution forecast,
like primary production will be at a maximum in the summer, is likely to be
true much further into the future than a higher resolution forecast. If we
want to forecast the structure of ecological networks beyond the forecasting
horizon of time-series based methods, we need forecasts of our predictive
model's inputs---a forecast of the distribution of both environmental
conditions and the potential species pool across space (@fig:models).

### How can we validate a forecasting model?

Often the purpose of building a forecasting model is to inform _present_ action
[@Dietze2018IteNea]. Yet, the nature of forecasting---trying to predict the
future---is that you can only know if a forecast is "right" once it is too
late to change it. If we want to maximise the chance that reality falls within
a forecasting model's predictions, there are two directions to approach this
problem: the first is to extend model validation techniques to a forecasting
context, and the second is to attempt to maximise the amount of uncertainty
in the forecast without compromising its resolution. Crossvalidation (see
_How do we validate a predictive model?_) can be used to test the efficacy
of a forecasting model. Given a time-series of $N$ observations, a model
can iteratively be trained on the first $n$ time-points of data, and the
forecasting model's accuracy can be evaluated on the remaining time-points
it hasn't "seen" [@Bishop2006PatRec]. This enables us to understand both how
much temporal data is required for a model to be robust, and also enables us
to explore the _forecasting horizon_ of a process. Further, this approach can
also be applied in the opposite temporal direction--- if we have reliable data
from the past, "hindcasting" can also be used to test a forecast's robustness.

However, these methods inevitably bump into a hard-limitation on what is
feasible for a forecasting model. The future is uncertain. Any empirical
time-series we use to validate a model was collected in past conditions that
may not persist into the future. Any system we wish to forecast will undergo
only one of many possible scenarios, yet we can only observe the realised
outcome of the system under the scenario that actually unfolds. It is therefore
impossible to assess the quality of a forecasting model in scenarios that
remain hypothetical. If the goal is to maximise the probability that reality
will fall within the forecast's estimates, forecasts should incorporate as
much uncertainty about the future scenario as possible---one way to do this
is ensemble modelling [@Parker2013EnsMod]. However, as we increase the amount
of uncertainty we incorporate into a forecasting model, the resolution of
the forecast's predictions could shrink [@Lei2017EvaTra], and therefore the
modeller should be mindful of the trade-off between resolution and accuracy
when developing any forecast. Finally, ensemble models are not guaranteed
to give more accurate results: for example, @Becker2020PreWil noted that
the ensemble model outperforms the best-in-class models, which should be
taken as an indication that careful model building and selection is of the
utmost importance when dealing with a problem as complex as the prediction
of species interactions.

# Conclusion: why should we predict species interaction networks?

Because we almost can, and because we definitely should. A better
understanding of species interactions, and the networks they form,
would help unify the fields of community, network, and spatial ecology;
improve the quantification of the functional relationships between species
[@Dehling2018BriElt; @OConnor2020UnvFoo]; re-evaluate metacommunities in
light of network structure [@Guzman2019MulExt]; and enable a new line of
research into the biogeography of species interactions [@Massol2017ChaFou;
@Braga2019SpaAna] which incorporates a synthesis of both Eltonian and
Grinnellian niche [@Gravel2019BriElt]. Further, the ability to reliably
predict and forecast species interactions would inform conservation efforts
for protecting species, communities, and ecosystems.  Integration of species
interactions into the assessment of vulnerability to climate change is a
needed methodological advance [@Foden2016IucSsc]. International panels draw
on models to establish scientific consensus [@Araujo2019StaDis], and they can
be improved through more effective prediction of species distributions and
interactions [@Syfert2014UsiSpe]. Further, recent studies argue for a shift
in focus from species to interaction networks for biodiversity conservation
to better understand ecosystem processes [@Harvey2017BriEco].

We should invest in network prediction because the right conditions to do so
reliably and rapidly, including forecasting, are beginning to emerge. Given
the possible benefits to a variety of ecological disciplines that would result
from an increased ability to predict ecological networks and their structure,
we feel strongly that the research agenda we outline here should be picked up
by the community. Although novel technologies are bringing massive amounts
of data to some parts of ecology (primarily environmental DNA and remote
sensing, but now more commonly image analysis and bioacoustics), it is even
more important to be intentional about *reconciling* data. This involves not
only the work of understanding the processes encoded within data, but also the
groundwork of developing pipelines to bridge the ever-expanding gap between
"high-throughput" and "low-throughput" sampling methods. An overall increase
in the volume of data will not result in an increase of our predictive
capacity as long as this data increase is limited to specific aspects of
the problem. In the areas we highlight in @fig:conceptual, many data steps
are still limiting: documenting empirical interactions is natural history
work that doesn't lend itself to systematic automation; expert knowledge is
by design a social process that may be slightly accelerated by text mining
and natural language processing (but is not yet, or not routinely or at
scale). These limitations are affecting our ability to reconstruct networks.

But the tools to which we feed these data, incomplete as they may be,
are gradually getting better; that is, they can do predictions faster,
they handle uncertainty and propagate it well, and they can accomodate
data volumes that are lower than we may expect [@Pichler2020MacLea]. It is
clear attempting to predict the structure of ecological networks at any
scale is a methodological and ecological challenge; yet it will result
in qualitative changes in our understanding of complex adaptive systems,
as well as changes to our ability to leverage information about network
structure for conservation decision. It is perhaps even more important
to forecast the structure of ecological networks because it is commonly
neglected as a facet of biodiversity that can (and should) be managed. In
fact, none of the Aichi targets mention biostructure or its protection,
despite this being recognised as an important task [@McCann2007ProBio],
either implicitly or explicitly. Being able to generate reliable datasets
on networks in space or time will make this information more actionable.

**Acknowledgements:** We acknowledge that this study was conducted on land
within the traditional unceded territory of the Saint Lawrence Iroquoian,
Anishinabewaki, Mohawk, Huron-Wendat, and Omàmiwininiwak nations. TS,
NF, TP are funded by a donation from the Courtois Foundation; FB, NF, and
TP are funded by IVADO; BM is funded by the NSERC Alexander Graham Bell
Canada Graduate Scholarship and the FRQNT master's scholarship; FB, GD,
NF, and GH are funded by the NSERC BIOS$^2$ CREATE program; GD is funded
by the FRQNT doctoral scholarship; DC, TS, LP, and TP are funded by the
Canadian Institute of Ecology & Evolution; this research was enabled in part
by support provided by Calcul Québec (www.calculquebec.ca) and Compute
Canada (www.computecanada.ca). This work was supported by funding to the
Viral Emergence Research Initiative (VERENA) consortium including NSF BII
2021909. AG and MDC are supported in part by the Liber Ero Chair.

# References
