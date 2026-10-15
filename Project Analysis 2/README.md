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
To answer this question I've followed some steps and used some tools: 
**SKILL: Power Query(ETL)**
### Extract
I used Power Query to extract [Data Jobs Posting All](/Data%20Analysis%20Using%20Excel/Main%20Worked%20on%20Data/data_jobs_salary_all.xlsx) (the main data) and create two queries:
- one with the data jobs salary all informations.
- the second is a query reference of the first one with additional transformations, listing only skills with associeted job_id.
### Transform
Using Power Query to do some cleaning and transformations on both queries:  
**Salary Data jobs Query cleaning**  

![query1 cleaning steps](./Data%20Analysis%20Using%20Excel/Images/data%20jobs%20salary%20Applied%20steps.png)  

**Job Skills Query Cleaning**  
![job skills query img](/Data%20Analysis%20Using%20Excel/Images/jobs%20skills%20Applied%20steps.png)  
*Noote this second query is reference of the first quey adding the transformations steps shown above to get each distinct skill name with it's assochieted job id.*  
### Load  
After doing the transformation above here's how both queries look:  

**Salary Data jobs**  

![salary data jobs](/Data%20Analysis%20Using%20Excel/Images/data%20jobs%20salary%20query%20view.png)  
  
**Jobs Skills**  
  
![skills jobs image](/Data%20Analysis%20Using%20Excel/Images/jobs%20skills%20view%20.png)
  
Then I've load the queries above into **Power Pivot** Data moduling to establish a relationship between the tables queries using job_id column.  
  
**Data Module Diagram View**  

![diagram view](/Data%20Analysis%20Using%20Excel/Images/job%20skills%20and%20data%20jobs%20salary%20diagram%20view.png)  
  
Using the power of **Pivot Tables Agregations Mesures and Charts** I was able to visualise some findings.  
  
![chart](/Data%20Analysis%20Using%20Excel/Images/chart1.png)  
  
### Insights:
- As we  can see there is a positive corolletion between the number of skills and the job median salary.  
- For Data Engineers job roles it's highly recommanded to have more skills if you want more pay.
- For Data Science job roles they relatively demand intermediate number of skills with high pay.
- For Data Analysis job roles they demand fewer number of skills and they tend to offer relatively low pay.  

## 2️⃣What Are The Top Demanded Skills?
- The processus of solving this question it was much simpler then question1. building on the question1 second query   
- First I loaded the second query (Job Skills) into a **Pivot table** using the **COUNT(job_skills)** Agregation function to count the skills accurance.  
- then I've sorted the results to get the **Top 10 Most Demanded Skills.** Using the *job title slicer* it helped to filter for my role.  

![project sheet image](/Data%20Analysis%20Using%20Excel/Images/question2%20sheet%20image.png)


