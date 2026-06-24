# 📊 Sample HR Analytics Dashboard

A comprehensive **HR Analytics Dashboard** developed during my internship at SPR Consultech, designed to analyze employee metrics, identify key performance indicators (KPIs), and provide actionable insights for HR business decisions.

---

## 🎯 Project Overview

**Role:** Data Analyst Intern  
**Organization:** SPR Consultech  
**Duration:** 1 month [JUL'25-AUG'25]  
**Tools:** Power BI, Excel, Data Modeling  
**Objective:** Transform raw HR data into interactive dashboards for stakeholder insights

---

## 📊 What This Dashboard Does

✅ **Employee Analytics** - Headcount, demographics, active/inactive status tracking  
✅ **Leave Management** - Leave balance, usage patterns, departmental trends  
✅ **Salary Analytics** - Compensation analysis by department, location, and role  
✅ **Attrition Insights** - Attrition rate trends, exit category distribution  
✅ **Geographic Analysis** - Employee distribution across multiple countries  
✅ **KPI Tracking** - CPE (Cost Per Employee), active employee count, workforce metrics  

---

## 🏗️ Data Architecture

### **Tables & Relationships:**

```
Employee Master ──────┐
                      ├─→ Analysis & Insights
Salary ───────────────┤
                      ├─→ Power BI Visuals
Leave ────────────────┤
                      ├─→ Dashboard Output
DimCalendar ──────────┘
```

### **Key Tables:**

1. **Employee Master**
   - Employee ID, Age, Age Groups, Acting Role, Active Status
   - Unique identifier for all employee records

2. **Salary**
   - Annual Salary, Cost Center Code, Country, Department, CPE
   - Financial metrics for compensation analysis

3. **Leave**
   - Balance Carried Forward, Cancelled Leaves, Captured Units
   - Leave category and status tracking

4. **DimCalendar**
   - Date dimensions, Month/Year hierarchy, Fiscal periods
   - Enables time-based analysis

---

## 📈 Key Metrics & KPIs

| KPI | Value | Insight |
|-----|-------|---------|
| **Total Active Employees** | 1,946 | Main workforce headcount |
| **Male Employees** | 1,712 | Gender distribution |
| **Female Employees** | 234 | Diversity metric |
| **Attrition Rate** | 0.3% | Very low attrition (stable workforce) |
| **CPE (Cost Per Employee)** | 10,940 | Workforce cost efficiency |
| **Countries** | 5 | Brazil, Chile, Mexico, Peru, South Africa |
| **Departments** | 10+ | Operations, Workshop, Engineering, etc. |

---

## 🎨 Dashboard Features

### **Page 1: Executive Summary**
- Active employee count (with gender breakdown)
- Attrition rate and trend analysis
- CPE metric for workforce efficiency
- Quick status filters

### **Page 2: Employee Analysis**
- Employee count by department
- Demographic distribution (age groups, roles)
- Employee distribution by country
- Active vs. inactive employee comparison

### **Page 3: Leave Management**
- Total leaves taken by department
- Average leave usage patterns
- Leave balance tracking
- Department-wise leave distribution

### **Page 4: Salary Analysis**
- Sum of salary per employee by department
- Compensation trends
- Cost analysis by business unit

### **Page 5: Attrition Analysis**
- Attrition rate trends over time (month-year view)
- Exit category distribution
- Department-wise attrition comparison

### **Page 6: Cross-Sheet Analysis**
- Comprehensive data relationships
- Drill-down capabilities
- Multi-dimensional analysis

---

## 💡 Key Technical Skills Demonstrated

✅ **Data Modeling** - Star schema design with proper table relationships  
✅ **DAX Calculations** - Complex measures (Attrition Rate, CPE, etc.)  
✅ **Power BI Visualizations** - Cards, bar charts, pie charts, line charts, tables  
✅ **Interactive Filtering** - CurrentStatus filters, drill-down capabilities  
✅ **Data Cleaning** - Excel data preparation before Power BI ingestion  
✅ **Business Intelligence** - KPI identification and business metric tracking  
✅ **Data Storytelling** - Multi-page dashboard for different audience perspectives  

---

## 📁 Repository Structure

```
HR-Analytics-Dashboard/
├── 📊 dashboard/
│   ├── sample_data_analysis_spr.pbix       (Power BI file)
│   └── dashboard_screenshot.png             (Visual preview)
│
├── 📁 data/
│   ├── SPR-HR_data.xlsx                    (Raw data - anonymized)
│   └── Data_Dictionary.md                   (Column descriptions)
│
├── 📄 README.md                             (This file)
├── 📄 Methodology.md                        (Analysis approach)
└── .gitignore                               (Confidentiality protection)
```

---

## Files In This Project

- **sample_data_analysis_spr.pbix** - The Power BI dashboard file (open in Power BI)
- **https://github.com/yogashreepattugarla03/HR-Analytics-Dashboard/blob/main/data/SPR-HR%20data.xlsx** - The raw data (Excel file)
- **Data_Dictionary.md** - Explains what each column means
- **Methodology.md** - How I built this project
- **Screenshots** - Pictures of the dashboard

---

## How To Use This Project

1. **Want to see the dashboard?** → Open the `.pbix` file in Power BI
2. **Want to see the data?** → Open the `.xlsx` file in Excel
3. **Want to understand columns?** → Read `Data_Dictionary.md`
4. **Want to know how I built it?** → Read `Methodology.md`

---

## 📊 Insights & Findings

### **1. Workforce Stability**
- Attrition rate of 0.3% indicates excellent employee retention
- 1,946 active employees across 5 countries
- Stable workforce composition

### **2. Geographic Distribution**
- Peru has highest employee count (796)
- South Africa (1,578 inactive), Chile, Brazil, Mexico also present
- Multi-country HR operations management

### **3. Leave Patterns**
- RAU (Research & Development) leads in leave usage (22 days)
- RR-PQ shows 19 average days
- Consistent leave distribution across departments

### **4. Salary Intelligence**
- Aggregated CPE: 10,940 (cost per employee metric)
- Operations & Workshop are largest cost centers
- Department-wise salary variance analysis available

### **5. Department Insights**
- "Other" category dominates (1,169 employees)
- Operations (749), Workshop (161), Engineering (158) are major departments
- Diverse organizational structure

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | Dashboard creation, visualization, DAX |
| **Excel** | Data cleaning, preprocessing, pivot tables |
| **DAX (Data Analysis Expressions)** | Complex calculations (Attrition, CPE, metrics) |
| **Power Query** | Data transformation & loading |

---

## 📚 What I Learned

✨ **Data Modeling Best Practices**
- Building star schema for analytics
- Creating proper table relationships
- Designing for query efficiency

✨ **Power BI Advanced Features**
- DAX measures and calculated columns
- Interactive filtering and drill-down
- Multi-page dashboard design
- Performance optimization

✨ **Business Analytics**
- Identifying meaningful KPIs
- Understanding HR metrics (attrition, CPE, etc.)
- Communicating insights to stakeholders
- Data-driven decision making

✨ **Data Storytelling**
- Designing dashboards for different audiences
- Selecting appropriate visualizations
- Creating actionable insights
- Executive summary design

