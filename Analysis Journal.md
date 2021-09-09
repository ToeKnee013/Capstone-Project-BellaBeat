# Analysis Journal
This is where I will conduct my analysis to uncover insights.

## Objective
Recall that our objectives are to...
1. Uncover trends in smart device usage
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

### Finding the Story in the Data
All data tells a story behind it, so let's try to figure out the story behind this data by uncovering some insights.

* I first used the following query to find a definitive time span of the data
```
SELECT
  DISTINCT ActivityDate
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
ORDER BY
  ActivityDate ASC
  ```
  This query resulted in 31 rows with the dates 2016-04-12 to 2016-05-12 implying that the data falls anywhere in that range.
  
  * I then wanted to find who took rest days
  ```
  SELECT
  *
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean`
WHERE
  Calories=0
  AND Distance=0 
  ```
  This query returned 4 rows with distance ```AND``` calories equating to 0.
  ![#RestDays](https://user-images.githubusercontent.com/88196954/132696785-7fe7a3af-30cd-4cbe-a1fa-1dd855cadae7.PNG)
**Insight : An interesting find is that the SedentaryActiveMinutes for each row equals to 1440 minutes.
Why is the number 1440 so important? In a given day, there are 1440 minutes. We know this because if we take 1440 (minutes in a day) and divide it by 60 (minutes in an hour), we get 24 which is how many hours there are in a day. With this information, we can gauge rest times that were taken.**

