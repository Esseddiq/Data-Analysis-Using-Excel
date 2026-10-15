# Introduction  
This project 2 analysis focuses on data skills demand and pay analysis, using real world data set you can check the main data in this link: [Data Jobs Posting All](/Data%20Analysis%20Using%20Excel/Main%20Worked%20on%20Data/data_jobs_salary_all.xlsx).  
with the help of the power of Microsoft Excel buit in tools I've answered the main following question.  
# Questions To answer
As a Data Analyst learner and a job sekker it's logiclly to ask:
1. Do more skills get you a better pay?  
2. What are the most highly demanded skills?
3. What is the data jobs salary in other regions?
4. How much the pay for the top optimal skills?  
# Excel Skills used
To answer the above questions I used tools as:   
- Pivot Tables  
- Pivot Charts  
- Power Query  
- Powe Pivot
- DAX  
# Project Analysis
## 1️⃣Do More Skills Get  Better Pay? 
### Skills Used: Power Query(ETL), Power Pivot, Pivot Tables & Charts.
### Extract
I used Power Query to extract [Data Jobs Posting All](/Data%20Analysis%20Using%20Excel/Main%20Worked%20on%20Data/data_jobs_salary_all.xlsx) (the main data) and create two queries:
- one with the data jobs salary all informations.
- the second is a query reference of the first one with additional transformations, listing only skills with associeted job_id.
### Transform
Using Power Query to do some cleaning and transformations on both queries:  
**Salary Data jobs Query cleaning**  

![query1 cleaning steps](../Images/data%20jobs%20salary%20Applied%20steps.png)  

**Job Skills Query Cleaning**  
![job skills query img](../Images/jobs%20skills%20Applied%20steps.png)  
*Noote this second query is reference of the first quey adding the transformations steps shown above to get each distinct skill name with it's assochieted job id.*  
### Load  
After doing the transformation above here's how both queries look:  

**Salary Data jobs**  

![salary data jobs](../Images/data%20jobs%20salary%20query%20view.png)  
  
**Jobs Skills**  
  
![skills jobs image](../Images/jobs%20skills%20view%20.png)
  
Then I've load the queries above into **Power Pivot** Data moduling to establish a relationship between the tables queries using job_id column.  
  
**Data Module Diagram View**  

![diagram view](../Images/job%20skills%20and%20data%20jobs%20salary%20diagram%20view.png)  
  
Using the power of **Pivot Tables Agregations Mesures and Charts** I was able to visualise some findings.  
  
![chart](../Images/chart1.png)  
  
### Insights:
- As we  can see there is a positive corolletion between the number of skills and the job median salary.  
- For Data Engineers job roles it's highly recommanded to have more skills if you want more pay.
- For Data Science job roles they relatively demand intermediate number of skills with high pay.
- For Data Analysis job roles they demand fewer number of skills and they tend to offer relatively low pay.  

## 2️⃣What Are The Top Demanded Skills?
### Skills Used: Pivot Tables , Pivot Charts & Slicers.
- The processus of solving this question it was much simpler then question1. building on the question1 second query   
- First I loaded the second query (Job Skills) into a **Pivot table** using the **COUNT(job_skills)** Agregation function to count the skills accurance.  
- then I've sorted the results to get the **Top 10 Most Demanded Skills.** Using the **job title slicer** it helped to filter for my role.  

![project sheet image](../Images/question2%20sheet%20image.png)  
### Insights:
- **SQL And Excel** are leading the Data Analyst Role demanding skills, as they are the domaine traditionnel and old core fundemntal skills.  
- **Python And Tableau** are following they are closly equals. **Python** as a new  programming language emerging skill in the Data domaine. and **Tableau** as traditionnel Data Visualisation skill.  
- Finally comes some of the less important technical skills in the Data domaine like **Word And Powepoint**.
## 3️⃣What's The Data Jobs Salary In Other Regions?
### Skills: Pivot Tables And DAX.
Loading the jobs salary data into Power Pivot, then into Pivot Tables I've Grouped the data BY the job_title short into rows.  
Then I  created some **DAX explicit mesures** 
1. Median salary for all countries:  
```
median_salary:=MEDIAN(data_jobs_salary[salary_year_avg])
```  
2. Median salary only for Unitted State:  
```
US_median_salary=CACULATE(
            MEDIAN(data_jobs_salary[salary_year_avg]),
            data_jobs_salary[job_country]="Unite 
            States")
```  
3. Median salary for all countries excepet US:  
```
non_US_median_salary=CACULATE(
            MEDIAN(data_jobs_salary[salary_year_avg]),
            data_jobs_salary[job_country]<>"Unite 
            States")
```  
  
    
![regions median salary](../Images/regions%20median%20salary%20image.png)



