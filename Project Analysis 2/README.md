# Introduction

This Project 2 analysis explores the demand for data skills and their relationship with pay. It uses a real-world dataset that you can access here: [All Data Job Postings](../Main%20Worked%20on%20Data/data_jobs_salary_all.xlsx).

Using Microsoft Excel's built-in tools, I investigated the following questions.

# Questions to Answer 🔎

As a data analyst learner and job seeker, it is logical to ask:

1. Do more skills lead to better pay?
2. What are the most in-demand skills?
3. How do data job salaries compare across regions?
4. What is the pay for the top skills?

# Excel Skills Used 🛠️

To answer these questions, I used the following tools:

- Pivot Tables
- Pivot Charts
- Power Query
- Power Pivot
- DAX

# Project Analysis 📊

## 1️⃣ Do More Skills Lead to Better Pay?

### 🛠️ Skills Used: Power Query (ETL), Power Pivot, Pivot Tables, and Pivot Charts

### 1. Extract

I used Power Query to extract the main dataset, [All Data Job Postings](../Main%20Worked%20on%20Data/data_jobs_salary_all.xlsx), and create two queries:

- The first contained the data from the full job-postings dataset.
- The second was a reference to the first query, with additional transformations to list each skill alongside its associated `job_id`.

### 2. Transform

I used Power Query to clean and transform both queries.

**Salary Data Query Cleaning**

![Salary data query cleaning steps](../Images/data%20jobs%20salary%20Applied%20steps.png)

**Job Skills Query Cleaning**

![Job skills query cleaning steps](../Images/jobs%20skills%20Applied%20steps.png)

*Note: The second query references the first and adds the transformation steps shown above. This produces a list of distinct skill names and their associated job IDs.*

### 3. Load

After applying the transformations, the two queries looked like this:

**Salary Data**

![Salary data jobs](../Images/data%20jobs%20salary%20query%20view.png)

**Job Skills**

![Job skills table](../Images/jobs%20skills%20view%20.png)

I then loaded both queries into the Power Pivot Data Model and created a relationship between the tables using the `job_id` column.

**Data Model Diagram View**

![Data Model diagram view](../Images/job%20skills%20and%20data%20jobs%20salary%20diagram%20view.png)

### 4. 📊 Visualize

Using Pivot Tables, aggregation measures, and charts, I was able to visualize some findings.

![More skills, more pay chart](../Images/chart1.png)

### 💡 Insights

- The chart suggests a positive correlation between the number of skills and median job salary.
- For data engineering roles, a broader skill set may be associated with higher pay.
- Data science roles appear to require an intermediate number of skills while offering relatively high pay.
- Data analyst roles appear to require fewer skills and offer comparatively lower pay in this dataset.

## 2️⃣ What Are the Most In-Demand Skills?

### 🛠️ Skills Used: Pivot Tables, Pivot Charts, and Slicers

The process for answering this question was simpler than the first one. I built on the second query created for Question 1.

1. First, I loaded the second query (`Job Skills`) into a Pivot Table and used the `COUNT` aggregation on `job_skills` to count how often each skill appeared.
2. Then, I sorted the results to identify the **10 most in-demand skills**. I also used the job title slicer to filter the results for a specific role.

![Project sheet for Question 2](../Images/question2%20sheet%20image.png)

*This worksheet screenshot shows the results of the steps described above.* 📊

### 💡 Insights

- **SQL and Excel** are among the leading skills demanded for data analyst roles. They are established, foundational skills in the field.
- **Python and Tableau** follow closely. Python is a widely used programming language, while Tableau is a popular data visualization tool.
- **Word and PowerPoint** also appear among the skills, although they are generally considered office-productivity tools rather than specialized data-analysis tools.

## 3️⃣ How Do Data Job Salaries Compare Across Regions?

### 🛠️ Skills Used: Pivot Tables and DAX

I loaded the job salary data into Power Pivot and then used Pivot Tables to group the results by `job_title_short`.

I created the following explicit DAX measures.

1. **Median salary across all countries:**

```DAX
median_salary :=
MEDIAN(data_jobs_salary[salary_year_avg])
```

2. **Median salary in the United States:**

```DAX
US_median_salary :=
CALCULATE(
    MEDIAN(data_jobs_salary[salary_year_avg]),
    data_jobs_salary[job_country] = "United States"
)
```

3. **Median salary outside the United States:**

```DAX
non_US_median_salary :=
CALCULATE(
    MEDIAN(data_jobs_salary[salary_year_avg]),
    data_jobs_salary[job_country] <> "United States"
)
```

4. I also used a country slicer to select a specific country and compare its median salary with the US median salary and the median salary for countries outside the US.

![Regional median salary worksheet](../Images/regions%20median%20salary%20image.png)

*This worksheet screenshot shows the results of the steps described above.*

### 💡 Insights

- The Pivot Table suggests that, for most data job roles in this dataset, median salaries in the United States are higher than those in many other countries.
- One possible explanation is that the United States has a large technology sector, including major technology companies. However, differences in salary can also reflect factors such as location, industry, experience, and cost of living.

## 4️⃣ What Do the Top 10 Skills Pay?

### 🛠️ Skills Used: Advanced Pivot Tables, Charts, and DAX

I used the same Data Model containing the job skills and salary tables.

1. I created a Pivot Table, placed the job skills in rows, and added a DAX measure to count each skill.
2. I used the DAX `CROSSFILTER()` function to change the filter direction between the two tables in the Data Model, allowing me to calculate the median salary associated with each skill.

```DAX
Skill Median Salary :=
CALCULATE(
    MEDIAN(data_jobs_salary[salary_year_avg]),
    CROSSFILTER(
        data_jobs_salary[job_id],
        data_jobs_skills[job_id],
        BOTH
    )
)
```

3. I selected the 10 most frequently occurring skills and then ordered them by median salary.
4. To visualize the results, I created an advanced combination Pivot Chart. The skill count is represented by a line with markers, while the median salary is represented by clustered columns. The two measures use separate axes.

![Optimal skills worksheet](../Images/optimal%20skills%20sheet%20image.png)

*This worksheet screenshot shows the results of the steps described above.* 📊

### 💡 Insights

- **Cloud skills such as AWS and Azure** appear to offer high median salaries in this analysis. These technologies are used across many areas of IT, not only data roles. Their salary and demand should be interpreted in the context of how often they appear in this dataset.
- **SQL and Python** are among the most frequently occurring skills in the dataset and also show relatively high median salaries. This supports their importance as foundational skills for data jobs.
- **Data visualization and spreadsheet skills, such as Tableau, Power BI, and Excel,** are also important. Their role as common, foundational tools does not make them less valuable.
- For people entering the data job market, a practical approach is to learn foundational skills first and then build expertise in more specialized technologies.

# Conclusion

This project began as a course-practice project. Working with real-world data on data-related job postings gave me a practical way to explore job-market demand, skills, and salaries.

Through this project, I practiced using Microsoft Excel tools such as Power Query, Power Pivot, DAX, Pivot Tables, and Pivot Charts to transform data, build a Data Model, and communicate findings through visualizations.
