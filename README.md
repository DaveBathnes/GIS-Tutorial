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
**Reverse geocoding:** Geo-coordinates -> Address.  Usage example: taking coordinates retrieved from GPS to determine current location.

**Geofencing:**  A feature in a software program that uses the global positioning system (GPS) or radio frequency identification (RFID) to define geographical boundaries. A geofence is a virtual barrier.

### Exercise: Geocode a batch of addresses

1. Go to [Batch Geocoder](https://www.doogal.co.uk/BatchGeocoding.php)
2. Copy data from file [/data/SomersetLibraryAddresses.csv](SomersetLibraryAddresses.csv) into input field.
3. Press geocode.

## Points, lines, and polygons

Typically when dealing with geo-spatial data, this will be in the form of Points, Lines, and Polygons.

**Points** - Individual locations on the ground.
**Lines** - Linear features made up of coordinates such as route lines.
**Polygons** - Bounded areas (shapes) made up of coordinates such as local authority boundaries and geofences.

## File formats

There are many different formats for storing geo data.  These are a few of them.

| Format | Description | Example |
| ------ | ----------- | ------- |
| GeoJSON | JavaScript Object Notation (JSON) style geo data. | [/data/Somerset School Catchment Areas 2014-15.geojson](Somerset School Catchment Areas) |
| Shapefiles | Format developed by ESRI for storing geospatial data.  More than one file!  | [/data/]() | 
| KML | XML type format for storing geospatial data. Used by Google Earth and Google fusion tables. |  |

## GIS software

Download and install: [QGIS](Quantum GIS)

## Exercise: Add multiple layers in QGIS
1. Open up QGIS
2. Choose a 


## WMS and WFS (and WMTS)

WMS and WFS are ways of dealing with geo data through web services.

WMS - Web Map Service.  Typically used to provide map images (typically as raster tiles)
WFS - Web Feature Service.  Provides feature information, then used to display on a map.

## Exercise: Add a WFS layer in QGIS.




## Geo-spatial databases

Most modern databases have some element of 'spatial' capability.
- SQL Server
- mySQL
- Oracle
- PostGIS

Download and install: [PostgreSQL - Open Source database](https://www.postgresql.org/)
Download and install: [PostGIS - Spatial functionality for PostgreSQL](http://www.postgis.net/)


Take a traditional database table: Libraries

| Name | Authority |
| --------- | ---- |
| Taunton Library | Somerset |
| Bath Central Library | Bath and North East Somerset |
| Box | Wiltshire |
| Newcastle Central Library | Newcastle |


An individual is a member of Somerset.  Find all libraries in their authority.

``` 
SELECT Name FROM Libraries  WHERE Authority = 'Somerset'
```

How about the query: Find all libraries within 5 miles of an individual?

```
SELECT Name FROM Libraries 
WHERE ST_DWithin(ST_SetSRID(ST_MakePoint(Lng,Lat)::geography, 4326), ST_SetSRID(ST_MakePoint(-3.106849,51.015344), 4326)::geography, 8046)
```

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

