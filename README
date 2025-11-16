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
