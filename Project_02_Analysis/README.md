# Excel Data Analytics — Project 2: Job Market Analysis

## Introduction

As someone actively exploring the data science job market, I wanted to understand what skills employers actually look for and how they affect salary. This project helped me dig into real job posting data and find answers through Excel.

## Questions I Explored

1. Do more skills get you better pay?
2. What's the salary for data jobs across different regions?
3. What are the top skills of data professionals?
4. What's the pay associated with the top 10 skills?

## Excel Skills Used

- 📊 **Pivot Tables**
- 📈 **Pivot Charts**
- 🧮 **DAX (Data Analysis Expressions)**
- 🔍 **Power Query (ETL)**
- 💪 **Power Pivot**

## Dataset

Real-world data science job postings from 2023, sourced via Luke Barousse's Data Analyst Bootcamp. Includes job titles, salaries, locations, and required skills.

---

## 1️⃣ Do More Skills Get You Better Pay?

### 🔍 Tool Used: Power Query (ETL)

#### 📥 Extract
Used Power Query to load the raw dataset and split it into two separate queries:
- `data_job_salary` — all job information
- `data_job_skills` — skills listed per job ID

#### 🔄 Transform

**data_jobs_all — Applied Steps:**

![Power Query Steps - data_jobs_all](Images/P2_SS_01.png)

Cleaned the dataset by changing column types, removing unnecessary columns, replacing text values, inserting calculated columns, and reordering fields for clarity.

**data_job_skills — Applied Steps:**

![Power Query Steps - data_job_skills](Images/P2_SS_02.png)

Cleaned the skills data by removing brackets, replacing delimiters, splitting columns, unpivoting, trimming text, capitalizing values, and renaming the final column.

#### 🔗 Load

**data_job_salary loaded:**

![Loaded data_job_salary](Images/P2_SS_03.png)

**data_job_skills loaded:**

![Loaded data_job_skills](Images/P2_SS_04.png)

### 📊 Analysis

![Skills vs Salary Chart](Images/P2_Chart_01.jpeg)

**💡 Insights:**
- A clear positive correlation exists between number of skills requested and median salary.
- Senior Data Engineer and Data Scientist roles — which require the most skills — also offer the highest pay.
- Roles like Business Analyst that require fewer skills sit at the lower end of the salary range.

**🤔 So What:**
Building multiple relevant skills is not just good practice — it directly maps to higher earning potential in the data field.

---

## 2️⃣ What's the Salary for Data Jobs in Different Regions?

### 🧮 Tools Used: PivotTables & DAX

Built a PivotTable using the Power Pivot Data Model. Added `job_title_short` to rows and `salary_year_avg` to values.

Created two DAX measures:

```dax
Median Salary US :=
CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
)

Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```

### 📊 Analysis

![Salary by Region Table](Images/P2_Chart_02.png)

**💡 Insights:**
- US salaries are consistently higher than Non-US across all roles.
- Senior Data Engineer tops at $150K in the US vs $147.5K Non-US — a relatively small gap at senior level.
- Data Analyst and Business Analyst show the least salary variation between regions.

**🤔 So What:**
Geography still plays a major role in compensation — especially for mid-level roles. US-based or US-remote roles offer significantly better pay for the same work.

---

## 3️⃣ What Are the Top Skills of Data Professionals?

### 💪 Tool Used: Power Pivot

Built a data model by connecting `data_jobs_all` and `data_job_skills` tables using `job_id` as the relationship key.

**Data Model:**

![Data Model Diagram](Images/P2_SS_05.png)

**Power Pivot Table:**

![Power Pivot Menu](Images/P2_SS_06.png)

### 📊 Analysis

![Top Skills Chart](Images/P2_Chart_03.png)

**💡 Insights:**
- SQL leads at ~70% likelihood in job postings, followed closely by Python at ~65%.
- Cloud tools like AWS, Azure, and Spark appear in 30-45% of postings — showing the industry's shift toward cloud infrastructure.
- Traditional tools like Java and Hadoop are still present but declining in relative demand.

**🤔 So What:**
SQL and Python are non-negotiable for anyone entering data roles. Cloud skills are the next priority to stay competitive.

---

## 4️⃣ What's the Pay for the Top 10 Skills?

### 📈 Tool Used: Combo PivotChart

Built a combo chart with:
- **Primary Axis:** Median Salary (Clustered Column)
- **Secondary Axis:** Skill Likelihood % (Line with Diamond Markers)

### 📊 Analysis

![Top 10 Skills Pay Chart](Images/P2_Chart_04.png)

**💡 Insights:**
- Python, Oracle, and Tableau are associated with the highest median salaries (~$95K-$100K).
- SQL has the highest skill likelihood (~52%) while still offering strong salary (~$92K).
- PowerPoint and Word show the lowest salaries and lowest demand — confirming that general productivity tools don't drive pay.

**🤔 So What:**
Investing time in Python, SQL, and visualization tools like Tableau or Power BI offers the best return for aspiring data professionals.

---

## Conclusion

This project gave me hands-on experience with Excel's advanced features — Power Query for data cleaning, Power Pivot for data modeling, DAX for custom measures, and PivotCharts for visualization. Working through real job market data made the analysis feel practical and directly relevant to my own career planning as an aspiring Data Analyst.

---

## Acknowledgements

This project is based on Luke Barousse's Excel Data Analytics Bootcamp. The dataset and project structure are credited to him. I completed this as a hands-on learning exercise to strengthen my Excel skills.
