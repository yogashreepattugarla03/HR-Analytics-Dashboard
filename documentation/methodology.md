# Analysis Methodology - SPR HR Analytics Dashboard
## How I Built This Dashboard

### Step 1: Understand The Data
Explored the 4 tables (Employee, Salary, Leave, Calendar) and checked data quality and relationships.

### Step 2: Design Data Model
Connected tables using Employee ID. Used Star Schema for efficiency and flexibility.

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

### Step 3: Identify Key Metrics
Selected metrics that matter: Employee count, Attrition rate, CPE, Salary growth, Leave patterns, Exit categories, Department and Country distribution.

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
### Step 5: Design 5 Dashboard Pages

**Page 1: Employee Analysis** - Count, age, gender, department, experience, status, job title, job grade

**Page 2: Leave Analysis** - Leave type, frequency rate, average units, total employees, cancellation rate

**Page 3: Salary Analysis** - Department salary sum, salary growth rate, total cost, average salary, gender split, top 10 paid

**Page 4: Cross Analysis** - Filters (status, country, grade, age, experience) + Metrics (attrition, CPE, active employees) + Analysis (exits by dept, top countries, leave by title, attrition trends)

**Page 5: Final Sheet** - Status filter + Metrics (attrition, active, gender split, CPE) + Analysis (top 5 dept by leave, top 10 attrition trends, top 5 countries, top 5 dept salary, top 10 dept leaves, exit breakdown, employee count)

### Step 6: Add Filters
Added interactive filters: Status, Country, Job Grade, Age Group, Experience Bucket (varies by page)

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
### Step 6: Add Filters
Added interactive filters: Status, Country, Job Grade, Age Group, Experience Bucket (varies by page)

## Key Decisions
- **Separate pages** for different topics (Employee, Leave, Salary) so each user sees what they need
- **Top N analysis** (top 5/10) to avoid overwhelming data
- **Multiple filters** for detailed analysis beyond just department
- **Include salary growth** to show trends, not just absolute values
- **Track leave cancellation** to understand actual usage

## What I Learned From Data
- Very low attrition (0.3%) = good retention
- Multi-country operation (5 countries)
- Leave usage varies by job title
- Stable cost per employee
- Gender diversity data available

---

