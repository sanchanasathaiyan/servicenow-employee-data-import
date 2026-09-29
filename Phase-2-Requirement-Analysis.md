Phase 2: Requirement Analysis

Project Title

Import Data Using Transform Maps (Spreadsheet)

1. Introduction

The requirement analysis phase identifies the functional and data requirements needed to implement the employee data import solution in ServiceNow.

The system is designed to import structured employee information from an Excel spreadsheet, transform the imported data, and store it in the Employee Test table.

2. Functional Requirements

The system should provide the following functionality:

2.1 Employee Data Preparation

The system should support employee data prepared in an Excel spreadsheet.

The spreadsheet should contain:

* Employee ID
* Employee Name
* Email
* Department
* Location

2.2 Employee Test Table

A custom **Employee Test** table should be created to store the transformed employee records.

The table should contain:

| Field         | Type   |
| ------------- | ------ |
| Employee ID   | String |
| Employee Name | String |
| Email         | String |
| Department    | String |
| Location      | String |

2.3 Employee Import Table

An Import Set table named **Employee Import** should be used to temporarily store the data imported from the spreadsheet.

2.4 Transform Map

A Transform Map named **Sample Spreadsheet Import** should be created.

The Transform Map should:

* Use **Employee Import** as the source table.
* Use **Employee Test** as the target table.
* Map the source fields to the corresponding target fields.
* Transform the imported data into employee records.

2.5 Data Transformation

The system should transform the imported spreadsheet data and create records in the Employee Test table.

2.6 Coalesce

Coalesce should be configured for an employee field so that existing employee records can be identified.

Employee ID is used as the unique employee identifier for the testing process.

The system should:

* Update an existing employee when the Employee ID already exists.
* Insert a new employee when the Employee ID does not exist.
* Prevent duplicate records when the same data is imported again.

2.7 Reports

The system should provide the following reports:

1.Employees by Department

   * Pie chart
   * Grouped by Department
   * Count aggregation

2. Employees by Location

   * Bar chart
   * Grouped by Location
   * Count aggregation

3. Employee List Report

   * List format
   * Employee ID
   * Employee Name
   * Email
   * Department
   * Location

2.8 Dashboard

An Employee Analytics Dashboard should be created to provide a centralized view of the employee reports.

3. Non-Functional Requirements

The project should provide:

* Simple and structured data import.
* Consistent employee data.
* Duplicate prevention through Coalesce.
* Easy validation of imported records.
* Clear reports for employee information.
* Centralized visualization through a dashboard.

4. Input Requirements

The primary input is an Excel spreadsheet containing employee information.

Example input fields:

| Employee ID | Employee Name | Email                                     | Department | Location  |
| ----------- | ------------- | ----------------------------------------- | ---------- | --------- |
| SB-0001     | Ravi Kumar    | [ravi@gmail.com](mailto:ravi@gmail.com)   | IT         | Chennai   |
| SB-0002     | Priya Sharma  | [priya@gmail.com](mailto:priya@gmail.com) | HR         | Hyderabad |
| SB-0003     | Arun Kumar    | [arun@gmail.com](mailto:arun@gmail.com)   | Finance    | Bangalore |
| SB-0004     | Ajay Kumar    | [ajay@gmail.com](mailto:ajay@gmail.com)   | IT         | Chennai   |

5. Output Requirements

After successful transformation, the employee information should be available in the **Employee Test** table.

The system should also provide:

* Inserted employee records
* Updated employee records
* Duplicate prevention
* Department report
* Location report
* Employee list report
* Employee Analytics Dashboard

6. Testing Requirements

The system should be tested using both existing and new employee IDs.

The testing process should verify that:

* Existing employee IDs are updated.
* New employee IDs are inserted.
* Re-importing unchanged records does not create duplicates.
* Imported data appears correctly in the Employee Test table.
* Reports display the employee data correctly.
* The dashboard displays the configured reports.

7. Requirement Summary

| Requirement         | Description                            |
| ------------------- | -------------------------------------- |
| Spreadsheet Import  | Import employee data from Excel        |
| Import Set          | Temporarily store imported data        |
| Employee Test Table | Store final employee records           |
| Transform Map       | Transfer and transform source data     |
| Field Mapping       | Map source fields to target fields     |
| Coalesce            | Identify existing employee records     |
| Validation          | Verify imported employee records       |
| Reports             | Analyze employee information           |
| Dashboard           | Provide centralized data visualization |

8. Conclusion

The requirement analysis defines the functional, data, testing, reporting, and dashboard requirements for the ServiceNow employee data import project.

These requirements provide the basis for designing and implementing the ServiceNow solution in the following phases.
