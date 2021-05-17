# sqlalchemy-challenge

## Why use SQLAlchemy?

This repository contains SQLAlchemy homework for SMU's Data Science Boot Camp, completed and submitted March 15th. The assignment concerns the usage of the python library ***SQLAlchemy***, which allows for Python control of SQL querying, in a more secure and controlled manner than other SQL-based libraries. Other libraries, such as ***mysql.connector***, use direct querying code, essentially running Jupyter Notebook as a proxy SQL server, such as the example here:



This is fine for running simple programs within a closed netowrk or a self-contained server, but if this program were o the web or running on an external server, we run into security issues. With the literal SQL querying language wriiten directly into the code, this querying code is exposed on the user end, meaning a hacker could easily modify the query to return any data from the server. Additionally, with the calling of the passwords from the personal system, as in the first cell, confidential information is also vulnerable.

This is why we uses ***SQLAlchemy***, whose code looks more like this:



With code like this, the user-end is not exposed to code that can directly connect to the server. Data can be used by the Notebook without being capable of manipulation.

## The Assignment

This assignment runs an analysis of weather data for a planned vacation to Honolulu, Hawaii. 



Completed advanced sqlalchemy with the following analysis:

- EDA on Precipitation and Station using sqlalchemy ORM queries and visualizations (like bar, scatter and histogram charts)
- Built Flask API script using python flask to to review the data from the queries in json format
