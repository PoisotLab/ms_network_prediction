## How to add references

- We use [Zotero](https://www.zotero.org/) for references management - in order to get access to the shared library, give your username to Tim
- We use the [Better BibTeX](https://retorque.re/zotero-better-bibtex/) plugin for citation key generations
- The citation key format we use is meant to convey information on the author, date, year, and title. It must be set in the Better BibTeX preferences as
~~~
[auth:fold][year][title:fold:nopunctordash:skipwords:lower:select=1,1:substring=1,3:capitalize][title:fold:nopunctordash:skipwords:lower:select=2,2:substring=1,3:capitalize]
~~~
- We also use the same package to automatically export the manuscript references to the root of the manuscript folder, using the name `references.bib` - this ensures that everyone will be working from the same set of references

## MS formats



[master_draft]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction-copyedit.pdf
[master_preprint]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction-preprint.pdf
[master_html]: https://poisotlab.github.io/ms_network_prediction/

|                 |            HTML            |        LaTeX source        |
|-----------------|:--------------------------:|:---------------------------:|
| `manuscript.md`| [:blue_book:][master_html]  | [:notebook:][master_tex] |

## Original google doc (with core points for all questions)

[link](https://docs.google.com/document/d/11nR25KtaiusAFkq4NFGnuihsQQN6c0xX-dZskIlQQn0/edit?usp=sharing) to original GoogleDoc

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
