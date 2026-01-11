# Topic:

---

# 🎯 Core DAX Functions — RELATED, CALCULATE, ALL, FILTER & Measure Totals

These functions are **cornerstones of real-world DAX**.  
Once these click, DAX stops feeling “magical” and starts feeling **logical** 🧠✨

All examples are written in **string form** for clean markdown notes.

---

## 🔗 RELATED Function

### 📌 What does RELATED do?
`RELATED` pulls a **value from a related table**  
(typically from a **dimension → fact** relationship).

🧠 Key requirements:
- Tables **must be related**
- Works in **row context**
- Commonly used in **calculated columns**

---

### ✅ Example (string form)
`Customer Country = RELATED(Customers[Country])`

📌 Meaning:
- For each row in the fact table
- Get the related customer’s country

🧠 Use when:
- You need lookup values
- Adding descriptive fields to fact tables

---

## 🧮 CALCULATE Function (Most Important Function)

### 📌 What does CALCULATE do?
`CALCULATE` **changes the filter context** of a measure.

🧠 Think of it as:
> “Calculate this measure, **but under these rules**”

---

### 🧠 Basic Syntax
`CALCULATE([Measure], Filter1, Filter2, ...)`

---

### ✅ Example (string form)
`Sales 2025 = CALCULATE([Total Sales], Date[Year] = 2025)`

📌 Meaning:
- Temporarily apply a filter
- Then evaluate the measure

---

### 🔥 Why CALCULATE is special
- It **creates or modifies filter context**
- It’s the gateway to:
  - Time intelligence
  - Advanced analytics
  - Context manipulation

🧠 **Golden rule**
> If a measure feels “smart”, it probably uses `CALCULATE`

---

## 📊 DAX Measure Totals (Why Totals Look “Different”)

### ❓ Why don’t totals equal the sum of rows?
Because:
- Measures are **re-evaluated**
- Totals have a **different filter context**

🧠 Important concept:
> Totals are **not sums of visible rows**  
> Totals are **a new calculation**

---

### 📌 Example (conceptual)
Row level:
- Each row → filtered by product

Total level:
- No product filter
- Measure recalculates for all products

🧠 This is expected behavior — not an error.

---

## 🌍 ALL Function

### 📌 What does ALL do?
`ALL` **removes filters** from:
- A table
- Or specific columns

---

### ✅ Example (string form)
`Total Sales All Time = CALCULATE([Total Sales], ALL(Date))`

📌 Meaning:
- Ignore any date filters
- Always return full total

---

### 🧠 Common Uses
- Percentage of total
- Baseline comparisons
- “Ignore slicers” logic

---

## 🎯 FILTER Function

### 📌 What does FILTER do?
`FILTER` returns a **filtered table** based on a condition.

🧠 Key idea:
- It works **row by row**
- Commonly used inside `CALCULATE`

---

### 🧠 Basic Syntax
`FILTER(Table, Condition)`

---

### ✅ Example (string form)
`High Value Sales = CALCULATE([Total Sales], FILTER(Products, Products[Price] > 1000))`

📌 Meaning:
- Filter the Products table
- Only include expensive products
- Then calculate sales

---

## 🔄 How These Functions Work Together

Most real DAX measures combine them:

CALCULATE
    ↓
FILTER modifies table
    ↓
ALL removes unwanted filters
    ↓
Measure recalculates


🧠 Example pattern:
- Percentage of total
- Top-N analysis
- Time comparisons

---

## 🧠 Mental Models to Remember

- 🔗 `RELATED` → lookup value
- 🧮 `CALCULATE` → change context
- 📊 Totals → new calculation
- 🌍 `ALL` → remove filters
- 🎯 `FILTER` → apply custom logic

---

## 🧾 Summary — Power DAX Essentials

- 🔗 **RELATED**
  - Pulls values from related tables
  - Works in row context
- 🧮 **CALCULATE**
  - Most important DAX function
  - Changes filter context
- 📊 **Measure Totals**
  - Recalculated, not summed
- 🌍 **ALL**
  - Removes filters
  - Enables total comparisons
- 🎯 **FILTER**
  - Applies row-by-row filtering
  - Often used inside `CALCULATE`

🚀 Master these five, and you unlock **advanced DAX thinking**.
