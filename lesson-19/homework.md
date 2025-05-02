# SSIS Task: Loading Student Registration Data from OLTP to OLAP

### **Overview**
This SSIS package will:
- **Extract student registration data** from an OLTP table.
![Image 1](images/image1.png)

---

- **Transform the data** (clean, lookup, and aggregate).
- **Load the data** into an OLAP system (Fact & Dimension Tables).
![Image 2](images/image2.png)

---

### **Dim Tables:**
- **Dim_Student**
- **Dim_Course**
![Image 3](images/image3.png)

---

### **Fact Table:**
- **Fact_Students_Registration**
![Image 4](images/image4.png)

---

- **Log Execution Details** (Success/Failure Logs).
