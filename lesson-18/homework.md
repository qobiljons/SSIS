# SSIS Task Overview: Loading Excel Files into an SQL Table with Execution Logging

## Task Objective:
You need to create an SSIS package that:
- **Loads multiple Excel files** into a SQL table using a **Foreach Loop Container**.
- Performs **incremental load** to ensure only new or updated records are loaded.
- **Logs errors** (if the process fails) into a dedicated **SQL error log table**.

### Error Log Table:
| **ID** | **PackageName**     | **RunnerUsername** | **ErrorID** | **ErrorMessage**             | **ErrorDate**         |
|--------|---------------------|--------------------|-------------|-----------------------------|-----------------------|
| 1      | Load_Excel_Files     | admin              | 5001        | File not found               | 2025-01-31 10:30:00   |
| 2      | Load_Excel_Files     | user1              | 6002        | Column mismatch in Excel     | 2025-01-31 11:00:00   |

### Execution Logging:
- **Logs successful executions** into a separate **SQL success log table**, tracking details like inserted and updated rows.

#### Success Log Table:
| **ID** | **PackageName**     | **RunnerUsername** | **SourceFile**               | **TargetTable**   | **InsertedRows** | **UpdatedRows** | **ExecutionDate**       |
|--------|---------------------|--------------------|------------------------------|-------------------|------------------|-----------------|-------------------------|
| 1      | Load_Excel_Files     | admin              | Employees_31012025.xlsx      | dbo.Employees     | 100              | 10               | 2025-01-31 10:35:00     |
| 2      | Load_Excel_Files     | user1              | Customers_31012025.xlsx      | dbo.Customers     | 50               | 5                | 2025-01-31 11:05:00     |
