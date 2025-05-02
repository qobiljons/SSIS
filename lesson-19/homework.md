# SSIS Task: Loading Student Registration Data from OLTP to OLAP

## Overview
This SSIS package will:

1. **Extract student registration data** from an OLTP table:

   | **StudentID** | **FirstName** | **LastName** | **DateOfBirth** | **Gender** | **Course** | **RegistrationDate**   | **FeePaid** |
   |---------------|---------------|--------------|-----------------|------------|------------|------------------------|-------------|
   | 1             | John          | Doe          | 2000-05-12      | M          | CS         | 2025-01-10 14:30:00    | 500.00      |
   | 2             | Jane          | Smith        | 2002-08-20      | F          | Math       | 2025-01-11 15:45:00    | 550.00      |

2. **Transform the data** (clean, lookup, and aggregate).

3. **Load the data** into an OLAP system (Fact & Dimension Tables):

### Dim Tables:

- **Dim_Student**:

   | **StudentKey** | **StudentID** | **FullName**   | **DateOfBirth** | **Gender** |
   |----------------|---------------|----------------|-----------------|------------|
   | 1              | 1             | John Doe       | 2000-05-12      | M          |
   | 2              | 2             | Jane Smith     | 2002-08-20      | F          |

- **Dim_Course**:

   | **CourseKey** | **CourseName** |
   |---------------|----------------|
   | 1             | CS             |
   | 2             | Math           |

### Fact Table:

- **Fact_Students_Registration**:

   | **RegistrationID** | **StudentKey** | **CourseKey** | **RegistrationDateKey** | **FeePaid** |
   |--------------------|----------------|---------------|-------------------------|-------------|
   | 1                  | 1              | 1             | 20250110                | 500.00      |
   | 2                  | 2              | 2             | 20250111                | 550.00      |

### Log Execution Details:
- Success/Failure Logs
