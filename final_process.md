# End-to-End Geospatial Framework for Assessing Healthcare Accessibility in Karnataka

## 1. Introduction

Improving healthcare accessibility is essential for ensuring equitable access to services—especially in a diverse and rapidly growing state like Karnataka. This project develops a comprehensive geospatial framework that integrates multiple spatial analysis techniques from data collection to advanced modeling. The framework combines methods from several reference studies to evaluate accessibility across districts and guide policy interventions.

## 2. Objectives

- **Map and Digitize Healthcare Facilities:**  
  Create accurate, geo-referenced maps of primary healthcare centers, medical college hospitals, and specialized clinics.
  
- **Quantify Accessibility:**  
  Calculate provider-to-population ratios, travel times, and Access Population Coverage (APC) for different districts.
  
- **Incorporate Advanced Spatial Models:**  
  Use the 2-Step Floating Catchment Area (2SFCA) and Enhanced 2SFCA (E2SFCA) methods to account for distance decay and multi-zone accessibility.
  
- **Integrate Socio-Economic Analysis:**  
  Evaluate the relationship between accessibility, population density, urbanization, and income levels.
  
- **Develop Decision-Support Tools:**  
  Provide actionable insights for healthcare planners and policy makers to address service disparities.

## 3. Data Collection

### 3.1 Spatial Data

- **Base Maps & Administrative Boundaries:**  
  - Obtain digitized maps of Karnataka (district and taluk boundaries) from government or GIS repositories.
  
- **Healthcare Facilities Data:**  
  - Collect location data (GPS coordinates) of primary healthcare centers, medical college hospitals, and other health services.
  
- **Population Data:**  
  - Use high-resolution population estimates (e.g., WorldPop or census data) to determine the demand in each area.
  
- **Socio-Economic Data:**  
  - Integrate per capita income, urbanization, and demographic variables.

*Reference Idea:*  
The **Mysore study** (Paper 1) detailed geo-referencing and digitization of healthcare facilities using GPS and GIS software. We adopt these methods to ensure that all healthcare facility locations are accurately mapped.

### 3.2 Ancillary Data

- **Travel Friction Surfaces:**  
  - Acquire friction surface rasters (e.g., from the Malaria Atlas Project) to model travel impedance.
  
- **Road Network Data:**  
  - Gather detailed road network and transportation data to support travel time analysis (both motorized and walking).

## 4. Data Preprocessing

### 4.1 Geo-Referencing and Digitization

- **Base Map Preparation:**  
  - Import and geo-reference base maps in GIS software (ArcGIS/QGIS).
- **Digitization:**  
  - Digitize administrative boundaries and plot healthcare facility points.

### 4.2 Data Cleaning and Integration

- **Standardization:**  
  - Clean and standardize facility addresses and GPS coordinates (using APIs if needed).
- **Layer Integration:**  
  - Merge population, socio-economic, and facility data into a unified spatial database.

*Reference Idea:*  
Techniques for geo-referencing and data cleaning from the **Mysore study** (Paper 1) are used here to prepare accurate datasets.

## 5. Methodology

### 5.1 Service Area Delineation

#### 5.1.1 Euclidean Buffers
- **Objective:**  
  - Create simple, circular buffers around each healthcare facility to estimate service areas.
  
#### 5.1.2 Thiessen Polygons
- **Objective:**  
  - Generate Thiessen (Voronoi) polygons to assign unique zones of influence for each facility, thereby identifying overlapping service areas and gaps.

*Reference Idea:*  
Paper 1 used Euclidean buffers and Thiessen polygons for delineating service areas. We adapt these techniques to initially identify the catchment areas of healthcare facilities.

### 5.2 Provider-to-Population Ratios

- **Calculation:**  
  - Divide the number of healthcare providers by the total population within each administrative unit (district or taluk).
  
- **Analysis:**  
  - Compare ratios to identify underserved areas and set benchmarks for accessibility.

*Reference Idea:*  
The **Primary Care study** (Paper 2) emphasized provider-to-population ratios along with distance-based measures. We use these metrics as a straightforward comparison of service availability.

### 5.3 Travel Time Analysis

#### 5.3.1 Friction Surface & Network Analysis
- **Travel Time Calculation:**  
  - Use friction surface rasters and network analysis algorithms (such as Dijkstra’s algorithm) to compute the shortest travel times from population centroids to the nearest healthcare facility.
  
- **Modes of Transport:**  
  - Model both motorized and walking travel times to capture a range of accessibility scenarios.

#### 5.3.2 Access Population Coverage (APC)
- **Definition:**  
  - APC is the proportion of the population within predetermined travel time thresholds (e.g., within 30, 60, or 90 minutes).
  
- **Calculation:**  
  - Overlay travel time rasters with population data to determine the percentage of the population with timely access.

*Reference Idea:*  
Paper 3 introduced the use of friction surfaces and APC to assess accessibility. These methods are directly incorporated to measure how many people can access healthcare facilities within acceptable travel times.

### 5.4 Advanced Accessibility Modeling

#### 5.4.1 2-Step Floating Catchment Area (2SFCA) Method
- **Step 1:**  
  - For each healthcare facility, identify all demand locations within a defined catchment area and compute the provider-to-demand ratio.
  
- **Step 2:**  
  - For each demand location, aggregate the ratios of all facilities within its catchment area to generate an overall accessibility score.

#### 5.4.2 Enhanced 2SFCA (E2SFCA) Method
- **Distance Decay Implementation:**  
  - Divide the catchment area into multiple zones (e.g., 0–5, 5–10, 10–15 miles) and assign decay weights using a Gaussian function.
  
- **Weighted Score Calculation:**  
  - Combine the weighted ratios to obtain a refined accessibility score that better reflects gradual changes in accessibility as travel distance increases.

*Reference Idea:*  
Paper 5 details the development of a geoprocessing toolbox using 2SFCA and E2SFCA methods. These advanced methods are adopted to provide a nuanced accessibility score that considers both supply and demand while incorporating distance decay effects.

### 5.5 Socio-Economic and Urban–Rural Analysis

- **Correlation Analysis:**  
  - Evaluate the relationship between accessibility scores and socio-economic factors such as per capita income and population density using statistical methods.
  
- **Urban vs. Rural Comparison:**  
  - Compare accessibility metrics between urban and rural areas to identify disparities and potential equity issues.

*Reference Idea:*  
The **Oral Health Care study** (Paper 4) provided insights into linking spatial accessibility with socio-economic factors and urbanization. These approaches help us integrate a broader perspective on accessibility beyond mere physical distance.

## 6. Tool Development and Implementation

### 6.1 Geoprocessing Toolbox

- **Development Environment:**  
  - Develop a custom Python-based geoprocessing toolbox for ArcGIS Pro that automates data preprocessing, buffer creation, network analysis, and 2SFCA/E2SFCA calculations.
  
- **User Interface:**  
  - Ensure the toolbox is user-friendly, allowing for adaptation to different datasets and regions.

*Reference Idea:*  
The toolbox approach from Paper 5 serves as a model for building automated tools that streamline spatial accessibility analysis.

## 7. Visualization and Reporting

### 7.1 Mapping and Dashboards
- **Density and Heat Maps:**  
  - Create visualizations showing provider-to-population ratios, travel times, and accessibility scores.
  
- **Interactive Dashboards:**  
  - Develop interactive maps to enable stakeholders to explore the data dynamically.

### 7.2 Reporting
- **Documentation:**  
  - Prepare comprehensive reports detailing the methodology, analyses, and findings.
  
- **Policy Recommendations:**  
  - Highlight areas with poor accessibility and suggest strategies for resource allocation and infrastructure development.

## 8. Final Analysis and Recommendations

- **Synthesis of Findings:**  
  - Integrate results from spatial, travel time, and advanced modeling analyses to provide a multi-dimensional view of healthcare accessibility.
  
- **Actionable Insights:**  
  - Recommend interventions such as the establishment of new facilities, improvement in transportation networks, or targeted resource allocation in underserved areas.
  
- **Future Directions:**  
  - Discuss potential extensions of the project, including regular updates and integration of additional non-spatial factors (e.g., healthcare utilization data).

## 9. Conclusion

This document outlines a robust, end-to-end geospatial framework for assessing healthcare accessibility in Karnataka. By integrating methods from several reference studies—including geo-referencing, travel time analysis, and advanced accessibility modeling (2SFCA/E2SFCA)—the framework provides a comprehensive tool for identifying service gaps and guiding policy decisions. The inclusion of socio-economic analyses further ensures that the framework addresses equity and resource distribution challenges, paving the way for improved healthcare outcomes across the state.

## 10. References

1. **Accessibility Analysis of Primary Healthcare Services in Mysore District Using Geospatial Techniques**  
   *Techniques: Geo-referencing, digitization, GPS data collection, Euclidean buffers, Thiessen polygons, nearest neighbor analysis.*  
   (Reference: :contentReference[oaicite:0]{index=0})

2. **Spatial Accessibility of Primary Care: Concepts, Methods and Challenges**  
   *Techniques: Provider-to-population ratios, distance-based measures, gravity models, conceptual framework of potential vs. realized access.*  
   (Reference: :contentReference[oaicite:1]{index=1})

3. **Assessing Population-level Accessibility to Medical College Hospitals in India: A Geospatial Modeling Study**  
   *Techniques: Friction surface rasters, Dijkstra’s algorithm for travel time, and Access Population Coverage (APC).*  
   (Reference: :contentReference[oaicite:2]{index=2})

4. **Mapping Accessibility to Oral Health Care in Coastal India – A Geospatial Approach Using GIS**  
   *Techniques: Dentist-to-population ratios, GIS mapping, urban–rural comparison, and socio-economic correlation analysis.*  
   (Reference: :contentReference[oaicite:3]{index=3})

5. **Enhancing Health Care Accessibility and Equity Through a Geoprocessing Toolbox for Spatial Accessibility Analysis**  
   *Techniques: Development of a geoprocessing toolbox using Python for ArcGIS Pro, implementation of 2SFCA and E2SFCA methods with travel time catchments.*  
   (Reference: :contentReference[oaicite:4]{index=4})

---

*This document integrates key ideas from the reference papers to develop a comprehensive methodology tailored to the context of Karnataka, ensuring that both spatial and non-spatial factors are incorporated to achieve a holistic view of healthcare accessibility.*

