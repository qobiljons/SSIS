# SSIS Package: Salary Data Processing

This SSIS package performs the following tasks to calculate, filter, and export salary data.

---

## 1. **Calculate Average Salary**

### 1.1 Execute SQL Task
- Use an **Execute SQL Task** to get the average salary from the first table (**SalaryFactTable**) and store it in a variable (`User::AvgSalary`).

### 1.2 Script Task
- Display the value of the variable `User::AvgSalary` using a **Script Task**.

---

## 2. **Filter Salaries**

### 2.1 Execute SQL Task
- Use another **Execute SQL Task** to retrieve salaries greater than the average salary from the second table (**SecondSalaryTable**).
- Store the filtered result in an **Object variable** (`User::FilteredSalaries`).

### 2.2 Script Task
- Display the filtered data using a **Script Task**.

---

## 3. **Export to File**

### 3.1 Data Flow Task
- Write the filtered data to a **CSV file**.
  - The file name should dynamically include the table name and the current date in the format: `SecondSalaryTable_ddMMyyyy.csv`.

---

## 4. **Sample Data and Structure**

### 4.1 Salary Fact Table
![Salary Fact Table](images/image1.png)

### 4.2 Second Salary Fact Table
![Second Salary Fact Table](images/image2.png)

---

## 5. **Expected Output**

- The result from the **Script Task** and the data in the **destination file** should look like this:

![Expected Output](images/image3.png)

---
