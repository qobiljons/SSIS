# Explanation

The task involves reading multiple `.txt` files with dynamic names (e.g., `customer1.txt`, `customer2.txt`) and loading their data into dynamically named SQL tables (e.g., `customer1`, `customer2`), where each file corresponds to a target table.

| CustomerID | Name    | Salary |
|------------|---------|--------|
| 101        | Alice   | 500    |
| 102        | Bob     | 300    |
| 103        | Charlie | 250    |


---

# Requirements

## Folder Setup:
- A folder containing `.txt` files like `customer1.txt`, `customer2.txt`, etc.

## Database Configuration:
- **SQL Server** with OLE DB connection.
- A dynamic schema for target tables (e.g., `CustomerID`, `Name`, `Salary`).

## SSIS Components:
- **Foreach Loop Container**: To iterate through files.
- **Flat File Connection Manager**: To read the `.txt` files.
- **Execute SQL Task**: To check and create target tables.
- **Data Flow Task**: To transform and load data dynamically.

## Variables:
- **User::FilePath**: Full file path of the current `.txt` file.
- **User::FileName**: File name for the target table.
- **User::SQLCreateTable**: SQL query for creating the dynamic table.

## Error Handling:
- A mechanism to log or redirect errors for invalid rows or files.
