Phase 6 – Project Testing

1. Testing Overview

The testing phase was carried out to verify the employee data import process using ServiceNow Import Sets and Transform Maps.

The main focus of this phase was to test the Coalesce functionality and verify that existing employee records are updated while new employee records are inserted.


2. Coalesce Testing

Coalesce was configured for the Employee ID field in the Transform Map.

The Employee ID is used to identify whether an employee record already exists in the Employee Test table.

The following behavior was tested:

- Existing Employee ID → Update the existing record
- New Employee ID → Insert a new record
- Existing Employee ID imported again → Do not create a duplicate record



3. Test Data

The following modified employee data was used for testing:

| Employee ID | Employee Name | Email | Department | Location |
|---|---|---|---|---|
| SB-0001 | Ravi Kumar Updated | ravi.updated@gmail.com | IT | Chennai |
| SB-0002 | Priya Sharma Updated | priya.updated@gmail.com | HR | Hyderabad |
| SB-0005 | Kiran Patel | kiran@gmail.com | Finance | Mumbai |
| SB-0006 | Sneha Reddy | sneha@gmail.com | IT | Pune |

The records `SB-0001` and `SB-0002` were existing records and were modified to test the update operation.

The records `SB-0005` and `SB-0006` were new records and were used to test the insert operation.


4. Test Execution

The modified Excel file was uploaded into the existing **Employee Import** table.

The existing Transform Map **Sample Spreadsheet Import** was selected and the transformation was executed.

After the transformation was completed, the Transform History was checked to verify the results.


5. Expected Transform Result

The expected transformation result is:

| Result | Count |
|---|---:|
| Total | 4 |
| Inserts | 2 |
| Updates | 2 |
| Ignored | 0 |
| Errors | 0 |

The two existing employee records should be updated and the two new employee records should be inserted.


6. Employee Data Validation

After the transformation, the **Employee Test** table was checked to verify the imported data.

The expected results are:

- `SB-0001` – Ravi Kumar Updated
- `SB-0002` – Priya Sharma Updated
- `SB-0005` – Kiran Patel
- `SB-0006` – Sneha Reddy

This verifies that both update and insert operations were processed correctly.


7. Duplicate Prevention Test

The same Excel data was imported again to test duplicate prevention using Coalesce.

Since the Employee IDs already existed in the Employee Test table, duplicate records should not be created.

The repeated import should result in the existing records being identified and ignored instead of creating duplicate records.


8. Testing Result

The testing verifies the following:

- Employee data can be imported successfully.
- Existing employee records can be updated.
- New employee records can be inserted.
- Coalesce can identify existing records using Employee ID.
- Duplicate records are prevented during repeated imports.
- Transform History can be used to verify the transformation results.


9. Conclusion

The testing phase verified the employee data import process using Import Sets, Transform Maps, and Coalesce.

The test demonstrates that existing employee records can be updated, new employee records can be inserted, and duplicate records can be prevented when the same employee data is imported again.

<img width="1917" height="912" alt="update" src="https://github.com/user-attachments/assets/8dd9cb57-1475-4324-b629-c3d7d5c6699b" />

<img width="1912" height="912" alt="repeated" src="https://github.com/user-attachments/assets/438fb97e-80e2-44fb-8f84-d032ed631ae4" />

