# Wakiso-Land-Value-Prediction
Notebooks for each of the Sub-counties in Wakiso District; Each containing all the data processing, feature engineering and final trained models to be deployed.

![Capture2](https://user-images.githubusercontent.com/32632588/136689382-cbff16ea-63f0-41b0-b4b7-462c75c59ed5.PNG)

**THE VARIABLES**

**1.NUMERICAL VARIABLES**

**a) Distance variables**

Location is a major influence in variations in Land values. Based on this hypothesis, most of the variables for each subcounty were calculated based on geodesic distance from;

i) Trading centres

ii) Schools (Primary, Secondary and Tertiary Insitutions)

iii) Health Centres (Mainly government health centres)

The GPS location Cordinates of each of these landmarks was extracted using the Google Geocoding API 

**b) Acreage**

This is size of each parcel of land in acres.

**c) Years**

This is calculated as the time period between when the parcel was valued and now.




**2. CATEGORICAL VARIABLES**

**a) Use**

The is the type of land use of the parcel at the time of valuation.

**b) Neighborhood (submarket)**

The different submarkets were obtained based on accessibility using the road network by;

i) Extracting the road networks of each subcounty from Open Street map using OSMNX, an open source Python Package

With the nodes;

![kiwatule_street_network](https://user-images.githubusercontent.com/32632588/136694850-9e241c58-4f96-4178-b066-3ab4f6ba573a.png)

With out the nodes;

![nonodes](https://user-images.githubusercontent.com/32632588/136696152-70590a66-5581-4ac3-8bb2-c5d3c39fc278.PNG)

ii) The street networks nodes were then clustered using cdlib,an open source Python library which returns a lists in a list, representing communities and implying the different property submarkets in a subcounty

iii) A bounding box, representing each submarket is then obtained by extracting the maximum and minimum GPS Cordinates for each submarket

iv) Based on the location of a parcel, it is assigned to a property submarket.

**c) Buffer region**

A buffer region on the road network was extracted based on the most accessible nodes/ roads on the network, represented by a boundary box.
The measure of this accessibility is measured by node centrality also known as the centrality measure using the networkx open source Python Library, shown below;

![Centrality](https://user-images.githubusercontent.com/32632588/136696735-ecba3216-81a1-4f9b-bd61-79b6a9c35efe.PNG)

For each land parcel, a categorical binary variable is given; 1 for if it falls within the buffer region and 0 for when it does not.

**d) Central Point**

This is a numerical variable obtained by measuring the  distance of each land parcel from the most accessible or most central point on the road network. This is measured by betweenness centrality as shown below;

![betweenness](https://user-images.githubusercontent.com/32632588/136697492-fe6667b3-d9e3-47cc-bfa8-0bb071677591.PNG)

The most central point is represented by the red point in the image below;

![Central](https://user-images.githubusercontent.com/32632588/136697410-3bdb25bf-254c-481d-9e8d-b14730e84893.PNG)

4.Namayumba Sucounty;
