# Explanation of the SSIS Task and Requirements

### Task Objective:
- Process the **most recent** `.txt` file from each of **three subfolders** inside a parent folder.
- Load the data from these files into a **target SQL table**.
- Log file details (file name, location, and creation time) into a **log table**.

### SSIS Components to Use:
- **Foreach Loop Container**: To loop through each subfolder and find `.txt` files.
- **Script Task**: To determine the **most recent file** in each folder.
- **Data Flow Task**: To load the file data into the target table.
- **Execute SQL Task**: To insert file metadata (name, path, creation time) into the log table.

### Process Flow:
1. Use **Foreach Loop** to iterate through subfolders.
2. In **Script Task**, get the latest `.txt` file from each folder.
3. Load file data into the target table.
4. Store file metadata in a log table.
