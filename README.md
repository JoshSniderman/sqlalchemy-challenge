# sqlalchemy-challenge

## Why use SQLAlchemy?

This repository contains SQLAlchemy homework for SMU's Data Science Boot Camp, completed and submitted March 15th. The assignment concerns the usage of the python library ***SQLAlchemy***, which allows for Python control of SQL querying, in a more secure and controlled manner than other SQL-based libraries. Other libraries, such as ***mysql.connector***, use direct querying code, essentially running Jupyter Notebook as a proxy SQL server, such as the example here:

![map_chart](Images/MySQL_Proxy.png)

This is fine for running simple programs within a closed network or a self-contained server, but if this program were on the web or running on an external server, we run into security issues. With the literal SQL querying language wriiten directly into the code, this querying code is exposed on the user end, meaning a hacker could easily modify the query to return any data from the server. Additionally, with the calling of the passwords from the personal system, as in the first cell, confidential information is also vulnerable.

This is why we uses ***SQLAlchemy***, whose code looks more like this:

![map_chart](Images/SQLAlchemy_example.png)

With code like this, the user-end is not exposed to code that can directly connect to the server. Data can be used by the Notebook without being capable of manipulation.

## The Assignment

This assignment runs an analysis of weather data for a planned vacation to Honolulu, Hawaii. 


## Overview of the Data

 The data used for this project includes a CSV file with a list of stations and a CSV file with a list of measurements.
 
 
 Measurement parameters includes:
 
 station: Identifing number of the station
 
 date: Date of recording
 
 prcp: A measurement of precipitation taken by the station
 
 tobs: A measurement of temperature taken by the station
 
 
 Station parameters includes:
 
 station: Identifing number of the station ex:USC00519397
 
 name: Name of the station ex: WAIKIKI 717.2, HI US
 
 latitude: Latitude of station
 
 longitude: Longitude of station
 
 elevation: Elevation of station 

## Limitations of the Data

That data contained in the CSV files is dated from January 1, 2010 to August 23, 2017 so at the time of this writing is missing almost two years of weather data. Because global temperatures have been observed to have an upward trend, any query based on an aggregated temperature for a particular date can be expected to be lower than what will actually occur.

## Methods

The data is stored using SQLite, queried using SQLAlchemy and written into a deployable app using flask. Jupyter notebooks, pandas, and matplotlib are used to examine and visualize the data.

# Analysis

To prepare the queries for the app as well as to better understand the data, the below analysis was conducted.

Using the last date in the available data, the last twelve months of data in the database is queried, placed into a DataFrame and plotted in a bar chart to show total daily precipitation.

## Daily Precipitation over last year of data
![prcp](Images/prcp.png)

Using the station with the most observations in the last twelve months of the data, temperatures are queried and plotted into a histogram.

## Temperature Histogram
![temphist](Images/temphist.png)

Selecting a date range for a trip taken to Hawaii, minimum, average and maximum temperatures for that date range are queried and placed into a bar graph with an error bar.

## Trip average temperature
![tempavg](Images/tempavg.png)

Again using a date range for a trip, the average daily norms are queried and plotted into an area graph.

## Trip temperature area chart
![temparea](Images/temparea.png)

## Flask Routes

The flask routes prepared are detailed below:

/

Home page listing all available routes.

/api/v1.0/precipitation

Returns a JSON representation of the dates and total recorded precipitation.

/api/v1.0/stations

Returns a JSON list of stations from the dataset.

/api/v1.0/tobs

Returns a JSON list of Temperature Observations (tobs) from a year from the last data point.

/api/v1.0/YYYY-MM-DD and /api/v1.0/YYYY-MM-DD/YYYY-MM-DD

Returns a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.

When given the start only, calculate TMIN, TAVG, and TMAX for all dates greater than and equal to the start date.

When given the start and the end date, calculate the TMIN, TAVG, and TMAX for dates between the start and end date inclusive.

