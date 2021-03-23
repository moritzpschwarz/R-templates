# R-templates
A collection of RMarkdown and R file templates



## Set-up

### Libraries required

- `rmarkdown`
- `knitr`
- To use Word documents: `officedown` (I also needed to install `cachem`)

- For `.lua` files and further information see this [StackOverflow Answer](https://stackoverflow.com/questions/52918716/authors-and-affiliations-in-the-yaml-of-rmarkdown) as well as the relevant GitHub repositories [here](https://github.com/pandoc/lua-filters/tree/master/scholarly-metadata) and [here](https://github.com/pandoc/lua-filters/tree/master/author-info-blocks).

- For the way I create the table of contents in PDF and Word files, see [this blog post](https://www.garrickadenbuie.com/blog/add-a-generated-table-of-contents-anywhere-in-rmarkdown/) by Garrick Aden‑Buie

## Detailed Explanation

### footer

If we want to use a `footer.hmtl`, we need to use the option `self_contained: FALSE` in the `html_document` specification

### Knit Options

  
```r
knit: (function(inputFile, encoding) { 
  rmarkdown::render(inputFile, 
  encoding = encoding, 
  output_format = "all", #other options 'pdf_document','html_document', 'officedown::rdocx_document'
  output_dir = here::here("output")) 
  })
```
