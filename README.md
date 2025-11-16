

# 🗺️ HW3: Spatial Data Creation, Processing, and Visualization

**An end-to-end project utilizing manual data collection, PostGIS spatial analysis, and AI code generation (Dyad/Google AI Studio) to process and visualize real-world geo-coordinates.**

---

## 🧠 Project Overview

This assignment involved creating, processing, and visualizing a custom set of spatial data points using a variety of modern geospatial and AI tools. The project covers the full lifecycle of spatial data, from ground-level collection to complex database queries and final interactive visualization.

### Project Goals

* **Data Acquisition:** Manually collect and structure 13 real-world geo-coordinates.
* **Data Structuring:** Convert raw data into the **KML (Keyhole Markup Language)** format with specific hierarchical folders.
* **Spatial Analysis:** Write and execute spatial queries using a robust database (PostGIS).
* **Visualization:** Utilize specialized tools (Google Earth, ArcGIS, OpenLayers) and AI-generated map applications.

---

## 🛠 Tech Stack

| Category | Tool | Purpose |
| :--- | :--- | :--- |
| **Data Format** | **KML** (.kml / XML) | Primary data serialization format. |
| **Spatial Database** | **PostgreSQL + PostGIS** | Base relational database with the spatial data add-on for advanced queries. |
| **AI Code Gen** | **Dyad IDE + Ollama (Gemma 2.0)** | Used to prompt an LLM to generate custom map application code (HTML/JS) using the **Leaflet** library. |
| **AI Visualization** | **Google AI Studio** | Used for creating **vibe-coded apps** to display geo-coordinates and outline areas on uploaded map screenshots. |
| **Visualization/Conversion** | Google Earth, KML Viewer, ArcGIS Online, OpenLayers | Tools used to visualize KML, Shapefiles, and browser-cached data. |

---

## 🗺️ Data & Spatial Analysis

### 1. Data Collection Summary
13 spatial coordinates were manually collected using a phone application (showing longitude/latitude) and compiled into a table:
* **1 Residence Point** (home/apartment/dorm).
* **12 Campus/Local Points** categorized into four KML folders:
    * 3 Libraries
    * 3 Restaurants/Coffee Places (Eateries)
    * 3 Fountains (Waterworks)
    * 3 Department Buildings

### 2. PostGIS Spatial Queries

Two essential spatial queries were executed using Postgres/PostGIS to derive new geometric objects from the 13 collected points:

1.  **Convex Hull Computation:** Computed the smallest convex polygon enclosing all 13 points. The resulting polygon coordinates were added back into the KML file and visually verified in Google Earth.
2.  **Nearest Neighbor Search:** Computed the **four nearest neighbors** to the residence location. The results were visualized by adding four line segments (Home to Neighbor N) to the KML file.

---

## 💻 Setup & Execution (PostGIS via Docker)

The easiest method for setting up the required spatial database environment is using Docker.

### 1️⃣ Docker Setup

Assuming Docker is installed, pull and run the official PostGIS image:

```bash
docker run -d --name postgis \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=postgres \
-e POSTGRES_DB=gis_database \
-p 5432:5432 postgis/postgis:16-3.4
````

The PostGIS instance is now accessible on port `5432`.

### 2️⃣ Running Spatial Queries

Queries are written in SQL, inserted into the PostGIS database, and executed via a client tool (like DataGrip or pgAdmin) to perform the Convex Hull and Nearest Neighbor calculations.

-----

## 🎨 Visualization & AI Integration

The collected data was visualized across multiple platforms to fulfill the assignment requirements.

### OpenLayers (HTML5 Local Storage)

  * Used the **OpenLayers JavaScript API** to visualize the 13 points.
  * Data persistence was achieved by storing the coordinates in the browser's **HTML5 localStorage** and reading them back for plotting.

### Dyad + LLM Code Generation (Leaflet)

  * Utilized **Dyad IDE** and **Ollama (Gemma 2.0)** to generate the initial code for a map visualization app.
  * The generated HTML/JS code (based on the **Leaflet map library**) was then modified to accept separate Longitude and Latitude inputs via two fields and plot a marker upon clicking an 'OK' button.

### ArcGIS Online & Shapefile Conversion

  * The KML file was converted to an **ESRI Shapefile (.zip)** using an online converter.
  * The resulting Shapefile was uploaded to **ArcGIS Online** for visualization.

### Google AI Studio (Vibe-Coded Apps)

  * Created two separate prompt-based applications:
    1.  An app to display a given `[lat,long]` coordinate as a map pin on Google Maps.
    2.  An app that allows the user to upload a map screenshot and a plaintext list of coordinates, then **outlines the coordinates in yellow** on the uploaded image.

-----

## 📝 Deliverables (Screenshots)

The following screenshots were required as proof of work for the assignment:

  * Google Earth snapshot (raw data)
  * KML viewer snapshot (raw data)
  * PostGIS Convex Hull in Google Earth
  * PostGIS Nearest Neighbors in Google Earth
  * OpenLayers visualization
  * ArcGIS visualization
  * Dyad (Leaflet) app visualization
  * Google AI Studio: first app (map pin)
  * Google AI Studio: second app (outlined points)

-----

## 🧑‍💻 Author

**Rusheel Vijay Sable**

  * **Role:** Full Stack & AI Developer | Data Science Enthusiast
  * **Motto:** "Delving into spatial data analysis and visualization."

<!-- end list -->

```
```
