Spatial databases are powerful because they not only store geometry, they also have the ability to compare _relationships between geometries_.

[ST_Contains(geometry A, geometry B)](http://postgis.net/docs/ST_Contains.html): Returns true if and only if no points of B lie in the exterior of A, and at least one point of the interior of B lies in the interior of A.

[ST_Crosses(geometry A, geometry B)](http://postgis.net/docs/ST_Crosses.html): Returns TRUE if the supplied geometries have some, but not all, interior points in common.

[ST_Disjoint(geometry A , geometry B)](http://postgis.net/docs/ST_Disjoint.html): Returns TRUE if the Geometries do not “spatially intersect” - if they do not share any space together.

[ST_Distance(geometry A, geometry B)](http://postgis.net/docs/ST_Distance.html): Returns the 2-dimensional cartesian minimum distance (based on spatial ref) between two geometries in projected units.

[ST_DWithin(geometry A, geometry B, radius)](http://postgis.net/docs/ST_DWithin.html): Returns true if the geometries are within the specified distance (radius) of one another.

[ST_Equals(geometry A, geometry B)](http://postgis.net/docs/ST_Equals.html): Returns true if the given geometries represent the same geometry. Directionality is ignored.

[ST_Intersects(geometry A, geometry B)](http://postgis.net/docs/ST_Intersects.html): Returns TRUE if the Geometries/Geography “spatially intersect” - (share any portion of space) and FALSE if they don’t (they are Disjoint).

[ST_Overlaps(geometry A, geometry B)](http://postgis.net/docs/ST_Overlaps.html): Returns TRUE if the Geometries share space, are of the same dimension, but are not completely contained by each other.

[ST_Touches(geometry A, geometry B)](http://postgis.net/docs/ST_Touches.html): Returns TRUE if the geometries have at least one point in common, but their interiors do not intersect.

[ST_Within(geometry A , geometry B)](http://postgis.net/docs/ST_Within.html): Returns true if the geometry A is completely inside geometry B