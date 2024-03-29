# Slater Fire Hydrology
Robin Ruhm

## Description
This project will look at the effects of the slater fire on infiltration by looking at the runoff response to precipitation events.  

##Background
The 2020 Slater Fire burned in the Indian Creek Watershed in the Mid-Klamath on Karuk lands including the town of Happy Camp.  Karuk collaborators have suggested that this may have had several hydrological effects including changing flood lines in Happy camp.

A host of literature looks at ecological effects of fires.  Specifically sufficiently high heat fires can vaporize and and induce chemical changes through pyrolysis to organic compounds.  While sufficient exposure to high heat will burn compounds away, limited exposure to heat combined with the temperature gradient of fires can lead to the settling of compounds back into topsoil with hydrophobic ends of compounds left exposed.  This can create a water-repellent layer that vastly reduces infiltration in future rain events.  See Robin's Water Repellency term paper (From Fire Ecology in the Fall of 2021) uploaded to the github for further background information (and a project proposal that this project builds towards): https://github.com/UW-GDA/SlaterFireHydrology/blob/main/water-repellency-term-paper.pdf.

## Problem Statement 
First I intend to use time series to understand the correlation of precipitation amount with river flow increase for various delay intervals post-rainfall both before and after a fire.  I will look for differences in time series regression coefficients from the before-fire and after-fire analysis and try to tease out statistically different effects.  While it is likely out of the scope of the course project this could be compared to nearby unburned areas as controls (to run a difference of differences analysis on the before and after times).  

Datasets you will use (with links, if available)
USGS flow data from Indian Creek CA: https://waterdata.usgs.gov/nwis/uv?site_no=11521500
Rainfall Data for Happy Camp CA: https://www.ncdc.noaa.gov/cdo-web/search?datasetid=GHCND
If needed, fire perimeter data: https://www.usgs.gov/faqs/where-can-i-find-wildfire-perimeter-data (although for this project that is likely not important for now)

## Tools/packages you’ll use (with links)
Pandas
Regression with StatsModel


## Planned methodology/approach
For both pre-fire and post-fire, linearly regress flow on precipitation n days prior (run independently with n ranging from 0 to 30 or possibly larger).  Also regress flow change (from the previous day rather than flow itself) on precipitation from n days prior (accounting for snowmelt and groundwater fed flows).  Try controlling for temperature.  Exclude days with average temperature less than 32 degrees.  Potentially restrict to days with high rainfall (to more precisely pinpoint rain-induced flows from other sources).  

Seek statistically significant differences in regression coefficient, correcting significance for the fact that on the order of a hundred independ regressions have been run (e.g. so a couple 3-standard deviation difference is consistent with the null hypothesis).

## Expected outcomes
Ideally this will find measureable differences in correlations of rainfall with post-precipitation river flows.  If so, then it will be up to future work to untangle what may be caused by infiltration changes, interception changes, or evapotranspiration changes.  If no change is noted, it will be an important result that runoff-driven river flows do not seem particularly impacted by fire scars in the Klamath (given that the Slater fire is one of the more severe fires in recent times).

## Results
Unfortunately the Happy Camp precipitation data was too sparse to use.  However, Salmon River (100 miles away) has reliable precipitation data; the two weather stations are fairly correlated in precipitation data (.76 correlation during the late season period the analysis focused on).  Therefore, it was used as the precipitation source.  Note that any analysis using this precipitation data should be interpreted using an instrumental variable (in particular, the effects both in terms of correlation and r-squared are greater by a factor of 1/.76 than what is found using this instrumental variable).  

The analysis did find an increase in regression coefficient post fire (2021) compared to pre-fire (2015-2019) for both Indian Creek and Sucker Creek (also contains part of the Slater fire scar).  Surprisingly, Salmon River (a control data set) experienced a drop in regression coefficient post-fire.  While this may be a result of the Salmon River's larger watershed and flows, it's geographic location south of the other two creeks, or factors at play relating to the year 2021 (in which case the fire scar might have been so important it outweighed those confounding factors), this might also simply indicate the scale of unpredictability of the data is too large to take much meaning from the analysis.  

## Conclusions
More analysis from other fires is needed to verify if we are seeing changing hydrological responses due to them.  Waiting a year or two would let us look at more years of Slater Fire data as well as post-fire data from the 2021 River Complex and McCash fires that were also large and relatively severe fires.  In the mean time more analysis can be made on older (mostly low to moderate-severity) fires.  Futhermore, this may turn out to be a case where existing data is too coarse to tease out fire-hydrological responses and field sampling of soil will be needed.

## References
See attached term paper from last quarter for references: https://github.com/UW-GDA/SlaterFireHydrology/blob/main/water-repellency-term-paper.pdf
