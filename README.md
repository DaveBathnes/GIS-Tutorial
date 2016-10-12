# GIS Tutorial
Everyone loves maps.  An Introduction to GIS for Taunton Developers Meetup.

**Me:** Dave Rowe.  Microsoft Developer, Open Data Geek with love of maps.

This is a very high level overview of map technologies.

## Geographic coordinate systems

Wikipedia: [Geographic coordinate systems](https://en.wikipedia.org/wiki/Geographic_coordinate_system)

*A geographic coordinate system is a coordinate system that enables every location on the Earth to be specified by a set of numbers or letters, or symbols.[n 1] The coordinates are often chosen such that one of the numbers represents vertical position, and two or three of the numbers represent horizontal position. A common choice of coordinates is latitude, longitude and elevation.*

| Coordinate type |  X  |  Y  |
| --------------- | --- | --- |
| Latitude and Longitude. |  |  |
| Northings and Eastings. |  |  |

## Spatial reference systems

Wikipedia: [Spatial Reference System.](https://en.wikipedia.org/wiki/Spatial_reference_system)

*A spatial reference system (SRS) or coordinate reference system (CRS) is a coordinate-based local, regional or global system used to locate geographical entities.*

| Reference System | Coordinates used | Who by |
| ---------------- | ---------------- | ------ |
| British National Grid | Eastings/Northings | Ordnance Survey |
| World Geodetic System 84 | Longitude/Latitude | GPS |

## Geocoding and reverse-geocoding

**Geocoding:** Address -> Geo-coordinates.
**Reverse geocoding:** Geo-coordinates to address.


### Exercise: Geocode a batch of addresses

## Points, lines, and polygons

Typically when dealing with geo-spatial data, this will be in the form of Points, Lines, and Polygons.

Points - Individual locations on the ground.
Lines - Linear features made up of coordinates such as route lines.
Polygons - Bounded areas (shapes) made up of coordinates such as local authority boundaries. 

## Area geographies


## GIS software

Download and install: [QGIS]()


## Example: Add a vector layer in QGIS

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



## Geo-spatial databases

Most modern databases have some element of 'spatial' capability.
- SQL Server
- mySQL
- Oracle
- 


Download and install: [PostgresSQL]()
Download and install: [PostGIS]()


Take a traditional relational database 


### Example: Load data in PostGIS database and perform query
1. Load 

## Web development mapping libraries

JavaScript library: [Leaflet]()


### Example: Create leaflet map


## Online map tools

Create account: [Mapbox](https://www.mapbox.com/)
Create account: [Carto](https://carto.com/)

### Example: Carto

## Animated maps

An animated map can be a 

## Example: Carto animated map from timeline data.




## 3D


[CesiumJS]

## Cool maps

