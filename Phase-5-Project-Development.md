 Phase 5: Project Development

 Project Title

Import Data Using Transform Maps (Spreadsheet)

 1. Development Overview

The development phase focuses on implementing the employee data import solution in ServiceNow.

The solution was developed using an Excel spreadsheet as the external data source, an Import Set table for staging the imported data, a Transform Map for transferring the data, and the Employee Test table as the target table.

 2. Excel Data Preparation

An Excel spreadsheet was prepared with the following fields:

* Employee ID
* Employee Name
* Email
* Department
* Location

The initial sample data used for the project included employee records such as:

| Employee ID | Employee Name | Email                                     | Department | Location  |
| ----------- | ------------- | ----------------------------------------- | ---------- | --------- |
| SB-0001     | Ravi Kumar    | [ravi@gmail.com](mailto:ravi@gmail.com)   | IT         | Chennai   |
| SB-0002     | Priya Sharma  | [priya@gmail.com](mailto:priya@gmail.com) | HR         | Hyderabad |
| SB-0003     | Arun Kumar    | [arun@gmail.com](mailto:arun@gmail.com)   | Finance    | Bangalore |
| SB-0004     | Ajay Kumar    | [ajay@gmail.com](mailto:ajay@gmail.com)   | IT         | Chennai   |

 3. Employee Test Table Development

A custom table named **Employee Test** was created in ServiceNow.

The table was configured with the following fields:

| Field         | Type   |
| ------------- | ------ |
| Employee ID   | String |
| Employee Name | String |
| Email         | String |
| Department    | String |
| Location      | String |

This table serves as the target table for the transformed employee records.

 4. Employee Import Table Development

An Import Set table named **Employee Import** was created.

The Employee Import table is used as the staging area for employee data uploaded from the Excel spreadsheet.

The imported spreadsheet data is first stored in this table before the transformation process.

 5. Transform Map Development

A Transform Map named Sample Spreadsheet Import was created.

 Source Table

Employee Import

 Target Table

Employee Test

The Transform Map connects the imported spreadsheet data with the target Employee Test table.

 6. Field Mapping

The source and target fields were mapped as follows:

| Source Field  | Target Field  |
| ------------- | ------------- |
| Employee ID   | Employee ID   |
| Employee Name | Employee Name |
| Email         | Email         |
| Department    | Department    |
| Location      | Location      |

The field mappings ensure that the imported employee information is transferred to the correct target fields.

 7. Data Transformation

The Excel spreadsheet was uploaded into ServiceNow through the Import Set process.

The imported data was then transformed using the Sample Spreadsheet Import Transform Map.

After successful transformation, employee records were created in the Employee Test table.

 8. Coalesce Development

Coalesce was configured on the Transform Map to identify existing employee records.

The Employee ID was used as the identifier for the insert and update testing process.

The Coalesce configuration supports the following behavior:

* Existing Employee ID → update the existing record.
* New Employee ID → insert a new record.
* Existing unchanged data → prevent duplicate creation.

 9. Insert and Update Implementation

Additional employee data was used to test the transformation process.

The test data contained:

* Existing Employee IDs with modified information.
* New Employee IDs.

This allowed the system to demonstrate both update and insert operations during transformation.

 10. Duplicate Prevention

The same imported data was uploaded again after the initial transformation.

The Coalesce configuration was used to identify records that already existed.

This prevented duplicate employee records from being created.

 11. Reports Development

Three reports were created using the Employee Test table.

 11.1 Employees by Department

* Table: Employee Test
* Type: Pie Chart
* Group By: Department
* Aggregation: Count

 11.2 Employees by Location

* Table: Employee Test
* Type: Bar Chart
* Group By: Location
* Aggregation: Count

 11.3 Employee List Report

* Table: Employee Test
* Type: List
* Employee ID
* Employee Name
* Email
* Department
* Location

 12. Dashboard Development

An **Employee Analytics Dashboard** was created.

The dashboard provides a centralized view of the employee reports created from the Employee Test table.

The configured reports were added to the dashboard for employee data visualization.

 13. Development Workflow

```text
Excel Spreadsheet
       ↓
Employee Import Table
       ↓
Sample Spreadsheet Import
       ↓
Field Mapping
       ↓
Data Transformation
       ↓
Employee Test Table
       ↓
Coalesce
       ↓
Insert / Update / Duplicate Prevention
       ↓
Reports
       ↓
Employee Analytics Dashboard
```

 14. Development Outcome

The ServiceNow implementation was completed with:

* Employee Test table
* Employee Import table
* Sample Spreadsheet Import Transform Map
* Source-to-target field mappings
* Employee data transformation
* Coalesce configuration
* Insert and update processing
* Duplicate prevention
* Employee reports
* Employee Analytics Dashboard

 15. Conclusion

The development phase implemented the complete employee data import workflow in ServiceNow.

The solution enables employee data to be imported from a spreadsheet, transformed into ServiceNow records, updated when existing Employee IDs are detected, and prevented from being duplicated.

Reports and the Employee Analytics Dashboard were also developed to provide visibility into the imported employee data.
