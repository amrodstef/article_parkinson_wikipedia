# READ ME

## Introduction

- The files, scripts and variables described below refers to an analysis of multidimensional aspects of Parkinson's and Alzheimer's diseases content on Wikipedia. It describes two indexes developed specifically for an submitted article: Multidimensional Content Index and Multidimensional Stability Index.

- All steps were developed in R (version 4.6.1), using RStudio IDE (RStudio version 2026.06.0+242);

- I suggest using a R project (".Rproj" file) as central repository to this scripts, allowing all scripts, graphics and other files to be imported/exported easily to the project directory;

- This repository includes the datasets and R scripts (in Rmarkdown format) used during the analysis, as its resulting graphics and tables;

## Files and folders documentation
```
This Repository/
├── README.md (THIS FILE) 
├── {CREATE .Rproj FILE IN THIS DIRECTORY}
├── article_alzhpark.html
├── article_alzhpark.Rmd
├── data/
│   ├──  input/
│   │    ├── art_references.csv
│   │    └── wiki_diseases.csv
│   └──output/
│        └── results_parkalz_article.csv
└── figures/
    ├── graph01_isolated_variables_pos_bord.png
    ├── graph02_counting_class_pos_bord.png
    └── graph03_parallel_sets_pos_bord.png
```
    
### Files description

- article_alzhpark.Rmd: Rmarkdown file containing the data organization, analysis and visualization scripts;
- article_alzhpark.html: HTML file exported from "article_alzhpark.Rmd";

#### ./data/input:

- art_references.csv: wikipedia references dataset collected for data analysis (details below);
- wiki_diseases.csv: content information on wikipedia articles collected for data analysis (details below);

#### ./data/output:

- results_parkalz_article.csv: resulting table containing both base (from input data) and secondary (from analysis results) variables (details below);

#### ./figures:

- graph01_isolated_variables_pos_bord.png: violin plots of base variables distribution;
- graph02_counting_class_pos_bord.png: horizontal bar plot of both research indexes;
- graph03_parallel_sets_pos_bord.png: parallel sets (or alluvial plot) of languages classification on one of the research indexes;


### Data details:

#### ./input/wiki_diseases.csv
Base variables used in the analysis, regarding content aspects of Wikipedia articles on Parkinson's and Alzheimer's diseases. More information about the data collection are available in: https://github.com/albertoleoncio/parkinson

* Variables:

```
- disease: disease to which the data refers. It can be "Parkinson" or "Alzheimer";
- language: article languages, individually represented to every collected article;category:
- words: numnber of words in Wikipedia articles;
- images: number of images in Wikipedia articles;
- intrawikis: number of intrawikis links in Wikipedia articles;
- sections: number of sections in Wikipedia articles;
- total_edits: total number of edits in Wikipedia articles;
- first_edit: date of first edit (or creation) date of Wikipedia articles;
- last_edit: date of last edit registered in Wikipedia articles;
- unique_editors: number of unique editors/users interacting with edits in Wikipedia articles.
```

#### ./input/art_references.csv
Base variables used in the analysis, regarding referential aspects of Wikipedia articles on Parkinson's and Alzheimer's diseases. More information about the data collection are available in: https://github.com/albertoleoncio/parkinson

* Variables:

```
- disease: disease to which the data refers. It can be "Parkinson" or "Alzheimer";
- language: article languages, individually represented to every collected article;
- category: Wikipedia articcle's category;
- reference: reference information and citation, when available;
- year: reference publication year;
- cctld: country code top-level domain
- doi: "Digital Object Identifier", when available;
- pmid: "PubMed ID", when available.
```

#### ./output/results_parkalz_article.csv:
Resulting data from the analysis. It include both initial and secondary variables, created during the analysis process. More information about the secondary variables and the analysis process can be accessed in "article_alzhpark" files, both .Rmd and the exported .html file.

* Variables:

```
- disease: disease to which the data refers. It can be "Parkinson" or "Alzheimer";
- language: article languages. Here, they are unique, as the data were grouped by the 'language' variable);
- multstabin: stability between the variables "parc_[dimension]", according to article metodology;
- words: number of words in Wikipedia articles (grouped by 'language');
- images: number of images in Wikipedia articles (grouped by 'language');
- intrawikis: number of intrawikis in Wikipedia articles (grouped by 'language');
- sections: number of sections in Wikipedia articles (grouped by 'language');
- total_edits: number of total edits received by Wikipedia articles (grouped by 'language');
- unique_editors: number of unique editors (users) to Wikipedia articles (grouped by 'language');
- tsle: "time since last edit", created from the differences between data collection date and "last_edit" initial variable;
- ref_count: number of references in Wikipedia articles (grouped by 'language');
- ref_idx: referential dimension index;
- nm_ref: "ref_idx" variable normalized to 0 - 1 interval;
- parc_ref: 1, lower, to 5, higher, classification of "ref_idx";
- txt_idx: textual dimension index;
- nm_txt: "txt_idx" variable normalized to 0 - 1 interval;
- parc_txt: 1, lower, to 5, higher, classification of "txt_idx";
- edt_idx: editorial dimension index;
- nm_edt: "edt_idx" variable normalized to 0 - 1 interval;
- par_edt: 1, lower, to 5, higher, classification of "edt_idx";
- multcoin: "[dimension]_idx" arithmetic mean to create Multidimensional Content Index;
- parc_multcoin: 1, lower, to 5, higher, general classification of  "multcoin";
- class_multcoin: labels of Multcoin, according to "parc_multcoin".
```
