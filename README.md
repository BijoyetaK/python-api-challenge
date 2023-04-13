# python-api-challenge
#### Module 6 assignment - Working with APIs
     -2 APIs used to fetch the data to play with: Geoapify and OpenWeatherMap 
     - API keys are stored as system environment variables 
     - Use of citipy Python library is used to determine the cities based on Latitude and Longitude
     - Use of geoViews Python library to create map visualizations. 
     - 2 deliverables in jupyter notebook - WeatherPy and VacationPy
     - Using the resultant output dataframes from WeatherPy, map visualizations are created in VacationPy
  

 #### WeatherPy
 ##### Data Collection
      - In this script, citipy library is used to generate a list of cities based on random Latitide and Longitude
      - Grouping the list of cities in sets of 50. Set parameters for each of them and make calls to the OpenWeatherMap API to fetch json response.
      - Parse the Json and retreive weather data, using .get() method in python dictionaries. https://www.geeksforgeeks.org/python-dictionary-get-method/
      - Append all those weather data collected only for the cities which has data in the response, into a city_data list of dictionaries. 
      - Convert the weather data collected intp Pandas Dataframe
      
 ##### Data Cleaning
      - Drop from the city data dataframe, the cities for which no weather data was found.
      - Count the cities which has weather data.
      - Export the city_data into a csv
      - Read the saved city_data from the csv with renaming the index_column to City_ID
      - The final city_data dataframe has City_ID, Latitude, Longitude, Temperature, Humidity, Cloudiness, Wind Speed, Country amd Date(date timestamp)
      - Using the strftime function in datetime module to convert the timestamp to date for later display in graph titles. 
      - Create Scatter plots tp showcase the Relationship Between Weather Variables and Latitude. The plots are saved as images. 
        - Latitude Vs Temperature
        - Latitude vs. Humidity
        - Latitude vs. Cloudiness
        - Latitude vs. Wind Speed
      - Compute Linear Regression for Each Relationship:
        - Create a series of scatter plots, derive the line equation and r values from lineregress function from scipy
        - Plots created and results are analyzed for:  
          - Northern Hemisphere: Temperature vs. Latitude
          - Southern Hemisphere: Temperature vs. Latitude
          - Northern Hemisphere: Humidity vs. Latitude
          - Southern Hemisphere: Humidity vs. Latitude
          - Northern Hemisphere: Cloudiness vs. Latitude
          - Southern Hemisphere: Cloudiness vs. Latitude
          - Northern Hemisphere: Wind Speed vs. Latitude
          - Southern Hemisphere: Wind Speed vs. Latitude
    
 #### VacationPy
      - This notebook is to used to determine the cities having ideal weather conditions and nearest hotels within a radius based on the city data collected in 
        WeatherPy. 
 ##### Data Collection
      - Import the GeoAPIfy key which are set as system environment variables. 
      - Import hvplot module in geoviews for map plots.
      - Read the city_data csv created in WeatherPy into Pandas dataframe. 
      
 ##### Data Cleaning
      - Create a Dataframe to contain only Humidity data for the cities.
      - Create a map that displays a point for every city in the city_data_df. The size of the point should be the Humidity in each city.
      - Narrow down the city_data_df to filter out the cities having ideal weather conditions and also drop any null values. 
      - Ideal weather conditions - Max Temp lesser than 27 degrees C but greater than 21 degrees C,Wind Speed less than 4.5 m/s, and having zero cloudiness. 
      - Show the count of such cities that fall under ideal weather conditions. 
      - Copy the dataframe containing the ideal weather condition cities to another hotels dataframe to store the city, country, coordinates,humidity and HotelName.
      - For each city, use the Geoapify API to find the first hotel located within the radius of 10,000 metres of your coordinates.
      - Create functions to set params and make API calls for those cities in the hotel_df using latitude, longitude, radius(10000), limit(first hotel, hence value 1). 
      - Functions are created for fetching the name and address from json individually
      
      - Converting the hotel_df to dict.Using for loop on the hotel_dict, inorder to fetch HoteName and Address from json and appending Latitude, Longitude, HotelName,          Address, City and Country to a hotels list. 
      - Convert the hotels list to data frame to display. Drop any null value. 
      
      - Create a map plot to dislay the list of those cities having those hotels. Country and HotelNames is displayed in the hover messages on the map data points. 
     
 
