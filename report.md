# Introduction / Business Problem
Employees or freelancers often need to move to another city when they change their employer. 
As it is hard to pick a matching neighborhood for a new place to live, 
it would be great if these persons receive recommendations of "target" neighborhoods based on their current neighborhood.

# Data
Input data would be the current home address and the target city. 
Output data are the neighborhoods in the target city ranked by their similarity regarding to the current neighborhood.
The current address and the target city need to be transformed into geo location data that is longitude and lattitude. That is done via the service *xyz*.
- For the current location the neighborhood is identified by means of the Foursquare service *xyz*.
- For this neighborhood all the venues are fetched and transformed into one hot encoded category counts.
Example:
- Then again the geo location of the target city is queried.
- For the target city location all the  neighborhoods are fetched, venues fetched, categories counted and one hot encoded.
- Together with the "source" neighborhood the target neighborhoods are clustered via kmeans.
- All the "target" neighborhoods that are in the same cluster as the "source" neighborhood are considered as recommended similar neighborhoods
- A map is shown that flags all recommended similar neighborhoods in the target city.
The result can be computed by relying only on the Foursquare location data.
