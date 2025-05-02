# SSIS Task Overview: Get Latest Employee Excel File & Remove Password

### **Task Objective:**
- Identify the **latest Excel file** in a folder where the **file name contains 'Employee'**.
- **Remove the password** protection from the Excel file.
- Use a **Script Task** to handle file selection and password removal.

---

### **SSIS Components to Use:**
- **Foreach Loop Container** → To iterate through Excel files in a folder.
- **Script Task** → 
  - Identify the **latest file** with "Employee" in the name.
  - Use **third-party libraries** (like **EPPlus** or **Interop**) to remove the password.
- **Data Flow Task (Optional)** → If you need to load the Excel data into SQL after removing the password.

---

### **Process Flow:**
1. **Use Foreach Loop Container** to scan for Excel files in a folder.
2. **In Script Task:**
   - Identify the latest file containing "Employee" in its name.
   - Use **Excel Interop** or **EPPlus** to remove password protection.
   - Save the decrypted file.
3. (Optional) **Load the decrypted file into SQL** if required.
