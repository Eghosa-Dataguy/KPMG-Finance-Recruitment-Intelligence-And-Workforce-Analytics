# KPMG-Finance-Recruitment-Intelligence-And-Workforce-Analytics
<img width="1126" height="758" alt="KPMG 1" src="https://github.com/user-attachments/assets/1805234d-7bfa-4d5b-8516-485ab2b710b4" />
<img width="1222" height="791" alt="KPMG 2" src="https://github.com/user-attachments/assets/287c1441-cc35-4ee6-9264-b65f08b340b6" />
<img width="1254" height="779" alt="KPMG 3" src="https://github.com/user-attachments/assets/02e82e9e-622b-4257-a3a8-65d4b67972bb" />

---

## Table Of Content

1. [Project Overview]
2. [Tools & Technologies]
3. [Project Workflow]
4. [Dataset Description]
5. [Data Transformation — Power Query]
6. [Calculated Columns]
7. [DAX Measures — KPIs & Indicators]
8. [Data Modelling]
9. [Key Findings & Insights]
10. [Business Recommendations]
11. [Strategic Conclusion]
12. [Skills Demonstrated]
13. [Author]
---

## 📌 Project Overview

This project is a full end-to-end Power BI business intelligence solution for the finance recruitment industry. Using a dataset of 2,312 finance job postings across 6 countries, 8 cities, and 8 industries, I built three interactive dashboards to answer real workforce intelligence questions:

What does the finance talent market look like right now?

Where are salaries highest by role, country, industry, and experience?

Which jobs are being filled fastest and what factors drive hiring success?

How are recruiters performing and where are pipeline bottlenecks?

**Dataset scope**:

2,312 finance job postings (Job IDs: FIN-10001 to FIN-10297+)
12 job titles across 8 departments
8 industries: Banking, Manufacturing, Retail, FinTech, Consulting, Insurance, Investment, Telecommunications
6 countries: Nigeria, South Africa, USA, United Kingdom, UAE, Canada
8 cities: Lagos, Abuja, Port Harcourt, London, New York, Toronto, Dubai, Johannesburg
Salary range: $30,000 — $145,000 USD | Average mid-salary: $77,030

---

## 🛠 Tools & Technologies

#### Tool	Purpose
Power BI Desktop	Dashboard creation, data modelling, DAX measures
Power Query	Data cleaning, null handling, column transformations
DAX (Data Analysis Expressions)	KPIs, calculated measures, conditional formatting logic
Microsoft PowerPoint	Wireframing and UI planning for all 3 dashboards
Microsoft Excel (.xlsx)	Source data file
GitHub	Version control and project documentation

---

## 📋 Project Workflow

     Raw Excel Data
         ↓
     Power Query — Data Cleaning & Transformation
         ↓
    Calculated Columns (Salary Mid, Experience Band, High Salary Flag)
         ↓
    DAX Measures (KPIs, Indicators, Color Codes)
         ↓
    Date Table Creation
         ↓
    Data Modelling (Table Relationships)
         ↓
    PowerPoint Wireframes (3 Dashboard Layouts)
         ↓
    Power BI Dashboard Design & Publishing

---

## 📂 Dataset Description

The source dataset is a single Excel workbook with 2,312 rows and 33 columns:

| Column	                    |     Description                                                         |
|--------------------------  |-------------------------------------------------------------------------|
|  Job ID	                 |    Unique identifier (FIN-10001 to FIN-10297+)                          |
|  Company Name	           |    Hiring company (2,192 unique companies)                              |
|  Recruiter Name	           |    Assigned recruiter                                                   |
|  Job Title	              |    One of 12 finance roles                                              |
|  Department	              |    One of 8 finance departments                                         |
|  Industry	                 |    Sector the company operates in                                       |
|  Location	                 |    City of the posting                                                  |
|  Country	                 |    Country of the posting                                               |
|  Employment Type        	  |    Full-Time, Contract, or Internship                                   |
|  Work Mode	              |    Onsite, Hybrid, or Remote                                            |
|  Experience Level	        |    Entry, Mid, or Senior                                                |
|  Years of Experience	     |    Required years (0–12)                                                |
|  Salary Min	              |    Minimum salary in USD                                                |
|  Salary Max	              |    Maximum salary in USD                                                |
|  Posting Date	           |    Date the job was posted                                              |
|  Closing Date	           |    Date the job listing closed                                          |
|  Applicants Count	        |    Number of applicants received                                        |
|  Hiring Status	           |    Open, Closed, or Filled                                              |
|  Required Skills	        |    Comma-separated list of tools and skills                             |
|  Education Requirement	  |    BSc Finance / BSc Accounting / BSc Economics / MBA                   |
|  Certification Required    |    CPA, ICAN, CFA, ACCA — or NULL if not required                       |
|  Recruiter Rating	        |    Rating out of 5                                                      | 
|  Interview Count	        |    Number of interviews conducted                                       |
|  Hired Candidates	        |    Number of candidates successfully hired                              |
|  Time to Hire	           |    Days from posting to hire                                            |
|  Job Satisfaction Estimate |    Estimated satisfaction score                                         |
|  Company Rating	           |    Company rating out of 5                                              |
|  Benefits Offered	        |    Benefits package type                                                |
|  Finance Tool Required	  |    Primary tool required (Power BI, Excel, SAP, Tableau, SQL)           |
|  Revenue Size	           |    Company revenue band                                                 |
|  Company Size	           |    Small, Medium, or Enterprise                                         |

---

## 🔧 Data Transformation — Power Query

After loading the Excel file into Power BI, I used Power Query to clean and prepare the data:

### Step 1 — Handled Null Values in Certification Required

The Certification Required column contained 436 null/blank values representing roles where no certification was needed. Rather than leaving these blank (which would exclude them from visuals), I replaced all nulls with a descriptive label:

    Replace Value → null → "NOT REQUIRED"

This ensured all 2,312 records were fully represented in certification-based filters and charts.

### Step 2 — Verified and Confirmed Data Types

Ensured all columns were assigned the correct data types:

   * Salary Min, Salary Max → Decimal Number
   * Posting Date, Closing Date → Date
   * Years of Experience, Interview Count, Time to Hire → Whole Number
   * All text fields → Text
  
### Step 3 — Reviewed and Removed Duplicates
Confirmed no duplicate Job IDs existed across the dataset.

### Step 4 — Closed & Applied

All transformations were applied and the clean data was loaded into the Power BI data model.

---

## 🧮 Calculated Columns

After loading the data, I created 3 new calculated columns directly in the data model using DAX:

### 1. Salary Mid

Calculates the midpoint between the minimum and maximum salary for each job posting used as a normalised salary benchmark across all visuals.

      Salary Mid = 
         ( Finance_Dataset[Salary Min] + Finance_Dataset[Salary Max] ) / 2

**Why**: Salary Min and Salary Max represent a range. The midpoint gives a single, balanced salary figure that avoids overweighting either extreme standard practice in compensation analytics.

**Result**: Average Salary Mid across all records = $77,030

### 2. Experience Band
   
Groups the numeric Years of Experience field into meaningful categorical bands for cleaner visualisation and filtering.

     Experience Band = 
          SWITCH(
                 TRUE(),
                 Finance_Dataset[Years of Experience] <= 2, "0–2 Years",
                 Finance_Dataset[Years of Experience] <= 5, "3–5 Years",
                 Finance_Dataset[Years of Experience] <= 8, "6–8 Years",
                 "9–12 Years"
                    )

**Why**: Raw years (0–12) are hard to read in charts. Banding them into 4 groups makes experience distribution immediately interpretable on visuals.

### 3. High Salary Flag
   
A binary flag that identifies whether a job's Salary Mid is above the dataset average used for conditional formatting, KPI indicators, and colour coding in visuals.

    High Salary Flag = 
       IF(
        Finance_Dataset[Salary Mid] > AVERAGE(Finance_Dataset[Salary Mid]),
       "Above Average",
       "Below Average"
       )

**Why**: This flag enables instant visual segmentation of premium vs standard salary postings. It feeds into colour coding across charts and the KPI indicator cards on the dashboard.

**Result**: 1,136 out of 2,312 jobs (49.1%) are flagged as above-average salary.

---

## 📐 DAX Measures — KPIs & Indicators

I created a dedicated Measures Table in the data model to keep all DAX measures organised and separate from the source data. Key measures include:

**KPI Measures**

    -- Total Job Postings
    Total Postings = COUNTROWS(Finance_Dataset)

    -- Total Filled Roles
    Total Filled = 
    CALCULATE(COUNTROWS(Finance_Dataset), Finance_Dataset[Hiring Status] = "Filled")

    -- Fill Rate %
    Fill Rate % = 
    DIVIDE([Total Filled], [Total Postings], 0) * 100

    -- Average Salary Mid
    Avg Salary Mid = AVERAGE(Finance_Dataset[Salary Mid])

    -- Average Time to Hire
    Avg Time to Hire = AVERAGE(Finance_Dataset[Time to Hire])

    -- Average Applicants per Job
    Avg Applicants = AVERAGE(Finance_Dataset[Applicants Count])

    -- Average Recruiter Rating
    Avg Recruiter Rating = AVERAGE(Finance_Dataset[Recruiter Rating])

    -- Average Job Satisfaction
    Avg Job Satisfaction = AVERAGE(Finance_Dataset[Job Satisfaction Estimate])
   
   ## Indicator & Colour Code Measures
   
   These measures drive the dynamic KPI card colours green for good performance, red for below threshold making the dashboard self-explanatory at a glance.

    -- Fill Rate Colour
    Fill Rate Color = 
    IF([Fill Rate %] >= 30, "Green", "Red")

    -- Time to Hire Indicator
    Time to Hire Status = 
    IF([Avg Time to Hire] <= 30, "✅ On Target", "⚠️ Delayed")

    -- Salary Status
    Salary Status = 
     IF([Avg Salary Mid] >= 77000, "Above Benchmark", "Below Benchmark")

    -- Recruiter Performance Colour
     Recruiter Color = 
     IF([Avg Recruiter Rating] >= 4, "Green", "Amber")
   
   ## Supporting Measures
   
    -- Open Jobs Count
    Open Jobs = 
    CALCULATE([Total Postings], Finance_Dataset[Hiring Status] = "Open")

    -- Closed Jobs Count
    Closed Jobs = 
    CALCULATE([Total Postings], Finance_Dataset[Hiring Status] = "Closed")

    -- High Salary Job Count
    High Salary Count = 
    CALCULATE([Total Postings], Finance_Dataset[High Salary Flag] = "Above Average")

    -- Avg Salary by Country (used in tooltip)
    Avg Salary by Country = 
          CALCULATE(AVERAGE(Finance_Dataset[Salary Mid]), 
          ALLEXCEPT(Finance_Dataset, Finance_Dataset[Country]))

---

## 🗂 Data Modelling

The data model was structured to support efficient filtering and cross-visual interactions:

 **Tables in the model**:

* Finance_Dataset — Main fact table (2,312 rows, 33 columns + 3 calculated columns)
* Date Table — Created using DAX for time intelligence filtering
* Measures Table — Dedicated table holding all DAX measures (no data rows)

**Date Table (created via DAX)**:

Date Table = 

    CALENDAR(
        MIN(Finance_Dataset[Posting Date]),
        MAX(Finance_Dataset[Closing Date])
     )

Date Table columns added:

    Year = YEAR('Date Table'[Date])
    Month = FORMAT('Date Table'[Date], "MMMM")
    Month Number = MONTH('Date Table'[Date])
    Quarter = "Q" & QUARTER('Date Table'[Date])

**Relationship**:

Date Table[Date] → Finance_Dataset[Posting Date] (One-to-Many, Single direction)

This relationship enables time-based filtering across all visuals (e.g., job postings by month, hiring trends over time).

---

## 💡 Key Findings & Insights

**Finding**

1	Nigeria dominates postings — 826 jobs (35.7%), more than any other country by a wide margin

2	32.3% Fill Rate — Only 747 of 2,312 postings were filled, signalling significant pipeline inefficiency

3	Avg Salary Mid: $77,030 — With a wide $30K–$145K range, experience and certification drive major salary variation

4	49.1% of jobs are high-salary — Nearly half of postings sit above the dataset salary average

5	Avg Time to Hire: 32.9 days — Finance roles take over a month on average to fill

6	202 avg applicants per job — High competition across all roles, especially Data Analyst and Credit Analyst

7	436 jobs require NO certification — 18.9% of postings — meaning certification holders face less competition for premium roles

8	Work mode is nearly evenly split — Onsite (33.7%), Hybrid (33.5%), Remote (32.8%) — flexibility is the norm, not the exception

9	Manufacturing and Retail lead by industry — 307 and 303 postings respectively

10	Recruiter Rating and Job Satisfaction both average ~4.0/5 — Solid baseline performance, with room for improvement

---

## 🎯 Business Recommendations

Based on the analysis of 2,312 finance job postings, salary trends, applicant volumes, and recruitment performance metrics, the following recommendations can help organizations improve hiring efficiency, attract top finance talent, and optimize recruitment outcomes.

## 1. Improve Recruitment Pipeline Efficiency
   
**Business Issue**

Only 32.3% of job postings were successfully filled, indicating inefficiencies across the recruitment process.

**Recommendation**

Organizations should review each stage of the recruitment funnel to identify bottlenecks and candidate drop-off points.

**Suggested Actions**:

* Reduce unnecessary interview stages.
* Automate candidate screening processes.
* Improve recruiter response times.
* Standardize hiring workflows across departments.

**Expected Impact**:


* Increased fill rates.
* Reduced recruitment delays.
* Improved candidate experience.
  
## 2. Reduce Time-to-Hire
   
**Business Issue**

The average finance position takes approximately 33 days to fill, resulting in prolonged vacancies and potential productivity losses.

**Recommendation**

Implement recruitment Service Level Agreements (SLAs) to accelerate hiring decisions.

**Suggested Actions**:

* Establish hiring timeline targets.
* Build talent pipelines for frequently recruited roles.
* Schedule interviews more efficiently.
* Monitor recruiter turnaround times.

**Expected Impact**:

* Faster hiring cycles.
* Reduced vacancy costs.
* Improved hiring efficiency.
  
## 3. Strengthen Compensation Competitiveness

**Business Issue**

Nearly 49.1% of job postings offer above-average salaries, highlighting strong competition for qualified finance professionals.

**Recommendation**

Regularly benchmark compensation packages against market standards to remain competitive.

**Suggested Actions**:

* Review salary structures periodically.
* Offer performance-based incentives.
* Enhance employee benefits packages.
* Introduce flexible work arrangements where possible.

**Expected Impact**:

* Higher offer acceptance rates.
* Improved talent attraction.
* Reduced candidate drop-off during negotiations.
  
## 4. Prioritize Professional Certifications

**Business Issue**

Approximately 81% of finance positions require professional certifications, making certifications a major hiring criterion.

**Recommendation**

Organizations should prioritize certified candidates and invest in employee certification development programs.

**Suggested Actions**:

* Target candidates with ICAN, ACCA, CPA, and CFA qualifications.
* Sponsor professional certification programs.
* Create certification-based career progression plans.

**Expected Impact**:

* Higher workforce competency.
* Improved employee performance.
* Stronger talent quality.

## 5. Enhance Employer Branding

**Business Issue**

The average job posting attracts approximately 202 applicants, creating intense competition for top talent.

**Recommendation**

Employers should strengthen their employer brand to attract higher-quality candidates.

**Suggested Actions**:

* Promote career growth opportunities.
* Showcase company culture and employee success stories.
* Improve candidate communication throughout the hiring process.
* Highlight workplace benefits and flexibility.

**Expected Impact**:

* Better applicant quality.
* Stronger employer reputation.
* Improved candidate engagement.

## 6. Expand Flexible Work Policies

**Business Issue**

Work mode preferences are nearly evenly distributed across Remote, Hybrid, and Onsite roles, indicating strong demand for flexibility.

**Recommendation**

Organizations should maintain flexible work arrangements where operationally feasible.

**Suggested Actions**:

* Expand hybrid work options.
* Introduce remote-friendly finance positions.
* Offer flexible scheduling policies.

**Expected Impact**:

* Larger talent pool.
* Improved employee satisfaction.
* Higher retention rates.

## 7. Focus Recruitment Resources on High-Demand Industries

**Business Issue**

Manufacturing, Retail, and FinTech sectors generated the highest recruitment activity.

**Recommendation**

Recruitment teams should allocate additional sourcing resources toward industries with sustained hiring demand.

**Suggested Actions**:

* Develop industry-specific talent pipelines.
* Increase sourcing efforts in high-growth sectors.
* Build specialized recruiter expertise.

**Expected Impact**:

* Improved recruiter productivity.
* Higher placement success rates.
* Better workforce planning.
  
## 8. Establish Recruiter Performance Monitoring

**Business Issue**

Recruitment outcomes vary significantly across recruiters, creating opportunities for performance improvement.

**Recommendation**

Implement recruiter performance scorecards using measurable recruitment KPIs.

## Suggested KPIs:

* Fill Rate
* Time-to-Hire
* Interview-to-Hire Ratio
* Candidate Satisfaction
* Hiring Manager Satisfaction

**Expected Impact**:

* Greater recruiter accountability.
* Consistent recruitment performance.
* Improved hiring outcomes.

---

## 📌 Strategic Conclusion

The analysis highlights a highly competitive finance recruitment landscape, driven by a large pool of applicants, moderate recruitment effectiveness, growing demand for professional certifications, and intensified competition for qualified finance talent.
 To attract and retain top candidates, organizations should focus on optimizing their hiring processes, offering competitive compensation packages, investing in certified professionals, enhancing their employer brand, and adopting flexible work arrangements. These strategies can help reduce recruitment timelines and improve access to high-quality talent in an increasingly competitive job market.
 
---

## 🧠 Skills Demonstrated

* ✅ End-to-end Power BI project development from raw data to published dashboard
* ✅ Power Query data cleaning: null replacement, type correction, column validation
* ✅ DAX calculated columns: Salary Mid, Experience Band, High Salary Flag
* ✅ DAX measures: KPIs, ratios, conditional indicators, and colour codes
* ✅ Dedicated Measures Table — professional model organisation
* ✅ Date Table creation using DAX for time intelligence
* ✅ Data modelling: table relationships, one-to-many joins
* ✅ PowerPoint wireframing before dashboard build — professional UI planning
* ✅ Multi-page Power BI report with navigation between dashboards
* ✅ Business interpretation of data into actionable workforce insights
  
---

## Author

## Clement Eghosa

Data Analyst | Financial Analyst | Business Analyst | Business Intelligence Enthusiast

 * Microsoft Excel
 * Power BI
 * SQL
 * Data Visualization
 * Dashboard Development
 * Business Analytics

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/eghosa-osalob)
[![GitHub](https://img.shields.io/badge/GitHub-View%20Profile-black?logo=github)](https://github.com/Eghosa-Dataguy)

---

*⭐ If you found this project helpful, consider giving the repository a star or connect on Linkedln.*

