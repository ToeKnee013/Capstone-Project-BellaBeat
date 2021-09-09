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

* Let's look for the average SedentaryActiveMinutes
```
SELECT
  AVG(SedentaryActiveMinutes)
FROM
  `bellabeat-case-study-321019.BellaBeat_Analysis.BellaBeat_Table_Clean` 
```
 **AVG = 991 minutes**
 
Great! This query gives us the average rest time for all the participants.

* Now we can work with the average and find some interesting details.
```
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
**Result: 989,701**

This query gives us the ```SUM``` of calories for the participants who had less rest times in minutes fell under the average of 991 minutes. In other words.

* Let's check out the opposite.
```
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
**Result: 1172705**

Interesting! It seems like the participants who had more rest time in minutes than the average SedentaryActiveMinutes of 991 burned more calories!

**Insight: In this instance, it seemes like particpants that had overall longer rest periods ended up burning more calories in total compared to the participants that had less overall rest periods.**

* This leads us to another question, ***what other variables can cause participants to lose more calories?*** Let's explore levels of intensities.

![SUM of Distance vs  SUM of Calories](https://user-images.githubusercontent.com/88196954/132764015-c73f4091-94bd-4164-b1a7-3c167dc1d112.png)

This chart tells us that there really isn't any big correlations between distance traveled and calories burned.

![SUM of Lightly Active Distance vs  SUM of Lightly Active Calories](https://user-images.githubusercontent.com/88196954/132764156-e41a9b7a-2854-4b01-8646-b3cee593c094.png)

This chart tells us there is a weak correlation between light active distance and light active calories burned.

![SUM of Moderately Active Distance vs  SUM of Moderately Active Calories](https://user-images.githubusercontent.com/88196954/132764164-2f208bd4-28c2-4666-b2ba-9780d8be0a90.png)

This chart tells us there is a stronger correlation betweeen moderate active distance and moderate active calories burned compared to the previous one.

![SUM of Very Active Distance vs  SUM of Very Active Calories](https://user-images.githubusercontent.com/88196954/132764168-033b2744-a6d0-47fb-8f5f-12c80f6585d3.png)

This chart tells us there is a strong correlation between very active distance and very active calories burned!

![SUM of Distance vs  SUM of Steps](https://user-images.githubusercontent.com/88196954/132764177-5730be32-6668-43b3-99d3-4252bb525087.png)

So we can check the integrity of our data, this chart says there is a very strong correlation between distance and steps. Makes sense.

#### Insight: There seems to be a correleation between distance traveled at a certain intensity vs calories burned at that respective intensity. We can note that the calories burned at a specfic intensity progressively increases along with the intensity of the distance traveled.
* Light Active Trendline = 0.218
* Moderate Active Trendline = 0.692
* Very Active Trendline = 0.861

In regards to the SUM of Distance vs. SUM of Calories chart, we can infer that there is a positive trend amongst the different intensities but may be slightly skewed due to the light active chart.
