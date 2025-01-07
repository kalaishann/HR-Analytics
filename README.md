# HR Analytics

![Dashboard](https://github.com/user-attachments/assets/4865c754-25bc-418d-9ae3-d74669581259)

#### PROBLEM STATEMENT:
-  The company has undergone changes in its organizational structure or operations, Which have led to the removal of certain employees.Board decided that employees those service years exceed 18 will be terminated.

#### DATA TRANSFORMATION IN POWER QUERY:
#### PREPROCESSING

![PREPROCESSING](https://github.com/user-attachments/assets/a55a6572-2861-433c-b313-a23003388c98)

![Get data into power bi](https://github.com/user-attachments/assets/5d1f315a-0a20-4769-a118-f3f941396291)

- If we confused which datatype to choose always go to transform tab and select detect data type - power query automatically assign data type however i preferred to do it in manually for safer side.

- IF i don't want any of the column - i just go to VIEW tab and select GO TO COLUMN, it will list out the columns in the file so that we can simply uncheck the columns we don't need for our analysis in this way we can improve our data optimization.

  
![Go to column](https://github.com/user-attachments/assets/a532efcb-3bcd-4846-a914-300aef553a00)

- EXPLORATORY DATA ANALYSIS
- I have noticed performance rating field has 2 values 3 & 4.However i need to know what 3 & 4 means.3 is for high performance and 4 is for low performance. we want that detail also should included in our analysis so i am gonna use ADD COLUMN tab to add this field values by using CONDITIONAL COLUMN - there i could give in which column i am to refer to do this conditional & give the conditions like if the value is 3 then o/p is high performance else low performance since we have only values.

![Data exploration analysis](https://github.com/user-attachments/assets/1acb3d98-4202-478e-96c5-9ce48848f1ec)

  ![Conditional column to add new column with performane rating description](https://github.com/user-attachments/assets/bb4c97d4-9d4e-496b-b494-647a0172427c)
  
- Here i CHOOSE COLUMNS in HOMES tab to uncheck the columns since i don't want the CF_age_band as well as CF_age_attritionlabel. We could directly delete the column or using REMOVE COLUMNS in ADD COLUMN tab as well. However i prefer to go with CHOOSE COLUMNS because there i can view the list so that it's pretty easy for me to determine.
![Choose column in HOME tab to determine columns](https://github.com/user-attachments/assets/9536e73d-d85e-4b6f-aee2-64a451b73fa0)

![Assigning data type for newly added column](https://github.com/user-attachments/assets/cee8d516-3983-4c3c-863d-eec6e38d7961)

- I want to create a new AGE_BAND COLUMN from AGE COLUMN using CONDITIONAL COLUMN since i have removed the age-band from the source.
  
![Conditional column for age_band as a new column from age column](https://github.com/user-attachments/assets/12a7da41-78d1-42aa-b7b7-fbce3abc77cb)

- I want to add description for JOB SATISFACTION COLUMN using CONDITIONAL COLUMN as a new column JOB SATISFACTION CATEGORY.

  
![Job Satisfaction Category column](https://github.com/user-attachments/assets/9f7f823d-ecc6-4965-aa72-554c5bd6e585)

- In DISTANCE FROM HOME column the minimum would be 1 and the max value would be 29. we need to as a categorical column so i am going to ADD COLUMN to DESCRIBE as Distance Category.

  ![Exploratory data analysis - Distance from Home ](https://github.com/user-attachments/assets/83ae653f-f194-4426-aac8-45e89d00cdb0)
  
![Conditional Column for Distance Category](https://github.com/user-attachments/assets/bababa1b-5c1a-401c-a0cd-40732e63348a)

- IS THERE ANY RELATIONSHIP B/W ATTRITION & PROMOTION STATUS? we don't have that detail directly available in our table, However we could get that from YEAR SINCE LAST PROMOTION COLUMN.SO I AM GOING TO ADD CALCULATED COLUMN USING CONDITIONAL COLUMN.


![CALCULATED COLUMN - PROMOTION STATUS](https://github.com/user-attachments/assets/67ef819c-df22-40fd-aa96-caaca7e4a324)

- I have noticed that YEARS AT COMPANY only has numeric data but what i want is along with number years should shown.so here i go with ADD COLUMN- AS TENURE, COLUMN FROM EXAMPLE -I WOULD WRITE 6 YEARS THEN THIS WILL WORK LIKE A FLASH FILL WITH MY EXAMPLE GIVEN ON THE FIRST ROW.

  
![Conditional column for Tenure](https://github.com/user-attachments/assets/8908f2c9-ba18-42e8-aedc-9cfdc48868cd)

![CALCULATED COLUMN -TENURE COLUMN FROM WORKING AT COMPANY COLUMN](https://github.com/user-attachments/assets/71c3fbd5-dce2-482a-a9ce-8878d37ff452)

![CALCULATED COLUMN -TENURE COLUMN ](https://github.com/user-attachments/assets/7d12989f-50a9-4406-955f-7bcfcfa2649c)

- Based on YEARS AT COMPANY we going to determine LAYOFF STATUS, we would terminate Employee with more than 18 years in the org and the rest will stay.

![CALCULATED COLUMN - Layoff Status](https://github.com/user-attachments/assets/e9b2275d-c962-45c6-bc6c-16ab46031fa5)

- To avoid the BLANK value in KPI card - i have included DAX measure using...
![FIXING BLANK IN DAX](https://github.com/user-attachments/assets/6f18730c-0caf-4c40-899a-178f3e6f1d37)


####  POWER VIEW:
- MEASURES- I used to create a separate table to keep all new measures which i am going to use here for better optimization.
- we can do that by selecting ENTER DATA in POWER VIEW. Once the All measure table have been created i started creating measure like by look what are all the fields has Summation symbol we could turn that in to measures like 

for ex: 
     
     1. TOTAL EMP = COUNT(EMP ID) will return no of emp in the org.

![Measures - Total Emp](https://github.com/user-attachments/assets/aad292d3-de67-447e-813e-6a028d3301e9)

     2. MALE COUNT = CALCULATE([TOTAL EMP],HR_DATA[GENDER]="MALE")

![MEASURE FOR MALE COUNT](https://github.com/user-attachments/assets/df2f369d-3b27-4d45-9bfa-1cf94208cd60)

     3. FEMALE COUNT = CALCULATE([TOTAL EMP],HR_DATA[GENDER]="FEMALE")


![MEASURE FOR FEMALE COUNT](https://github.com/user-attachments/assets/5a893083-0495-4d68-98e7-dcd327c4de54)
     
     4. % MALE = DIVIDE([MALE],[TOTAL EMP],0)

![MEASURE - % MALE](https://github.com/user-attachments/assets/bb636734-97f9-4581-b607-40377891592b)

     5. % FEMALE = DIVIDE([FEMALE],[TOTAL EMP],0)


![MEASURE - % FEMALE](https://github.com/user-attachments/assets/74773327-02d2-4a62-ad34-7d2fb15c7bc6)
     
     
     6. % DUE FOR PROMOTION 

![MEASURE - DUE FOR PROMOTION](https://github.com/user-attachments/assets/35eb8ec1-9663-45ff-9767-9ca15bf40ca5)

![% DUE FOR PROMOTION](https://github.com/user-attachments/assets/8ad87150-0572-4af2-bb59-00f2bbf90717)


     7. % NOT DUE FOR PROMOTION

![MEASURE - NOT DUE FOR PROMOTION](https://github.com/user-attachments/assets/2d58d7e1-d738-4ecf-9e64-326a1d6fb38b)


![% NOT DUE FOR PROMOTION](https://github.com/user-attachments/assets/3a8b2405-a04d-4d89-928c-a4432d7c68af)


#### DASHBOARD PREPARATION:
1. First thing what i do is fixing the canvas sttings to HD resolution like Height:1080 Weight:1920 and in the VIEW TAB i would set VIEW PAGE as FIT TO PAGE.
![Dashboard - canvas settings for HD resolution](https://github.com/user-attachments/assets/5b38916c-507a-4cf8-ac78-11e3890e5775)

2.Determination of WIre FRAME for page layout which include what are all slicers,KPI CARDS need to show for DYNAMIC DASHBOARD.
3.EVALUTING the KPI CARD VALUES by COMPARING DAX RESULT with VISUAL LEVEL FILTER to ensure DATA ACCURACY.
![CROSS CHECKING THE VALUES](https://github.com/user-attachments/assets/731f059b-3aa2-4d47-9854-8b42cbd8ac6d)

#### POWER BI SERVICE:
- Created a workspace in power bi service as HR Analytics.

![Created a Workspace in POWER BI SERVICE](https://github.com/user-attachments/assets/632830ba-629f-4662-a051-f18934274ffd)

- Publishing on POWER BI service by selecting appropriate workspace.
- 
![Uploading PUBLISHING HR ANALYTICS REPORT IN POWER BI SERVICE.png…]()

![Published sucessfully](https://github.com/user-attachments/assets/addfb172-848d-4019-8827-ecf3b56d522f)

- Setting Email alert to get notification if the particular KPI exceed the thershold.

![Settingup alert to get notified for attrition go beyond thershold level](https://github.com/user-attachments/assets/aa5ff619-fb9a-49a9-b48b-25b1fe130260)


![Email alert setting](https://github.com/user-attachments/assets/dee786ac-f1c8-4647-b682-c76b22dca881)

- Sheduling refresh to get real time data.
![Schedule refresh for real time data](https://github.com/user-attachments/assets/7f5b8c6f-35c8-4ba8-a394-72d9ede2b243)
