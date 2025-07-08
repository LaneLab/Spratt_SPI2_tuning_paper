# Spratt_SPI2_tuning_paper
This repository contains csv summary files and code used for data extraction in the first preprint version of Spratt M., Lane K. (2025) (https://doi.org/10.1101/2025.07.01.662634)


# Flow Cytometry Data 

## Summary Dataframes 
6 .xlsx files are included - found in FlowSummaryStats
Stored as CSV files. FlowJo was used to analyze FCS files. CSVs contain summary statistics as exported by FlowJo and are organized by figure. 

# DIMM Data: 

## Summary Dataframes 
4 data files are included - found in DIMM_summaries

- **Full_MotherCell_Data.csv** - contains all processed median sfGFP and mRuby2 intensity values and cell length (feret_diameter_um) for 3 separate experiments - 258 total mother cells. 

- **CellCycle_Stats.csv** - contains information about all cycles of all tracked cells. Every combination of unique_ID and cell_ID will have multiple rows pertaining to what cycle the data is on. Cycle numbers start at 0 for each cell that emerges. Note that this contains 'incomplete' cycles that were not fully captured by the imaging - these are filtered in the analysis notebooks. 

- **Switch_Stats.csv** - contains information pertaining to detected GFP reporter switches of each cell. Cells that were born above the GFP(+) threshold or do not have a detected start increase time have NaNs in these columns. Also contains boolean classifiers that are used for filtering in notebooks. See companion text file for details on what each column header refers to. 

- **mRuby_Stats.csv** - contains information about Ruby features for each cell_id. 

## Analysis
1 python script and 6 jupyter notebooks for downstream analysis and plotting are included - found in DIMM_code 

- **TrackmateXML.py** - contains base pyTrackmate script with modifications to sort cell_ID assignment by Y position in the channel.

- **Lineage_Extraction.ipynb** - notebook used to apply pyTrackmate, extract cell information from XML files, and store lineages in a dictionary of xarray datasets called ds_all. 

- **Processing.ipynb** - working from ds_all to generate summary dataframes used in downstream analysis and plotting, includes code used to produce all summary dataframes in this repository.  

- **Mother_Plotting.ipynb** - plotting and analysis from Full_MotherCell_Data.csv used to generate figures. 

- **Cycle_Feature_Plotting** - plotting and analysis from CellCycle_Stats.csv used to generate figures. 

- **ParentProgenyCorrelative_Plotting.ipynb** - plotting and analysis from combined data sets to generate figure 6E. 

- **Random_Forest.ipynb** - processing and creation of RFR from combined summary dataframes. 
