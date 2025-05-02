# SSIS Task: Incremental Load for Student Data Using Slowly Changing Dimension (SCD) Type 2 Logic

### **Objective:**
Develop an SSIS package to perform an incremental load from various source files (Excel, CSV, TXT) into a SQL Server table, implementing **Slowly Changing Dimension (SCD) Type 2** logic. This approach will insert new records for any changes in existing rows, maintaining historical data, and utilize an **IsActive** flag to indicate the current active record.

---

### **Requirements:**

#### **Source Data:**
- **File Types:** Excel, CSV, and TXT files containing student registration information.
- **Data Consistency:** Ensure uniform structure across all files for seamless processing.

#### **Destination:**
- **SQL Server Table:** `dbo.Students`

##### **Table Schema:**
- **StudentID** (Primary Key)
- **FirstName**
- **LastName**
- **DateOfBirth**
- **Gender**
- **Course**
- **RegistrationDate**
- **Email**
- **IsActive** (BIT)
- **StartDate** (DATETIME)
- **EndDate** (DATETIME)

---

### **SSIS Package Design:**

#### **Control Flow:**
- Use a **Foreach Loop Container** to iterate through the source files.
- Within the loop, implement a **Data Flow Task** to process each file.

#### **Data Flow Components:**
- **Source Components:**
  - Utilize appropriate **Source Components** for Excel, CSV, and TXT files.
- **Derived Column Transformation:**
  - Apply transformations to add or modify columns (e.g., `LoadDate` column with the current timestamp).
- **Lookup Transformation:**
  - Match incoming records with existing records in `dbo.Students` based on `StudentID`.
- **Conditional Split Transformation:**
  - Determine if a record is new, existing with changes, or unchanged.

#### **For Existing Records with Changes:**
- Use an **OLE DB Command Transformation** to:
  - Update the existing record's `IsActive` flag to `0`.
  - Set the `EndDate` to the current date.
- Insert a new record with updated information:
  - Set `IsActive` to `1`, `StartDate` to the current date, and `EndDate` to a default high date (e.g., `'9999-12-31'`).

#### **For New Records:**
- Insert into `dbo.Students`:
  - Set `IsActive` to `1`, `StartDate` to the current date, and `EndDate` to a default high date.

---

### **Data Handling Logic:**
- **New Records:** Insert into `dbo.Students` with `IsActive` set to `1`, `StartDate` to the current date, and `EndDate` to a default high date.
- **Existing Records with Changes:** 
  - Update the existing record's `IsActive` to `0` and `EndDate` to the current date.
  - Insert a new record with updated information, `IsActive` set to `1`, `StartDate` to the current date, and `EndDate` to a default high date.
- **Unchanged Records:** No action required.

---

### **Error Handling and Logging:**
- Capture and **log** any data flow errors.
- Maintain logs for successful inserts, updates, and errors for auditing purposes.

---

### **Performance Considerations:**
- Implement **batch inserts and updates** to optimize performance.
- Ensure appropriate **indexing** on `StudentID`, `IsActive`, `StartDate`, and `EndDate` columns in `dbo.Students`.

---

### **Testing and Validation:**
- Develop **test cases** to validate the SSIS package against various scenarios, including:
  - New records
  - Updated records
  - Unchanged records
- **Verify data integrity** post-load to ensure accuracy.

---

### **References:**
- For a practical demonstration of implementing Slowly Changing Dimensions in SSIS, refer to the following tutorial:
  - [Insert tutorial link here]
- For a detailed explanation of Slowly Changing Dimension (SCD) Type 2, consult this resource:
  - [Insert resource link here]
