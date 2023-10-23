# IBM_coursera_capstone
This repo contains the relevant files for the coursera course.

# Restaurant Location Recommendation in New York State.  

## 1. Introduction
### 1.1 Background
People love to eat good food and different cuisine restaurants have provided them to taste
various delicacies. Restaurants have always played a crucial role in business, social life of the
society. Many personal and professional events happen at restaurants. But a restaurant's
investment and maintenance costs would be high. So every restaurant owner wants to get a
high return on their investments. The taste of food, ambience and the location of the restaurant
are few major contributing factors for a successful restaurant.

### 1.2 Problem
Consider the following hypothetical scenario :
**Resto-grand** a successful multi-chained restaurant company has its brands around Europe,
India, California. They wanted to start their restaurants in New York state and required some
suggestions on where to open them.
The aim of the project is to find suitable locations for the restaurants in New York state.

### 1.3 Audience
Here **'Resto-grand'**’s business owners to whom we are preparing the report is the target
audience. But this report can be used by other business people who want to find a suitable
location to open a restaurant in New York state.

## 2. Data
To tackle the above mentioned problem, we need to have the dataset that contains :
● Cities present in New York State.
● Latitude and Longitude locations of the cities of New York state.
● Top venues present in each city of New York state.

### 2.1 Data Sources
● List of cities present in New York state can be obtained from wikipedia’s page :
( https://en.wikipedia.org/wiki/List_of_cities_in_New_York )
● Latitude and Longitude locations of them can be found using python's geopy package.
● We will use foursquare.com’s API to find the most common venues present at given
geographical coordinates.

### 2.2 Description of data
The below output is obtained after cleaning the data acquired from wikipedia’s page and using
python’s geopy package. Each row represents a city in New York state, its county, population
and geographical coordinates.
We will use foursquare’s API to find the most common venues present around the 30 km radius
of each city of New York.

## 3. Methodology
The first step is to collect data about cities of New York state from the wikipedia page at the
following link ( https://en.wikipedia.org/wiki/List_of_cities_in_New_York ). There are 62 cities in New
York state.

### 3.1 Data cleaning and exploration
Then we tidy up the data to contain city, county, population columns. We will use this data to find the
geographical coordinates of each city using python’s geopy package and the top 5 rows of data is as
follows -
Using folium, a map rendering software we shall just see the location of cities on the world map.
The blue points represent our 62 cities in New York state.
Later we use foursquare’s api to find the list of venues around a city (‘Amsterdam’) to see where we
get necessary venues in that city. We will restrict the limit of venues obtained to 100 and which are
present around 30 km radius of the city. Once we receive the response in json format, we will tidy it
up and represent it in a dataset having venue’s name, its category and its geographical coordinates.
The top 5 rows of the dataset is shown below -
As we can see, we got 100 venues with 44 unique categories in Amsterdam. It contains restaurants
as well.
We generalize this and find the venues around 30km in each city of New York state and create a
dataframe which consists of venue's name,category,geographical location along with to which city it
belongs and city’s geographical location. The top 5 rows are shown below :
Later we use the one-hot encoding technique on the 'Venue Category' column to find the unique
venues present in the city / neighborhood and then calculate the frequencies of venues present
in each city. Finally we obtain a dataset each row containing the city name and the top 10 most
common venues in that city. A portion of it can be seen below -

### 3.2 Machine Learning method
As we have data available for our machine learning model we shall proceed this step by using
an unsupervised algorithm as we don’t have any labelled data. We use the KMeans Clustering
algorithm that arranges the similar cities into a cluster and dissimilar cities in different clusters.
For this algorithm we need to pass a parameter called number of clusters. The optimal value of
this can be found by using the KElbowVisualizer module in the yellowbrick package.
From the above graph, we can see the value of k = 7. So, we will input this value as the number
of clusters into KMeans algorithm and fit the dataset containing the top 10 most common
venues in each city. When done, we add the cluster labels to the dataset. The first 5 rows of the
table are shown below -

## 4. Results
We shall merge the above dataset with the dataset which has the city's geographical details. We
can slice the data into 7 different clusters as per the 7 cluster labels(0,1,2,3,4,5,6).
### 4.1 Cluster - 0
Cluster 0 contains cities where parks, bakeries, gyms are priority in the top most venues.
### 4.2 Cluster - 1
Cluster 1 contains the cities where cafes, bars, restaurants, ice cream shops are priority in the
top most venues.
### 4.3 Cluster - 2
Cluster 2 contains the cities where many restaurants, pizza places and bars are priority in the
top most venues.
### 4.4 Cluster - 3
Cluster 3 contains the cities where discount stores, sandwich and pizza places are priority in the
top most venues.
### 4.5 Cluster - 4
Cluster 4 contains the cities where coffee shops, pizza places , ice cream shops are priority in
the top most venues.
### 4.6 Cluster - 5
Cluster 5 contains the cities where convenience stores, sandwich places and restaurants are
priority in the top most venues.
### 4.7 Cluster - 6
Cluster 6 contains the cities where pizza places and bakeries are priority in the top most
venues.

## 5. Discussions and recommendations
Based on what we have learned about the clusters, we can advise the **'Resto-grand'**’s business
owners to consider the cities from Cluster-2 as the most suitable location for their restaurants.
These are the cities that are well represented by the restaurants, other bar and pizza places.
This shows there is very high demand in the locality for the restaurant and in turn can be
successful provided proper ambience and taste of the food. All the blue colored circles
represent this cluster.

## 6. Conclusion
In this project we discussed the process of solving a hypothetical real world scenario of finding
suitable locations for opening a restaurant in New York state. The analysis is done mainly using
the python and python libraries such as pandas, scikit-learn, folium, yellowbrick to name a few.
We made use of the foursquare api to find the popular venues and its categories present in the
city within a 30km radius. KMeans unsupervised machine learning algorithm was used to group
these cities into clusters after knowing the top most venue category in each city.
