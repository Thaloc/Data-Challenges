# README.md

# Org Chart Overhaul

Compute reporting chains and report counts from a parent-child (employee-manager) hierarchy.

## Task
From `OfficeSpace.csv`, produce these columns for every employee:
- **Reporting Hierarchy**: highest manager → … → employee
- **Direct Reports**: number of employees directly managed
- **Total Reports**: total employees under them (direct + indirect)

Then answer:
- **What is the sum of the `Total Reports` column?**

## Input
**OfficeSpace.csv** with (at minimum):
- `Employee Name`
- `Manager Name` (null/blank for the top-level manager)

## Method
1. Map each employee to their manager.
2. Build an adjacency list of direct reports for each manager.
3. Compute:
   - Reporting hierarchy by walking up the manager chain (memoized).
   - Direct reports from adjacency list length.
   - Total reports via recursion over descendants (memoized).
4. Sum the `Total Reports` column for the submission answer.

## Run
```bash
pip install pandas
python your_script.py
