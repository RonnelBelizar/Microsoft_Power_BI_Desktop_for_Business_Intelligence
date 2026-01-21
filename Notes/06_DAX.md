# Topic:

---

# 🎯 Advanced DAX Concepts — FILTER, Iterators, Time Intelligence & Best Practices

This section connects **how DAX thinks** with **how you should write it**.  
These are the ideas that separate *working DAX* from *good DAX* 🧠✨

All examples are written in **string form**.

---

## 🎯 FILTER (Deeper Understanding)

### 📌 What FILTER really does
`FILTER` returns a **table** after applying a **row-by-row condition**.

🧠 Key idea:
- `FILTER` creates a **virtual table**
- That table is then used by `CALCULATE` or iterators

---

### ✅ Example (string form)
`High Sales Only = FILTER(Sales, Sales[Amount] > 100000)`

📌 Meaning:
- Scan each row
- Keep only rows where condition is true

⚠️ Important:
- `FILTER` is powerful
- But can be **expensive** if overused

---

## 🔁 Iterator Functions

### 📌 What is an Iterator?
An **iterator**:
- Loops **row by row**
- Evaluates an expression for each row
- Then aggregates the result

🧠 Iterator functions end with **X**.

---

### ⭐ Common Iterators
- `SUMX`
- `AVERAGEX`
- `MINX`
- `MAXX`
- `COUNTX`

---

### ✅ Example (string form)
`Total Revenue = SUMX(Sales, Sales[Quantity] * Sales[UnitPrice])`

📌 Meaning:
1. Go row by row in Sales
2. Multiply Quantity × Price
3. Sum the results

🧠 Use iterators when:
- Calculations involve **multiple columns**
- Simple `SUM` is not enough

⚠️ Performance note:
- Iterators are **more expensive**
- Use only when necessary

---

## ⏳ Time Intelligence

Time intelligence functions require:
- A **proper Date table**
- A **relationship** to your fact table

---

## 📈 Performance-to-Date Functions

Used for cumulative analysis within a period.

---

### 📅 DATESYTD (Year-to-Date)
`Sales YTD = CALCULATE([Total Sales], DATESYTD(Date[Date]))`

📌 Meaning:
- From start of year
- Up to current date

---

### 📆 DATESQTD (Quarter-to-Date)
`Sales QTD = CALCULATE([Total Sales], DATESQTD(Date[Date]))`

---

### 📅 DATESMTD (Month-to-Date)
`Sales MTD = CALCULATE([Total Sales], DATESMTD(Date[Date]))`

---

## ⏪ Previous Period Functions

Used for comparisons.

---

### 📆 Previous Year
`Sales Last Year = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Date[Date]))`

📌 Meaning:
- Compare same period
- One year back

---

## 🔄 Running Total

Shows cumulative growth over time.

---

### 📈 Running Total Example
`Running Total Sales = CALCULATE([Total Sales], FILTER(ALL(Date), Date[Date] <= MAX(Date[Date])))`

📌 Meaning:
- Remove date filters
- Accumulate values up to current date

---

## 🧠 DAX Best Practices (Real-World Rules)

These rules will **save you from pain later** 😅

---

### 🧱 Know When to Use Columns vs Measures
- 🧱 Calculated Columns:
  - Row-level logic
  - Categorization
- 📐 Measures:
  - Aggregations
  - KPIs
  - Anything dynamic

---

### 📐 Always Use Explicit Measures
❌ Don’t rely on auto-generated sums  
✅ Write your own measures — even simple ones

🧠 Benefits:
- Reusable
- Maintainable
- Predictable behavior

---

### 🏷️ Use Fully Qualified Column References
Always write:
- `TableName[ColumnName]`

🧠 Why?
- Avoid ambiguity
- Improve readability
- Prevent future errors

---

### ⬆️ Move Calculations “Upstream”
If possible:
- Do it in:
  - Source system
  - Power Query (M)
- Not in DAX

🧠 Why?
- Faster models
- Cleaner DAX
- Better performance

---

### 🐢 Minimize Expensive Iterators
- Avoid iterators when:
  - Simple aggregations work
- Prefer:
  - `SUM` over `SUMX`
  - `COUNT` over `COUNTX`

🧠 Rule of thumb:
> Use iterators **only when you must**

---

## 🧾 Summary — Advanced DAX in Practice

- 🎯 `FILTER` creates virtual tables
- 🔁 Iterators loop row by row (powerful but expensive)
- ⏳ Time intelligence enables:
  - YTD, QTD, MTD
  - Period comparisons
  - Running totals
- 📐 Best practices focus on:
  - Measures over columns
  - Explicit over implicit
  - Performance-aware DAX

🚀 Follow these rules, and your DAX will scale **cleanly and confidently**.

