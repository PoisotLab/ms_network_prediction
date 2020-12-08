---
bibliography: [references.bib]
---

# Meta

**BOX 1: Biological Examples**

## Why should we predict and forecast species interaction networks?

Networks of species interactions underpin our understanding of key ecological
processes [@Pascual2006EcoNet; @Heleno2014EcoNet]. Although they have initially
been used to describe the interactions *within* a community, our interest in the
last decade has shifted towards understanding their structure and their
variation over space [@Trojelsgaard2016EcoNet; @Baiser2019EcoRul], and
established network ecology as an important emerging component of biogeography
and macroecology. But our understanding of network structure, and in particular
across space, is limited by the availability of data. Characterizing a network
requires an exhaustive list of species interactions at the sampled location, and
these data remain extremely scarce. This is because sampling ecological
interactions is extremely difficult [@Jordano2016SamNet]; in turn, the
difficulty of sampling interactions can lead to biases in our estimate of
network structure [@deAguiar2019RevBia]. As many ecological systems, ecological
networks have entered their "long now" [@Carpenter2002EcoFut], where
contemporary actions will have long-term, low-predictability consequences,
sometimes over centuries [@Burkle2013PlaInt]. It is therefore imperative to
develop a roadmap that would enable prediction (for the present) and forecasting
(for the future) of network structure [@McCann2007ProBio; @Seibold2018NecMul],
of the processes it encodes [@Thompson2012FooWeb], that can account for the
spatial, temporal, and climate change dimensions [@Burkle2011FutPla]. In this
paper, we adopt a question-driven approach to identify opportunities,
roadblocks, and tools that are part of this research agenda.

## Who would benefit from it?
The ability to reliably predict and forecast species interactions would improve our understanding of how species function within ecosystems and inform conservation efforts for protecting species, communities and ecosystems. Knowledge of species interactions is one of the most severe biodiversity shortfalls [@Hortal2015SevSho], because data collection is tedious, time-consuming and expensive. Predicting these interactions from existing datasets is the only way to have information for the bulk of species interacting in a particular ecosystem, and especially for interactions across the landscape. 

First, these predictions would help unify the fields of community, network, and ecosystem ecology, and, in particular, move the field forward toward a comprehensive but cohesive niche concept [@Gravel2019BriElt], improve the quantification of functional relationships of species [@Dehling2018BriThe; @O’Connor2020UnvThe], re-evaluate meta-communities in light of trophic levels [@Guzman2018TowMul], and enable a new line of research into the biogeography of species interactions [@Massol2017IslBio;Braga2019SpaAna]. Second, having knowledge of species interactions could greatly improve our models for other ecological phenomena. The vast majority of predictions and forecasts are currently made using only environmental variables. We would be much better able to anticipate when a species will be able track its climate niche or tolerate a changing climate if we also knew the antagonistic or facilitative relationships with other species in the area. Even process-based ecosystem models [ref] could include much more detailed information on how elements of those ecosystems (species) interact. Third, reliable predictions of species interactions are critical for informing ecosystem management[@Harvey2017BriEco] and systematic conservation prioritization [@Pollock2020ProBio], and for anticipating extinctions and their consequences [@McDonald-Madden2016UsiFoo; McWilliams2019TheSta]. Reliable predictions for biodiversity change are increasingly sought after in international conservation programs (e.g. IPBES and GEO BON), and predictions that incorporate species interactions could substantially improve these assessments.



## Why do we need to predict interactions between species?

Ecosystems are build up by a set of species that interact directly or indirectly 
through elements from their common environment. These interactions form complex 
networks that structure ecological communities and maintain ecosystem functions 
[@Landi2018ComSta; @Albrecht2018PlaAni]. The understanding of interactions is 
therefore crucial for ecosystem management, but also for many other aspects of
biodiversity. For instance, it is well known that ecosystem functions lead to
services that are related to basic issues of health and the economy of humans, 
like pathogens transmission, food security, or the availability of freshwater. 
But with a changing world that includes a high rate of biodiversity loss, land 
transformation, and the worldwide increase in temperature, researchers are worried 
about how to protect human lives and improve life quality in different countries, 
having into account the measure of the change in the world in the following years.  

However, we are far from having a comprehensive knowledge about biodiversity,
especially regarding ecological interactions. Although we have seen a growing
number of records for species occurrences, this growth is much slower for
ecological interactions, especially because interactions are hard to capture and
because of forbidden links [@Jordano2016SamNet]. This knowledge gap motivated a
variety of approaches to deal with interactions in ecological research based on
assumptions that are not always true, such as the correlation between
co-occurrence and interaction. Although sometimes this is a valid simplification
to model communities, it is known that co-occurrence is only one of the elements
necessary for an interaction to occur [@Blanchet2020CooNot]. Other elements that
contribute to the realization of an interaction are abundance and traits
matching in space and time, and the combination of these elements allow us to
infer potential from realized interactions and empirical data about populations
[@Poisot2016StrPro]. 

Because interactions carry a lot of ecological and evolutive information about
biodiversity, predicted links can help us to have a more complete framework to
understand processes and future rearrangements of nature. Moreover,
using reliable current data for making predictions about how ecosystems will 
change over time will give us stronger arguments that could be communicated 
to decision-makers and the scientific community about what are future environmental 
risks awaiting and how to mitigate them [@Kindsvater2018OveDat].

## Why predict networks and interactions at the same time?

Ecological networks are quite sparse [@MacDonald2020RevLin]---composed of a set of interactions, but also a larger set of non-interactions.
If we aim to predict the structure of networks from the "bottom-up"---
by considering each pairwise combination of $S$ different species---we are left with $S^2$ interaction values to estimate. Instead, we can use our existing understanding of the mechanisms that structure ecological networks to widdle down the set of feasible adjacency matrices, thereby reducing the amount of information we must predict, and making the problem of predicting interactions less daunting.

The processes that structure ecological networks do not only occur at the scale of interactions---there are also processes at the network level which  limit what interactions are possible.
The realized structure of a network is the synthesis of the interactions forming the basis for network structure, and the network structure refining the possible interactions---"Part makes whole, and whole makes part" [@Levins1987DiaBio].

## What is currently limiting our ability to predict network structure?

Predicting the structure of ecological networks is dependent on species interactions data,
but species interactions are challenging to sample
comprehensively [@Bennett2019PotPit; @Jordano2016SamNet] and sampling methodology
matters [@deAguiar2019RevBia]. This leads to a scarcity of data that can limit the range of computational tools usable by network ecologists. Most deep learning methods, for instance, are very data expensive. This paucity of data is compounded by
a collection of biases that can be found in existing datasets. Species interaction
datasets are typically dominated by food webs, pollination, and host-parasite networks
[@Ings2009EcoNet; @Poisot2020EnvBia].
This could prove to be a limiting factor when trying to understand or predict
networks of *under represented* interaction types or trying to integrate
different network types [@Fontaine2011EcoEvo], especially given the structural variation of
ecological networks [@Michalska-Smith2019TelEco]. Spatial biases in data coverage are
prevalent at the global scale (with South America, Africa and Asia being under
represented) and different interaction types show biases towards different biomes (or
environmental conditions) [@Poisot2020EnvBia].
These 'spatial gaps' serve as a limitation to our ability to confidently make
predictions when accounting for real-world environmental conditions, especially when
encountering environments for which there are no analogous data. This stresses the need for an integrated, flexible, and data-efficient set of computational tools which will allow us to predict ecological networks accurately from existing and imperfect datasets.  

We are also currently limited by the level of detail at which we can describe ecological networks, *i.e.* the level of organisation. For instance, our
understanding of individual based networks [see for example @Araujo2008NetAna; @Tinker2012StrMec] is still in its infancy
[@Guimaraes2020StrEco] and acts as a 'lower-limit' at which we
would be able to predict networks. On the note of scale, the resolution of
environmental (or landscape) data would also limit our ability to predict
networks at finer scales, although current trends in e.g. remote sensing would
suggest that with time this would become less of a hindrance [@Makiola2020KeyQue].


## What is currently enabling our ability to predict network structure?

The acquisition of biodiversity and environmental data has tremendously 
increased over the past decades thanks to the rise of citizen science 
[@Dickinson2010CitSci] and of novel technology [@Stephenson2020TecAdv], 
including wireless sensors [@Porter2005WirSen], DNA monitoring 
[@Creer2016EcoSF], and satellite remote sensing [@Skidmore2015AgrBio; @Lausch2016LinEar]. 
Standard practices in data integration and quality control [@Kissling2018BuiEss] and in 
Next-generation biomonitoring [NGB; @Makiola2020KeyQue] are being set, with favorable 
consequences on our ability to make reliable predictions of many ecosystem properties 
and components. Open access databases, such as [GBIF](https://www.gbif.org/) (for biodiversity data), 
[NCBI](https://www.ncbi.nlm.nih.gov/) (for taxonomic and genomics data), 
[TreeBASE](https://www.treebase.org/treebase-web/home.html) (for phylogenetics data), 
[CESTE](https://icestes.github.io/) [@Jeliazkov2020GloDat] (for metacommunity ecology 
and species traits data), and [WorldClim](https://www.worldclim.org/data/bioclim.html) 
(for bioclimatic data) contain millions of high-quality data that can be integrated and 
used to monitor and model biodiversity at the global scale. Regarding species interactions 
data, [Mangal](https://mangal.io/#/) is perhaps the most comprehensive open database of 
published ecological networks [@Poisot2016ManMak], whereas 
[GloBI](https://www.globalbioticinteractions.org/about) is an extensive database 
of realized and potential species interactions [@Poelen2014GloBio].

The rise of computing power, along with recent advances in machine learning techniques 
and applications (see @Christin2019AppDee for the use of deep learning in ecology), 
enable us to manipulate a very large number of data from different sources. Accurate 
predictions of ecological networks across space can thus be generated by integrating 
various high-quality, open access datasets, such as the ones archived in the abovementioned 
databases, if we use predictive methods appropriately. Moreover, ongoing developments in 
the field of artificial intelligence are aimed at using deep learning more efficiently in 
low-data regimes [e.g. @Antoniou2018DatAug] and with unbalanced datasets [@Chawla2010DatMin]. 
Considering the current biases in network ecology [@Poisot2020EnvBia] and the scarcity of data 
of species interactions, the prediction of ecological networks will undoubtedly benefit from these improvements. 
The advancement of prediction techniques coupled with a movement towards standardising data 
collection protocols (e.g. @Perez-Harguindeguy2013NewHan for plant functional traits) and  
metadata (e.g. [DarwinCore](https://www.tdwg.org)), which would facilitate interoperability and 
integration of datasets, as well as a growing interest at the government level [@Scholes2012BuiGlo] 
paints a positive picture for the prediction of networks in the coming years.

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

## What is the spatial scale suitable for the prediction of species interactions?

# Giving a temporal component to network predictions requires forecasting

**Box 3: Forecasting**

## What data do we need to turn a predictive model into a forecasting model?

## How can we validate a forecast, and would hindcasting help?

## What ecological knowledge would forecasting bring?

# References
