Spatial joins are the bread-and-butter of spatial databases. They allow you to combine information from different tables by using spatial relationships as the join key.

[ST_Contains(geometry A, geometry B)](http://postgis.net/docs/ST_Contains.html): Returns true if and only if no points of B lie in the exterior of A, and at least one point of the interior of B lies in the interior of A.

[ST_DWithin(geometry A, geometry B, radius)](http://postgis.net/docs/ST_DWithin.html): Returns true if the geometries are within the specified distance of one another.

[ST_Intersects(geometry A, geometry B)](http://postgis.net/docs/ST_Intersects.html): Returns TRUE if the Geometries/Geography “spatially intersect” - (share any portion of space) and FALSE if they don’t (they are Disjoint).

[round(v numeric, s integer)](http://www.postgresql.org/docs/current/interactive/functions-math.html): PostgreSQL math function that rounds to s decimal places

[strpos(string, substring)](http://www.postgresql.org/docs/current/static/functions-string.html): PostgreSQL string function that returns an integer location of a specified substring.

[sum(expression)](http://www.postgresql.org/docs/current/static/functions-aggregate.html#FUNCTIONS-AGGREGATE-TABLE): PostgreSQL aggregate function that returns the sum of records in a set of records.






SELECT
khdtk.pengelola,
bkph.balai,
khdtk.geom,
ST_Area(khdtk.geom)/10000
FROM khdtk
JOIN bkph
ON ST_Intersects(khdtk.geom, bkph.geom);