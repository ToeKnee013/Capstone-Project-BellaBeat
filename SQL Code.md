# Data Cleaning

```
  #Searching for NULL values
SELECT
  *
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
WHERE
  Id IS NULL
  OR ActivityDate IS NULL
  OR TotalSteps IS NULL
  OR TrackerDistance IS NULL
  OR LoggedActivitiesDistance IS NULL
  OR VeryActiveDistance IS NULL
  OR ModeratelyActiveDistance IS NULL
  OR LightActiveDistance IS NULL
  OR SedentaryActiveDistance IS NULL
  OR VeryActiveMinutes IS NULL
  OR FairlyActiveMinutes IS NULL
  OR LightlyActiveMinutes IS NULL
  OR SedentaryMinutes IS NULL
  OR Calories IS NULL
```
```
  # Checking for duplicates
SELECT
  Id,
  ActivityDate,
  COUNT(*)
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
GROUP BY
  Id,
  ActivityDate
HAVING
  COUNT(*) > 1 
```
```
  #Converting decimals to integers
SELECT
  CAST(TotalDistance AS INT64) AS TotalDistance2,
  + CAST(VeryActiveDistance AS INT64) AS VeryActiveDistance2,
  + CAST(ModeratelyActiveDistance AS INT64) AS ModeratelyActiveDistance,
  + CAST(LightActiveDistance AS INT64) AS ModeratelyActiveDistance,
  + CAST(LightActiveDistance AS INT64) AS LightActiveDistance,
  + CAST(SedentaryActiveDistance AS INT64) AS SedentaryActiveDistance
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity` 
  ```
  ```
  # Creating a new table analysis
SELECT
  Id,
  ActivityDate,
  TotalSteps,
  CAST(TotalDistance AS INT64) AS Distance,
  + CAST(VeryActiveDistance AS INT64) AS VeryActiveDistance,
  + CAST(ModeratelyActiveDistance AS INT64) AS ModeratelyActiveDistance,
  + CAST(LightActiveDistance AS INT64) AS LightlyActiveDistance,
  + CAST(SedentaryActiveDistance AS INT64) AS SedentaryActiveDistance,
  VeryActiveMinutes,
  FairlyActiveMinutes AS ModeratelyActiveMinutes,
  LightlyActiveMinutes,
  SedentaryMinutes AS SedentaryActiveMinutes,
  Calories
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
  
```
# Data Analysis

```
  # Range of activity dates
SELECT
  DISTINCT ActivityDate
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
ORDER BY
  ActivityDate ASC 
```
```
  # Finding who took rest days
SELECT
  *
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
WHERE
  Calories=0
  AND Distance=0 
  ```
  ```
    # Average SedentaryActiveMinutes
SELECT
  AVG(SedentaryActiveMinutes)
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
```
```
  # Total Calories of participants where they got a lower than AVG SedentaryActiveMinutes
SELECT
  SUM (Calories) AS TotalCalories,
FROM (
  SELECT
    *
  FROM
    `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
  WHERE
    SedentaryActiveMinutes < 991)
ORDER BY
  TotalCalories
```
```
  # Total Calories of participants where they got a higher than AVG SedentaryActiveMinutes
SELECT
  SUM (Calories) AS TotalCalories,
FROM (
  SELECT
    *
  FROM
    `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
  WHERE
    SedentaryActiveMinutes > 991)
ORDER BY
  TotalCalories
```

