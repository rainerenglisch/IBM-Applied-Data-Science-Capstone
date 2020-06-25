# Introduction / Business Problem
Employees or freelancers often need to move to another city when they change their employer. 
As it is hard to pick a matching neighborhood for a new place to live, 
it would be great if these persons receive recommendations of "target" neighborhoods based on their current neighborhood.

# Data
Input data:
1. would be the current *home address* and (e.g. Landgrabenweg 151, 53227 Bonn, Deutschland)
2. the *target city* including country  (e.g. Berlin, Germany)
3. the *target city's neighborhoods *

Output data:
1. are the *recommended neighborhoods* in the target city ranked by their similarity regarding to the current home neighborhood.

## How will the output be computed?
1. The current home address needs to be transformed into geo location data that is longitude and lattitude. That is done via the python module geopy.
2. The geolocations of the target city's neighborhoods of the target city are retrieved. That is done via the python module geopy.
3. For the home location the home neighborhood is explored by means of the Foursquare service venues/explore.
4. For this home neighborhood all the venues are fetched, categories counted and hot encoded.
5. For the target city location all the  neighborhoods are fetched and their venues fetched, categories counted and one hot encoded.
6. Together with the "source" neighborhood the target neighborhoods they are clustered via kmeans.
7. All the "target" neighborhoods that are in the same cluster as the "source" neighborhood are considered as recommended similar neighborhoods
8. A map is shown that flags all recommended similar neighborhoods in the target city.

The result can be computed by relying only on the Foursquare location data.
