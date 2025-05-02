# SSIS Task: Incremental Load (Type 1) for Student Data Using Lookup and Derived Columns

### **Source Files Example:**
| StudentID | FirstName | LastName | DateOfBirth | Gender | Course | RegistrationDate | Email                  |
|-----------|-----------|----------|-------------|--------|--------|------------------|------------------------|
| 1         | John      | Doe      | 2000-05-12  | M      | CS     | 2025-01-10       | john.doe@email.com     |
| 2         | Jane      | Smith    | 2002-08-20  | F      | Math   | 2025-01-11       | jane.smith@email.com   |

---

### **Existing Target Table:**
| StudentID | FirstName | LastName | DateOfBirth | Gender | Course  | RegistrationDate | Email                   |
|-----------|-----------|----------|-------------|--------|---------|------------------|--------------------------|
| 1         | John      | Doe      | 2000-05-12  | M      | CS      | 2025-01-10       | john.doe@email.com       |
| 2         | Jane      | Smith    | 2002-08-20  | F      | Math    | 2025-01-11       | jane.smith@email.com     |
| 3         | Alice     | Brown    | 2001-09-15  | F      | Physics | 2025-01-12       | alice.brown@email.com    |


### **Task Overview:**
1. **Extract** data from multiple file sources (Excel, CSV, TXT).
2. **Transform** the data:
   - Use **Lookup** to check for existing records.
   - Use **Derived Columns** to modify or add new calculated columns.
3. **Load** data incrementally into a SQL table:
   - **Insert** new student records.
   - **Update** existing student records if any changes are detected.
