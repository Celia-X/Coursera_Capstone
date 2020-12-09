# <center>Business choice and data analysis of Beijing</center>

## 1. Introduction

<div style="text-align: justify">  As well known, Beijing is the capital city in China and one of the largest metropolis cities in the world. It is the nation's political, cultural and educational center. The current metro area population of Beijing Municipality in 2020 is 20,463,000 in an area of 16,800 square kilometers. It is therfore considered as one of the most densely populated cities. There are however lots of business-development opportunities and challenges, which makes this super city more attractive and more competitive. </div>

<div style="text-align: justify"> Beijing is divided into 16 districts as shown in the Figure 1.1 below. Different districts have not only different area sizes and population, but also various venues. From the perspective of a business investor, espacially in the field of sales and marketing, it should be very interesting to learn the details of the city. Considering that Beijing is a crowded city, which may result in more potential consumers, a business inverstor would like to start his business in this city. Although there is a great market, the investor should also think about the type of business he will start. The optimal solution as expected should be the district with high cosumption potential but few competitors. </div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-administrative-map.jpg" style="zoom:50%" />

 **<center>Figure 1.1 Beijing Districts Map</center>**

<div style="text-align: justify">The following 2 problems are tried to be solved with the help of data analysis:</div>
<div style="text-align: justify">The situation is that a business investor decides to start his business in Beijing.</div>
<div style="text-align: justify">1. which districts would be a better choice?</div>
<div style="text-align: justify">2. which type of business can be started in the corresponding area?</div>

<div style="text-align: justify">In order to find answers for these questions and support decisions of the business investor, the population density, consumption level and the common venues of each district in Beijing will be studied.</div>

## 2. Data description

* <div style="text-align: justify">The basic data of Beijing is scrambled from Wikipedia, which provides the administrative divisions of the city and the population density of each district. The data should be cleaned and only the useful information such as "district name" and "density" need to be retained. Intense population density means that there would be lack of resources, which may lead to higher operation costs.</div>

* <div style="text-align: justify">Consumption level could represent the market potential. To measure the consumption level of each district, the parameter "Total Retail Sales of Consumer Goods"(TRSCG) is selected from the National Bureau of Statistics of China. In this capstone, the newest data in 2019 will be summarized and it will be processed to gain the "Total Retail Sales of Consumer Goods per Person" in each district.</div>

* <div style="text-align: justify">The geo.json file can be obtained from Aliyun, which contains all districts of Beijing. With the help of the geo.json file, data visualizaition of each district in Beijing can be carried out.  </div>

* <div style="text-align: justify">By using Google Map, the latitudes as well as the longitudes of each district's certer can be gathered and the data can be visualized on OpenStreetMap.</div>

* <div style="text-align: justify">Foursquare API can be used to get the common venues of the given districts in Beijing. Based on this data, the features of the districts can be further analyzed and the districts can also be clustered.</div>

## 3. Methodology

<div style="text-align: justify">Python 3.7 is used to deal with the data after data collection and cleaning. The master data contains the following components "District","Chinese","Density","Consumption Level/Person" as shown in the Figure 3.1. "Chinese" is remained to match the geo.json file for the data visualization.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-master%20data.png" style="zoom:50%" />

 **<center>Table 3.1 Master Data for the Analysis</center>**

<div style="text-align: justify">A chart with horizontal bars is generated to explain whether there is a relationship or similarity between population density and consumption level per person in each districts. Figure 3.2 make the comparison between these two factors visible. As shown in the figure, there is no similar distribution structure between population density and consumption level. Although Dongcheng District and Xicheng District have obvious intense population density, the differences of consumption level per person between these districts and other districts are not so big compared with the differences of the population density.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-comparison.png" style="zoom:50%" />

 **<center>Figure 3.1 Comparison between population density and consumption level in each districts</center>**

<div style="text-align: justify">A visualization on the map can make the comparison more clearly, therefore, choropleth map in created to visualize the population density and consumption level per person in each districts on geograpical perspective.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-density.png" style="zoom:25%" />

 **<center>Figure 3.2 Population density in the choropleth map</center>**

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-consumption.png" style="zoom:26%" />

 **<center>Figure 3.3 Personal consumption level in the choropleth map</center>**

<div style="text-align: justify">Population density influences the resources in the area, higher population density may result in higher price for renting. Thus, the population density can be seen as a cost parameter. Personal consumption level represents the consumption capacity in the area. Districts with higher personal consumption level should be a good place to start a business. Considerung of this two aspects, a new parameter "Personal consumption level/population density" was defined, which can represent the relationship between the market potential and the business start-up cost. The higher the parameter is, the better market to entry is.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-c%3Ad.png" style="zoom:24.8%" />

 **<center>Figure 3.4 Attractiveness of each district for business investor</center>**

<div style="text-align: justify">After general understanding of the districts in Beijing, it is time to analyze the business type can be chosen. Hence, the common venues in each district and how the districts can be clustered need to be carried out. Firstly, the geographical coordinates (including latitudes and longitudes) are gained with the help of the geocoder package. Then, the geographic details can be visulized on the map, which is shown in the figure below.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-coordinates.png" style="zoom:50%" />

 **<center>Table 3.2 Geographic coordinates of each districts in Beijing</center>**

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-map.png" style="zoom:33%" />

 **<center>Figure 3.5 Geographic details of districts in Beijing</center>**

<div style="text-align: justify">The 16 districts need to be explored by the Foursquare API and they should be segmented. Therefore, the limit of 100 venues and the radius of 2000 meters for each district are defined. The following figure domonstrates the venues of each district. It is obvious that Dongcheng District, Xicheng District and Haidian District gain more venues. On the other hands, the venues of other districts are much less. However, the result depends on the given geographical coordinates and the radius. If the given information is more detailed, the result should be more abundant. </div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-venue.png" style="zoom:50%" />

 **<center>Figure 3.6 Number of venues of different districts in Beijing</center>**

<div style="text-align: justify">The Foursquare API returns the 10 most common venues in each district. Table below shows the outcome.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-top%2010.png" style="zoom:50%" />

 **<center>Table 3.3 10 most common venues in each district</center>**

<div style="text-align: justify">K-Means algorithm is one of the most common cluster methods of unsupervised learning and it is used in this section. However, the optimal K can not be determined with Elbow-Method as shown in the Figure 3.7,which represents that Elbow-Method is not suitable for this situation. Therefore, a user-defined K-Value is carried out. Considering of the amounts of the districts to be segemented, here K-Value is set to be 3. </div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-k.png" style="zoom:50%" />

 **<center>Figure 3.7 K-Values with Elbow-Method</center>**

<div style="text-align: justify">With the defined K-Value = 3, the districts would be segmented in 3 clusters. In order to find the characteristics of each districts, the numbers of venues in each cluster are summarized below. Here the 1st common avenues of each district are selected.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-cluster.png" style="zoom:50%" />

**<center>Figure 3.8 Venues of Different Districts in Beijing</center>**

<div style="text-align: justify">Figure 3.8 shows that cluster 0 is a "multi-function-district" since there are many venues with different functions. Cluster 1 is "restaurant-district" as only "Chinese Restaurant" is the 1st common venue. Moreover, cluster 2 can be defined as "hotel-tourist-district", according to the analysis.</div>

### 4. Results

<div style="text-align: justify">Based on the data processed and analyzed in Section 3, the final result is represented in the Figure 4.1 below. Red points indicate the districts in cluster 0 "multi-function-district", purple point shows the districts in cluster 1 "restaurant-district", while green points represent district in cluster 2 "hotel-tourist-district". The attractiveness of each districts for the business investor can be told by the area filled with color green. The darker the color is, the more attractive the district is.</div>

<img src="https://raw.githubusercontent.com/Celia-X/Coursera_Capstone/main/beijing-final-cluster.png" style="zoom:33%" />

 **<center>Figure 4.1 Conparison between population density and consumption level in each districts</center>**

### 5. Discussion

<div style="text-align: justify">As  mentioned before, the user-defined parameter "personal cosumption level/population density" represents the possibility of return on invest and helps to determine the attractiveness of the districts. In the figure, Huairou District, Yanqing District and Miyun District are filled with dark green, which means that these districts seems to be more attractive for the business investor. Huairou District is "multi-fuction". If it is chosen to start a new business, Chinese restaurant may not be a recommendation, since it is the most common venues in cluster 0. Yanqing District and Miyun District are segemented as "hotel-tourist-district" are also good choices for business starting. The most common venues in this cluster are hotels and resorts.To start the business these areas, there are many choices. However, the further analysis should focus more on details and the data should be expanded into neighbourhoods or streets. </div>

<div style="text-align: justify">During the analysis, it shows that not every data analysis method can yield the result with high quality, such as Elbow-Method is not suitable to find the optimal K-value in this work. Therefore, to choose the approporiate method for data analyzing is also an essential part for the analysis.</div>

### 6. Conclusion

<div style="text-align: justify">Super city can bring chances as well as challenges to the business investor. A better result can be expected, if the investor can summarize information from the historical data.</div>

<div style="text-align: justify">The data analysis can help not only busniess investor but also other characters with their decision making and lead to a more profitable outcome.</div>


```python

```
