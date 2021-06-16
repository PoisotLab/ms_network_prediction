# Reviewer 1

## Major Points
_Validation (246 – 280):
This section could benefit from comparison of main performance metrics – as used in ML and
subfields, as they are often missing from ecological papers. For instance ROC-AUC,
PR-ROC-AUC, F-score, K-statistics, Cohen’s kappa to mention a few. A way to go about it
would be discussing differences between measures calculated in the sensitivity-specificity
space (e.g., ACC, AUC, TSS), and those calculated in the precision-recall space (e.g.,
PR-AUC, F-score, etc). The former cannot capture the intricacies of imbalanced class/sparse
network problem. You can have a very high TSS and very low F-Score, for instance. The
choice for which metric to tune a predictive model for/select between different models/
algorithms depends on the application of the prediction exercise. These discussions need to
be added to this section to make it 1) correct (see below), and 2) provide an explanation
of these metrics and their utilisation that I think would be invaluable to the community at
large._

**Our changes in response**:
- Table of validation metrics
- ROC-PR curve conceptual figure

_Considering the above, validation of proof of concept/and Figure 4 must be updated to
reflect the different values/natures of these metrics (e.g., in addition to TSS, a metric
from precision-recall space must be shown). The discussion around validation of proof of
concept needs to be expanded with: 1) the additional metrics as per above; and 2) backing
up of why a TSS around 0.5/50% is actually any good; yes, it should undoubtedly be used
instead of accuracy, but what does a roughly around random TSS means? The authors make very
strong claims with regards to their proof of concept which need to be backed up. For
instance, when measured, proof of concept might yield good performance on the PR-metrics,
which could strengthen the argument for it._

**Our changes in response**:
- ROC-PR for proof-of-concept, shows much better than neutral classifier   
- ROC-PR curve conceptual figure

Uncertainties and variations in models’ outcomes must be discussed more prominently. This
is becoming increasingly important, particularly with DL/ML algorithms being prune to
underspecification. For instance, we might train proof of concept 1000 times, changes in
random seeds/sampling/training data might lead to equally-performing trained models
(including on test sets) but which might yield wildly/somewhat different predictions.
Providing means to quantifying this uncertainty is crucial for any predictive (including
on networks) models and it must be discussed. In addition, mentions of different
subsampling techniques and their role/effect on models and their predictions needs to
be mentioned: for instance what might happen if we were to over-sample/under-sample at
random, or within the restrictions of a given network/interaction type/biases in the
underlying data. How can subsampling/bootstrapping be used effectively? And how can
you quantify (to an extent) the uncertainties in underlying data/network structure?

**Our changes in response**:
- we have added a sentence about bootstrapping/monte carlo crossvalidation
- we might add uncertainty to our proof-of-concept ROC-PR curves

_Lines 87-8: in addition, a claim is made that a slight inflation of positive
interactions would overcome existing biases (in relation to imbalanced nature of the
network). This needs to be described in more details, and qualified with evidence
(e.g., sampling metrics), also a discussion must be made in relation to various
subsampling/instance-synthesis techniques, and their effect on the predictions
(as per above). Furthermore, clarification needs to be made if performance metrics
were derived from the raw or the slightly inflated data._

**Our changes in response**:
- we have added a sentence about bootstrapping/monte carlo crossvalidation
- we might add uncertainty to our proof-of-concept ROC-PR curves


_Becker et al 2020: I am aware of this study and its limitations. Here, it is
presented in the same way peer-reviewed studies are (see below), without
discussing those limitations, particularly: 1) Study design – the overall
performance of the final ensemble is significantly worse than some of
components. 2) Lack of any quantification of uncertainties (e.g., as per
discussion above). Overall, the authors cite only two pre-prints, to the
exclusion of other pre-prints that could be useful in this discussion.
Therefore, the authors must either: 1) justify why only those two preprints were
used, 2) expand selection to include additional pre-prints; or 3) remove these
citations. Furthermore, there are few cases where the aforementioned work has
been cited to the exclusion of other peer-reviewed work (e.g., in discussion of
node-embedding: line 365)._

**Our changes in response**:
- idk weird comment



_How do we predict how species that we have never observed together will interact (355-374): there are other ways to incorporate network-structure into models to predict interactions within a given network, such as calculating network-based features, they need to be mentioned here for completeness._

**Our changes in response**:
- we added a sentence on structural network prediction models in addition to
it already being in the conceptual roadmap figure

## Minor Points

_Interaction types: in general the authors allude to various types of interactions such as
those present in food webs, and host-pathogen/parasite interactions. I think more could be
made of these, in relation to uni-, bi- and k-partite networks, and type of interactions:
for instance, in complex k-partite networks, network-based features might prove invaluable
(because they can be computed to quantify indirect interactions in ways that other methods
might not account for)._

**Our changes in response**:
- foo




_Lines 318-340: There are few other models that connect networks/their structures to predict
interactions within the networks/subset of nodes in networks. They need to be sited here._

**Our changes in response**:
- is this motifs?


_Lines 375-397: this section could benefit from discussion of various types of flow in
networks, for instance there are few examples in the literature (needs to be cited), were
authors looked at the concept of flow in subtypes of ecological networks, and its meaning.
Particularly for unipartite ecological networks – flow can be misleading in some scenarios,
and very powerful in others._

**Our changes in response**:
- we discuss this already in feasability section 

_In addition to interaction strength, weighted networks need to be mentioned somewhere, even
if only for completeness._

**Our changes in response**:
- already is


# Reviewer 2
