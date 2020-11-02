# GLOBIOM-LookupTable

## Index
* [Introduction](#introduction)
* [Lookup-Table structure](#lookup-table-structure)
* [SDG scenario dimensions](#sdg-scenario-dimensions)
* [Regional aggregation](#regional-aggregation)
* [Output variables](#output-variables)
* [Loading the table in R](#loading-the-table-in-r)
* [User guidelines](#user-guidelines)

## Introduction
This dataset provides a model emulation (so called "Lookup-Table") of the [GLOBIOM](https://iiasa.ac.at/web/home/research/GLOBIOM/GLOBIOM.html)-[G4M](https://iiasa.ac.at/web/home/research/researchPrograms/EcosystemsServicesandManagement/G4M.en.html) models with respect to greenhouse gas (GHG) emission reduction potentials from agriculture, forestry and other land use (AFOLU) and land based biomass potentials for bioenergy. The dataset represents a two dimensional scenario matrix combining different carbon price and biomass price trajectories for the Shared Socio-economic Pathway 2 [(SSP2)](https://www.sciencedirect.com/science/article/pii/S0959378016300784) and can be used in other models e.g. energy system models, to develop climate mitigation pathways that explicitly consider impacts/potentials from the land use sector.

Information on the GLOBIOM model can be found [here](https://iiasa.github.io/GLOBIOM). Detailed information on the GLOBIOM-G4M Lookup-Table structure and results are presented our paper ['Land based climate change mitigation potentials within the agenda for sustainable development'](https://iopscience.iop.org/journal/1748-9326) and the accompanying [supplementary material](https://iopscience.iop.org/journal/1748-9326). 

For further questions please contact [Stefan Frank](mailto:frank@iiasa.ac.at)

## Lookup-Table structure
The Lookup-Table represents a combination of 7 biomass price and 12 GHG price  trajectories that have been quantified in GLOBIOM-G4M, yielding in total 84 scenarios. The biomass price for bioenergy production (US$/GJ) and carbon price (US$/tCO<sub>2</sub>eq) increase linearly from 2020 onwwards and reach their maximum in 2100. Prices range from 0 - 60 US$/GJ (BIO00, BIO03, BIO05, BIO08, BIO13, BIO30, and BIO60) and 0 - 3000 US$/tCO<sub>2</sub>eq (GHG000, GHG010, GHG020, GHG050, GHG100, GHG200, GHG400, GHG600, GHG1000, GHG1500, GHG2000, and GHG3000). This approach allows to quantify supply functions where the supplied biomass quantity available for bioenergy is a function of the biomass price and conditional on a GHG price. Vice versa we quantify the cost-efficient AFOLU mitigation potential in the form of a marginal abatement cost curves (MACC) conditional on the biomass demand where the emission reduction is a function of the GHG price converted through global warming potential of the non-CO<sub>2</sub> gases to cover also methane (CH<sub>4</sub>) and nitrous oxide (N<sub>2</sub>O) emissions in addition to carbon dioxide (CO<sub>2</sub>). 

The biomass supply curves and MACCs are highly interdependent, for instance: a biomass price remunerating forest harvest for bioenergy may encourage additional afforestation. This will increase the carbon sink of the forest while at the same time providing more biomass for bioenergy production. The Lookup-Table represents a GLOBIOM-G4M model emulation and provides a comprehensive and detailed response surface for the land use sector that can also be used in other models to explicitly consider dynamics and interlinkages between biomass use and AFOLU emissions but also other important land use related indicators. 

## SDG scenario dimensions
The Lookup-Table has been quantified for two set of scenarios: with- (scenSDGs) and without (scenBASE) consideration of selected SDGs by 2030:

* SDG2 - represented by limiting undernourishment to 1%

* SDG6 - represented by respecting environmental water flow requirements for fresh water ecosystems protection

* SDG12 - represented by reducing livestock calorie intake in overconsuming countries through preference change to 430 kcal/capita/day and halving food waste

* SDG15 - represented by increasing the share of protected areas to 17% and avoiding conversion of biodiversity hot-spots

## Regional aggregation
The Lookup-Table is provided for [5 world regions](https://tntcat.iiasa.ac.at/SspDb/dsd?Action=htmlpage&page=about#regiondefs):

AFR – Middle East and Africa  

ASIA – South, East, and South-East Asia    

LAM – Latin and Central America  

OECD – North America, Europe, Pacific OECD  

REF – Russia, Ukraine and Former Soviet Union  

and a higher resolution including 10 world regions:

|Acronym|Region|Definition| 
|---|---|---|
|CIS|Commonwealth of Independent States|Russia, Ukraine, Former Soviet Union countries|
|EAS|East Asia|China, South Korea, Japan|
|EUR|Europe|European Union, Rest of Europe|
|MAF|Middle East and North Africa|Middle East, Turkey, North Africa|
|NAM|North America|Canada, USA, Mexico, Rest of Central America|
|OCE|Oceania|Australia, New Zealand, Pacific Islands|
|SAM|South America|Argentina, Brazil, Rest of South America|
|SAS|South Asia|India, Rest of South Asia|
|SEA|South East Asia|Indonesia, Malaysia, Rest of South East Asia|
|SSA|Sub-Saharan Africa|South Africa, Eastern Africa, Southern Africa, Western Africa, Congo Basin|

## Output variables
The Lookup-Table contains results with respect to:

|Variable|Unit|Definition| 
|---|---|---|
|Land Cover &#124; Cropland|million ha|Arable land including dedicated energy crops|
|Land Cover &#124; Cropland &#124; Irrigated|million ha|Irrigated arable land|
|Land Cover &#124; Cropland &#124; Energy Crops|million ha|Dedicated energy crops i.e. poplar, willow and miscanthus|
|Land Cover &#124; Forest|million ha|Total forest area|
|Land Cover &#124; Forest &#124; Forestry|million ha|Managed forest area for material or energy use including afforestation|
|Land Cover &#124; Forest &#124; Natural Forest|million ha|Unmanaged forest area including reforestation|
|Land Cover &#124; Forest &#124; Afforestation and Reforestation|million ha|Afforested or reforested|
|Land Cover &#124; Other Natural Land|million ha|Other natural vegetation e.g. savannah |
|Land Cover &#124; Pasture|million ha|Pasture area|
|Emissions &#124; CH4 &#124; Land Use|Mt CH4/yr|Methane emissions from land use|
|Emissions &#124; CH4 &#124; Land Use &#124; Agriculture|Mt CH4/yr|Methane emissions from agriculture|
|Emissions &#124; CH4 &#124; Land Use &#124; Agriculture &#124; Rice|Mt CH4/yr|Methane emissions from rice cultivation|
|Emissions &#124; CH4 &#124; Land Use &#124; Agriculture &#124; AWM|Mt CH4/yr|Methane emissions from manure management|
|Emissions &#124; CH4 &#124; Land Use &#124; Agriculture &#124; Enteric Fermentation|Mt CH4/yr|Methane emissions from enteric fermentation|
|Emissions &#124; CH4 &#124; Land Use &#124; Agricultural Waste Burning|Mt CH4/yr|Methane emissions from crop residue burning|
|Emissions &#124; CH4 &#124; Land Use &#124; Savannah Burning|Mt CH4/yr|Methane emissions from savannah burning|
|Emissions &#124; CO2 &#124; Land Use|Mt CO2/yr|Carbon dioxide emissions/removals from land use|
|Emissions &#124; CO2 &#124; Land Use &#124; Afforestation|Mt CO2/yr|Carbon dioxide emissions/removals from afforestation and reforestation|
|Emissions &#124; CO2 &#124; Land Use &#124; Deforestation|Mt CO2/yr|Carbon dioxide emissions from deforestation|
|Emissions &#124; CO2 &#124; Land Use &#124; Forest Management|Mt CO2/yr|Carbon dioxide emissions/removals from forest management|
|Emissions &#124; CO2 &#124; Land Use &#124; Other LUC|Mt CO2/yr|Carbon dioxide emissions/removals from other land use changes including establishment of dedicated energy crops|
|Emissions &#124; N2O &#124; Land Use|kt N2O/yr|Nitrous oxide emissions from land use|
|Emissions &#124; N2O &#124; Land Use &#124; Agriculture|kt N2O/yr|Nitrous oxide emissions from agriculture|
|Emissions &#124; N2O &#124; Land Use &#124; Agriculture &#124; AWM|kt N2O/yr|Nitrous oxide emissions from manure management|
|Emissions &#124; N2O &#124; Land Use &#124; Agriculture &#124; Cropland Soils|kt N2O/yr|Nitrious oxide emissions from fertilizers & manure applied, crop residues and organic soils|
|Emissions &#124; N2O &#124; Land Use &#124; Agriculture &#124; Pasture|kt N2O/yr|Nitrious oxide emissions from manure dropped on pastures|
|Emissions &#124; N2O &#124; Land Use &#124; Agricultural Waste Burning|kt N2O/yr|Nitrous oxide emissions from crop residue burning|
|Emissions &#124; N2O &#124; Land Use &#124; Savannah Burning|kt N2O/yr|Nitrous oxide emissions from savannah burning|
|Price &#124; Primary Energy &#124; Biomass|US$2000/GJ|Biomass price for bioenergy use|
|Price &#124; Agriculture &#124; Non-Energy Crops and Livestock &#124; Index|Index (2005 = 1)| Price index for crop- and livestock products|
|Price &#124; Agriculture &#124; Non-Energy Crops &#124; Index|Index (2005 = 1)|Crop price index|
|Water &#124; Withdrawal &#124; Irrigation|million m3/yr|Irrigation water use|
|Fertilizer Use &#124; Nitrogen|Tg N/yr|Nitrogen fertilizer use|
|Fertilizer Use &#124; Phosphorus|Tg P/yr|Phosphorus fertilizer use|
|Agricultural Demand|million t DM/yr|Total agricultural demand|
|Agricultural Demand &#124; Food|million t DM/yr|Food demand|
|Agricultural Demand &#124; Food &#124; Crops|million t DM/yr|Food demand crops|
|Agricultural Demand &#124; Food &#124; Livestock|million t DM/yr|Food demand livestock|
|Agricultural Demand &#124; Non-Food|million t DM/yr|Demand for other industrial uses|
|Agricultural Demand &#124; Non-Food &#124; Crops|million t DM/yr|Demand for other industrial uses crops|
|Agricultural Demand &#124; Non-Food &#124; Livestock|million t DM/yr|Demand for other industrial uses livestock|
|Agricultural Demand &#124; Feed|million t DM/yr|Feed demand|
|Agricultural Demand &#124; Feed &#124; Crops|million t DM/yr|Feed demand crops|
|Agricultural Demand &#124; Bioenergy|million t DM/yr|Bioenergy demand|
|Agricultural Demand &#124; Bioenergy &#124; 1st generation|million t DM/yr|Agricultural bioenergy demand from cereals, sugar crops and oilseeds|
|Agricultural Demand &#124; Bioenergy &#124; 2nd generation|million t DM/yr|Agricultural bioenergy demand from energy crops|
|Food Demand|kcal/cap/day|Food consumption|
|Food Demand &#124; Crops|kcal/cap/day|Food consumption crops|
|Food Demand &#124; Livestock|kcal/cap/day|Food consumption livestock|
|Agricultural Production|million t DM/yr|Agricultural production|
|Agricultural Production &#124; Livestock|million t DM/yr|Agricultural production livestock|
|Agricultural Production &#124; Non-Energy Crops|million t DM/yr|Agricultural production non-energy crops|
|Agricultural Production &#124; Energy Crops|million t DM/yr|Agricultural production energy crops|
|Forestry Production &#124; Forest Residues|million t DM/yr|Forestry production logging residues|
|Forestry Demand &#124; Roundwood|million m3/yr|Forestry demand total roundwood for material and energy use|
|Forestry Demand &#124; Roundwood &#124; Wood Fuel|million m3/yr|Forestry demand fuelwood for energy use|
|Forestry Demand &#124; Roundwood &#124; Industrial Roundwood|million m3/yr|Forestry demand industrial roundwood for material and energy use|
|Forestry Production &#124; Roundwood|million m3/yr|Forestry production total roundwood for material and energy use|
|Forestry Production &#124; Roundwood &#124; Wood Fuel|million m3/yr|Forestry production fuelwood for energy use|
|Forestry Production &#124; Roundwood &#124; Industrial Roundwood|million m3/yr|Forestry production industrial roundwood for material and energy use|
|Price &#124; Carbon|US$2000/tCO2eq|Carbon price on CO2, N2O, and CH4 emissions|
|Primary Energy &#124; Biomass|EJ/yr|Total biomass potential for bioenergy|
|Primary Energy &#124; Biomass &#124; Energy Crops|EJ/yr|Biomass potential for bioenergy from energy crops|
|Primary Energy &#124; Biomass &#124; Roundwood harvest|EJ/yr|Biomass potential for bioenergy from roundwood harvest|
|Primary Energy &#124; Biomass &#124; Logging residues|EJ/yr|Biomass potential for bioenergy from forest logging residues|
|Primary Energy &#124; Biomass &#124; Forest industry residues|EJ/yr|Biomass potential for bioenergy from forest industry residues|
|Primary Energy &#124; Biomass &#124; Fuelwood|EJ/yr|Biomass potential for bioenergy from fuelwood|
|Primary Energy &#124; Biomass &#124; Other Solid|EJ/yr|Biomass potential for bioenergy from other sources|

## Loading the table in R

To load the table in R as a tibble and transform it to [tidy data](https://tidyr.tidyverse.org/articles/tidy-data.html), use the following lines of code:
```
library(tidyverse)
dat <- read_csv("globiom_g4m_lookuptable.csv")
dat <- pivot_longer(dat, cols=as.character(seq(2000, 2100, by=10)), names_to="Year")
```

## User guidelines
The Lookup-Table dataset is free to use under the [CC BY 4.0 licence](https://creativecommons.org/licenses/by/4.0/). Please cite our [paper](https://iopscience.iop.org/journal/1748-9326) when using the dataset.

*Frank S, Gusti M, Havlík P, Lauri P, DiFulvio F, Forsell N, Hasegawa T, Krisztin T, Palazzo A, and Valin H (2020). Land based climate change mitigation potentials within the agenda for sustainable development. Environmental Research Letters. Accepted.*


