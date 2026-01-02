# Topic:

---

# 🔢 Basic Math, Stats & Logical Functions in DAX

This section covers the **most commonly used beginner DAX functions**.  
All examples are written in **string form** so they stay clean inside your notes.

---

## 🔢 Basic Math & Statistical Functions

Used for **totals, averages, and numeric summaries**.

---

### ➕ SUM
Adds all numeric values in a column.

📌 Example:  
`Total Quantity = SUM(Transactions[Quantity])`

🧠 Use when:
- You need totals (sales, quantity, hours, revenue)

---

### 📊 AVERAGE (AVG)
Calculates the average (mean) value.

📌 Example:  
`Average Quantity = AVERAGE(Transactions[Quantity])`

🧠 Use when:
- Measuring typical or average performance

---

### 📈 MAX
Returns the highest value in a column.

📌 Example:  
`Max Quantity = MAX(Transactions[Quantity])`

🧠 Use when:
- Finding peaks or highest records

---

### 📉 MIN
Returns the lowest value in a column.

📌 Example:  
`Min Quantity = MIN(Transactions[Quantity])`

🧠 Use when:
- Finding minimums or lowest values

---

### ➗ DIVIDE
Safely divides two numbers.

📌 Example:  
`Average Price = DIVIDE([Total Sales], [Total Quantity])`

🧠 Why use `DIVIDE` instead of `/`?
- Prevents divide-by-zero errors
- Returns blank instead of crashing

---

## 🔢 Counting Functions

Used to **count rows or values**.

---

### 🔢 COUNT
Counts **numeric values only**.

📌 Example:  
`Quantity Count = COUNT(Transactions[Quantity])`

🧠 Use when:
- Column contains only numbers

---

### 🔤 COUNTA
Counts **non-blank values** (text or numbers).

📌 Example:  
`Non Blank Count = COUNTA(Customers[CustomerName])`

🧠 Use when:
- Column includes text

---

### 🧬 DISTINCTCOUNT
Counts **unique values** only.

📌 Example:  
`Unique Customers = DISTINCTCOUNT(Transactions[CustomerID])`

🧠 Use when:
- Counting distinct users, products, or IDs

---

### 📊 COUNTROWS
Counts **rows in a table**.

📌 Example:  
`Transaction Rows = COUNTROWS(Transactions)`

🧠 Use when:
- You need total number of records

---

## 🔀 Basic Logical Functions

Used for **decision-making and business rules**.

---

### 🔁 IF
Returns one value if true, another if false.

📌 Example:  
`Sales Category = IF([Total Sales] > 100000, "High", "Low")`

🧠 Use when:
- Simple yes/no logic

---

### ⚠️ IFERROR
Handles errors gracefully.

📌 Example:  
`Safe Average = IFERROR([Total Sales] / [Total Quantity], 0)`

🧠 Use when:
- Preventing errors in visuals

---

### 🔄 SWITCH
Cleaner alternative to multiple IF statements.

📌 Example:  
`Performance = SWITCH(TRUE(), [Total Sales] > 100000, "Excellent", [Total Sales] > 50000, "Good", "Average")`

🧠 Use when:
- Multiple conditions exist

---

### 🔗 AND
Checks if **all conditions are true**.

📌 Example:  
`High Performer = AND([Total Sales] > 100000, [Total Quantity] > 1000)`

---

### 🔀 OR
Checks if **any condition is true**.

📌 Example:  
`Promo Eligible = OR([Customer Type] = "VIP", [Total Sales] > 50000)`

---

## 🧠 Quick Comparison Tables

### 🔢 Math & Stats

| Function  | Purpose                    |
|----------:|----------------------------|
| `SUM`     | Adds values                |
| `AVERAGE` | Mean value                 |
| `MAX`     | Highest value              |
| `MIN`     | Lowest value               |
| `DIVIDE`  | Safe division              |

---

### 🔢 Counting

| Function         | Counts What?          |
|-----------------:|-----------------------|
| `COUNT`          | Numeric values only   |
| `COUNTA`         | Non-blank values      |
| `DISTINCTCOUNT`  | Unique values         |
| `COUNTROWS`      | Table rows            |

---

### 🔀 Logical

| Function   | Purpose                     |
|-----------:|-----------------------------|
| `IF`       | True / False logic          |
| `IFERROR`  | Handle errors               |
| `SWITCH`   | Multiple conditions         |
| `AND`      | All conditions must be true |
| `OR`       | Any condition can be true   |

---

## 🧾 Summary — What to Remember

- 🔢 Use **SUM / AVERAGE / MIN / MAX** for basic analytics
- ➗ Use **DIVIDE** instead of `/`
- 🔢 Counting functions differ by:
  - numeric
  - non-blank
  - distinct
  - rows
- 🔀 Logical functions turn numbers into decisions
- 🧠 Best practice:
  > Combine math + logic to create meaningful KPIs

🚀 These functions are the foundation of **almost every DAX measure**.
