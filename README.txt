HW3 – Spatial Data Collection, Processing & Visualization

Author: Rusheel Vijay Sable
Course: Database Systems
Date: 11-15-2025

📌 Overview

This assignment walks through the end-to-end workflow of creating, analyzing, and visualizing custom spatial data. I manually collected real-world GPS coordinates, structured them into a KML file, visualized them in multiple platforms, generated spatial queries via PostGIS, and built browser-based and LLM-generated mapping applications.

This README documents:
✔ What I did
✔ The tools I used
✔ Screenshots included
✔ All files included in the .zip

Everything required in the HW spec is completed.

0. 📍 Data Collection

I manually collected 18 GPS coordinates:

Home Location

1 point — my home address (collected using real GPS on my phone)

USC Campus Locations (17 points total)

Separated into 4 categories:

Libraries	
Restaurants / Coffee Shops	
Waterworks	
Department Buildings	

✔ I took a selfie at each location (all selfies included in the ZIP).
✔ All coordinates were recorded manually from phone GPS — no Google Maps clicking.

1. 🗂 KML File Creation

I created a fully structured KML file containing:

<Folder> tags for the 4 categories

All 13 points as <Placemark> entries

Coordinates in proper order: longitude, latitude

Convex hull polygon from PostGIS

4 nearest-neighbor line segments from home point

File included:
✔ Rusheel_USC_Map.kml

2. 🌍 Google Earth Visualization

Loaded the full KML file into Google Earth (web/desktop).

Verified:
✔ All 13 points show correctly
✔ Folders expand/collapse
✔ Hull polygon outlines correctly
✔ Nearest-neighbor lines display cleanly

Included screenshot:
✔ Google_Earth.png

3. 🔎 KML Viewer Validation

Uploaded the KML to:
http://kmlviewer.nsspot.net/

Verified all:
✔ Placemark names
✔ Hull polygon
✔ Linestrings

Screenshot:
✔ KML_Viewer.png

4. 🛢 PostGIS Spatial Queries

I used PostgreSQL + PostGIS to run all spatial computations.

4.1 Convex Hull

Steps completed:

Inserted all 13 points into a PostGIS table

Ran:

SELECT ST_AsText(ST_ConvexHull(ST_Collect(geom))) FROM locations;


Converted returned polygon WKT into a KML <Polygon>

Added this polygon into my master KML

Loaded into Google Earth to confirm shape

Screenshot included:
✔ Convex_Hull_GE.png

4.2 Nearest Neighbors (k = 4)

Found the 4 closest USC points to my home location:

SELECT name, ST_Distance(home.geom, l.geom) AS dist
FROM locations l
ORDER BY home.geom <-> l.geom
LIMIT 4;


Created 4 <LineString> elements:

Home → Neighbor 1

Home → Neighbor 2

Home → Neighbor 3

Home → Neighbor 4

Added to KML and validated in Google Earth.

Screenshot included:
✔ Nearest_Neighbors_GE.png

5. 🗺 OpenLayers Web Map

I built a browser-based map using OpenLayers.

Completed tasks:
✔ Stored all 13 coordinates in localStorage
✔ Read them using JavaScript
✔ Added markers for every point
✔ Customized marker view + zoom
✔ Verified all points appear correctly

Files included:
✔ OL.html

Screenshot:
✔ OpenLayers.png

6. 🧭 ArcGIS Visualization

Used MyGeodata Cloud to convert my KML into a shapefile.
Uploaded shapefile into ArcGIS Online using “Add Layer From File”.

Verified:
✔ All points display
✔ Symbolization works
✔ Attribute table contains names
✔ Convex hull polygon renders

Screenshot:
✔ ArcGIS.png

7. 🤖 Dyad + Gemma (LLM-Generated Map App)

Using Dyad + Gemma 2B via Ollama, I generated a mapping web app.

Modified the returned code to match HW requirements:

✔ Added two input fields — latitude + longitude
✔ Added an OK button
✔ When pressed → map centers + updates marker
✔ Tested all 12 USC points individually

Screenshot included:
✔ Dyad_Map_Application.png

8. 🤖 Google AI Studio – Application 1

Prompted an LLM in Google AI Studio to build:

A simple interactive map

Accepting a (latitude, longitude)

Placing a marker at that input location

Using Google Maps API

Screenshot included:
✔ GoogleAI_App1.png

9. 🤖 Google AI Studio – Application 2

Created a second LLM app:

✔ Uploaded the USC map screenshot
✔ Provided the plaintext list of my 12 coordinates
✔ LLM highlighted all 12 points with yellow markers/outlines

Screenshot:
✔ GoogleAI_App2.png

📁 Files Included in the ZIP

Everything below is inside the uploaded ZIP:

KML & Data

Rusheel_USC_Map.kml

points.csv (if generated)

Screenshots

Google_Earth.png

KML_Viewer.png

Convex_Hull_GE.png

Nearest_Neighbors_GE.png

OpenLayers.png

ArcGIS.png

Dyad_Map_Application.png

GoogleAI_App1.png

GoogleAI_App2.png

Code

OL.html

Images

selfie_home.jpg

selfie_library_1.jpg

selfie_restaurant_2.jpg

… (all 18 selfies)

Documentation

README.md (this file)

📌 Summary

This assignment covered:

Real-world geospatial data collection

KML file creation & editing

Google Earth + KML viewer visualization

PostGIS spatial analytics

Convex hull generation

Nearest neighbor queries

Browser mapping via OpenLayers

ArcGIS shapefile visualization

LLM-generated mapping applications via Dyad & Google AI Studio

All tasks have been completed fully, with clean output, working code, and screenshots.