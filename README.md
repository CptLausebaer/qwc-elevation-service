# qwc-elevation-service


Elevation service
-----------------

Returns elevations.

Run as

    ELEVATION_DATASET=<path/to/dtm.tif> python elevation.py

Requires GDAL Python bindings. `python-gdal` or `python3-gdal` packages on Debian/Ubuntu (Note: virtualenv creation requires --system-site-packages option).

API:
* Runs by default on `http://localhost:5002`
* `GET: /getelevation?pos=<pos>&crs=<crs>`
  - *pos*: the query position, as `x,y`
  - *crs*: the crs of the query position
  - *output*: a json document with the elevation in meters: `{elevation: h}`
* `POST: /getheightprofile`
  - *payload*: a json document as follows:

        {
            coordinates: [[x1,y1],[x2,y2],...],
            distances: [<dist_p1_p2>, <dist_p2_p3>, ...],
            projection: <EPSG:XXXX, projection of coordinates>,
            samples: <number of height samples to return>
        }

  - *output*: a json document with heights in meters: `{elevations: [h1, h2, ...]}`