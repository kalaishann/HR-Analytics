# HR Analytics


#### PROBLEM STATEMENT:
-  The company has undergone changes in its organizational structure or operations, Which have led to the removal of certain employees.Board decided that employees those service years exceed 18 will be terminated.

#### DATA TRANSFORMATION IN POWER QUERY:
- If we confused which datatype to choose always go to transform tab and select detect data type - power query automatically assign data type however i preferred to do it in manually for safer side.

- IF i don't want any of the column - i just go to VIEW tab and select GO TO COLUMN, it will list out the columns in the file so that we can simply uncheck the columns we don't need for our analysis in this way we can improve our data optimization.

- I have noticed performance rating field has 2 values 3 & 4.However i need to know what 3 & 4 means.3 is for high performance and 4 is for low performance. we want that detail also should included in our analysis so i am gonna use ADD COLUMN tab to add this field values by using CONDITIONAL COLUMN - there i could give in which column i am to refer to do this conditional & give the conditions like if the value is 3 then o/p is high performance else low performance since we have only values.

- Here i CHOOSE COLUMNS in HOMES tab to uncheck the columns since i don't want the CF_age_band as well as CF_age_attritionlabel. We could directly delete the column or using REMOVE COLUMNS in ADD COLUMN tab as well. However i prefer to go with CHOOSE COLUMNS because there i can view the list so that it's pretty easy for me to determine.

- I want to create a new AGE_BAND COLUMN from AGE COLUMN using CONDITIONAL COLUMN since i have removed the age-band from the source.

- I want to add description for JOB SATISFACTION COLUMN using CONDITIONAL COLUMN as a new column JOB SATISFACTION CATEGORY.

- In DISTANCE FROM HOME column the minimum would be 1 and the max value would be 29. we need to as a categorical column so i am going to ADD COLUMN to DESCRIBE as Distance Category.

- IS THERE ANY RELATIONSHIP B/W ATTRITION & PROMOTION STATUS? we don't have that detail directly available in our table, However we could get that from YEAR SINCE LAST PROMOTION COLUMN.SO I AM GOING TO ADD CALCULATED COLUMN USING CONDITIONAL COLUMN.

- I have noticed that YEARS AT COMPANY only has numeric data but what i want is along with number years should shown.so here i go with ADD COLUMN- AS TENURE, COLUMN FROM EXAMPLE -I WOULD WRITE 6 YEARS THEN THIS WILL WORK LIKE A FLASH FILL WITH MY EXAMPLE GIVEN ON THE FIRST ROW.

- Based on YEARS AT COMPANY we going to determine LAYOFF STATUS, we would terminate Employee with more than 18 years in the org and the rest will stay.

- To avoid the BLANK value in KPI card - i have included DAX measure using...


####  POWER VIEW:
- MEASURES- I used to create a separate table to keep all new measures which i am going to use here for better optimization.
- we can do that by selecting ENTER DATA in POWER VIEW. Once the All measure table have been created i started creating measure like by look what are all the fields has Summation symbol we could turn that in to measures like 

for ex: 
     
     1. TOTAL EMP = COUNT(EMP ID) will return no of emp in the org.

     2. MALE COUNT = CALCULATE([TOTAL EMP],HR_DATA[GENDER]="MALE")

     3. FEMALE COUNT = CALCULATE([TOTAL EMP],HR_DATA[GENDER]="FEMALE")
     
     4. % MALE = DIVIDE([MALE],[TOTAL EMP],0)

     5. % FEMALE = DIVIDE([FEMALE],[TOTAL EMP],0)
     
     6. % DUE FOR PROMOTION =CALCULATE([TOTAL EMP],)


#### DASHBOARD PREPARATION:
1. First thing what i do is fixing the canvas sttings to HD resolution like Height:1080 Weight:1920 and in the VIEW TAB i would set VIEW PAGE as FIT TO PAGE.
2.Determination of WIre FRAME for page layout which include what are all slicers,KPI CARDS need to show for DYNAMIC DASHBOARD.
3.EVALUTING the KPI CARD VALUES by COMPARING DAX RESULT with VISUAL LEVEL FILTER to ensure DATA ACCURACY.


#### POWER BI SERVICE:
Created a workspace in power bi service as HR Analytics.

