# Topic: DAX

---

# 📊 DAX 101 — Beginner-Friendly Notes

---

## 🧠 What is DAX?

**DAX (Data Analysis Expressions)** is a formula language used in **Power BI**, **Excel Power Pivot**, and **SSAS** to create calculations on data.

Think of DAX as:
- 🧮 **Excel formulas on steroids**
- 📈 Designed for **analytics & business logic**
- 🧠 Works with **relationships, filters, and context**

---

### 🔹 What can you do with DAX?

DAX is mainly used to create:

#### 1️⃣ Calculated Columns (Row-by-Row)
- Calculated **per row**
- Stored in the table
- Useful for **filtering, categorizing, tagging**

✅ Example (string form):  
`Full Name = Customers[FirstName] & " " & Customers[LastName]`

---

#### 2️⃣ Measures (Aggregations)
- Calculated **on the fly**
- NOT stored in the table
- React to **filters, slicers, visuals**

✅ Example (string form):  
`Total Sales = SUM(Sales[Amount])`

---

## 🔄 DAX vs M Language (Power Query)

| Feature              | 🧠 DAX                              | 🛠️ M Language                     |
|----------------------|-----------------------------------|-----------------------------------|
| Used in              | Power BI Model / Reports          | Power Query (ETL stage)           |
| Purpose              | Calculations & analytics          | Data cleaning & transformation   |
| When it runs         | After data is loaded              | Before data is loaded            |
| Performance impact   | Affects report performance        | Affects refresh performance      |
| Best for             | KPIs, totals, ratios              | Cleaning, merging, reshaping     |
| Example              | Total Sales, YoY Growth           | Remove nulls, split columns      |

🧠 **Rule of thumb**  
> 🛠️ Clean data with **M** → 📊 Analyze data with **DAX**

---

## 🧱 Calculated Columns

### 📌 What are Calculated Columns?
- Created using DAX
- Computed **row by row**
- Stored in the model
- Increase model size ⚠️

### ✅ When to use them:
- Categorization
- Flags (Yes / No)
- Filtering logic

✅ Example (string form):  
`Sales Category = IF(Sales[Amount] > 1000, "High", "Low")`

📍 Result appears as a **new column** in the table.

---

## 📐 DAX Measures

### 📌 What are Measures?
- Dynamic calculations
- Calculated at **query time**
- Respect slicers, filters, visuals
- Best for performance 🚀

---

### 🔹 Implicit vs Explicit Measures

| Type                | Implicit Measure ⚡                      | Explicit Measure 🧠                          |
|---------------------|------------------------------------------|----------------------------------------------|
| How it’s created    | Auto-created by Power BI                 | Manually written in DAX                      |
| Example             | Drag column → Power BI sums it           | `Total Sales = SUM(Sales[Amount])`           |
| Control             | ❌ Limited                                | ✅ Full control                               |
| Reusability         | ❌ No                                     | ✅ Yes                                       |
| Best practice       | ❌ Avoid                                  | ✅ Recommended                                |

🧠 **Always prefer explicit measures**

---

### ⚡ Quick Measures

- Pre-built DAX templates
- Created via UI (no typing needed)
- Great for beginners 👶

Examples:
- Running total
- Year-to-date (YTD)
- Percentage of total

⚠️ Downside:
- Can create **complex & unreadable DAX**
- Harder to debug later

---

## 🧮 Calculated Columns vs Measures

| Feature                    | 🧱 Calculated Column            | 📐 Measure                     |
|----------------------------|----------------------------------|--------------------------------|
| Calculated when            | Data refresh                     | Report interaction             |
| Stored in model            | ✅ Yes                           | ❌ No                          |
| Affected by slicers        | ❌ No                            | ✅ Yes                         |
| Used for                  | Filtering, grouping              | KPIs, totals, analytics        |
| Performance impact        | Higher memory usage              | More efficient                 |
| Appears in table rows     | ✅ Yes                           | ❌ No                          |

🧠 **Simple rule**
> 🧱 Need row logic? → **Calculated Column**  
> 📐 Need totals or KPIs? → **Measure**

---

## 🗂️ Table Type Difference

### 📊 Calculated Column
- Lives **inside a table**
- Behaves like normal data
- Can be sliced, filtered, grouped

### 📐 Measure
- Lives in the **Measures area**
- Returns a **single value**
- Used in visuals (cards, charts)

---

## 🧾 Summary — DAX in One Glance

- 📊 **DAX** is for analytics, not cleaning data
- 🧱 **Calculated Columns**
  - Row-by-row
  - Stored in the model
  - Best for filtering & categorization
- 📐 **Measures**
  - Dynamic & efficient
  - React to slicers and visuals
  - Best for KPIs and aggregations
- ⚔️ **DAX vs M**
  - M = data prep
  - DAX = data analysis
- ✅ Best practice:
  - Use **M** to clean
  - Use **Measures** over columns
  - Prefer **explicit measures**

🚀 Once DAX clicks, Power BI starts to feel **powerful and fun**.

   
   
# 📐 DAX Fundamentals — Measures, Context, and Evaluation

---

## 🗂️ Dedicated Measure Tables (Best Practice)

### 📌 What is a Dedicated Measure Table?
A **dedicated measure table** is a table created **only to store measures**  
(no rows, no data — just measures).

🧠 Think of it as:
- 📁 A clean folder for all your KPIs
- 🧹 A way to keep your model organized
- 🚀 A performance-friendly best practice

---

### ✅ Why use a Dedicated Measure Table?

- 🧭 Easier navigation (no hunting for measures)
- 📊 Keeps fact & dimension tables clean
- 👥 Easier for others to understand your model
- 📐 Encourages **measure-first** design

---

### 🛠️ How it’s usually created (conceptual)
- Create an empty table (or a 1-row table)
- Rename it to something like:
  - `Measures`
  - `KPI`
  - `Report Metrics`
- Hide the column
- Move **all measures** into this table

📌 Measures live **inside the table**, but are **not affected by its rows**

---

## 🎯 Filter Context

### 📌 What is Filter Context?
**Filter context** is the set of filters applied to your data **before a measure is calculated**.

These filters can come from:
- 🎛️ Slicers
- 📊 Visuals (rows, columns, legends)
- 📄 Report / page / visual filters
- 🔗 Table relationships

🧠 **Key idea**
> Measures are always evaluated **based on the current filter context**

---

### ✅ Example (conceptual)

If a report has:
- Year = 2025
- Region = Philippines

Then a measure like:
`Total Sales = SUM(Sales[Amount])`

Will calculate:
> Total sales **only for 2025 and Philippines**

---

## 🔄 How Measures Are Calculated (Step-by-Step)

Understanding this flow is 🔑 to mastering DAX.

---

### 🥇 Step 1 — Filter Context is Detected
- Power BI checks:
  - Slicers
  - Visual selections
  - Filters
- Builds the **current filter context**

📌 Example filters:
- Product = ECG Machine
- Month = January

---

### 🥈 Step 2 — Filters Flow Downstream
- Filters travel through:
  - Relationships
  - Dimension → Fact tables
- Related tables get **automatically filtered**

🧠 This is why:
- Proper relationships are critical
- Star schema matters ⭐

---

### 🥉 Step 3 — Measure is Evaluated
- The measure runs
- It calculates using:
  - The **filtered table**
  - The **filtered rows only**

📌 Conceptual result:
> Measure returns **one number**, based on the current filters

---

## 🧠 Mental Model to Remember

Filters applied
        ↓
Relationships filter tables
        ↓
Measure calculates result


Or simply:
> 🎯 **Filters first, math second**

---

## 🧾 Summary — Key Takeaways

- 🗂️ **Dedicated Measure Tables**
  - Keep models clean
  - Store all measures in one place
  - Best practice for real projects

- 🎯 **Filter Context**
  - Measures always respect filters
  - Comes from slicers, visuals, and relationships

- 🔄 **Measure Evaluation Flow**
  1. Filter context is detected
  2. Filters flow through relationships
  3. Measure evaluates on filtered data
- 🧠 Golden rule:
  > Measures don’t change data — filters do

🚀 Master filter context, and DAX suddenly makes sense.

---

# ✍️ DAX Syntax & Operators — Made Simple

---

## 🧩 Understanding Basic DAX Syntax

Let’s start with a **simple DAX measure written in string form**:

`Total Quantity = SUM(Transactions[quantity])`

This single line already contains the **core building blocks of DAX**.

---

## 🏷️ Measure Name

### 📌 `Total Quantity`
- This is the **measure name**
- It’s what you see in:
  - Fields pane
  - Visuals (cards, tables, charts)

🧠 Important notes:
- Measures are **always referenced inside square brackets**
- Example reference:
  - `[Total Quantity]`

📌 Brackets are required because:
- Measure names can contain spaces
- DAX needs to clearly identify them

---

## 🧠 Function Name

### 📌 `SUM`
- This is a **DAX function**
- It performs an **aggregation**

Why aggregation matters 👇

### 🧱 In a Calculated Column:
- DAX works **row by row**
- This is valid:
  - `= Transactions[quantity]`
- Because each row has **one value**

### 📐 In a Measure:
- DAX must return **a single value**
- This is **NOT valid**:
  - `= Transactions[quantity]`
- Power BI doesn’t know:
  - which row?
  - which value?

👉 You must tell DAX **how to summarize**  
(using functions like `SUM`, `COUNT`, `AVERAGE`, etc.)

🧠 **Golden rule**
> Measures always need **aggregation**

---

## 🗂️ Referenced Table Name

### 📌 `Transactions`
- This is the **table name**
- It tells DAX **where the column lives**

⚠️ Naming matters:
- If your table name is:
  - `Transactions Table`
- You must write it exactly:
  - `'Transactions Table'`

🧠 Quotes are required when:
- Table names contain spaces
- Special characters are used

---

## 📊 Referenced Column Name

### 📌 `[quantity]`
- This is the **column name**
- Columns are always written:
  - Inside square brackets

📌 Full column reference format:
- `TableName[ColumnName]`

---

## 🧮 Full Syntax Breakdown (Visual)

[Measure Name] = FUNCTION(TableName[ColumnName])

Applied example:

[Total Quantity] = SUM(Transactions[quantity])

---

## ➗ DAX Operators

Operators are used to **perform logic and calculations** inside DAX.

---

### 🔢 Arithmetic Operators

Used for math operations:

| Operator | Meaning         | Example (string form) |
|---------:|-----------------|-----------------------|
| `+`      | Addition        | `A + B`               |
| `-`      | Subtraction     | `A - B`               |
| `*`      | Multiplication  | `A * B`               |
| `/`      | Division        | `A / B`               |
| `^`      | Power           | `A ^ 2`               |

📌 Example:
- `Total Cost = [Quantity] * [Unit Price]`

---

### 🔍 Comparison Operators

Used for conditions:

| Operator | Meaning          | Example |
|---------:|------------------|---------|
| `=`      | Equal to         | `A = B` |
| `<>`     | Not equal to     | `A <> B` |
| `>`      | Greater than     | `A > B` |
| `<`      | Less than        | `A < B` |
| `>=`     | Greater or equal | `A >= B` |
| `<=`     | Less or equal    | `A <= B` |

📌 Common use:
- Inside `IF` logic

---

### 🔀 Logical Operators

Used to combine conditions:

| Operator | Meaning | Example |
|---------:|---------|---------|
| `&&`     | AND     | `A && B` |
| `||`     | OR      | `A || B` |
| `!`      | NOT     | `!A`     |

📌 Example (conceptual):
- `IF(A > 100 && B = "Yes", "High", "Low")`

---

## 🧠 Key Mental Models

- 🧱 **Columns** → row-by-row
- 📐 **Measures** → one result
- 🧮 **Measures need aggregation**
- 🎯 **Operators control logic and math**

---

## 🧾 Summary — DAX Syntax in One Page

- ✍️ A DAX measure has:
  - Measure name
  - Function
  - Table reference
  - Column reference

- 🧱 Calculated columns can reference columns directly
- 📐 Measures **must aggregate**
- 🗂️ Table names with spaces need quotes

- ➗ DAX operators fall into:
  - Arithmetic
  - Comparison
  - Logical

🚀 Master the syntax, and DAX stops feeling scary.

---

# 🧠 Common DAX Function Categories — Big Picture Guide

DAX has **many functions**, but they’re easier to learn when grouped into **categories**.  
Below is a **high-level, beginner-friendly map** of the most common ones — with **simple explanations and string-form examples**.

---

## 🔢 Math & Stats Functions

Used for **numeric calculations and aggregations**.

### 📌 Common Use Cases
- Totals
- Averages
- Minimum / Maximum
- Counting rows or values

### ⭐ Common Functions
- `SUM`
- `AVERAGE`
- `MIN`
- `MAX`
- `COUNT`
- `COUNTROWS`

### ✅ Examples (string form)
- `Total Sales = SUM(Sales[Amount])`
- `Average Price = AVERAGE(Products[Price])`
- `Row Count = COUNTROWS(Transactions)`

🧠 Best for:
> KPIs, totals, summary numbers

---

## 🔀 Logical Functions

Used for **decision-making** and **conditional logic**.

### 📌 Common Use Cases
- Categorizing data
- Creating flags (Yes / No)
- Business rules

### ⭐ Common Functions
- `IF`
- `SWITCH`
- `AND`
- `OR`
- `NOT`

### ✅ Examples (string form)
- `Sales Flag = IF([Total Sales] > 100000, "High", "Low")`
- `Status = SWITCH(TRUE(), [Qty] = 0, "Out of Stock", "Available")`

🧠 Best for:
> Turning numbers into meaning

---

## 🔤 Text Functions

Used for **working with text values**.

### 📌 Common Use Cases
- Combining text
- Cleaning text
- Extracting parts of strings

### ⭐ Common Functions
- `CONCATENATE`
- `LEFT`
- `RIGHT`
- `MID`
- `LEN`
- `UPPER`
- `LOWER`
- `TRIM`

### ✅ Examples (string form)
- `Full Name = CONCATENATE(Customers[FirstName], " ", Customers[LastName])`
- `Upper Name = UPPER(Customers[Name])`

🧠 Best for:
> Labels, display values, formatting

---

## 🎯 Filter Functions

Used to **modify or control filter context**.

### 📌 Common Use Cases
- Applying custom filters
- Overriding slicers
- Time intelligence logic

### ⭐ Common Functions
- `CALCULATE`
- `FILTER`
- `ALL`
- `ALLEXCEPT`
- `VALUES`
- `SELECTEDVALUE`

### ✅ Examples (string form)
- `Total Sales All Time = CALCULATE([Total Sales], ALL(Date))`
- `Selected Year = SELECTEDVALUE(Date[Year])`

🧠 Best for:
> Advanced analytics and context control

---

## 📊 Table Functions

Used to **return or manipulate tables**.

### 📌 Common Use Cases
- Virtual tables
- Iterations
- Advanced filtering

### ⭐ Common Functions
- `SUMX`
- `AVERAGEX`
- `FILTER`
- `VALUES`
- `DISTINCT`
- `ADDCOLUMNS`

### ✅ Examples (string form)
- `Total Revenue = SUMX(Sales, Sales[Qty] * Sales[Price])`
- `Distinct Products = DISTINCT(Products[ProductName])`

🧠 Best for:
> Row-by-row calculations inside measures

---

## 📅 Date & Time Functions

Used for **time-based analysis**.

### 📌 Common Use Cases
- Year-to-date (YTD)
- Month-to-date (MTD)
- Year-over-year (YoY)

### ⭐ Common Functions
- `TODAY`
- `NOW`
- `DATE`
- `YEAR`
- `MONTH`
- `DATESYTD`
- `SAMEPERIODLASTYEAR`

### ✅ Examples (string form)
- `Sales YTD = TOTALYTD([Total Sales], Date[Date])`
- `Sales Last Year = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Date[Date]))`

🧠 Best for:
> Trends, seasonality, growth analysis

---

## 🔗 Relationship Functions

Used to **control or activate relationships**.

### 📌 Common Use Cases
- Multiple date relationships
- Inactive relationships
- Role-playing dimensions

### ⭐ Common Functions
- `USERELATIONSHIP`
- `RELATED`
- `RELATEDTABLE`
- `CROSSFILTER`

### ✅ Examples (string form)
- `Sales by Ship Date = CALCULATE([Total Sales], USERELATIONSHIP(Sales[ShipDate], Date[Date]))`
- `Customer Country = RELATED(Customers[Country])`

🧠 Best for:
> Complex data models and advanced reporting

---

## 🧾 Summary — How to Think About DAX Functions

- 🔢 **Math & Stats** → numbers & totals
- 🔀 **Logical** → decisions & rules
- 🔤 **Text** → labels & formatting
- 🎯 **Filter** → control context
- 📊 **Table** → row-by-row logic
- 📅 **Date & Time** → trends & time intelligence
- 🔗 **Relationship** → model behavior

🧠 **Learning tip**  
> Master **Math + Logical + Filter** first — everything else builds on them.

🚀 With these categories in mind, DAX becomes a toolbox instead of a maze.
