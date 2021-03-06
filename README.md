# VE-Database
Database of events taken from GDELT 2.0 and Petrarch/Phoenix 
***
#Violent Event Database

***

The Violent Event Database (VED) will provide end-users the ability to compare violent events from disparate data sources to determine how well a given data source may serve a project analyzing political violence. Specifically, I will gather data from the [Global Database of Event, Language, and Tone (GDELT)](http://data.gdeltproject.org/events/index.html) and the [Phoenix Data Project](http://phoenixdata.org/data) for the time beginning 09/01/2015 and ending 10/01/2015. The data are global in scope and updated every 15 minutes, so one month of data can have millions of observations. Depending on data size, I may filter down to only include events that are considered increasingly violent (-7 to -10 on the Goldstein scale). Note: see [CAMEO](http://eventdata.parusanalytics.com/data.dir/cameo.html) for description of Goldstein scale and CAMEO coding ontology. 

This project is being conducted in support of on-going work efforts to provide a more precise/higher-fidelity geo-located events database for analysis. If successful, it will be expanded to ingest additional data sources and a variable temporal domain.   

##Database Structure  

***

Four tables will be needed to harmonize the data and allow us to conduct a proper comparison.  

* **Phoenix Data Table**
    - Columns: Phoenix-assigned **_Event ID_** | **_CAMEO code_** | **_Description_** of event | **_Date_**  

* **GDELT Data Table**  
    - Columns: GDELT-assigned **_Event ID_** | **_CAMEO code_** | **_Description_** of event | **_Date_**  

* **Temporal Data Table**
    - Columns: GDELT/Phoenix-assigned **_Event ID_** | **_Date_**
    - Rows: All dates 09/01/15 - 10/01/15. Where/if Event ID is missing, "."  

* **Spatial Data Table**
    - Columns: GDELT/Phoenix-assigned **_Event ID_** | Location event occurred (**_Place Name_**) | **_Latitude_** | **_Longitude_** 

##Questions  

***

The PK will need to be determined in part by date. Since the goal is to be able to accurately compare events from each data set, this will need to begin with the Temporal and Spatial Data Tables, and end with the CAMEO code of the event. Thus, if an event is listed in GDELT as being a protest in Peshawar, Pakistan on 02/01/15, and also in Phoenix, we would consider the event common between both data sources. If, however, the event exists in GDELT but not in Phoenix, it would be a unique event. This should necessitate a composite PK, though I will need to think a little more about how to operationalize it.
