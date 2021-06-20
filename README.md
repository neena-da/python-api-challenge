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
    Observation : We cannot really see any relation/trend between the latitudes and the cloudiness
  * Latitude vs. Wind Speed Plot
    Observation : We cannot really see any relation/trend between the latitudes and the wind speed

### Plotting the Linear Regression
* Using loc, split the dataframe into 2 dataframes bases on the latitudes - Northern Hemisphere (Latitude >=0) and Southern Hemisphere (Latitude < 0)
* Set up a function to generate the scatter plot for different measures for both cities in northern hemisphere and southern hemisphere. The function will create the scatter plot based on the x values and y values passed and also return the slope, intercept and rvalue.
* Performed the Linear Regression and ploted the line of best fit for the below
  * Latitude vs. Temperature Plot - Northern Hemisphere
    Observation : We can see the maximum temperature decrease with latitude for cities in the northern hemisphere.
  * Latitude vs. Temperature Plot - Southern Hemisphere
    Observation : We can see the maximum temperature increase with latitude for cities in the southern hemisphere.                  
  * Latitude vs. Humidity Plot - Northern Hemisphere
    Observation : We cannot really see any relation/trend between the latitudes and the humidity
  * Latitude vs. Humidity Plot - Southern Hemisphere
    Observation : We cannot really see any relation/trend between the latiudes and the humidity. Howvever, the humidity of majority           of cities in southern hemisphere is found to be higher.
  * Latitude vs. Cloudiness Plot - Northern Hemisphere
    Observation : We cannot really see any relation/trend between the latitudes and the cloudiness
  * Latitude vs. Cloudiness Plot - Southern Hemisphere
    Observation : We cannot really see any relation/trend between the latitudes and the cloudiness
  * Latitude vs. Wind Speed Plot - Northern Hemisphere
    Observation : We cannot really see any relation/trend between the latitudes and the wind speed
  * Latitude vs. Wind Speed Plot - Southern Hemisphere
    Observation : We cannot really see any relation/trend between the latitudes and the  wind speed

## VacationPy

### Loading the csv file from WeatherPy
* Load the csv file as a dataframe

### Creating Humidity Heatmap
* Configure google api key
* Saved the latitude and longitude from the dataframe to be used as location
* Saved the humidity from the dataframe to be used as weights
* Created the heatmap for the humidities and saved the figure in the outpue folder.

### Create the Hotel Marker Map
* Filter the dataframe to only include cities with maximum temperature between 70 and 80 Farenheit, with wind speed less than 10mph and cloudiness equal to 0 %.
* Retrived 10 cities from the selected cities satisfying the above criteria. Added a column Hotel Name with blank rows.
* Make the Google place API call to find hotels within 5000m from the city. Used the type = 'lodging' in the parameters.
* Retreived the Hotel name from the API json response and populated the dataframe with the hotel name.
* Removed any cities for which there are no hotels within 5000m.
* Added the marker layer on top of the heatmap layer with info_box_content displayed.

