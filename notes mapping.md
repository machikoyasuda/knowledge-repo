---
## QGIS analysis

- Vector: Count Analysis
- Number of points within each neighborhood. 
- Click I for identification layers
- JOIN ATTRIBUTES BY LOCATION: - Take attributes of first located feature
 
* JENKS BREAKS

Merge geocoded dots with neighborhood -- and join them, so you get that in the DBF.

Import it into Excel by saving as CSV.

---

## Microsoft Excel: Pivot Table 

Name of each neighborhood in a column

AND

Scores, summed
Names, count of

---

SPATIAL JOIN of CSV & NEIGHBORHOODS

Create a new field in Field Calculator

Style: graduated colors

---

There is a better way!

## POSTGRES.

Store all your GIS files in a database - it's not much different from a spreadsheet.

createdb -T template_postgis -U postgres ona

shp2pgsql (GDAL or OGR)

shp2gpsql -s 4326 (name of shp file) | psql -d (name of db)

shp2pgsql -s 4326 geocoded_inspections.shp | psql 

* SRID lookup key http://spatialreference.org/ref/epsg/4326/

## POSTGIS.

ST_Contains - does the first geometry contain something in the second?

SELECT * FROM geocoded_inspections WHERE ST_Contains((SELECT  the_geom FROM l WHERE name='Echo Park'), geocoded_inspections.the_geom)

http://postgis.refractions.net/documentation/manual-1.4/ST_Contains.html

Inner query + Contains

## Connect QGIS to PostGIS layer.

To view your data. 

QGIS > Add DB > Connect to localhost

-- 

Field calculator
update existing field
per_capital
decimal

PNTCNT / population

---

OUTLINE:

I. What is geo data?
    Lat / Lon
    Polygons
    Projections
    Formats
        CSV
        SHP
        GeoJSON
        WKT/WKB

II. Let's get some data
    - But is it geo data?
    - Geocode it
    - See what you've done in QGIS
    - OK, let's make a simple leaflet map with this.
        - hmmm...that's unsatisyfing.

III. Let's analyze some data
    - How can we analyse the data?
        - Points are hard to make a pattern of. Can we organize the data around something?
    - Neighborhood shapes.
    - Simple QGIS point count.
        - Let's display it on a leaflet map.
    - Can we get more advanced?
        - Merge shape name to point file
        - export to excel
        - pivot table
        - re-import to qgis.
        - export shape
    - Well that's annoying...

IV. Let's pull out the big guns.
    - Say hello to PostGIS.

    createdb -T template_postgis -U postgres ona
    shp2pgsql -s 4326 data/la-county-neighborhoods-v6.shp | psql -U postgres -d ona
    check it:
        psql -U postgres -d ona
        \dt

    shp2pgsql -s 4326 data/geocoded_inspections.shp | psql -U postgres -d ona

    Now we can query by the columns in the tables, just like any old SQL table!

    SELECT COUNT(*) FROM geocoded_inspections WHERE Score < 90;
    SELECT COUNT(*) FROM geocoded_inspections WHERE Score::int < 90;

    OK, so?

    Well, we can query by spatial attributtes too! Let's check out what one of our rows looks like:

    SELECT * FROM "la-county-neighborhoods-v6" WHERE name = 'Downtown';

    See all that hex code? that's the shape in WKB. We can use that for queries. For example, I want all of the 
    points that cross through Echo Park, where I live.

    SELECT * FROM geocoded_inspections WHERE ST_Contains((SELECT the_geom FROM "la-county-neighborhoods-v6" WHERE Name = 'Echo Park'), geocoded_inspections.the_geom);

    Interesting.

    ALTER TABLE "la-county-neighborhoods-v6" ADD COLUMN count float;
    ALTER TABLE "la-county-neighborhoods-v6" ADD COLUMN sum float;
    ALTER TABLE "la-county-neighborhoods-v6" ADD COLUMN avg float;

    UPDATE "la-county-neighborhoods-v6" SET count=(SELECT COUNT(*) FROM geocoded_inspections WHERE ST_Contains("la-county-neighborhoods-v6".the_geom, geocoded_inspections.the_geom));
    UPDATE "la-county-neighborhoods-v6" SET sum=(SELECT SUM(Score::int) FROM geocoded_inspections WHERE ST_Contains("la-county-neighborhoods-v6".the_geom, geocoded_inspections.the_geom));
    UPDATE "la-county-neighborhoods-v6" SET avg=sum/count;


    - now let's open it up in QGIS. Yeah, we can do that like a shapefile!
    - OK, now let's save it as a geojson file and load it into leaflet.

    - Maybe you don't have neighborhoods. That's OK -- let's use census tracts!

    - Tilemill.

Download and save as PNG, PDF, SVG

MBTiles -> Upload to MapBox account, publish map --> Upload it via Leaflet. 


