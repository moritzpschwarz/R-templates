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

### Citations and Bibliography

The template is currently set-up to work perfectly with the [`rbbt` package](https://github.com/paleolimbot/rbbt), which connects Zotero and RStudio. The `.yaml` line  ```bibliography: "`r rbbt::bbt_write_bib('biblio.bib', overwrite = TRUE)`"```  checks the document for any included references (using the `@identifier` logic that is standard across RMarkdown) and then creates a `.bib` file in the same folder as the Rmd file. This is a perfect set-up (for me) because I can use the `rbbt` add-in to RStudio to search my Zotero database and quickly add authors without ever having to export the library in Zotero. 

**Note:**
- Zotero needs to be running when knitting
- I would always use a `.bib` file extension and not a `.json` extension because if your document does not contain any references, the `.bib` file does not crash - the `.json` file crahses, because it requires a certain format (i.e. it would at least require two square brackets `[]` in the file.

If you intend to use a different Reference Management system, please just replace the bibliography with the path to your bibliography file, i.e. `bibliography: bibliography.bib`.

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
