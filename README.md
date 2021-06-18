# python-api-challenge
# Python API Challenge Assignment - Data Analytics Bootcamp

* Created a repository in Github called python-api-challenge.
* Created 2 folders called VacationPy and WeatherPy.
* Created a file WeatherPy.py in the folder WeatherPy. In the same folder, created an api_keys.py file to hold the open weather api key. Created an Output folder to hold all the output files.
* Created a file VacationPy.py in the folder VacationPy. In the same folder, created an api_keys.py file to hold the google api key. Created an Output folder to hold all the output files.
* Created a gitignore file and added the api_keys file to it so it is is not copied to Github for privacy.

## WeatherPy

### Dependencies and Setup

* Imported all libraries and the api key for the open weather api.
* Created a random list of 1500 latitudes and longitudes from a  random range of -90 to +90 for latitudes and -180 and +180 for longitudes.
* Using Citypy, retrieved the nearest city for each of the latitude, longitude combination. Stored the cities a new list called cities.

### API Call to Open Weather API

* Setup the base url for the open weather API - 'http://api.openweathermap.org/data/2.5/weather?'
* Setup empty lists to retrive data from the open weather API json response
* Looped through each of the city in the cities list form above, appending the city, api_key and units = imperial to the base url. Units = imperial will retreive the temperature in Farenheit and Wind speed in miles/hour.
* Used try and except to retrive the below fields from the json response and append to the emplty lists created.
	Latitude, Longitude, Maximum temperature, Humidity, Cloudiness, Wind speed, Date and City
* Printed a log of all the cities found.

### Converting data into DataFrames and cleaning the dataframe
* Created a dataframe using pandas with all of the above retrieved data formt he json response.
* Printed out the number of cities and the statistics for the dataframe.
* Found the indices of cities with Hunidity greater than 100%. 
* Removed from the dataframe all rows with Humidity greater than 100% and saved it in a new dataframe called clean_city_data.

### Plotting the data (Scatter Plot)
* Retreived the current date using the module time.
* Plotted Scatter Plots for the below
  * Latitude vs. Temperature Plot
    Observation : We can see the maximum temperature increase with latitude for cities with latitude less than 0.
                  We can see the maximum temperature decrease with latitude for cities with latitude greater than 0.
 * Latitude vs. Humidity Plot
    Observation : We cannot really see any relation/trend between the latitudes and the humidity
 * Latitude vs. Cloudiness Plot
    Observation : We cannot really see any relation/trend between the latitudes and the humidity
* Latitude vs. Wind Speed Plot
    Observation : We cannot really see any relation/trend between the latitudes and the humidity




