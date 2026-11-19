# Spatial Databases - PostgreSQL & PostGIS

SQL solutions to the **Spatial Databases** course (*Bazy Danych Przestrzennych*). The course goes from relational database design in PostgreSQL to spatial analysis in PostGIS on real HERE map data of Karlsruhe, and ends with an Azure IoT exercise.


## Tech stack
PostgreSQL · PostGIS · SQL · GitHub Actions (automatic submission on push to `main`) · Azure IoT

## Contents

### `01_setup` - relational database & SQL queries
- Database `firma` with schema `ksiegowosc` (accounting): employees, hours worked, salaries, bonuses, payroll. Primary and foreign keys, `COMMENT ON` documentation.
- 16 queries (`zad5a`-`zad5p`): multi-table `JOIN`s, `LEFT JOIN` with `COALESCE`, `GROUP BY` / `HAVING`, aggregates (`SUM`, `AVG`, `MIN`, `MAX`, `COUNT DISTINCT`), overtime calculation with `GREATEST`, pattern matching (`LIKE` / `ILIKE`), sorting, and a `DELETE` with a subquery.

### `02_IntroToPostGIS` - introduction to PostGIS
- `CREATE EXTENSION postgis`; tables of buildings (polygons), roads (lines) and points of interest (points) built from EWKT.
- Spatial measures and operations: `ST_Length`, `ST_Area`, `ST_Perimeter`, `ST_Distance`, `ST_Buffer`, `ST_Difference`, `ST_SymDifference`, `ST_Centroid`.

### `03_Geometry_and_HEREdata` - geometry types & real map data
**Part 1 - geometry types:** curved geometries (`CIRCULARSTRING`, `ST_CurveToLine`), polygons with holes, 3D multipoints, geometry collections; `ST_ShortestLine`, `ST_MakePolygon`, `ST_Collect`, `ST_HasArc`.

**Part 2 - HERE data (Karlsruhe, 2018 vs 2019):**
- detecting buildings that were built or renovated between 2018 and 2019,
- counting new POIs within 500 m of those buildings, by category (`ST_DWithin`, CTEs),
- reprojecting streets and points to DHDN / Berlin Cassini (EPSG:3068) with `ST_Transform`,
- finding intersections within 200 m of a line built from input points,
- counting sporting goods stores within 300 m of parks,
- finding railway and watercourse crossings (bridges) with `ST_Intersection` and saving them to a new table.

### `04_azure_iot` - Azure IoT
- `pred.json`: a time series of GPS positions (timestamp, lat/lon) used in the Azure IoT exercise.


