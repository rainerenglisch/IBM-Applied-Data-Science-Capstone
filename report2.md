# Introduction / Business Problem
Employees or freelancers often need to move to another city when they change their employer. 
As it is hard to pick a matching neighborhood for a new place to live, 
it would be great if these persons receive recommendations of "target" neighborhoods based on their current neighborhood.

# Data
Input data:
1. The current *home address* and (e.g. Landgrabenweg 151, 53227 Bonn, Deutschland)
2. The *target city* including country  (e.g. Berlin, Germany)
3. An URL to the *target city's neighborhoods*

Output data:
1. Are the *recommended neighborhoods* in the target city ranked by their similarity regarding to the current home neighborhood.

## How will the output be computed?
1. The current home address needs to be transformed into geo location data that is longitude and lattitude. That is done via the python module geopy.
> E.g.: "For address XYZ, 53229 Bonn, Deutschland the geograpical coordinate are 50.75860485, 7.150333800000002."
2. The geolocations of the target city's neighborhoods of the target city are retrieved. That is done via the python module geopy.
> E.g.: "For address Berlin, Deutschland the geograpical coordinate are 52.5170365, 13.3888599."
3. For the home location the home neighborhood is explored by means of the Foursquare service venues/explore.
> E.g.:  


| Neighborhood | Neighborhood  Latitude | Neighborhood Longitude |	Venue |	Venue Latitude |	Venue Longitude 	|Venue Category |
| --- | --- | --- | --- | --- |--- |--- |
| Adlershof |	8 |	8 |	8 	|8 |	8 	|8|
|Alt-Hohenschönhausen| 	10| 	10| 	10| 	10| 	10| 	10|
|Alt-Treptow| 	26| 	26| 	26| 	26| 	26| 	26|
|Baumschulenweg| 	6| 	6| 	6| 	6| 	6| 	6|
|Biesdorf| 	6| 	6| 	6| 	6| 	6| 	6|

4. For this home neighborhood and the target city neighborhoods all the venues are fetched, categories counted and hot encoded.
> E.g.: 

| Neighborhood | Zoo Exhibit | ATM |	African Restaurant |	American Restaurant |	Argentinian Restaurant  	| Art Gallery|
| --- | --- | --- | --- | --- |--- |--- |
| Adlershof |	0 |	0|	0 	|0 |	0	|0|
|Alt-Hohenschönhausen| 	0| 	0| 	0| 	0| 	0| 	0|
|Alt-Treptow| 	0| 	0.1| 	0| 	0| 	0| 	0.7|
|Baumschulenweg| 	0| 	0.3| 	0| 	0| 	0| 	0|
|Biesdorf| 	0| 	0| 	0| 	0| 	0| 	0|


5. By means of the euclidean distance , the similarity of the target neighborhood are compared with the home neighborhood. The top ten similar neighboorhoods are printed and displayed on a map.

> E.g.: 

| Neighborhood | Rank | Distance |
| --- | --- | --- | 
| Adlershof |	1 |	0.1|
|Alt-Hohenschönhausen| 	2| 	0.3|
|Alt-Treptow| 	3| 	0.4|
|Baumschulenweg| 	4| 	0.5|
|Biesdorf| 	5| 	0.6|


# Methodology 
## First thoughts
First I thought about using k-means by putting the home neighboorhood into the list of target city's neighborhoods. That is, recommending the neighborhoods that would be in the same cluster as the home neighboorhood. However, I realized I wanted to have actually the features of my home location to be centroid. 
## Final thoughts
My final solution to the problem described in the introduction was derived from the clustering k-means approached that was shown in the neighborhood clustering notebook for New York in this course. 
In Summary what the k-means algorithm does is: It creates centroids where every observation (neighborhood) gets assigned to exactly one centroid.
Like in the example clustering notebook a feature vector was created for every neighborhood consisting of one hot encoded venue categories.
## Approach
My idea was 
1. to set the feature vector of the home neighborhood as the "centroid" like with k-means
2. to use euclidean distance to measure the distance of all observation (in that case the target city's neighborhoods feature vectors)
3. To rank the recommendation by that distance (the closer to zero the better).


# Results 
The jupyter notebook that ran with the home location "Buschweg, 53229 Bonn, Germany" and target city "Berlin, Germany". The goal was to find a neighborhood in Berlin that is similar to the one in Bonn.

## Map of top ten recommendations
![alt text](https://github.com/rainerenglisch/IBM-Applied-Data-Science-Capstone/raw/master/top_ten_recommended_neighboorhoods_map2.png "List of smallest distances to home neighborhood feature vector")

The winner neighborhood "Hakenfelde" lies in North West outer border of Berlin. 

# Discussion 
Hier I want to show the result of comparing my home neighborhood in Bonn with the neighborhoods in Berlin.

## Distribution of euclidean distances 
![alt text](https://github.com/rainerenglisch/IBM-Applied-Data-Science-Capstone/raw/master/distribution_distances.png "Distribution of distances")
The distance results are very interesting as it is skewed to right. Nearly 90% of the distances are around 1. That is, there are not many good matches. For other location in Bonn, I experienced a uniform distribution of the distances. 

## List of top ten neighborhoods with smallest distances
![alt text](https://github.com/rainerenglisch/IBM-Applied-Data-Science-Capstone/raw/master/top_ten_recommended_neighboorhoods_list.png "List of smallest distances to home neighborhood feature vector")

The top ten list confirms the observation that there are not many good matches. That is why it is surprising, we find an extremely good match in the neighborhood "Hakenfelde" which has a distance of nearly 0! The next best match is "Stadtrandsiedlung Malchow" with a distance of only around 0.7.

The winner neighborhood "Hakenfelde" lies in North West outer border of Berlin. Similarly, the home neighboorhood is at the North East border of Bonn.

# Conclusion 
The comparison of venues seems to work quite well. Of course, for a comprehensive comparison of neighborhoods more than data about venues are needed. For instance, socio-economic information could be used about income, age distribution. Aswell, it could be nice that if a person could up- or downvote features of his or hers home neighborhood in order to find a better even better match in the target city.

# A link to Notebook 
This is the link to my notebook:

[I'm an inline-style link](https://github.com/rainerenglisch/IBM-Applied-Data-Science-Capstone/blob/master/my_capstone.ipynb)


# Your choice of a presentation or blogpost. (10 marks)
