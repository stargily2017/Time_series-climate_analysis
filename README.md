# Time series climate analysis in Honolulu, Hawaii

## Excecutive Summary

Using Python and SQLAlchemy, to explore the basic climate analysis and data exploration with climate database.
Honolulu is the capital and largest city of Hawaii, located on the island of Oahu, and is a major cultural, economic, 
and tourism hub. To help with my trip planning, I decided to do a climate analysis about the area.

## Methedology

Python : Using jupyter notebook for python programming and import all modules like matplotlib, Numpy, pandas, pyplot, datetime from the base core
to find the exploratory precipitation and station analysis.
SQLAlchemy : Using Visual Studio Code, Import sqlAlchemy, from SQLAlchemy to get automap_base, create_engine, func, inspect
Flask : Import flask and jasonify

## Skills
Data cleaning, interptretation, API keys, Histogram, matplot.pyplot chart, @app.route, def functions. 

SQLAlchemy ORM(object-relational mapper) queries, Pandas, and Matplotlib. 

Use the SQLAlchemy create_engine() function to connect to your SQLite database.

Used the SQLAlchemy automap_base() function to reflect your tables into classes, and then save references to the classes named station and measurement.

Linked Python to the database by creating a SQLAlchemy session.

Performed a precipitation analysis and then a station analysis by completing the steps in the following two subsections.

## API key

https://openweathermap.org/api

## Exploratory analysis with time series

### Design Your Climate App

I designed a Flask API based on the queries that just developed. use Flask to create @app routes as follows:
1.	/
Start at the homepage.
List all the available routes.
@app.route("/")
def homepage():
    print("Server returns climate app home page...")
    return (
        f"Welcome to the Hawaii Climate App!<br/>"
        f"Available Routes:<br/>"
        f"/api/v1.0/precipitation<br/>"
        f"/api/v1.0/stations<br/>"
        f"/api/v1.0/tobs<br/>"
        f"/api/v1.0/<start><br/>"
        f" /api/v1.0/<start>/<end><br/>"
        f"Format of <start> and <end> date for querying is 'YYYY-MM-DD'"
    )
2.	/api/v1.0/precipitation
o	Convert the query results from your precipitation analysis (i.e. retrieve only the last 12 months of data) to a dictionary using date as the key and prcp as the value.
o	Return the JSON representation of your dictionary.
  all the dates and precipitation values put in the precipitation dict, we get the result in the specific period of time for the query date as 12months ago.
3.	/api/v1.0/stations
o	Return a JSON list of stations from the dataset.
  all the statons data put in the bin and give the for loop to get in each specific data. 
   list_stations = []

    for stn in total_data:
        station_dict = {}

        station_dict["id"] = stn[0]
        station_dict["station"] = stn[1]
        station_dict["name"] = stn[2]
        station_dict["latitude"] = stn[3]
        station_dict["longitude"] = stn[4]
        station_dict["elevation"] = stn[5]
        
        list_stations.append(station_dict)
4.	/api/v1.0/tobs
o	Query the dates and temperature observations of the most-active station for the previous year of data.
o	Return a JSON list of temperature observations for the previous year.
  
5.	/api/v1.0/<start> and /api/v1.0/<start>/<end>
o	Return a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a specified start or start-end range.
o	For a specified start, calculate TMIN, TAVG, and TMAX for all the dates greater than or equal to the start date.
o	For a specified start date and end date, calculate TMIN, TAVG, and TMAX for the dates from the start date to the end date, inclusive.
    
    
  @app.route("/api/v1.0/<start>"). in this route, we have to give any <start> format like "/api/v1.0/2016-08-23" in the web page. then server returns TMIN , TMAX, TAVG. 

## Result and Personal Reflections

<img width="136" height="148" alt="image" src="https://github.com/user-attachments/assets/22a3bb15-d399-40c0-b3d2-24349676296b" />

The minimum rainfall precipitation is 0, and maximum is 6.7. 
The best time for a trip to Honolulu depends on your priorities, but April, May, September, and October are generally considered ideal due to a good balance of dry weather and fewer crowds.
I studied how to use API keys from different websites and getting the best results.


![image](https://github.com/stargily2017/sqlalchemy-challenge/assets/117419179/369241d2-76d5-4255-a36a-fb9ab9c70939)

Temperature vs frequency for all the stations
![image](https://github.com/stargily2017/sqlalchemy-challenge/assets/117419179/bff59b73-f449-421a-86fd-55db3a2d1837)

