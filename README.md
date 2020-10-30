## TODO

- [ ] Edit `metadata.json` - add Authour details
- [ ] Add references to Zotero

## Versions

[master_pdf]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction.pdf
[master_tex]: https://poisotlab.github.io/ms_network_prediction/ms_network_prediction.tex
[master_html]: https://poisotlab.github.io/ms_network_prediction/ndex.html

Different versions of `manuscript.md`.

|                 |            HTML            |             PDF            |        LaTeX source        |
|-----------------|:--------------------------:|:--------------------------:|:---------------------------:|
| `master` (main)| [:blue_book:][master_html] | [:notebook_with_decorative_cover:][master_pdf] | [:notebook:][master_tex] |

## Markdown Primer

### Citations

This is a citation: `@HampAnde15`
we can also have citations in brackets: `[@HampAnde15]`.

### Equations

There is an equation, which we can cite with `{@eq:eq1}`.

`$$J'(p) = \frac{1}{\text{log}(S)}\times\left(-\sum p \text{log}(p)\right)$$ {#eq:eq1}`

### Figures

`![This is the legend of the figure](figures/biomes.png){#fig:biomes}`

We can refer to `+@fig:biomes.`