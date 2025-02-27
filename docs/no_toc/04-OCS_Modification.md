


# Modifying and creating open case studies

## Learning Objectives

This chapter will cover how to modify the case studies to your own needs using the following methods:  

- Modular case study use with the help of the [OCSdata package](https://github.com/opencasestudies/OCSdata)
- Modifying a case study with [GitHub](https://github.com/opencasestudies) and [RStudio](https://www.rstudio.com/)
- Creating your own case study with our [template](https://github.com/opencasestudies/ocs-bp-template) and [MakeCaseStudies](https://rsconnect.biostat.jhsph.edu/MakeCaseStudies/)

## Modular use

Some educators may find that only certain sections of a case study are relevant to their specific needs. For example, a statistics teacher may want students to practice the skills covered in the data analysis section, but doesn't have time to go through the whole case study. The case studies are designed to allow for such use. This educator and their students may jump right in to any case study section without working through any previous sections. This is made possible because the data files are saved at the end of each section. These data files are made available on the case study's GitHub repository and may also be downloaded with the help of the OCSdata package. See Chapter 2 for more details on the structure and organization of a case study data folder. The table below explains which data sub-folder and package function to use for each case study section.

| Data Folder | Case Study Section | OCSdata Function |
| ----- | -------- | ------ |
| raw | Data Import | `raw_data` |
| imported | Data Exploration, Data Wrangling | `imported_data` |
| wrangled | Data Visualization, Data Analysis | `wrangled_csv`, `wrangled_rda` |
| simpler_import | Data Import | `simpler_import_data` |
| extra | Suggested Homework (?) | `extra_data` |

### Example of Modular Use

The following steps illustrate how one would skip to a specific case study section. The data analysis section from the "Opioids in United States" case study is used for this example, but these directions apply for any section in any case study.

1) Use the table of contents to navigate to the section of interest. Click on the arrow that reads "If you skipped the previous sections click here."

<img src="resources/images/skip_section.gif" title="Moving image (GIF) showing a user skipping to the data analysis section of a case study" alt="Moving image (GIF) showing a user skipping to the data analysis section of a case study" style="display: block; margin: auto;" />

2) Follow the instructions provided to download the data files from the previous section either with OCSdata or manually through GitHub:

2.1) Download with OCSdata:

  2.1.1) First install and load the OCSdata package:
  
  ```r
  install.packages("OCSdata") #only run once to install package
  ```
  
  ```
  ## Installing package into '/usr/local/lib/R/site-library'
  ## (as 'lib' is unspecified)
  ```
  
  ```
  ## Warning: package 'OCSdata' is not available (for R version 4.0.2)
  ```
  
  ```r
  library(OCSdata) #run every new R session to load package
  ```

  2.1.2) Now download the wrangled data into your R environment using the following function command:
  
  ```r
  wrangled_rda("ocs-bp-opioid-rural-urban", outpath = getwd())
  ```
  *This command will download the wrangled data in .RDA format. You may also be downloaded wrangled data in .CSV format by replacing 'wrangled_rda' with 'wrangled_csv'*

  2.1.3) Load the RDA files with the following commands:
  
  ```r
  load(file = here::here("OCS_data", "data", "wrangled", "Annual_opioid_data.rda"))
  load(file = here::here("OCS_data", "data", "wrangled", "county_info.rda"))
  ```

2.2) Manually Download from GitHub:

  2.2.1) Download the .RDA files available on the case study GitHub repository from [here](https://github.com/opencasestudies/ocs-bp-opioid-rural-urban/tree/master/data/wrangled)

  *The CSV versions of the files may also be downloaded here, if preferred*

  2.2.2) Move the data files from your 'Downloads' folder to your R session's current working directory (you can see what this is with ```getwd()```).

  2.2.3) Load the RDA files with the following commands:
  
  ```r
  load(file = here::here("Annual_opioid_data.rda"))
  load(file = here::here("county_info.rda"))
  ```

3) All the data you need to work through the current section is now loaded into your environment. You are ready to work through the section of interest, without needing to work through any of the previous sections.

## Modify a case study

The case studies are written in [R Markdown](https://rmarkdown.rstudio.com/) documents and developed within an RStudio project. R Markdown documents are denoted with the file extension ".Rmd" and allow for the inclusion of code chunks and outputs in a written report. They are written using Markdown syntax (avocado$). RStudio projects are used to organize the case studies and support version control (is this correct?). The [knitr](https://yihui.org/knitr/) package "knits" the case study written in R Markdown and outputs the document as an HTML file. Open Case Studies uses these HTML files to post the case studies online. The entire case study project is contained in a GitHub repository which allows for easy distribution and version control. [GitHub Pages](https://pages.github.com/) is used to host the case study webpage from the case study repository.

$ do we have any resources for markdown we prefer to use?

Modifying a case study requires the following simple steps:

1. Clone or fork the case study repository from GitHub. Clone if you only want to have the repository locally. Fork if you would like to have both a local version and a remote repository on your personal GitHub account.

2. In the repository folder, open the case study .Rproj file to open the project up in RStudio.

3. Edit the sections to be modified in the index.Rmd file.

4. Save your changes, then click on the "Knit" drop down menu in the top left corner of RStudio. Choose which file format you'd like to knit to.

<img src="resources/images/rstudio_modify_knit_red.png" title="Screenshot of RStudio window with Knit button highlighted in red and drop down menu showing. Window also shows the Opioids case study repository with the index.Rmd file opened." alt="Screenshot of RStudio window with Knit button highlighted in red and drop down menu showing. Window also shows the Opioids case study repository with the index.Rmd file opened." style="display: block; margin: auto;" />

5. Distribute your modified case study as you please! (avocado should i add a note here about hosting online with personal GitHub pages?)

*add reference to a resource on GitHub for beginners?

*create a video showing: step by step example of forking a case study repository, editing Rmd content, knitting, and sharing the output

## Create a case study

Open Case Studies offers two options for creating a case study. The first method is a template repository available on GitHub. The second is a new live web application. The first option offers more customization, while the second is much more fast and simple.

### Template Case Study

A template case study is available in a repository on our GitHub page at [github.com/opencasestudies/ocs-bp-template](https://github.com/opencasestudies/ocs-bp-template). This template contains the basic skeletal structure used for our case studies. Creating a new case study with the template is very similar to modifying an existing case study:

1. Clone the template at [opencasestudies/ocs-bp-template](https://github.com/opencasestudies/ocs-bp-template). (avocado should be "click use as template button")

2. Open the index.Rmd file in RStudio.

3. Add the case study content to the index.Rmd file. Use the instructions provided in this file to add different elements such as images and videos.

4. Save your changes and knit the case study to the preferred file format.

5. Distribute the knitted case study as you please!

*avocado create a video showing step by step example of creating case study with template

### MakeCaseStudies App

Open Case Studies now also offers the [MakeCaseStudies](https://rsconnect.biostat.jhsph.edu/MakeCaseStudies/) app as an option for our users to create their own case studies. The app has an easy-to-use interface where users can copy and paste their content into text boxes on the "Create" tab and check the "Preview" tab to see what they’ve made so far. Once satisfied, click the download button to export your finished case study!

*avocado attach/add link to video about app from DELTA symposium

## Session info


```
## R version 4.0.2 (2020-06-22)
## Platform: x86_64-pc-linux-gnu (64-bit)
## Running under: Ubuntu 20.04.3 LTS
## 
## Matrix products: default
## BLAS/LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.8.so
## 
## locale:
##  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C              
##  [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8    
##  [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=C             
##  [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                 
##  [9] LC_ADDRESS=C               LC_TELEPHONE=C            
## [11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] OCSdata_1.0.2
## 
## loaded via a namespace (and not attached):
##  [1] knitr_1.33         magrittr_2.0.2     usethis_2.1.5.9000 hms_0.5.3         
##  [5] R6_2.4.1           rlang_0.4.10       httr_1.4.2         stringr_1.4.0     
##  [9] highr_0.8          tools_4.0.2        xfun_0.26          jquerylib_0.1.4   
## [13] htmltools_0.5.0    ellipsis_0.3.1     ottrpal_0.1.2      yaml_2.2.1        
## [17] digest_0.6.25      tibble_3.0.3       lifecycle_1.0.0    crayon_1.3.4      
## [21] bookdown_0.24      purrr_0.3.4        readr_1.4.0        vctrs_0.3.4       
## [25] fs_1.5.0           glue_1.6.1         evaluate_0.14      rmarkdown_2.10    
## [29] stringi_1.5.3      compiler_4.0.2     pillar_1.4.6       pkgconfig_2.0.3
```
