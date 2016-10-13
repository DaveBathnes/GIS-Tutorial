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

- **Geocoding:** Address -> Geo-coordinates.  Usage example: Plotting a user address search onto a map.
- **Reverse geocoding:** Geo-coordinates -> Address.  Usage example: taking coordinates retrieved from GPS to determine current location.
- **Geofencing:**  A feature in a software program that uses the global positioning system (GPS) or radio frequency identification (RFID) to define geographical boundaries. A geofence is a virtual barrier.

### Exercise: Geocode a batch of addresses

1. Go to [Batch Geocoder](https://www.doogal.co.uk/BatchGeocoding.php)
2. Copy data from file [SomersetLibraryAddresses.csv](/data/SomersetLibraryAddresses.csv) into input field.
3. Press geocode.

### Exercise: Reverse geocode a batch of coordinates
1. Go to [Batch reverse geocoder](https://www.doogal.co.uk/BatchReverseGeocoding.php)
2. Copy data from file [/data/SomersetLibraryCoordinates.csv](/data/SomersetLibraryCoordinates.csv)
3. Press reverse geocode.

## Points, lines, and polygons

Typically when dealing with geo-spatial data, this will be in the form of Points, Lines, and Polygons.

- **Points** - Individual locations made up of a single coordinate set.
- **Lines** - Linear features made up of coordinates such as route lines.
- **Polygons** - Bounded areas (shapes) made up of coordinates such as local authority boundaries and geofences.

## File formats

There are many different formats for storing geo data.  These are a few of them.

| Format | Description | Example |
| ------ | ----------- | ------- |
| GeoJSON | JavaScript Object Notation (JSON) style geo data. | [/data/Somerset School Catchment Areas 2014-15.geojson](Somerset School Catchment Areas) |
| Shapefiles | Format developed by ESRI for storing geospatial data.  More than one file!  | [/data/]() | 
| KML | XML type format for storing geospatial data. Used by Google Earth and Google fusion tables. | [SomersetLibraries](/data/SomersetLibraries.kml) |

## GIS software

The traditional way of working with GIS data is through Desktop applications

- [ESRI ArcDesktop](http://www.esri.com/software/arcgis/arcgis-for-desktop) - World leader for GIS software
- [MapInfo](http://www.pitneybowes.com/us/location-intelligence/geographic-information-systems/mapinfo-pro.html) - Acquired by Pitney Bowes Business Insight
- [Quantum GIS](http://qgis.org/en/site/) - Open Source option.  Brilliant.

Download and install: [Quantum GIS](http://qgis.org/en/site/)

## Exercise: Add a layer in QGIS
1. Open up QGIS
2. Choose Layer > Add layer > Add vector layer
3. Select the file [Somerset School Catchment Areas 2014-15](/data/Somerset School Catchment Areas 2014-15.geojson)

## WMS and WFS (and WMTS)

WMS and WFS are ways of dealing with geo data through web services.

**WMS** - Web Map Service.  Typically used to provide map images (typically as raster tiles)
**WFS** - Web Feature Service.  Provides feature information, then used to display on a map.

## Exercise: Add a WFS layer in QGIS.

| Data | Service URL |
| ---- | ----------- |
| Taunton Allotments | http://inspire.misoportal.com/geoserver/taunton_deane_borough_council_allotments/wfs?service=wfs&version=2.0.0&request=GetCapabilities |
| Taunton Parks and Recreation | http://inspire.misoportal.com/geoserver/taunton_deane_borough_council_parks_and_recreation_gardens/wfs?service=wfs&version=2.0.0&request=GetCapabilities |
| Taunton Play areas | http://inspire.misoportal.com/geoserver/taunton_deane_borough_council_play_areas/wfs?service=wfs&version=2.0.0&request=GetCapabilities |
| Taunton Tree Preservation Orders | http://inspire.misoportal.com/geoserver/taunton_deane_borough_council_tpos_06completed1/wfs?service=wfs&version=2.0.0&request=GetCapabilities |
| Taunton Car Parks | http://inspire.misoportal.com/geoserver/taunton_deane_borough_council_car_parks/wfs?service=wfs&version=2.0.0&request=GetCapabilities |

Add WMTS: https://api.mapbox.com/styles/v1/mapbox/streets-v10/wmts?access_token=pk.eyJ1IjoibGlicmFyaWVzaGFja2VkIiwiYSI6IlctaDdxSm8ifQ.bxf1OpyYLiriHsZN33TD2A

## Geo-spatial databases

Most modern databases have some element of 'spatial' capability.
- SQL Server
- mySQL
- Oracle
- PostGIS

Download and install: [PostgreSQL - Open Source database](https://www.postgresql.org/)
Download and install: [PostGIS - Spatial functionality for PostgreSQL](http://www.postgis.net/)

Take a database table: Libraries

| Name | Authority | Latitude | Longitude |
| --------- | ---- | -------- | --------- |
| Taunton Library | Somerset |  |  |
| Bath Central Library | Bath and North East Somerset |  |  |
| Box | Wiltshire |  |  |
| Newcastle Central Library | Newcastle |  |  |

An individual is a member of Somerset.  Find all libraries in their authority.

``` 
SELECT Name FROM Libraries  WHERE Authority = 'Somerset'
```

How about the query: Find all libraries within 5 miles of an individual?

```
SELECT Name FROM Libraries 
WHERE ST_DWithin(
    ST_SetSRID(ST_MakePoint(Longitude,Latitude), 4326)::geography, 
    ST_SetSRID(ST_MakePoint(-3.106849,51.015344), 4326)::geography
    , 8046)
```

- **ST_MakePoint** - Constructs a Point (from the latitude and longitude)
- **ST_SetSRID** - Instructs the database which spatial reference system we're using.
- **ST_DWithin** - Returns true if the two geometries are within the specified distance of one another (8046 metres - 5 miles)

## Web development mapping libraries

There are many JavaScript libraries for creating maps that allow for full integration with web development projects.

- [Leaflet](http://leafletjs.com/) - An open source option.
- [OpenLayers](http://openlayers.org/) - Another open source option.  Can be more confusing!
- [Google maps](https://developers.google.com/maps/) - Allows you to use Google's map tiles layer and other plugins.
- [Bing maps](https://www.microsoft.com/maps/choose-your-bing-maps-API.aspx) - The same but from Microsoft.

### Example: Create leaflet map
1. Go to the [Leaflet quick start guide](http://leafletjs.com/examples/quick-start/)
2. Follow instructions for creating your first map.
3. See [example here](LeafletExample.html)

## Online map tools

If you're not a web developer, but still want to create online maps that as a content editor you can embed or publish, then there are plenty of options.

Create account: [Mapbox](https://www.mapbox.com/)
Create account: [Carto](https://carto.com/)

### Example: Carto postcode data.
(Assumes having created a Carto account)
1. Login to Carto and select to import a new data file.
2. Select the file [PostalArea.zip](/data/PostalArea.zip) and allow Carto to upload it.
3. Play with the resulting data and create a map!