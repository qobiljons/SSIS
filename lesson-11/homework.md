# Task Overview: Complex File Processing Workflow Using PowerShell in SSIS

### Requirements:
1. **Use PowerShell** to move files from **SourceFolder** to **TargetFolder** based on:
   - **Current Timestamp** in file names.
   - **File Size** (e.g., greater than 1KB).
   - **File Extension** (e.g., only `.csv` files).

2. **Archive the moved files** in SSIS as `Archive_<CurrentTimestamp>.zip`.
   - Validate that the archive file is not corrupt before proceeding.

3. **Append a log entry** to track archived files.

4. After archiving:
   - **Delete only successfully archived files** from the **SourceFolder**.

5. **Log the archive file name**, archive file location, and file archived date to the SQL log table for monitoring.
