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

You can install squire from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("mrc-ide/squire")
```
Note: do we need to refer to a specific branch here? 

## Model Structure

![Model Structure](/images/Explicit_Healthcare_Model_Structure.JPG | width = 200)