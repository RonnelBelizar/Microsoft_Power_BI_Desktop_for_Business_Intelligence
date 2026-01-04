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

---

# 🔤 DAX Text Functions — Clean & Practical Guide

Text functions are used to **manipulate, clean, and format text values**.  
They’re commonly used in **calculated columns** and sometimes in **measures** (for labels or logic).

All examples are written in **string form** for clean notes ✨

---

## 📏 LEN

Returns the **number of characters** in a text string.

📌 Example:  
`Name Length = LEN(Customers[CustomerName])`

🧠 Use when:
- Checking text length
- Validating IDs or codes

---

## 🔗 CONCATENATE

Joins two text strings together.

📌 Example:  
`Full Name = CONCATENATE(Customers[FirstName], " ", Customers[LastName])`

🧠 Tip:
- You can also use `&` for concatenation:
  - `Customers[FirstName] & " " & Customers[LastName]`

🧠 Use when:
- Creating labels
- Combining names or codes

---

## 🔠 UPPER / LOWER

Changes text case.

### 🔼 UPPER
Converts text to **ALL CAPS**.

📌 Example:  
`Upper Name = UPPER(Customers[CustomerName])`

---

### 🔽 LOWER
Converts text to **lowercase**.

📌 Example:  
`Lower Name = LOWER(Customers[CustomerName])`

🧠 Use when:
- Standardizing text
- Cleaning inconsistent casing

---

## ✂️ LEFT / RIGHT / MID

Used to **extract parts of a text string**.

---

### ⬅️ LEFT
Extracts characters from the **start** of text.

📌 Example:  
`First 3 Letters = LEFT(Products[ProductCode], 3)`

---

### ➡️ RIGHT
Extracts characters from the **end** of text.

📌 Example:  
`Last 2 Digits = RIGHT(Products[ProductCode], 2)`

---

### 🎯 MID
Extracts text from the **middle**.

📌 Example:  
`Middle Code = MID(Products[ProductCode], 2, 4)`

🧠 MID parameters:
- Start position
- Number of characters

---

## 🔁 SUBSTITUTE

Replaces specific text with new text.

📌 Example:  
`Clean Name = SUBSTITUTE(Customers[CustomerName], "-", " ")`

🧠 Use when:
- Removing special characters
- Cleaning inconsistent text

---

## 🔍 SEARCH

Finds the **position of text** inside another text string.

📌 Example:  
`At Symbol Position = SEARCH("@", Users[Email])`

🧠 Important notes:
- Case-insensitive
- Returns a number (position)
- Errors if text is not found

🧠 Common use:
- Checking if text exists
- Extracting substrings using `MID`

---

## 🧠 Quick Reference Table

| Function        | What it Does                      |
|----------------:|-----------------------------------|
| `LEN`           | Counts characters                 |
| `CONCATENATE`   | Joins text                        |
| `UPPER`         | Converts to uppercase             |
| `LOWER`         | Converts to lowercase             |
| `LEFT`          | Extracts from start               |
| `RIGHT`         | Extracts from end                 |
| `MID`           | Extracts from middle              |
| `SUBSTITUTE`    | Replaces text                     |
| `SEARCH`        | Finds text position               |

---

## 🧾 Summary — Text Functions in Practice

- 🔤 Text functions are great for:
  - Labels
  - Cleaning messy data
  - Formatting display values
- ✂️ Use `LEFT / RIGHT / MID` to extract parts
- 🔁 Use `SUBSTITUTE` to clean text
- 🔍 Use `SEARCH` to locate text
- 🧠 Best used in:
  - Calculated columns
  - Light logic inside measures

🚀 Master text functions and your data instantly looks cleaner and smarter.

---

# 📅 Basic Date & Time Functions in DAX

Date & time functions are used for **time-based logic**, **reporting**, and **analysis**.  
They are essential for **trends, aging, schedules, and time intelligence**.

All examples are written in **string form** for clean markdown notes ✨

---

## ⏰ TODAY / NOW

### 📆 TODAY
Returns the **current date** (no time).

📌 Example:  
`Today Date = TODAY()`

🧠 Use when:
- Tracking current date
- Date-based flags (e.g., overdue items)

---

### ⌛ NOW
Returns the **current date and time**.

📌 Example:  
`Current Timestamp = NOW()`

🧠 Use when:
- Time-sensitive tracking
- Refresh-based timestamps

⚠️ Note:
- Updates only when the dataset refreshes

---

## 📆 DAY / MONTH / YEAR

Extract specific parts of a date.

---

### 📅 DAY
Returns the **day of the month**.

📌 Example:  
`Order Day = DAY(Orders[OrderDate])`

---

### 🗓️ MONTH
Returns the **month number** (1–12).

📌 Example:  
`Order Month = MONTH(Orders[OrderDate])`

---

### 🏷️ YEAR
Returns the **year**.

📌 Example:  
`Order Year = YEAR(Orders[OrderDate])`

🧠 Use when:
- Creating date attributes
- Grouping by year or month

---

## ⏱️ HOUR / MINUTE / SECOND

Extract time components from a datetime value.

---

### 🕒 HOUR
Returns the **hour** (0–23).

📌 Example:  
`Order Hour = HOUR(Orders[OrderDateTime])`

---

### ⏲️ MINUTE
Returns the **minute** (0–59).

📌 Example:  
`Order Minute = MINUTE(Orders[OrderDateTime])`

---

### ⏳ SECOND
Returns the **second** (0–59).

📌 Example:  
`Order Second = SECOND(Orders[OrderDateTime])`

🧠 Use when:
- Analyzing activity by time of day

---

## 📆 WEEKDAY / WEEKNUM

Used for **week-based analysis**.

---

### 📅 WEEKDAY
Returns the **day of the week** as a number.

📌 Example:  
`Day of Week = WEEKDAY(Orders[OrderDate])`

🧠 Notes:
- Default:
  - Sunday = 1
  - Saturday = 7
- Can be customized using parameters

---

### 📊 WEEKNUM
Returns the **week number of the year**.

📌 Example:  
`Week Number = WEEKNUM(Orders[OrderDate])`

🧠 Use when:
- Weekly reporting
- Operational dashboards

---

## 📆 EOMONTH

Returns the **last day of a month**, before or after a given date.

📌 Example:  
`Month End Date = EOMONTH(Orders[OrderDate], 0)`

🧠 Offset examples:
- `0` → current month end
- `1` → next month end
- `-1` → previous month end

🧠 Use when:
- Financial reporting
- Monthly cutoffs

---

## ⏳ DATEDIFF

Calculates the **difference between two dates**.

📌 Example:  
`Days Open = DATEDIFF(Orders[OrderDate], TODAY(), DAY)`

🧠 Time units:
- `DAY`
- `MONTH`
- `YEAR`
- `HOUR`
- `MINUTE`
- `SECOND`

🧠 Use when:
- Aging reports
- SLA tracking
- Duration analysis

---

## 🧠 Quick Reference Table

| Function        | Purpose                          |
|----------------:|----------------------------------|
| `TODAY`         | Current date                     |
| `NOW`           | Current date & time              |
| `DAY`           | Day of month                     |
| `MONTH`         | Month number                     |
| `YEAR`          | Year                             |
| `HOUR`          | Hour                             |
| `MINUTE`        | Minute                           |
| `SECOND`        | Second                           |
| `WEEKDAY`       | Day of week number               |
| `WEEKNUM`       | Week of year                     |
| `EOMONTH`       | End of month date                |
| `DATEDIFF`      | Difference between dates         |

---

## 🧾 Summary — Date & Time Essentials

- 📅 Use **TODAY / NOW** for current date logic
- 📆 Use **DAY / MONTH / YEAR** to break down dates
- ⏱️ Use **HOUR / MINUTE / SECOND** for time analysis
- 📊 Use **WEEKDAY / WEEKNUM** for weekly views
- 📆 Use **EOMONTH** for month-end calculations
- ⏳ Use **DATEDIFF** for aging and duration

🚀 Date functions are the backbone of time-based analytics in Power BI.

