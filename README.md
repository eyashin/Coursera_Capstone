# Coursera Capstone: The battle of Prague Neighborhoods
## Introduction: Business Problem:
Every day millions of people use the services of cafes and restaurants. For example, the restaurant and food service industry is a $660 billion industry in the United States. This industry is divided into two groups: those that prepare and serve food and those that produce and distribute food, equipment, and services needed by food providers. The most common example of the first group is restaurants. The second group includes equipment suppliers and food and beverage suppliers.
Imagine that your company distributes food, equipment, and services and your main customers are restaurants. Nowadays the number of restaurants has decreased. And still you want to expand your business. The best way to do this is to find another location for it.
You select Prague the capital of Czech Republic. You need to know what areas are in the city of Prague and the number of restaurants of a certain type in different districts. In addition, the necessary information for solving logistics problems is the density of restaurants per square kilometer.

Data Requirement:

Based on the problem mentioned above, factors to be considered are:
-	Number and area of neighborhoods in Prague 
-	Number of restaurants and their categories in each neighborhood

The following data sources will be required to extract relevant data:
-	A list of neighborhoods in Prague from open data
-	A geocoder library for extracting latitude and longitude coordinates
-	Foursquare API for searching for restaurants within these neighborhoods and providing their various latitudes and longitude coordinates

## Methodology:
First, let's look at the administrative division of Prague at https://en.wikipedia.org/wiki/Districts_of_Prague [1].

I found geo info at open data server [2]. You can download data or use downloaded TMMESTSKECASTI_ansi.json.
Let’s look at Area of districts. We need to use Shape Area field. I used Python to transfer json to Pandas dataframe. The biggest neighborhoods are:

Neighborhood       Area
-	Praha 6  41.561204
-	Praha 5  27.510820
-	Praha 4  24.200364
-	Praha 12  23.317909
-	Praha 8  21.79410

The smallest neighborhoods are:

Neighborhood      Area

-	Petrovice  1.786429
-	Lysolaje  2.474802
-	Lochkov  2.716217
-	Benice  2.773783
-	Sterboholy  2.968908

The size of districts differs by more than 20 times. We can draw that information on a choropleth style map. These neighborhoods and markers were plotted with the help of Folium library. The dark green zone is the largest Prague 6 district on the left bank of the Vltava River. I used Google geocode API to find the coordinates of Prague.[5]
Unfortunately, folium maps are not correctly displayed through the pdf, so they can be seen in this report, although, not interactively. An interactive version of the map is available in Notebook at https://github.com/eyashin/Coursera_Capstone.
 
Next, we use Foursquare API to get 100 restaurants that are within a radius of 1500 meters from the center of each district. Then we make API calls to Foursquare in a Python loop. Foursquare returns the data in the JSON format and we extract the information from the following fields: neighborhood, Id, restaurant’s name, restaurant’s category, restaurant’s latitude and longitude.
We loaded 2028 items for analysis.
Then we calculate the number of restaurants and their density for every district. 
 
Than show top data by density and quantity
 
 
## Results:
One of the goals of my work was to visualize the Number of restaurants and their density per square kilometer with choropleth style map. 
 
We can see that districts on the right bank of the Vltava River are more interesting for restaurant business.
 
The areas with the largest number of restaurants are clearly visible without clustering.

## Discussion:
Our analysis shows that there is a great number of restaurants in Prague. If we take into consideration the quantity and density of restaurants the most interesting districts for business are:
-	Praha 1
-	Praha 2
-	Praha 3
-	Praha 7

## Conclusion:
The purpose of this project is to identify Prague districts for distributors of food, equipment, and services. Using data analysis I have prepared several recommendations. Of course, final decision on expanding business will be made by stakeholders and will be based on the level of competition, prices and other economic factors in every recommended district.

## Limitations:
In this project I used free Account of Foursquare API that came with limitations. The number of restaurants in one district is limited to 100.
