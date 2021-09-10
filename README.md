# Google Data Analytics: Capstone Project
## BellaBeat
## Project Overview
I am a junior analyst working for **Bellabeat**, a high-tech manufacturer of health-focused products for women. **Urška Sršen**, cofounder and Chief Creative Officer of Bellabeat, believes that analyzing smart device fitness data could help unlock new growth opportunities for the company. I have been asked to focus on one of Bellabeat's products and analyze smart device data to gain insight into how consumers are using their smart devices. I will use the insights discovered to help guide the company's marketing strategy and make high-level recommendations.
## Ask
Sršen the co-founder and Chief Creative Officer at Bellabeat, a tech manufacturer with health-focused womens products, is asking me to analyze smart device usage in order to gain insight into how consumers use non-Bellebeat smart devices. She then wants me to select one Bellabeat product to apply insight to my final presentation.
1. What are some trends in smart device usage?
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

I will attempt to uncover some of these trends in the data provided. These trends will be listed under the ***Analyze*** heading
## Prepare
Urška Sršen encourages me to use public data on Kaggle that explores smart device users' daily habits.\
[FitBit Fitness Tracker Data](https://www.kaggle.com/arashnic/fitbit) this Kaggle data set contains personal fitness tracker from about thirty fitbit users.
#### Credibility/Source
*"These datasets were generated by respondents to a distributed survey via Amazon Mechanical Turk between 03.12.2016-05.12.2016. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. Individual reports can be parsed by export session ID (column A) or timestamp (column B). Variation between output represents use of different types of Fitbit trackers and individual tracking behaviors / preferences."*(CC0: Public Domain, dataset made available through [Mobius](https://www.kaggle.com/arashnic))
## Process
The tools used for the cleaning, analysis and sharing are BigQuery: SQL, Google Sheets and Tableau
refer to the [Detailed Cleaning Report](https://github.com/ToeKnee013/Capstone-Project-BellaBeat/blob/main/Detailed%20Cleaning%20Report.md) for more details on the cleaning.
To summarize, I made the following changes:
* no ```NULL``` values were found
* No duplicates were found in ```Id``` and ```ActivityDate```
* Formatted the table
* Made a new table named "BellaBeat_Table_Clean"
* Exported and imported the table into Google Sheets
## Analyze
Recall our objectives
1. What are some trends in smart device usage?
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

Assumptions for the analysis:
* Strictly working with this dataset [FitBit_Data.csv](https://docs.google.com/spreadsheets/d/13DV9aDM-sPMUAaUXHZQ0kvvuuSA9kTYpFmW2J4SuLqk/edit?usp=sharing) for the analysis
* "Calories" refers to calories burned
* "Distance" refers to miles

With these metrics for the analysis set, the most important variables to look at with the given data are *Distance* and *Calories*. In the end, I developed four simple charts for the analysis.

(![SUM of Distance vs  SUM of Calories](https://user-images.githubusercontent.com/88196954/132784390-b71ef437-2ba3-46b7-952b-672804bc08cd.png)

![SUM of Lightly Active Distance vs  SUM of Lightly Active Calories](https://user-images.githubusercontent.com/88196954/132784660-7c7e38ea-547b-4008-a9eb-f19714dc20e4.png)

![SUM of Moderately Active Distance vs  SUM of Moderately Active Calories](https://user-images.githubusercontent.com/88196954/132784677-730fe130-ef2f-4699-abb1-140b0314c447.png)

![SUM of Very Active Distance vs  SUM of Very Active Calories](https://user-images.githubusercontent.com/88196954/132784683-5bd09502-d80a-42e4-985e-376a1ed353d5.png)

![SUM of Distance vs  SUM of Steps](https://user-images.githubusercontent.com/88196954/132784616-a381d820-e3c5-44dd-b45d-b8d421c8a226.png)


What can we learn from these charts?
* #### Insight: There seems to be a correleation between distance traveled at a certain intensity vs calories burned at that respective intensity. We can note that the calories burned at a specfic intensity progressively increases along with the intensity of the distance traveled.
## Share
![BellaBeat FitBit Analysis](https://user-images.githubusercontent.com/88196954/130274675-346730c0-5af7-433d-8a96-a02241a4478b.png)
[Click here to view the interactive dashboard in Tableau](https://public.tableau.com/views/GoogleDataAnalyticsCapstoneProjectBellaBeat/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)

#### Insights:
* FitBit users on average, tended to progressively decrease distance and calories burned throughout the course of 2 months according to the "Calories Burned April-May" boxplot graph
  * April 2016 Boxplot:
    * Upper Whisker: 3,653
    * Upper Hinge: 2,799
    * Median: 2,221
    * Lower Hinge: 1,942
    * Lower Whisker: 1,495
  * May 2016 Boxplot:
    * Upper Whisker: 3,311
    * Upper Hinge: 2,735
    * Median: 2,135
    * Lower Hinge: 1,865
    * Lower Whisker: 1,237
* A Distinct correlation can be drawn from the Total Distance vs. Total Calories scatter plot 
  * R-Squared ≈ 0.6
  * P-value < 0.0001
## Act
Final recommendations for marketing strategy:
1. Promote an advertisement towards individuals seeking weight loss which encourages them to exercise with more intensity
2. Integrate a software mechanic that promotes burning calories which rewards the customers.  i.e. earning points for staying consistent with target calories burned a week or month which can be spent to obtain in app cosmetics/avatars/etc or reward points used to purchase groceries/gas/gift cards/etc.
