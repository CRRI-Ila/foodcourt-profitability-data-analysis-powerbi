
# Data Model Relationships Documentation
## Power BI Project

This document explains the relationships configured in the Power BI data model.

Café Sales is the central fact table of the model.

<img width="1889" height="991" alt="image" src="https://github.com/user-attachments/assets/325cf8d7-41f3-4013-92cc-27fb8ee1d4db" />
---

## 1. Relationship: NP Academic Calendar to Café Sales
<img width="360" height="530" alt="image" src="https://github.com/user-attachments/assets/aa3bd030-b965-491a-a2ef-93ee93db6dc8" />

### Purpose
This relationship allows analysis of:
- Sales by semester
- Academic weeks and weekdays
- Holiday vs non-holiday performance
- Time-based trend analysis

### Tables and Columns

| From Table | Column | To Table | Column |
|------------|--------|----------|--------|
| NP Acad Calendar | Date | Café Sales | Date |

### Relationship Configuration
- Cardinality: Many to One (*:1)
- Active: Yes
- Cross-filter direction: Single
- Relationship type: Dimension to Fact

### Explanation
The calendar table contains one row per date.  
The Café Sales table contains multiple transactions per date.  

Therefore the relationship is many-to-one from Café Sales to NP Academic Calendar.

---

## 2. Relationship: Operating Costs to Café Sales
<img width="424" height="517" alt="image" src="https://github.com/user-attachments/assets/621a02dc-830b-43d2-b0cf-0f89d860c5b2" />

### Purpose
This relationship allows:
- Revenue vs operating cost comparison
- Monthly profitability analysis
- Cost tracking by location
- Performance analysis by month and location

Operating costs are recorded monthly while sales are recorded daily.  
A composite key is used to connect both tables.

### Tables and Columns

| From Table | Column | To Table | Column |
|------------|--------|----------|--------|
| Operating Costs | Mth-Yr-Loc | Café Sales | Mth-Yr-Loc |

### Relationship Configuration
- Cardinality: Many to One (*:1)
- Active: Yes
- Cross-filter direction: Single
- Relationship type: Dimension to Fact

### Explanation
The Operating Costs table contains one record per month per location.  
The Café Sales table contains many transactions per month per location.  

Therefore the relationship is many-to-one from Café Sales to Operating Costs.

---

## Key Column Used: Mth-Yr-Loc

This column combines:
- Month
- Year
- Location

Example values:
- Oct-22-FC22
- Apr-23-Munch
- Oct-23-MakanPlace

This ensures operating costs are correctly assigned to sales by month and location.

---

## Data Model Structure

The model follows a star schema design:

NP Academic Calendar -> Café Sales <- Operating Costs

Café Sales acts as the central fact table connected to dimension tables.

---

## Conclusion

The relationships in this model ensure accurate time-based and cost-based analysis.  
They support profitability analysis, cost tracking, and performance evaluation across locations and academic periods.

