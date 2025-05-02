# Task 1: Use Script Task

### Folder Setup and File Identification:
1. **Create Folder**: Create a folder containing multiple `.txt` and `.csv` files.
2. **File Filtering**:
   - Identify `.txt` files that end with the current date in the format `ddMMyyyy.txt` (e.g., `Employees_25012025.txt` if today's date is January 25, 2025).
   - **Process Only Valid Files**: The script task will filter files that match the required pattern.

### File Processing:
1. **Read Content**: For each filtered `.txt` file, read the employee details.
   - The content should be in a structured format such as: `ID, Name, Salary`.
2. **Insert Data**: Insert each line from the file into the SQL `Employees` table. Each line should correspond to a row in the table.

---

# Task 2: Excel File Processing

### Input Data:
- A folder containing 3 Excel files.
- Each Excel file contains **2 sheets**, but the script should dynamically handle more sheets if present.

### Sheet Structure:
Each sheet has the following columns:
- `ID`
- `Name`

### Processing Requirements:
1. **Loop Through Excel Files**: Iterate through each Excel file in the folder.
2. **Process Sheets**: For each file, process all sheets (2 sheets per file, but the script should be flexible for more sheets).
   - Extract the data from each sheet.

### Output Requirements:
1. **Insert Data**: Insert the extracted data into the `Customer` SQL table.
2. **Save as Text Files**: For each sheet, save the extracted data to a `.txt` file.
   - The file name should correspond to the sheet name (e.g., `Sheet1.txt`, `Sheet2.txt`).
