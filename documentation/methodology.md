# Analysis Methodology - SPR HR Analytics Dashboard

## Overview
This document outlines the approach, methodology, and analytical framework used to develop the SPR HR Analytics Dashboard.

---

## Analysis Objectives

1. **Transform Raw Data** → Convert employee data into actionable insights
2. **Identify Key Metrics** → Define and calculate critical HR KPIs
3. **Enable Data-Driven Decisions** → Support HR strategy with analytics
4. **Provide Self-Service Analytics** → Create interactive dashboards

---

## Development Process

### **step 1: Data Understanding & Preparation**

**Steps Taken:**
- Analyzed source data structure in Excel
- Identified 4 main tables: Employee Master, Salary, Leave, Calendar
- Validated data integrity and relationships
- Documented data quality issues (if any) and resolutions

**Data Exploration:**
- Employee count: 1,946 active employees
- Countries: 5 (Brazil, Chile, Mexico, Peru, South Africa)
- Departments: 10+ distinct business units
- Time period: [Actual data period]
- Data granularity: Employee-level transactions

**Findings:**
- Data quality: High
- Missing values: Minimal handling required
- Outliers: None identified
- Duplicates: None found

---

### **step 2: Data Modeling**

**Architecture Decision: Star Schema**

Why Star Schema?
✅ Optimized for analytics queries  
✅ Maintains data integrity  
✅ Enables efficient joins  
✅ Supports multidimensional analysis  

**Table Design:**

```
FACT TABLES (Events/Transactions):
├─ Leave (transactions)
└─ Salary (employee records)

DIMENSION TABLES (Context):
├─ Employee Master (who)
├─ DimCalendar (when)
└─ Department/Country (where)
```

**Relationships Established:**
- EmployeeID (Primary Key) → Links all tables
- One-to-Many: Employee Master → Salary, Leave
- One-to-Many: DimCalendar → Time-based analysis

**Data Types Optimization:**
- Integers for IDs → Efficient joins
- Currency for salary → Proper aggregation
- Text for categorical → Filtering clarity
- Date for temporal → Time analysis

---

### **step 3: KPI Identification**

**HR Metrics Selected & Rationale:**

| KPI | Formula | Business Value |
|-----|---------|-----------------|
| **Active Employees** | COUNT(EmployeeID) WHERE Status='Active' | Workforce size tracking |
| **Attrition Rate** | Terminated / Total * 100 | Retention health |
| **CPE (Cost Per Employee)** | Total Salary / Headcount | Workforce cost efficiency |
| **Gender Distribution** | Count by Gender | Diversity metrics |
| **Leave Utilization** | Sum(Leave Taken) by Department | Work-life balance tracking |
| **Salary Analysis** | Sum/Avg Salary by Department | Compensation equity |
| **Department Distribution** | Count by Department | Org structure clarity |
| **Geographic Spread** | Count by Country | Multi-location analysis |

**Why These Metrics?**
- Directly support HR business questions
- Actionable for HR decision-makers
- Benchmarkable against industry standards
- Align with organizational strategy

---

### **step 4: DAX Calculations**

**Measures Created:**

```dax
// Count-based measures
Active Employees = CALCULATE(COUNTA(EmployeeMaster[EmployeeID]), 
  EmployeeMaster[CurrentStatus]="Active")

Male Employees = CALCULATE(COUNTA(EmployeeMaster[EmployeeID]), 
  EmployeeMaster[Gender]="M")

Terminated Count = CALCULATE(COUNTA(EmployeeMaster[EmployeeID]), 
  EmployeeMaster[CurrentStatus]="Terminated")

// Rate calculations
Attrition Rate = [Terminated Count] / COUNTA(EmployeeMaster[EmployeeID])

// Aggregations
Total CPE = SUM(Salary[CPE])

Total Salary = SUM(Salary[Annual_Salary])

Average Salary = AVERAGE(Salary[Annual_Salary])

Total Leaves Taken = SUM(Leave[CapturedUnits])

// Time intelligence (if applicable)
YoY Growth = [Current Year] / [Previous Year]
```

**Calculation Approach:**
- Use CALCULATE for conditional logic
- Apply FILTER for segment-specific analysis
- Leverage SUMX/AVERAGEX for row context
- Use time intelligence functions for trends

---

### **step 5: Visualization Design**

**Visualization Selection Rationale:**

| Chart Type | When Used | Why |
|-----------|-----------|-----|
| **Cards** | Single KPI | Quick scanning |
| **Bar Charts** | Category comparison | Easy ranking comparison |
| **Pie Charts** | Part-to-whole | Segment proportions |
| **Line Charts** | Trends over time | Pattern recognition |
| **Tables** | Detailed data | Precision, drill-down |
| **Matrix/Heatmap** | Multi-dimensional | Complex relationships |

---

### **step 6: Interactivity & Filtering**

**Filters Implemented:**

1. **CurrentStatus Filter**
   - Values: Active, Inactive, New, Re-Instate New, Terminated
   - Impact: Affects all employee counts
   - Use Case: Segment analysis

2. **Department Filter**
   - Dynamic based on data
   - Impact: Narrows analysis to specific units
   - Use Case: Department manager drill-down

3. **Country Filter**
   - Values: Brazil, Chile, Mexico, Peru, South Africa
   - Impact: Geographic segmentation
   - Use Case: Multi-country analysis

4. **Time Filter (Month/Year)**
   - Based on DimCalendar
   - Impact: Trend analysis over time
   - Use Case: Historical trend tracking

---

## 📈 Analysis Insights Discovered

### **Workforce Stability**
- **Finding:** Attrition rate of 0.3% is exceptionally low
- **Implication:** Strong employee retention, low turnover costs
- **Recommendation:** Identify and share retention best practices

### **Geographic Distribution**
- **Finding:** Peru has largest employee concentration (796 employees)
- **Implication:** Significant Latin American operations
- **Recommendation:** Monitor location-specific HR practices

### **Leave Patterns**
- **Finding:** RAU department shows highest average leave (22 days)
- **Implication:** Potential workload or burnout indicator
- **Recommendation:** Review workload distribution in RAU

### **Salary Efficiency**
- **Finding:** CPE averaged 10,940 across workforce
- **Implication:** Stable, predictable workforce costs
- **Recommendation:** Use as baseline for budget forecasting

### **Department Insights**
- **Finding:** "Other" category dominates (1,169 employees)
- **Implication:** Need for better department classification
- **Recommendation:** Standardize department naming convention

---

## Tools & Technologies used

| Tool | Purpose | Version/Skill Level |
|------|---------|-------------------|
| **Power BI Desktop** | Dashboard development | Intermediate-Advanced |
| **DAX** | Complex calculations | Intermediate |
| **Power Query** | Data transformation | Intermediate |
| **Excel** | Data preparation | Intermediate |
| **SQL-like Relationships** | Data modeling | Intermediate |

---
