# Data Jobs Market Excel Dashbroad
![GIF Dashbroad](./images%20p1/Dashboard.gif)  
# Introduction
First this Excel Dashbroad📉 project is a course practice idea provided by *Mr Luke Barousse*, I added my touch and some other changes to the course idea💡, you can access the course material via this link [Excel For Data Analysis By Luke Barousse]( https://lukeb.co/excel). 
Second this Dashboard it's designed to help Data Jobs seekers to search for thier ideal Data Job Title combined with other factors such as role median salary💰, country pay, best platforme to applay in and the job scheduel type pay.   
You can access the [project Excel workbook from here](project%201%20work%20book.xlsx)  
# Skills Used
I created the Dashbroad project by using the following Excel tools:  
1. **🧮Formulas & Fuctions:** to do some calculations using statistical functions and arrays formulas.
2. **❎Data Validation:** to list the distinct elements in the input cells.  
3. **💫Power Query:** this tool it help me clean and adjuted some columns before doing calculations.  
4. **📉Charts:** to visualize the results and calculation I did on the main data.
# Dashboard Building
## 📊Charts
### 📈Data Jobs Titles Median Salary Chart
![data roles median salary](./images%20p1/data%20roles%20ms%20chart.png)  
  
- 🛠️ Excel Features: Utilized bar chart feature (with formatted salary values) and optimized layout for clarity.
- 🎨 Design Choice: Horizontal bar chart for visual comparison of median salaries.
- 📉 Data Organization: Sorted job titles by descending salary for improved readability.
- 💡 Insights Gained: This enables quick identification of salary trends, noting that Senior roles and Engineers are higher-paying than Analyst roles.  
  
### 🌍Countries Median Salary Map
![countries map](./images%20p1/countries%20map%20chart.png)  
- 🛠️ Excel Features: Utilized Excel's map chart feature to plot median salaries globally.
- 🎨 Design Choice: Color-coded map to visually differentiate salary levels across regions.
- 📊 Data Representation: Plotted median salary for each country with available data.
- 👁️ Visual Enhancement: Improved readability and immediate understanding of geographic salary trends.
- 💡 Insights Gained: Enables quick grasp of global salary disparities and highlights high/low salary regions.

### 📊Jobs Schedule Type 
![jobs scheduele type chart](./images%20p1/scheduel%20type%20chart.png)  
## 🧮Formulas & Functions  
***NOOTE!: The tables results below of the applied formulas are source data for the charts visualization above.***
### 💰 Median Salary by Job Titles
```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,
    jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```
- 🔍 Multi-Criteria Filtering: Checks job title, country, schedule type, and excludes blank salaries.
- 📊 Array Formula: Utilizes MEDIAN() function with nested IF() statement to analyze an array.
- 🎯 Tailored Insights: Provides specific salary information for job titles, regions, and schedule types.
- 🔢 Formula Purpose: This formula populates the table below, returning the median salary based on job title, country, and scheduel type specified.  
![alt text](./images%20p1/job%20titles%20ms%20table.png)
  
### 💰 Median Salary For Countries
```
=MEDIAN(IF(
    ((jobs[job_title_short]=titlejob )*
    ( jobs[salary_year_avg]<>0)*
    (jobs[job_country]=B5)*
    (ISNUMBER(SEARCH(s_type,
    jobs[job_schedule_type])))),
    jobs[salary_year_avg]))
```
- 🔍 Multi-Criteria Filtering: Checks job title, country, schedule type, and excludes blank salaries.
- 📊 Array Formula: Utilizes MEDIAN() function with nested IF() statement to analyze an array.
- 🎯 Tailored Insights: Provides specific salary information for regions,job title and schedule types.
- 🔢 Formula Purpose: This formula populates the table below(only first ones the original table is too large), returning the median salary based on Country, job title, and scheduel type specified.  

![countries table](./images%20p1/countries%20table.png)

### 💰 Median Salary For Job scheduel Type
To do the final calculation I had to go from different steps using different tools:
#### ***Data Cleaning Power Query use*** 
**Jobs Scheduel Type Before Cleaning**  

![before](./images%20p1/main%20data%20power%20query%20view.png)

**Jobs Scheduel Type After Cleaning**  
![after](./images%20p1/scheduel%20type%20clean.png)
  
*The main propuse of this step is to distinct scheduel jobs type spereated each one into a row, so that I can get the unique values of scheduel types, then do the folowing calculations on them.*  
#### ***Calculations***
```
=MEDIAN(IF
   (((jobs[job_title_short]=titlejob )*
   (jobs[salary_year_avg]<>0)*
   (jobs[job_country]=county)*
   (ISNUMBER(SEARCH(E2,
   jobs[job_schedule_type])))),
   jobs[salary_year_avg]))
```
-🔢 Formula Purpose:This formula is doing the same job as those formulas above and it will produce the following table.  
![scduel table](./images%20p1/scheduel%20type%20table.png)  

## ❎Data Validation
### 🔍 Filtered List
- 🔒 Enhanced Data Validation: Implementing the filtered list as a data validation rule under the Job Title, Country, and job scheduel Type option in the Data tab ensures:
  - 🎯 User input is restricted to predefined, validated schedule types
  - 🚫 Incorrect or inconsistent entries are prevented
  - 👥 Overall usability of the dashboard is enhanced
######
![data validation gif](./images%20p1/job%20titles%20ms%20data%20validation.gif)

# Conclusion
I created this dashboard to showcase insights into salary trends across various data-related job titles. Utilizing data from my Excel course, this dashboard allows users to make informed decisions about their career paths. Exploring the functionalities to understand how location and job type influence salaries.




