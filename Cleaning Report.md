# Cleaning Report
I will break down the actions I took to clean the table in steps.
## Steps
1.   I selected all the columns from the table that are relevant to the trends I wish to identify. Then I make a new table named "Working_Table"
```
SELECT Id,
ActivityDate,
TotalDistance,
VeryActiveDistance,
ModeratelyActiveDistance,
LightActiveDistance,
SedentaryActiveDistance,
Calories
FROM `bellabeat-case-study-321019.BellaBeat_Analysis.Daily_Activity`
```
2.   I filtered out any rows where total distance and calories equaled to 0 because if I hadn't, that would be an anomaly which could lead to less accurate findings in data trends.
```
SELECT *
FROM `bellabeat-case-study-321019.BellaBeat_Analysis.Working_Table`
WHERE Calories>0 AND TotalDistance>0
```
3.   I then downloaded and prepare to export the data into Google Sheets for the final steps of the cleaning process

[FitBit_Data.csv](https://github.com/ToeKnee013/Capstone-Project-BellaBeat/files/6978276/FitBit_Data.csv)

4.   I imported the file into Google Sheets and made a seperate copy of the original sheet so that I can refer back to it if needed. In the "Copy of FitBit Data" I then proceeded to format columns C:G to only show the numbers in the cells up to the hundredths place for a much cleaner table.
5.   Still in the "Copy of FitBit Data" sheet, I sort all the cells in the sheet by the "Id" header row A to Z and its ready for analysis! here is the final product of the cleaned table [FitBitData](https://docs.google.com/spreadsheets/d/1nrvda6w7dXlXnBXhhRo4ivpMc5a31Emi9eh5vpt0WJw/edit?usp=sharing)
6.   I updated the table by deleting the "SedentaryActiveDistance" column since the information it provdied was negligible.
