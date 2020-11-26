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

In machine learning, a predictive (supervised) model is trained on a dataset
containing an outcome variable which we want to predict (also called label,
response, or dependent variable) and predictor variables (also called features,
descriptors, or independent variables) [@Kuhn2013AppPre; @KuhnTidMod]. Before
fitting the model, the dataset will generally be split into a training and
validation subset. The model learns to predict the outcome from the training
subset, then the fit and model performance are evaluated on the validation set
[@Christin2020GoiFur]. Depending on the type of model, the validation step is
part of the training and the model will keep learning until it reaches a certain
threshold based on the loss function. Fitting and adjusting the model can be
done by adjusting the model parameters depending on the type of model (layer
compositions and network structures for neural networks, number of trees and
splits for tree-based models).

Another important step in predictive modeling is feature engineering, i.e.
adjusting and reworking the predictors to enable models to better uncover
predictor-response relationships [@Kuhn2019FeaEng]. It is also important to
consider that fitting a predictive model must be placed in a bigger frame with
some more steps. For instance, some other general phases of the modeling process
are: exploratory data analysis, model tuning and selection, and model evaluation
[@KuhnTidMod]. Model validation will be discussed in the next section.

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
