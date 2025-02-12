# GHGRP for Energy
This repository is a collection of code and documentation for extracting and analyzing energy-related information from the U.S. Environmental Protection Agency's [Greenhouse Gas Reporting Program](https://www.epa.gov/ghgreporting). Three proposed goals for this effort are:
1. Share and improve code for working with data from the GHGRP (specifically, via the [Envirofacts](https://www.epa.gov/enviro/greenhouse-gas-customized-search) [API](https://www.epa.gov/enviro/envirofacts-data-service-api))
2. Document where energy-related data are found in Envirofacts, providing a guide for analysts and researchers
3. Develop a community for utilizing and improving GHGRP data for energy analysis and research

## Brief Overviews 
### The GHGRP
>The GHGRP requires reporting of greenhouse gas (GHG) data and other relevant information from large GHG emission sources, fuel and industrial gas suppliers, and CO2 injection sites in the United States. Approximately 8,000 facilities are required to report their emissions annually, and the reported data are made available to the public in October of each year. (https://www.epa.gov/ghgreporting)

Requirements of the GHGRP are identified in [40 CFR Part 98 Mandatory Greenhouse Gas Reporting](https://www.ecfr.gov/cgi-bin/text-idx?c=ecfr&SID=be77ce6e756f0befaa0dd95743e3342e&tpl=/ecfrbrowse/Title40/40cfr98_main_02.tpl). In general, facilities must report if their emissions from stationary fuel combustion is at least 25,000 metric tons CO2e/year. Other triggers for reporting requirements include facilities that produce, for example, adipic acid, aluminum, ammonia, cement, and HCFC-22. More detail on source categories is provided in [Table A-3 to Subpart A of Part 98—Source Category List for §98.2(a)(1)](https://www.ecfr.gov/cgi-bin/retrieveECFR?gp=&SID=cf45c5e98d651810a6ced4b08e0e4bf6&mc=true&n=sp40.23.98.a&r=SUBPART&ty=HTML#ap40.23.98_19.3). 
GHGRP reporting is divided into subparts, which correspond to source categories of GHG emissions. The EPA provides a [list of these subparts and links associated guidance material](https://www.epa.gov/ghgreporting/resources-subpart-ghg-reporting).

### GHGRP Data Sources
EPA provides several ways of [accessing GHGRP data](https://www.epa.gov/ghgreporting/ghg-reporting-program-data-sets). Here's a brief summary of key ways. 
* **[Facility Level Information on Greenhouse Gases Tool (FLIGHT)](https://ghgdata.epa.gov/ghgp/main.do):** allows you to view data in several formats including maps, tables, charts and graphs for individual facilities or groups of facilities. You can search the data set for individual facilities by name or location or filter the data set by state or county, fuel type, industry sectors and sub-sectors, annual facility emission thresholds, and greenhouse gas type. You can also compare emission trends over time and download data generated as a product of your analyses.
* **[Industrial Profiles](https://www.epa.gov/ghgreporting/ghgrp-industrial-profiles):** contain detailed analyses for each industry, updated periodically. These analyses include estimates of GHGRP coverage, emissions trends (including discussion), emissions by state, gas, and process, the number of reporters whose emissions fall above and below certain threshold values, and monitoring methods used. Each profile contains data from the indicated year back to 2011, and in some cases, 2010.
* **[Data Summary Spreadsheets, link to .zip](https://www.epa.gov/sites/production/files/2019-10/2018_data_summary_spreadsheets.zip):** multi-year data summary spreadsheet containing the most important, high-level information for facilities, as well as yearly spreadsheets containing slightly more detailed information than the multi-year summary, including reported emissions by greenhouse gas and process.
* ***[Envirofacts](https://www.epa.gov/enviro/greenhouse-gas-customized-search):*** Provides all publicly available data collected by the GHGRP in a searchable, downloadable format for facilities. This includes GHG data and much of the underlying data facilities use to determine GHG values and other reported data elements in 32 industry types. Although users can click through and select data, it's recommended that the API is used instead.
    * [Data Model](https://www.epa.gov/enviro/greenhouse-gas-model)
    * [API](https://www.epa.gov/enviro/envirofacts-data-service-api)

## How to use

Edit your desired output directory and years to download in `envirofacts_api/Get_GHGRP_data.py`, then run:
```shell
python envirofacts_api/Get_GHGRP_data.py
```
The script will download each table from each subpart, one year at a time. You can remove or re-order tables in `tables.txt` if desired. Currently, there are bugs in reading the subpart W tables (url does not exist)

The list of tables was parsed from "CUSTOMIZED SEARCH DATA ELEMENT SEARCH TOOL RESULTS" at https://enviro.epa.gov/enviro/ghg_nav_tool_v2.get_list?clmn_like=emissions&view_type=CUSTOM


