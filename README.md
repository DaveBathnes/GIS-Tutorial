# GIS Tutorial
Everyone loves maps.  An Introduction to GIS for Taunton Developers Meetup.

**Me:** Dave Rowe.  Microsoft Developer, Open Data Geek with love of maps.

This is a very high level overview of map technologies.

## Geographic coordinate systems

Wikipedia: [Geographic coordinate systems](https://en.wikipedia.org/wiki/Geographic_coordinate_system)

*A geographic coordinate system is a coordinate system that enables every location on the Earth to be specified by a set of numbers or letters, or symbols.[n 1] The coordinates are often chosen such that one of the numbers represents vertical position, and two or three of the numbers represent horizontal position. A common choice of coordinates is latitude, longitude and elevation.*

| Coordinate type |  X  |  Y  |
| --------------- | --- | --- |
| Longitude and Latitude. | -3.106849 | 51.015344 |
| Eastings and Northings. | 322454 | 124580 |

## Spatial reference systems

Wikipedia: [Spatial Reference System.](https://en.wikipedia.org/wiki/Spatial_reference_system)

*A spatial reference system (SRS) or coordinate reference system (CRS) is a coordinate-based local, regional or global system used to locate geographical entities.*

| Reference System | Coordinates used | Who by |
| ---------------- | ---------------- | ------ |
| British National Grid | Eastings/Northings | Ordnance Survey |
| World Geodetic System 84 | Longitude/Latitude | GPS |

- Converter [Coordinate Converter - British Geological Survey](http://www.bgs.ac.uk/data/webservices/convertform.cfm)

**Why do we have different spatial reference systems?**

A spatial reference systems defines how to to plot features on the curved surface of the earth to a flat paper or computer screen.  As the earth is different in different parts of the world we need different spatial reference systems.

## Geocoding and reverse-geocoding

Geocoding and reverse geocoding are ways of matching address and location data with geo-coordinates.

**Geocoding:** Address -> Geo-coordinates.  Usage example: Plotting a user address search onto a map.
**Reverse geocoding:** Geo-coordinates to address.  Usage example: taking coordinates retrieved from GPS to determine current location.

### Exercise: Geocode a batch of addresses

1. Go to [Batch Geocoder](https://www.doogal.co.uk/BatchGeocoding.php)
2. Copy data from file []().
3. 

## Points, lines, and polygons

Typically when dealing with geo-spatial data, this will be in the form of Points, Lines, and Polygons.

**Points** - Individual locations on the ground.
**Lines** - Linear features made up of coordinates such as route lines.
**Polygons** - Bounded areas (shapes) made up of coordinates such as local authority boundaries. 

## Area geographies





## File formats

| Format | Description | Example |
| GeoJSON | JavaScript Object Notation (JSON) style geo data. | [/data/Somerset] |
| Shapefiles |  |
| TAB files |  |
| KML |  |   |
| CSV |   |


## WMS and WFS (and WMTS)

WMS and WFS are ways of dealing with geo data through web services.

WMS - 
WFS - 

|  |  |
|  |  |


WMTS - 

| Tile service |  |
| Google  |  |
| Carto |  | 
| Bing |  |
| MapBox |  |
| OpenStreetMap |  |


## GIS software

Download and install: [QGIS]()

## Exercise: Add multiple layers in QGIS
1. Open up QGIS
2. Choose a 



## Geo-spatial databases

Most modern databases have some element of 'spatial' capability.
- SQL Server
- mySQL
- Oracle
- 


Download and install: [PostgresSQL]()
Download and install: [PostGIS]()


Take a traditional relational database:


| Person ID | Name | Postcode |
| --------- | ---- |
| 1 | Dave |
| 2 | Sarah |
| 3 | Tom |


Table 2: Postcodes
| Postcode ID | Postcode |


Find all
``` 
SELECT name FROM People  WHERE Postcode = 'BA1 6AX'
```

How about the query: Find all people 


### Example: Load data in PostGIS database and perform query
1. Load in 
2. 

## Web development mapping libraries

JavaScript library: [Leaflet]()


### Example: Create leaflet map


## Online map tools

Create account: [Mapbox](https://www.mapbox.com/)
Create account: [Carto](https://carto.com/)

### Example: Carto postcode data.

## Animated maps

An animated map can be a great way of providing a data visualisation.

## Example: Carto animated map from timeline data.

