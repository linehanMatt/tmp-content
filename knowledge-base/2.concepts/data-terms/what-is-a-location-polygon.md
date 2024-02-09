---
title: 'What is a location polygon?'
description: 'A location polygon is a shape that represents a point of interest using geospatial coordinates.'
lastUpdated: '2023-06-09T15:42:00.187Z'
tags: ['Data Types', 'Location']
---
### Overview

A location polygon is an object that represents a place, point of interest, or location in the real world. Polygons are usually represented by the coordinates of their vertices. A polygon may have any number of vertices and any number of edges. The coordinates of the vertices are typically represented using WGS84 latitude and longitude pairs.

Because polygons can represent real-world locations they are often used to add context to location data. When collected, location data typically consists of the latitude, longitude, and altitude along with metadata about the device and time it was collected. Those attributes on their own have less value than if they can be mapped to a location that provides context for the location. For example the latitude _40.74576, -73.9848_ would have little meaning by itself, but if it could be mapped to the Narrative Headquarters, the record would have additional context and would be easier to use.

### Examples

#### A polygon representing Oracle Park in San Francisco

![Oracle Park geoJSON Polygon](https://solutions.narrative.io/hubfs/KB/Concepts/Screen%20Shot%202020-01-21%20at%209.15.18%20AM.png)

#### A polygon representing the borough of Manhattan in New York City

![Manhattan Borough NYC Polygon](https://solutions.narrative.io/hubfs/KB/Concepts/Screen%20Shot%202020-01-21%20at%209.27.14%20AM.png)

### Encoding Polygons

Location can be encoded using a number of different standards. While the underlying file format and contents may differ, largely each standard is representing the same fundamental object, a location polygon.

* **geoJSON**: [geoJSON](https://en.wikipedia.org/wiki/GeoJSON) is a standard that is based on JSON making it easy to parse in commonly used programming languages. The files can also be read and edited in a text editors
* **Shapefile**: [Shapefiles](https://en.wikipedia.org/wiki/Shapefile) are based on an open specification.  Unlike geoJSON, shapefiles require custom libraries to use and are harder to parse/understand by humans.
* **WKT**: WKT stands for [well-known text representation of geometry](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry) and is another format used to encode polygons. This format typically requires third-party libraries to parse. It is text-based so WKT files can be edited using a text editor, but the syntax is typically hard for humans to easily parse.
* **Point + radius**: Point + radius is not a standard, and technically not a polygon, is when locations are represented by their midpoint and a circle is drawn around the midpoint at a specified radius. Point + radius is most often used when the borders of a point of interest are not known. Many systems will draw a polygon from the point + radius by choosing a number of vertices and using the radius to extrapolate those vertices (seen below).

![Polygon from a circle](https://solutions.narrative.io/hubfs/KB/Concepts/wZbsJ.png)

### Additional Resources

Wikipedia: [World Geodetic System](https://en.wikipedia.org/wiki/World_Geodetic_System)

Github: [GeoJSON of Major/Minor league ballparks](https://github.com/cageyjames/GeoJSON-Ballparks)
