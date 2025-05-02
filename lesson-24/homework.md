# SSIS Package: Environment-Aware Deployment and Scheduling

**Create an SSIS package that utilizes project configurations for different environments (Production, Development, QA), deploy it to SQL Server Database (SSISDB), and schedule it to run every 2 hours for one day. Additionally, ensure the ability to dynamically change the SSIS package connection servers via the SQL Agent job.**

---

## **Key Points:**

### **Project Configurations:** 
- Set up SSIS parameters for each environment (Dev, QA, Prod) and map these to environments in SSISDB.

### **Connection String Management:**
- Use the **Override Connection String** feature in SQL Server Agent to change server connections dynamically.

### **Job Scheduling:**
- Schedule the SSIS package to run every 2 hours for 1 day using SQL Server Agent.

### **Environment-Aware Deployments:**
- The SSIS project should be deployed to SSISDB, and the environments should allow for flexible connections based on the environment.
