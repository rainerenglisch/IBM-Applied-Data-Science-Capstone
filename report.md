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
E.g.: "For address XYZ, 53229 Bonn, Deutschland the geograpical coordinate are 50.75860485, 7.150333800000002."
2. The geolocations of the target city's neighborhoods of the target city are retrieved. That is done via the python module geopy.
E.g.: "For address Berlin, Deutschland the geograpical coordinate are 52.5170365, 13.3888599."
3. For the home location the home neighborhood is explored by means of the Foursquare service venues/explore.
E.g.:  	


| Neighborhood | Neighborhood  Latitude | Neighborhood Longitude |	Venue |	Venue Latitude |	Venue Longitude 	|Venue Category |
| --- | --- | --- | --- | --- |--- |--- |
| Adlershof |	8 |	8 |	8 	|8 |	8 	|8|
|Alt-Hohenschönhausen| 	10| 	10| 	10| 	10| 	10| 	10|
|Alt-Treptow| 	26| 	26| 	26| 	26| 	26| 	26|
|Baumschulenweg| 	6| 	6| 	6| 	6| 	6| 	6|
|Biesdorf| 	6| 	6| 	6| 	6| 	6| 	6|

4. For this home neighborhood and the target city neighborhoods all the venues are fetched, categories counted and hot encoded.
5. By means of the euclidean distance , the similarity of the target neighborhood are compared with the home neighborhood. The top ten similar neighboorhoods are printed and displayed on a map.

