# Optimal Airport Hub Location – P-Median Model (Southeast U.S.)

## Overview
This project applies **operations research and optimization modeling** to determine the most efficient airport hub locations across the Southeastern United States. Using a **weighted p-median model**, we identify optimal hub locations that minimize total travel distance for populations in surrounding counties.

The analysis begins with the state of **Arkansas** as a test case, then expands to **11 states** across the Southeast to find the best sites for regional airport hubs.

---

## Objective
To determine which airports best serve as **central hubs** by minimizing the total population-weighted distance between counties and their assigned airports.

### Business Context
Establishing optimal airport hubs can:
- Improve logistics and transportation efficiency  
- Support regional air traffic planning and infrastructure development  
- Reduce travel time for surrounding populations

---

## States Included
Alabama, Arkansas, Florida, Georgia, Louisiana, Mississippi, North Carolina, Oklahoma, South Carolina, Tennessee, and Texas.

---

## Methodology

### Model Type
The project uses a **weighted p-median model**, where:  
- *i* indexes **counties**  
- *j* indexes **airports**

**Decision Variables**  
- Xᵢⱼ = 1 if county *i* is assigned to airport *j*; 0 otherwise  
- Yⱼ = 1 if airport *j* is selected as one of the *p* optimal hubs; 0 otherwise  

**Parameters**  
- dᵢⱼ – distance between county *i* and airport *j*  
- aᵢ – population of county *i*  
- p – number of airports to select  

**Objective Function**  
Minimize total weighted distance:

**Minimize:** Σᵢ Σⱼ (aᵢ × dᵢⱼ × Xᵢⱼ)

subject to:
- Each county is assigned to exactly one airport  
- Only *p* airports are selected  
- A county cannot be assigned to an unselected airport  
- Decision variables Xᵢⱼ and Yⱼ are binary (0 or 1)

---

## Implementation

### Data Sources
- **Airports:** U.S. Bureau of Transportation Statistics (bts.gov)  
- **County Data:** IPUMS NHGIS (National Historical Geographic Information System)  

### Files in Repository
- `Main_Model.ipynb` – Runs the optimization model for Arkansas  
- `Arkansas_Model.ipynb` – Core implementation of the p-median model  
- `airports.csv`, `arAirports.csv` – Airport data files  
- `counties.csv`, `arCounties.csv` – County population and location data  
- `Optimal Airport Hub Locations.docx` – Technical write-up and mathematical formulation  
- `Opti Presentation.pptx` – Presentation summarizing model results  

---

## Results

### Phase 1 – Arkansas Test
The model identified **Bill & Hillary Clinton Airport (Little Rock, AR)** as the optimal hub location within the state.

### Phase 2 – Regional Expansion
After extending the model to 11 states and setting p = 3, the optimal hub locations were:

1. **Easterwood Airport (College Station, TX)**  
2. **Anderson Regional Airport (Anderson, SC)**  
3. **Lakeland Linder International Airport (Lakeland, FL)**  

Across these states, the **average person is only 165 miles** from a designated hub.

---

## Key Takeaways
- Starting small (one-state model) helps validate the approach before scaling.  
- Adding **weights** such as population significantly changes the optimal results.  
- Constraining models (e.g., requiring inclusion of a specific hub) can simulate realistic business or policy priorities.  

---

## Citations
- *Model Reference:* IEEE Conference Publication, IEEE Xplore  
- *County Data:* IPUMS NHGIS  
- *Airport Data:* Tyler Data & Insights, Bureau of Transportation Statistics (bts.gov)
