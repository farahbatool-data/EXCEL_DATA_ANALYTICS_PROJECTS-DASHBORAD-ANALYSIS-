# Excel Salary Dashboard

![Dashboard Preview](Images/project_Gif.gif)

## Introduction

This data jobs salary dashboard was created to help job seekers investigate salaries for their desired jobs and ensure they are being adequately compensated.

The data is from Luke Barousse's Excel course, which provides a foundation in analyzing data using this powerful tool. The dataset contains detailed information on job titles, salaries, locations, and essential skills.

### Dashboard File
My final dashboard is in [Salary_Dashboard_01.xlsx](Salary_Dashboard_01.xlsx).

### Excel Skills Used

- **📉 Charts**
- **🧮 Formulas and Functions**
- **❎ Data Validation**

### Data Jobs Dataset

The dataset contains real-world data science job information from 2023. It includes:

- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

---

## Dashboard Build

### 📉 Charts

#### 📊 Data Science Job Salaries - Bar Chart

![Bar Chart](Images/char_bar.jpeg)

- 🛠️ **Excel Features:** Utilized bar chart feature with formatted salary values and optimized layout for clarity.
- 🎨 **Design Choice:** Horizontal bar chart for easy visual comparison of median salaries across roles.
- 📉 **Data Organization:** Sorted job titles by descending salary for improved readability.
- 💡 **Insights Gained:** Senior roles and Engineers are higher-paying than Analyst roles. Senior Data Scientist leads at ~$155K.

---

#### 🗺️ Country Median Salaries - Map Chart

![Map Chart](Images/map.jpeg)

- 🛠️ **Excel Features:** Utilized Excel's map chart feature to plot median salaries globally.
- 🎨 **Design Choice:** Color-coded map to visually differentiate salary levels across regions.
- 📊 **Data Representation:** Plotted median salary for each country with available data.
- 💡 **Insights Gained:** Clear global salary disparities visible — North America and parts of Europe show higher salary ranges.

---

### 🧮 Formulas and Functions

#### 💰 Median Salary by Job Titles

```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

- 🔍 **Multi-Criteria Filtering:** Checks job title, country, schedule type, and excludes blank salaries.
- 📊 **Array Formula:** Uses `MEDIAN()` with nested `IF()` to analyze an array of values.
- 🎯 **Tailored Insights:** Returns median salary based on job title, country, and schedule type selected.

🍽️ **Background Table**

![Background Table](Images/table_background%20.jpeg)

📉 **Dashboard Implementation**

![Dashboard Implementation](Images/dashboard_impl.jpeg)

---

#### ⏰ Count of Job Schedule Type

```
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

- 🔍 **Unique List Generation:** Uses `FILTER()` to exclude entries containing "and" or commas, and omit zero values.
- 🔢 **Formula Purpose:** Generates a clean list of unique job schedule types for the dashboard dropdown.

---

### ❎ Data Validation

#### 🔍 Filtered List

- 🔒 **Enhanced Data Validation:** Filtered list applied as data validation rule under `Job Title`, `Country`, and `Type`:
    - 🎯 User input restricted to predefined, validated options
    - 🚫 Incorrect or inconsistent entries are prevented
    - 👥 Overall dashboard usability is improved

---

## Conclusion

I built this dashboard as part of Luke Barousse's Excel course to explore salary trends across data-related job titles. The dashboard allows users to filter by job title, country, and schedule type to make informed career decisions. This project helped me strengthen my Excel skills — particularly array formulas, map charts, and data validation.

---

## Acknowledgements

This project is based on the original work by **[Luke Barousse](https://github.com/lukebarousse)** from his Excel Data Analytics course. The dataset, structure, and core analysis approach are credited to him. I replicated this project as a hands-on learning exercise to strengthen my Excel skills in charts, formulas, and data validation.
