# Google Data Analytics: Capstone Project
## BellaBeat
## Project Overview
I am a junior analyst working for **Bellabeat**, a high-tech manufacturer of health-focused products for women. **Urška Sršen**, cofounder and Chief Creative Officer of Bellabeat, believes that analyzing smart device fitness data could help unlock new growth oppurtunities for the company. I have been asked to focus on one of Bellabeat's products and analyze smart device data to gain insight into how consumers are using their smart devices. I will use the insights discovered to help guide the companys marketing strategy and make high-level recommendations.
## Ask
Sršen the cofounder and Chief Creative Officer at Bellabeat, a tech manufacturer with health-focused womens products, is asking me to analze smart device usage in order to gain insight into how consumers use non-Bellebeat smart devices. She then wants me to select one Bellabeat product to apply insight to my final presentation.
1. What are some trends in smart device usage?
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

I will identify 2 key trends within the data that could answer the questions above. These trends will be listed under the ***Analyze*** heading
## Prepare
Urška Sršen encourages me to use public data on Kaggle that explores smart device users' daily habits.\
[FitBit Fitness Tracker Data](https://www.kaggle.com/arashnic/fitbit) this Kaggle data set contains personal fitness tracker from about thirty fitbit users.
#### Credibility/Source
*"These datasets were generated by respondents to a distributed survey via Amazon Mechanical Turk between 03.12.2016-05.12.2016. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. Individual reports can be parsed by export session ID (column A) or timestamp (column B). Variation between output represents use of different types of Fitbit trackers and individual tracking behaviors / preferences."*(CC0: Public Domain, dataset made available through [Mobius](https://www.kaggle.com/arashnic))
## Process
The tools used for the cleaning and analysis are BigQuery SQL and Google Sheets
Refer to the [cleaning report](https://github.com/ToeKnee013/Capstone-Project-BellaBeat/blob/main/Cleaning%20Report.md) for more details on the cleaning.
To summarize, I made the follwing changes:
* Filtered out any columns that were unrelated to the analysis
* Made a new table named "Working_Table"
* In the new table, I filtered out any rows where calories and distance equal zero ```WHERE Calories>0 AND TotalDistance>0```
* Exported and imported file into Google Sheets now named "FitBit Data"
* Made a copy of the original sheet to work on and formatted all the cells with decimal places to the nearest hundredths place
* Sorted the sheet by the "Id" header row A to Z
## Analyze
I chose to find trends that could provide insight into these following questions
1. Does total distance correlate with total calories burned?
2. Do levels of intensity affect calories burned?

Assumptions for the analysis:
* Strictly working with this dataset [FitBit_Data.csv](https://github.com/ToeKnee013/Capstone-Project-BellaBeat/files/7009212/FitBit_Data.csv) for the analysis
* Calories burned is linked to weight loss
* "Calories" in the data refers to calories burned
* "Distance" doesn't have a specified metric system in this data therefore, I will still assume that the bigger the "distance" number, the greater the general distance is covered

With these metrics for the analysis set, the most important variables to look at with the given data are *Distance* and *Calories*. In the end, I developed four simple charts for the analysis.

![Total Distance vs  Total Calories](https://user-images.githubusercontent.com/88196954/129946417-ccb9f333-d9eb-457c-93b2-0807cec587db.png)
![Total Light Active Distance vs  Total Light Active Calories](https://user-images.githubusercontent.com/88196954/129946767-2e83841b-59bc-4bb1-9601-72de51d441a6.png)
![Total Moderately Active Distance vs  Total Moderate Calories](https://user-images.githubusercontent.com/88196954/129946783-ee7a1bf5-6d64-4f59-83e1-da0b9e14b94c.png)
![Total Very Active Distance vs  Total Very Active Calories](https://user-images.githubusercontent.com/88196954/129946796-019bf6df-dd77-46e7-8154-9ba95c675446.png)

What can we learn from these charts?
* There is a positive correlation between distance and calories burned although it varies across intensities and distance traveled.
## Share
![BellaBeat FitBit Analysis](https://user-images.githubusercontent.com/88196954/130270641-46d8166a-b56c-45bf-961d-3501ee28dee5.png)
[Click here to view the interactive dashboard in Tableau](https://public.tableau.com/views/GoogleDataAnalyticsCapstoneProjectBellaBeat/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)
