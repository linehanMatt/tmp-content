---
title: 'Location Datasets for POI attribute'
description: 'Narrative requires specific file types and formats when uploading location lists. '
lastUpdated: '2023-08-14T15:22:37.182Z'
tags: ['Buying Data', Data Studio']
---
Narrative provides many different types of filters for buyers looking to create data forecasts and queries. Location filters are an important part of the forecast/query process. Users can indicate areas of interest by providing rows of locations to match against providers' datasets. However, these location files must come in three specific types and formats in order for them to work with Narrative's system.

### File Types

This section outlines the three available file types and includes example files with the desired schemas. Each file covers locations for [the top five ice cream shops](https://www.gayot.com/restaurants/top-best-ice-cream-shops-in-the-usa.html) in the US with different respective formats.

#### GeoJSON format

Narrative accepts GeoJSON but only in .json, .parquet, or .geojson file formats. Narrative does not accept GeoJSON added into a CSV file. To learn more about GeoJSON and see an external example check out this [link](https://en.wikipedia.org/wiki/GeoJSON).

Within GeoJSON, Narrative only accepts [Polygon](http://geojson.org/schema/Polygon.json) [](http://geojson.org/schema/Polygon.json)and [MultiPolygon](http://geojson.org/schema/MultiPolygon.json) [](http://geojson.org/schema/MultiPolygon.json)schemas. Other schemas such as [LineString](http://geojson.org/schema/LineString.json) and [MultiPoint](http://geojson.org/schema/MultiPoint.json) are not accepted. [](http://geojson.org/schema/Polygon.json)Not sure if your GeoJSON is formatted correctly? Validate the format of your GeoJSON using this external [link.](https://geojsonlint.com/)

Here is a file that matches our required schema: [Ice Cream Shops](https://solutions.narrative.io/hubfs/IceCreamShops-2.json)

#### WKT in CSV format

Narrative also accepts WKT in CSV format. Narrative does not accept WKT in JSON format. To learn more about WKT use this external [link](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry). Here is a file that matches our required schema: [Ice Cream Shops](https://solutions.narrative.io/hubfs/IceCreamShops-1.csv)

#### Point Radius

Narrative also accepts Point Radius in TXT, JSON, Parquet and CSV formats. Each row contains a lon/lat point and a radius that extends around the point. Here is a file that matches our required schema in TXT format: [Ice Cream Shops](https://solutions.narrative.io/hubfs/IceCreamShops-1.txt) [](https://solutions.narrative.io/hubfs/IceCreamShops-1.txt)

### Resources

**Drawing Points**: Not sure how to change your desired area into one of our accepted formats? Here is a [free tool](https://boundingbox.klokantech.com/) that allows you to search for your location and create lon/lat coordinates for GeoJSON and Point Radius or WKT for polygons. You can explore any area using the search bar in the top left. Users should make sure they change to the desired format in the bottom left corner when copying over text.

**Lat/Lon Order**: Not sure which formats accept lat/lon vs lon/lat? Here is a [helpful breakdown](https://macwright.com/lonlat/) of all lat/lon formats, including the ones that Narrative accepts.  

Please reach out to <support@narrative.io> with any questions!
