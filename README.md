# Fraction of mixoplankton based on EMODnet biology data and literature classification


## Introduction

Mixoplankton is a newly introduced term indicating plankton that is capabable of both photosynthesis and phagotrophy. More details are found in Flynn et al., (2019). The potential trophic state can be seen as an inherent characteristic of plankton species. A literature and expert-knowledge study has provided the classification in either phototrophy or mixotrophy which is submitted as traits data to WoRMS. This analysis 

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

Data are extracted from EMODnet Biology. This is described in more detail in the product on phytoplankton abundance.

Data are requested per dataset and subregion. This is done in the script "scripts/requestData.R". 

The general form is:downloadURL <- paste0("https://geo.vliz.be/geoserver/wfs/ows?service=WFS&version=1.1.0&request=GetFeature&typeName=Dataportal%3Aeurobis-obisenv_full&resultType=results&viewParams=where%3A%28%28up.geoobjectsids+%26%26+ARRAY%5B", mrgid, "%5D%29%29+AND+datasetid+IN+(", datasetid, ");context%3A0100&propertyName=datasetid%2Cdatecollected%2Cdecimallatitude%2Cdecimallongitude%2Ccoordinateuncertaintyinmeters%2Cscientificname%2Caphiaid%2Cscientificnameaccepted%2Cinstitutioncode%2Ccollectioncode%2Coccurrenceid%2Cscientificnameauthorship%2Cscientificnameid%2Ckingdom%2Cphylum%2Cclass%2Corder%2Cfamily%2Cgenus%2Csubgenus%2Caphiaidaccepted%2Cbasisofrecord%2Ceventid&outputFormat=csv")

where *datasetid* and *mrgid* are varied as described in the script. 

The data were extracted from the Greater North Sea including the Celtic Seas.

## Data product

The data product is the spatial variation of the proportion of mixoplankton species *sensu* Flynn et al. (2019) as compared to the sum of mixoplankton and phytoplankton species in the different seasons, winter, spring, summer, and authumn.

The data product is prepared by joining the requested data with a table describing the trophic mode of about 1500 planktonic species that are regualarly  monitored in the North Sea and the Baltic Sea. This list with traits has been submitted to the WoRMS traits database, but is not yet available via WoRMS. Therefore, the joined table of the occurences and these traits is available in this project in "data/derived_data" as "allDataTrait.csv". 
Not all species could be matched. The product only represents the species that where present in the EMODnet plankton datasets, assuming that it still is representative for the overall signal. The species in the traits list include, but is not limited to, all species monitored by the Dutch Government in the North Sea, and that is available in the Helcom phytoplankton products for the Baltic Sea. It is likely that those species cover most of the biomass that is present. 

The product is based on the occurence of species per grid cell. It therefore does not represent biomass ratio's, but only the ratio' of occurring species. 




## More information:



### References

* Flynn KJ, Mitra A, Anestis K, Anschütz AA, Calbet A, Ferreira GD, Gypens N, Hansen PJ, John U, Martin JL, Mansour JS, Maselli M, Medić N, Norlin A, Not F, Pitta P, Romano F, Saiz E, Schneider LK, Stolte W, Traboni C (2019) Mixotrophic protists and a new paradigm for marine ecology: where does plankton research go now? Journal of Plankton Research 41 (4): 375‑391. https://doi.org/10.1093/plankt/fbz026

### Code and methodology

https://github.com/wstolte/mixoplanktonFractions

### Citation and download link

This product should be cited as:



Available to download in:

{{link_download}}

### Authors

Willem Stolte & Lisa Schneider
