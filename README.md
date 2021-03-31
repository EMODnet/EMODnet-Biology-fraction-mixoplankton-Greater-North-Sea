# Fraction of mixoplankton based on EMODnet biology data and literature classification


## Introduction

Mixoplankton (sensu Flynn et al., 2019) is a newly introduced term indicating plankton that is capabable of both photosynthesis and phagotrophy. More details are found in Flynn et al., (2019). The potential trophic state can be seen as an inherent characteristic of plankton species. A literature and expert-knowledge study has provided the classification in either phototrophy or mixotrophy which is submitted as traits data to WoRMS. This analysis makes use of this classification to estimate the spatial and temporal distribution of the fraction of mixoplanktonic species in the Greater North Sea including the Celtic Seas.

## Directory structure

```
{{directory_name}}/
├── analysis
├── data/
│   ├── derived_data/
│   └── raw_data/
├── docs/
├── product/
└── scripts/
```

* **analysis** - Markdown or Jupyter notebooks
* **data** - Raw and derived data
* **docs** - Rendered reports
* **product** - Output product files
* **scripts** - Reusable code

## Data series

Data are extracted from EMODnet Biology. This is described in more detail in [the product on phytoplankton abundance](https://github.com/EMODnet/EMODnet-Biology-Phytoplankton-Greater-NorthSea).

Data are requested per dataset and subregion. This is done in the script ["scripts/requestData.R"](https://github.com/EMODnet/EMODnet-Biology-Phytoplankton-Greater-NorthSea/blob/master/scripts/requestData.R). 

The general form is:downloadURL <- paste0("https://geo.vliz.be/geoserver/wfs/ows?service=WFS&version=1.1.0&request=GetFeature&typeName=Dataportal%3Aeurobis-obisenv_full&resultType=results&viewParams=where%3A%28%28up.geoobjectsids+%26%26+ARRAY%5B", mrgid, "%5D%29%29+AND+datasetid+IN+(", datasetid, ");context%3A0100&propertyName=datasetid%2Cdatecollected%2Cdecimallatitude%2Cdecimallongitude%2Ccoordinateuncertaintyinmeters%2Cscientificname%2Caphiaid%2Cscientificnameaccepted%2Cinstitutioncode%2Ccollectioncode%2Coccurrenceid%2Cscientificnameauthorship%2Cscientificnameid%2Ckingdom%2Cphylum%2Cclass%2Corder%2Cfamily%2Cgenus%2Csubgenus%2Caphiaidaccepted%2Cbasisofrecord%2Ceventid&outputFormat=csv")

where *datasetid* and *mrgid* are varied as described in the script. 

The data were extracted from the Greater North Sea including the Celtic Seas. The regions of interest were selected from the intersect of the Exclusive Economic Zones and IHO sea areas (Flanders Marine Institute, 2020) created by Marine Regions.

## Data product

The data product is the spatial variation of the proportion of mixoplankton species *sensu* Flynn et al. (2019) as compared to the sum of mixoplankton and phytoplankton species in the different seasons, winter, spring, summer, and autumn.

The data product is prepared by joining the requested data with a table describing the trophic mode of about 1500 planktonic species that are regularly  monitored in the North Sea and the Baltic Sea. This list with traits has been submitted to the WoRMS traits database (Schneider et al., 2020a; WoRMS Editorial Board, 2021). Because it is not easy to extract all known traits of plankton in one table, a table with these traits is available in this project in "data/raw_data" as "traits.csv". 

Not all species could be matched. The product only represents the species that where present in the EMODnet plankton datasets and that could be matched with the traits list, assuming that it still is representative for the overall signal. 

The species in the traits list include, but is not limited to, all species monitored by the Dutch Government in the North Sea (e.g. Schneider et al., 2020b), and that are available in the Helcom phytoplankton products for the Baltic Sea. It is likely that those species cover most of the biomass that is present. 

The product is based on the occurrence of species per grid cell. It therefore does not represent biomass ratio's, but only the ratio' of occurring species. 

The EMODnet mapping package [EMODnetBiologyMaps](https://github.com/EMODnet/EMODnetBiologyMaps) was used to produce maps of the rasters.

## More information:

https://emodnet.github.io/EMODnet-Biology-fraction-mixoplankton-Greater-North-Sea/


### References

* Fernández-Bejarano S, Schepers L (2020). EMODnetBiologyMaps: Creates ggplot maps with the style of EMODnet. R package version 0.0.1.0. Integrated data products created under the European Marine Observation Data Network (EMODnet) Biology project (EASME/EMFF/2017/1.3.1.2/02/SI2.789013), funded by the by the European Union under Regulation (EU) No 508/2014 of the European Parliament and of the Council of 15 May 2014 on the European Maritime and Fisheries Fund, https://github.com/EMODnet/EMODnetBiologyMaps
* Flanders Marine Institute (2020). The intersect of the Exclusive Economic Zones and IHO sea areas, version 4. Available online at https://www.marineregions.org/.https://doi.org/10.14284/402
* Flynn KJ, Mitra A, Anestis K, Anschütz AA, Calbet A, Ferreira GD, Gypens N, Hansen PJ, John U, Martin JL, Mansour JS, Maselli M, Medić N, Norlin A, Not F, Pitta P, Romano F, Saiz E, Schneider LK, Stolte W, Traboni C (2019) Mixotrophic protists and a new paradigm for marine ecology: where does plankton research go now? Journal of Plankton Research 41 (4): 375‑391. https://doi.org/10.1093/plankt/fbz026
* Schneider LK, Anestis K, Mansour J, Anschütz AA, Gypens N, Hansen PJ, John U, Klemm K, Lapeyra Martin J, Medic N, Not F, Stolte W. (2020a) A dataset on trophic modes of aquatic protists. Biodiversity Data Journal 8. https://doi.org/10.3897/BDJ.8.e56648.
* Schneider LK, Flynn KJ, Herman PMJ, Troost TA, Stolte W. (2020b) Exploring the trophic spectrum: placing mixoplankton into marine protist communities of the Southern North Sea. Frontiers in Marine Science 7: 997 -  https://doi.org/10.3389/fmars.2020.586915
* WoRMS Editorial Board (2021). World Register of Marine Species. Available from https://www.marinespecies.org at VLIZ. Accessed 2021-03-31. doi:10.14284/170


### Code and methodology

Code in analysis/narrative.Rmd

### Citation and download link

This product should be cited as: 

Willem Stolte & Lisa Schneider (2020) ‘Proof of concept’ product: Fraction of mixoplankton (photo-phagotrophic) species in the Greater North Sea and Celtic Seas. Integrated data products created under the European Marine Observation Data Network (EMODnet) Biology project (EASME/EMFF/2017/1.3.1.2/02/SI2.789013), funded by the by the European Union under Regulation (EU) No 508/2014 of the European Parliament and of the Council of 15 May 2014 on the European Maritime and Fisheries Fund


Available to download in: 

https://www.emodnet-biology.eu/data-catalog?module=dataset&dasid=6621


### Authors

Willem Stolte & Lisa Schneider
