# Task Requirements with Script Task

### **Input Data:**
- A folder containing **3 Excel files**, each with **2 sheets**.
- Each sheet contains the following columns:
  - `ID`
  - `Name`

### **Processing Steps:**
1. **Use Script Task** to loop through all Excel files in the folder.
2. For each **Excel file**:
   - Access each sheet in the file.
   - Extract the data from the sheet.

### **Output Requirements:**
1. **Insert the Data**:
   - Insert the extracted data into the SQL `Customer` table with the columns:
     - `ID`
     - `Name`
2. **Save the Data**:
   - Save the data from each sheet into a `.txt` file.
   - The file name should match the sheet name (e.g., `Sheet1.txt`, `Sheet2.txt`).
   - Use a **comma-separated format** for the `.txt` file.

### **Error Handling:**
- Log errors for:
  - Missing files.
  - Missing sheets.
  - Data issues (e.g., invalid format).
- Handle exceptions during:
  - Database insertions.
  - File writing.
