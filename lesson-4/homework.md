# SSIS Package Overview

**Objective**: Process multiple flat files sequentially, log progress, and load data into a SQL table with error handling.

---

## Package Structure

### 1. Foreach Loop Container
- Processes multiple files in a folder (e.g., `data1.txt`, `data2.txt`, etc.).

### 2. Script Task (Before Data Flow Task)
- Logs the **start** of file processing.

### 3. Data Flow Task
- Loads data from the flat files into the SQL table (`dbo.Customers`), with an additional `LoadDate` column.

### 4. Script Task (After Data Flow Task)
- Logs the **completion** of file processing.

---

## Precedence Constraints

### 1. File Processing Success
- If the file is processed successfully, the flow continues to the next step.

### 2. File Processing Failure
- If the file processing fails, skip to the error-handling step.

---

## Error Handling

### Log Failures:
- In case of failure, log the failure information (e.g., failure date, reason, package name, etc.) to a **log table** in the SQL database.
