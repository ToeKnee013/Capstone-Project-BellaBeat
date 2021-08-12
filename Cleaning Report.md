# Cleaning Report
I will break down the actions I took to clean the table in steps.
## Steps
1. I selected all the columns from the table that are relevant to the trends I wish to identify. Then I make a new table
```
SELECT Id, ActivityDate, TotalDistance, VeryActiveDistance, ModeratelyActiveDistance, LightActiveDistance, SedentaryActiveDistance, Calories
FROM `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
```
2. I filtered out any rows where total distance and calories equaled to 0
```
SELECT *
FROM `bellabeat-case-study-321019.BellaBeat_Analysis.Working_Table`
WHERE Calories>0 AND TotalDistance>0
```
