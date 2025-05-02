# Requirement:
Process files in a folder whose names start with **"data_"** and end with **".txt"**.
- Example file names: 
  - `data_20250125.txt`, `data_20250126.txt`

### Example Data:

# Example File Data (data_20250125.txt)
Assume this file contains emplyee details
| EmployeeID | Name         | Department | Salary  |
|-----------:|:-------------|:-----------|--------:|
|        101 | John Doe     | HR         | 50,000  |
|        102 | Jane Smith   | IT         | 60,000  |
|        103 | Alice Brown  | Finance    | 55,000  |
|        104 | Robert Black | Marketing  | 45,000  |
---

### Perform a **Fuzzy Lookup** using a SQL **Employee** table to verify if the data exists in the SQL database.

#### Lookup Table Example:
| EmployeeID | Name        | Department | Salary |
|-----------:|:------------|:-----------|-------:|
|        101 | John Doe    | HR         | 50,000 |
|        102 | Jane Smith  | IT         | 60,000 |
|        105 | Sarah White | Sales      | 52,000 |

---

### If the Data Exists:
- Load it into the **SQL Employee** table.

### If the Data Does Not Exist:
- Load it into an **error table** with an additional column **Definition** containing the value `"No exists in SQL table"`.

#### Example Error Table:
##### Employees Not Found in SQL Table

| EmployeeID | Name         | Department | Salary  | Status               |
|-----------:|:-------------|:-----------|--------:|:---------------------|
|        103 | Alice Brown  | Finance    | 55,000  | Not in SQL table     |
|        104 | Robert Black | Marketing  | 45,000  | Not in SQL table     |
****
