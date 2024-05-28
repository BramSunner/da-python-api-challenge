# da-python-api-challenge
Module 6 Challenge for DATA-PT-EAST-APRIL-041524-MTTH.

# About The Project
This challenge contains two separate projects: VacationPy and WeatherPy.

## VacationPy

In this project: we are provided with a CSV file containing the following information about some cities:
1. name of the city,
2. latitude of the city,
3. longitude of the city,
4. max temperature of the city (in Fahrenheit),
5. humidity of the city (as a percent),
6. cloudiness of the city (as a percent),
7. wind speed of the city (in miles per hour),
8. the country in which the city is located,
9. an ID number for the city,
10. and the date the information was collected (as a unix timestamp).
From the CSV, we create a Pandas DataFrame for our usage later in the project.

We generate a visualization from the DataFrame using the library 'hvplot.pandas'...  
The visualization places the cities at their latitude and longitude values and sizes the points based on their humidity levels.  
The background for this visualization is a world map: i.e. the points are placed at their respective place on Earth.

From the DataFrame, we select a smaller range of cities based on our ideal conditions:
1. Max Temperature is between 55 and 64 degrees Fahrenheit,
2. and Humidity is less than 51%.
Using these constrictions, a new DataFrame is created.
We then clean the DataFrame of null values and move along.

Using the new DataFrame, we make a series of calls to the GeoApify Places API.  
Each of these calls takes in the latitude and longitude of a city and returns the name of a hotel within 10000 miles of the coordinates.  
These hotels are placed into a new column in the DataFrame named 'Hotel Name'.
After the hotel names are collected, we use hvplot.pandas to make another visualization placing these points on a map of Earth.  
The points on this graph show the hotel name upon hovering over them.  

## WeatherPy

In this project: we generate a random list of cities using the citipy library.

Then, we gather weather data on these cities from the list of cities.  
This data includes:
1. the latitude of the city,
2. the longitude of the city,
3. the max temperature of the city (in Fahrenheit),
4. the humidity of the city (as a percent),
5. the cloudiness of the city (as a percent),
6. the wind speed of the city (in miles per hour),
7. the country in which the city is located,
8. and the date the data was collected.
This data is processed into a dictionary and then appended to a list.

From the list above, we create a Pandas DataFrame of the information.
This DataFrame is exported as a CSV file (to avoid making futher API calls if running the program fresh again).

We read in the CSV as a DataFrame and then begin creating a few visualizations of the weather data:
1. a scatter plot of Latitude vs. Temperature for the cities,
2. a scatter plot of Latitude vs. Humidity for the cities,
3. a scatter plot of Latitude vs. Cloudiness for the cities,
4. and a scatter plot of Latitude vs. Wind Speed for the cities.

We then define a function to make a graph which includes a line of best fit and the r-squared value for the graph.  
We split our DataFrame into the northern (latitude greather than or equal to 0) and southern (latitude less than 0) hemispheres.  
Our function is run on the both the hemisphere DataFrames to create similar visualizations as above but with the added line of best fit and r-squared value.
We create a scatter plot for the following items:
1. Latitude vs. Temperature for both hemispheres,
2. Latitude vs. Humidity for both hemispheres,
3. Latitude vs. Cloudiness for both hemispheres,
4. and Latitude vs. Wind Speed for both hemispheres.

After each pair of graphs for the hemispheres we include a few observations about the graphs.
It appears that the graphs for Latitude vs. Temperature present us with data that has a strong correlation.  
For the northern hemisphere there is an r-squared value of .65 and for the southern hemisphere the r-squared value is .63.  
These values represent that we can reliably predict a temperature based on the latitude of a city.  
This information makes sense, as the hottest parts of the Earth are centered around the equator and the coldest parts are the poles.
For the rest of the graphs produced in the code: there appears to be no correlation what-so-ever for the data.  
All of the remaning graphs produce r-squared values of 0 (if not so close to 0 that it might as well be rounded to it).

# Built In
Python.  
Jupyter Notebook.  

# Acknowledgements

In the project VacationPy, in cells 3 and 8, I used the Xpert Learning Assistant to help me figure out how to make different colors for points in an hvplot.pandas plot.  
I did not use particular code given by the assistant; however, the entire concept of adding a row that specifies color values for the points was given to me from that.
