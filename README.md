![image](https://github.com/The2035Initiative/Buffer_Protocol_2035_Initiative_draft/assets/141206781/a801039a-1760-48e7-915c-76a41e71eac8)
# California Climate Action: Large Equitable CA Survey for Advanced Electrification Consumer-Facing Policies

### Overview
This quantitative analysis is looking at a collection of EJ spatial datasets of CA at the census tract level to identify disadvantaged communities (DAC). In this repository, we will overlay the data sets and visualize (relative to CalEnviroScreen) where the data sets do not overlap. The large equitable CA electrification survey aims to provide robust representation of historically underrepresented communities by oversampling DAC tracts. This analysis will aid in the decision making on which census tracts or zip codes need to be included for oversampling.


### Data
- [CalEnviroScreen](https://oehha.ca.gov/calenviroscreen/maps-data)
- [SB535 Disadvantaged Communities](https://oehha.ca.gov/calenviroscreen/sb535)
- [San Diego Climate Equity Index](https://www.arcgis.com/home/item.html?id=859711eac76f47a7996b39a424c5c222)
- [EJScreen Tool](https://www.epa.gov/ejscreen/download-ejscreen-data)
- [White House Map](https://screeningtool.geoplatform.gov/en/downloads#3/33.47/-97.5)
- [Climate & Health Vulnerability Indicators for CA (Climate Vulnerability Metric)](https://www.cdph.ca.gov/Programs/OHE/Pages/CC-Health-Vulnerability-Indicators.aspx#) 
- [DOE's Energy Justice Mapping Tool - Disadvantaged Communities Reporter (EJMT)](https://energyjustice.egs.anl.gov/)
- [CDC's Environmental Justice Index (EJI)](https://www.atsdr.cdc.gov/placeandhealth/eji/index.html)
- [CDC's Social Vulnerability Index (SVI)](https://www.atsdr.cdc.gov/placeandhealth/svi/index.html)
- [US Climate Vulnerability Index: Overall Climate Vulnerability in The U.S.](https://map.climatevulnerabilityindex.org/map/cvi_overall/usa?mapBoundaries=Tract&mapFilter=0&reportBoundaries=Tract&geoContext=State)

##### Data Notes

The data provided by [Climate & Health Vulnerability Indicators for CA (Climate Vulnerability Metric)](https://www.cdph.ca.gov/Programs/OHE/Pages/CC-Health-Vulnerability-Indicators.aspx#) includes the `Environmental Exposures Domain`, the `Population Sensitivty Domain`, and the `Adaptive Capacity Domain`.

### File Overview 
```
├── Script/
|   ├── identifying_ctracts_oversampling.ipynb
|   ├── clim_vuln_metrics_indicators_wrangle.ipynb
|   ├── relating_data.ipynb
|   ├── simple_wkflw.ipynb
|
├── Deliverables/
|   ├── no_overlap_map (future works, pending)
|   ├── no_overlap_tracts/
|       └──"associated_data_no_overlap.csv"
│   
├── .gitignore
├── README.md
├── LICENSE
|
├── environment.yml (future works, pending)
├── requirements.txt (future works, pending)

```

#### Notebook Descriptions

##### `identifying_ctracts_oversampling.ipynb`
Currently filled with data exploration and the overarching game plan for this project.
You will see that there are some schema inconsistencies that need to be addressed within the Climate Vulnerability Metric data in order to properly map the observations.
A db schema is currently in the works to create a temporary table to relate the observations to their appropriate geographical locations.

##### `clim_vuln_metrics_indicators_wrangle.ipynb`
Using an ESG lense, looking at all of the individual datasets to identify the nuances in column names, cleaning, then combining into a single csv file to read in later.
There is a combination of 19 xlsx and 1 NETCDF file for the Climate Vulnerability Metrics Indicators.

##### `relating_data.ipynb`
This notebook contains the development of the intermediate tables required to relate the Climate Vulnerability Metrics Indicators data to it's associated geo-locations.

##### `simple_wkflw.ipynb`
To provide an update on this project to our team, I am subsetting the data that plotted properly in `identifying_ctracts_oversampling.ipynb` and overlaying them to see their overlap relative to the CalEnviroScreen data. An output of 2 csv files containing census tracts that overlapped, and census tracts that did not overlap will be produced, alongside some engaging visualizations. The objective is to create a framework that will be later leveraged once the Climate Vulnerability Metric and EJScreen data are wrangled.