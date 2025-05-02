# SSIS Task Overview: Data Quality Services (DQS) for Cleaning Employee Age Data

### Task Objective:
- Use **Data Quality Services (DQS)** in SSIS to clean **dirty age data** in the `EmployeeFacts` table.
- Ensure the **age values end with " years old"**.
- Add a **LoadTime** column to track when the data was processed.
- Load the cleaned data into a **SQL target table**.

### SSIS Components to Use:
- **DQS Cleansing Transformation** (in Data Flow): Clean dirty age data.
- **Derived Column Transformation**: Append " years old" to the Age column and add LoadTime.
- **OLE DB Destination**: Load cleaned data into the target SQL table.

### Process Flow:
1. Extract data from `EmployeeFacts` using **OLE DB Source**.
2. Use **DQS Cleansing** to standardize Age values.
3. Use **Derived Column** to add " years old" suffix and include LoadTime.
4. Load the final cleaned data into the SQL table.
