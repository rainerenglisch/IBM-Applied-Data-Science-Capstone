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
section which represents the main component of the report where you discuss and describe any exploratory data analysis that you did, any inferential statistical testing that you performed, if any, and what machine learnings were used and why.

My solution to the problem described in the introduction was derived from the clustering k-means approached that was shown in the neighborhood clustering notebook for New York in this course. 
In Summary what the k-means algorithm does is: It creates centroids where every observation (neighborhood) gets assigned to exactly one centroid.
My idea was 
1. to set the feature vector of the home neighborhood as the "centroid" like at k-means
2. to use euclidean distance to measure the distance of all observation (in that case the target city's neighborhoods feature vectors)
3. To rank the recommendation by that distance (the closer to zero the better).


# Results 
section where you discuss the results.
# Discussion 
section where you discuss any observations you noted and any recommendations you can make based on the results.
# Conclusion 
section where you conclude the report.

# A link to Notebook 
on your Github repository pushed showing your code. (15 marks)

# Your choice of a presentation or blogpost. (10 marks)
