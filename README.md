---
output: github_document
---



<!-- README.md is generated from README.Rmd. Please edit that file -->



# squire

<!-- badges: start -->
[![Travis build status](https://travis-ci.org/mrc-ide/squire.svg?branch=master)](https://travis-ci.org/mrc-ide/squire)
[![AppVeyor build status](https://ci.appveyor.com/api/projects/status/github/mrc-ide/squire?branch=master&svg=true)](https://ci.appveyor.com/project/mrc-ide/squire)
[![Codecov test coverage](https://codecov.io/gh/mrc-ide/squire/branch/master/graph/badge.svg)](https://codecov.io/gh/mrc-ide/squire?branch=master)
<!-- badges: end -->

squire enables users to simulate models of SARS-CoV-2 epidemics. This is done using an age-structured SEIR model that also explicitly considers healthcare capacity and disease severity. 

## Overview

squire is a package enabling users to quickly and easily generate calibrated estimates of SARS-CoV-2 epidemic trajectories under different control scenarios. It consists of the following:

* An age-structured SEIR model incorporating explicit passage through healthcare settings and explicit progression through disease severity stages.
* The ability to calibrate the model to different epidemic start-dates based on available death data.
* Simulate the impacts of different control interventions (including general social distancing, specific shielding of elderly populations, and more stringent suppression strategies).

If you are new to squire, the best place to start is below, where we detail how to install the package, how to set up the model, and how to run it with and without control interventions. 

## Installation

<i>squire</i> utilises the package ['ODIN'] (https://github.com/mrc-ide/odin) to generate the model. ['ODIN'] (https://github.com/mrc-ide/odin) implements a high-level language for implementing mathematical models and can be installed by running the following command:

```r
install.packages("odin")
```

The model generated using ODIN is written in C and so you will require a compiler to install dependencies for the package and to build any models with ODIN. Windows users should install [Rtools](https://cran.r-project.org/bin/windows/Rtools/).  See the relevant section in [R-admin](https://cran.r-project.org/doc/manuals/r-release/R-admin.html#The-Windows-toolset) for advice.  Be sure to select the "edit PATH" checkbox during installation or the tools will not be found.

The function `odin::can_compile()` will check if it is able to compile things, but by the time you install the package that will probably have been satisfied.

After installation of ODIN, ensure you have the devtools package installed by running the following:

``` r
install.packages("devtools")
```
Then install the <i>squire</i> package directly from GitHub by running:

``` r
devtools::install_github("mrc-ide/squire")
Note: do we need to refer to a specific branch here? 
```
If you have any problems installing then please raise an issue on the <i>squire</i> [`GitHub`](https://github.com/mrc-ide/squire/issues). 

If everything has installed correctly, we then need to load the package: 
``` r
library(squire)
```

## Model Structure

### Overall Structure

<img src="https://github.com/mrc-ide/squire/blob/healthcare_capacity/images/Explicit_Healthcare_Model_Structure.JPG" align="center" style = "border: none; float: center;" width = "600px">

squire uses an age-structured SEIR model, with the infectious class divided into different stages reflecting progression through different disese severity pathways. These compartments are:  
* S = Susceptibles  
* E = Exposed (Latent Infection)  
* I<sub>Mild</sub> = Mild Infections (Not Requiring Hospitalisation)  
* I<sub>Case</sub> = Infections Requiring Hospitalisation  
* I<sub>Hospital</sub> = Hospitalised (Requires Hospital Bed)  
* I<sub>ICU</sub> = ICU (Requires ICU Bed)  
* I<sub>Rec</sub> = Recovering from ICU Stay (Requires Hospital Bed)  
* R = Recovered  
* D = Dead  

### Decision Trees for Healthcare Capacity 
<img src="https://github.com/mrc-ide/squire/blob/healthcare_capacity/images/Explicit_Healthcare_Oxygen_Decision_Tree.JPG" align="center" style = "border: none; float: center;" width = "400px">

Given initial inputs of hospital/ICU bed capacity and the average time cases spend in hospital, the model dynamically tracks available hospital and ICU beds over time. 

Individuals newly requiring hospitalisation (either a hospital or ICU bed) are then assigned to either receive care (if the relevant bed is available) or not (if maximum capacity would be exceeded otherwise). Whether or not an individual receives the required care modifies their probability of dying.  

## Getting Started

### Running the Model

### Extracting Relevant Outputs 

### Calibrating the Model to Observed Deaths Data

###

