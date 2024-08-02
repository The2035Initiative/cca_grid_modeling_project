![image](https://github.com/The2035Initiative/Buffer_Protocol_2035_Initiative_draft/assets/141206781/a801039a-1760-48e7-915c-76a41e71eac8)
# Designing California’s Clean and Climate Resilient Electricity Grid for Vulnerable Communities

### Overview
Our team includes UC San Diego, UC Berkeley, UC Santa Barbara, NREL, LBNL and GridLab, as part of a California Climate Action RFP. We develop tools that enable public and private planners to identify equitable decarbonization approaches for disadvantaged communities that are resilient to climate impacts. Our focus is on how Distributed Energy Resources (DERs) and electrified loads can work together during climate extremes to ensure resilience, quantifying the benefits of demand response, and DERs in disadvantaged communities. Our objective is to produce actionable outcomes to help disadvantaged communities create resilient distribution networks against climate change impacts while designing equitable decarbonization pathways.

At this stage, Thrust 2.1, we are modeling the supply side (generation and storage) potential and costs of rooftop solar for different building-types to inform feasible microgrid configurations in CA. We are combining spatially-explicit data from multiple studies to consider physical, technical, environmental, and social siting constraints. 

### EJ Data
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

### Energy Data
- [Annual Technology Baseline 2024 NREL](https://data.openei.org/s3_viewer?bucket=oedi-data-lake&prefix=ATB%2Felectricity%2Fcsv%2F2024%2F)
- [Google’s Project Sunroof](https://sunroof.withgoogle.com/data-explorer/place/ChIJPV4oX_65j4ARVW8IJ6IJUYs/#?overlay=flux)
- [Tracking the Sun Berkeley Lab](https://emp.lbl.gov/tracking-the-sun/): [Summary Data Tables XLXS](https://emp.lbl.gov/sites/default/files/emp-files/7_summary_tables_and_figures.xlsx)
- [Microsoft US Building Footprints](https://github.com/microsoft/USBuildingFootprints)
- [Commercial Building Energy Consumption Survey (CBECS)](https://www.eia.gov/consumption/commercial/) / [Building Activity tables 2018](https://www.eia.gov/consumption/commercial/data/2018/) / [Table B4](https://www.eia.gov/consumption/commercial/data/2018/bc/pdf/b4.pdf)
- [United States Census Bureau: American Community Survey (ACS)](https://www.census.gov/programs-surveys/acs/data.html): [Housing data](https://data.census.gov/table/ACSDP5YAIAN2015.DP04?q=DP04&t=Financial%20Characteristics:Heating%20and%20Air%20Conditioning%20(HVAC):Homeownership%20Rate:Housing:Housing%20Units:Physical%20Characteristics:Telephone,%20Computer,%20and%20Internet%20Access:Types%20of%20Rooms:Units%20and%20Stories%20in%20Structure:Water,%20Sewage,%20and%20Plumbing%20Facilities:Year%20Structure%20Built&g=040XX00US06)
- [Zillow](www.zillow.com/research/about-us) requested data access to internal categorized building-type datasets at the smallest granular level on 30 July 2024.


##### Data Notes

The data provided by [Climate & Health Vulnerability Indicators for CA (Climate Vulnerability Metric)](https://www.cdph.ca.gov/Programs/OHE/Pages/CC-Health-Vulnerability-Indicators.aspx#) includes the `Environmental Exposures Domain`, the `Population Sensitivty Domain`, and the `Adaptive Capacity Domain`.

### File Overview 
```
├── Script/
|   ├── Thrust_1.1_DAC_Survey/
|       ├── Python/
|          └── initial_exploration.ipynb
|          └── clim_vuln_metrics_indicators_wrangle.ipynb
|          └── relating_data.ipynb
|          └── simple_wkflw.ipynb
|          └── ejscreen_wrangle.ipynb
|       ├── R/
|          └── sb535_map.qmd
|          └── sd_cei_map.qmd
|          └── white_house_map.qmd
|          └── doe_ejmt_map.qmd
|          └── cdc_ej_map.qmd
|          └── cdc_svi_map.qmd
|          └── Climate_Vulnerability_Metric_Indicators_map.qmd
|          └── collective_map.qmd
|          └── relating_datasets.qmd
|          └── dissolving_block_groups_into_census_tracts.qmd
|
|   ├── Thrust_2.1_Building_Energy_DS/
|       ├── Python/
|          └── ca_grid_model_data_exploration.ipynb
|
├── Deliverables/
|   ├── Thrust_1.1_DAC_Survey/
|       └──combined_census_tracts_screeners.csv
|       ├── interactive_maps/
|             ├── no_overlap_maps/
|                   └── (too large for GitHub)
|             ├── overlaid_maps/
|                   └── (too large for GitHub)
│
|   ├── Thrust_2.1_Building_Energy_DS/
|
|
├── .gitignore
├── README.md
├── LICENSE
|
├── environment.yml (future works, pending)
├── requirements.txt (future works, pending)
```

### Thrust Task Descriptions
#### `Thrust 1.1 DAC Survey`
##### The Question
What are the barriers to and propensity of adoption of residential electrification, electric vehicles, and DERs in disadvantaged communities?

##### The Deliverable
The goal of this thrust is to understand the barriers to and propensity of adoption of DERs and electrification of end-uses for households in vulnerable communities. This information will be used by the other thrusts to explore how demand-side strategies can help to enhance these communities’ resilience against climate change.Results from this thrust will be included in the public visualization tool/map described under “Timeframe, Milestones and Evaluation Metrics.”

##### The Methodology In-Between
This quantitative analysis is looking at a collection of EJ spatial datasets of CA at the census tract level to identify disadvantaged communities (DAC). In this repository, we will overlay the data sets and visualize (relative to CalEnviroScreen) where the data sets do not overlap. The large equitable CA electrification survey aims to provide robust representation of historically underrepresented communities by oversampling DAC tracts. This analysis will aid in the decision making on which census tracts or zip codes need to be included for additional sampling.


#### `Thrust 2.1 Building Energy Data Set`
##### The Question
What are the technical and spatial constraints (e.g., feeder capacity, land use, access to chargers) on DER and microgrid deployment to serve DACs?

##### The Deliverable
The goals of this thrust are to design a comprehensive dataset at the census tract level that contains information on CA building types, their associated rooftop solar technical potentials, and associated feeder information that can be leveraged to develop different community solar microgrid configurations and sizing (from household to community-level). We will identify the optimal deployment of DER and non-DER resources for each configuration, and evaluate their long-run average cost alongside climate resilience, reliability, and land use performance metrics. Results from this research thrust will inform the planning and design of microgrids at multiple scales that improve climate resiliency and enable household electrification in DACs. Results from this thrust will be included in the public visualization tool/map described under “Timeframe, Milestones and Evaluation Metrics.”

##### The Methodology In-Between
This is a primarily research driven portion of the project, focusing on applying solar rooftop potential research that has previously been conducted that includes California. The viability of the data sets is heavily associated with granularity of the resolution. Data components smaller than the census tract level will be adapted and expanded for final conglomerate dataset that will be fed into the CA sustainable grid model.

### List of Project Supporters
- National Renewable Energy Laboratory ("NREL")
- Southern California Edison ("SCE")
- GridLab
- Electric Power Research Institute ("EPRI")
- Lawrence Berkeley National Laboratory ("LBNL")
- Sacramento Municipal Utility District ("SMUD")

### Citations
```
1. “About Zillow Research - Zillow Research.” Zillow, 28 Feb. 2024, www.zillow.com/research/about-us.Accessed 2 August 2024.
2. AWS S3 Explorer for the Open Energy Data Initiative. data.openei.org/s3_viewer?bucket=oedi-data-lake&prefix=ATB%2Felectricity%2Fcsv%2F2024%2F. Accessed 26 July 2024.
2. CDC/ATSDR Social Vulnerability Index (CDC/ATSDR SVI). www.atsdr.cdc.gov/placeandhealth/svi/index.html.Accessed 30 June 2024.
3. Council on Environmental Quality. “Explore the map.” Climate and Economic Justice Screening Tool, Nov. 2022, screeningtool.geoplatform.gov/en/downloads#3/33.47/-97.5. Accessed 30 June 2024.
4. Department of Public Health. Climate and Health Vulnerability Indicators for CA. www.cdph.ca.gov/Programs/OHE/Pages/CC-Health-Vulnerability-Indicators.aspx#.Accessed 30 June 2024.
5. Environmental Protection Agency “Download EJScreen Data | US EPA.” US EPA, 8 July 2024, www.epa.gov/ejscreen/download-ejscreen-data.Accessed 30 June 2024.
6. Department of Energy, Energy Justice Dashboard. energyjustice.egs.anl.gov. “Environmental Justice Index (EJI).”Accessed 30 June 2024.
7. Centers for Disease Control and Prevention, 15 Mar. 2024, www.atsdr.cdc.gov/placeandhealth/eji/index.html.Accessed 30 June 2024.
8. G. Barbose, N. Darghouth, E. O’Shaughnessy, and S. Forrester. “Tracking the Sun.” Energy Markets Lab & Policy UC Berkeley, Sept. 2023, emp.lbl.gov/tracking-the-sun. Accessed 26 July 2024.
9. J. Michaels. “Commercial Buildings Energy Consumption Survey (CBECS):  2018 CBECS Survey Data.” Independent Statistics and Analysis U.S. Energy Information Administration, 2018, www.eia.gov/consumption/commercial/data/2018. Accessed 23 July 2024.
10.  marcsteele. City_of_San_Diego_CEI_2021_Revision 2021 Climate Equity Index.” ESRI ArcGIS Online, 31 Mar. 2021, www.arcgis.com/home/item.html?id=859711eac76f47a7996b39a424c5c222. Accessed 30 June 2024.
12. Microsoft. “GitHub - Microsoft/USBuildingFootprints: Computer Generated Building Footprints for the United States.” GitHub, github.com/microsoft/USBuildingFootprints. Accessed 26 July 2024.
13. “Overall Climate Vulnerability in the U.S. | the U.S. Climate Vulnerability Index.” The U.S. Climate Vulnerability Index, map.climatevulnerabilityindex.org/map/cvi_overall/usa?mapBoundaries=Tract&mapFilter=0&reportBoundaries=Tract&geoContext=State.Accessed 30 June 2024.
14. P. Hidalgo-Gonzalez, Et Al. “Designing California’s clean and climate resilient electricity grid for vulnerable communities.” Seed and Matching Award Template – Project Description (2023 Climate Action). 
15. Project Sunroof - Data Explorer | California. sunroof.withgoogle.com/data-explorer/place/ChIJPV4oX_65j4ARVW8IJ6IJUYs/#?overlay=flux.
16. “SB 535 Disadvantaged Communities.”Accessed 30 June 2024.
17. OEHHA CA.Gov, May 2023, oehha.ca.gov/calenviroscreen/sb535. Accessed 30 June 2024.
18. U.S. Census Bureau. Explore Census Data. data.census.gov/table/ACSDP1Y2022.DP04?q=DP04&t=Housing:Housing%20Units:Physical%20Characteristics:Types%20of%20Rooms:Units%20and%20Stories%20in%20Structure&g=040XX00US06,06$1400000&y=2022.Accessed 30 June 2024.
```
