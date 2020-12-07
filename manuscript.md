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

Networks can vary either in their structural properties (e.g. changes in
connectance or degree distribution) or in their composition (e.g. changes in
nodes and links identity). Interestingly, variation in the structural properties
of ecological networks tend to respond mostly to changes in the size of the
network. First, the number of links in ecological networks scales with the
number of species [@MacDonald2020RevLin; @Brose2004UniSpa]. Second, connectance
and size are driving the rest of the structural properties of ecological
networks [@Poisot2014WheEco; @Dunne2002FooStr; @Riede2010ScaFoo].

On a lower level, species turnover in space obviously results in changes in the
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

## How do we predict what the species pool at a particular location is?

The next step in the predictive approach we put forward, starting with networks
prediction, then interactions, is to focus on species themselves. The species
present at a particular site who can interact form the species pool of the
network. A common approach in biogeography to predict whether a species will be
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

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
