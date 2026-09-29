Phase 3: Project Design

Project Title

Import Data Using Transform Maps (Spreadsheet)

1. System Design Overview

The system is designed to import employee data from an Excel spreadsheet into ServiceNow.

The imported spreadsheet data is first stored in the **Employee Import** table. A **Transform Map** is then used to map the source fields to the corresponding fields in the **Employee Test** table.

After transformation, the employee records are available in the target table. Coalesce is used to identify existing records and prevent duplicate employee records.

2. System Architecture

The overall system architecture is:

```text
+---------------------------+
|    Excel Spreadsheet      |
| Employee ID               |
| Employee Name             |
| Email                     |
| Department                |
| Location                  |
+-------------+-------------+
              |
              v
+---------------------------+
|    Employee Import        |
|      Import Set Table     |
+-------------+-------------+
              |
              v
+---------------------------+
|       Transform Map       |
|  Sample Spreadsheet Import|
+-------------+-------------+
              |
              v
+---------------------------+
|       Field Mapping       |
| Source Fields -> Target   |
+-------------+-------------+
              |
              v
+---------------------------+
|      Employee Test        |
|      Target Table         |
+-------------+-------------+
              |
              v
+---------------------------+
|        Coalesce           |
| Insert / Update / Ignore  |
+-------------+-------------+
              |
              v
+---------------------------+
| Reports & Dashboard       |
+---------------------------+
```

3. Database / Table Design

3.1 Employee Test Table

The Employee Test table is the target table used to store the final employee records.

| Field         | Type   | Purpose                    |
| ------------- | ------ | -------------------------- |
| Employee ID   | String | Identifies the employee    |
| Employee Name | String | Stores employee name       |
| Email         | String | Stores employee email      |
| Department    | String | Stores employee department |
| Location      | String | Stores employee location   |

3.2 Employee Import Table

The Employee Import table acts as the staging table for data imported from the Excel spreadsheet.

The spreadsheet data is loaded into this table before the transformation process.

4. Transform Map Design

The Transform Map is named:

Sample Spreadsheet Import

 Source Table

Employee Import

 Target Table

Employee Test

The Transform Map connects the imported spreadsheet fields with the corresponding fields in the Employee Test table.

 5. Field Mapping Design

The required field mappings are:

| Source Field  | Target Field  |
| ------------- | ------------- |
| Employee ID   | Employee ID   |
| Employee Name | Employee Name |
| Email         | Email         |
| Department    | Department    |
| Location      | Location      |

The mapping ensures that each spreadsheet field is transferred to the correct target field.

 6. Data Processing Design

The data processing flow is:

1. Employee data is prepared in an Excel spreadsheet.
2. The spreadsheet is uploaded into ServiceNow.
3. The data is loaded into the Employee Import table.
4. The Transform Map identifies the source and target tables.
5. Source fields are mapped to target fields.
6. The transformation is executed.
7. Records are created or updated in the Employee Test table.
8. Coalesce is used to identify existing employee records.
9. The processed data is used for reports and dashboard visualization.

 7. Coalesce Design

Coalesce is used to identify an existing employee record based on the selected unique employee field.

For this project, **Employee ID** is used as the employee identifier for insert and update testing.

The expected behavior is:

| Condition                   | Result                   |
| --------------------------- | ------------------------ |
| Employee ID does not exist  | Insert new record        |
| Employee ID already exists  | Update existing record   |
| Same data is imported again | Prevent duplicate record |

 8. Reporting Design

Three reports are designed for the Employee Test table.

 Report 1: Employees by Department

* Table: Employee Test
* Report Type: Pie Chart
* Group By: Department
* Aggregation: Count

 Report 2: Employees by Location

* Table: Employee Test
* Report Type: Bar Chart
* Group By: Location
* Aggregation: Count

 Report 3: Employee List Report

* Table: Employee Test
* Report Type: List
* Columns:

  * Employee ID
  * Employee Name
  * Email
  * Department
  * Location

 9. Dashboard Design

The project uses an **Employee Analytics Dashboard** to provide a centralized view of the employee reports.

The dashboard contains the configured employee reports and provides a single location for viewing employee data.

 10. Design Summary

The project design connects the external spreadsheet data source with the ServiceNow target table through an Import Set and Transform Map.

The design supports:

* Spreadsheet data import
* Staging through Employee Import
* Source-to-target field mapping
* Data transformation
* Employee record creation
* Existing record updates
* Duplicate prevention
* Employee reporting
* Dashboard visualization

 11. Conclusion

The project design defines the architecture, tables, field mappings, transformation process, Coalesce behavior, reports, and dashboard.

This design provides the structure required for implementing the employee data import solution in ServiceNow.
