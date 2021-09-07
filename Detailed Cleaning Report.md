# Cleaning Report
I will break down the actions I took to clean the table in steps.
## Steps
### 1. NULL VALUES
First I check for any ```NULL``` values in the "Daily_Activity" table because it contains all the columns from the dataset merged into one.
```
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
There were 0 ```NULL``` values, it appears the dataset is already relatively clean.

### 2. DUPLICATES
Next up, lets check for any duplicate values. Intuitively, I compared the following two queries.
```
SELECT
  *
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity` 
```
```
SELECT
  *
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity` 
```
Both the tables that were returned gave me 940 rows, so I imagined there were no duplicates. To Double check, I found some resources online and produced this code.
```
USING
  COUNT
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
This code returned no values at all using the ```COUNT(*) > 1``` condition. This means there are no duplicates in the table because not a single value was returned that contained a higher ```COUNT``` than 1.

### 3. FORMATTING
Following up, lets convert those messy decimal values into whole numbers using ```CAST``` and ```INT64```.
```
SELECT
  CAST(TotalDistance AS INT64) AS TotalDistance,
  + CAST(VeryActiveDistance AS INT64) AS VeryActiveDistance,
  + CAST(ModeratelyActiveDistance AS INT64) AS ModeratelyActiveDistance,
  + CAST(LightActiveDistance AS INT64) AS LightActiveDistance,
  + CAST(SedentaryActiveDistance AS INT64) AS SedentaryActiveDistance
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
```
Note that from here on out we will be working with aproximate whole numbers.

### 4. CREATING A NEW TABLE
Finally I prepare a new table to be used for analysis using the following query.
```
SELECT
  Id,
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

4.   I then downloaded and prepare to export the data into Google Sheets for the final steps of the cleaning process

[FitBit_Data.csv](https://github.com/ToeKnee013/Capstone-Project-BellaBeat/files/6978276/FitBit_Data.csv)

4.   I imported the file into Google Sheets and made a seperate copy of the original sheet so that I can refer back to it if needed. In the "Copy of FitBit Data" I then proceeded to format columns C:G to only show the numbers in the cells up to the hundredths place for a much cleaner table.
5.   Still in the "Copy of FitBit Data" sheet, I sort all the cells in the sheet by the "Id" header row A to Z and its ready for analysis! here is the final product of the cleaned table [FitBitData](https://docs.google.com/spreadsheets/d/1nrvda6w7dXlXnBXhhRo4ivpMc5a31Emi9eh5vpt0WJw/edit?usp=sharing)
6.   I updated the table in the "Copy of FitBit Data" sheet by deleting the "SedentaryActiveDistance" column since the information it provided was negligible.
