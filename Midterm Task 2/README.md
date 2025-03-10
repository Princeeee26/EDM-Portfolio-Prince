# Midterm Lab Task 2 - Data Cleaning and Preparation using Power Query
- This portfolio shows how to use Power Query to prepare and clean data. The dataset has many connected tables, and cleaning methods are used to make the data more consistent and high quality before analysis.

## Step 1: Download and Load Data
- Download the dataset (Uncleaned_DS_jobs.csv)  
- Open Excel  
- Go to Data → New Query → Open File → Text/CSV
- Click Load and then Edit using Power Query Editor
### Duplicate Raw Data
- Right-click the dataset in the Queries pane  
- Select Duplicate
### Clean Salary Data
- Select the Salary Estimate column  
- Go to Transform Menu → Extract → Text Before Delimiter  
- Type "(" and click OK  
- Create two new columns: Min Salary and Max Salary  
   - Select Salary Estimate column → Add Column Menu → Column from Examples → From Selections  
   - Type the first min salary value and press Enter (all rows will auto-fill)  
   - Rename the column to "Min Sal"  
   - Repeat the process for Max Salary

## Step 2: Add Role Type Column
- Go to Add Column Menu → Custom Column  
- Rename the column to "Role Type"  
- Use this logic:  
   - If Job Title contains "Data Scientist" → Assign "Data Scientist"  
   - If Job Title contains "Data Analyst" → Assign "Data Analyst"  
   - If Job Title contains "Data Engineer" → Assign "Data Engineer"  
   - If Job Title contains "Machine Learning" → Assign "Machine Learning Engineer"  
   - Otherwise, assign "Other"  
- Change the column type to Text  

## Step 3: Split Location Column
- Select the Location column
-  Add a Custom Column with corrections:  
   - If Location = "New Jersey" → Assign ", NJ"  
   - If Location = "Remote" or "United States" → Assign ", Other"  
   - If Location = "Texas" → Assign ", TX"  
   - If Location = "California" → Assign ", CA"  
- Click OK, then select the new column  
- Go to Transform → Split Column → By Delimiter (comma ",")  
- Click OK  
- Rename the second split column to "State Abbreviations"  
- Check and replace incorrect values (e.g., "Anne Rundell" → "MA")  

## Step 4: Split Size Column
- Create two new columns: MinCompanySize and MaxCompanySize  
- Use the same method as Salary Estimate to split values
### Handle Negative Values
- Filter out -1s from the Competitors column  
- Filter out 0s from the Revenues column  
- Remove -1s from the Industry column
### Clean Company Names
- Remove any extra characters or ratings after company names
### Copy Cleaning Steps as Proof 
- Go to Home Menu → Click Advanced Editor  
- Copy and save the code in your portfolio

## Step 5: Reshape and Group Data
### Group by Role Type
- Duplicate the raw data → Rename it as "Sal By Role Type dup"
- Select only Role Type, Min Salary, and Max Salary columns  
- Change Min and Max Salary type to currency  
- Multiply values by 1000 (Numbers Column → Standard → Multiply → Type 1000)  
- Group rows by Role Type and get the average for Min and Max Salary

### Group by Company Size  
- Create a reference of raw data → Rename it as "Sal By Role Size ref"
- Select only Size, Min Salary, and Max Salary columns  
- Change Min and Max Salary type to currency  
- Multiply values by 1000  
- Group rows by Size and get the average for Min and Max Salary  


## Step 6: Merge State Mapping
- Click Unclean DS Jobs  
- Right-click in the Queries pane → New Query → Open Workbook State Mapping  
- Select the columns and click OK  
- Select Uncleaned DS Jobs query  
- Choose the State Abbreviation column in both queries  
- Click Merge → Click OK  
- Rename the merged column as "State Full Name"  
- Remove nulls and blanks  

## Step 7: Group by State
- Create a reference of raw data → Rename it as "Sal By State ref"  
- Select only State Full Name, Min Salary, and Max Salary columns  
- Change Min and Max Salary type to currency  
- Multiply values by 1000  
- Group rows by State Full Name and get the average for Min and Max Salary

## Step 8: View Query Dependencies  
- Go to View Menu → Click Dependencies  
- Check if all queries are correctly linked 

## Here's the screenshot of my output before I started data cleaning
![screenshot](/Midterm%20Task%202/Images/Before.PNG)

## Here's the Data Cleaning Activities
![screenshot](/Midterm%20Task%202/Images/Data%20Cleaning%20Activities.PNG)

## Here's the screenshot of my output after I started data cleaning

![screenshot](/Midterm%20Task%202/Images/Uncleaned_DS_jobs.png)

![screenshot](/Midterm%20Task%202/Images/Sal_by_role_type_dup.png)

![screenshot](/Midterm%20Task%202/Images/Sal_by_size_ref.png)

![screenshot](/Midterm%20Task%202/Images/Sal_by_size_role_type_dup.png)

![screenshot](/Midterm%20Task%202/Images/Sal_by_state_ref.png)

![screenshot](/Midterm%20Task%202/Images/states.png)

## Here's the screenshot of the Query Dependencies
![screenshot](/Midterm%20Task%202/Images/Query%20Dependencies.png)


