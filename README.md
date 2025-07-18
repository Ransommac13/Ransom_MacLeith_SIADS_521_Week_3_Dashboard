# Ransom_MacLeith_SIADS_521_Week_3_Dashboard
This is the public location for the ipynb Dashboard and associated files that I compiled for the Week 3 assignment of SIADS 521. 

## Data Source
I downloaded the CSV file from data.gov at this URL: 'https://catalog.data.gov/dataset/ems-incident-dispatch-data'. 
It was originally distributed by the Fire Department of New York City via NYC Open Data at this URL: 'https://data.cityofnewyork.us/Public-Safety/EMS-Incident-Dispatch-Data/76xm-jjuj/about_data'. This URL includes an Excel document that describes the dataset, including the meanings of all columns and codes. 

I would not recommend attempting to load all 28 million rows, which record nearly all EMS dispatch incidents between Jan 1, 2023 and May 10, 2025. Because the purpose of this visualization is exploratory in nature, it is not necessary to visualize all 28 million incidents at once. 

## Dependencies
* pip
* Pandas
* Numpy
* Scipy
* ipywidgets
* IPython
* plotly

## Introduction
When I visit friends in New York City, a common background noise is the familiar whoop of ambulance sirens. And it makes sense; considering NYC's population density, I'm surprised I don't hear sirens more often. When I do hear them, I often think that NYC seems like a horrible place to have an emergency, with its tall buildings, crowded streets, and inconsistent presence of elevators. Therefore, out of curiousity, I decided to explore EMS response times in NYC using publicly available data. 

The purpose of this dashboard is to explore the relationship between EMS response times and various factors included in the dataset, including the borough in which the incident occurred, the initial severity level of the incident, and the relative frequency of EMS incidents in the local area. The dataset also enables the investigation of the subcomponent response times that contribute to the overall EMS response time, such as how long it takes to assign an EMS response team, how long it takes the EMS response team to mobilize, and how long it takes the response team to arrive on scene. This dashboard is meant to be exploratory, not prescriptive. One of the most important takeaways from the data and associated visualizations is there is not enough information to conclude the cause of any differene in EMS response times, only that there appears to be some. 

## Visualization Technique
(1) Line Chart: The line chart shows the stage of the incident on the x axis, and the cumulative EMS response time on the y axis. This is a good visualization to start with, because it most closely replicates how we (or at least I) intuitively think about an EMS response: as a process. Step 1 is to report the incident. Step 2 is to assign the incident to an EMS response team. Step 3 is the EMS response team mobilizing itself and starting towards the scene of the incident. Step 4 is arriving on scene and providing immediate care. And so on. The viewer can see how each stage of the process relatively contributes to overall EMS response time. In addition, creating separate lines by borough (or by incident incident severity level using the widget) allows the viewer to explore potential differences in EMS response times by borough or initial incident severity level. 

(2) The box plots build on top of the initial picture established by the line chart. Instead of exploring singular points in the line chart, the box plots' quartiles give a more realistic picture of EMS response times. To stay consistent with the line chart, the box plot chart's x axis can be either borough or initial incident severity level. This allows the viewer to explore, for example, whether the initial severity level of the incident affects the urgency of the dispatcher and EMS response team and by approximately how much. The y axis variable can be changed to any stage of the EMS response, allowing the viewer to explore, for example, whether differences between boroughs lie in the time it takes to dispatch an incident or the time it takes for the response team to arrive on scene. The y axis does allow for root transformations due to the heavy right skewness of response time data. This enables for more visually obvious comparisons between categories. However, because the degree of skewness differs depending on the y variable chosen (and because some viewers may wish to view the data without transformations), the box plot chart allows the viewer to select the root transformation to apply. 

(3) The scatter plot represents an initial investigation into why EMS response times may differ geographically. It transforms the raw data into a pivot table that includes the count of incidents and mean response times of incidents grouped by incident dispatch area. This allows the viewer to explore whether an increase in the number of incidents in a local area causes an increase in the average EMS response time. Consistent with the other charts, the y axis variable can be changed to any stage of the EMS response, allowing the viewer to explore whether an increase in incident frequency affects different stages of the EMS response differently. 

(4) The histogram allows the viewer to explore the distribution of response times for a specific borough in more depth. Similar to the box plots, it allows the viewer to select the root transformation to apply. Consistent with the other charts, the historgram can display the distribution of times for any stage of the EMS response. 

## Visualization Library
### What I though about when choosing a Library
After doing some initial exploration into the nature of the NYC EMS Incident Data, it became clear that the exploration of this dataset would be the first step of the many steps required to turn this data into real improvements in EMS response times. For understandable reasons, the dataset includes sufficient data to identify differences and potential issues in the dispatch system but insufficient data to accurately hypothesize the underlying reasons. Therefore, for this dashboard, it did not make sense to create one that was overly procedural. 

On the other hand, in the event that more data on the dispatch process becomes available, further data analyses and visualizations would likely benefit from being more procedural and convincing of a specific argument. In an ideal world, these visualizations would remain compatiable with preliminary data explorations. 
### Plotly Library
The Plotly library is the ideal choice for this purpose due to its modular flexibility. This dashboard primarily uses Plotly express, and the primary reason is that its easier. The purpose of this dashboard is preliminary exploration, so it would not make sense to create overly procedural charts. That being said, Plotly has the ability to produce more procedural and customizable charts using Plotly graph objects and Dash. I didn't utilize these features in this dashboard, but they are accessible within the same Library in service of follow-on data visualizations. 
### Dashboard Approach
This dashboard specifically is fairly declarative due to its reliance on Plotly express. This limits its professionalism but this is a drawback I am willing to accept. This initial exploration of the dataset isn't meant for presentation to the public or high-level decision makers. The use of a more declarative library allows me to save time while still identifying potential trends and pain points for further investigation. 
### Installing Plotly
Plotly.py is free and open-source and does integrate with Jupyter notebooks. 
#### To install Plotly type the following command: 
!pip install plotly
#### Or if using an Anaconda Python distribution:
conda install -c plotly plotly
