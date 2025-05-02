# SSIS Workflow for File Existence Check

### 1. Create Variables:
- **FolderPath** (String): Folder path to check.
- **FileName** (String): Pattern of the file to locate (e.g., DataFile_*.csv).
- **FileExists** (Boolean): Flag to indicate if the file exists.
- **FullFilePath** (String): Full path of the identified file.

### 2. Script Task:
- Check if the folder exists.
- Search for files matching the FileName pattern.
- Update FileExists and FullFilePath variables.
- Add retry logic and content validation (e.g., non-empty file).
- Log errors for missing files or folders.

### 3. Precedence Constraint:
- Use an expression (@[User::FileExists] == True) to connect the Script Task to the next Data Flow Task.

### 4. Data Flow Task:
- Populate data from the file identified in FullFilePath.
- Use the variable FullFilePath dynamically in the Flat File Connection Manager.
