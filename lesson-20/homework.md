# SSIS Task: Incremental Load Using Slowly Changing Dimension (SCD) Type 0 with IsActive Flag

### **Source Sample Data**
| StudentID | FirstName | LastName | DateOfBirth  | Gender | Course | RegistrationDate | Email                 | IsActive |
|-----------|-----------|----------|--------------|--------|--------|------------------|-----------------------|----------|
| 1         | John      | Doe      | 2000-05-12   | M      | CS     | 2025-01-10       | john.doe@email.com    | 1        |
| 2         | Jane      | Smith    | 2002-08-20   | F      | Math   | 2025-01-11       | jane.smith@email.com  | 1        |
---

### **Existing Target Data**
| StudentID | FirstName | LastName | DateOfBirth | Gender | Course | RegistrationDate | Email                   |
|-----------|-----------|----------|-------------|--------|--------|------------------|-------------------------|
| 1         | John      | Doe      | 2000-05-12  | M      | IT     | 2025-01-10       | john.doe@email.com      |
| 2         | Jane      | Smith    | 2002-08-20  | F      | Math   | 2025-01-11       | jane.smith@email.com    |
| 3         | Alice     | Brown    | 2001-09-15  | F      | Physics| 2025-01-12       | alice.brown@email.com   |

---

### **Task Overview:**
1. **Extract** data from multiple file sources (Excel, CSV, TXT).
2. **Transform** using:
   - **Lookup** to check for existing records.
   - **Derived Columns** to modify or add new calculated columns.
3. **Load** data incrementally into a SQL table using **Slowly Changing Dimension (SCD) Type 0 with an IsActive flag**:
   - **If the record is new**, insert it with **IsActive = 1**.
   - **If the record exists and has changed**, insert it as a new row and set the previous record's **IsActive = 0**.

---

### **Result:**
The final result should look like this:
| StudentID | FirstName | LastName | DateOfBirth  | Gender | Course  | RegistrationDate | Email                     | IsActive | LoadDate           |
|----------:|:----------|:---------|:-------------|:-------|:--------|:-----------------|:--------------------------|:---------|:-------------------|
|         1 | John      | Doe      | 2000-05-12   | M      | CS      | 2025-01-10       | john.doe@email.com        | 0        | 2025-01-30 10:00:00 |
|         1 | John      | Doe      | 2000-05-12   | M      | IT      | 2025-01-10       | john.doe@email.com        | 1        | 2025-01-31 14:30:00 |
|         2 | Jane      | Smith    | 2002-08-20   | F      | Math    | 2025-01-11       | jane.smith@email.com      | 1        | 2025-01-30 10:00:00 |
|         3 | Alice     | Brown    | 2001-09-15   | F      | Physics | 2025-01-12       | alice.brown@email.com     | 1        | 2025-01-31 14:30:00 |
