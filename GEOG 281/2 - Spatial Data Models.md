[TOC]



# Spatial Data Models

## Representing Reality 

- a GIS stores data in **THEMES ** or **LAYERS** of discrete information
- ie: hydrologic data is mapped on a separate overlay from soils or geology



### The Thematic Approach

- using thematic layers allows one to organize the complexity of the real world, into a simpler representation
- this helps us examine and understand natural relationships
- useful in real world:
  - tracking delivery vehicles
  - planning applications
  - modelling global atmopsheric circulation



### GIS as a Representation of Reality

1. **Selection**
   - select objects in the real world to be included in the digital model
2. **Representation in a standard way**
   - real world objects must be represented by "virtual" objects
   - **digitizing**
     - converting real world information (from remote sensing raster data) to virtual objects
     - using points, lines and polygons
3. **Quantification**
   - numeric values, data are assigned to the features of the real world included in the GIS

#### Limitations

- accuracy of representations will be limited to the technology that is used to collect the data from the real world
  - the number of places and time periods are vast, almost impossible to collect every bit of information about the real world

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\GEOG 281\screenshots\limitations.png)

#### Fields vs. Objects

**Fields**

- geographic space is seen as **continuous** phenomena
- A single value can be recorded for every point on Earth's surface

**Objects**

- geographic space is seen as **discrete** spatial entities (features)
- objects have identifiable boundaries
- represented by points, lines, areas (graphical elements)



## Data Types

Two basic types of data:

1. **SPATIAL DATA**
   - describes the absolute and relative location of geographic features
   - contains location and shape of geographic features (geometry)
   - points, lines, areas to represent real-world features
   - example: Geographic coordinates of a forest
2. **ATTRIBUTE DATA**
   - describes characteristics of spatial features
   - quantitative and/or qualitative
   - often referred to as *tabulated data*
   - example: forest crown closure, dominant species, height etc



### Characteristics That Define Objects

- **Type:** unique ID, type code, object class
- **Attributes:** qualitative/quantitative data
- **Relations:** calculable vs. attributable
- **Geometry:** point, line, area/polygon
- **Quality:** accuracy, resolution, coverage extent, representation

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\GEOG 281\screenshots\data_characteristics.png)

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\GEOG 281\screenshots\geographic_data.png)



## Basic Spatial Data Models

- models are used for the graphic representation of geographic space
- two types of GIS data models: **raster and vector**

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\GEOG 281\screenshots\raster_vector.png)



### Raster Data Model

- set of colored pixels representing chart information as a picture (on a screen)
  - simply an array of pixels arranged in rows and columns
- pixels are color coded, but do not represent features on their own
- pixels are the smallest individual unit of a raster image



#### The Process:

- divide the world into square cells (rows and columns)
- register the corners of the Earth
- Discrete objects are represented as collections of one or more cells
- represent fields by assigning attribute values to cells
- used to represent continuous fields rather than discrete objects



Raster data is ideally suited for mathematical modelling.



#### Raster Data Characteristics

- no explicit coding of geographic coordinates required
  - topology is irrelevant
- each raster cell (pixel) can contain only a single discrete value
- raster data allows for sophisticated mathematical modelling
  - handles continuous data
  - unable to handle linear data analysis



### Vector Data Model

- real world objects are represented by points, lines and polygons
- an objects representation is described by attributes and coordinates
- Spatial locations of features is explicit:
  - does not store the space between objects/features
  - more "compact" than the raster data model
- **applications:**
  - common in urban analysis and planning
  - less common in natural resource planning
- ideally suited for computer mapping and spatial database management



