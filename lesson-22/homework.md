# SSIS Task: Incremental Load for Student Registration Data with Slowly Changing Dimension (SCD) Type 1 Logic

### **Objective:**
Develop an SSIS package to perform an incremental load from various source files (Excel, CSV, TXT) into a SQL Server table, implementing **Slowly Changing Dimension (SCD) Type 1** logic. This approach will update existing records with new data when changes are detected, without preserving historical data.

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

---

### **SSIS Package Design:**

#### **Control Flow:**
- Use a **Foreach Loop Container** to iterate through the source files.
- Within the loop, implement a **Data Flow Task** to process each file.

#### **Data Flow Components:**
- **Source Components:**
  - Utilize appropriate Source Components for Excel, CSV, and TXT files.
- **Derived Column Transformation:**
  - Apply transformations to add or modify columns as necessary.
- **Lookup Transformation:**
  - Match incoming records with existing records in `dbo.Students` based on `StudentID`.
- **Conditional Split Transformation:**
  - Determine if a record is new or existing.

#### **For Existing Records:**
- Use an **OLE DB Command Transformation** to update the existing record with the new data.

#### **For New Records:**
- Insert the new record into `dbo.Students`.

---

### **Data Handling Logic:**
- **New Records:** Insert into `dbo.Students`.
- **Existing Records with Changes:** Update the existing record with the new data.
- **Unchanged Records:** No action required.

---

### **Error Handling and Logging:**
- Capture and **log** any data flow errors.
- Maintain logs for successful inserts, updates, and errors for auditing purposes.

---

### **Performance Considerations:**
- Implement **batch inserts and updates** to optimize performance.
- Ensure appropriate **indexing** on `StudentID` and other frequently queried columns in `dbo.Students`.

---

### **Testing and Validation:**
- Develop **test cases** to validate the SSIS package against various scenarios, including:
  - New records
  - Updated records
  - Unchanged records
- **Verify data integrity** post-load to ensure accuracy.
