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

## Why do we need to predict interactions between species?

## Why predict networks before interactions?

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
