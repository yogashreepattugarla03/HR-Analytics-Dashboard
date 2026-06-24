# Data Dictionary - SPR HR Analytics Dashboard

## Overview
This document describes all columns and tables in the SPR HR Analytics dataset used for the Power BI dashboard.

---

## **TABLE 1: Employee Master**

| Column Name | Data Type | Description | Example |
|------------|-----------|-------------|---------|
| **EmployeeID** | Integer | Unique identifier for each employee | 1001 |
| **Acting_Role** | Text | Current job role/position | Manager, Executive, Associate |
| **Age** | Integer | Employee age in years | 32 |
| **Age_Bins** | Text | Age grouped into ranges | 20-30, 30-40, 40-50 |
| **Age_Buckets** | Text | Age categorization | Young, Mid-Career, Senior |
| **CurrentStatus** | Text | Employment status | Active, Inactive, New, Re-Instate New, Terminated |

**Key Insight:** This is the core employee dimension table. Used for headcount analysis, demographics, and status tracking.

---

## **TABLE 2: Salary**

| Column Name | Data Type | Description | Example |
|------------|-----------|-------------|---------|
| **EmployeeID** | Integer (FK) | Foreign key linking to Employee Master | 1001 |
| **Annual_Salary** | Currency | Annual compensation in local currency | 50000 |
| **Cost_Center_Code** | Text | Organizational cost center code | CC001, CC002 |
| **Country** | Text | Country of employment | Brazil, Chile, Mexico, Peru, South Africa |
| **Currency_Code** | Text | Currency of salary | USD, BRL, MXN, PEN, ZAR |
| **Department** | Text | Department/Business Unit | Operations, Workshop, Engineering, HR, Finance |
| **Description/Display** | Text | Detailed department/role description | "Sales - Operations Manager" |
| **CPE** | Currency | Cost Per Employee metric | 10940 |

**Key Insight:** Contains all compensation and organizational structure data. Essential for salary analysis, department-wise costing, and CPE calculations.

---

## **TABLE 3: Leave**

| Column Name | Data Type | Description | Example |
|------------|-----------|-------------|---------|
| **EmployeeID** | Integer (FK) | Foreign key linking to Employee Master | 1001 |
| **BalanceCarriedForward** | Decimal | Leave balance from previous period | 5.5 |
| **Cancelled** | Text | Cancelled leave indicator | Yes/No |
| **CapturedUnits** | Decimal | Leave units captured/taken | 10.0 |
| **Category_Sort** | Integer | Sorting order for leave categories | 1, 2, 3 |
| **Code** | Text | Leave type code | CL, SL, PL, UL |
| **ConsecutiveLeave** | Integer | Number of consecutive leaves taken | 3 |
| **ConsecutiveLeaveFlag** | Text | Flag for consecutive leave | Yes/No |
| **CreditUnitsTaken** | Decimal | Credit units taken in leave | 15.0 |
| **EmpID** | Text | Employee ID (alternate field) | EMP1001 |

**Key Insight:** Tracks all leave management data. Used for leave usage analysis, leave balance reporting, and leave patterns by department.

---

## **TABLE 4: DimCalendar**

| Column Name | Data Type | Description | Example |
|------------|-----------|-------------|---------|
| **Date** | Date | Calendar date | 2025-01-15 |
| **DATE_01** | Text | Formatted date (DD-MM-YYYY) | 15-01-2025 |
| **Month/Year/Sort** | Text | Month-Year combination | Jan-2025, Feb-2025 |
| **Month/Year** | Text | Month-Year for display | January 2025 |
| **YEAR** | Integer | Calendar year | 2025 |

**Key Insight:** Standard date dimension for time-based analysis. Enables month-year grouping and trend analysis over time.

---

## **Key Relationships:**

```
Employee Master
    ↓ (via EmployeeID)
    ├─→ Salary
    ├─→ Leave
    └─→ DimCalendar (via dates)
```

**Note:** All three (Salary, Leave, DimCalendar) connect to Employee Master for comprehensive HR analytics.

---

## **Important Calculations & Measures (DAX)**

### **Attrition Rate**
```
Attrition Rate = 
  CALCULATE(COUNTA(EmployeeMaster[EmployeeID]), 
  EmployeeMaster[CurrentStatus] = "Terminated") / 
  CALCULATE(COUNTA(EmployeeMaster[EmployeeID]))
```
**Insight:** Shows percentage of employees who left the company

### **Active Employees**
```
Active Count = 
  CALCULATE(COUNTA(EmployeeMaster[EmployeeID]), 
  EmployeeMaster[CurrentStatus] = "Active")
```
**Insight:** Current working workforce headcount

### **CPE (Cost Per Employee)**
```
CPE = SUM(Salary[CPE]) / COUNTA(EmployeeMaster[EmployeeID])
```
**Insight:** Average cost per employee metric

### **Total Leaves Taken**
```
Total Leaves = SUM(Leave[CapturedUnits])
```
**Insight:** Aggregate leave consumption across workforce

---
## Data Connections
All tables connect via **EmployeeID**
---
