

---

# **Electric Vehicle Population Data Analysis**

This project provides an in-depth analysis of electric vehicle data. The dataset contains various attributes of electric vehicles registered in different cities and counties. The analysis focuses on trends, insights, and vehicle characteristics such as make, model, electric range, and more.

## **Dataset Description**

The dataset contains the following columns:

### **Dataset Metadata: Electric Vehicle Population Data**

| **Column Name**                             | **Description**                                                                                                      | **Data Type**       |
|---------------------------------------------|----------------------------------------------------------------------------------------------------------------------|---------------------|
| `VIN (1-10)`                                | Vehicle Identification Number (first 10 characters) unique to each electric vehicle.                                 | String              |
| `County`                                    | Name of the county where the vehicle is registered.                                                                  | String              |
| `City`                                      | Name of the city where the vehicle is registered.                                                                    | String              |
| `State`                                     | Abbreviation of the U.S. state where the vehicle is registered (e.g., WA for Washington).                            | String              |
| `Postal Code`                               | 5-digit postal code of the vehicle's location.                                                                       | Integer             |
| `Model Year`                                | The year the vehicle model was manufactured.                                                                         | Integer             |
| `Make`                                      | Manufacturer of the electric vehicle (e.g., Tesla, BMW, Nissan).                                                     | String              |
| `Model`                                     | Model name of the electric vehicle.                                                                                  | String              |
| `Electric Vehicle Type`                     | Type of electric vehicle (e.g., Battery Electric Vehicle (BEV), Plug-in Hybrid Electric Vehicle (PHEV)).              | String              |
| `Clean Alternative Fuel Vehicle (CAFV) Eligibility` | Indicates whether the vehicle is eligible as a Clean Alternative Fuel Vehicle.                                        | String              |
| `Electric Range`                            | The maximum electric range of the vehicle in miles (zero if not researched or applicable).                            | Integer             |
| `Base MSRP`                                 | Manufacturer’s Suggested Retail Price for the base model of the vehicle.                                              | Integer             |
| `Legislative District`                      | Legislative district number corresponding to the vehicle's location.                                                  | Integer             |
| `DOL Vehicle ID`                            | Unique identifier assigned to the vehicle by the Department of Licensing.                                             | Integer             |
| `Vehicle Location`                          | Geographic coordinates (latitude, longitude) representing the vehicle's registered location.                         | String (POINT)      |
| `Electric Utility`                          | Name of the utility company providing electricity to the vehicle's registered location.                               | String              |
| `2020 Census Tract`                         | 2020 U.S. Census tract number corresponding to the vehicle's registered location.                                     | Integer             |

## **Analysis Overview**

- A series of SQL queries have been used to analyze the dataset.
- Key insights include trends in electric vehicle makes, models, ranges, and locations.
- Advanced SQL techniques like subqueries, CASE statements, window functions, and stored procedures were implemented.


---

### **Key Insights**

1. **Diverse Vehicle Manufacturers**:
   - The dataset includes vehicles from a wide range of manufacturers, with Tesla being one of the dominant brands.

2. **Increasing Adoption of Newer Models**:
   - A significant portion of electric vehicles are from model years 2020 and later, indicating an increase in the adoption of newer electric vehicle models.

3. **Electric Range Categories**:
   - Electric vehicles were categorized into three groups based on their range:
     - **Short Range**: Less than 100 miles
     - **Medium Range**: 100 to 200 miles
     - **Long Range**: More than 200 miles
   - Most vehicles fall into the **Medium** and **Long Range** categories, highlighting the advancements in battery technology.

4. **High-End Electric Vehicles**:
   - The top 5 vehicles with the highest base MSRP were identified, with a focus on premium electric vehicles costing above $50,000.

5. **Manufacturer Trends**:
   - Tesla, Nissan, and Chevrolet dominate the dataset, with Tesla leading in both quantity and vehicle range.

6. **Electric Vehicle Performance**:
   - The vehicle with the highest electric range has a range of **X** miles, showcasing the potential for long-distance electric travel.

7. **Geographic Distribution**:
   - Certain counties have a higher average MSRP, indicating that electric vehicles in these areas tend to be more expensive. The county with the highest average MSRP is **[County Name]**.

8. **Vehicle Pair Comparisons**:
   - In some cities, vehicles were found with significant differences in electric range, even among vehicles from the same manufacturer.

9. **Growth in Electric Vehicle Registration**:
   - The cumulative number of electric vehicles registered has steadily increased, with recent model years showing a sharp rise in registrations.

10. **Data Enrichment**:
    - A new metric, **Model_Length**, was added to analyze the length of vehicle model names, providing additional insights into manufacturer naming conventions.

---
