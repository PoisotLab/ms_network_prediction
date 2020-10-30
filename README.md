## TODO

- [ ] Add references to Zotero
- [ ] How to update ref list
- [ ] How to do the collaborative writing thing... So pull requests(?)
- [ ] Edit `metadata.json` - add author details (low priority) 

## How to add references

- We use [Zotero](https://www.zotero.org/) for references management - in order to get access to the shared library, give your username to Tim
- We use the [Better BibTeX](https://retorque.re/zotero-better-bibtex/) plugin for citation key generations
- The citation key format we use is meant to convey information on the author, date, year, and title. It must be set in the Better BibTeX preferences as
~~~
[auth:fold][year][title:fold:nopunctordash:skipwords:lower:select=1,1:substring=1,3:capitalize][title:fold:nopunctordash:skipwords:lower:select=2,2:substring=1,3:capitalize]
~~~
- We also use the same package to automatically export the manuscript references to the root of the manuscript folder, using the name `references.bib` - this ensures that everyone will be working from the same set of references

## MS formats

[master_tex]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction.tex
[master_html]: https://poisotlab.github.io/ms_network_prediction/index.html

|                 |            HTML            |        LaTeX source        |
|-----------------|:--------------------------:|:---------------------------:|
| `manuscript.md`| [:blue_book:][master_html]  | [:notebook:][master_tex] |

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

There is an equation, which we can cite with `@eq:eq1`, or we can cite a figure with `@fig:biomes`.

`$$J'(p) = \frac{1}{\text{log}(S)}\times\left(-\sum p \text{log}(p)\right)$$ {#eq:eq1}`

Inline eq. look like this `$\mathbf{U}\cdot\mathbf{\Sigma}\cdot\mathbf{V}^T$`

### Figures

`![This is the legend of the figure](figures/conceptual.png){#fig:conceptual}`
