
# datazoom.amazonia

datazoom.amazonia is an R package that facilitates access to official data regarding the Amazon. The package provides functions that download and pre-process selected datasets. Currently we support:
* INPE - PRODES: deforestation by municipality
* INPE - DEGRAD: degradation by municipality
* INPE - DETER: deforestation warnings by municipality
* MDIC - COMEX: exports and imports by municipality or state
* IBGE - PIB-Munic: gdp by municipality
* IBGE - SIGMINE: mining area by municipality or state
* MAPBIOMAS - land covering by municipality or state
* IBAMA - environmental fines and infractions by municipality or state

<!-- badges: start -->
[![R build status](https://github.com/datazoompuc/datazoom.amazonia/workflows/R-CMD-check/badge.svg)](https://github.com/datazoompuc/datazoom.amazonia/actions)
<!-- badges: end -->

## Installation
The package can be installed using `devtools` like so:

```
if(!require(devtools)) install.packages("devtools")
devtools::install_github("datazoompuc/datazoom.amazonia")
```

## Usage for INPE data

```
library(datazoom.amazonia)

# Downloads data

data <- load_prodes(c(2018, 2019))

data <- load_degrad(2016)

data <- load_prodes(2017, space_aggregation = "state", language = "pt")

data <- load_deter("amazonia", space_aggregation = "state",
                   time_aggregation = "year", language = "pt")

# Loads data locally

data <- load_prodes("~/Downloads")

data <- load_deter("~/Downloads")

```

## Usage for COMEX data

```
# Downloads data

years <- c(2000:2009)

data <- load_comex(years, ncm = TRUE, exp = TRUE, imp = TRUE)

```

## Usage for IBGE data

```
##PIB-Munic

data <- load_amazon_gdp(c(2014, 2015))

data <- load_amazon_gdp(2017, space_aggregation = "state", language = "pt")

##SIGMINE

data <- load_sigmine(space_aggregation = 'municipality')

```

## Usage for MAPBIOMAS data

```
# Downloads data

data <- load_mapbiomas_covering(space_aggregation = 'municipality', path = NULL, code_state = "PA", code_mun = NULL, covering = 3,
                                  type = 'stacked', year_begin = 2000, year_end = 2010)

data <- load_mapbiomas_transition(transition_interval = 5)

# Loads data locally

data <- load_mapbiomas_covering("~/Downloads")

data <- load_mapbiomas_transition("~/Downloads")

##IBAMA

# Downloads data

data <- load_ibama(
                   download_directory = getwd(),
                   time_aggregation = "ano",
                   space_aggregation = "municipio", 
                   years = c(2010, 2012),
                   language = "pt")

# Loads data locally

data <-load_ibama(
                  download_data = FALSE,
                  load_from_where = "./Desktop/data.xls",
                  time_aggregation = c("year", "month"),
                  space_aggregation = c("municipality", "state"))


```

## Credits
DataZoom is developed by a team at Pontifícia Universidade Católica do Rio de Janeiro (PUC-Rio), Department of Economics. Our official website is at: http://www.econ.puc-rio.br/datazoom/index.html.
