# DAX Measures Documentation

## Orange Groove Cafe – Power BI SIT Project

All DAX measures are organised in a separate table named **Metrics**.
This improves model readability and keeps calculations separate from raw data tables.

The measures support revenue analysis, cost tracking, profitability evaluation, and operational insights.

---

# 1. Time Measures

## Duration of Days

Calculates the number of days in the selected sales period.

```DAX
Duration of Days =
DATEDIFF(
    MIN('Café Sales'[Date]),
    MAX('Café Sales'[Date]),
    DAY
)
```

---

# 2. Quantity Measures

## Total Quantity

Total number of items sold.

```DAX
Total Quantity =
SUM('Café Sales'[Quantity])
```

## Items Per Day

Average number of items sold per day.

```DAX
Items Per Day =
SUM('Café Sales'[Quantity]) / [Duration of Days]
```

## PERdayQuantity

Average daily quantity based on operating month days.

```DAX
PERdayQuantity =
SUM('Café Sales'[Quantity]) /
SUM('Operating Costs'[Op Month].[Day])
```

---

# 3. Revenue Measures

## Revenue

Total revenue based on item price and quantity.

```DAX
Revenue =
SUMX(
    'Café Sales',
    'Café Sales'[Price] * 'Café Sales'[Quantity]
)
```

## Revenue per Item

Average revenue earned per item sold.

```DAX
Revenue per Item =
DIVIDE([Revenue], [Total Quantity])
```

---

# 4. Cost Measures

## Ingredient Cost

Total ingredient cost for all items sold.

```DAX
Ingredient Cost =
SUMX(
    'Café Sales',
    'Café Sales'[Cost] * 'Café Sales'[Quantity]
)
```

## Fixed Costs

Sum of rental and staff salary costs.

```DAX
Fixed Costs =
SUM('Operating Costs'[Rental Cost]) +
SUM('Operating Costs'[Staff Salaries])
```

## Variable Costs

Utility expenses plus ingredient costs.

```DAX
Variable Costs =
SUM('Operating Costs'[Utility Expenses]) +
[Ingredient Cost]
```

## Total Staff Cost

Total salary cost.

```DAX
Total Staff Cost =
SUM('Operating Costs'[Staff Salaries])
```

## Totalcost

Total operating cost.

```DAX
Totalcost =
[Variable Costs] + [Fixed Costs]
```

## Cost per Item

Average cost per item sold.

```DAX
Cost per Item =
DIVIDE([Totalcost], [Total Quantity])
```

---

# 5. Profit Measures

## Profit

Total profit after deducting all costs.

```DAX
Profit =
[Revenue] - [Totalcost]
```

## Profit Margin %

Profit as a percentage of revenue.

```DAX
Profit Margin % =
DIVIDE([Profit], [Revenue])
```

## new pm

Maximum profit margin recorded.

```DAX
new pm =
MAX('Café Sales'[Profit Margin])
```

## old pm

Minimum profit margin recorded.

```DAX
old pm =
MIN('Café Sales'[Profit Margin])
```

---

# 6. Location and Product Measures

## FC (Food Club 22 Quantity)

```DAX
FC =
CALCULATE(
    SUM('Café Sales'[Quantity]),
    'Operating Costs'[Location] = "Food Club 22"
)
```

## MP (Makan Place Quantity)

```DAX
MP =
CALCULATE(
    SUM('Café Sales'[Quantity]),
    'Operating Costs'[Location] = "Makan Place"
)
```

## LA (Specific Product Quantity)

Soymilk Pure Matcha Latte quantity sold.

```DAX
LA =
CALCULATE(
    SUM('Café Sales'[Quantity]),
    'Café Sales'[Menu Item] = "Soymilk Pure Matcha Latte"
)
```

---

# 7. Target Measures

## Target

Revenue target used for KPI comparison.

```DAX
Target =
500000
```

## Revenue Variance

Difference between actual revenue and target.

```DAX
Revenue Variance =
[Revenue] - [Target]
```

## Target Achievement %

Percentage of revenue target achieved.

```DAX
Target Achievement % =
DIVIDE([Revenue], [Target])
```

---

# 8. Model Notes

* All measures are stored in the **Metrics** table.
* Relationships used:

  * NP Acad Calendar[Date] → Café Sales[Date]
  * Operating Costs[Mth-Yr-Loc] → Café Sales[Mth-Yr-Loc]
* Measures support profitability, operational efficiency, and performance tracking.

---

# Conclusion

These DAX measures enable:

* Profitability analysis
* Cost monitoring
* Sales performance tracking
* Target evaluation
* Operational decision-making

They form the core analytical logic of the Orange Groove Cafe Power BI model.
