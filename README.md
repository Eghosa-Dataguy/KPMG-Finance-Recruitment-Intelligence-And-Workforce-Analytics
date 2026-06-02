# KPMG-Finance-Recruitment-Intelligence-And-Workforce-Analytics
<img width="1126" height="758" alt="KPMG 1" src="https://github.com/user-attachments/assets/1805234d-7bfa-4d5b-8516-485ab2b710b4" />
<img width="1222" height="791" alt="KPMG 2" src="https://github.com/user-attachments/assets/287c1441-cc35-4ee6-9264-b65f08b340b6" />
<img width="1254" height="779" alt="KPMG 3" src="https://github.com/user-attachments/assets/02e82e9e-622b-4257-a3a8-65d4b67972bb" />

This project provided an excellent opportunity to integrate data visualization, workforce analytics,and business intelligence into a comprehensive executive-level reporting solution that help stakeholders monitor performance, identify trends, and make informed strategic decisions. Where i loaded the datatsets into  Excel for necessary cleaning and better understanding of what the datasets is all about, then i moved on to loading it into PowerBI (Power Query) where i opened a new columns for Salary Mid-point, Experience Band, High Salary-Flag, Required Skills, & Skill Count and also opened a New Table as Date Table for appropraite trend analysis. Afterwards i moved on in Calculating my DAX Measures and making the visuals and proving accurate insights and decisions :

Avg Time to Hire:
   Average Time to Hire = FORMAT(AVERAGE
         ('Finance Dataset'[Time to Hire]), "0"
         ) & " Days"


Total Interviews Conducted = SUM(
          'Finance Dataset'[Interview Count]
          )
    

Total Hired Candidates = SUM(
       'Finance Dataset'[Hired Candidates]
       )
  

Hiring Success Rate = DIVIDE(
      [Total Hired],
         [Total Applicant],
     0)


Avg Company Rating = AVERAGE(
       'Finance Dataset'[Company Rating]
       )
        
 
## INSIGHTS :
* The finance job market is highly active, with ***2.31K*** job postings, ***2.19K*** hiring companies, & ***468K*** applicants,nindicating strong competition for finance roles.
* Demand is fairly balanced across full-time, contract, & internship positions, while onsite, hybrid, & remote work modes are almost equally represented.
* Roles such as Internal Auditor, Risk Analyst, Tax Analyst, & FP & A Analyst are among the most sought-after positions.
* Employers consistently prioritize technical skills, with SQL,Power BI,ableau, Excel, SAP,&Python appearing as the most frequently requested competencies.
* Average salaries range from ***59K-95K***, with senior-level professionals earning significantly more than mid-level &entry-level candidates.
* Recruitment efficiency remains a challenge, with an average time-to-hire of ***33days*** & a relatively low hiring success rate of ***2.7%***, suggesting a large gap between applicant volume & successful placements.
* Manufacturing, Retail, & FinTech industries show the highest hiring activity, while Investment& Insurance sectors offer some of the most competitive salaries.
  
 ## RECOMMENDATIONS.
* Job seekers should strengthen proficiency in SQL, Power BI, Excel, Tableau, and Python, as these skills are consistently demanded across finance roles.
* Organizations should streamline recruitment processes to reduce the 33days average hiring cycle & improve hiring conversion rates.
* Recruiters should focus on targeted candidate screening& talent matching to address the low 2.7% hiring success rate.
* Companies can attract stronger talent by offering competitive salary packages& flexible work arrangements, especially for high-demand finance positions.
* Training& certification programs should be encouraged, as over 80% of roles require professional certifications or specialized qualifications.
* Businesses should invest in workforce planning and analytics to better align hiring needs with market demand &improve recruitment efficiency.

 Beyond the charts& metrics, the dashboard shows how organizations can identify high-demand roles, benchmark salary competitiveness, understand what skills employers are prioritizing, & assess how effectively their hiring process is performing.
 
 ## Tools & Skills:
* Power BI Desktop
* Power Query(ETL Processing)
* DAX (Data Modeling & Calculations)
* Data Visualization Techniques\Business Intelligence
* KPI Design Framework
* Data Storytelling\Decision-Making

  Kindly give me a star⭐ if you find this helpful
