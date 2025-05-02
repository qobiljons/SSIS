# SSIS Package: Excel & Flat File Data Integration

This SSIS package integrates data from an Excel file and a Flat File, performs transformations, and loads the data into a SQL Server table. The package includes complexities such as row-specific data extraction, custom delimiters, and the use of variables for dynamic configuration.

---

## 1. **Data Sources**

### 1.1 Excel File

- **Data starts at Row 4**, ignore rows above it.
- **Column names are in Row 5**.

#### Excel Data Sample:

| **ID** | **Name** | **Age** | **D** | **E** |
|--------|----------|---------|-------|-------|
| 1      | Alice    | 30      |       |       |
| 2      | Bob      | 25      |       |       |

---

### 1.2 Flat File

- The flat file contains a **header row** that matches the schema of the Excel file.

#### Flat File Data Sample:

| **ID** | **Name** | **Age** |
|--------|----------|---------|
| 3      | Charlie  | 35      |
| 4      | David    | 28      |

## 2. **SQL Table Configuration**

- Use an **SSIS variable** to store the destination SQL table name.
- **Challenge:**
  - If the table **does not exist**, dynamically create it using an **Execute SQL Task** based on the schema of the source data.
  - Add a **timestamp column** (`LoadDateTime`) to track when each row is processed.

---

## 3. **Transformations**

### 3.1 Derived Column Transformations
- **MonthsForAge**: Create a derived column that calculates the age in months (for example, 36 months for someone 3 years old).
- **SourceType**: Add a derived column indicating the data source (`"Excel"` or `"Flat File"`) for each row. This column will be inserted into the SQL target table.

---

## 4. **Data Integration**

- Use a **Union All** transformation to combine the data from both sources (Excel and Flat File).
  - Ensure proper column alignment and standardization before combining the data.

---

## 5. **Dynamic Configuration**

- Use **SSIS variables** to store the file paths for:
  - The Excel source.
  - The Flat File source.

---

## 6. **Data Validation and Error Logging**

### 6.1 Conditional Split Transformation
- Use a **Conditional Split** transformation to:
  - **Exclude** rows where the age is less than 18 years old.

### 6.2 Logging Failed Rows
- Log all rows that fail validation into a flat file (`ErrorLog.txt`).
- Include the **reason for failure** in the error log (e.g., "Missing Age" or "Age < 18").

---

## 7. **Final SQL Table Schema**

| Column Name      | Description                           |
|------------------|---------------------------------------|
| [All Source Columns] | From Excel/Flat File schema         |
| `MonthsForAge`   | Derived column, age in months        |
| `SourceType`     | `"Excel"` or `"Flat File"`            |
| `LoadDateTime`   | Timestamp when the row was processed  |

---

## 8. **Notes**

- Ensure **correct column mapping** and **data type alignment** across both data sources (Excel and Flat File).
- Use **Precedence Constraints** and **Data Flow Tasks** to ensure proper execution sequence.
- Optionally, use a **Script Task** for enhanced logging or custom validation logic.

---
