## TODO

- [ ] Edit `metadata.json` - add author details
- [ ] Add references to Zotero

## MS formats

[master_pdf]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction.pdf
[master_tex]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction.tex
[master_html]: https://poisotlab.github.io/ms_network_prediction/index.html

|                 |            HTML            |             PDF            |        LaTeX source        |
|-----------------|:--------------------------:|:--------------------------:|:---------------------------:|
| `manuscript.md`| [:blue_book:][master_html] | [:notebook_with_decorative_cover:][master_pdf] | [:notebook:][master_tex] |

## Outline and Task Assignments

[link](https://docs.google.com/document/d/11nR25KtaiusAFkq4NFGnuihsQQN6c0xX-dZskIlQQn0/edit?usp=sharing) to original GoogleDoc

* Meta **[Tanya :paw_prints: + Laura]**
  - *BOX 1: Biological Examples* **[Dom]**
  - What is the paper about? **[Tim]**
  - Who would benefit from it? **[Laura]**
  - Why do we need to predict interactions between species? **[Norma + Gracielle]**
  - Why predict networks before interactions? **[Michael]**
  - What is currently limiting our ability to predict network structure? **[Tanya :paw_prints: + Francis]**
  - What is currently enabling our ability to predict network structure? **[Francis]**
  - *Conceptual figure*
* A primer on predictive (network) ecology **Michael + Tim]**
  - What are the most important properties of networks to predict? **[Norma + Tim]**
  - What is the added value of using machine learning? **[Francis]**
  - How do we fit a predictive model? **[Gab]**
  - How do we validate a predictive model? **[Michael]**
  - How do we propagate uncertainty through a predictive model? **[Michael + Francis + Laura]**
  - How do we determine what interaction networks are feasible? **[Tanya :paw_prints: + Michael]**
* Interactions **[Tanya :paw_prints: + Tim]**
  - *Box 2: Machine Learning Illustration* **[Tim]**
  - What is a species interaction? **[Tanya :paw_prints: + Ben]**
  - How do we predict how species that have never co-occurred will interact? **[Dom + Gracielle]**
  - What does interaction strength mean? **[Ben]**
  - How are interaction strengths actually inferred? **[Ben + SeNd HeLp]**
  - Could we use hypergraphs and multi-layer networks to predict more interactions? **[Norma + Tim]**
* Network predictions must have a spatial component **[Michael + Laura]**
  - *Everything is connected figure*
  - How much do networks vary over space? **[Dom]**
  - How do we predict what the species pool at a particular location is? **[Gab]**
  - How could predictions for individual species, such as those used by IPBES/IUCN, be improved by considering ecological interactions? **[Gab]**
  - What is the spatial scale suitable for the prediction of species interactions? **[Gracielle]**
* Giving a temporal component to network predictions requires forecasting **[Michael + Laura]**
  - *Box 3: Forecasting* **[Michael]**
  - What data do we need to turn a predictive model into a forecasting model? **[Laura]**
  - How can we validate a forecast, and would hindcasting help? **[Michael + Dom]**
  - What ecological knowledge would forecasting bring? **[Dom]**

## A Markdown Primer

### Citations

This is a citation: `@HampAnde15`

We can also have citations in brackets: `[@HampAnde15]`.

### Equations

There is an equation, which we can cite with `{@eq:eq1}`.

`$$J'(p) = \frac{1}{\text{log}(S)}\times\left(-\sum p \text{log}(p)\right)$$ {#eq:eq1}`

Inline eq. look like this `$\mathbf{U}\cdot\mathbf{\Sigma}\cdot\mathbf{V}^T$`
### Figures

`![This is the legend of the figure](figures/conceptual.png){#fig:conceptual}`

We can refer to `+@fig:biomes.`

`@fig:biomes.` will only give fig number + hyperlink
