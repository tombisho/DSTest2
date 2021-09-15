# DataSHIELD Project Client Environment

This R project template uses the [renv](https://rstudio.github.io/renv/) for setting up a reproducible [DataSHIELD](https://datashield.org/) client side R environment. This allows to use the appropriate DataSHIELD client R packages, matching the selected server-side [DataSHIELD profiles](https://opaldoc.obiba.org/en/latest/admin/rserver.html#datashield-profiles).

The project's R environment includes the following R packages (and their dependencies):

* [DSOpal](https://datashield.github.io/DSOpal/) to connect with [OBiBa Opal](https://www.obiba.org/pages/products/opal/) nodes
* [DSMolgenisArmadillo](https://molgenis.github.io/molgenis-r-datashield/) to connect with [Molgenis Armadillo](https://github.com/molgenis/molgenis-service-armadillo/) nodes
* [DSLite](https://datashield.github.io/DSLite/) to connect with a pure R local node
* [dsBaseClient](http://datashield.github.io/dsBaseClient/) to use the base DataSHIELD functions

## Usage

### Clone this Repository

Start by creating your project source code repository from this template: see instructions in [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template). You could also just download this folder, but it is a good practice to have source code in a version control system (Git).

Read the [Introduction to renv](https://rstudio.github.io/renv/articles/renv.html) vignette to learn the basics of R environment management.

### Open Project in RStudio

1. Open this project in [Rstudio](https://www.rstudio.com/) by selecting the `project.Rproj` file.
2. If reported by *renv* in the R console, run the `renv::restore()` to install the R packages in their specific version (i.e. as described by the `renv.lock` file).

Use `libPaths()` to locate where the R packages are installed.

### Adding a new Dependency

1. Install the R package using `install.packages()` or using [renv::install()](https://rstudio.github.io/renv/reference/install.html) which allows to manage R packages installed from an archived version, a GitHub repository, Bioconductor repository or a local package folder
2. Load the R package in one of your R source code with `library()` (see [R/script.R](https://github.com/datashield/DSProjectTemplate/blob/main/R/script.R) as an example)
3. Run `renv::snapshot()` to save the new R environment in the file `renv.lock` file

### Use Git Branches

Different R environments means different package dependencies, and also potentially different R/DataSHIELD analysis code. In order to maintain/develop different environments in parallel, you can use the Git branches. Upgrading to new versions of dependencies will be facilitated. To make a new branch:

1. Select Git tab and *New Branch* in Rstudio, or command line `git checkout -b branchName`
2. Install/update R packages
3. Update analysis R script to connect to the appropriate DataSHIELD server profiles and to fix any breaking changes
4. Run `renv::snapshot()`
5. Commit changes in Git using Rstudio or command line

See also the vignette [Collaborating with renv](https://rstudio.github.io/renv/articles/collaborating.html).
