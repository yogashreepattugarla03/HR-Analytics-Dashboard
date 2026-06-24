# Project Methodology

This explains how I built the dashboard.

---

## Step 1: Understand The Data

I looked at the raw Excel data and identified:
- 4 main tables: Employee, Salary, Leave, Calendar
- Checked for missing or duplicate data
- Made sure all employee IDs match across tables
- Confirmed data quality and consistency

---

## Step 2: Design The Data Model

Connected the 4 tables using Employee ID as the key and created a "Star Schema" structure.

**The structure:**
```
Employee Master (who)
    ↓
Salary (how much they earn)
Leave (time off)
Calendar (when)
```

This design is:
- Fast - easier for Power BI to process
- Simple - easier to understand
- Flexible - easy to add more data later

---

## Step 3: Identify Important Metrics (KPIs)

Decided to measure:

| Metric | Why It Matters |
|--------|----------------|
| **Active Employees** | Shows company size |
| **Attrition Rate** | Shows if people are leaving |
| **Cost Per Employee** | Shows cost efficiency |
| **Leave by Department** | Shows workload across teams |
| **Salary by Department** | Shows compensation data |
| **Gender Distribution** | Shows diversity metrics |
| **Geographic Distribution** | Shows where people work |

---

## Step 4: Create Calculations (DAX Formulas)

Wrote formulas to calculate metrics:

### Active Employees Formula
Count all rows where Status = "Active"  
Result: 1,946

### Attrition Rate Formula
(Count Terminated / Count Total) * 100  
Result: 0.3%

### Average Leave by Department Formula
Sum of all leave / Count of departments

These formulas allow Power BI to calculate metrics automatically instead of doing it manually in Excel.

---

## Step 5: Design The Dashboard

Created 6 different pages:

### Page 1: Executive Summary
- Top-level numbers for quick overview
- Shows active employees, attrition rate, CPE

### Page 2: Employee Analysis
- Employee count by department and country
- Age distribution analysis

### Page 3: Leave Analysis
- Leave usage patterns
- Which departments take most leave

### Page 4: Salary Analysis
- Salary breakdown by department
- Cost analysis by business unit

### Page 5: Attrition Trends
- Trends over time
- Exit category breakdown

### Page 6: Detailed Breakdown
- All data together
- For deeper analysis

Different pages serve different purposes so each user can see what they need.

---

## Step 6: Add Filters

Added interactive filters so users can focus on specific data:

- **Current Status** - See only active/inactive/terminated employees
- **Department** - Filter by specific department
- **Country** - Filter by specific country
- **Date** - See trends over specific time periods

---

## Key Decisions Made

### Decision 1: Anonymize Data
Replaced employee names with IDs to protect privacy and maintain confidentiality.

### Decision 2: Separate Tables
Kept employee info, salary, and leave in separate tables to keep data organized and flexible for future changes.

### Decision 3: Use DAX for Calculations
Used DAX formulas instead of Excel to make calculations automatic and professional.

### Decision 4: Create Multiple Pages
Created different dashboard pages so different people (executives, HR, finance, analysts) can see what they need.

---

## Findings From The Data

**Finding 1: Very Low Attrition**
- Only 0.3% of employees left
- Indicates good employee satisfaction and retention

**Finding 2: Multi-Country Operation**
- 5 countries with Peru having the most employees (796)
- Shows it's a large, global company

**Finding 3: Leave Patterns Vary**
- Different departments take different amounts of leave
- Indicates different workload levels across teams

**Finding 4: Cost Efficiency**
- CPE of 10,940 is stable
- Helps with budgeting and financial planning

---

## Skills Used

| Skill | What I Did |
|-------|-----------|
| **Power BI** | Built the dashboard and created visualizations |
| **Excel** | Prepared and cleaned the raw data |
| **DAX** | Wrote formulas to calculate metrics and KPIs |
| **Data Modeling** | Connected tables and created relationships |
| **Database Design** | Used star schema best practices |
