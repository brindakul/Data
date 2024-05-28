# Effects of Weather on Accidents(Dataset collected for New York,Virginia,Florida)

Here we present a dataset that provides information about the effect of weather on the accidents caused in cities like New York, Virginia and Florida.

#### ChromeDriver - required to run Selenium webscraping library
- Please download and install a driver that is suitable for your setup via the following link: https://chromedriver.chromium.org/downloads
- Once downloaded, please replace the chromedriver.exe file located in the folder labeled "chrome_driver" 
- From here, you should be able to execute the script successfully

## General Information

    Dataset Name                accident_weather
    Institution Name            Drexel University, Philadelphia, PA
    Data Investigators          Kartik Vora
                                Mahima Modi
                                Jerin Philip
                                Brinda Kulkarni
    Contact Person              Prof. Rezapour
    Date of Data Collection     June, 2022
    Data Collected From         Weather, Crash Accidents
    Data API
    Language                    English
    Collector Script            DSCI_final_Notebook.ipynb (Jupyter Notebook)
    Purpose of Data Collection  Educational

## Data and File Overview

    File Name              accident_weather.csv
    File Format            Comma Separated Values (CSV)


## Methodological Information

1. The open Weather data consists of the records of the daily weather update for the past year. The Crash data consists of the records of the information about the Crashes occured in the past years in cities New York, Virginia and Florida.
2. We collect the Weather data by making the Weather API calls and obtain the the Crash Data of the cities using various Web Scraping techniques. 
3. The **get_weather_data** method in our code is built to accept the api_key, time, lattitude and longitude and scrape the respective Weather data(cloudiness, temperature, feels_like, pressure,humidity, wind_deg, wind_speed, rain and weather_desc) for the respective input values. The merged Weather data along with the time, latittude and longitude is appended to the Weather.csv.  
4. The **get_nyc_data_using_selenium** method is used to scrape the New York city crash data using the Selenium tool. Here we find the Xpath of the tables and fetch its records for a fixed number of pages using the Selenium driver. The fetched records are added to a dataframe which is converted to a csv file. 
5. The **get_nyc_data_using_api** method id another way to fetch the New York Crash data. It uses Socrata to get the Crash data from the API and stores it in a dataframe. The dataframe obtained gets converted into a csv file. 
6. The **clean_nyc_data** method is used to clean the New York Dataset to obtain the records after 5th June, 2021.
7. The **merge_weather_accident_nyc** method is used to call the get_weather_data for the records from the New York Crash dataset and merge the weather and crash data. It is then stored into a csv file.
8. The **get_virginia_data_using_api** method is used to get Virginia Crash data using request URL. The required columns are fetched and stored into a dataframe. The obtained records is then stored into csv file. 
9. The **clean_virginia_data** method is is used to clean the Virginia Dataset to obtain the records after 4th June, 2021.
10. The **merge_weather_accident_virginia** method is used to call the get_weather_data for the records from the Virginia Crash dataset and merge the weather and crash data. It is then stored into a csv file.
11. The **get_florida_data_using_query** method is to get Florida Crash data using request URL. The required columns are fetched and stored into a dataframe. The obtained records is then stored into csv file.
12. The **clean_florida_data** method is method is used to clean the Florida Dataset to obtain the records after 4th June, 2021 and eliminate the accidents caused due to Aggressive driving.
13. The **merge_weather_accident_florida** method is used to call the get_weather_data for the records from the Florida Crash dataset and merge the weather and crash data. It is then stored into a csv file.
14. The **create_accident_weather_data** method is used to fetch all the 3 merged datasets of cities New York, Florida and Virginia and merge them together in a single dataframe.
15. The **add_carsh_location** method is fetching the latitude and longitude from the merged dataset and adding the zipcode of the chosen coordinates.


## Data-specific Information

    Number of Data Attributes       17
    Number of Rows (Records)        8523
    Attribute List                  CRASH_DT | Latitide | Longitude | cloudiness | Temperature| feels_like | pressure | humidity | wind_deg | wind_speed | rain | weather_desc | city | zipcode 

## Prerequisites For Running The Script

Please make sure you have the latest version of Python installed on your system before proceeding with running the script. Install the chromedriver version according to your version of Google Chrome.

## Running the Code

The script is an IPython Notebook which can either be run locally on Jupyter Notebook or using Google Collaboratory.(It will take around 2 hours for the complete notebook to work)

The selenium Web Scraping code works only on local Jupyter Notebook. To try this, please uncomment the "get_nyc_data_using_selenium" function and uncomment call to that function from create_accident_weather_data() function.

## Sharing and Access Information

## Challenges
Since we are using free weather API with Student account, it allows us access to only last 1 year's data. We had to filter out the rest of the data. 
Selenium does not work on google colab, so it needs to be run locally.
