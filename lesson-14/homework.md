# SSIS Task Overview: Handling Missing Customers & Error Logging

### Task Objective:
# Task Overview: Loading Customers Data into SQL Table with Lookup Validation

## 1. Load the Customers File into SQL Table

The provided **Customers file** contains the following data:

| **CustomerID** | **CustomerName** | **Email**            | **Phone**       | **Address**  |
|----------------|------------------|----------------------|-----------------|--------------|
| 101            | John Doe         | john@example.com     | 123-456-7890    | 123 Main St  |
| 102            | Alice Smith      | alice@example.com    | 987-654-3210    | 456 Oak St   |
| 103            | Bob Johnson      | bob@example.com      | 555-123-4567    | 789 Pine St  |
| 104            | Emma Watson      | emma@example.com     | 111-222-3333    | 101 Birch St |

---

## 2. Validate Each CustomerID Against a Lookup Table

- The **Lookup Table** contains the following data:

| **CustomerID** | **Status** |
|----------------|------------|
| 101            | Active     |
| 102            | Active     |
| 104            | Active     |

---

## 3. Load Data Logic

1. **If CustomerID exists in Lookup Table** (Status = Active), load data into the **Customers Table**.

   ### Customers Table (Valid Data):

   | **CustomerID** | **CustomerName** | **Email**            | **Phone**       | **Address**  |
   |----------------|------------------|----------------------|-----------------|--------------|
   | 101            | John Doe         | john@example.com     | 123-456-7890    | 123 Main St  |
   | 102            | Alice Smith      | alice@example.com    | 987-654-3210    | 456 Oak St   |
   | 104            | Emma Watson      | emma@example.com     | 111-222-3333    | 101 Birch St |

2. **If CustomerID does not exist in Lookup Table**, load into the **Customers_ErrorTable**.

   ### Customers ErrorTable (Missing in Lookup):

   | **CustomerID** | **CustomerName** | **Email**            | **Phone**       | **Address**  | **ErrorReason**       |
   |----------------|------------------|----------------------|-----------------|--------------|-----------------------|
   | 103            | Bob Johnson      | bob@example.com      | 555-123-4567    | 789 Pine St  | CustomerID not found  |


---

### Additional Requirements:
- **Send an email notification** listing missing customers.
- Implement an **Event Handler** to capture and log errors.
- Update the **SSISLog Table** with error details.

### SSIS Components to Use:
- **Data Flow Task** → Load and validate **CustomerID** using a **Lookup Transformation**.
- **Conditional Split** → Route missing **CustomerIDs** to **Customers_ErrorTable**.
- **Execute SQL Task** → Insert missing customers into the **Customers_ErrorTable**.
- **Script Task** → Notify about missing customers via email.
- **Event Handler (OnError Event)** → Capture errors, send email with details, and update the **SSISLog Table**.

### Process Flow:
1. Extract data from the **Customers File**.
2. Perform a **Lookup** against the **Customer Reference Table**.
3. Route missing **CustomerIDs** to the **Error Table**.
4. **Send an email notification** listing missing customers.
5. Capture **package errors** via the **Event Handler** and send an email with error details (message, date, package name, runner ID/name).
6. Update the **SSISLog Table** with error details.
