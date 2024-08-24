1.Write a query to list all electric vehicles with their VIN (1-10), Make, and Model.

```bash
SELECT  VIN, make, model
FROM electric_vehicle_population_data; 
```








2. Write a query to display all columns for electric vehicles with a Model Year of 2020 or later.
``` bash
SELECT *
FROM electric_vehicle_population_data
WHERE `model year`>=2020 ;
```



3. Write a query to list electric vehicles manufactured by Tesla.
```bash
SELECT *
FROM electric_vehicle_population_data
WHERE make="tesla" ;
```



4. Write a query to find all electric vehicles where the Model contains the word Leaf.
```bash
SELECT *
FROM electric_vehicle_population_data
WHERE Model LIKE '%Leaf%' ;
```


5. Write a query to count the total number of electric vehicles in the dataset.
```bash
SELECT COUNT(DISTINCT VIN) AS total_vehicle_count 
FROM electric_vehicle_population_data;
```




6. Write a query to find the average Electric Range of all electric vehicles.
```bash
SELECT AVG(`electric Range`)
FROM electric_vehicle_population_data;
```
7. Write a query to list the top 5 electric vehicles with the highest Base MSRP, sorted in descending order.
```bash
SELECT VIN, `model year` , make, `base MSRP`
FROM electric_vehicle_population_data
ORDER BY `base msrp` DESC LIMIT 5;
```

8. Write a query to list all pairs of electric vehicles that have the same Make and Model Year. 
 Include columns for VIN_1, VIN_2, Make, and Model Year.
```bash
SELECT e1.vin AS vin1, e2.vin AS vin2 , e1.make, e1.`model year`
FROM electric_vehicle_population_data AS e1
JOIN electric_vehicle_population_data AS e2
ON e1.make=e2.make 
   and e1.`model year`=e2.`model year`
   and e1.vin<e2.vin;
```
9. Write a query to find the total number of electric vehicles for each Make. Display Make and the count of vehicles.
```bash
SELECT make, count(*) AS vehicle_count
FROM electric_vehicle_population_data
GROUP BY make 
ORDER BY vehicle_count DESC;
```


10. Write a query using a CASE statement to categorize electric vehicles into three categories based on their Electric Range: Short Range for ranges less than 100 miles, Medium Range for ranges between 100 and 200 miles, 
and Long Range for ranges more than 200 miles.
```bash
SELECT make, `electric range`,
CASE 
    WHEN `electric range` < 100 THEN 'Short range'
    WHEN `electric range` BETWEEN 100 AND 200 THEN 'Medium range'
    ELSE 'Long range'
END AS Range_category
FROM electric_vehicle_population_data;
```

11. Write a query to add a new column Model_Length to the electric vehicles table that 
calculates the length of each Model name.
```bash
ALTER TABLE electric_vehicle_population_data ADD COLUMN `Model Length` INT;
SET SQL_SAFE_UPDATES = 0;
UPDATE electric_vehicle_population_data SET `Model length`=LENGTH(model);
SELECT model, `model length` FROM electric_vehicle_population_data;
```




12. Write a query using an advanced function to find the electric vehicle with the highest Electric Range.
```bash
WITH RankedVehicles AS (
    SELECT make, model, 
           `electric range`, 
           Row_number() OVER (ORDER BY `electric range` DESC) AS Range_rank  
    FROM electric_vehicle_population_data
)
SELECT make, model, `electric range`
FROM RankedVehicles
WHERE Range_rank = 1;
```

13. Create a view named HighEndVehicles that includes electric vehicles with a Base MSRP of $50,000 or higher.
```bash
CREATE VIEW HighEndVehicles AS 
( SELECT DISTINCT VIN, make, model, `electric vehicle type`, `Base MSRP`
FROM electric_vehicle_population_data 
WHERE `Base MSRP`> 50000);
SELECT * FROM HighEndVehicles;
```
14. Write a query using a window function to rank electric vehicles based on their Base MSRP within each Model Year.
```bash
SELECT DISTINCT VIN, make, model, `model year`, `Base MSRP`,
RANk() OVER (Partition by `model year` ORDER BY `Base MSRP` DESC) AS ranking 
FROM electric_vehicle_population_data;
```

15. Write a query to calculate the cumulative count of electric vehicles registered each year sorted by Model Year.
```bash
SELECT `Model Year`, 
       COUNT(*) AS Vehicles_Registered_That_Year, 
       SUM(COUNT(*)) OVER (ORDER BY `Model Year`) AS Cumulative_Vehicles_Registered
FROM electric_vehicle_population_data
GROUP BY `Model Year`
ORDER BY `Model Year`;
```

16. Write a stored procedure to update the Base MSRP of a vehicle given its VIN (1-10) and new Base MSRP.
```bash
DELIMITER //

CREATE PROCEDURE UpdateBaseMSRP(
    IN p_VIN VARCHAR(10),
    IN p_NewBaseMSRP DECIMAL(10, 2)
)
BEGIN
    UPDATE electric_vehicle_population_data
    SET `Base MSRP` = p_NewBaseMSRP
    WHERE `VIN (1-10)` = p_VIN;
END //

DELIMITER ;
CALL updstebaseMSRP(`WBY8P6C58K`, 5000);
SELECT vin , `base msrp` FROM electric_vehicle_population_data;
```

17. Write a query to find the county with the highest average Base MSRP for electric vehicles. 
Use subqueries and aggregate functions to achieve this.
```bash
SELECT County, AVG_MSRP
FROM (
    SELECT County, AVG(`Base MSRP`) AS AVG_MSRP
    FROM electric_vehicle_population_data
    GROUP BY County
) AS CountyAvgMSRP
ORDER BY AVG_MSRP DESC
LIMIT 1;
```
18. Write a query to find pairs of electric vehicles from the same City where one vehicle has a longer Electric Range than the other. Display columns for VIN_1, Range_1, VIN_2, and Range_2.
```bash
SELECT ev1.VIN AS VIN_1, 
ev1.`Electric Range` AS Range_1, ev2.VIN AS VIN_2, 
ev2.`Electric Range` AS Range_2
FROM electric_vehicle_population_data ev1
JOIN electric_vehicle_population_data ev2 
ON ev1.City = ev2.City 
AND ev1.`Electric Range` > ev2.`Electric Range`
AND ev1.VIN <> ev2.VIN;
```
